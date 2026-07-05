[Amazon Product Scraper](https://apify.com/scrapie/Amazon-Product-Scraper?fpr=data)

# Amazon Product Scraper — Apify Actor

> **Extract Amazon product data at scale** — titles, prices, ratings, images, descriptions, and more. Supports 5 regions, keyword search, direct URL scraping, and Pay-per-event billing. Built with Crawlee + Playwright.

[![Apify Actor](https://img.shields.io/badge/Apify-Actor-brightgreen)](https://apify.com/)
[![Node.js](https://img.shields.io/badge/Node.js-22-green)](https://nodejs.org)
[![Playwright](https://img.shields.io/badge/Playwright-1.59-blue)](https://playwright.dev)
[![License: ISC](https://img.shields.io/badge/License-ISC-yellow)](https://opensource.org/licenses/ISC)

---

## Table of Contents

- Overview
- Key Features
- Supported Regions
- Input Parameters
- Output Schema
- Example Input & Output
- Anti-Bot & Proxy Handling
- How It Works
- Use Cases
- Getting Started on Apify
- Local Development
- Cost & Pay-per-Event
- FAQ

---

## Overview

The **Amazon Product Scraper** is a production-ready [Apify Actor](https://apify.com/actors) that automates the extraction of structured product data from Amazon search results and individual product pages. Whether you need to **monitor competitor pricing**, **build a product catalog**, or **conduct e-commerce market research**, this actor provides the data you need — reliably and at scale.

Powered by **[Crawlee](https://crawlee.dev)** and **[Playwright](https://playwright.dev)**, the actor renders JavaScript-heavy Amazon pages as a real browser would, bypassing common scraping challenges like lazy-loaded content and dynamic pricing.

---

## Key Features

- 🔍 **Keyword Search** — Provide one or more search terms and scrape matching product listings automatically.
- 🔗 **Direct URL Support** — Scrape specific product pages or search result pages by pasting URLs directly.
- 🌍 **5 Regional Amazon Stores** — US, India, UK, UAE, and Australia with correct locale and timezone emulation.
- 💰 **Structured Price Data** — Prices extracted and parsed as numbers, ready for analysis or price comparison.
- ⭐ **Ratings & Review Counts** — Average star rating and total number of customer reviews per product.
- 🖼️ **Product Images** — Full-resolution image URLs extracted from the product gallery.
- 📦 **Availability & Offers** — Stock status, promotions, coupons, and deal information.
- 🛡️ **Anti-Bot Detection** — Automatically detects CAPTCHA, Robot Check, and "Dogs of Amazon" error pages.
- 🔄 **Smart Pagination** — Follows "Next Page" links until the `maxItems` limit is reached.
- 💳 **Pay-per-Event Billing** — Integrates with Apify's cost-control system; automatically stops when the charge limit is hit.
- 🔒 **Proxy Support** — Fully compatible with Apify Proxy (residential, datacenter) to avoid IP bans.

---

## Supported Regions

| Region Code | Amazon Domain | Currency | Locale | Timezone |
| --- | --- | --- | --- | --- |
| `US` | amazon.com | $ | en-US | America/New_York |
| `IN` | amazon.in | ₹ | en-IN | Asia/Kolkata |
| `UK` | amazon.co.uk | £ | en-GB | Europe/London |
| `UAE` | amazon.ae | AED | en-AE | Asia/Dubai |
| `AU` | amazon.com.au | A$ | en-AU | Australia/Sydney |

---

## Input Parameters

Configure the actor using the following input fields:

| Parameter | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `searchTerms` | `string[]` | No | `[]` | Keywords to search on Amazon (e.g., `["trimmer for men", "earbuds"]`) |
| `startUrls` | `URL[]` | No | `[]` | Direct Amazon product or search result URLs to scrape |
| `region` | `string` (enum) | **Yes** | `"US"` | Amazon regional store. One of: `US`, `IN`, `UK`, `UAE`, `AU` |
| `maxItems` | `integer` | No | `10` | Maximum number of product detail pages to scrape (minimum: 1) |
| `proxyConfiguration` | `object` | No | — | Apify Proxy settings (recommended for large-scale runs) |

> **Tip:** You can supply both `searchTerms` and `startUrls` at the same time. The actor will process both sources and respect the overall `maxItems` limit.

---

## Output Schema

Each scraped product is saved as a JSON object to the Apify **Dataset**. Here is the full output schema:

| Field | Type | Description |
| --- | --- | --- |
| `url` | `string` | Canonical Amazon product URL (tracking params removed) |
| `title` | `string` | Full product title |
| `price` | `number|null` | Parsed numeric price (e.g., `29.99`) |
| `thumbnail` | `string` | Image URL from search results listing |
| `description` | `string` | Product description from the detail page |
| `features` | `string` | Bullet points from the "About this item" section |
| `availability` | `string` | Stock status (e.g., "In Stock", "Only 3 left in stock") |
| `offers` | `string[]` | List of applicable promotions, coupons, and deals |
| `ratingCount` | `string` | Total number of customer reviews (e.g., "1,234 ratings") |
| `avgRating` | `string` | Average star rating (e.g., "4.5 out of 5 stars") |
| `asin` | `string` | Amazon Standard Identification Number (ASIN) |
| `images` | `string[]` | All product image URLs from the gallery |
| `internalLinks` | `string[]` | Related product page links found on the product page |
| `timestamp` | `string` | ISO 8601 timestamp of when the product was scraped |

---

## Example Input & Output

### ✅ Input Example

```
{
  "searchTerms": ["trimmer for men", "wireless earbuds"],
  "region": "IN",
  "maxItems": 5,
  "proxyConfiguration": {
    "useApifyProxy": true,
    "apifyProxyGroups": ["RESIDENTIAL"]
  }
}
```

### 📦 Output Example (Single Product)

```
{
  "url": "https://www.amazon.in/dp/B09XK8QSQS",
  "title": "Philips Series 3000 Beard Trimmer for Men BT3231/15",
  "price": 1295.00,
  "thumbnail": "https://m.media-amazon.com/images/I/71FasHLsCqL._AC_UL320_.jpg",
  "description": "Philips Series 3000 Beard Trimmer comes with 13 length settings...",
  "features": "• DuraPower Technology for 4x longer lasting battery\n• 13 length settings (1-13mm)\n• 60-min cordless use after 1-hr charge\n• Self-sharpening steel blades",
  "availability": "In stock",
  "offers": ["₹100 coupon applied at checkout", "5% off with SBI Credit Card"],
  "ratingCount": "52,341 ratings",
  "avgRating": "4.2 out of 5 stars",
  "asin": "B09XK8QSQS",
  "images": [
    "https://m.media-amazon.com/images/I/71FasHLsCqL._SL1500_.jpg",
    "https://m.media-amazon.com/images/I/61OcEkVvr0L._SL1500_.jpg"
  ],
  "internalLinks": [
    "https://www.amazon.in/dp/B07PBJPSQF",
    "https://www.amazon.in/dp/B09TGK3GH4"
  ],
  "timestamp": "2026-04-14T15:42:00.000Z"
}
```

---

## Anti-Bot & Proxy Handling

Amazon aggressively blocks automated access. This actor includes multiple layers of protection:

1. **Browser Fingerprinting** — Uses Crawlee's built-in fingerprint rotation to mimic real users.
2. **Locale & Timezone Emulation** — Sets browser locale and timezone to match the target Amazon region, preventing geo-redirects.
3. **Human-like Delays** — Random wait times (1–3 seconds) between actions to simulate browsing behavior.
4. **CAPTCHA Detection** — Automatically detects CAPTCHA, Robot Check, and "Dogs of Amazon" error pages and retries with a new session.
5. **Diagnostic Screenshots** — On block events, saves screenshots and HTML to the Key-Value Store for debugging.
6. **Proxy Support** — Pair with Apify Proxy (residential proxies recommended) for production-scale runs.

> **Recommendation:** For runs larger than 50 products, always enable `proxyConfiguration` with residential proxies to minimize block rates.

---

## How It Works

```
[Input: searchTerms / startUrls]
         │
         ▼
[Build Search URLs per Region]  ──► amazon.com/s?k=keyword
         │
         ▼
[LIST Handler: Search Results Page]
  • Detect blocks (CAPTCHA / Robot / Dogs)
  • Extract product cards (URL, title, price, thumbnail)
  • Enqueue product detail URLs (up to maxItems)
  • Follow "Next Page" if more items needed
         │
         ▼
[DETAIL Handler: Product Page]
  • Scrape full product data
  • Parse price to number
  • Extract all images from gallery
  • Extract related product links
  • Push result to Dataset
  • Check Pay-per-event charge limit
         │
         ▼
[Apify Dataset Output]
```

---

## Use Cases

- **Price Monitoring & Alerts** — Track competitor or supplier prices over time.
- **Product Research** — Gather data for niche analysis, reviews, and trend spotting.
- **Catalog Building** — Import product data (title, images, ASIN, price) into your store or database.
- **Competitive Intelligence** — Analyze competitors' product listings, ratings, and customer sentiment.
- **Academic Research** — Collect e-commerce data for market studies.
- **Affiliate Marketing** — Automate product discovery for affiliate content sites.
- **Price Comparison Sites** — Aggregate Amazon pricing across multiple regions.

---

## Getting Started on Apify

1. **Open the Actor** on the [Apify Console](https://console.apify.com/).
2. Click **Try for free** or **Run**.
3. Fill in the **Input** form:

- Add one or more **Search Terms** (e.g., `trimmer for men`).
- Select your target **Region** (US, IN, UK, UAE, AU).
- Set **Max Items** (default: 10).
- *(Optional)* Enable **Proxy** for better success rates.
4. Click **Start** and wait for the run to complete.
5. View results in the **Dataset** tab or download as **JSON / CSV / Excel**.

---

## Cost & Pay-per-Event

This actor supports **Apify's Pay-per-event (PPE)** billing model. Each product successfully scraped and pushed to the dataset is counted as one chargeable event. The actor:

- Checks the charge limit after every product push.
- Stops gracefully when the charge limit is reached.
- Logs a warning: `"Apify charge limit (Pay-per-event) reached. Stopping further scraping."`

This ensures you are never charged more than your configured budget.

---

## FAQ

**Q: Does this work on all Amazon regions?**

A: Yes. The actor supports `amazon.com` (US), `amazon.in` (India), `amazon.co.uk` (UK), `amazon.ae` (UAE), and `amazon.com.au` (Australia).

**Q: What happens when Amazon blocks the crawler?**

A: The actor detects CAPTCHA and robot-check pages, saves a diagnostic screenshot to the Key-Value Store, and retries the request with a fresh browser session and IP (when proxies are configured).

**Q: Why do I need proxies?**

A: Amazon actively blocks datacenter IPs. Residential proxies look like real user traffic and significantly reduce block rates. For runs > 50 products, proxies are strongly recommended.

**Q: Can I scrape product reviews?**

A: Not in the current version. This actor focuses on product listing data. Review scraping can be added as a future enhancement.

**Q: Is this against Amazon's Terms of Service?**

A: Web scraping public data is a legal grey area that varies by jurisdiction. This actor only accesses publicly visible, non-authenticated Amazon pages. Always consult your legal team and comply with local laws when using scraped data.

**Q: Can I export results to CSV or Excel?**

A: Yes. From the Apify Console Dataset view, you can export data to JSON, CSV, XML, Excel, and RSS formats with one click.

---

## Tech Stack

| Technology | Role |
| --- | --- |
| [Apify SDK v3](https://docs.apify.com/sdk/js) | Actor lifecycle, dataset, proxy |
| [Crawlee v3](https://crawlee.dev) | Crawler framework, routing |
| [Playwright v1.59](https://playwright.dev) | Headless browser automation |
| Node.js 22 | Runtime |
| Docker | Containerized deployment |

---

## License

[ISC License](https://opensource.org/licenses/ISC) © 2026