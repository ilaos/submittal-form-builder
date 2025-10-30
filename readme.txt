=== Submittal & Spec Sheet Builder ===
Contributors: webstuffguy
Tags: submittals, spec-sheets, pdf, construction, leads, catalog, branding
Requires at least: 6.1
Tested up to: 6.7
Requires PHP: 7.4
Stable tag: 1.0.0
License: GPLv2 or later
License URI: https://www.gnu.org/licenses/gpl-2.0.html

Create professional submittal packets and spec sheets directly from your WordPress site. Build branded PDFs from your product catalog, capture leads, and simplify documentation workflows. Perfect for construction submittals and complex product catalogs - serve contractors, manufacturers, distributors, and equipment suppliers.

== Description ==

**Submittal & Spec Sheet Builder** helps manufacturers, suppliers, contractors, and distributors create professional submittal packets and product spec sheets in minutes — right inside WordPress.

Whether you're creating construction submittals or managing a complex product catalog with thousands of SKUs (landscape supplies, industrial fasteners, equipment, flooring, etc.), this plugin lets customers browse your catalog and build their own spec sheets.

Forget clunky spreadsheets and manual formatting. With this plugin you can:

- Organize products into categories, types, and models (handle hundreds or thousands of SKUs)
- Let visitors select items and instantly **generate polished PDF packets**
- Add your company logo, brand colors, and contact info automatically
- Collect project details or contact info before download for **lead capture**
- Manage and export leads directly from the admin panel
- Track who views your PDFs and follow up with qualified leads

### Key Features

- 🧩 **Visual Builder:** Browse by category → product → type → model, with inline specifications.
- 🧾 **PDF Generation:** Includes cover, table of contents, and product spec sheets.
- 🎨 **Branding Tools:** Add logos, colors, and custom footer text for consistent presentation.
- 📨 **Lead Capture:** Optional form before PDF download; export leads as CSV.
- 📦 **Product Catalog Manager:** Manage all product data inside WordPress — no developer needed.
- ⚙️ **Agency Tools (optional):** White-label branding, analytics, preset themes, and team handoff features.

> Fast, flexible, and built for the real world — ideal for construction professionals creating submittals, distributors with complex catalogs (landscape supplies, industrial parts, equipment), and any B2B business with hundreds of products that need professional spec sheets.

== Privacy ==

This plugin stores lead form submissions locally in your WordPress database.

Optional analytics and lead routing features can be enabled to collect non-personally identifiable information (product names, counts, timestamps).  
All data stays within your WordPress site unless you configure an outgoing webhook.

To disable all remote analytics:
```php
add_filter('sfb_enable_remote_analytics', '__return_false');
== Installation ==

Upload the plugin ZIP via Plugins → Add New → Upload Plugin, then activate it.

Create a new page and add the shortcode:

csharp
Copy code
[submittal_builder]
Configure branding under Settings → Branding (logo, colors, footer).

Add or import your products in Catalog Builder.

Test the front-end builder by selecting products → Review → Generate PDF.

== Screenshots ==

Product browser – browse catalog by category and specification.

Selection step – add items to submittal with live count and visual feedback.

Review screen – confirm selections, add project info, and generate PDFs.

Optional lead capture – collect contact info before download.

Generated PDF – includes cover page, summary, and all selected spec sheets.

Branded cover – automatically styled with your logo and company details.

Product sheet – includes detailed specification fields for compliance.

Catalog builder – manage product hierarchy inside WordPress.

Custom fields – support for HVAC, Electrical, Plumbing, and Steel industries.

Quick add – add new models or types directly from the builder interface.

== Frequently Asked Questions ==

= Does this plugin send data to any third parties? =
No. All data is stored locally in your WordPress database unless you configure a webhook or analytics integration.

= Can I customize the PDF? =
Yes — you can control branding colors, footer text, and logo. Additional layout presets are available for agencies.

= Can I import or reuse catalogs? =
Yes — you can import existing data or use pre-made industry packs for faster setup.

= Is it compatible with page builders? =
Yes. The shortcode works inside Elementor, Gutenberg, and most other editors.

== Changelog ==

= 1.0.0 =
Initial WordPress.org release

* Complete submittal and spec sheet PDF generation system
* Visual product catalog builder with category/product/model hierarchy
* Customizable branding (logo, colors, footer text)
* Lead capture forms with CSV export
* REST API for frontend PDF generation
* Pro features: PDF themes, watermarks, approval signature blocks
* Agency features: White-label mode, analytics, lead routing, webhooks
* Multi-tier licensing system (Free, Pro, Agency)
* Internationalization ready (i18n)
* Freemium architecture with feature gating

== Upgrade Notice ==

= 1.0.0 =
Initial release of Submittal & Spec Sheet Builder for WordPress.org. Create professional PDF submittal packets with full branding and lead capture capabilities.