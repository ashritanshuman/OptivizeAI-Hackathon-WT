# Mini Hackathon — Build Guide & Prompt Pack
### Subject: Advanced Web Technologies (CSE0309) — HTML5 + CSS3 Only

## Project Topic

**"Optivize AI" — AI-Powered Business Automation SaaS Platform**

Taken directly from the attached UI reference. The site sells an AI SaaS product
that helps businesses automate tasks, predict outcomes, and secure their data —
so the 7 required pages are framed around that product instead of a generic business:

- **Home** — pitch the platform (hero, stats, features, pricing teaser)
- **About** — the company behind Optivize AI, its mission, and team
- **Services** — the individual AI features/modules sold as "services" (Automation, Analytics, Security, Integrations, Support, Custom AI)
- **Login / Register** — customer portal access to the platform dashboard
- **Payment** — checkout for a subscription plan (Starter/Pro/Enterprise)
- **Legal** — privacy policy, terms, and refund policy for the SaaS subscription

Use **"Optivize AI"** as the business name everywhere a name is needed in the prompts below.

This document has two parts:
1. **Analysis** — what the PDF requires + what the "Optivize AI" UI reference tells us about the visual system.
2. **Prompt Pack** — a ready-to-use, one-piece-at-a-time prompt for every component/page, exactly as the hackathon rules demand ("Create only this page/component"). Copy each prompt **one at a time, in order**, into your AI tool.

---

## PART 1 — ANALYSIS

### 1.1 What the PDF requires (hard constraints)

| Rule | Detail |
|---|---|
| Tech | HTML5 + CSS3 **only** — no JS-dependent effects, no frameworks |
| Prompting | One page/component per AI request — never "build the whole site" |
| Folder structure | Fixed, exact — see below |
| Pages | 7 total: Home, About, Services, Login, Register, Payment, Legal |
| Navbar/Footer | Identical across all 7 pages |
| Layout | Flexbox and/or Grid |
| Responsiveness | Mobile, tablet, desktop |
| Extras | Hover effects, alt text on all images, semantic tags (`header`, `nav`, `main`, `section`, `footer`), good typography/color |
| Submission | README.md with project description + full list of AI prompts used |

**Compulsory folder structure:**
```
project-name/
├── index.html
├── about.html
├── services.html
├── login.html
├── register.html
├── payment.html
├── legal.html
├── css/
│   ├── style.css        → resets, variables, typography, global layout
│   ├── components.css   → navbar, footer, buttons, cards, forms, pricing table
│   └── responsive.css   → all @media queries
├── images/
└── README.md
```

### 1.2 Reading the reference UI ("Optivize AI")

The screenshot is a green-and-white SaaS landing page. Since your project is a **general business site** with Home/About/Services/Login/Register/Payment/Legal pages (not a SaaS product), you're not cloning it page-for-page — you're **borrowing its design system** (colors, spacing, card style, button style, section rhythm) and applying that system consistently across your 7 required pages.

**Design tokens extracted from the image:**

- **Primary green:** `#22c55e` (buttons, icons, accents) — darker shade `#16a34a` for hover/active
- **Deep green (dark cards / footer CTA):** `#0f2e1a` to `#123524`
- **Background tint (section backgrounds):** very light green `#eafbef` / `#f2fbf4`
- **Neutral text:** near-black `#111827` for headings, gray `#6b7280` for body copy
- **Surface:** white `#ffffff` cards with `border-radius: 16–20px` and soft shadow `0 8px 24px rgba(0,0,0,0.06)`
- **Buttons:** pill-shaped (`border-radius: 999px`), solid green primary / white-with-border secondary, both with hover lift + shadow transition
- **Typography:** large bold sans-serif headings (~48–56px hero), medium body (~16px), generous line-height
- **Layout pattern:** centered max-width container (~1200px), alternating left/right image+text feature blocks, 3-column card grids, badge/pill labels above headings

**Sections identified in the reference (top to bottom):**
1. Sticky navbar — logo left, nav links center, pill CTA button right
2. Hero — pill badge, big heading, subtext, two CTA buttons
3. Stats/dashboard preview strip — 4–5 small metric cards, one dark "highlight" card
4. Trust bar — 4 quick stats in a row (companies, uptime, tasks, rating)
5. "Transforming Every Industry" — left accordion list, right screenshot mockup
6. Section title — centered heading + subheading
7. Three alternating feature blocks (icon badge → heading → text → "Learn More" link, paired with a graphic)
8. "Get Started in 3 Steps" — 3-column numbered cards
9. Pricing — 3 cards, middle one highlighted/elevated as "Most Popular"
10. Testimonials — 2 cards with avatar, name, star rating, big stat number
11. Dark CTA banner with two buttons + mockup image
12. Footer — logo/description/socials + 4 link columns incl. newsletter signup, bottom bar with copyright + legal links

