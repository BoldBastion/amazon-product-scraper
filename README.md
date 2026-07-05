[Amazon Product Scraper](https://apify.com/scraply/amazon-product-scraper?fpr=data)

## Amazon Product Scraper

The Amazon Product Scraper is a fast, scalable web automation tool that collects structured product data directly from Amazon product and search pages. It solves the tedious, error-prone task of manually capturing titles, prices, ASINs, ratings, images, and seller details by turning any list of Amazon category or product URLs into clean records for analysis. Built for marketers, developers, data analysts, and researchers, this amazon product data scraper powers price tracking, catalog building, and competitive intelligence at scale — from single ASIN lookups to bulk category crawls.

## What data / output can you get?

The actor saves one dataset item per product. Below are key fields that the scraper extracts (as they appear in the output records), with examples for clarity. You can export results via the Apify UI or API to CSV, JSON, or Excel.

| Data type | Description | Example value |
| --- | --- | --- |
| asin | Product ASIN (extracted from URL) | "B08N5WRWNW" |
| title | Product name/title | "Logitech G915 TKL Wireless Mechanical Keyboard" |
| url | Canonical product page URL | "[https://www.amazon.com/dp/B08N5WRWNW](https://www.amazon.com/dp/B08N5WRWNW)" |
| price | Current price object | {"value": 159.99, "currency": "$"} |
| listPrice | Crossed/list price object (if present) | {"value": 199.99, "currency": "$"} |
| inStock | Availability boolean | true |
| inStockText | Availability text from page | "In Stock" |
| brand | Brand/store string | "Logitech" |
| stars | Average rating (float) | 4.6 |
| reviewsCount | Total number of reviews | 12457 |
| breadCrumbs | Category/breadcrumb path | "Electronics > Computers & Accessories > Keyboards" |
| thumbnailImage | Main image URL | "[https://m.media-amazon.com/images/I/....jpg](https://m.media-amazon.com/images/I/....jpg)" |
| galleryThumbnails | Array of gallery thumbnail URLs | ["[https://m.media-amazon.com/images/I/...jpg](https://m.media-amazon.com/images/I/...jpg)", "..."] |
| features | Bullet points from “About this item” | ["Lightspeed wireless...", "Low-profile mechanical..."] |
| productOverview | Key-value specs list | [{"key":"Connectivity","value":"Wireless"},{"key":"Color","value":"Black"}] |
| seller | Seller object (id, url, name, businessName, phone, address) | {"id":"A1ABCDEF12","url":"[https://www.amazon.com/sp?seller=A1ABCDEF12","name":"Acme](https://www.amazon.com/sp?seller=A1ABCDEF12%22,%22name%22:%22Acme) Co","businessName":null,"phone":null,"address":null} |
| bestsellerRanks | Array of BSR rankings (if found) | [{"rank":5,"category":"Computer Keyboards"}] |
| delivery | Estimated delivery date (parsed) | "Tuesday, May 12" |
| fastestDelivery | Fastest delivery date (parsed) | "Monday, May 11" |
| monthlyPurchaseVolume | Purchase velocity snippet | "3K bought in past month" |
| isAmazonChoice | Amazon’s Choice badge flag | true |
| amazonChoiceText | Amazon’s Choice badge text | "Amazon's Choice in Keyboards by Logitech" |

Bonus fields include: starsBreakdown (per-star histogram), visitStoreLink, galleryThumbnails, highResolutionImages, answeredQuestions, description, reviewsLink, hasReviews, returnPolicy, support, variantAsins, categoryPageData, locationText, loadedCountryCode, and more. Many fields can be null if Amazon does not display them for a given product/region.

## Key features

- 🚀 Concurrent scraping for speed — Configurable maxConcurrentRequests lets this amazon bulk product scraper collect many product pages in parallel for faster runs.
- 🧭 Category & search support — Start from Amazon search/category URLs or direct product pages; the actor discovers product links and scrapes detailed records.
- 💾 Structured JSON output — Every product is pushed to the dataset in real time with clean keys (e.g., asin, title, price, seller, bestsellerRanks) for easy BI integration.
- 🌍 Proxy country selection — Use Apify Proxy with residential IPs and optional proxyCountry to reduce blocking and target relevant listings for your region.
- 🎯 Fine-grained limits — Control maxItemsPerStartUrl and maxSearchPagesPerStartUrl to tune breadth vs. depth for your amazon listing scraper workflows.
- 🧱 Robust extraction — Captures pricing (price, listPrice, shippingPrice), availability, ratings, overview specs, image URLs, and seller signals to power amazon price scraper use cases.
- 🔌 API-friendly — Access runs and datasets programmatically as an amazon product scraper api on Apify; connect results to data pipelines or dashboards.
- 📤 Easy exports — Download results as JSON, CSV, or Excel; ideal for catalogs, analysis, and reporting with any amazon product data extractor workflow.

## How to use Amazon Product Scraper - step by step

1. 🔑 Sign in to Apify

- Create a free Apify account or log in to your dashboard.
2. 🔎 Find the actor

- Search for “Amazon Product Scraper” and open the actor page.
3. 📥 Add input data

- In “categoryOrProductUrls”, paste Amazon search/category URLs (e.g., [https://www.amazon.com/s?k=keyboard](https://www.amazon.com/s?k=keyboard)) or product URLs (e.g., [https://www.amazon.com/dp/B08N5WRWNW](https://www.amazon.com/dp/B08N5WRWNW)).
- The array accepts plain URL strings or objects with a url key, for example: {"url":"[https://www.amazon.com/dp/ASIN"}](https://www.amazon.com/dp/ASIN%22%7D).
4. ⚙️ Configure options (optional)

- maxItemsPerStartUrl to limit products per start URL.
- maxSearchPagesPerStartUrl to control pagination depth.
- proxyCountry to guide geo-targeting; keep default for auto-selection.
- maxConcurrentRequests to control parallelism.
- scrapeProductDetails to toggle detailed product-page extraction.
5. ▶️ Run the actor

- Click Start. Products are extracted automatically.
- Items are saved to the dataset in real time as each product is found.
6. 📊 Download results

- Open the run’s Dataset and export to JSON, CSV, or Excel — or fetch via the Apify API.

Pro tip: Chain this amazon product scraping tool into your analytics stack. With the Apify API, you can run this amazon product scraper python-style from your codebase and sync results into a warehouse or price monitoring dashboard.

## Use cases

| Use case | Description |
| --- | --- |
| E‑commerce price monitoring | Track live prices, listPrice changes, and availability as part of an amazon price monitoring tool. Automate alerts when competitors change pricing. |
| Market research & trend analysis | Analyze stars, reviewsCount, bestsellerRanks, and monthlyPurchaseVolume across categories with an amazon product catalog scraper. |
| Catalog enrichment | Build a structured product catalog with asin, title, brand, features, productOverview, and images using an amazon product data extractor workflow. |
| ASIN mapping & validation | Use this amazon asin scraper to normalize products (asin, url, brand) and connect them to internal SKUs or listings. |
| Competitive benchmarking | Compare brands, “Amazon’s Choice” flags, and seller metadata at scale using an amazon listing scraper. |
| Data pipelines & RPA | Integrate the amazon product scraper api into ETL pipelines for bulk aggregation, reporting, or downstream ML features. |

## Why choose Amazon Product Scraper?

This actor focuses on precision and scale, delivering reliable product records without the hassle of unstable alternatives.

- ✅ Accurate field coverage: Prices, availability, ratings, ASINs, images, features, and seller details extracted from product pages.
- ⚡ Scalable concurrency: Tune maxConcurrentRequests to speed up bulk runs for thousands of items in a single workflow.
- 💾 Integration-ready JSON: Structured keys and stable schema make it easy to plug into BI, data lakes, or automation scripts.
- 🌍 Proxy & region-aware: Built-in Apify Proxy support with optional proxyCountry for better relevance and lower blocking.
- 🔐 Platform reliability: Production-ready infrastructure on Apify — export CSV/JSON, schedule runs, and track changes over time.
- 💻 Developer friendly: Run via UI or programmatically; ideal for teams building an amazon product scraper python integration or API pipeline.

## Is it legal / ethical to use Amazon Product Scraper?

Yes — when used responsibly. This actor collects publicly available product information (e.g., prices, titles, ratings) and does not access private or authenticated data.

Follow these guidelines:

- Only scrape publicly available pages and product data.
- Respect platform terms and local regulations (e.g., GDPR/CCPA where applicable).
- Avoid collecting sensitive or personal data.
- Use data for legitimate purposes such as research, analytics, and price comparison.
- Consult your legal team for compliance in your jurisdiction and specific use case.

## Input parameters & output format

Example JSON input

```
{
  "categoryOrProductUrls": [
    "https://www.amazon.com/s?k=keyboard",
    "https://www.amazon.com/dp/B08N5WRWNW"
  ],
  "maxItemsPerStartUrl": 100,
  "maxSearchPagesPerStartUrl": 5,
  "maxConcurrentRequests": 10,
  "proxyCountry": "AUTO_SELECT_PROXY_COUNTRY",
  "scrapeProductDetails": true,
  "proxyConfiguration": {
    "useApifyProxy": true,
    "apifyProxyGroups": ["RESIDENTIAL"]
  }
}
```

Parameters

- categoryOrProductUrls (array)

- Description: Enter one or more Amazon category or product URLs. You can filter within categories using Amazon filters. You can choose different Amazon country domains by using a different URL.
- Default: not set (prefill example provided)
- Required: Yes
- maxItemsPerStartUrl (integer)

- Description: Maximum number of results to scrape per start URL.
- Default: 100
- Required: No
- language (string, nullable)

- Description: Language to use on Amazon. If unsupported by the domain, the default language is used.
- Default: not set
- Required: No
- proxyCountry (string)

- Description: Select a proxy country to avoid geo-blocking and access region-specific content. Automatic selection is the default.
- Default: "AUTO_SELECT_PROXY_COUNTRY"
- Required: No
- maxSearchPagesPerStartUrl (integer)

- Description: Maximum number of search pages to scrape per start URL.
- Default: 9999
- Required: No
- maxProductVariantsAsSeparateResults (integer)

- Description: Maximum number of product variants to scrape as separate results.
- Default: not set
- Required: No
- maxOffers (integer)

- Description: Maximum number of offers to scrape per product.
- Default: 0
- Required: No
- scrapeSellers (boolean)

- Description: If enabled, extracts further information about sellers. Works with maxOffers; with maxOffers=0, only the featured offer seller is scraped.
- Default: false
- Required: No
- ensureLoadedProductDescriptionFields (boolean)

- Description: Force-load seller-editable description fields (e.g., description, aPlusContent, attributes). Increases requests and may extend scraping time.
- Default: false
- Required: No
- useCaptchaSolver (boolean)

- Description: Automatically solve captchas. Works well primarily on .com; some fields may be missing after solving (attributes, manufacturer attributes, bestseller ranks).
- Default: false
- Required: No
- scrapeProductVariantPrices (boolean)

- Description: Extract prices of different product variations. Increases requests and scraping time.
- Default: false
- Required: No
- scrapeProductDetails (boolean)

- Description: If enabled, extracts detailed data for each product found on category/search pages. If disabled, only quick product info is extracted.
- Default: true
- Required: No
- maxConcurrentRequests (integer)

- Description: Number of concurrent product page requests.
- Default: 10 (min 1, max 20)
- Required: No
- countryCode (string, nullable)

- Description: Country code for delivery location settings.
- Default: not set
- Required: No
- zipCode (string, nullable)

- Description: Zip code for delivery location settings.
- Default: not set
- Required: No
- locationDeliverableRoutes (array)

- Description: Routes/page types where deliverable location settings should be applied. Useful to speed up scraping by limiting localization to specific pages.
- Default: ["PRODUCT", "SEARCH", "OFFERS"]
- Required: No
- proxyConfiguration (object)

- Description: Apify proxy settings. Use residential proxies for best results and fewer blocks.
- Default: not set (editor prefill: {"useApifyProxy": true, "apifyProxyGroups": ["RESIDENTIAL"]})
- Required: No

Output

- Dataset: One item per product is pushed in real time with the following structure (fields may be null if not present on the page).
- Key-value store (key: OUTPUT): A single JSON object summarizing the run, including stats and the full list of products.

Example dataset item

```
{
  "title": "Logitech G915 TKL Wireless Mechanical Keyboard",
  "url": "https://www.amazon.com/dp/B08N5WRWNW",
  "asin": "B08N5WRWNW",
  "originalAsin": "B08N5WRWNW",
  "price": { "value": 159.99, "currency": "$" },
  "inStock": true,
  "inStockText": "In Stock",
  "listPrice": { "value": 199.99, "currency": "$" },
  "brand": "Logitech",
  "author": null,
  "shippingPrice": { "value": 0.00, "currency": "$" },
  "stars": 4.6,
  "starsBreakdown": { "1star": 0.04, "2star": 0.03, "3star": 0.07, "4star": 0.23, "5star": 0.63 },
  "reviewsCount": 12457,
  "answeredQuestions": 123,
  "breadCrumbs": "Electronics > Computers & Accessories > Keyboards",
  "videosCount": 0,
  "visitStoreLink": { "text": "Visit the Logitech Store", "url": "https://www.amazon.com/stores/Logitech" },
  "thumbnailImage": "https://m.media-amazon.com/images/I/....jpg",
  "galleryThumbnails": ["https://m.media-amazon.com/images/I/...jpg"],
  "highResolutionImages": ["https://m.media-amazon.com/images/I/..._SL1500_.jpg"],
  "importantInformation": null,
  "sustainabilityFeatures": null,
  "description": "Low-profile mechanical switches... Lightspeed wireless...",
  "features": ["Lightspeed wireless...", "Low-profile mechanical..."],
  "attributes": [],
  "productOverview": [
    { "key": "Connectivity", "value": "Wireless" },
    { "key": "Color", "value": "Black" }
  ],
  "variantAsins": ["B08XYZ1234"],
  "variantDetails": [],
  "reviewsLink": "/product-reviews/B08N5WRWNW?reviewerType=all_reviews",
  "hasReviews": true,
  "delivery": "Tuesday, May 12",
  "fastestDelivery": "Monday, May 11",
  "returnPolicy": "Eligible for return, refund or replacement within 30 days of receipt.",
  "support": null,
  "variantAttributes": [],
  "manufacturerAttributes": [],
  "seller": {
    "id": "A1ABCDEF12",
    "url": "https://www.amazon.com/sp?seller=A1ABCDEF12",
    "name": "Acme Co",
    "businessName": null,
    "phone": null,
    "address": null
  },
  "bestsellerRanks": [{ "rank": 5, "category": "Computer Keyboards" }],
  "isAmazonChoice": true,
  "amazonChoiceText": "Amazon's Choice in Keyboards by Logitech",
  "bookDescription": null,
  "priceRange": null,
  "aPlusContent": null,
  "brandStory": null,
  "productComparison": null,
  "aiReviewsSummary": null,
  "monthlyPurchaseVolume": "3K bought in past month",
  "productPageReviews": [],
  "productPageReviewsFromOtherCountries": [],
  "locationText": "Deliver to New York 10001",
  "loadedCountryCode": "US",
  "offers": [],
  "unNormalizedProductUrl": "https://www.amazon.com/s?k=keyboard",
  "categoryPageData": {
    "pageNumber": 1,
    "saleSummary": null,
    "isSponsored": false,
    "bestsellerBadge": null,
    "productPosition": 1
  },
  "input": "https://www.amazon.com/s?k=keyboard"
}
```

Example OUTPUT object (key-value store)

```
{
  "status": "success",
  "scrapedAt": "2026-04-03T18:35:38.783Z",
  "duration": "111.31s",
  "stats": {
    "totalProducts": 100,
    "totalErrors": 0,
    "urlsProcessed": 2
  },
  "products": [ { "asin": "B08N5WRWNW", "title": "…", "url": "…", "price": { "value": 159.99, "currency": "$" }, "...": "..." } ],
  "errors": null
}
```

Note: Some fields can be null if Amazon hides content or it’s not applicable to a product. The actor pushes each product to the dataset as soon as it’s parsed, so you’ll see items streaming in during the run.

## FAQ

### Is there a free Amazon Product Scraper option?

Yes. This actor includes 120 free trial minutes on Apify so you can test scraping and evaluate output before upgrading. You can then continue with the monthly plan or pay per platform usage.

### Can I run it via an API or from code?

Yes. Every Apify actor exposes a REST API. You can start runs, pass input, and download datasets programmatically — perfect for building an amazon product scraper api workflow or integrating with an amazon product scraper python script.

### Does it work on search/category pages and product pages?

Yes. Provide Amazon search/category URLs to collect multiple product links, or direct product URLs for single-item detail extraction. Use maxItemsPerStartUrl and maxSearchPagesPerStartUrl to control scope.

### Can it scrape reviews text?

It captures review signals like stars and reviewsCount and provides a reviewsLink for the “all reviews” page. Full review text is not included in the dataset items produced by this actor.

### Does it support proxies and geo-targeting?

Yes. Use proxyConfiguration with Apify residential proxies and set proxyCountry to reduce blocks and target region-specific content. By default, the proxy country is selected automatically.

### Is there a Chrome extension?

No. This is an Apify actor (cloud-based). You control it via the Apify UI or API, then export results to CSV/JSON/Excel — a more reliable approach than an amazon product scraper chrome extension for bulk runs.

### How many products can I scrape per run?

It depends on your input and limits. Configure maxItemsPerStartUrl and maxSearchPagesPerStartUrl, and tune maxConcurrentRequests for throughput. The actor streams each product as soon as it’s parsed, making it suitable for large batches in an amazon bulk product scraper workflow.

### Which data fields are guaranteed?

Fields depend on page availability. Common fields like asin, title, url, price, inStock, brand, stars, reviewsCount, thumbnailImage, breadCrumbs, and seller are widely available; other fields may be null if not present on a given page.

## Final thoughts

The Amazon Product Scraper is built for scalable, structured product data extraction from Amazon. With concurrency controls, proxy support, and clean JSON records, it’s ideal for price tracking, catalog enrichment, and competitive analysis. Teams across marketing, analytics, and engineering can run it from the Apify UI or via API, export to CSV/JSON/Excel, and plug results straight into dashboards or pipelines. Start extracting smarter, high-quality Amazon product data today.