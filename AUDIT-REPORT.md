# The Hub Anoka — Website Audit Report
**Date:** March 7, 2026
**URL:** https://www.thehubanoka.com
**Platform:** Wix
**Prepared for:** Luke Kroeplin

---

## Executive Summary

The Hub's current Wix site has a warm brand identity and decent imagery, but suffers from significant SEO, performance, accessibility, and conversion issues that are limiting its ability to attract new customers and rank in search results. The site is essentially invisible to AI search tools (ChatGPT, Perplexity, Google AI Overviews) due to missing structured data, poor heading hierarchy, and thin content.

---

## Critical Issues (Blockers)

### 1. H1 Tag is "When to shop" — Not the Business Name or Value Prop
- **Impact:** Google and AI crawlers use H1 as the primary signal for what a page is about. "When to shop" tells nothing about the business.
- **Fix:** H1 should be "The Hub — Home Decor, Gifts & Boutique in Anoka, MN"

### 2. Heading Hierarchy is Broken — Entire Page Content Stuffed into H3 Tags
- **Impact:** The "Welcome to The Hub" section and the owners' bio are both inside `<h3>` tags as massive text blocks (200+ words each). Search engines see these as headings, not content. This destroys readability scoring and confuses crawlers.
- **Fix:** Move body text to `<p>` tags. Use proper heading hierarchy (H1 → H2 → H3).

### 3. No Open Graph Image
- **Impact:** When someone shares the site on Facebook, Instagram, or iMessage, there's no preview image. This kills social sharing and referral traffic — critical for a local boutique.
- **Fix:** Add `og:image` meta tag with the storefront or logo image.

### 4. Four Images Have No Alt Text (31% of all images)
- **Impact:** Accessibility violation (WCAG 2.1 Level A failure), plus Google Image Search can't index these. The gallery images — which showcase the actual store interior — have zero alt text.
- **Fix:** Add descriptive alt text to all images.

### 5. No Robots Meta Tag
- **Impact:** While not blocking crawling, explicit robots directives are a best practice signal. Combined with Wix's JavaScript-heavy rendering, some crawlers may struggle.
- **Fix:** Add `<meta name="robots" content="index, follow">`.

---

## High Severity Issues

### 6. Wix Performance Tax — JavaScript-Heavy Rendering
- **Impact:** Wix sites load 50-200+ JavaScript files, resulting in poor Core Web Vitals (LCP, CLS, FID). Google uses these as ranking signals. Typical Wix PageSpeed score: 20-40/100 on mobile.
- **Fix:** Migrate to static HTML/CSS on Cloudflare Pages (this project). Expected PageSpeed: 90+/100.

### 7. No Structured Data for Products, Events, or Hours
- **Impact:** The existing LocalBusiness schema is minimal — no `openingHours`, no `priceRange`, no `hasOfferCatalog`. Events page has zero schema. Google can't generate rich snippets for events or hours.
- **Fix:** Add comprehensive LocalBusiness schema with openingHours, plus Event schema on events page.

### 8. Thin Content — Homepage Has ~300 Words of Actual Content
- **Impact:** Modern SEO requires 500-1000+ words of topically relevant content. AI search tools need clear, structured text to extract and cite. The homepage is mostly images with two large story paragraphs that aren't structured for scannability.
- **Fix:** Add sections for product categories, community involvement, and location information with proper headings.

### 9. No Google Business Profile Integration
- **Impact:** No link to or from Google Business Profile. No reviews widget. For a local boutique, Google Business Profile is the #1 discovery channel.
- **Fix:** Add link to Google Business Profile, embed reviews if available.

### 10. Events Page is Static — Monthly PDFs/Images with No SEO Value
- **Impact:** Events are shown as three static cards (February, March, April) that link to... nothing visible in the crawl. No event names, dates, descriptions, or structured data. This is zero SEO value for event-related searches.
- **Fix:** List events with proper markup, dates, and Event schema.

---

## Medium Severity Issues

### 11. Contact Form Collects Unnecessary Fields
- **Impact:** Phone and Address fields on a contact form for a boutique create friction. Every extra field reduces submission rate by ~10%.
- **Fix:** Simplify to Name, Email, Message.

### 12. "Log In" Button with No Clear Purpose
- **Impact:** Confuses visitors. There's no membership program or account functionality visible. It's a default Wix element.
- **Fix:** Remove unless there's an active membership/loyalty program.

### 13. Duplicate Contact Info — Appears 3 Times on Homepage
- **Impact:** Email, phone, and address appear in the header, contact section, and footer. Clutters the page.
- **Fix:** Keep in footer (always visible) and contact section. Remove from header bar — use that space for a CTA instead.

### 14. Copyright Says "©2022" — Outdated
- **Impact:** Signals neglect to visitors and crawlers.
- **Fix:** Auto-update to current year.

### 15. No Email Signup / Newsletter
- **Impact:** Missing the #1 owned-audience channel for retail. No way to capture visitor interest for future marketing.
- **Fix:** Add email signup with clear value prop ("Get first access to new arrivals & event invites").

### 16. No Product Category Showcasing
- **Impact:** The site mentions "home decor, self care items, gifts, accessories, women's clothing, and faith based items" in text but doesn't visually showcase any categories. Visitors can't browse or get excited about products.
- **Fix:** Add visual category cards linking to relevant content.

---

## Low Severity Issues

### 17. Image File Names Are Wix Hashes
- **Impact:** `6a3473_3b612ca1d9024aeeb0760c1a1e251200~mv2.png` tells Google nothing. Descriptive filenames improve image SEO.
- **Fix:** Rename to descriptive names (storefront.jpg, jessica-jordan-owners.jpg, etc.).

### 18. No Favicon Customization
- **Impact:** Minor brand polish issue.
- **Fix:** Add custom favicon matching the Hub logo.

### 19. "Proudly created with Wix.com" in Footer
- **Impact:** Unprofessional for a business site. Links equity to Wix.
- **Fix:** Remove in rebuild.

### 20. Hours Section Uses Stock Image Background
- **Impact:** The hours section uses a stock "Image by Jon Tyson" (inspirational text photo) instead of the actual store. Missed opportunity for brand reinforcement.
- **Fix:** Replace with store interior image.

---

## AI Search Readiness Assessment

| Signal | Status | Impact |
|--------|--------|--------|
| Clear entity identification | ⚠️ Partial — name in schema but H1 is wrong | High |
| Structured FAQ content | ❌ Missing | Medium |
| Product/service categories defined | ❌ Missing | High |
| Location clearly stated with schema | ✅ Basic schema present | Low |
| Opening hours in schema | ❌ Missing from schema | High |
| Content structured with headings | ❌ Broken hierarchy | Critical |
| Unique, non-generic descriptions | ⚠️ Present but not structured | Medium |
| Event information crawlable | ❌ Not crawlable | High |

**AI Search Score: 2/10** — An AI search tool asked "What is The Hub in Anoka MN?" would struggle to provide a useful answer from this site's content.

---

## Recommendation

Rebuild as a static site (HTML/CSS/JS) deployed to Cloudflare Pages with:
- Proper semantic HTML and heading hierarchy
- Comprehensive structured data (LocalBusiness + Event + BreadcrumbList)
- Optimized images with descriptive filenames and alt text
- Core Web Vitals score targeting 90+
- AI-search-ready content structure
- Email capture integration
- Mobile-first responsive design

This is what we're building now.
