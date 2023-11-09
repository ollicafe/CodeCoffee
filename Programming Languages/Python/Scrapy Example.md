---
tags:
  - Python
---
An example using [[Scrapy]] made by following this guide: [Scrapy Beginner's Series Part 1](https://scrapeops.io/python-scrapy-playbook/scrapy-beginners-guide/#step-2---setup-our-scrapy-project). This is a quick run-through of the tutorial without going too in-depth on the reasoning

# Starting
Using a [[Virtual Environment]] in [[Visual Studio Code]], we start the project with the following command
```
scrapy startproject chocolatescraper
```
This will make our project template we use

# Create Spider
To make the spider for the project, use the `genspider` command:
```
scrapy genspider chocolatespider chocolate.co.uk
```
Which will yield a spider file in the spider folder that looks like this:
```Python
import scrapy

class ChocolatespiderSpider(scrapy.Spider):
    name = 'chocolatespider'
    allowed_domains = ['chocolate.co.uk']
    start_urls = ['http://chocolate.co.uk/']

    def parse(self, response):
        pass

```
and then we change the URL we will be starting with for this project:
```Python
import scrapy

class ChocolatespiderSpider(scrapy.Spider):
    name = 'chocolatespider'
    allowed_domains = ['chocolate.co.uk']
    start_urls = ['https://www.chocolate.co.uk/collections/all']

    def parse(self, response):
        pass
```

# Getting Our Selectors
We get our selectors by inspecting the page to find elements we want to scrape for, in this example we are getting the products and then getting the name, price, and URL of the product. The ending code should look like this:
```Python
import scrapy 

class ChocolatespiderSpider(scrapy.Spider):

    #the name of the spider
    name = 'chocolatespider'

    #the url of the first page that we will start scraping
    start_urls = ['https://www.chocolate.co.uk/collections/all']

    def parse(self, response):

        #here we are looping through the products and extracting the name, price & url
        products = response.css('product-item')
        for product in products:
            #here we put the data returned into the format we want to output for our csv or json file
            yield{
                'name' : product.css('a.product-item-meta__title::text').get(),
                'price' : product.css('span.price').get().replace('<span class="price">\n              <span class="visually-hidden">Sale price</span>','').replace('</span>',''),
                'url' : product.css('div.product-item-meta a').attrib['href'],
            }
```

# Running the Spider
To get our spider to run, we do the following command:
```
scrapy crawl chocolatespider
```
If we want to save the data to a CSV file, we do 
```
scrapy crawl chocolatespider -O myscrapeddata.csv
```

