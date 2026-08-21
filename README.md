# Optivize AI — AI-Powered Business Automation SaaS Platform

**Course Subject**: Advanced Web Technologies (CSE0309) — Mini Hackathon Project

## Project Description

**Optivize AI** is an enterprise-grade AI SaaS web application designed to help businesses automate tasks, run predictive analytics, and maintain rigorous data security. Built strictly using pure HTML5 and CSS3 (with zero JavaScript or third-party JS frameworks), the project implements a green-tinted modern design system extracted from high-converting SaaS landing pages. It features pure CSS keyframe entrance animations, card hover elevations, responsive multi-column layouts, accessibility-focused semantic markup, and a pure CSS hamburger menu using the checkbox hack for mobile viewports.

---

## Technologies Used

- **HTML5**: Semantic document structuring (`header`, `nav`, `main`, `section`, `article`, `footer`), native form controls, and accessible media markup.
- **CSS3**: Custom properties (variables), Flexbox, CSS Grid, media queries for responsiveness, keyframe animations, backdrop filters, glassmorphic header, and pure CSS checkbox hack navigation.
- **No JavaScript**: 100% JS-free implementation adhering strictly to hackathon specifications.

---

## Directory Structure

```
OptivizeAI/
├── index.html          → Home Page (Hero, Trust Stats, Features, Services Preview, Pricing, Testimonials, CTA)
├── about.html          → About Page (Banner, Company Story, Mission & Vision, 4-Member Team Grid)
├── services.html       → Services Page (Banner, 6 Service Cards Grid, Enterprise Quote CTA)
├── login.html          → Login Page (Centered Auth Card, Form Controls, Remember Me)
├── register.html       → Register Page (Centered Signup Card, Radio buttons, Select dropdown, Checkboxes)
├── payment.html        → Payment Page (Order Summary HTML Table, Credit Card Form)
├── legal.html          → Legal & Policies Page (Privacy Policy, Terms of Service, Refund Policy)
├── css/
│   ├── style.css       → Resets, design tokens/variables, typography, animations, global utilities
│   ├── components.css  → Navbar, footer, buttons, cards, forms, tables, badges, UI widgets
│   └── responsive.css → Media queries for Desktop (>1024px), Tablet (768px-1024px), and Mobile (<768px)
├── images/             → High-resolution local image assets with descriptive alt tags
└── README.md           → Project documentation and AI prompt log
```

---

## How to Run

1. Clone or navigate to the project directory:
   ```bash
   cd OptivizeAI
   ```
2. Open `index.html` in any web browser (Google Chrome, Mozilla Firefox, Safari, Microsoft Edge). No server build step or npm package installation is required!

---

## Prompts Used During Development

Below is the full sequence of AI prompts used to design, structure, and build the Optivize AI platform one component and page at a time:

### Prompt 0 — Project Context & Setup
```
I'm building a 7-page responsive business website using ONLY HTML5 and CSS3 (no JavaScript, no frameworks). This is a mini-hackathon and I will ask you to build ONE page or ONE component at a time — do not generate anything yet, just remember this context for the prompts that follow.

Design system to follow on every component:
- Primary green: #22c55e, hover green: #16a34a
- Dark green accent (for highlighted/CTA sections): #123524
- Light green section background: #eafbef
- Text: headings #111827, body #6b7280, white #ffffff
- Cards: white background, border-radius 18px, box-shadow 0 8px 24px rgba(0,0,0,0.06), hover lifts with transform: translateY(-6px) and a stronger shadow (transition 0.3s ease)
- Buttons: pill-shaped (border-radius 999px), solid green primary / outlined white secondary, hover = darker green + slight scale(1.04), transition 0.3s ease
- Font: a clean sans-serif (system-ui, "Segoe UI", or import "Poppins"/"Inter" from Google Fonts)
- Container max-width: 1200px, centered, consistent horizontal padding
- Use semantic HTML5 tags: header, nav, main, section, footer, article where relevant
- Use CSS-only animations: fadeInUp keyframe on hero/heading elements on load, transition-based hover effects on cards, buttons, and nav links — no JavaScript
- Split CSS across: css/style.css (resets, variables, typography, base layout), css/components.css (navbar, footer, buttons, cards, forms), css/responsive.css (all media queries)
- Images live in /images/ and every <img> must have descriptive alt text

Confirm you understood, then wait for my next prompt.
```