### 1.3 Mapping the UI system onto your 7 pages

| Page | How the design system applies |
|---|---|
| **index.html** | Full hero + trust stats strip + 3 alternating feature blocks + 3-step section + pricing (optional but matches "Features/Services preview" requirement) + short About teaser + footer |
| **about.html** | Hero-style header banner (smaller), Mission/Vision as 2 cards, Team section as a 3–4 column card grid (same card style as pricing/feature cards) |
| **services.html** | Section title style from UI + 6+ service cards in a grid (same card shadow/radius/hover-lift as the feature cards) |
| **login.html** | Centered card (same white card style), pill button, green accents on focus states |
| **register.html** | Same card style, longer form, radio/checkbox styled to match the green theme |
| **payment.html** | Order summary styled as a table inside a white card; payment form in a second card; pill "Pay Now" button |
| **legal.html** | Clean typographic page using the same container width, section spacing, and heading style — no cards needed, just readable typography |

Navbar and footer (sections 1 and 12 above) are built **once** and reused verbatim on all 7 pages.

### 1.4 Animation plan (CSS3-only — no JS)

Since the brief is HTML+CSS only, use **pure CSS**:
- `@keyframes fadeInUp` on hero text/badge on page load
- `transition: transform .3s ease, box-shadow .3s ease` on all cards → lift + shadow grow on `:hover`
- Buttons → `transition` on `background-color`, `transform: scale(1.04)` on `:hover`
- Nav links → underline-grow effect via `::after` + `transition`
- Accordion (About/Industry-style list, if used) → pure CSS `details/summary` or `:checked` + `max-height` transition trick
- Pricing "Popular" card → subtle `transform: scale(1.05)` static elevation, plus hover lift on the others

### 1.5 Unsplash image plan

Go to **unsplash.com**, search each term below, download a **landscape** photo for heroes/banners and a **square-ish** photo for cards, save into `/images/` with the exact filename listed (so your HTML `src` paths just work):

| Section | Search term on Unsplash | Suggested filename |
|---|---|---|
| Hero / home banner | `business team meeting` or `startup office` | `hero-main.jpg` |
| Dashboard/mockup graphic | `analytics dashboard laptop` | `dashboard-preview.jpg` |
| Feature block 1 | `automation technology` | `feature-automation.jpg` |
| Feature block 2 | `data analytics chart` | `feature-analytics.jpg` |
| Feature block 3 | `data security` | `feature-security.jpg` |
| About — team | `professional portrait` (get 4 different ones) | `team-1.jpg` … `team-4.jpg` |
| About — mission banner | `office collaboration` | `about-banner.jpg` |
| Services — 6 cards | `workflow automation` (1), `data analytics chart` (2), `cybersecurity data` (3), `api integration technology` (4), `customer support headset` (5), `artificial intelligence code` (6) | `service-1.jpg` … `service-6.jpg` |
| Testimonials avatars | `business portrait headshot` | `avatar-1.jpg`, `avatar-2.jpg` |
| Footer/CTA banner | `city skyline business` | `cta-banner.jpg` |

Always add real, descriptive `alt` text (e.g. `alt="Two colleagues reviewing analytics dashboard"`) — it's a scored requirement.

---

## PART 2 — PROMPT PACK (use ONE at a time)

Paste **Prompt 0** first to give your AI tool the shared context. Then paste each numbered prompt **one at a time**, in its own turn, exactly as the hackathon rules require. Save every prompt you use — you need the full list for `README.md`.

### Prompt 0 — Project context (setup, not code generation)
```
I'm building a 7-page responsive business website using ONLY HTML5 and CSS3
(no JavaScript, no frameworks). This is a mini-hackathon and I will ask you
to build ONE page or ONE component at a time — do not generate anything yet,
just remember this context for the prompts that follow.

Design system to follow on every component:
- Primary green: #22c55e, hover green: #16a34a
- Dark green accent (for highlighted/CTA sections): #123524
- Light green section background: #eafbef
- Text: headings #111827, body #6b7280, white #ffffff
- Cards: white background, border-radius 18px, box-shadow 0 8px 24px rgba(0,0,0,0.06),
  hover lifts with transform: translateY(-6px) and a stronger shadow (transition 0.3s ease)
- Buttons: pill-shaped (border-radius 999px), solid green primary / outlined white secondary,
  hover = darker green + slight scale(1.04), transition 0.3s ease
- Font: a clean sans-serif (system-ui, "Segoe UI", or import "Poppins"/"Inter" from Google Fonts)
- Container max-width: 1200px, centered, consistent horizontal padding
- Use semantic HTML5 tags: header, nav, main, section, footer, article where relevant
- Use CSS-only animations: fadeInUp keyframe on hero/heading elements on load,
  transition-based hover effects on cards, buttons, and nav links — no JavaScript
- Split CSS across: css/style.css (resets, variables, typography, base layout),
  css/components.css (navbar, footer, buttons, cards, forms), css/responsive.css (all media queries)
- Images live in /images/ and every <img> must have descriptive alt text

Confirm you understood, then wait for my next prompt.
```

