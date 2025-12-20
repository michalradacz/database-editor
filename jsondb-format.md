# JSONDB File Format Specification

**Version:** 1.0  
**File Extension:** `.jsondb`  
**MIME Type:** `application/json`  
**Encoding:** UTF-8

## Overview

JSONDB is a simple, human-readable database format designed for lightweight relational data storage. It supports multiple tables, various field types, and relationships between tables.

## File Structure

A JSONDB file is a valid JSON document with the following top-level structure:

```json
{
  "meta": { ... },
  "tables": [ ... ]
}
```

## Schema

### Root Object

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `meta` | object | Yes | Database metadata |
| `tables` | array | Yes | Array of table definitions |

### Meta Object

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | string | Yes | Human-readable name of the database |
| `columnVisibility` | object | No | UI settings for column visibility |

The `columnVisibility` object uses table IDs as keys, with nested objects mapping field IDs to boolean visibility values.

### Table Object

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | string | Yes | Unique identifier (format: `id_[a-z0-9]+`) |
| `name` | string | Yes | Display name of the table |
| `fields` | array | Yes | Array of field definitions |
| `records` | array | Yes | Array of data records |

### Field Object

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | string | Yes | Unique identifier (format: `id_[a-z0-9]+`) |
| `name` | string | Yes | Display name of the field |
| `type` | string | Yes | Data type (see Field Types below) |
| `options` | string | Conditional | Comma-separated values for `select` type |
| `compositeTemplate` | string | Conditional | Template for `composite` type |
| `primary` | boolean | No | If true, this field represents the record's display name |
| `filter` | boolean | No | If true, filtering is enabled for this field |
| `targetTableId` | string | Conditional | Target table ID for `parent`/`children` types |
| `parentFieldId` | string | No | Back-reference field ID for `children` type |

### Field Types

| Type | Description | Value Format |
|------|-------------|--------------|
| `text` | Single-line text | string |
| `textarea` | Multi-line text with Markdown support | string |
| `number` | Numeric value | number |
| `date` | Date value | string (ISO 8601: `YYYY-MM-DD`) |
| `boolean` | True/false value | boolean |
| `select` | Selection from predefined options | string |
| `composite` | Computed field from other fields | N/A (computed) |
| `parent` | Reference to a record in another table | string (record ID) |
| `children` | Computed list of referencing records | N/A (computed) |

### Record Object

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | string | Yes | Unique identifier (format: `id_[a-z0-9]+`) |
| `values` | object | Yes | Field values keyed by field ID |

## Field Type Details

### Text (`text`)
Simple single-line text input.

### Textarea (`textarea`)
Multi-line text with Markdown rendering support. Supports:
- Headers (`#`, `##`, `###`)
- Bold (`**text**`) and italic (`*text*`)
- Lists (ordered and unordered)
- Code blocks and inline code
- Blockquotes
- Links

### Number (`number`)
Numeric values stored as JSON numbers. Supports integers and decimals.

### Date (`date`)
Date values stored as ISO 8601 strings (`YYYY-MM-DD`).

### Boolean (`boolean`)
True/false values stored as JSON booleans.

### Select (`select`)
Selection from a predefined list. Options are defined in the `options` property as a comma-separated string.

**Example:**
```json
{
  "type": "select",
  "options": "Low,Medium,High,Critical"
}
```

### Composite (`composite`)
A computed field that concatenates values from other fields. The template uses `{FieldName}` placeholders.

**Example:**
```json
{
  "type": "composite",
  "compositeTemplate": "{FirstName} {LastName} ({Department})"
}
```

Composite fields can be marked as `primary` to create dynamic record display names.

### Parent (`parent`)
Creates a many-to-one relationship. The value stores the ID of a record in the target table.

**Example:**
```json
{
  "type": "parent",
  "targetTableId": "id_abc123xyz"
}
```

### Children (`children`)
A computed field that displays all records from another table that reference this record. Requires `targetTableId` and optionally `parentFieldId` to specify which parent field to follow.

## Relationships

JSONDB supports relational data through `parent` and `children` field types:

1. **Parent Field**: Stores a reference (record ID) to a record in another table
2. **Children Field**: Computed inverse relationship showing all records that reference this record

**Example: Projects and Tasks**

