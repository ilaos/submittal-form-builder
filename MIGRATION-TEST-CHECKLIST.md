# PDF Generation Migration - Testing Checklist

## ✅ Basic Functionality Tests

### 1. PDF Generation (Free Version)
- [ ] Select 1-3 products
- [ ] Add project name
- [ ] Click "Generate PDF"
- [ ] Verify PDF downloads successfully
- [ ] Verify PDF contains all selected products
- [ ] Verify PDF has proper branding/footer
- [ ] Check browser console for errors (should be none)

### 2. Review Step Features
- [ ] Add quantities to products (should work if review.js is loaded)
- [ ] Add notes to products
- [ ] Verify quantities appear in generated PDF
- [ ] Verify notes appear in generated PDF

### 3. Configurable Fields (Dropdowns)
- [ ] Select product with dropdown fields (e.g., Size, Voltage options)
- [ ] Choose values from dropdowns
- [ ] Generate PDF
- [ ] Verify selected dropdown values appear in PDF specs

### 4. Error Handling
- [ ] Try generating PDF with no products selected
  - Should show: "Please select at least one product"
- [ ] Disable REST API endpoint temporarily
  - Should show user-friendly error message
- [ ] Check error appears in console with details

---

## 🔒 Pro Feature Tests (Requires Pro License)

### 5. PDF Themes (Pro)
**Setup:**
- Activate Pro license
- Go to Settings → Branding
- Set theme to "Engineering", "Architectural", or "Corporate"

**Test:**
- [ ] Generate PDF with Engineering theme (blue accents)
- [ ] Generate PDF with Architectural theme (modern layout)
- [ ] Generate PDF with Corporate theme (professional styling)
- [ ] Verify theme applies to cover page and headers

### 6. PDF Watermark (Pro)
**Setup:**
- Activate Pro license
- Go to Settings → Branding
- Enable watermark, enter text (e.g., "DRAFT" or "CONFIDENTIAL")

**Test:**
- [ ] Generate PDF
- [ ] Verify watermark appears diagonally on pages
- [ ] Verify watermark is semi-transparent
- [ ] Verify watermark doesn't obscure content

### 7. Signature Block (Pro)
**Setup:**
- Activate Pro license
- Enable signature/approval block feature

**Test:**
- [ ] Generate PDF
- [ ] Verify signature block appears at end
- [ ] Verify 3-column approval table is present
- [ ] Verify signature lines are formatted correctly

### 8. White-Label Mode (Pro/Agency)
**Setup:**
- Activate Pro license
- Go to Settings → White-Label Mode
- Enable white-label
- Add custom footer text

**Test:**
- [ ] Generate PDF
- [ ] Verify plugin branding is removed from footer
- [ ] Verify custom footer text appears
- [ ] Verify cover page has no plugin attribution

---

## 🔍 Advanced Tests

### 9. Lead Capture Integration (Pro)
**Setup:**
- Enable lead capture in settings

**Test:**
- [ ] Click "Generate PDF"
- [ ] Verify lead capture modal appears BEFORE PDF generation
- [ ] Fill in email/phone
- [ ] Submit modal
- [ ] Verify PDF generates after submission
- [ ] Check database for lead entry

### 10. REST API Direct Test
**Using browser console or Postman:**

```javascript
// Test REST API directly
fetch(window.location.origin + '/wp-json/sfb/v1/generate', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'X-WP-Nonce': document.querySelector('#sfb-builder-app').dataset.nonce
  },
  body: JSON.stringify({
    review: {
      project: { name: 'Test Project', notes: 'Test notes' },
      products: [{ id: 123, quantity: 1, note: '' }]  // Replace 123 with real product ID
    },
    selected_field_values: {}
  })
})
.then(r => r.json())
.then(data => console.log(data));
```

**Expected response:**
```json
{
  "ok": true,
  "url": "https://site.com/wp-content/uploads/sfb/Submittal_Test_Project_2025-01-27.pdf",
  "filename": "Submittal_Test_Project_2025-01-27.pdf",
  "format": "pdf",
  "pro_active": true,
  "features": { ... }
}
```

### 11. Compare Old vs New
**Before deleting old handler:**
- [ ] Generate PDF using new REST API (current frontend)
- [ ] Note: file size, page count, layout
- [ ] Generate PDF using old AJAX endpoint (if still available)
- [ ] Verify both produce similar output
- [ ] Verify new one has Pro features if license active

---

## 🐛 Regression Tests

### 12. Other Frontend Features
- [ ] Product search still works
- [ ] Category filtering still works
- [ ] Product selection/deselection still works
- [ ] Selected products tray still works
- [ ] Navigation between steps still works

### 13. Admin Backend
- [ ] Admin catalog builder still works
- [ ] Product editing still works
- [ ] Settings save properly
- [ ] License activation still works

---

## 📊 Performance Tests

### 14. PDF Generation Speed
- [ ] Time PDF generation with 5 products: ____ seconds
- [ ] Time PDF generation with 20 products: ____ seconds
- [ ] Time PDF generation with 50 products: ____ seconds
- [ ] Verify no significant performance degradation

### 15. Browser Compatibility
- [ ] Chrome (latest)
- [ ] Firefox (latest)
- [ ] Safari (latest)
- [ ] Edge (latest)
- [ ] Mobile Safari (iOS)
- [ ] Mobile Chrome (Android)

---

## ✅ Pro Feature Verification (Visual Inspection)

Open generated PDFs and verify:

### Free Version PDF Should Have:
- ✅ Cover page with company name
- ✅ Table of contents
- ✅ Summary page
- ✅ Product specification pages
- ✅ Page numbers
- ✅ Plugin branding in footer
- ❌ NO theme styling (standard layout)
- ❌ NO watermark
- ❌ NO signature block

### Pro Version PDF Should Have:
- ✅ Everything from Free version
- ✅ Theme-specific styling (colors, fonts)
- ✅ Watermark (if enabled)
- ✅ Signature/approval block (if enabled)
- ✅ Custom footer (if white-label enabled)
- ❌ NO plugin branding (if white-label enabled)

---

## 🔧 Troubleshooting

### If PDF generation fails:
1. Check browser console for JavaScript errors
2. Check wp-content/debug.log for PHP errors
3. Verify REST API is accessible: visit `/wp-json/sfb/v1/health`
4. Check nonce is present: `console.log(document.querySelector('#sfb-builder-app').dataset.nonce)`
5. Verify composer packages installed (vendor/autoload.php exists)

### If Pro features don't work:
1. Verify Pro license is active: Go to Settings → License
2. Check license status in console: `console.log(sfbSettings.pro_active)`
3. Verify features are enabled: Check feature gates in settings
4. Clear browser cache and try again

---

## 📝 Sign-Off

**Tested by:** ___________________
**Date:** ___________________
**Environment:** [ ] Local [ ] Staging [ ] Production
**WordPress Version:** ___________________
**Plugin Version:** ___________________

**Overall Result:** [ ] ✅ PASS [ ] ❌ FAIL

**Notes:**
