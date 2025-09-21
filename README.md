# Advertising E‑Commerce — Product Specification & Development Approach

**Product name (placeholder):** WhiteLabel Shop

**Purpose:** Build a demo/advertising e‑commerce site that doubles as a live, clickable showcase and a deployable white‑label script. Visitors can explore a fully functional furniture store demo and, after purchase, deploy their own branded copy to any hosting + domain with editable company data, products, theme basics, and payment settings.

---

## 1. Executive Summary

WhiteLabel Shop is a self‑hosted, React‑powered e‑commerce product packaged for sale. The public demo acts as marketing: prospects can browse, test, and verify functionality. After purchase they receive an installer package (ZIP) and license key to deploy the same system on their hosting. The deployed copy is fully editable through an admin panel (no coding required): business details, logo, products, prices, shipping, and payment credentials.

This approach combines the strengths of a live demo (higher conversion) with the practicality of a self‑hosted product (customers host their own store, minimal ongoing server costs for the vendor).

---

## 2. Objectives

* Provide a realistic, fully interactive demo site that showcases the product’s UI, UX and feature set.
* Offer an easy installer + admin UX so non‑technical clients can deploy and run their own store on any standard web host.
* Enable buyers to brand and edit the store via a GUI without touching code.
* Protect the product with a licensing/activation flow while keeping the installation process friction‑free.
* Make the product extensible for future SaaS transition or additional premium features.

---

## 3. Key Users & Roles

* **Prospect / Shopper (Demo visitor):** Browses demo store, checks UX and features.
* **Buyer / Client (Deployer):** Purchases the product, receives installer + license, deploys to own hosting, customises store content and settings.
* **Admin (Client staff):** Manages products, orders, settings from an admin panel.
* **Vendor (You):** Maintains demo, issues licenses, publishes updates, offers paid support.

---

## 4. Core Features (Demo & Deployable Product)

### Demo mode (public site)

* Complete storefront (categories, search, filters, product pages).
* Simulated checkout (no real payments unless enabled).
* Admin demo walkthrough video / tooltip overlays.
* Prominent CTA and purchase flow for the script.

### Deployable script (client installation)

* Installer wizard: DB details, admin user, site name, license key verification.
* Admin Dashboard (React):

  * Company settings (name, logo, address, contact, business hours).
  * Theme settings (primary color, accent, font choices, header/footer text).
  * Product management (images, SKUs, price, stock, variants, dimensions).
  * Category management and product attributes.
  * Order management (view, update status, export CSV/PDF).
  * Shipping options (flat rate, per‑item, free threshold) and tax settings.
  * Payment integrations (PayFast, Ozow, Yoco) + Cash on Delivery.
* Content editable pages: About, Contact, Terms, Policies.
* Email templates (order confirmation, shipping notification).

### Licensing & Updates

* License key generation portal (vendor side).
* Online activation during install (calls vendor API). Optional offline activation flow for restricted hosts.
* Update check in admin (manual download or auto‑update if enabled).

---

## 5. Technical Architecture

* **Frontend (Storefront & Admin):** React + Vite, React Router, Context API or Redux for state, Tailwind CSS for styling.
* **Backend API:** Node.js + Express (REST API) — authentication via JWT.
* **Database:** MySQL / MariaDB (works with most hosts).
* **File Storage:** Local file uploads (images) with optional S3/GCS later.
* **Payment Integrations:** PayFast, Ozow, Yoco SDKs/APIs.
* **License Server:** Small Node service (or separate endpoint in vendor backend) that validates license keys and returns activation status.
* **Installer:** Browser‑based wizard that writes `.env` / `config.php` (depending on packaging) and migrates DB schema.

---

## 6. Installer Flow (User Experience)

