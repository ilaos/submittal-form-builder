# Old AJAX Handler Removal Guide

## ⚠️ IMPORTANT: Only remove after testing is complete!

After thoroughly testing the new REST API implementation, you can safely remove the old AJAX handler to clean up the codebase.

---

## 📍 Location of Old Handler

**File:** `submittal-form-builder.php`
**Function:** `ajax_generate_frontend_pdf()`
**Lines:** 6856-7186 (approximately 330 lines)

---

## 🗑️ What to Remove

### 1. Remove AJAX Action Hook

**File:** `submittal-form-builder.php`
**Search for:** `add_action('wp_ajax_sfb_generate_frontend_pdf'`
**Also search for:** `add_action('wp_ajax_nopriv_sfb_generate_frontend_pdf'`

**Lines to delete:**
```php
add_action('wp_ajax_sfb_generate_frontend_pdf', [$this, 'ajax_generate_frontend_pdf']);
add_action('wp_ajax_nopriv_sfb_generate_frontend_pdf', [$this, 'ajax_generate_frontend_pdf']);
```

### 2. Remove AJAX Handler Function

**File:** `submittal-form-builder.php`
**Function:** Lines 6856-7186

**Delete entire function:**
```php
function ajax_generate_frontend_pdf() {
  // ... 330 lines of code ...
}
```

**Reason:** This logic is now duplicated in `api_generate_frontend_pdf_rest()` which is called by the REST API.

---

## ✅ What to Keep

### Keep These (Still Used):
1. ✅ `api_generate_packet()` - REST API handler (lines 9582+)
2. ✅ `api_generate_frontend_pdf_rest()` - New REST compatibility layer (lines 7188-7443)
3. ✅ All REST API route registrations in `Includes/class-sfb-rest.php`
4. ✅ Frontend JavaScript (already migrated to REST)

---

## 🔍 Verification Before Removal

Before removing the old handler, verify:

- [ ] All tests from `MIGRATION-TEST-CHECKLIST.md` pass
- [ ] No JavaScript errors in browser console
- [ ] No PHP errors in debug.log
- [ ] Pro features work correctly (themes, watermark, signature)
- [ ] Lead capture integration works (if enabled)
- [ ] PDF generation works on both desktop and mobile

---

## 📝 Removal Steps

### Step 1: Search for AJAX Hook Registrations
```bash
grep -n "wp_ajax_sfb_generate_frontend_pdf" submittal-form-builder.php
```

### Step 2: Comment Out First (Safety)
Instead of deleting, comment out the function first:

```php
/*
function ajax_generate_frontend_pdf() {
  // ... entire function ...
}
*/
```

### Step 3: Test for 24-48 Hours
- Monitor for any issues
- Check error logs
- Verify no one is still using the old endpoint

### Step 4: Permanent Deletion
After confirming everything works:
1. Delete the commented function
2. Delete the AJAX action hooks
3. Commit with message: `refactor: remove deprecated AJAX PDF handler (migrated to REST API)`

---

## 🚨 Rollback Plan

If issues arise after removal:

### Quick Rollback via Git
```bash
git revert HEAD
git push origin main
```

### Manual Restore
1. Copy function from git history
2. Paste back into submittal-form-builder.php
3. Re-add AJAX action hooks
4. Clear cache
5. Test

---

## 📊 Impact Analysis

### Files Affected by Removal:
- ✅ `submittal-form-builder.php` (remove ~330 lines)
- ❌ No frontend changes needed (already migrated)
- ❌ No database changes needed
- ❌ No settings changes needed

### Lines of Code:
- **Before:** ~330 lines in AJAX handler
- **After:** 0 lines (logic moved to REST handler)
- **Net savings:** ~330 lines (reduced duplication)

---

## 🎯 Benefits of Removal

1. **Less code duplication** - PDF logic exists in one place
2. **Easier maintenance** - Only one handler to update
3. **Better architecture** - REST API is the standard
4. **Pro features** - Only REST API supports Pro features
5. **Cleaner codebase** - Removes legacy code

---

## ⏰ Timeline

**Recommended approach:**

| Phase | Duration | Action |
|-------|----------|--------|
| Testing | 2-3 days | Run full test checklist |
| Comment Out | 1 day | Comment function, monitor |
| Monitor | 2-3 days | Watch logs, check reports |
| Delete | 1 day | Permanent removal + commit |

**Total time:** ~1 week for safe migration

---

## 📞 Support

If you encounter issues:
1. Check `MIGRATION-TEST-CHECKLIST.md`
2. Review git history for exact changes
3. Check WordPress debug.log
4. Check browser console errors
5. Contact support if needed

---

## ✅ Removal Checklist

Before removal:
- [ ] All tests pass (see MIGRATION-TEST-CHECKLIST.md)
- [ ] Tested on production-like environment
- [ ] Monitored for 2-3 days with no issues
- [ ] Created git commit before removal
- [ ] Documented removal in CHANGELOG

After removal:
- [ ] Function deleted from submittal-form-builder.php
- [ ] AJAX hooks removed
- [ ] Git commit created
- [ ] Changes pushed to remote
- [ ] Tested again after removal
- [ ] Updated plugin version number
- [ ] Added note to CHANGELOG

---

**Last Updated:** 2025-01-27
**Migration Version:** 1.0
**Safe to remove after:** Thorough testing complete ✅
