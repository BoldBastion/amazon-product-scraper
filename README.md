[Amazon Product Scraper](https://apify.com/muffin/amazon-product-scraper?fpr=data)

# Amazon Product Scraper -- Real-Time Price, Reviews & Product Data API

Scrape any Amazon product by ASIN. Returns price, rating, reviews count, seller info, buybox status, BSR, images, features, and 25+ structured fields. Works across 10 Amazon marketplaces with native currency support.

## Key Capabilities

- **25+ structured fields** per product including price, rating, reviews, seller, buybox, BSR, images, variants, and more.
- **10 Amazon marketplaces** -- US, UK, DE, FR, IT, ES, JP, CA, BR, MX with correct local currency (USD, GBP, EUR, JPY, CAD, BRL, MXN).
- **Real-time data** -- results in 2-5 seconds per product. No stale cache.
- **Browser-grade stealth** -- real browser fingerprints, locale-aware sessions, automatic anti-bot handling. 99%+ success rate.
- **Pay per result** -- no idle compute costs. You pay only for successfully scraped products.

## How It Works

1. Pass one or more Amazon ASINs and a country code.
2. The Actor scrapes each product page in real time.
3. Structured data (25+ fields) is pushed to the Apify dataset.
4. Download results as JSON, CSV, Excel, or access via API.

### Input Example

```
{
    "asins": ["B0CHWRXH8B", "B09V3KXJPB", "B07FZ8S74R"],
    "country": "US"
}
```

You can also pass ASINs as a comma-separated string:

```
{
    "asins": "B0CHWRXH8B, B09V3KXJPB, B07FZ8S74R",
    "country": "DE"
}
```

## Supported Marketplaces

| Country | Domain | Code |
| --- | --- | --- |
| United States | amazon.com | US |
| United Kingdom | amazon.co.uk | UK |
| Germany | amazon.de | DE |
| France | amazon.fr | FR |
| Italy | amazon.it | IT |
| Spain | amazon.es | ES |
| Japan | amazon.co.jp | JP |
| Canada | amazon.ca | CA |
| Brazil | amazon.com.br | BR |
| Mexico | amazon.com.mx | MX |

## Output Schema

Every product result includes 25+ structured fields:

```
{
    "asin": "B0CHWRXH8B",
    "title": "Apple AirPods Pro 2 Wireless Earbuds, USB-C Charging",
    "brand": "Apple",
    "price": 189.99,
    "currency": "USD",
    "original_price": 249.99,
    "rating": 4.7,
    "reviews_count": 67432,
    "availability": "In Stock",
    "seller_name": "Amazon.com",
    "seller_id": "ATVPDKIKX0DER",
    "is_prime": true,
    "is_buybox_winner": true,
    "is_amazon_choice": true,
    "is_best_seller": false,
    "bestseller_rank": 1,
    "bestseller_category": "Electronics",
    "main_image": "https://m.media-amazon.com/images/I/61SUj2aKoEL._AC_SL1500_.jpg",
    "images": ["..."],
    "features": ["INTELLIGENT NOISE CANCELLATION -- ...", "..."],
    "description": "AirPods Pro 2 feature up to 2x more Active Noise Cancellation...",
    "categories": ["Electronics", "Headphones", "Earbud Headphones"],
    "parent_asin": "B0BDHWDR12",
    "country": "US",
    "url": "https://www.amazon.com/dp/B0CHWRXH8B",
    "scraped_at": "2026-04-12T14:32:07Z"
}
```

### Field Reference

| Field | Type | Description |
| --- | --- | --- |
| asin | string | Amazon Standard Identification Number |
| title | string | Full product title |
| brand | string | Brand name |
| price | number | Current selling price |
| currency | string | Currency code (USD, GBP, EUR, etc.) |
| original_price | number | List price before discount (null if none) |
| rating | number | Average star rating (1.0-5.0) |
| reviews_count | integer | Total number of customer reviews |
| availability | string | Stock status text |
| seller_name | string | Seller/merchant name |
| seller_id | string | Amazon seller ID |
| is_prime | boolean | Prime delivery eligible |
| is_buybox_winner | boolean | Whether this offer holds the buybox |
| is_amazon_choice | boolean | Amazon's Choice badge |
| is_best_seller | boolean | Best Seller badge |
| bestseller_rank | integer | Best Sellers Rank (BSR) |
| bestseller_category | string | BSR category |
| main_image | string | Primary product image URL |
| images | array | All product image URLs |
| features | array | Bullet point feature list |
| description | string | Product description text |
| categories | array | Category breadcrumb path |
| parent_asin | string | Parent ASIN for variations |
| country | string | Marketplace country code |
| url | string | Full product page URL |
| scraped_at | string | ISO 8601 timestamp of the scrape |

## Integration Examples

### Python (Apify Client)

```
from apify_client import ApifyClient

client = ApifyClient("YOUR_API_TOKEN")

run = client.actor("muffin/amazon-product-scraper").call(
    run_input={
        "asins": ["B0CHWRXH8B", "B09V3KXJPB"],
        "country": "US",
    }
)

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(f"{item['asin']}: {item['title']} -- ${item['price']}")
```

### JavaScript (Apify Client)

```
import { ApifyClient } from "apify-client";

const client = new ApifyClient({ token: "YOUR_API_TOKEN" });

const run = await client.actor("muffin/amazon-product-scraper").call({
    asins: ["B0CHWRXH8B", "B09V3KXJPB"],
    country: "US",
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
items.forEach((item) => console.log(`${item.asin}: $${item.price}`));
```

### Apify API (cURL)

```
# Start a run
curl -X POST "https://api.apify.com/v2/acts/muffin~amazon-product-scraper/runs?token=YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"asins": ["B0CHWRXH8B"], "country": "US"}'

# Get results from dataset
curl "https://api.apify.com/v2/datasets/DATASET_ID/items?token=YOUR_TOKEN"
```

## Use Cases

**Price Monitoring** -- Track competitor prices across multiple marketplaces on a schedule. Feed data into your pricing engine.

**FBA Product Research** -- Evaluate products by BSR, price, reviews, and competition data at scale.

**MAP Compliance** -- Verify resellers adhere to Minimum Advertised Price policies across all Amazon marketplaces.

**Competitor Tracking** -- Monitor changes in pricing, images, bullet points, seller info across your competitive landscape.

**Brand Protection** -- Detect unauthorized sellers or counterfeit listings by scanning your branded ASINs.

## Comparison with Alternatives

| Feature | This Actor | Jungle Scout Scraper | Other Scrapers |
| --- | --- | --- | --- |
| Marketplaces | **10** | 1-2 | 1-3 |
| Fields per result | **25+** | 10-15 | 8-12 |
| BSR data | Yes | Yes | Sometimes |
| Buybox & seller ID | Yes | No | Partial |
| Amazon Choice / Best Seller | Yes | No | No |
| Anti-bot technology | **Browser-grade** | Basic proxy | Basic proxy |
| Success rate | **99%+** | ~90% | ~85% |

## AI Agent Integration (MCP)

This Actor works with the [Apify MCP server](https://docs.apify.com/platform/integrations/mcp), enabling AI agents to scrape Amazon product data programmatically.

**What AI agents can do with this Actor:**

- Look up any Amazon product by ASIN to get current price, availability, and reviews
- Compare prices across different Amazon marketplaces (US, UK, DE, etc.)
- Monitor product pricing and stock status
- Extract product features and descriptions for analysis
- Check seller information and buybox status

**MCP configuration:**

```
{
    "mcpServers": {
        "apify": {
            "url": "https://mcp.apify.com",
            "headers": {
                "Authorization": "Bearer YOUR_APIFY_TOKEN"
            }
        }
    }
}
```

Then ask your AI agent: *"Look up Amazon product B0CHWRXH8B and tell me its price and rating"*

## FAQ

**How fast are results?**
Single ASINs return in 2-5 seconds. Batches of 50 ASINs complete in 10-30 seconds.

**What if a product is not found?**
An error item is pushed to the dataset with the ASIN and error message. You can filter these by checking the `error` field.

**Can I scrape variations?**
Yes. Each variation has its own ASIN. The `parent_asin` field links variants to the parent listing.

**Do I need my own proxies?**
No. All proxy management and anti-bot handling is built in.

**Which fields are always present?**
`asin`, `country`, `url`, and `scraped_at` are always present. Other fields depend on the listing -- an out-of-stock product may not have a price.

**Can I use this commercially?**
Yes. No restrictions on commercial use.

**Does this work with AI agents?**
Yes. This Actor is fully compatible with the Apify MCP server. AI agents can discover it via `search-actors`, inspect its schema via `fetch-actor-details`, and call it via `call-actor`.