1. Upload ZIP to hosting and extract.
2. Visit `example.com/install`.
3. Step 1: Accept license & terms.
4. Step 2: Enter DB host, name, user, password. Test connection.
5. Step 3: Enter admin account details (email, password) + site name.
6. Step 4: Enter license key (online activation). Option: skip and use trial/demo mode.
7. Step 5: Finish — installer writes config, runs migrations, seeds sample products. Redirect to admin dashboard.

---

## 7. Admin / Customisation (Editable After Purchase)

* **Branding:** logo upload, favicon, store name.
* **Contact info & legal pages:** editable WYSIWYG content blocks.
* **Theme basics:** select primary color, choose layout variant (compact / spacious), toggle hero banner.
* **Products & Inventory:** add/edit/delete, bulk import/export CSV.
* **Payments & Shipping:** enable/disable gateways, configure credentials, shipping zones.
* **Store Status:** maintenance mode (with custom message), demo toggles.

---

## 8. Security & Compliance

* Passwords hashed (bcrypt). JWT with expiry and refresh option.
* Input validation & prepared queries to prevent SQL injection.
* CSRF tokens for state‑changing endpoints if using cookies.
* Optional HTTPS enforcement in installer instructions.
* GDPR‑style data handling checklist for customers (store owners).

---

## 9. Distribution & Commercial Model

Options to sell:

* Direct sales via vendor website (WooCommerce + EDD + software licensing).
* Marketplaces like CodeCanyon (subject to their rules).
* Tiered pricing:

  * **Basic:** Installer package, 6 months updates.
  * **Pro:** Installer + 12 months updates + priority email support.
  * **Agency:** Multiple activations, white‑labeling assistance, customisation hours.

Include clear licensing terms (single domain per license, transfer policy, renewal for updates/support).

---

## 10. Marketing / Demo Site Strategy

* Public demo with clear “buy” CTA and feature tour.
* Live admin demo (read‑only link) so prospects can explore admin UX.
* Short onboarding videos and FAQ for non‑technical buyers.
* Showcase local payment gateways to appeal to South African market.

---

## 11. MVP Roadmap & Timeline (Suggested)

**Sprint 0 (1 week):** Requirements, wireframes, environment setup.
**Sprint 1 (2 weeks):** Backend core — products, orders, DB migrations, API.
**Sprint 2 (2 weeks):** Frontend store — product listing, detail, cart, basic checkout (COD/EFT).
**Sprint 3 (2 weeks):** Admin panel — product CRUD, orders view, basic settings.
**Sprint 4 (1 week):** Installer wizard + license server basics.
**Sprint 5 (1 week):** Payment integrations (PayFast) + email notifications.
**Sprint 6 (1 week):** Demo site polish, docs, packaging, and launch.

Total: \~10 weeks for a solid MVP (can compress if you scaffold from boilerplates).

---

## 12. Deliverables

* Deployable ZIP installer package.
* Public demo site (hosted by vendor).
* Admin & Storefront React apps.
* Backend API + license server code.
* Installation & user documentation (step‑by‑step + videos).
* 3 months of updates/support (or as per pricing tier).

---

## 13. Next Steps (Immediate)

1. Decide product name & demo domain.
2. Confirm target pricing tiers and license policy.
3. Create wireframes for storefront and admin UX.
4. Start Sprint 0: project repo, CI, seed data, and basic DB schema.

---

### Appendix: Suggested Database Entities (high level)

* `users` (admins, staff)
* `products` (id, title, slug, description, price, images, stock, attributes)
* `categories` (hierarchy)
* `orders` (customer data, totals, status)
* `order_items` (product\_id, qty, price)
* `settings` (key/value for theme & company data)
* `licenses` (key, status, expiry, domain)

---

*Prepared for: Your product concept — Advertising E‑Commerce / White‑Label Script*

*If you want I can now:*

* Convert this into a numbered formal SPEC document (SPEC‑001).
* Generate wireframe mockups (simple layout images) or a Trello/GitHub milestone checklist.
* Produce starter code scaffolding (React + Express template) to begin Sprint 1.
