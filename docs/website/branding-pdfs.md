# Branding & PDF Generation

[← Back to Documentation](./index.md)

**Customize your brand and understand PDF generation**

---

## Overview

This guide covers how to customize your brand appearance in generated PDFs and understand the PDF generation process. Proper branding makes your submittal packets look professional and reinforces your company identity.

---

## Branding Customization

Make generated PDFs match your company's brand identity.

### Logo Setup

Your logo is the most important branding element, appearing prominently on the PDF cover page.

**Access Logo Settings:**
```
WordPress Admin → Submittal Builder → Settings → Branding
```

---

#### Logo Specifications

**Recommended Specs:**
- **Format:** PNG with transparent background (preferred)
- **Alternative:** JPG with white or solid background
- **Dimensions:** 300×100 pixels (optimal)
- **Aspect Ratio:** ~3:1 (horizontal orientation)
- **Max File Size:** 2 MB
- **Resolution:** 72-150 DPI for digital, 300 DPI for print

**Acceptable Formats:**
- ✅ PNG (best - supports transparency)
- ✅ JPG/JPEG (good - smaller file size)
- ✅ SVG (Pro - scalable, crisp at any size)
- ❌ GIF (not recommended)
- ❌ BMP (not supported)

---

#### Uploading Your Logo

**Steps:**
1. Navigate to **Settings → Branding**
2. Click **"Upload Logo"** button
3. **Select from Media Library** or **Upload New**
4. **Crop/resize** if needed using built-in editor
5. Click **"Select"** to confirm
6. Logo preview appears below button
7. Click **"Save Changes"** at bottom of page

**Tips:**
- Upload the highest quality version you have
- Plugin will automatically resize for optimal PDF display
- Transparent PNGs look best on colored backgrounds

---

#### Logo Placement

**Where Your Logo Appears:**

**PDF Cover Page:**
- Top center or top left (configurable)
- Large size (~2-3 inches wide)
- High contrast against background

**PDF Footer (Optional):**
- Small version in corner
- Subtle branding on every page
- Can be disabled in settings

---

#### Logo Best Practices

✅ **Do:**
- Use high-resolution original file
- Choose transparent PNG when possible
- Test logo on both white and colored backgrounds
- Keep it simple (complex logos may not scale well)
- Use official company logo files

❌ **Don't:**
- Use low-resolution images (pixelated in PDF)
- Upload logos with excess whitespace around them
- Use logos with very thin lines (may not print clearly)
- Forget to crop square logos to horizontal format

---

### Brand Colors

Colors reinforce your brand and make PDFs visually appealing.

**Access Color Settings:**
```
Settings → Branding → Brand Colors
```

---

#### Primary Brand Color

Your main brand color used throughout the PDF.

**Used For:**
- Cover page background or accents
- Section headers
- Table headers
- Dividers and borders
- Button colors

**How to Set:**
1. Click on color picker box
2. Select color visually, OR
3. Enter hex code (e.g., `#0066CC`)
4. Preview updates immediately
5. Save changes

