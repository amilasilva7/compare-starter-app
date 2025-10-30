# SEO Playbook for Web & AI Engines

This playbook provides a comprehensive overview of the Search Engine Optimization (SEO) strategy for the UK Price Comparison Website. It covers keyword strategy and advanced techniques tailored for both traditional search engines (like Google) and modern AI-powered answer engines.

Our guiding principle is **E-E-A-T**: **E**xperience, **E**xpertise, **A**uthoritativeness, and **T**rustworthiness.

---

### **Part 1: Keyword & Content Strategy**

We will target users at every stage of their journey by categorizing keywords based on their intent.

**1. Transactional Keywords (Users ready to buy/compare)**
*   **Goal:** Capture high-conversion traffic.
*   **Target Pages:** Our main comparison tool pages.
*   **Examples:**
    *   *Head (broad):* "car insurance", "compare broadband", "home insurance quotes"
    *   *Body (more specific):* "compare car insurance uk", "cheapest business energy supplier", "van insurance for over 50s"
    *   *Long-Tail (very specific):* "business contents insurance for a small shop", "compare fixed rate energy tariffs in scotland"

**2. Informational Keywords (Users doing research)**
*   **Goal:** Build trust, establish expertise (E-E-A-T), and capture users early.
*   **Target Pages:** Our blog, guides, and FAQ sections.
*   **Examples:**
    *   *Questions:* "how does a no claims bonus work?", "what level of contents insurance do I need?", "is public liability insurance a legal requirement?"
    *   *Problem-based:* "lower my car insurance premium", "how to switch energy provider without penalty"
    *   *vs. Comparisons:* "comprehensive vs third party insurance", "fixed vs variable energy tariff"

**3. Navigational Keywords (Users looking for us)**
*   **Goal:** Ensure easy access for users who already know our brand.
*   **Target Pages:** Homepage, login page.
*   **Examples:** "[Our Brand Name]", "[Our Brand] login", "[Our Brand] car insurance"

---

### **Part 2: Advanced SEO Techniques**

#### **Pillar 1: Technical SEO**

*   **For Web & AI:**
    *   **Core Web Vitals:** Continue optimizing for speed. This is a foundational ranking factor.
    *   **Mobile-First Indexing:** Our mobile-first design is already aligned with Google's primary indexing method.
    *   **Canonical Tags:** Use `rel="canonical"` on all pages to prevent duplicate content issues, especially with tracking parameters.
    *   **Clean XML Sitemaps:** Maintain a dynamic sitemap that includes all canonical URLs and submit it to Google Search Console.

*   **Specifically for AI Engines:**
    *   **Deep Structured Data (Schema):** This is how we spoon-feed AI. We will go beyond basic schema. For every single quote on a results page, we will implement a detailed `Product` and `Offer` schema.

    **Example `JSON-LD` for one car insurance quote:**
    ```json
    {
      "@context": "https://schema.org",
      "@type": "Product",
      "name": "Comprehensive Car Insurance",
      "brand": {
        "@type": "Brand",
        "name": "Example Insurer Ltd"
      },
      "offers": {
        "@type": "Offer",
        "priceCurrency": "GBP",
        "price": "450.00",
        "priceValidUntil": "2025-11-30",
        "url": "https://our-site.co.uk/redirect/example-insurer-123",
        "seller": {
          "@type": "Organization",
          "name": "Example Insurer Ltd"
        }
      },
      "review": {
        "@type": "Review",
        "reviewRating": {
          "@type": "Rating",
          "ratingValue": "4.5",
          "bestRating": "5"
        },
        "author": {
          "@type": "Person",
          "name": "Jane Doe"
        }
      }
    }
    ```

#### **Pillar 2: On-Page SEO**

*   **For Web & AI:**
    *   **Title & Meta Tags:** Craft compelling, keyword-rich titles and descriptions for a high click-through rate.
    *   **Internal Linking:** Create a "topic cluster" model. Our main "Car Insurance" page (the pillar) will link out to all related articles like "How No-Claims Bonus Works" (the cluster content), and these articles will link back to the pillar. This builds topical authority.
    *   **Author Bios:** For all informational content, we will include detailed author bios with credentials and links to social profiles to reinforce E-E-A-T.

*   **Specifically for AI Engines:**
    *   **Content Formatting for Snippets:** AI loves scannable content it can lift for "AI Overviews" or featured snippets. We will:
        *   Use clear headings (`H2`, `H3`) for each section.
        *   Use bulleted (`<ul>`) and numbered lists (`<ol>`) extensively.
        *   Provide concise, direct answers to questions right below the heading.
        *   Use tables (`<table>`) to compare features, which are very easy for AI to parse.
    *   **Create "Answer Targets":** Frame content to directly answer questions.

#### **Pillar 3: Off-Page SEO**

*   **For Web & AI:**
    *   **Digital PR:** We will create one major, data-backed content piece per quarter (e.g., "The UK's Most & Least Expensive Postcodes for Car Insurance in 2025") and pitch this story to earn high-authority backlinks.
    *   **Expert Contributions:** Offer our internal experts for quotes and commentary in financial news articles.

*   **Specifically for AI Engines:**
    *   **Building Citations:** When our data or experts are cited on other authoritative sites (like the BBC, MoneySavingExpert, etc.), AI models recognize this as a strong signal of our authority and trustworthiness.
