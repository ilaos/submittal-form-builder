# Product Management

[← Back to Documentation](./index.md)

**Complete guide to managing your product catalog**

---

## Overview

The Catalog Builder is where you add, organize, and manage all products that appear in your frontend builder. This guide covers everything from basic product creation to advanced catalog management.

**Access Catalog Builder:**
```
WordPress Admin → Submittal Builder → Catalog Builder
```

**Required Capability:** `manage_options` (Administrator role)

---

## Product Hierarchy

Products are organized in a flexible 4-5 level hierarchy designed to match how contractors and engineers think about product selection.

### Structure

```
Category (e.g., "Valves")
  └── Product (e.g., "Ball Valves")
      └── Type (e.g., "2-Way")
          ├── Subtype (e.g., "1-1/4" Flange") [Optional]
          │   └── Model (e.g., "BV-125-FL")
          └── Model (e.g., "BV-200") [If no subtypes]
```

### Levels Explained

**Level 1: Category**
Top-level grouping of related products.

**Examples:**
- Valves
- C-Studs
- Track
- HVAC Units
- Electrical Panels

**Purpose:** Broad classification, used for filtering

---

**Level 2: Product**
Specific product line within a category.

**Examples:**
- Ball Valves (under Valves category)
- Steel Studs (under C-Studs category)
- Hat Channel (under Framing category)
- Air Handlers (under HVAC category)

**Purpose:** Product family or line

---

**Level 3: Type**
Variant or specification type.

**Examples:**
- 2-Way (under Ball Valves)
- 20 Gauge (under Steel Studs)
- 25 Gauge (under Steel Studs)
- Single Zone (under HVAC Units)

**Purpose:** Key differentiator, commonly used for selection

---

**Level 4: Subtype** (Optional)
Size, configuration, or specification subgroup within a Type.

**Examples:**
- 1-1/4" Flange (under 2-Way Ball Valves)
- 1-1/2" Flange (under 2-Way Ball Valves)
- 18 mil (under 20 Gauge Steel Studs)

**Purpose:** Additional grouping for sizes, configurations, or specifications

**Note:** This level is optional. If you don't need subgroupings, you can add Models directly under Types.

---

**Level 5: Model**
Individual product model with specific specifications.

