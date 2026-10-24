# Awaken Coffee: Shopify Theme

A responsive Shopify storefront for a fictional coffee brand, built from a Figma design as a practice project. It is built on Shopify's Skeleton starter theme.

**Live preview:** [preview link] (storefront password: [password])

![Awaken Coffee homepage](./screenshots/home.png)

## Design credit

Layout and styling are based on the "Ecommerce Shopping Store Coffee" Figma Community file by [creator name] ([link to the file page]), used under the license stated on that page ([license, for example CC BY 4.0]). I rebuilt it in Liquid with English copy and a left-to-right layout. Product photos are from Pexels. Sample reviews are placeholder content, not real customers.

## What I built

Custom sections, all configurable in the theme editor:

- **Hero:** image picker, heading, subtext and button, with the photo blended into a gradient background
- **Category tiles:** built with blocks, so tiles can be added, removed and reordered
- **Featured products:** a grid driven by a collection setting, with square crops, lazy-loaded responsive images and an empty-collection fallback
- **Promo banner:** heading, text, button and a background color setting
- **Testimonials:** built with blocks

Restyled Skeleton templates, keeping the original form logic:

- **Header:** centered logo, main menu and accessible account and cart links, collapsing to two rows on phones
- **Footer:** newsletter signup using Shopify's customer form, footer links and payment icons
- **Product page:** two-column layout with sticky details on desktop, a variant selector that hides for single-variant products, a quantity field and a sold-out state
- **Cart page:** line items, line totals, subtotal and an empty-cart state

Theme-wide work:

- CSS variables for the palette and fonts in `assets/awaken-theme.css`
- Full-width section backgrounds using Skeleton's `full-width` utility class
- A dark page backdrop that frames the content on wide screens
- Mobile-first layouts, checked at phone width

## Performance and accessibility

Lighthouse (mobile, simulated slow 4G, development store):

| Performance |
