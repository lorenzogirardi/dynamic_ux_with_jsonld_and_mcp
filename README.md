
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

**Repository:**

- Original: [lorenzogirardi/demo-app-eshop](https://github.com/lorenzogirardi/demo-app-eshop)
- JSON-LD Upgraded: [lorenzogirardi/demo-app-eshop-jsonld](https://github.com/lorenzogirardi/demo-app-eshop-jsonld)


### Setup

- Both versions of the shop were dockerized and served via ngrok to simulate real-world exposure.
- Live tests were run with AI chat platforms to analyze how each version responded to product queries.

***

## Screenshots and What They Show

| Screenshot | Description |
| :-- | :-- |
| ![Designer Shoes page][^1] | **Product Page:** Shows human-readable details for a pair of designer shoes—name, image, price, and description. The classic version, meant for human eyes only, lacks structured machine data. |
| ![Perplexity comparison][^2] | **Conversational AI Test:** Perplexity fails to find details on the classic shop (left), but instantly extracts price, availability, images, and description from the JSON-LD enabled shop (right). This verifies the transformation for AI consumption. |
| ![Jules code change][^3] | **Key Code Edit:** Shows how the JSON-LD script was added to each product page. This injects schema.org compliant metadata for all product details, enabling machine parsing and AI understanding. |
| ![Ngrok containers][^4] | **Technical Exposure:** ngrok dashboard proves both docker containers (classic and JSON-LD) were exposed to the internet for parallel testing, simulating a real user/scenario. |


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


### Future-Proofing Your Commerce Strategy

The retail future is conversational; traditional keywords are giving way to voice and chat recommendations.
JSON-LD makes a product catalog “first-class content” in every context—chat, voice, smart home, and social commerce.

***

## Conclusion: Why This Is Strategic

The experiment with demo-app-eshop proves a simple truth:
**Structured data is the new foundation for digital commerce, not only for Google search but for all the intelligent platforms users will increasingly rely on.**

- **Quick impact for minimal technical effort**
- **Gains in AI SEO are immediate and measurable**
- **Strategic advantage in a fast-evolving digital landscape**

Smart businesses will empower their content with AI-centric structure today, gaining visibility, relevance, and adaptability for tomorrow’s shopping journeys.

***

### Visual Evidence

- ![Designer Shoes page][^1]
- ![Perplexity comparison][^2]
- ![Jules code change][^3]
- ![Ngrok containers][^4]

Each screenshot documents the journey from old-school presentation to full AI SEO readiness, serving as a playbook for all modern e-commerce projects.

***

**Author:**
Tech Manager \& R\&D Lead
August 2025

***

> Ready to enable AI SEO for your shop?
> Start with JSON-LD, future-proof your visibility, and join the conversational commerce revolution today.

---

<div style="text-align: center">⁂</div>

[^1]: product-page-example.jpg

[^2]: perplexity-difference.jpg

[^3]: jules-code-change.jpg

[^4]: docker-and-ngrok.jpg