### Prompt 1 — Navbar component
```
Create only this component: the Navbar.

Build the HTML for a sticky navbar (semantic <header><nav>) with:
- Logo/site name on the left ("Optivize AI")
- Center nav links: Home, About, Services, Pricing, Login
- A pill-shaped green "Get Started" button on the right, linking to register.html
- Mobile: nav links should collapse using a CSS-only hamburger technique
  (checkbox hack — <input type="checkbox"> + <label>, no JavaScript)

Then give me the matching CSS for css/components.css only (navbar styles,
hover underline effect on links, sticky/shadow-on-scroll look, mobile checkbox-menu styles).
Follow the design system from before. Output the navbar as an HTML snippet
I will paste into every page, and the CSS separately.
```

### Prompt 2 — Footer component
```
Create only this component: the Footer.

Build the HTML (semantic <footer>) with:
- Left: logo + one-line description + 4 social icon links (use simple inline SVGs or text labels, no JS)
- 3 link columns: "Product" (Features, Pricing, Services), "Company" (About, Legal, Careers),
  "Support" (Help Center, Contact, FAQ)
- A small newsletter signup: email input + "Subscribe" button (form has no real action, just static markup)
- Bottom bar: © 2026 Optivize AI. All rights reserved. + Privacy Policy / Terms links pointing to legal.html

Then give me the CSS for css/components.css only (dark background section,
grid layout for the columns, input/button styling matching the design system).
```

### Prompt 3 — Home page (index.html)
```
Create only this page: index.html (Home).

Use the Navbar and Footer components already built. Between them, build:
1. Hero section: small pill badge above heading reading "Your All-in-One AI SaaS
   Platform", large heading "Supercharge Your Business with AI-Powered Automation"
   + a subheading about saving time and cutting costs with AI, two CTA buttons
   (primary "Start Free Trial", secondary "Book a Demo"), hero image from
   /images/hero-main.jpg with descriptive alt text, CSS fadeInUp animation on load
2. Trust/stats strip: 4 quick stats in a flex row ("500+ Companies Trust Us",
   "99.9% Uptime SLA", "50M+ Tasks Automated", "4.9★ Average Rating")
3. Features section: section title centered, then 3 alternating left/right blocks
   (icon badge + heading + short paragraph + "Learn More" link, paired with an image:
   feature-automation.jpg, feature-analytics.jpg, feature-security.jpg)
4. Services preview: 3–4 card grid teasing services.html (icon, title, one-line description),
   with hover-lift on cards, and a "View All Services" button linking to services.html
5. Short About teaser: 2-column layout (text + image), "Learn More" button linking to about.html
6. CTA banner: dark green rounded section with heading + 2 buttons before the footer

Use Flexbox/Grid, semantic HTML5, and write the CSS for the page-specific layout
into css/style.css (reuse card/button styles already defined in components.css —
don't redefine them). Every image needs real alt text.
```

### Prompt 4 — About page (about.html)
```
Create only this page: about.html.

Reuse the Navbar and Footer. Build:
1. Page header banner: heading "About Optivize AI" + short subtext, background
   image images/about-banner.jpg with a dark overlay for text contrast
2. Company story: 2-column text + image section
3. Mission & Vision: 2 side-by-side cards (icon, heading, paragraph)
4. Team section: heading + 4-card grid, each card = photo (images/team-1.jpg …
   team-4.jpg), name, role, using the same card style as before with hover-lift

Semantic HTML5, Flexbox/Grid, alt text on every image. Add any page-specific
CSS to css/style.css.
```

### Prompt 5 — Services page (services.html)
```
Create only this page: services.html.

Reuse Navbar and Footer. Build:
1. Page header banner: "Our Services" heading + subtext
2. A responsive grid of 6 service cards for these Optivize AI modules — each with
   image (images/service-1.jpg through service-6.jpg), title, short description,
   price tag (optional), "Learn More" button, same card style/hover-lift as the rest
   of the site:
   1. Automated Task Management
   2. Predictive Analytics
   3. Data Security & Compliance
   4. Third-Party Integrations
   5. 24/7 Priority Support
   6. Custom AI Solutions

Semantic HTML5, CSS Grid for the card layout, alt text on every image.
Page-specific CSS goes in css/style.css.
```

