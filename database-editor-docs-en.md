# Database Editor - User Guide

https://github.com/michalradacz/database-editor

https://mrt.site44.com/database-editor.html

## Introduction

Database Editor is a web application for creating and managing simple relational databases. It allows you to define multiple tables with various field types, create relationships between tables, and work with data without requiring installation or a server.

### Key Features

- Create multiple tables in a single database
- 9 different field types including table relationships
- Composite fields for dynamic record names
- Filtering and searching records
- Import and export data in CSV and TSV formats
- Generate text from records using templates
- Automatic saving to browser storage
- Markdown support in text fields
- Fully offline functionality
- Bilingual interface (English/Czech)

### File Format

The application uses a custom `.jsondb` format - a human-readable JSON file containing both structure and data.

---

I## Changelog

* v1.3.1 small but important improvement, bulk operations for records selected by user
* v 1.3: New big function - View data structure (displays textual and graphical view for whole data semantic structure for current record)
* v 1.2: Tags and Collections for better data organization across whole database
* v 1.1: New URL field type and grouping in table of record
* v 1.0: First public version on Github)


## Getting Started

### First Launch

1. Open [online editor](https://mrt.site44.com/database-editor) / or download and Open the `database-editor.html` file in a modern web browser (Chrome, Firefox, Edge, Safari)
2. The application starts with an empty database called "New Database"
3. The **⚙️ Management** tab is displayed automatically

### Creating Your First Database

1. In the **Management** tab → **Database** subtab, enter your database name
2. Go to the **Tables** subtab and click **Add Table**
3. Name your table (e.g., "Contacts") and click **Save**
4. Click the **Fields** button next to your created table
5. Add the fields you need (e.g., Name, Email, Phone)
6. Mark one field as **Primary** - it will serve as the record's display name
7. Click on the table tab in the top bar
8. Add records using the **➕ Add Record** button

### Saving and Loading

| Action | Description |
|--------|-------------|
| **New** | Creates a new empty database (warning: deletes current data) |
| **Load** | Opens an existing `.jsondb` file from disk |
| **Save** | Downloads the database as a `.jsondb` file |
| **Copy JSON** | Copies the entire database to clipboard |
| **Paste JSON** | Loads database from clipboard (or opens input dialog on mobile) |

### Auto-Save

The application automatically saves the database state to browser storage. After refreshing the page or closing and reopening the browser, you'll find your data as you left it.

⚠️ **Important:** For permanent storage, always use the **Save** button to download a `.jsondb` file. Browser storage may be cleared when clearing history or in incognito mode.

---

## Application Interface

### Header

The top section of the screen contains:

- **Database Editor** - application name
- **New** - creates a new empty database
- **Load** - loads database from file
- **Save** - downloads database as file
- **Copy JSON** - copies database to clipboard
- **Paste JSON** - loads database from clipboard
- **Language** - toggle between English (EN) and Czech (CS)

### Table Tabs

Below the header is a row of tabs:

- **Individual table tabs** - click to view table data
- **⚙️ Management** - database settings, table management, and tools

The active tab is highlighted.

### Window Title

The browser window title displays:
- Database name
- Currently displayed table name

Format: `Database: [name] | [table]`

---

## Database Management

The **⚙️ Management** tab contains three subtabs:

### Database Subtab

Contains:
- **Database name** - text field to change the name
- **Statistics** - overview of table count and total records

### Tables Subtab

List of all tables in the database. Each table shows:
- Table name
- Number of fields
- Number of records

**Buttons for each table:**

| Button | Action |
|--------|--------|
| ▲ | Move table up |
| ▼ | Move table down |
| **Fields** | View and edit field definitions |
| ✏️ | Rename table |
| 🗑️ | Delete table including all data |

**Adding a new table:**
1. Click **Add Table**
2. Enter the name
3. Click **Save**

### Tools Subtab

Contains the **Text Generator** - see [Text Generator](#text-generator) section.

---

## Working with Tables

### Creating a Table

1. Go to **⚙️ Management** → **Tables**
2. Click **Add Table**
3. Enter the table name
4. Click **Save**

The new table appears in the list and as a new tab.

### Renaming a Table

1. Click ✏️ next to the table
2. Edit the name
3. Click **Save**

### Deleting a Table

1. Click 🗑️ next to the table
2. Confirm deletion in the dialog

⚠️ **Warning:** Table deletion is irreversible and removes all data and field definitions. Save your database before deleting.

### Changing Table Order

Use the ▲ and ▼ arrows to move tables in the list. The order determines the tab order in the top bar.

---

## Field Definitions

### Viewing Table Fields

1. In **⚙️ Management** → **Tables**, click **Fields** next to the desired table
2. The **Table Fields** card appears with a list of all fields

### Adding a Field

1. Click **Add Field**
2. Enter the **Field Name**
3. Select the **Field Type** (see below)
4. Fill in additional settings based on type
5. Optionally check:
   - **Primary (record name)** - this field's value will represent the record
   - **Enable filtering** - shows a filter for this field in table view
   - **Grouping**: Allow grouping table of records by this field, can be folded and unfolded
6. Click **Save**

### Field Types

#### Text

Single-line text field for short texts (names, titles, codes).

#### Multi-line Text / Markdown

Multi-line text field with Markdown formatting support. When viewing a record, the text is rendered as formatted.

**Supported formatting:**
- `# Heading 1`, `## Heading 2`, `### Heading 3`
- `**bold text**`
- `*italic*`
- `- list item` or `* list item`
- `1. numbered list`
- `` `inline code` ``
- ` ``` code block ``` `
- `> blockquote`
- `[link text](URL)`
- `---` horizontal rule

#### Number

Numeric field for integers and decimals. Enables proper value-based sorting.

#### Date

Date picker field with calendar. Dates are stored in ISO format (YYYY-MM-DD) and displayed in local format.

#### Yes/No

Checkbox field for boolean values. Displays as "Yes" or "No".

#### Selection List

Dropdown menu with predefined values.

**Settings:**
- In the **Values (comma-separated)** field, enter the options
- Example: `Low,Medium,High,Critical`

#### URL

Clickable link for URL address.


#### Composite

Calculated field combining values from other fields using a template.

**Settings:**
1. Click the field name buttons to insert them into the template
2. Or manually write the template with `{Field Name}` placeholders

**Template example:** `{First Name} {Last Name} ({Department})`

**Properties:**
- Value is calculated automatically when displayed
- Field cannot be directly edited
- Can be marked as primary for dynamic record names
- Supports values from field types: text, number, date, yes/no, selection, parent record

#### Parent Record

Creates an N:1 (many-to-one) relationship to records in another table.

**Settings:**
- Select **Target Table** - the table from which to select the parent record

**Usage:**
- When editing a record, select the parent record from a dropdown
- The ➕ button allows creating a new parent record directly while editing
- In record view, the link to parent record is clickable

#### Child Records

Displays a list of records from another table that reference this record (inverse relationship).

**Settings:**
- **Target Table** - table containing child records
- **Back-reference Field** (optional) - specific "Parent Record" field in target table

**Properties:**
- This field is not directly edited
- Records are displayed automatically based on relationships
- Hidden by default in table view (can be enabled)

### Editing a Field

1. Click ✏️ next to the field
2. Modify settings
3. Click **Save**

### Deleting a Field

1. Click 🗑️ next to the field
2. Confirm deletion

⚠️ **Warning:** Data in this field will be irreversibly deleted from all records.

### Changing Field Order

Use the ▲ and ▼ arrows. Order affects:
- Column order in the table
- Field order in the edit form
- Field order in record detail view

---

## Working with Records

### Viewing Records

Click on a table tab in the top bar. You'll see:

1. **Table name** and Export/Import/Add Record buttons
2. **Search field** and filters
3. **Record count** (filtered / total)
4. **Records table** with actions
5. **Column visibility** (collapsible section)

### Adding a Record

1. Click **➕ Add Record**
2. Fill in field values in the form
3. Click **Save**

**Creating a parent record on the fly:**

If you need to select a parent record that doesn't exist yet:
1. Click ➕ next to the parent record dropdown
2. Fill in and save the new parent record
3. You'll return to the original form with the new record automatically selected

### Viewing Record Details

Click on:
- The primary field value (record name) in the table
- A link to parent/child record
- The 👁️ button in the record row

**In the record detail view you'll see:**
- All fields with values
- Formatted Markdown text
- Clickable links to related records
- **Edit** button to switch to editing mode

### Editing a Record

1. Click ✏️ next to the record in the table, or
2. In record detail view, click **Edit**
3. Change values in the form
4. Click **Save**

### Deleting a Record

1. Click 🗑️ next to the record
2. Confirm deletion in the dialog

⚠️ Deleting a record may affect records in other tables that reference it.

---

## Filtering and Searching

### Full-text Search

The **Search...** field above the table searches all record fields.

**Properties:**
- Case-insensitive search
- Searches anywhere in text (not just at the beginning)
- Results update immediately as you type
- Searches even in fields that aren't displayed

### Filters

For fields with filtering enabled, a dropdown menu appears.

**Filter options:**
- **All values** - shows all records (no filter)
- **(no value)** - shows records with empty field
- **Specific value** - shows only records with this value

**Combining filters:**
- Filters can be combined with search
- When using multiple filters, only records matching all conditions are shown (logical AND)

### Sorting

Click on a column header to sort:
- **First click:** ascending (▲ after name)
- **Second click:** descending (▼ after name)
- **Third click:** default order

**Sorting by field type:**
- Text: alphabetically
- Number: numerically
- Date: chronologically
- Yes/No: No before Yes
- Composite field: by calculated text value

### Column Visibility

1. Click **Column Visibility** below the table to expand
2. Check or uncheck columns
3. Changes take effect immediately

**Notes:**
- **Child Records** fields are hidden by default
- Visibility settings are saved with the database

---

## Import and Export

### Export to CSV/TSV

1. In table view, click **📤 Export**
2. Select format:
   - **CSV (comma)** - comma-separated values
   - **TSV (tab)** - tab-separated values
3. Data appears in the text area
4. Use:
   - **📋 Copy** - copies to clipboard
   - **💾 Save File** - downloads as .csv or .tsv file

**Export includes:**
- Header with field names
- All records in the table
- Child Records and Composite fields are not exported (they're calculated)

### Import from CSV/TSV

1. In table view, click **📥 Import**
2. Select format (CSV or TSV)
3. Load data:
   - **Load file** - select file from disk, or
   - **Paste data** - directly into the text area
4. Check **First row contains column names** if applicable
5. Click **Import**

**Import behavior (Upsert):**
- Columns are matched by name to existing fields
- If a record with the same primary field value exists → **it's updated**
- If the record doesn't exist → **a new one is created**
- After import, the count of new and updated records is displayed

**Import tips:**
- Column names in CSV must exactly match field names
- For Yes/No fields use: true/false, 1/0, yes/no
- For Date fields use format YYYY-MM-DD
- Parent Record field requires the ID of an existing record

---

## Text Generator

The text generator allows creating bulk text output from records using a template.

### Usage

1. Go to **⚙️ Management** → **Tools**
2. In the **Text Generator** section:
   - Select a table
   - Click field buttons to insert them into the template
   - Or write the template manually with `{Field Name}` placeholders
3. Select data source:
   - **All records** - uses all records in the table
   - **Filtered records** - uses only records matching the current filter
4. Click **Generate**
5. Copy the result using the **Copy** button

### Template Examples

**Email list:**
```
{Name} <{Email}>
```

**Address labels:**
```
{First Name} {Last Name}
{Street}
{ZIP} {City}
---
```

**Custom format CSV export:**
```
"{Name}";"{Surname}";"{Phone}"
```

**HTML list:**
```
<li><a href="mailto:{Email}">{First Name} {Last Name}</a></li>
```

### Supported Placeholders

- `{Field Name}` - value of text, number field
- For Yes/No fields: displays "Yes" or "No"
- For Date: displays in local format
- For Parent Record: displays the parent record's name
- For non-existent fields: placeholder remains unchanged

---

## Tips and Tricks

### Efficient Database Structure

1. **Use relationships** instead of repeating data
   - Bad: Repeating full company address in each contact
   - Good: Companies table + Contacts table with company reference

2. **Set primary field** for each table
   - Makes record identification easier
   - Displayed in links and lists

3. **Use composite fields** for complex names
   - Example: `{Last Name}, {First Name}` as primary field

4. **Enable filtering** only on fields where it makes sense
   - Typically: Status, Category, Type, Priority
   - Not suitable for: Notes, Description, unique values

### Backups

- Regularly save the database using the **Save** button
- Keep multiple versions of `.jsondb` files
- Auto-save in browser is only temporary

### Working on Mobile

- The application is responsive and works on mobile devices
- For pasting JSON on mobile, a text input automatically opens (Clipboard API often doesn't work)
- Use horizontal scroll for wide tables

### Transfer Between Devices

1. **Using file:** Save `.jsondb`, transfer, load
2. **Using clipboard:** Copy JSON → transfer text → Paste JSON

---

## Troubleshooting

### Data Not Saving

**Cause:** Auto-save to browser may fail in incognito mode or when storage is full.

**Solution:** Always use the **Save** button to download a `.jsondb` file.

### Cannot Paste JSON from Clipboard (Mobile)

**Cause:** Mobile browsers often block the Clipboard API.

**Solution:** The application automatically opens a text field where you can paste JSON manually (long press → Paste).

### Import Not Working Correctly

**Possible causes and solutions:**

1. **Wrong column names** - Names must exactly match field names (including special characters)
2. **Wrong format** - Check if you're using the correct delimiter (comma vs. tab)
3. **Missing header** - Check/uncheck "First row contains column names"

### Records Disappeared After Import

**Cause:** Import uses upsert logic - records with the same primary field are overwritten.

**Solution:** Save a backup of the database before importing.

### Relationships Between Tables Not Working

**Checklist:**
1. "Parent Record" field has the correct target table set
2. Records exist in the target table
3. For "Child Records" field, there's a corresponding "Parent Record" field in the other table

### Application Is Slow

**Possible causes:**
- Too many records (thousands) in one table
- Too many columns displayed at once
- Older browser or device

**Solutions:**
- Hide unnecessary columns
- Split data into multiple tables
- Use a modern browser

---

## Support

Database Editor is an open-source application.

**File Format:** The `.jsondb` format specification is available in the `JSONDB-FORMAT.md` document, including JSON Schema for validation.

---

*Last updated: 2025*