### Prompt 1 — Navbar Component
```
Create only this component: the Navbar.

Build the HTML for a sticky navbar (semantic <header><nav>) with:
- Logo/site name on the left ("Optivize AI")
- Center nav links: Home, About, Services, Pricing, Login
- A pill-shaped green "Get Started" button on the right, linking to register.html
- Mobile: nav links should collapse using a CSS-only hamburger technique (checkbox hack — <input type="checkbox"> + <label>, no JavaScript)

Then give me the matching CSS for css/components.css only (navbar styles, hover underline effect on links, sticky/shadow-on-scroll look, mobile checkbox-menu styles). Follow the design system from before. Output the navbar as an HTML snippet I will paste into every page, and the CSS separately.
```

### Prompt 2 — Footer Component
```
Create only this component: the Footer.

Build the HTML (semantic <footer>) with:
- Left: logo + one-line description + 4 social icon links (use simple inline SVGs or text labels, no JS)
- 3 link columns: "Product" (Features, Pricing, Services), "Company" (About, Legal, Careers), "Support" (Help Center, Contact, FAQ)
- A small newsletter signup: email input + "Subscribe" button (form has no real action, just static markup)
- Bottom bar: © 2026 Optivize AI. All rights reserved. + Privacy Policy / Terms links pointing to legal.html

Then give me the CSS for css/components.css only (dark background section, grid layout for the columns, input/button styling matching the design system).
```

### Prompt 3 — Home Page (index.html)
```
Create only this page: index.html (Home).

Use the Navbar and Footer components already built. Between them, build:
1. Hero section: small pill badge above heading reading "Your All-in-One AI SaaS Platform", large heading "Supercharge Your Business with AI-Powered Automation" + a subheading about saving time and cutting costs with AI, two CTA buttons (primary "Start Free Trial", secondary "Book a Demo"), hero image from /images/hero-main.jpg with descriptive alt text, CSS fadeInUp animation on load
2. Trust/stats strip: 4 quick stats in a flex row ("500+ Companies Trust Us", "99.9% Uptime SLA", "50M+ Tasks Automated", "4.9★ Average Rating")
3. Features section: section title centered, then 3 alternating left/right blocks (icon badge + heading + short paragraph + "Learn More" link, paired with an image: feature-automation.jpg, feature-analytics.jpg, feature-security.jpg)
4. Services preview: 3–4 card grid teasing services.html (icon, title, one-line description), with hover-lift on cards, and a "View All Services" button linking to services.html
5. Short About teaser: 2-column layout (text + image), "Learn More" button linking to about.html
6. CTA banner: dark green rounded section with heading + 2 buttons before the footer

Use Flexbox/Grid, semantic HTML5, and write the CSS for the page-specific layout into css/style.css (reuse card/button styles already defined in components.css — don't redefine them). Every image needs real alt text.
```

### Prompt 4 — About Page (about.html)
```
Create only this page: about.html.

Reuse the Navbar and Footer. Build:
1. Page header banner: heading "About Optivize AI" + short subtext, background image images/about-banner.jpg with a dark overlay for text contrast
2. Company story: 2-column text + image section
3. Mission & Vision: 2 side-by-side cards (icon, heading, paragraph)
4. Team section: heading + 4-card grid, each card = photo (images/team-1.jpg … team-4.jpg), name, role, using the same card style as before with hover-lift

Semantic HTML5, Flexbox/Grid, alt text on every image. Add any page-specific CSS to css/style.css.
```

