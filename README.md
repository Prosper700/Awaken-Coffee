# Awaken Coffee: Shopify Theme

A responsive Shopify storefront for a fictional coffee brand, built from a Figma design as a practice project. It is built on Shopify's Skeleton starter theme.

**Live preview:** https://awaken-coffee-kyseqlby.myshopify.com/ (storefront password: meufil)

![Awaken Coffee homepage](/screenshots/home.png)

## Design credit

Layout and styling are based on the "Ecommerce Shopping Store Coffee" Figma Community file by
Farzane Mojtabavi (https://www.figma.com/community/file/1228040426929552232/ecommerce-shoping-store-coffee?q_id=d84cbdbc-6c05-4dab-8bdb-5f4b68b0276d), used under the license stated( CC BY 4.0). I rebuilt it in Liquid with English copy and a left-to-right layout. Product photos are from Pexels. Sample reviews are placeholder content, not real customers.

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

| Performance | Accessibility | Best Practices | SEO |
| ----------- | ------------- | -------------- | --- |
| 66          | 100           | 100            | 92  |

For comparison, the untouched Skeleton starter scored 53, 87, 100 and 85 in the same setup.

Fixes along the way:

- Added `aria-label` text to the account and cart icon links
- Fixed the heading order by changing the logo from an `h2` to a `div`
- Added a `main` landmark to the layout
- Raised the contrast of the testimonial location text
- Added alt text to product images
- Loaded only the font weights in use and loaded the font stylesheet without blocking rendering
- Gave the hero image eager loading with high fetch priority, and lazy-loaded the rest
- Served all images as WebP at sensible sizes through Shopify's image filters

The remaining Performance gap is mostly blocking time. Part of it comes from scripts that Shopify injects on every storefront, which a theme cannot remove.

## Project structure

```
.
├── assets/awaken-theme.css            # Palette and font variables
├── layout/theme.liquid                # Page wrapper, fonts, main landmark
├── sections/
│   ├── awaken-hero.liquid
│   ├── awaken-categories.liquid
│   ├── awaken-featured.liquid
│   ├── awaken-banner.liquid
│   ├── awaken-testimonials.liquid
│   ├── header.liquid                  # Restyled
│   ├── footer.liquid                  # Restyled, with newsletter signup
│   ├── product.liquid                 # Restyled
│   └── cart.liquid                    # Restyled
├── snippets/awaken-background.liquid  # Page backdrop
└── templates/                         # JSON templates written by the theme editor
```

## Running it locally

1. Install Node.js and the [Shopify CLI](https://shopify.dev/docs/api/shopify-cli)
2. Clone this repository
3. Run `shopify theme dev --store your-store.myshopify.com`

The editor and the local preview behave differently for form submits, so test the cart and newsletter in a normal browser tab or on the store's real preview link.

## Workflow notes

`shopify theme push` overwrites the target theme's files, including the JSON that the theme editor writes. After changing the layout in the editor, I run `shopify theme pull --only "templates/*.json" --only "sections/*.json" --only "config/*.json"` before pushing, so the layout is never overwritten. For code-only changes, I push with `--only "sections/*.liquid"` and similar filters.

## What I would do next

- Update product availability when a variant is selected, using JavaScript
- Build a collection page template in the same style
- Add a mobile menu drawer
- Compress the remaining images further and test on a live store

## License

Built on Shopify's [Skeleton Theme](https://github.com/Shopify/skeleton-theme), released under the MIT License. See [LICENSE.md](./LICENSE.md).
