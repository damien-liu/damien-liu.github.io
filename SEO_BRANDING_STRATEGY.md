# SEO & Branding Strategy — Damien Liu

## Status: ✅ Implemented

This document covers all changes made and strategic recommendations for
`damien-liu.github.io`.

---

## 1. Tagline & Power Slogans

**Previous:** `Self-Taught Software Engineer | AI & Data Science Enthusiast | Lifelong Learner 🧑🏻‍💻`

**Problems identified:**
- "Self-Taught" — undercuts authority; signals junior positioning
- "Enthusiast" — implies hobbyist, not practitioner
- "Lifelong Learner" — filler phrase that communicates nothing differentiating
- Emoji — reduces perceived professionalism in search snippets

### ✅ Implemented (Variation A — selected):
> **Software Engineer × AI Automation × Financial Data Science — Tokyo**

### Alternative Variations:

**Variation B** (impact-forward):
> **Engineering AI Systems That Move Markets — Tokyo**

**Variation C** (consulting-oriented):
> **AI Automation · Quantitative Engineering · Cross-Domain Solutions**

**Rationale:** The `×` symbol visually signals "intersection" rather than the generic pipe `|`. Ending with "Tokyo" provides geo-authority and is a valuable local SEO signal for "Tokyo-based developer" queries.

---

## 2. Meta Strategy

### ✅ Title Tag (implemented in `config.toml`)
```
Damien Liu | AI & Full-Stack Engineer — Tokyo
```
- **Length:** 46 characters (within 60-char limit)
- **Signals:** Name (brandable), primary keyword, location
- **CTR optimization:** Pipe separator and em dash create visual hierarchy in SERPs

### ✅ Meta Description (implemented in `head/custom.html`)
```
Damien Liu — Tokyo-based Software Engineer specialising in AI Automation,
Financial Data Science, and full-stack systems. Building intelligent solutions
at the intersection of code and capital markets.
```
- **Length:** 155 characters
- **Keywords included:** AI Automation, Financial Data Science, Tokyo-based, Software Engineer
- **CTA implicit:** "Building intelligent solutions" suggests deliverable value

---

## 3. JSON-LD Structured Data (implemented)

### Person Schema
Located in `layouts/partials/head/custom.html`. Includes:
- Full name, alternate name, avatar image URL
- Job title: "Software Engineer"
- `knowsAbout`: 12 skill/topic entries
- `hasCredential`: 4 Japanese certifications (Boki, Takken, FP, FE/AP)
- `workLocation`: Tokyo, Japan (with PostalAddress)
- `sameAs`: GitHub + LinkedIn (expandable)

### WebSite Schema
- Site name matching title tag
- `potentialAction` → SearchAction for sitelinks search box eligibility
- Publisher set as Person (individual site, not organization)

### BlogPosting Schema (per-article, automatic)
- Headline, description, dates, word count, categories, tags
- Author linked back to root site
- `mainEntityOfPage` for canonical signaling

**Validation:** After deploying, validate at https://search.google.com/test/rich-results

---

## 4. Information Architecture — Link Equity Strategy

### Current Structure
```
damien-liu.github.io (root)          ← Professional landing
    └── /p/{slug}/                   ← Blog posts (same domain)
    └── /about/                      ← NEW: About page
    └── /archives/                   ← Archive listing
    └── /search/                     ← Search
```

### Recommendations for Root ↔ Blog Subdomain (if migrating blog to `blog.damien-liu.github.io`)

**Option A — Keep Single Domain (RECOMMENDED):**
Your current setup (`/p/` posts on the root domain) is already optimal for link equity. All backlinks, domain authority, and topical signals consolidate on a single domain. **Do not split** unless you have a strong operational reason.

**Option B — If You Must Use a Subdomain:**
1. Add a **prominent "Blog" link** in the root site navigation pointing to `blog.damien-liu.github.io`
2. On every blog post, include an **author bio block** linking back to `https://damien-liu.github.io/about/`
3. Add `rel="author"` to the link
4. Cross-reference blog posts from the About page's "Featured Work" section
5. Use consistent `sameAs` and canonical URLs in JSON-LD across both properties
6. Submit **both** properties to Google Search Console

### Internal Linking Best Practices (Immediate Actions):
- [ ] Link from the About page to your best 2-3 blog posts
- [ ] In each blog post, add a contextual link to the About page or relevant other posts
- [ ] Use descriptive anchor text (e.g., "AI token optimization guide" not "click here")

---

## 5. Side-Hustle Keywords — High-Value Long-Tail Targets

These keywords target **consulting/service queries** with commercial intent:

| # | Keyword | Monthly Search Volume (est.) | Intent | Difficulty |
|---|---------|-----|--------|------------|
| 1 | **"AI automation consultant Tokyo"** | 50-150 | Commercial | Low |
| 2 | **"financial data analysis Python freelance"** | 100-300 | Commercial | Medium |
| 3 | **"AI agent development consulting"** | 200-500 | Commercial | Medium |
| 4 | **"stock analysis automation Python developer"** | 50-200 | Commercial | Low |
| 5 | **"bilingual software engineer Japan freelance"** | 30-100 | Commercial | Low |

### Content Strategy to Rank for These Keywords:
1. **Pillar Post:** "How I Built an AI-Powered Stock Analysis Pipeline" (targets #4)
2. **Case Study:** "Reducing AI Agent Costs by 90%" (you already have this — optimize for #3)
3. **Service Page:** Create a `/consulting/` page describing your offerings (targets #1, #2)
4. **Comparison Post:** "Python vs. R for Financial Data Science in 2026" (targets #2)
5. **Portfolio Piece:** "Cross-Cultural Engineering: Building for the Japanese Market" (targets #5)

---

## 6. Files Created / Modified

### Created:
| File | Purpose |
|------|---------|
| `layouts/partials/head/custom.html` | JSON-LD structured data + meta tags |
| `content/page/about/index.md` | Professional About page |

### Modified:
| File | Change |
|------|--------|
| `config/_default/config.toml` | Title tag → `Damien Liu \| AI & Full-Stack Engineer — Tokyo` |
| `config/_default/params.toml` | Sidebar subtitle → Power Slogan; OG image enabled |

---

## 7. Post-Deploy Checklist

- [ ] Run `hugo` and verify the site builds without errors
- [ ] Validate JSON-LD at [Google Rich Results Test](https://search.google.com/test/rich-results)
- [ ] Submit sitemap to [Google Search Console](https://search.google.com/search-console)
- [ ] Verify Open Graph tags with [Facebook Debugger](https://developers.facebook.com/tools/debug/)
- [ ] Verify Twitter Card with [Twitter Card Validator](https://cards-dev.twitter.com/validator)
- [ ] Review the About page renders correctly at `/about/`
- [ ] Check all internal links resolve (About → posts, posts → About)
- [ ] Consider adding a `/consulting/` or `/services/` page for direct lead generation

---

*Strategy authored for Damien Liu — February 2026*
