# QA Checklist — Copy → Acceptance Criteria

Use this checklist when reviewing the site during staging and QA.

Global
- All copy strings match content.csv keys and values.
- Responsive: text does not overflow or overlap at breakpoints (mobile, tablet, desktop).
- Accessibility: every interactive element has accessible name and keyboard operability.

Homepage
- hero.headline:
  - Shows on page load and is within H1.
  - CTA (.hero .cta-primary) navigates to /new-arrivals.
- newsletter:
  - Input accepts email; invalid email shows "Please enter a valid email address."
  - Successful submission shows "Get 10% off" confirmation or promo code.

Product pages
- product.h1:
  - H1 matches product title from CMS.
- product.short_desc & product.long_desc:
  - Template fields populated — no raw placeholders like [PRODUCT_NAME] visible to users.
- size selector:
  - "Select size" present; trying to add-to-cart without size shows "Please select a size to continue."
  - Disabled sizes have aria-disabled and visually clear label "Sold out".
- stock messages:
  - "Only [n] left" appears when inventory <= threshold (e.g., 5).
  - "Out of stock — join the waitlist" appears when SKU unavailable and waitlist CTA works.
- add to cart:
  - When clicked with valid options: mini-cart shown with "Added to cart" and product line.
  - When clicked with missing required options: error message inline and focus moves to first invalid field.

Cart & Mini-cart
- Cart header "Your Cart" visible.
- Empty state:
  - When cart is empty show message "Your cart is empty — find your next favorite outfit in New Arrivals." and CTA to /new-arrivals.
- Promo codes:
  - Entering valid promo: totals update and "Promo applied — you saved $[amount]" shown.
  - Invalid promo: "Promo code not valid or expired" shown.
- Quantity changes:
  - Changing qty updates subtotal and triggers analytics event product_quantity_change.

Checkout
- Form validation:
  - Required fields show "This field is required." and aria-invalid on error.
  - Invalid postal shows "Please enter a valid postal/ZIP code."
  - Card declines show "Your card was declined. Please check your details or try another card."
- Processing:
  - After clicking "Place Order", show loader and "Processing your payment — please do not refresh the page."
  - Order confirmation page displays Order # and confirmation email line.
- Duplicate prevention:
  - "Place Order" disabled while processing; no duplicate orders in backend.

Contact & Support
- Contact form success shows "Thanks — we’ll get back to you within 1 business day."
- If order number provided, ensure it's logged and visible in support email.

Footer & Legal
- Privacy Policy, Shipping Information, Returns & Exchanges links load legal pages.
- Footer tagline "Modern style, made simple." visible on all pages.

SEO & Metadata
- Homepage meta title and description match content.csv seo entries.
- Product pages include Product schema: name, image, description, sku, offers (price, currency, availability).
- Breadcrumb structured data present and matches visible breadcrumbs.

Analytics
- Events fire with expected payload keys:
  - product_add_to_cart -> {productId, sku, price, qty}
  - begin_checkout -> cart totals, item list
  - purchase_complete -> order id, revenue, items
  - newsletter_signup -> email (hashed if required by privacy policy)

Localization & Placeholder safety
- No placeholders like [PRODUCT_NAME] or [n] visible in public pages.
- Strings marked for translation are provided in content.csv and flagged in notes.

Copy QA process
1. Import content.csv into Google Sheets or CMS.
2. Use "Find" to check for placeholder tokens ([...]) — none should remain.
3. Run through QA checklist on staging at these breakpoints: 375px, 768px, 1024px.
4. Accessibility scan with axe / Lighthouse and manual keyboard tests for critical flows (product -> cart -> checkout).
5. Report any mismatches to the content owner with the element_id for rapid fixes.

If you'd like, I can:
- Export this content.csv as an actual downloadable CSV file (zipped), or
- Convert component-spec.md into TypeScript interfaces and TSX component stubs.
Which of those would you prefer next?
