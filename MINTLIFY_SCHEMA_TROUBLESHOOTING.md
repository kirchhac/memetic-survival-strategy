# Mintlify Schema Troubleshooting Guide

## Common Schema Errors & Solutions

### **Error: "Invalid discriminator value. Expected 'mint' | 'maple' | 'palm' | 'willow' | 'linden' | 'almond' | 'aspen'"**
**Solution**: Add the required `theme` field to your `docs.json`:
```json
{
  "theme": "mint"
}
```

### **Error: "Unrecognized key(s) in object: 'anchors'"**
**Solution**: Remove the `colors.anchors` field - it's no longer supported in modern Mintlify.

### **Error: "Invalid type. Expected field to be of type 'object', received 'array'"**
**Solution**: Navigation structure has changed. Use the new format:
```json
"navigation": {
  "dropdowns": [
    {
      "dropdown": "Documentation",
      "icon": "book",
      "description": "Your description",
      "groups": [
        {
          "group": "Group Name",  // Note: "group" not "title"
          "pages": ["page1", "page2"]
        }
      ]
    }
  ]
}
```

### **Error: "navigation.groups[0].group: This field is required"**
**Solution**: Each group must have a `group` field (not `title`):
```json
{
  "group": "Welcome",  // ✅ Correct
  "pages": ["introduction"]
}
```

## **Current Working Schema Structure (2024)**

```json
{
  "$schema": "https://mintlify.com/schema.json",
  "name": "Your Project Name",
  "theme": "mint",
  "logo": {
    "dark": "/logo/dark.svg",
    "light": "/logo/light.svg"
  },
  "favicon": "/favicon.png",
  "colors": {
    "primary": "#000000",
    "light": "#ffffff",
    "dark": "#000000"
  },
  "topbarLinks": [
    {
      "name": "GitHub",
      "url": "https://github.com/yourusername/repo"
    }
  ],
  "topbarCtaButton": {
    "name": "Get Started",
    "url": "/introduction"
  },
  "anchors": [
    {
      "name": "GitHub",
      "icon": "simple-icons:github",
      "url": "https://github.com/yourusername/repo"
    }
  ],
  "navigation": {
    "dropdowns": [
      {
        "dropdown": "Documentation",
        "icon": "book",
        "description": "Your description",
        "groups": [
          {
            "group": "Getting Started",
            "pages": ["introduction", "quick-start"]
          }
        ]
      }
    ]
  },
  "footerSocials": {
    "github": "https://github.com/yourusername/repo"
  },
  "search": {
    "include": ["**/*.mdx"]
  },
  "css": "./styles.css"
}
```

## **Key Changes from Legacy Schema**

1. **Required Fields**: `theme` is now mandatory
2. **Navigation**: Must use `dropdowns` with `groups` containing `group` field
3. **Colors**: `anchors` field removed from colors object
4. **Structure**: More hierarchical navigation structure

## **Troubleshooting Steps**

1. **Check Official Examples**: Always look at [Mintlify's official docs](https://github.com/mintlify/docs) for current schema
2. **Validate Schema**: Use `mint dev` to test locally before pushing
3. **Error Messages**: Read error messages carefully - they often point to specific field issues
4. **Schema Updates**: Mintlify frequently updates their schema - check for changes

## **Resources**

- **Official Schema**: https://mintlify.com/schema.json
- **Official Examples**: https://github.com/mintlify/docs
- **Community**: https://mintlify.com/community
- **Documentation**: https://mintlify.com/docs

---

**Last Updated**: August 2024  
**Based on**: Experience with "The Stars Within Us" project  
**Status**: Working with Mintlify's current schema
