[Amazon Product Scraper](https://apify.com/focused_vanguard/amazon-product-scraper?fpr=data)

# Amazon Product Scraper - Price & Inventory API

Scrape Amazon products by ASIN, keyword, or URL. Get prices, Prime status, stock levels, ratings, Best Seller Rank, and more. Perfect for **price monitoring**, **competitor analysis**, and **market research**.

## Features

- **Multiple input modes**:

- Search by keyword
- Direct ASIN lookup
- Product URL input
- **Rich data extraction**:

- Product title and ASIN
- Current and original prices
- Prime eligibility
- Stock status
- Rating and review count
- Best Seller Rank (BSR)
- Brand information
- Feature bullet points
- Product images
- **Multi-marketplace support**: amazon.com, .co.uk, .de, .fr, .es, .it, .ca, .au, .jp, .in
- **Filtering**: By rating, Prime-only

## Use Cases

### Price Monitoring

Track competitor prices over time. Run scheduled scrapes to detect price changes.

### Competitor Analysis

See what products competitors are selling and their pricing strategies.

### Market Research

Find best-selling products in any category using BSR data.

### Affiliate Marketing

Get product data for affiliate sites and comparison tools.

## Input

| Field | Type | Description |
| --- | --- | --- |
| `searchMode` | string | `keyword`, `asin`, or `urls` |
| `keywords` | string | Search keywords (one per line) |
| `asins` | string | ASINs (one per line) |
| `productUrls` | string | Product URLs (one per line) |
| `maxProducts` | number | Max products per keyword (default: 30) |
| `amazonDomain` | string | Marketplace domain (e.g., amazon.com) |
| `minRating` | number | Minimum rating filter (0-5) |
| `primeOnly` | boolean | Only Prime products |

### Example Input

```
{
  "searchMode": "asin",
  "asins": "B09JQL3NWT\nB08N5WRWNW",
  "amazonDomain": "amazon.com"
}
```

## Output

Each product includes:

```
{
  "asin": "B09JQL3NWT",
  "title": "Apple AirPods Pro (2nd Generation)...",
  "url": "https://www.amazon.com/dp/B09JQL3NWT",
  "price": {
    "amount": 189.99,
    "currency": "$",
    "originalAmount": 249.00,
    "savings": "24% off",
    "isPrimePrice": true
  },
  "stock": "in_stock",
  "isPrime": true,
  "deliveryEstimate": "FREE delivery Tomorrow",
  "rating": 4.7,
  "reviewCount": 125430,
  "bestSellerRank": 1,
  "bestSellerCategory": "Electronics",
  "brand": "Apple",
  "features": ["Active Noise Cancellation", "..."],
  "images": ["https://m.media-amazon.com/images/..."],
  "source": "amazon",
  "domain": "amazon.com",
  "scrapedAt": "2026-01-19T21:00:00.000Z"
}
```

## Pricing

**Pay per product scraped**: $0.003 per product

| Volume | Cost |
| --- | --- |
| 100 products | $0.30 |
| 1,000 products | $3.00 |
| 10,000 products | $30.00 |

## Tips

1. **Use ASIN mode for best results** - Direct ASIN lookups are most reliable
2. **Respect rate limits** - Amazon has strict anti-bot measures
3. **Use Apify proxies** - Essential for reliable scraping
4. **Check multiple marketplaces** - Prices vary by region

## Important Notes

- Amazon actively blocks automated scraping
- Using Apify's proxy infrastructure is recommended
- Some pages may require residential proxies for full data extraction
- Results may vary based on product availability and region

## Related Actors

- AliExpress Product Scraper
- Walmart Product Scraper

---

**Keywords**: amazon scraper, amazon api, amazon price tracker, asin lookup, amazon data, ecommerce scraper, price monitoring, amazon crawler, product research