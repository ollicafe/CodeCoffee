---
tags:
  - Python
  - Web-Scrape
  - Web-Scraping
  - Web-Dev
  - Web
---
# Intro
A [[Python]] library used for #Web-Scraping , implemented by 

# Installing
To install Scrapy, you can use [[pip]]
```
pip install scrapy
```

And you can test if Scrapy is installed with `scrapy` and you should get an output like this:
```
$ scrapy

Usage:
  scrapy <command> [options] [args]

Available commands:
  bench         Run quick benchmark test
  check         Check spider contracts
  commands
  crawl         Run a spider
  edit          Edit spider
  fetch         Fetch a URL using the Scrapy downloader
  genspider     Generate new spider using pre-defined templates
  list          List available spiders
  parse         Parse URL (using its spider) and print the results
  runspider     Run a self-contained spider
```
# Starting The Project
The command line syntax to begin the project is this:
```
scrapy startproject <project_name>
```
This will create a template project for us to use. The template includes the following:
- **settings.py** is where all your project settings are contained.
- **items.py** is a model for the extracted data.
- **pipelines.py** is where the item yielded by the spider gets passed, it’s mostly used to clean the text and connect to file outputs or databases (CSV, JSON SQL, etc).
- **middlewares.py** is useful when you want to modify how the request is made and scrapy handles the response.
- **scrapy.cfg** is a configuration file to change some deployment settings, etc.

# Creating a Spider
There are different types of spiders
- **Spider** - Takes a list of URLs and scrapes each one
- **CrawlerSpider** - Designed to crawl an entire website by following any link it can find
- **SiteMapSpider** - Designed to extract URLs from a sitemap

## Create Spider
To make a new generic spider, run the `genspider` command:
```
scrapy genspider <name_of_spider> <website>
```
You will now have a new spider in your spider folder. It should look like this:
```Python
import scrapy

class SpiderName(scrapy.Spider):
    name = "Name of Spider" 
    allowed_domains = ["Website URL"]
    start_urls = ["Website URL"]

    def parse(self, response):
        pass
```

- **name** - The name we refer to the spider with
- **allowed_domains** - Defines to Scrapy that is should only scrape pages of the listed URLs. This prevents the spider from going rogue and scraping unnecessary websites.
- **start_urls** - Tells Scrapy the first URL to scrape
- **parse** - parses after a response is received from the webpage

# Scrapy Shell
Scrapy Shell lets you test out functions from Scrapy, to use do `scrapy shell`, it will output something like this:
```
[s] Available Scrapy objects:
[s]   scrapy     scrapy module (contains scrapy.Request, scrapy.Selector, etc)
[s]   crawler    <scrapy.crawler.Crawler object at 0x0000023CE27864F0>
[s]   item       {}
[s]   settings   <scrapy.settings.Settings object at 0x0000023CE2786880>
[s] Useful shortcuts:
[s]   fetch(url[, redirect=True]) Fetch URL and update local objects (by default, redirects are followed)
[s]   fetch(req)                  Fetch a scrapy.Request and update local objects
[s]   shelp()           Shell help (print this help)
[s]   view(response)    View response in a browser
>>>
```

# Running our project
To run a project, go to the top level of the project and return the following command:
```
scrapy crawl <name_of_spider>
```

And to make it output to a file:
```
scrapy crawl <name_of_spider> -O <name_of_file>
```

Make sure the file extension is included for whatever file type we want.
Supported file types:

# Selector
This part is so confusing