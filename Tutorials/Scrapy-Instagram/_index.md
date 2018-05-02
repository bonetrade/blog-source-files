+++
title = "Scraping Instagram Post Metadata"
description = "A short tutorial on using Scrapy to scrape Instagram"
weight = 110
+++

Instagram used to have an API that allowed a very comprehensive exploration of the metadata attached to each . To use this API, one had to register as a developer and agree to the terms of service. [Pablo Barbera](http://pablobarbera.com/) from the London School of Economics has developed an excellent package for R, [instaR](https://github.com/pablobarbera/instaR) to work with the API. However, changes to the API and the approval process in the last few years has restricted use of the public API to mostly commercial purposes. That is to say, they wish to monetize the content. The result is that using Barbera's package is often not feasible for us.

Other alternatives are possible, and while they do not necessarily provide complete access to the full stream of _possible_ data, they do provide an awful lot. In essence, these approaches involve mimicing an individual paging through search results, very very quickly.

Here we will get started with a python package written by [Github user h4t0n, Andrea Tarquini](https://github.com/h4t0n) that depends on the [Scrapy](https://scrapy.org/) framework.

## Requirements:

+ Python
+ Scrapy

If you are on a mac, you already have python installed. We will install Scrapy inside of a virtual environment, so as to avoid making dependency conflicts and so on with other python packages on our machine.

```
$ mkdir scrapytest
$ virtualenv scrapytest
$ source scrapytest/bin/activate
```

Install Scrapy: `$ pip install scrapy`

Download the [instagram-scraper](https://github.com/h4t0n/instagram-scraper) from the repository.

Unzip that file. Then, make a new text file at the same level as the instagram-scraper folder. Give that file the extension `.cfg`

```
├── instagram-scraper
│   ├── __init__.py
│   ├── items.py
│   ├── pipelines.py
│   ├── settings.py
│   └── spiders
│       ├── __init__.py
│       └── hashtag.py
└── scrapy.cfg
```

Edit that file so that it contains the basic configuration information scrapy needs in order to pull together the scraper that h4t0n made:

```
# basic information for scrapy cfg file

[settings]
default = instagram-scraper.settings

[deploy]
#url = http://localhost:6800/
project = tutorial
```

The first thing this file does is tell scrapy where to find the settings.py file in the `instagram-scraper` folder. The second line isn't even really needed, but these are the defaults when creating a new scrapy scraper, so we'll keep them for posterity.

## Running the scraper

If you look in the `instagram-scraper` folder, you'll notice the `spiders` subfolder. The `hashtag.py` file is the one that lays out how to interact with Instagram. We want Scrapy to use that file, so:

`$ scrapy crawl hashtag`

You will then be prompted to enter the target hashtag. The spider will then begin searching and scraping. Output prints to the terminal window and to file.

## Output

The output will be in a new folder, 'scraped' and subfolder, 'hashtag'. Each hashtag search will have its own subfolder, and the output file there will have its timestamp as its name. Each line in the output is json formatted. You can concatenate all of the files together with `cat * > output.json`. To make a properly formatted json file, open `output.json` in a text editor, add `,` to each line (except the last one), and put a `[` at the start of the file and a `]` at the end.

The data is now ready to be put into a database for further querying.

Deactivate your virtualenv:

`$ deactivate`
