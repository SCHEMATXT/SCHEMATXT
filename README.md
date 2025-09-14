# Schema.txt Specification

## The AI-Era Evolution of robots.txt

Schema.txt is a proposed standard that provides AI crawlers and search engines with efficient access to rich structured semantic data, pre-extracted, indexed, and cataloged by entity type, delivering high-value structured content without the need for complex inference processing thus solving the compute cost crisis of inferential content understanding.

## The Problem

- AI crawlers require expensive inference to extract semantics from raw HTML
- Cloudflare's paywall model makes traditional web crawling unsustainable
- 20% of the internet (Cloudflare-protected) becomes increasingly expensive to access
- Current schema.org implementation remains fragmented across individual pages

## The Solution

Schema.txt creates a domain-level **semantic catalog** of your knowledge graph fragments that directs AI systems to structured data endpoints, eliminating the need for expensive page-by-page inference.

## Discovery Through robots.txt

Schema.txt leverages the existing robots.txt infrastructure for universal discovery; following the same pattern as sitemap declarations:

```
# robots.txt
User-agent: *
Disallow:

Schema: https://example.com/schema.txt // Step 4
Sitemap: https://example.com/sitemap.xml
Sitemap: https://example.com/schema-sitemap.xml // Step 5
```

This approach ensures:
- **Zero discovery friction** - every crawler already reads robots.txt
- **Universal compatibility** - no new discovery protocols needed
- **Instant adoption pathway** - leverages existing infrastructure

## Specification

### File Location
Referenced via robots.txt Schema directive:
```
Schema: https://example.com/schema.txt
```

### Basic Structure
```
# Schema.txt v1.0 - Semantic Catalog for AI Systems
# Format: @type, @id, @endpoint

# Organization Information
@type: Organization
@id: org-main
@endpoint: https://cdn.example.com/schema/organization.json

# Product Catalog
@type: Product
@id: product-catalog
@endpoint: https://cdn.example.com/schema/products/*.json
@index: https://cdn.example.com/schema/products/index.json

# Reviews and Ratings
@type: Review
@id: review-feed
@endpoint: https://cdn.example.com/schema/reviews/*.json
@index: https://cdn.example.com/schema/reviews/index.json

# Real-time Updates
@type: LiveData
@id: live-feed
@endpoint: https://cdn.example.com/schema/live/*.json
@refresh: 300
```

### Endpoint Requirements

All referenced endpoints must return valid JSON-LD formatted according to schema.org specifications:

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "@id": "https://example.com/products/widget-123",
  "name": "Professional Widget",
  "description": "High-quality widget for professional use",
  "offers": {
    "@type": "Offer",
    "price": "99.99",
    "priceCurrency": "USD"
  }
}
```

## Benefits

### For AI Systems
- **90% reduction** in inference costs
- Real-time access to structured data via CDN endpoints
- Efficient discovery of semantic relationships
- Reduced bandwidth and compute requirements
- **Universal discovery** through existing robots.txt parsing

### For Website Owners  
- Direct control over AI understanding
- Real-time data updates without re-crawling
- Improved search visibility
- Future-proof semantic architecture
- **No new infrastructure required** - uses existing robots.txt

### For Search Engines
- Scalable semantic understanding
- Reduced infrastructure costs
- Higher quality search results
- Efficient index updates
- **Immediate implementation** using current robots.txt parsers

## Implementation Guide

### Step 1: Audit Current Schema
Analyze existing structured data implementation across your domain.

### Step 2: Create CDN Endpoint Architecture
Design JSON-LD endpoints hosted on CDN for optimal global performance:
- Organization data
- Product catalogs
- Reviews and ratings  
- Real-time updates

### Step 3: Deploy schema.txt
Create the semantic catalog file with @type, @id, and @endpoint directives.

### Step 4: Update robots.txt
Add Schema directive pointing to your schema.txt file:
```
Schema: https://example.com/schema.txt
```
### Step 5: Add to schema-sitemap.xml // Optional
Add schema.txt json files as API endpoints to your schema-sitemp.xml file. 
Referenced for example from a dedicated 'GEO' page, that is both human, and machine readable. .

### Step 6: Validate
Use schema.org validation tools to ensure all endpoints are JSON-LD compliance.

## Technical Implementation

### CDN Architecture
- **Global distribution** ensures fast access for international AI crawlers
- **Caching efficiency** reduces server load and improves response times
- **Real-time updates** possible without full site re-crawling

### Crawler Implementation
For existing crawlers to support schema.txt:

1. **Parse robots.txt** (already implemented)
2. **Check for Schema directive** (simple addition)
3. **Fetch and parse schema.txt** (basic text parsing)
4. **Access CDN endpoints** (existing JSON-LD processing) // Or, instead use API endpoints
5. **Create GEO page of endpoints** (Create human, and machine readable links to API endpoints)
6. **Update GEO page headers to point to endpoints** (Add <link rel="alternate"> links for each artifact)

### Rate Limiting and Security
- Implement appropriate rate limiting on schema endpoints
- Use HTTPS for all endpoints
- Consider access controls for sensitive data

## Adoption Strategy

### Phase 1: Early Adopters
- AI-first search engines (Perplexity, ChatGPT, etc.)
- Companies facing high crawling costs
- Technical implementers seeking efficiency gains

### Phase 2: Universal Adoption
- Major search engines integrate schema.txt parsing
- Web frameworks add schema.txt generation
- SEO tools include schema.txt optimization

### Why Adoption Will Be Rapid
- **Technical barrier is minimal** - extends existing robots.txt parsing
- **Economic incentive is massive** - 90% compute cost reduction
- **Discovery is automatic** - every crawler already reads robots.txt

## Future Roadmap

- [ ] W3C Community Group proposal for Schema directive in robots.txt
- [ ] Major AI crawler adoption through direct outreach
- [ ] Integration with existing schema.org tooling
- [ ] Analytics and monitoring standards for schema.txt usage

## License

This specification is released under Creative Commons Attribution 4.0 International License to encourage widespread adoption.

---

**Created by the [VISEON.IO](https://www.reddit.com/r/viseon) team - Making the web AI-ready, efficiently.**

**Community Discussion**: [r/schematxt](https://www.reddit.com/r/schematxt)


