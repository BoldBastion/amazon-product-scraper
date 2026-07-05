[Amazon Product Scraper](https://apify.com/apivault_labs/amazon-product-scraper?fpr=data)

# Amazon Product Scraper

Scrape Amazon product data in real-time. Get prices, ratings, reviews, availability, and more.

## Features

- **Real-time data** — Fresh product information, not cached
- **Multiple regions** — Works with amazon.com, amazon.co.uk, amazon.de, etc.
- **Flexible input** — Accept full URLs or just ASINs
- **Customizable fields** — Choose which data to extract
- **Parallel processing** — Scrape multiple products simultaneously

## Input

| Field | Type | Description |
| --- | --- | --- |
| productUrls | array | List of Amazon product URLs or ASINs |
| extractName | boolean | Extract product name (default: true) |
| extractPrice | boolean | Extract current price (default: true) |
| extractOriginalPrice | boolean | Extract original price before discount (default: true) |
| extractRating | boolean | Extract product rating (default: true) |
| extractReviews | boolean | Extract reviews count (default: true) |
| extractDescription | boolean | Extract product description (default: true) |
| extractBrand | boolean | Extract brand name (default: true) |
| extractCategory | boolean | Extract category (default: true) |
| extractASIN | boolean | Extract ASIN (default: true) |
| extractAvailability | boolean | Extract stock status (default: true) |
| extractSeller | boolean | Extract seller name (default: true) |
| extractImage | boolean | Extract main image URL (default: true) |
| maxConcurrency | integer | Parallel requests (default: 3) |
| timeout | integer | Timeout per product in seconds (default: 120) |

## Output

```
{
  "success": true,
  "inputUrl": "https://www.amazon.com/dp/B0BSHF7WHW",
  "productName": "Apple 2023 MacBook Pro Laptop M2 Pro",
  "price": "$1,854.30",
  "originalPrice": "$1,999.00",
  "rating": 4.7,
  "reviewsCount": 482,
  "brand": "Apple",
  "asin": "B0BSHF7WHW",
  "availability": "In Stock",
  "seller": "Amazon.com",
  "category": "Electronics",
  "imageUrl": "https://m.media-amazon.com/images/...",
  "productUrl": "https://www.amazon.com/dp/B0BSHF7WHW"
}
```

## Supported URL Formats

- Full URL: `https://www.amazon.com/dp/B0BSHF7WHW`
- Short URL: `https://amzn.to/xxxxx`
- ASIN only: `B0BSHF7WHW`
- Product page: `https://www.amazon.com/Apple-MacBook-Pro/dp/B0BSHF7WHW`

## Use Cases

- Price monitoring and tracking
- Competitor analysis
- Product research
- Inventory monitoring
- Market analysis