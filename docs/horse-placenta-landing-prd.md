# Horse-Placenta Hangover Remedy - Traffic Test PRD  
Date: 7 July 2025  

---

## 1. Objective  
Run a one-week traffic test to gauge demand for a Japanese horse-placenta hangover remedy in the United States. Drive paid traffic from Facebook lead-gen ads to a single-page site that captures emails for a launch discount.

---

## 2. Success Metrics  

| Metric | Target | Why it matters |
| --- | --- | --- |
| Link CTR | > 1 % | Confirms ad copy and creative resonate |
| Cost per lead | < $5 | Acquisition must stay affordable for scale |
| Leads collected | ≥ 50 in 7 days | Provides a base for qualitative follow-up |

---

## 3. Personas  

1. **Social Drinker – “Kim (29)”**  
   Enjoys nightlife, wants a fast morning recovery.  

2. **Bio-hacker – “James (35)”**  
   Experiments with novel supplements and Japanese wellness products.

---

## 4. User Stories  

- *As Kim,* I want to see the benefit immediately and join the waitlist in one click.  
- *As James,* I need a short, credible explanation of why horse placenta works before sharing my email.

---

## 5. Functional Requirements  

| ID | Requirement |
|----|-------------|
| F-1 | Headline: “Feel human after a big night - Japan’s horse-placenta fix.” |
| F-2 | Hero section with product mockup or lifestyle image (supplied externally). |
| F-3 | Two-line benefit statement plus micro “Why horse placenta?” blurb. |
| F-4 | Inline email capture or single button that scrolls to the form. |
| F-5 | Form posts to **Zapier Webhook**; Zap stores email to Google Sheet or Airtable. |
| F-6 | Thank-you confirmation replaces the form after submit. |
| F-7 | Facebook Pixel and GA4 fire PageView on load and Lead on submit. |
| F-8 | Page loads in < 1 s on 3 G and passes Core Web Vitals. |

---

## 6. Non-Functional Requirements  

- Mobile-first responsive design up to 1440 px.  
- WCAG AA color contrast.  
- Dependencies limited to Tailwind CDN and vanilla JS (Alpine optional).  
- Lighthouse performance: 100 on desktop, ≥ 90 on mobile.

---

## 7. Tech Stack  

| Layer | Implementation |
|-------|----------------|
| Front-end | Static `index.html` with Tailwind CDN. |
| Email capture | Zapier Webhook (POST). |
| Hosting | **Netlify free plan using platform sub-domain** (example `placentareset.netlify.app`). |
| Analytics | Facebook Pixel and GA4 via gtag. |

---

## 8. Build Flow inside Cursor  

1. Scaffold repository `horse-placenta-landing`.  
2. Create `index.html` satisfying F-1 to F-8, using Tailwind classes.  
3. Paste Zapier Webhook URL into the `<form action="">`.  
4. Add JS that hides the form and shows the thank-you message after a successful `fetch()`.  
5. Insert Pixel and GA4 snippets.  
6. Copy externally created hero image into `/static/hero.jpg` and update `<img src="">`.  
7. Commit to Git and deploy to Netlify; confirm sub-domain URL works.

---

## 9. Ad Test Parameters  

- **Platform:** Facebook Lead Generation objective.  
- **Budget:** $10 / day for 7 days.  
- **Ad sets (3 to 5):** social drinkers, nightlife, bio-hackers, Japanese wellness fans.  
- **Creatives:** one static image (matches hero) and one short reel.  
- Pause any ad set once CPL > $5 after 20 leads.

---

## 10. Launch Checklist  

| Item | Tool | Pass condition |
|------|------|----------------|
| Mobile layout | Chrome dev tools | No overflow; CTA visible on first scroll |
| Form submit | Live site | Email arrives in Zap destination |
| Page speed | PageSpeed Insights | LCP < 2 s on mobile |
| Pixel events | FB Events Manager | PageView and Lead fire successfully |

---

*End of PRD – copy this file into* `/docs/horse-placenta-landing-prd.md` *inside Cursor to keep everyone aligned.* 