[Amazon Product Scraper](https://apify.com/sovereigntaylor/amazon-product-scraper?fpr=data)

# Amazon Product Scraper

Scrape Amazon product listings, prices, ratings, reviews, and seller data. Monitor prices, track competitors, research products, and build e-commerce databases. Works with Amazon.com with structured JSON output.

## Why This Actor?

- **Complete product data** — Titles, prices, ratings, reviews, ASINs, images, Prime status, and more
- **Price monitoring** — Track price changes over time with scheduled runs
- **Competitor intelligence** — Compare your products against the competition
- **Pay per result** — Only charged for successfully scraped products
- **E-commerce ready** — Structured output for FBA research, dropshipping, and retail arbitrage

## Features

- Search products by keyword on Amazon
- Extract 20+ data fields per product
- Get current price, original price, and discount percentage
- Capture ratings, review counts, and Best Seller Rank
- Prime eligibility and shipping information
- Seller name and marketplace data
- Product images (main + thumbnails)
- ASIN for direct product identification
- Sort by relevance, price, reviews, or newest
- Configurable result limits
- Proxy support for reliable scraping

## Input Parameters

| Field | Type | Default | Description |
| --- | --- | --- | --- |
| `searchTerm` | string | *required* | Product search keyword (e.g., "wireless headphones", "running shoes") |
| `maxResults` | number | `20` | Maximum products to return (1-500) |
| `sortBy` | string | `"relevance"` | Sort order: `relevance`, `price-asc`, `price-desc`, `avg-review`, `newest` |

## Output Example

```
{
  "title": "Sony WH-1000XM5 Wireless Noise Canceling Headphones",
  "price": "$348.00",
  "originalPrice": "$399.99",
  "discount": "13% off",
  "rating": 4.7,
  "reviewCount": 12543,
  "asin": "B0BX2L8PBS",
  "image": "https://m.media-amazon.com/images/I/51aYEHXCYlL._AC_SL1500_.jpg",
  "isPrime": true,
  "isBestSeller": false,
  "seller": "Amazon.com",
  "url": "https://amazon.com/dp/B0BX2L8PBS",
  "category": "Electronics > Headphones",
  "availability": "In Stock",
  "scrapedAt": "2026-03-02T10:30:00Z"
}
```

## Use Cases

### Price Monitoring & Alerts

Track prices for products you sell or plan to buy. Schedule daily runs and detect price drops, deals, and competitor price changes.

**Example:** Monitor laptop prices:

```
{
  "searchTerm": "gaming laptop",
  "maxResults": 100,
  "sortBy": "price-asc"
}
```

### Amazon FBA Product Research

Find winning products for your FBA business. Analyze demand (review counts), competition (number of sellers), and pricing in any category.

**Example:** Research trending products:

```
{
  "searchTerm": "phone accessories",
  "maxResults": 200,
  "sortBy": "avg-review"
}
```

### Competitor Analysis

Track competitor products, their pricing strategy, and customer reception. Compare ratings and review counts across similar products.

### Dropshipping Research

Find products with high demand and good margins. Filter by price range, reviews, and Prime eligibility to identify opportunities.

### Market Intelligence

Build product databases for analytics. Track category trends, seasonal pricing patterns, and product lifecycle data.

### Retail Arbitrage

Compare Amazon prices with other marketplaces to find arbitrage opportunities for reselling.

## Integration Examples

### Python

```
from apify_client import ApifyClient

client = ApifyClient('YOUR_API_TOKEN')
run = client.actor('sovereigntaylor/amazon-product-scraper').call(run_input={
    'searchTerm': 'wireless earbuds',
    'maxResults': 50,
    'sortBy': 'avg-review'
})

for item in client.dataset(run['defaultDatasetId']).iterate_items():
    print(f"{item['title']}: {item['price']} ({item['rating']} stars)")
```

### JavaScript

```
const { ApifyClient } = require('apify-client');
const client = new ApifyClient({ token: 'YOUR_API_TOKEN' });

const run = await client.actor('sovereigntaylor/amazon-product-scraper').call({
    searchTerm: 'wireless earbuds',
    maxResults: 50,
    sortBy: 'avg-review'
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
items.forEach(item => console.log(`${item.title}: ${item.price}`));
```

### Google Sheets

Use Apify's Google Sheets integration to export results directly to a spreadsheet. Set up a scheduled run for automatic daily updates.

## FAQ

**Which Amazon domains are supported?**
Currently Amazon.com. International domains coming soon.

**How often can I scrape?**
As often as you need — daily, hourly, or on-demand. Use Apify's scheduler for automated recurring runs.

**Is this legal?**
This actor extracts publicly available data from Amazon. Please review Amazon's Terms of Service and your local regulations regarding web scraping.

**Can I track specific ASINs?**
Yes, use specific product URLs or ASINs as search terms to monitor exact products.

**What about Amazon product detail pages?**
This actor extracts data from search results. For deep product page data, check our [Amazon Reviews Scraper](https://apify.com/sovereigntaylor/amazon-reviews-scraper).

## Pricing

Pay per result — you're only charged for each product successfully scraped. No subscriptions, no minimums. See the Pricing tab for details.

## Related Actors

- [Amazon Reviews Scraper](https://apify.com/sovereigntaylor/amazon-reviews-scraper) — Extract customer reviews for any Amazon product
- [Amazon BSR Tracker](https://apify.com/sovereigntaylor/amazon-bsr-tracker) — Track Best Seller Rank over time
- [Amazon Keyword Tracker](https://apify.com/sovereigntaylor/amazon-keyword-tracker) — Monitor keyword rankings on Amazon
- [eBay Scraper](https://apify.com/sovereigntaylor/ebay-scraper) — Compare with eBay marketplace data
- [Walmart Scraper](https://apify.com/sovereigntaylor/walmart-scraper) — Cross-marketplace price comparison