# playwright-scrape-api

Simple scraping API based on playwright.
It creates a REST API scrape endpoint to return the content of a page.

It runs in docker.

It is inspired from the Typescript version of [Firecrawl](https://github.com/mendableai/firecrawl/tree/main/apps/playwright-service-ts) and it is 100% compatible with it.

Improvements:
* better domain blocking handling
* better media blocking handling
* scrape multiple pages in parallel
* scrape endpoint compatible with Firecrawl API
* return cleaned html and markdown
* uses https://github.com/Kaliiiiiiiiii-Vinyzu/patchright-python instead of playwright

## Env vars
* `ADS_BLOCKED_DOMAINS`: list of domains to block
* `ADS_BLOCKLIST_URL`: url to a domain blocklist. For example: https://raw.githubusercontent.com/hagezi/dns-blocklists/main/domains/light.txt
* `ADS_BLOCKLIST_PATH`: path to a domain blocklist. For example blocklist.txt
* `BLOCK_MEDIA`: true or false. If true, blocks media.

* `PROXY_SERVER`: adress of the proxy server
* `PROXY_USERNAME`: username of the proxy server
* `PROXY_PASSWORD`: password of the proxy server

## Endpoints
* `/scrape`
  - url: url to scrape
  - wait_after_load: time in ms to wait after the page is loaded. Default: 0
  - timeout: time in ms before timeout. Default: 15000
  - headers: Specific headers to add = Default: None
* `/v1/scrape`
  - url: url to scrape
  - waitFor: time in ms to wait after the page is loaded. Default: 0
  - timeout: time in ms before timeout. Default: 15000
  - headers: Specific headers to add = Default: None
  - formats: List of formats to include in the output: markdown, html, rawHtml : Default : ["markdown"]
  - **needs [html-to-markdown cli](https://github.com/JohannesKaufmann/html-to-markdown) for Markdown output**
* `/scrape_multiple`
  - urls: a list of urls to scrape
  - wait_after_load: time in ms to wait after the page is loaded. Default: 0
  - timeout: time in ms before timeout. Default: 15000
  - headers: Specific headers to add = Default: None
 