**Color Picker Options:**
- Visual selector (hue and saturation)
- Hex code input (#RRGGBB)
- RGB values (Red, Green, Blue)
- HSL values (Hue, Saturation, Lightness)

---

#### Color Best Practices

✅ **Do:**
- Use your official brand color
- Ensure good contrast with white text (if used on dark backgrounds)
- Test print appearance (colors look different on screen vs paper)
- Keep it professional (avoid neon or overly bright colors)

❌ **Don't:**
- Use very light colors (won't show up well)
- Choose colors with poor contrast
- Forget to match your website/marketing materials
- Change frequently (consistency matters)

**WCAG Contrast Guidelines:**
For text legibility:
- **Dark backgrounds:** Use white or very light text
- **Light backgrounds:** Use dark text
- Test contrast ratio: aim for at least 4.5:1

---

#### Secondary Color (Pro)

Accent color for tables, borders, and secondary elements.

**Available in:** Pro and Agency licenses

**Used For:**
- Alternating table rows
- Secondary headers
- Borders and dividers
- Accent elements

**Default:** Automatically generated as a lighter/darker shade of primary color

**To Customize:**
Same process as primary color selection in Settings → Branding.

---

### Company Information

Information that appears on PDF cover pages and footers.

**Access:**
```
Settings → Branding → Company Information
```

---

#### Required Fields

**Company Name**

Your legal or trade name.

**Appears:**
- PDF cover page (large, prominent)
- PDF footer (small)
- Email signatures (Pro)

**Example:** "Acme Steel & Supply Co."

**Tips:**
- Use official registered name
- Include designations if relevant (LLC, Inc., etc.)
- Keep it concise (long names may wrap awkwardly)

---

#### Optional Fields

**Phone Number**

Primary business phone.

**Format:** Flexible (any format accepted)
**Recommended:** (555) 123-4567 or +1-555-123-4567

**Appears:** Cover page contact section

---

**Email Address**

General business email or sales contact.

**Example:** info@acmesteel.com
**Appears:** Cover page contact section, clickable link in PDF

---

**Website**

Company website URL.

**Format:** Include `https://` for clickable links
**Example:** https://www.acmesteel.com

**Appears:** Cover page, footer, clickable link in PDF

---

**Physical Address**

Business address for contact information.

**Format:** Multi-line accepted
**Example:**
```
123 Industrial Parkway
Suite 200
City, ST 12345
```

**Appears:** Cover page contact section

---

**Additional Contact Info (Pro)**

Optional fields for:
- Fax number
- Toll-free number
- Support email
- Social media links

---

### Footer Text

Custom text displayed at bottom of every PDF page.

**Access:**
```
Settings → Branding → Footer Text
```

**Default:**
```
{company} | {website} | Page {page} of {total}
```

**Available Variables:**
- `{company}` - Company name
- `{website}` - Website URL
- `{phone}` - Phone number
- `{email}` - Email address
- `{page}` - Current page number
- `{total}` - Total number of pages
- `{date}` - Generation date

**Example Footers:**

**Minimal:**
```
Page {page} of {total}
```

**Standard:**
```
{company} | www.yoursite.com | {page}/{total}
```

**Detailed:**
```
{company} | {phone} | {email} | Generated {date} | Page {page}
```

**Tips:**
- Keep footer short (one line max)
- Include page numbers for easy reference
- Include contact info for quick access
- Test with multi-page PDFs to verify appearance

---

## PDF Generation

Understanding how PDFs are created and structured.

### PDF Structure

Generated PDFs follow a consistent, professional structure designed for compliance and ease of use.

---

#### 1. Cover Page

**Contains:**
- Company logo (top center or left)
- Project name (large, prominent)
- Date generated
- Company information block
- Brand color accents

**Purpose:**
- Professional first impression
- Quick project identification
- Contact information readily available

**Customizable Elements:**
- Logo placement
- Color scheme
- Company info displayed
- Cover layout (Pro themes)

---

#### 2. Table of Contents

**Contains:**
- List of all selected products
- Product model numbers
- Page numbers for each product
- Clickable navigation links (PDF bookmarks)

**Purpose:**
- Quick navigation
- Overview of packet contents
- Easy reference for specific products

**Features:**
- Automatically generated
- Always accurate page numbers
- Clickable in most PDF readers
- Can be disabled in settings

---

#### 3. Summary Table

**Contains:**
- All products in compact table format
- Key specifications (Size, Thickness, KSI, etc.)
- Category and type information
- One-page overview

**Purpose:**
- Quick reference
- Comparison at a glance
- Bid sheet for pricing
- Project planning

**Customizable:**
- Which specs appear (based on field configuration)
- Table styling (Pro themes)
- Column order

---

#### 4. Individual Spec Sheets

**One page per product containing:**
- Product model number (header)
- Full specifications table
- All configured fields with values
- Category and type badges
- Optional product image (if available)

**Purpose:**
- Compliance submittal
- Detailed product data
- Code approval
- Installation reference

**Layout:**
- Clean, readable format
- Print-optimized
- Consistent styling
- All specs visible

---

#### 5. Footer

**Appears on every page:**
- Page numbers
- Company name
- Contact info (configurable)
- Generation date

**Purpose:**
- Orientation reference
- Quick contact lookup
- Document tracking

---

### PDF Generation Process

Understanding what happens when users click "Generate PDF."

**Step-by-Step:**

1. **User clicks "Generate PDF"**
   - Frontend sends AJAX request to server
   - Passes selected product composite keys
   - Includes project information

2. **Server validates request**
   - Checks nonce for security
   - Verifies products exist
   - Loads branding settings

3. **HTML template rendered**
   - Cover page generated with branding
   - TOC created with page calculations
   - Summary table built
   - Spec sheets rendered for each product

4. **PDF conversion**
   - HTML converted to PDF using DomPDF library
   - Styles applied
   - Page numbers calculated
   - Bookmarks created

5. **File saved temporarily**
   - PDF saved to `/wp-content/uploads/submittal-builder/`
   - Unique filename generated
   - Temporary URL created

6. **Response sent to user**
   - Download URL returned
   - Success page displayed
   - File ready for download

**Typical Processing Time:**
- 1-5 products: 2-5 seconds
- 6-15 products: 5-10 seconds
- 16-30 products: 10-20 seconds
- 31+ products: 20-30 seconds

**Factors Affecting Speed:**
- Number of products
- Server resources (CPU, memory)
- PDF complexity
- Image processing (if product images included)

---

### PDF File Details

**Filename Format:**
```
submittal-{project-slug}-{timestamp}.pdf
```

**Example:**
```
submittal-miller-hall-renovation-20251015-143022.pdf
```

**File Properties:**
- **Size:** ~50-150 KB per product page
- **Format:** PDF 1.7 (widely compatible)
- **Orientation:** Portrait (default) or Landscape
- **Page Size:** Letter (8.5" × 11") or A4

**Metadata:**
- Title: Project name
- Author: Company name
- Creator: Plugin name (or white-labeled)
- Creation date: Generation timestamp

---

### PDF Retention

**Storage Location:**
```
/wp-content/uploads/submittal-builder/YYYY/MM/
```

**Automatic Cleanup:**
- Runs daily via WordPress cron
- Deletes files older than retention period
- Default retention: 24 hours (configurable in Settings)

**Retention Options:**
- 1 hour (minimal storage)
- 6 hours
- 24 hours (default, recommended)
- 48 hours
- 7 days (maximum)

**Manual Cleanup:**
Admin can trigger immediate cleanup:
```
Settings → Advanced → Click "Run Cleanup Now"
```

---

## PDF Themes (Pro)

Apply preset design themes for different aesthetics and use cases.

**Available in:** Pro and Agency licenses

**Access:**
```
Settings → PDF → Enable PDF Themes
```

---

### Available Themes

**Default Theme**
- Clean, professional
- High readability
- Versatile for all industries
- Blue accents (customizable)

**Corporate Theme**
- Bold, modern
- Strong color presence
- Ideal for marketing materials
- Impression-focused

**Architectural Theme**
- Minimal, elegant
- Lots of whitespace
- Subtle colors
- Blueprint-inspired

**Industrial Theme**
- Strong, utilitarian
- High contrast
- Easy to read in shop environments
- Rugged aesthetic

---

### Applying Themes

**Steps:**
1. Navigate to **Settings → PDF**
2. Enable **"Use PDF Themes"** checkbox
3. Select theme from dropdown
4. Click **"Save Changes"**
5. Generate test PDF to preview

**Note:** Themes respect your brand color and logo settings while adjusting layout, fonts, and overall aesthetic.

---

## Troubleshooting Branding

### Logo doesn't appear in PDF

**Cause:** Logo not uploaded or file path broken.

**Solution:**
1. Re-upload logo via Settings → Branding
2. Ensure file format is PNG or JPG
3. Check file size is under 2 MB
4. Clear browser cache and regenerate PDF

---

### Logo appears pixelated

**Cause:** Low-resolution source file.

**Solution:**
1. Upload higher-resolution logo
2. Use minimum 300×100 pixels
3. Ensure 150+ DPI for print
4. Use PNG for best quality

---

### Brand color doesn't show

**Cause:** Color not saved or very light color not visible.

**Solution:**
1. Re-select color and click Save Changes
2. Try darker color for better visibility
3. Check browser console for JavaScript errors
4. Clear cache and regenerate PDF

---

### Footer text not updating

**Cause:** Settings not saved or caching issue.

**Solution:**
1. Verify you clicked "Save Changes"
2. Check for success message
3. Clear server cache (if caching plugin active)
4. Regenerate PDF (don't use old cached PDFs)

---

## Next Steps

### Related Documentation

- [Admin Settings](./admin-settings.md) - Full settings reference
- [Product Management](./product-management.md) - Adding products
- [User Guide](./user-guide.md) - Frontend builder usage
- [Troubleshooting](./troubleshooting.md) - Common issues

### Need Help?

- **Documentation:** [Full Documentation](./index.md)
- **WordPress.org Forum:** https://wordpress.org/support/plugin/submittal-builder/
- **Email Support:** support@webstuffguylabs.com (Pro users)

---

[← Back to Documentation](./index.md) | [Next: Troubleshooting →](./troubleshooting.md)

---

© 2025 WebStuff Guy Labs. All rights reserved.