**Examples:**
- BV-125-FL (under 1-1/4" Flange subtype)
- 362S162-20 (under 20 Gauge Steel Studs)
- 600S162-20 (under 20 Gauge Steel Studs)

**Purpose:** Specific orderable product with full specs

**Note:** These appear in generated PDFs with their full hierarchy path.

---

## How Hierarchy Affects What Users See

Understanding the hierarchy is important because **Product (Level 2)** is the main organizing principle for both the frontend and PDF output.

### Quick Reference Card

| Hierarchy Level | Example | Where It Appears |
|----------------|---------|------------------|
| **Category** | "Framing" | Sidebar navigation for filtering |
| **Product** | "25 GAUGE 18 MIL" | **Colored section headers** grouping models together |
| **Type** | "1-1/4\" FLNG" | Blue badge on model cards |
| **Subtype** | (optional) | Can be used for additional grouping |
| **Model** | "162S162-43" | Individual card title / main item name |

### Frontend Product Browser

When customers browse products on your site, here's what they see:

```
┌─────────────────────────────────────────┐
│ Sidebar: Categories                     │
│ ☑ Framing                               │
│ ☐ Valves                                │
│ ☐ HVAC                                  │
└─────────────────────────────────────────┘

┌─────────────────────────────────────────┐
│ 25 GAUGE 18 MIL          7 models      │ ← Product header (your theme color)
├─────────────────────────────────────────┤
│ ┌──────────┐  ┌──────────┐  ┌──────────┐│
│ │1-1/4 FLNG│  │1-1/2 FLNG│  │2" FLNG   ││ ← Type badges
│ │          │  │          │  │          ││
│ │162S162-43│  │250S162-54│  │350S162-54││ ← Model names
│ │          │  │          │  │          ││
│ │Size: 1.25│  │Size: 1.5 │  │Size: 2.0 ││
│ └──────────┘  └──────────┘  └──────────┘│
└─────────────────────────────────────────┘

┌─────────────────────────────────────────┐
│ 20 GAUGE 30 MIL          5 models      │ ← Next product
├─────────────────────────────────────────┤
│ (more models...)                        │
└─────────────────────────────────────────┘
```

**Key Points:**
- **Category** appears in the sidebar for filtering (click to show only those products)
- **Product** becomes the colored header - all models with the same Product name are grouped together
- **Type** shows as a small blue badge on each model card
- **Model** is the main name displayed on each card

### PDF Submittal Packet

The PDF uses the same Product-based grouping:

**Summary Page:**
```
SUMMARY
This packet contains 12 models across 2 products.

┌─────────────────────────────────────────┐
│ 25 GAUGE 18 MIL (7 models)             │
├─────────────────────────────────────────┤
│ Qty │ Model        │ Specs     │ Notes  │
│  1  │ 162S162-43   │ Size: 1.25│        │
│  1  │ 250S162-54   │ Size: 1.5 │        │
│  1  │ 350S162-54   │ Size: 2.0 │        │
│ ... │ ...          │ ...       │        │
└─────────────────────────────────────────┘

┌─────────────────────────────────────────┐
│ 20 GAUGE 30 MIL (5 models)             │
├─────────────────────────────────────────┤
│ ... │ ...          │ ...       │        │
└─────────────────────────────────────────┘
```

**Individual Model Pages:**
```
Page header breadcrumb:
Framing / 25 GAUGE 18 MIL

Model: 162S162-43
[Full specifications and details]
```

### Why This Matters

When planning your catalog, think about **Product** as your main grouping:

✅ **Good Product Grouping:**
- "25 GAUGE 18 MIL" (groups all 25-gauge 18-mil models together)
- "Ball Valves 2-Way" (groups all 2-way ball valve models together)
- "Air Handlers Single Zone" (groups all single-zone models together)

❌ **Avoid This:**
- Using generic products like "Standard" or "Various" (makes poor section headers)
- Putting too many different items in one Product (creates giant unwieldy sections)
- Using the same Product name across different categories (creates confusion)

**Pro Tip:** Your Product name will appear on every PDF page as part of the breadcrumb and as section headers in the summary, so choose descriptive, professional names.

---

## Using the Catalog Builder

The Catalog Builder features a visual tree interface for managing your product hierarchy.

### Interface Overview

**Left Panel: Product Tree**
- Hierarchical view of all products
- Expandable/collapsible items
- Drag-and-drop reordering
- Right-click context menus

**Right Panel: Inspector**
- Edit selected item details
- Add/remove specifications
- Manage relationships
- Preview information

**Top Toolbar:**
- **+ New** - Add new items
- **⚙️ Manage Fields** - Customize specification field names
- **Import/Export** - Bulk operations
- **Search** - Find products quickly

---

### Managing Fields

Before adding products, set up your specification field names to match your industry.

**Click "⚙️ Manage Fields" button** in the toolbar.

**Field Manager Dialog:**

**Quick Presets:**
- **Steel/Construction** - Size, Flange, Thickness, KSI
- **HVAC** - BTU Rating, CFM, Voltage, SEER
- **Electrical** - Voltage, Amperage, Wattage, Phase
- **Plumbing** - Diameter, PSI, Material, GPM

**Custom Fields:**
1. Click "Add Field" to create new specification field
2. Enter field name (e.g., "Load Capacity")
3. Optionally set field type (text, number, select)
4. Reorder fields by dragging
5. Remove unused fields with X button
6. Click "Save Changes"

**Important:** Field changes apply to ALL models in your catalog. Existing model data is preserved when field names change.

---

### Adding Categories

Categories are the top level of your product hierarchy.

**Method 1: Toolbar Button**
1. Click "+ New" in toolbar
2. Select "Category" from dropdown
3. Enter category name
4. Press Enter or click Save
5. Category appears in tree

**Method 2: Right-Click Menu**
1. Right-click on empty area or "Root"
2. Select "Add Category"
3. Enter name inline
4. Press Enter

**Best Practices:**
- Use broad, intuitive category names
- Aim for 5-15 categories (not too many)
- Match industry standards when possible
- Keep names short and clear

**Examples:**
- ✅ "C-Studs" - Clear and standard
- ✅ "HVAC Equipment" - Broad but specific
- ❌ "Miscellaneous" - Too vague
- ❌ "Category 1" - Not descriptive

---

### Adding Products

Products are added under categories.

**Steps:**
1. **Click on a Category** in the tree
2. **Inspector modal opens** on the right
3. **Navigate to Details tab**
4. **Scroll down to "Add Child" section**
5. **Click "+ Product" button**
6. **Enter product name** in the dialog
7. **Click Save** or press Enter
8. **Product appears** under the category

**Alternative Methods:**

**Kebab Menu (⋮):**
1. Hover over category node
2. Click ⋮ menu icon
3. Select "➕ Add Product"
4. Type name inline
5. Press Enter

**Keyboard Shortcut:**
1. Select category node
2. Press **Shift+N**
3. Type product name
4. Press Enter

**Best Practices:**
- Use specific product line names
- Include product family or series
- Avoid generic names like "Product 1"

**Examples:**
- ✅ "Steel Studs" - Clear product line
- ✅ "Hat Channel" - Specific product
- ❌ "Items" - Too generic

---

### Adding Types

Types are added under products.

**Steps:**
1. **Click on a Product** in the tree
2. **Inspector modal opens**
3. **Details tab** → scroll to "Add Child"
4. **Click "+ Type" button**
5. **Enter type name** (e.g., "20 Gauge")
6. **Click Save**
7. **Type appears** under the product

**Alternative:** Use kebab menu (⋮) or press Shift+N when product is selected.

**Best Practices:**
- Use key differentiators (gauge, size, capacity)
- Be specific but concise
- Match industry nomenclature

**Examples:**
- ✅ "20 Gauge" - Industry standard
- ✅ "Single Zone" - Clear variant
- ✅ "100 Amp" - Specific capacity
- ❌ "Type A" - Not descriptive

---

### Adding Subtypes (Optional)

Subtypes provide an additional grouping level between Types and Models.

**When to Use Subtypes:**
- Grouping models by size (e.g., "1-1/4" Flange", "1-1/2" Flange")
- Grouping by configuration (e.g., "Flanged", "Threaded")
- Grouping by specification range (e.g., "18 mil", "27 mil")
- Any other subgrouping that helps organize models

**When to Skip Subtypes:**
If your models don't need additional grouping, you can add Models directly under Types.

**Steps:**
1. **Click on a Type** in the tree
2. **Inspector modal opens**
3. **Details tab** → scroll to "Add Child"
4. **Click "+ Subtype" button**
5. **Enter subtype name** (e.g., "1-1/4\" Flange")
6. **Click Save**
7. **Subtype appears** under the type

**Alternative:** Use kebab menu (⋮) or press Shift+N when type is selected.

**Best Practices:**
- Use when you have multiple size variants
- Use when you have configuration options
- Be specific about what differentiates the subgroup
- Keep names concise

**Examples:**
- ✅ "1-1/4\" Flange" - Specific size/type
- ✅ "Flanged Connection" - Clear configuration
- ✅ "18 mil Coating" - Specific specification
- ❌ "Subtype 1" - Not descriptive

**Note:** Once you create a Subtype, you'll add Models under the Subtype instead of directly under the Type.

---

### Adding Models

Models are the actual products with specifications.

**Steps (when adding directly under Type):**
1. **Click on a Type** in the tree (if you're not using Subtypes)
2. **Inspector modal opens**
3. **Details tab** → scroll to "Add Child"
4. **Click "+ Model" button**
5. **Enter model number** (e.g., "362S162-20")
6. **Click Save**
7. **Model appears** under the type

**Steps (when adding under Subtype):**
1. **Click on a Subtype** in the tree (if you created Subtypes)
2. **Inspector modal opens**
3. **Details tab** → scroll to "Add Child"
4. **Click "+ Model" button**
5. **Enter model number** (e.g., "BV-125-FL")
6. **Click Save**
7. **Model appears** under the subtype

**Alternative:** Use kebab menu (⋮) or press Shift+N when type or subtype is selected.

**Best Practices:**
- Use manufacturer model numbers
- Include SKU or part number
- Be precise and accurate
- Match ordering systems

**Examples:**
- ✅ "362S162-20" - Exact model number
- ✅ "AHU-5000-1Z" - SKU format
- ❌ "Model 1" - Not specific

---

### Adding Specifications

Specifications are key-value pairs added to models.

**Steps:**
1. **Click on a Model** in the tree
2. **Inspector modal opens**
3. **Navigate to Fields tab** (not Details tab)
4. **Fill in specification fields:**
   - Size
   - Thickness
   - KSI
   - (or whatever fields you configured)
5. **Values save automatically** as you type
6. **Close inspector** when done

**Field Manager:**
If you need to add/change field names, click "⚙️ Manage Fields" in the toolbar first.

**Best Practices:**
- Fill in all relevant fields
- Use consistent units (inches, mm, etc.)
- Be precise with numbers
- Include all compliance data

**Examples:**
```
Size: 3.625"
Flange: 1.625"
Thickness: 20 GA
KSI: 33
```

---

## Editing Products

### Editing Item Details

**To Edit Any Item:**
1. Click on the item in the tree (Category, Product, Type, Subtype, or Model)
2. Inspector opens with Details tab
3. Edit name, slug, or other properties
4. Changes save automatically
5. Press Enter or click outside to confirm

**Editable Properties:**
- **Name** - Display name
- **Slug** - URL-friendly identifier (auto-generated)
- **Description** - Optional notes (internal use)

---

### Editing Specifications

**To Edit Model Specs:**
1. Click on the model in the tree
2. Switch to **Fields tab** in inspector
3. Edit specification values
4. Changes save automatically

**Bulk Editing:**
To edit multiple models with similar specs:
1. Edit first model completely
2. Note the values
3. Edit subsequent models (values are remembered in form)
4. Copy/paste for efficiency

---

## Organizing Products

### Reordering Items

**Drag and Drop:**
1. Click and hold on any item
2. Drag to new position
3. Drop between other items or into different parent
4. Order saves automatically

**Use Cases:**
- Alphabetize products
- Group related items
- Prioritize popular products
- Match catalog order

**Tips:**
- Products appear in frontend builder in this order
- Drag models within same type only
- Drag types within same product only

---

### Moving Items

**Change Parent:**
1. Drag the item
2. Drop onto new parent item
3. Item moves to new location
4. Composite keys update automatically

**Example:**
Move "362S162-20" from "20 Gauge" to "25 Gauge" type.

---

## Deleting Products

### Delete Individual Items

**Method 1: Inspector**
1. Click on the item to delete
2. Inspector opens
3. Click "Delete" button at bottom
4. Confirm deletion
5. Item removed from tree

**Method 2: Kebab Menu**
1. Hover over the item
2. Click ⋮ menu
3. Select "🗑️ Delete"
4. Confirm deletion

**Method 3: Keyboard**
1. Select the item
2. Press **Delete** or **Backspace** key
3. Confirm deletion

**Warning:** Deleting a parent (Category, Product, Type, or Subtype) deletes all children.

---

### Bulk Delete

**To Delete Multiple Items:**
1. Hold **Ctrl** (Windows) or **Cmd** (Mac)
2. Click multiple items to select
3. Press **Delete** key
4. Confirm bulk deletion

---

## Searching Products

### Using Search

**Search Box (Top Toolbar):**
1. Click search box
2. Type model number, name, or spec value
3. Tree filters to show matches only
4. Click X to clear search

**Search Includes:**
- Model numbers
- Product names
- Categories and types
- Specification values

**Use Cases:**
- Find product quickly in large catalog
- Verify product exists
- Locate duplicates

---

## Composite Keys

Every model has a unique composite key that identifies it across the system.

### Format

**Without Subtypes:**
```
category-slug:product-slug:type-slug:model-slug
```

**With Subtypes:**
```
category-slug:product-slug:type-slug:subtype-slug:model-slug
```

### Examples

**Without Subtype:**
```
c-studs:steel-studs:20-gauge:362s162-20
```

**With Subtype:**
```
valves:ball-valves:2-way:1-1-4-flange:bv-125-fl
```

### Where It's Used

- REST API endpoints
- Frontend selection tracking
- PDF generation
- Database storage
- URL parameters (Pro drafts feature)

### Automatic Generation

Composite keys are generated automatically from item names:
- Lowercase
- Spaces become hyphens
- Special characters removed
- Unique within hierarchy level

**Example Transformations:**
- "C-Studs" → `c-studs`
- "Steel Studs" → `steel-studs`
- "20 Gauge" → `20-gauge`
- "1-1/4\" Flange" → `1-1-4-flange`
- "362S162-20" → `362s162-20`

---

## Importing Products

### Bulk Import (Coming Soon)

Import products from CSV or JSON files.

**Supported Formats:**
- CSV with headers
- JSON structured data
- Excel spreadsheets (.xlsx)

**Import Process:**
1. Prepare import file with correct structure
2. Click "Import" button in toolbar
3. Upload file
4. Map columns to fields
5. Preview import
6. Confirm and import

**CSV Structure Example:**
```csv
Category,Product,Type,Model,Size,Thickness,KSI
C-Studs,Steel Studs,20 Gauge,362S162-20,3.625",20 GA,33
C-Studs,Steel Studs,20 Gauge,600S162-20,6",20 GA,33
Track,Track (C1P1),20 Gauge,250T125-20,2.5",20 GA,33
```

---

## Exporting Products

### Export Catalog

**Export Full Catalog:**
1. Click "Export" button in toolbar
2. Choose format (CSV or JSON)
3. File downloads
4. Save for backup or transfer

**Use Cases:**
- Backup before major changes
- Transfer to another site
- Share with team
- Data analysis in Excel

**Export Formats:**

**CSV:** Spreadsheet-compatible, easy to edit
**JSON:** Structured data, preserves hierarchy

---

## Best Practices

### Catalog Organization

✅ **Do:**
- Plan hierarchy before adding products
- Use consistent naming conventions
- Fill in all specifications completely
- Organize logically (alphabetically or by popularity)
- Set up field names before adding models

❌ **Don't:**
- Create too many categories (causes confusion)
- Skip specifications (incomplete data)
- Use inconsistent naming
- Create duplicate products
- Forget to save changes

---

### Naming Conventions

✅ **Do:**
- Use industry-standard terminology
- Be specific and descriptive
- Include model numbers exactly as manufacturer lists
- Use consistent units (all inches or all mm)

❌ **Don't:**
- Use vague names ("Product 1", "Item A")
- Mix naming styles within catalog
- Include unnecessary characters
- Use all caps (except for acronyms)

---

### Specifications

✅ **Do:**
- Include all relevant specs
- Use consistent units across all products
- Double-check accuracy
- Include compliance data (ASTM, etc.)

❌ **Don't:**
- Leave critical fields blank
- Use abbreviations inconsistently
- Include units in values (units should be in field name)
- Copy specs without verifying

---

## Troubleshooting

### Products not appearing in frontend

**Cause:** Product missing required specifications or hierarchy incomplete.

**Solution:**
1. Verify product has at least 4 levels:
   - Without Subtypes: Category → Product → Type → Model
   - With Subtypes: Category → Product → Type → Subtype → Model
2. Check that model has specifications filled in
3. Ensure Fields tab has values, not just Details tab
4. Clear cache (if caching enabled)

---

### Can't add child items

**Cause:** Wrong level selected or interface error.

**Solution:**
1. Verify you're adding child to correct parent type:
   - Categories can have Products
   - Products can have Types
   - Types can have Subtypes or Models
   - Subtypes can have Models
   - Models have no children
2. Refresh page and try again
3. Check browser console for JavaScript errors

---

### Drag and drop not working

**Cause:** Browser compatibility or JavaScript error.

**Solution:**
1. Update browser to latest version
2. Try different browser (Chrome, Firefox, Edge)
3. Check browser console for errors
4. Disable browser extensions temporarily

---

### Changes not saving

**Cause:** Network issue or permission problem.

**Solution:**
1. Check internet connection
2. Verify user has `manage_options` capability
3. Look for error messages in admin notices
4. Check browser console for AJAX errors

---

## Advanced Features

### Custom Field Types (Agency)

Define field types beyond simple text.

**Field Types:**
- **Text** - Free-form text
- **Number** - Numeric values only
- **Select** - Dropdown with preset options
- **URL** - Website or document links
- **Date** - Date values

---

### Product Templates (Agency)

Create product templates for faster data entry.

**Use Case:** Adding multiple similar products with same spec fields.

**Steps:**
1. Create first product completely
2. Save as template
3. Duplicate template for new products
4. Edit only differing values

---

### Revision History (Agency)

Track changes to products over time.

**Features:**
- See who edited what and when
- Revert to previous versions
- Compare changes side-by-side

---

## Next Steps

### Related Documentation

- [User Guide](./user-guide.md) - How customers use the builder
- [Admin Settings](./admin-settings.md) - Configuring the plugin
- [Branding & PDFs](./branding-pdfs.md) - Customizing PDF output
- [Troubleshooting](./troubleshooting.md) - Solving common issues

### Need Help?

- **Documentation:** [Full Documentation](./index.md)
- **WordPress.org Forum:** https://wordpress.org/support/plugin/submittal-builder/
- **Email Support:** support@webstuffguylabs.com (Pro users)

---

[← Back to Documentation](./index.md) | [Next: Branding & PDFs →](./branding-pdfs.md)

---

© 2025 WebStuff Guy Labs. All rights reserved.