### Prompt 6 — Login page (login.html)
```
Create only this page: login.html.

Reuse Navbar and Footer. Build a centered login card containing:
- Heading "Welcome Back"
- Email input, Password input (proper <label>s, semantic <form>)
- "Remember Me" checkbox
- "Forgot Password?" link
- Pill-shaped green "Login" submit button (no real action — just static form)
- "Don't have an account? Register" link pointing to register.html

Style the form with the same input focus states (green border/glow on :focus),
same card shadow/radius as the rest of the site. CSS goes in css/style.css
(or components.css if you want reusable form input styles — your call, keep it consistent).
```

### Prompt 7 — Register page (register.html)
```
Create only this page: register.html.

Reuse Navbar and Footer. Build a centered registration card with a <form> containing:
- Full Name, Email, Password, Confirm Password (text/email/password inputs)
- Phone (tel input)
- Gender: radio buttons (Male / Female / Other), styled to match the green theme
- Plan of Interest: a <select> dropdown with options: Starter (Free), Pro ($49/mo),
  Enterprise ($99/mo)
- Terms & Conditions checkbox with a link to legal.html
- Pill-shaped green "Create Account" submit button
- "Already have an account? Login" link pointing to login.html

Keep the same card/input styling system as login.html. Add any new styles to
css/style.css, reusing input/label rules already defined.
```

### Prompt 8 — Payment / Checkout page (payment.html)
```
Create only this page: payment.html.

Reuse Navbar and Footer. Build two side-by-side cards (stack on mobile):
1. Order Summary card: a <table> with columns Product, Quantity, Price, Total,
   3–4 sample rows, and a bold Grand Total row
2. Payment Form card: Card Number, Expiry Date, CVV, Name on Card inputs,
   plus a small note "This is a static demo page — no real payment will be processed",
   and a pill-shaped green "Pay Now" button

Same card/input styling as the rest of the site. Table should be responsive
(scrolls or stacks on small screens). CSS additions go in css/style.css.
```

### Prompt 9 — Legal / Privacy Policy page (legal.html)
```
Create only this page: legal.html.

Reuse Navbar and Footer. Build a clean, readable typographic page (no cards needed)
inside a centered max-width container, with:
- H1 "Legal & Policies"
- Section: Privacy Policy (heading + 2–3 paragraphs)
- Section: Terms & Conditions (heading + 2–3 paragraphs)
- Section: Refund Policy (heading + 1 short paragraph)
Use proper heading hierarchy (h1 > h2), <article>/<section> tags, generous
line-height and spacing for readability, matching the site's font and color system.
Add page-specific CSS to css/style.css.
```

### Prompt 10 — Responsive layer (responsive.css)
```
Create only this: the full css/responsive.css file.

Given the site is built with a navbar, footer, hero, feature blocks, card grids
(services/team/pricing), forms (login/register/payment), and a table (payment),
write media queries for:
- Desktop: default (already styled)
- Tablet (max-width: 1024px): reduce container padding, adjust grid columns to 2
- Mobile (max-width: 768px): stack all grids/flex rows to 1 column, switch navbar
  to the checkbox-hamburger mobile menu, shrink hero heading font-size, make the
  payment summary table scroll horizontally or convert to stacked rows, full-width buttons

Only output the media query rules — assume base styles already exist in
style.css/components.css.
```

### Prompt 11 — README.md
```
Create only this: README.md for the project.

Include:
- Project name and one-paragraph description
- Tech used: HTML5, CSS3 (Flexbox/Grid), no JS/frameworks
- Folder structure (paste the structure)
- How to run (open index.html in a browser)
- Full list of every AI prompt used during the hackathon, numbered in the order
  they were used (I will paste the list of prompts myself)
```

---

## Quick checklist before you submit
- [ ] All 7 pages present, exact filenames
- [ ] Exact folder structure (no extra/renamed folders)
- [ ] Navbar + footer identical on every page
- [ ] Every `<img>` has real alt text
- [ ] Hover effects on buttons + cards
- [ ] Flexbox/Grid used for layout
- [ ] Semantic tags throughout
- [ ] Tested at mobile/tablet/desktop widths
- [ ] README.md with prompt list included
- [ ] Images downloaded from unsplash.com into /images/ (not hotlinked)