![GitHub contributors](https://img.shields.io/github/contributors/ranahaani/gnews)
![GitHub issues](https://img.shields.io/github/issues-raw/ranahaani/gnews)
[![GNews license](https://img.shields.io/github/license/ranahaani/GNews)](https://github.com/ranahaani/GNews)
[![GNews stars](https://img.shields.io/github/stars/ranahaani/GNews)](https://github.com/ranahaani/GNews) 
[![PyPI](https://img.shields.io/pypi/v/gnews)](https://pypi.org/project/gnews/)
[![PyPI - Downloads](https://img.shields.io/pypi/dm/gnews)](https://pypistats.org/packages/gnews)

# GNews 

🚩 A Happy and lightweight Python Package that searches Google News RSS Feed and returns a usable JSON response \
🚩 As well as you can fetch full article (**No need to write scrappers for articles fetching anymore**)

![Gnews](https://github.com/ranahaani/GNews/blob/master/imgs/gnews.gif)

## Installation

``` shell
pip install gnews
```

## Usage

```python
from gnews import GNews

google_news = GNews()
json_resp = google_news.get_news('Pakistan')
print(json_resp[0])


```
```
{
'publisher': 'Aljazeera.com',
 'description': 'Pakistan accuses India of stoking conflict in Indian Ocean  '
                'Aljazeera.com',
 'published date': 'Tue, 16 Feb 2021 11:50:43 GMT',
 'title': 'Pakistan accuses India of stoking conflict in Indian Ocean - '
          'Aljazeera.com',
 'url': 'https://www.aljazeera.com/news/2021/2/16/pakistan-accuses-india-of-nuclearizing-indian-ocean'
 }

```
- Get news will return the list, `[{'title': '...', 'published date': '...', 'description': '...', 'url': '...', 'publisher': '...'}]`
#### Available locations and languages

```python
print(google_news.countries)

'Australia', 'Botswana', 'Canada ', 'Ethiopia', 'Ghana', 'India ', 'Indonesia', 'Ireland', 'Israel ', 'Kenya', 'Latvia',
'Malaysia', 'Namibia', 'New Zealand', 'Nigeria', 'Pakistan', 'Philippines', 'Singapore', 'South Africa', 'Tanzania',
'Uganda', 'United Kingdom', 'United States', 'Zimbabwe', 'Czech Republic', 'Germany', 'Austria', 'Switzerland', 'Argentina',
'Chile', 'Colombia', 'Cuba', 'Mexico', 'Peru', 'Venezuela', 'Belgium ', 'France', 'Morocco', 'Senegal', 'Italy', 'Lithuania',
'Hungary', 'Netherlands', 'Norway', 'Poland', 'Brazil', 'Portugal', 'Romania', 'Slovakia', 'Slovenia', 'Sweden',
'Vietnam', 'Turkey', 'Greece', 'Bulgaria', 'Russia', 'Ukraine ', 'Serbia', 'United Arab Emirates', 'Saudi Arabia', 'Lebanon',
'Egypt', 'Bangladesh', 'Thailand', 'China', 'Taiwan', 'Hong Kong', 'Japan', 'Republic of Korea'
```

```python
print(google_news.languages)

'english', 'indonesian', 'czech', 'german', 'spanish', 'french', 'italian', 'latvian', 'lithuanian', 'hungarian',
'dutch', 'norwegian', 'polish', 'portuguese brasil', 'portuguese portugal', 'romanian', 'slovak', 'slovenian', 'swedish',
'vietnamese', 'turkish', 'greek', 'bulgarian', 'russian', 'serbian', 'ukrainian', 'hebrew', 'arabic', 'marathi', 'hindi', 'bengali',
'tamil', 'telugu', 'malyalam', 'thai', 'chinese simplified', 'chinese traditional', 'japanese', 'korean'
```
#### We can set country, language, period and size during initialization

```python
google_news = GNews(language='english', country='United States', period='7d', max_results=10)
```


#### Others methods to set country, language, period and size
```python
set_period('7d') # News from last 7 days
max_results(10) # number of responses across a keyword
set_country('United States') # News from a specific country 
set_language('english') # News in a sepcific language
```
Google News cover across **141+ countries** with **41+ languages**.
On the bottom left side of the Google News page you may find a `Language & region` section where you can find all of the supported combinations.
## Article Properties
| Properties   | Description                                    | Example                                                                                                                                                                                                                                                                             |
|--------------|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| title        | Title of the article                           | IMF Staff and Pakistan Reach Staff-Level Agreement on the Pending Reviews Under the Extended Fund Facility                                                                                                                                                                                                   |
| url         | Google news link to article                    | [Article Link](http://news.google.com/news/url?sa=t&fd=R&ct2=us&usg=AFQjCNGNR4Qg8LGbjszT1yt2s2lMXvvufQ&clid=c3a7d30bb8a4878e06b80cf16b898331&cid=52779522121279&ei=VQU7WYjiFoLEhQHIs4HQCQ&url=https://www.theguardian.com/commentisfree/2017/jun/07/why-dont-unicorns-exist-google) |
| published date      | Published date                                 | Wed, 07 Jun 2017 07:01:30 GMT                                                                                                                                                                                                                                                       |
| description  | Short description of article                   | IMF Staff and Pakistan Reach Staff-Level Agreement on the Pending Reviews Under the Extended Fund Facility ...                                                                                                                                                                                                                  |
| publisher    | Publisher of article                           | The Guardian                                                                                                                                                                                                                                                                        |                                                                                                                                                        |


## Getting full article
 > you can use newspaper3k to scrap full article, you can also get full article using `get_full_article` by passing url.

> Make sure you already install newspaper3k

##### _Install newspaper3k_

`pip3 install newspaper3k`

```python

from gnews import GNews

google_news = GNews()
json_resp = google_news.get_news('Pakistan')
article = google_news.get_full_article(json_resp[0]['url']) # newspaper3k instance, you can access newspaper3k all attributes in article
```

```python
article.title 
```
> IMF Staff and Pakistan Reach Staff-Level Agreement on the Pending Reviews Under the Extended Fund Facility'

```python
article.text 
```


> End-of-Mission press releases include statements of IMF staff teams that convey preliminary findings after a mission. The views expressed are those of the IMF staff and do not necessarily represent the views of the IMF’s Executive Board.\n\nIMF staff and the Pakistani authorities have reached an agreement on a package of measures to complete second to fifth reviews of the authorities’ reform program supported by the IMF Extended Fund Facility (EFF) ..... (full article)
```python
article.images
```

> `{'https://www.imf.org/~/media/Images/IMF/Live-Page/imf-live-rgb-h.ashx?la=en', 'https://www.imf.org/-/media/Images/IMF/Data/imf-logo-eng-sep2019-update.ashx', 'https://www.imf.org/-/media/Images/IMF/Data/imf-seal-shadow-sep2019-update.ashx', 'https://www.imf.org/-/media/Images/IMF/Social/TW-Thumb/twitter-seal.ashx', 'https://www.imf.org/assets/imf/images/footer/IMF_seal.png'}
`
```python
article.authors
```

>`[]`

Read full documentation for `newspaper3k`
[newspaper3k](https://newspaper.readthedocs.io/en/latest/user_guide/quickstart.html#parsing-an-article)

## Todo
- Save to MongoDB
- Save to MySQL

## License

MIT © 
