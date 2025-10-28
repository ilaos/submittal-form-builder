# Dropdown Field Type Feature - Testing Guide

**Feature:** Product Configurator with Dropdown Field Types
**Status:** Implementation Complete - Ready for Testing
**Date:** 2025-10-21

---

## What Was Implemented

### Backend (Admin Interface)
- **Field Types Tab** on Type and Subtype nodes
- Toggle fields between "Text Input" and "Dropdown"
- Add/remove dropdown options
- Auto-save on every change
- Field inheritance: Models inherit from parent Type/Subtype

### Frontend (Product Selection)
- Dropdown selectors appear on product cards for select-type fields
- Users can choose values from dropdowns
- Selected values stored separately from database defaults
- Auto-selects product when dropdown value is chosen

### PDF Generation
- User-selected dropdown values override database specs
- PDFs show the values the user actually selected
- Works with both review and legacy product submission formats

---

## Testing Checklist

### ✅ Part 1: Configure Field Types (Admin)

1. **Go to:** Submittal Builder → Catalog Builder
2. **Find a Type or Subtype** (e.g., "20 Gauge 30 MIL")
3. **Click on it** to open Inspector modal
4. **Click "Field Types" tab**
5. **Find a field** (e.g., "KSI")
6. **Toggle to "Dropdown"** - Should see "✓ Saving..." then "✓ Saved"
7. **Add options:** 33, 50
8. **Close modal and reopen** - Verify it stayed as Dropdown with options

**Expected Result:** Field type persists as Dropdown with options intact

---

### ✅ Part 2: Toggle Back to Text (Admin)

1. **Open same Type's Field Types tab**
2. **Find the dropdown field** (e.g., "KSI")
3. **Toggle back to "Text Input"** - Should see "✓ Saving..." then "✓ Saved"
4. **Close modal and reopen** - Verify it's now Text Input (options should be gone)

**Expected Result:** Field type persists as Text Input

**This was the bug we just fixed!** Previously it would revert back to Dropdown.

---

### ✅ Part 3: Verify Frontend Dropdowns

1. **Go to:** Your frontend builder page (with `[submittal_builder]` shortcode)
2. **Find a product** that inherits from the Type you configured
3. **Look for dropdown** on the product card

**Expected Result:**
- If field is configured as Dropdown → Shows dropdown with options
- If field is configured as Text → Shows normal spec text (no dropdown)

---

### ✅ Part 4: Select Dropdown Values

1. **Find a product card** with a dropdown (e.g., KSI dropdown)
2. **Select a value** from dropdown (e.g., "50")
3. **Check browser console** - Should log: `[SFB] Field "KSI" set to "50" for product...`
4. **Verify product auto-selected** - Should appear in "Selected Products" tray

**Expected Result:** Dropdown value is captured and product is auto-selected

---

### ✅ Part 5: Generate PDF with Selected Values

1. **Select 2-3 products** with dropdown fields
2. **Choose different values** for each (e.g., Product A: KSI=33, Product B: KSI=50)
3. **Click "Continue" or "VIEW →"** to go to Review step
4. **Add project name** (optional)
5. **Click "Generate PDF"**
6. **Open the PDF**
7. **Check spec sheets** for each product

**Expected Result:**
- Product A spec sheet shows KSI = 33 (the value you selected)
- Product B spec sheet shows KSI = 50 (the value you selected)
- NOT the database default values

---

## Key Implementation Details

### Admin (assets/admin.js)

**Lines 1354-1415:** Inline save on field type toggle
- Builds payload with fresh `newConfigs` directly
- Doesn't rely on React state update
- Fixes closure issue where `autoSave()` captured stale state

**Lines 1021-1045:** Field inheritance logic
- Models check parent Type/Subtype for `field_configs`
- Walks up parent chain if needed
- Falls back to text input if no configs found

### Frontend (assets/js/frontend.js)

**Lines 434-473:** `buildConfigurableFields()` function
- Filters for select-type fields
- Renders HTML dropdowns with options
- Pre-selects current value if exists

**Lines 727-749:** Dropdown change handlers
- Stores selected values in `state.selectedFieldValues` Map
- Keyed by `composite_key`
- Auto-selects product on value change

**Lines 1163-1180:** PDF submission
- Converts Map to plain object
- Sends as `selected_field_values` POST parameter
- Works with both review and legacy formats

### Backend (submittal-form-builder.php)

**Lines 6307-6324:** Field configs API
- Inherits from parent Type/Subtype
- Returns `field_configs` array in products API

**Lines 6435-6467:** Receive selected values
- Decodes `selected_field_values` JSON
- Builds `composite_key → product_id` map

**Lines 6520-6530:** Merge into specs
- Looks up product by composite_key
- Merges user-selected values over database specs
- Logs merge for debugging

---

## Common Issues & Solutions

### Issue: Field type doesn't persist when toggling
**Solution:** This was the closure bug - now fixed with inline save approach

### Issue: Dropdown doesn't show on frontend
**Possible Causes:**
- Field not configured as "Dropdown" on parent Type/Subtype
- No options added to dropdown
- Browser cache - try hard refresh (Ctrl+Shift+R)

### Issue: PDF shows database value, not selected value
**Possible Causes:**
- Check browser console for `[SFB]` logs during PDF generation
- Verify `selected_field_values` is being sent in POST
- Check PHP error logs for merge confirmation

---

## Debug Logging

### Frontend Console
Look for these log messages:
```
[SFB] Field "KSI" set to "50" for product category::product_label
```

### PHP Error Logs
Look for these log messages:
```
[SFB] Merged user-selected values for product 123: Array([KSI] => 50)
```

---

## Next Steps After Testing

If everything works:
1. ✅ Test with multiple field types (Size, Thickness, etc.)
2. ✅ Test with Subtypes (should inherit from grandparent Type)
3. ✅ Test toggling between Text ↔ Dropdown multiple times
4. ✅ Generate PDFs with various dropdown combinations
5. ✅ Test on mobile devices

If you find issues:
- Check browser console for JavaScript errors
- Check WordPress debug log for PHP errors
- Provide specific steps to reproduce the issue

---

**Implementation Complete!** 🎉

All code changes have been made and the inline save fix has been applied to resolve the field type persistence issue.