```json
{
  "tables": [
    {
      "id": "id_projects",
      "name": "Projects",
      "fields": [
        { "id": "id_pname", "name": "Name", "type": "text", "primary": true },
        { "id": "id_ptasks", "name": "Tasks", "type": "children", "targetTableId": "id_tasks" }
      ],
      "records": [
        { "id": "id_p1", "values": { "id_pname": "Website Redesign" } }
      ]
    },
    {
      "id": "id_tasks",
      "name": "Tasks",
      "fields": [
        { "id": "id_tname", "name": "Name", "type": "text", "primary": true },
        { "id": "id_tproject", "name": "Project", "type": "parent", "targetTableId": "id_projects" }
      ],
      "records": [
        { "id": "id_t1", "values": { "id_tname": "Design mockups", "id_tproject": "id_p1" } },
        { "id": "id_t2", "values": { "id_tname": "Implement frontend", "id_tproject": "id_p1" } }
      ]
    }
  ]
}
```

## ID Generation

IDs follow the pattern `id_[timestamp][random]` where:
- `timestamp` is the current time in base-36
- `random` is a random string in base-36

Example: `id_m4x7k2a9bc3def`

## Complete Example

```json
{
  "meta": {
    "name": "Contact Database",
    "columnVisibility": {
      "id_contacts": {
        "id_notes": false
      }
    }
  },
  "tables": [
    {
      "id": "id_companies",
      "name": "Companies",
      "fields": [
        {
          "id": "id_cname",
          "name": "Company Name",
          "type": "text",
          "primary": true,
          "filter": true
        },
        {
          "id": "id_cemployees",
          "name": "Employees",
          "type": "children",
          "targetTableId": "id_contacts",
          "parentFieldId": "id_company"
        }
      ],
      "records": [
        {
          "id": "id_comp1",
          "values": {
            "id_cname": "Acme Corporation"
          }
        }
      ]
    },
    {
      "id": "id_contacts",
      "name": "Contacts",
      "fields": [
        {
          "id": "id_fname",
          "name": "First Name",
          "type": "text"
        },
        {
          "id": "id_lname",
          "name": "Last Name",
          "type": "text"
        },
        {
          "id": "id_fullname",
          "name": "Full Name",
          "type": "composite",
          "compositeTemplate": "{First Name} {Last Name}",
          "primary": true
        },
        {
          "id": "id_email",
          "name": "Email",
          "type": "text"
        },
        {
          "id": "id_company",
          "name": "Company",
          "type": "parent",
          "targetTableId": "id_companies",
          "filter": true
        },
        {
          "id": "id_priority",
          "name": "Priority",
          "type": "select",
          "options": "Low,Medium,High",
          "filter": true
        },
        {
          "id": "id_active",
          "name": "Active",
          "type": "boolean",
          "filter": true
        },
        {
          "id": "id_birthdate",
          "name": "Birth Date",
          "type": "date"
        },
        {
          "id": "id_notes",
          "name": "Notes",
          "type": "textarea"
        }
      ],
      "records": [
        {
          "id": "id_rec1",
          "values": {
            "id_fname": "John",
            "id_lname": "Doe",
            "id_email": "john.doe@acme.com",
            "id_company": "id_comp1",
            "id_priority": "High",
            "id_active": true,
            "id_birthdate": "1985-03-15",
            "id_notes": "Key contact for **sales** department.\n\n## Notes\n- Prefers email communication\n- Available Mon-Thu"
          }
        }
      ]
    }
  ]
}
```

## Validation

A JSON Schema is available for validating JSONDB files: `jsondb-schema.json`

## Importing Data

When importing CSV/TSV data:
- The first row should contain column headers matching field names
- Records with matching primary field values are updated (upsert behavior)
- New records are created for non-matching entries

## Best Practices

1. **Use descriptive names**: Table and field names should be clear and meaningful
2. **Set primary fields**: Always designate one field as primary for better record identification
3. **Enable filters wisely**: Only enable filtering on fields that benefit from it
4. **Use composite fields**: For complex display names, use composite fields instead of duplicating data
5. **Leverage relationships**: Use parent/children fields to maintain referential integrity

## License

This specification is released under the MIT License. Implementations are free to use this format without restriction.
