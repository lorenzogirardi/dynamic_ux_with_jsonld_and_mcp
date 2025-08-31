
# Dynamic UX with jsonld and mcp

## Redefining SEO for the Age of Conversational AI


***

### Table of Contents

- [Introduction](#introduction)
- [User Behavior Shift: Conversational AI Discovery Is the New Entry Point](#user-behavior-shift-conversational-ai-discovery-is-the-new-entry-point)
- [Case Study: Upgrading demo-app-eshop](#case-study-upgrading-demo-app-eshop)
- [Screenshots and What They Show](#screenshots-and-what-they-show)
- [Technical Deep Dive: Jules’ JSON-LD Integration](#technical-deep-dive-jules-json-ld-integration)
- [How JSON-LD Transforms E-Commerce for AI Discovery](#how-json-ld-transforms-e-commerce-for-ai-discovery)
- [Business Impact of AI-Friendly Content](#business-impact-of-ai-friendly-content)
- [Conclusion: Why This Is Strategic](#conclusion-why-this-is-strategic)

***

## Introduction

This article began as a classic exploration into JSON-LD and its impact on structured data for e-commerce. However, as research and experimentation progressed, a fundamental realization emerged: what’s actually changing is the entire user experience paradigm. 
The way end-users interact with digital products is shifting beyond traditional web and app models—toward dynamic, conversational discovery driven by AI.

For years, the typical customer journey followed one of several well-established routes:

- **Traditional Website Experience:**
Customers access product information via desktop or mobile browsers, interacting with a backend-for-frontend (BFF) architecure that serves tailored content.  
![Traditional Website Experience](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_480/v1756653459/ai/dynamic_ux_with_jsonld_and_mcp/misc/traditional1.png)

- **Mobile App Direct API Access:**
Users connected through native apps, directly hitting underlying APIs for transactional or product data.  
![Mobile App Direct API Access](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_480/v1756653459/ai/dynamic_ux_with_jsonld_and_mcp/misc/traditional2.png)


- **Partner Integrations:**
Third-party platforms aggregate or resell products by connecting directly to the e-commerce native APIs, creating new distribution channels.  
![Partner Integrations](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_480/v1756653459/ai/dynamic_ux_with_jsonld_and_mcp/misc/traditional3.png) 
<br/><br/>
<br/><br/>

What’s new (and truly disruptive) is the rise of AI-powered chat interfaces.

- **Conversational AI Discovery:**
The customer asks an AI assistant (via desktop chat, mobile app bot, or integrated partner channel) for product information. Instead of static, pre-built pages, content is dynamically constructed on demand, tailored to the specific user question, intent, and context.  
![Conversational AI Discovery](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_720/v1756653459/ai/dynamic_ux_with_jsonld_and_mcp/misc/chat-driven-user-experience.png)   


This shift means that sites must expose product data in ways instantly consumable by AI—not just for classic SEO, but for rich, contextual, real-time answers. 
JSON-LD becomes the bridge, enabling e-commerce sites to participate fully in the conversational, intent-driven commerce ecosystem.

The days when classic SEO alone could guarantee visibility for products online are ending. As users move to conversational AI platforms—ChatGPT, Gemini, Perplexity, and Mistral—websites must expose data in a way that is instantly machine-readable and context-aware. This involves a shift from simple keywords and descriptions to rich, structured data using [JSON-LD](https://json-ld.org/) and [schema.org](https://schema.org/).


***

## User Behavior Shift: Conversational AI Discovery Is the New Entry Point

Search is evolving rapidly. More and more users now seek answers, recommendations, and product suggestions directly through conversational platforms—sometimes bypassing traditional search engines altogether. AI chat platforms now provide:

- **Direct answers** to complex, natural-language queries (for example: “Show me blue Gucci sneakers under £1000 and tell me if they’re in stock”)  
- **Contextual relevance**, understanding and matching user intent far beyond simple keyword search  
- **Instant access** to product details, images,localtion, prices, and offers—sourced from structured, machine-consumable site content  

This shift signals a fundamental change: **the future center of digital product discovery is not search (SEO) alone, but Conversational AI Discovery**.  
If product information isn’t provided in a structured, AI-friendly way, it won’t appear in chat results—resulting in missed opportunities and lost sales.

While SEO is still a supporting element in this ecosystem, the primary focus for the next generation of digital commerce is ensuring that products are discoverable, interpretable, and actionable within conversational AI environments.  
Those who adapt will gain visibility and relevance; those who don’t risk disappearing from the main channel where user queries begin.

***

## Case Study: Upgrading demo-app-eshop


### Setup

- Both versions of the shop were dockerized and served via ngrok to simulate real-world exposure.
- Live tests were run with AI chat platforms to analyze how each version responded to product queries.

***

## Screenshots and What They Show

### Application overview
 
![traditional plp](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_720/v1756552351/ai/dynamic_ux_with_jsonld_and_mcp/traditional/plp-traditional.png) 

![traditional pdp](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_720/v1756551701/ai/dynamic_ux_with_jsonld_and_mcp/traditional/pdp-traditional.png) 



***

## Technical Deep Dive: Jules’ JSON-LD Integration

**Process Overview:**

1. **Enhanced Open Graph Metadata**
Open Graph tags were upgraded to make previews richer on social and chat platforms.
2. **Insertion of JSON-LD Structured Data**
A script using schema.org/Product was added. This embeds all product details in a format AI models are designed to read.

**Sample Code Snippet:**

```tsx
const jsonLd = {
  "@context": "https://schema.org",
  "@type": "Product",
  name,
  description,
  image: imageUrl,
  offers: {
    "@type": "Offer",
    price: (price / 100).toString(),
    priceCurrency: "GBP",
    availability: "https://schema.org/InStock"
  },
  url: url
};
return (
  <div>
    {/* Product UI ... */}
    <script type="application/ld+json" dangerouslySetInnerHTML={{ __html: JSON.stringify(jsonLd) }} />
  </div>
);
```

- Updated in `src/app/products/[id]/page.tsx`
- Every product detail is mapped to its schema property and updated dynamically per page load.
- Minimal code effort for massive increase in machine and AI visibility.

![jules](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_720/v1756556731/ai/dynamic_ux_with_jsonld_and_mcp/misc/jules-prompt.png)


![git](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_720/v1756556737/ai/dynamic_ux_with_jsonld_and_mcp/misc/github-commit-jsonld.png)


***

## How JSON-LD Transforms E-Commerce for AI Discovery

### Immediate AI Advantages

- **Direct Information Extraction:**
AI engines obtain precise product info (name, price, availability, image) instantly—without network scraping, error, or delay.
- **Contextual User Matching:**
Every question an AI gets (“What’s the price?” “Is it in stock?” “Describe the design and material”) is fully answerable with high accuracy.
- **Future-Proof and Omni-Channel:**
JSON-LD and schema.org format is compatible with chatbots, voice assistants, search engines, social platforms, and future digital channels.
- **Rapid Development:**
As verified in this project, changes require minimal engineering and immediately open the shop to AI-driven referrals.


#### Traditional

![src pdp traditional](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_720/v1756552933/ai/dynamic_ux_with_jsonld_and_mcp/traditional/pdp-source-traditional.png)

![schema validation traditional](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_720/v1756556418/ai/dynamic_ux_with_jsonld_and_mcp/traditional/schema-validation-traditional.png)

![src pdp traditional](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_720/v1756556418/ai/dynamic_ux_with_jsonld_and_mcp/traditional/rich-test-traditional.png)




#### Jsonld

![src pdp jsonld](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_720/v1756556048/ai/dynamic_ux_with_jsonld_and_mcp/jsonld/pdp-source-jsonld.png)

![schema validation jsonld](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_720/v1756556046/ai/dynamic_ux_with_jsonld_and_mcp/jsonld/schema-validation-jsonld.png)

![src pdp jsonld](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_720/v1756556045/ai/dynamic_ux_with_jsonld_and_mcp/jsonld/rich-test-jsonld.png)


### Query-Optimized Content

Traditional SEO optimizes for keywords. AI SEO, enabled by JSON-LD, optimizes for **user requests**.
Structured data ensures the answer matches the actual question, not what the developer *hopes* will be understood.

***

## Business Impact of AI-Friendly Content

### Strategic Advantages

- **Visibility Where It Matters**
Products become “findable” by any platform, not just search engines. AI chat results are now the main driver of discovery.
- **Conversion-Boosting Experiences**
Detailed, relevant, and rich results build trust and drive faster purchase decisions. Users get full answers without friction.
- **B2B Integration Power**
Resellers, affiliates, and partners can integrate products via machine-readable feeds—no custom scraping required.
- **Analytics Evolution**
Organizations can now track conversational engagement, AI-driven sessions, and measure new channels of customer interaction.


#### Traditional

![perplexity traditional answer](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_720/v1756553130/ai/dynamic_ux_with_jsonld_and_mcp/traditional/perplexity-chat-traditional.png)


#### Jsonld

![perplexity jsonld answer](https://res.cloudinary.com/ethzero/image/upload/c_scale,w_720/v1756556046/ai/dynamic_ux_with_jsonld_and_mcp/jsonld/perplexity-chat-json.png)


### Future-Proofing Your Commerce Strategy

The retail future is conversational; traditional keywords are giving way to voice and chat recommendations.
JSON-LD makes a product catalog “first-class content” in every context—chat, voice, smart home, and social commerce.

***

## Conclusion: Why This Is Strategic

The experiment proves a simple truth:
**Structured data is the new foundation for digital commerce, not only for Google search but for all the intelligent platforms users will increasingly rely on.**

- **Quick impact for minimal technical effort**
- **Gains in AI SEO are immediate and measurable**
- **Strategic advantage in a fast-evolving digital landscape**

Smart businesses will empower their content with AI-centric structure today, gaining visibility, relevance, and adaptability for tomorrow’s shopping journeys.

***

## Reflections: Is This Really the Future?

So is this the future? Yes and no.  
There are enormous new opportunities ahead, but also many new challenges. Conversational platforms like ChatGPT, Claude, Gemini, and Perplexity are quickly becoming the primary interfaces for users—but at present, these interfaces are asynchronous and opaque.

- **Who is calling your e-commerce?**  
  Shop owners never know who is querying their business—there’s no clear user identification when the interaction goes through AI agents.
- **Unintended side effects of open data**  
  The more information we expose, the greater the risk of undesirable consequences. For example, if you publish the number of items in stock, competitors can easily analyze your business performance.
- **Sensitive data risks**  
  There's always the danger of unintentionally exposing sensitive data that should remain private.
- **WAF (Web Application Firewall) solutions**  
  Security solutions for filtering and protecting traffic, like WAFs, become much trickier when the main traffic source is indirect or mediated by AI chat platforms.

### What is still missing?
Realistically, just as search engine monopolies formed around Google, Yahoo, Baidu, or Bing, we’re likely to see a small handful of dominant chat platforms.  
These will almost certainly evolve to include sort of collaboration/registration/whatever processes, mechanisms for optimizing the way queries work, and features to pass specific fields enabling a full, end-to-end traceable session—from chat request to final e-commerce transaction.

In short, the frontier is wide open but incomplete:  
- **We need session traceability and user context**
- **We must balance data openness with business privacy and security**
- **We should prepare for a future where e-commerce optimization is not just SEO, but also “Chat Optimization” and secure, user-aware integrations with AI platforms**

This is just the beginning, and the conversation—and technology—will keep evolving.