### Prompt 5 — Services Page (services.html)
```
Create only this page: services.html.

Reuse Navbar and Footer. Build:
1. Page header banner: "Our Services" heading + subtext
2. A responsive grid of 6 service cards for these Optivize AI modules — each with image (images/service-1.jpg through service-6.jpg), title, short description, price tag (optional), "Learn More" button, same card style/hover-lift as the rest of the site:
   1. Automated Task Management
   2. Predictive Analytics
   3. Data Security & Compliance
   4. Third-Party Integrations
   5. 24/7 Priority Support
   6. Custom AI Solutions

Semantic HTML5, CSS Grid for the card layout, alt text on every image. Page-specific CSS goes in css/style.css.
```

### Prompt 6 — Login Page (login.html)
```
Create only this page: login.html.

Reuse Navbar and Footer. Build a centered login card containing:
- Heading "Welcome Back"
- Email input, Password input (proper <label>s, semantic <form>)
- "Remember Me" checkbox
- "Forgot Password?" link
- Pill-shaped green "Login" submit button (no real action — just static form)
- "Don't have an account? Register" link pointing to register.html

Style the form with the same input focus states (green border/glow on :focus), same card shadow/radius as the rest of the site. CSS goes in css/style.css (or components.css if you want reusable form input styles — your call, keep it consistent).
```

### Prompt 7 — Register Page (register.html)
```
Create only this page: register.html.

Reuse Navbar and Footer. Build a centered registration card with a <form> containing:
- Full Name, Email, Password, Confirm Password (text/email/password inputs)
- Phone (tel input)
- Gender: radio buttons (Male / Female / Other), styled to match the green theme
- Plan of Interest: a <select> dropdown with options: Starter (Free), Pro ($49/mo), Enterprise ($99/mo)
- Terms & Conditions checkbox with a link to legal.html
- Pill-shaped green "Create Account" submit button
- "Already have an account? Login" link pointing to login.html

Keep the same card/input styling system as login.html. Add any new styles to css/style.css, reusing input/label rules already defined.
```

### Prompt 8 — Payment / Checkout Page (payment.html)
```
Create only this page: payment.html.

Reuse Navbar and Footer. Build two side-by-side cards (stack on mobile):
1. Order Summary card: a <table> with columns Product, Quantity, Price, Total, 3–4 sample rows, and a bold Grand Total row
2. Payment Form card: Card Number, Expiry Date, CVV, Name on Card inputs, plus a small note "This is a static demo page — no real payment will be processed", and a pill-shaped green "Pay Now" button

Same card/input styling as the rest of the site. Table should be responsive (scrolls or stacks on small screens). CSS additions go in css/style.css.
```

### Prompt 9 — Legal / Privacy Policy Page (legal.html)
```
Create only this page: legal.html.

Reuse Navbar and Footer. Build a clean, readable typographic page (no cards needed) inside a centered max-width container, with:
- H1 "Legal & Policies"
- Section: Privacy Policy (heading + 2–3 paragraphs)
- Section: Terms & Conditions (heading + 2–3 paragraphs)
- Section: Refund Policy (heading + 1 short paragraph)
Use proper heading hierarchy (h1 > h2), <article>/<section> tags, generous line-height and spacing for readability, matching the site's font and color system. Add page-specific CSS to css/style.css.
```

### Prompt 10 — Responsive Layer (responsive.css)
```
Create only this: the full css/responsive.css file.

Given the site is built with a navbar, footer, hero, feature blocks, card grids (services/team/pricing), forms (login/register/payment), and a table (payment), write media queries for:
- Desktop: default (already styled)
- Tablet (max-width: 1024px): reduce container padding, adjust grid columns to 2
- Mobile (max-width: 768px): stack all grids/flex rows to 1 column, switch navbar to the checkbox-hamburger mobile menu, shrink hero heading font-size, make the payment summary table scroll horizontally or convert to stacked rows, full-width buttons

Only output the media query rules — assume base styles already exist in style.css/components.css.
```

### Prompt 11 — README.md
```
Create only this: README.md for the project.
```
