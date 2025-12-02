---
description: >-
  This guide provides setup instructions and functionality documentation for
  administrators deploying the Revenue Cloud visual configuration components.
---

# Revenue Cloud Addon - Administrator Guide

### Table of Contents <a href="#table-of-contents" id="table-of-contents"></a>

1. [Component Overview](https://file+.vscode-resource.vscode-cdn.net/Users/erikpilgrim/revenueCloudAddon/ADMIN_GUIDE.md#component-overview)
2. [Visual Logic Generator - Quick Action Setup](https://file+.vscode-resource.vscode-cdn.net/Users/erikpilgrim/revenueCloudAddon/ADMIN_GUIDE.md#visual-logic-generator)
3. [Revenue Cloud Configuration - Flow Integration](https://file+.vscode-resource.vscode-cdn.net/Users/erikpilgrim/revenueCloudAddon/ADMIN_GUIDE.md#revenue-cloud-configuration)
4. [Revenue Cloud Bulk Generator](https://file+.vscode-resource.vscode-cdn.net/Users/erikpilgrim/revenueCloudAddon/ADMIN_GUIDE.md#revenue-cloud-bulk-generator)
5. [Apex Helper Class](https://file+.vscode-resource.vscode-cdn.net/Users/erikpilgrim/revenueCloudAddon/ADMIN_GUIDE.md#apex-helper-class)

***

### Component Overview <a href="#component-overview" id="component-overview"></a>

This package contains three Lightning Web Components designed to enhance Salesforce Revenue Cloud with visual 2D/3D product configuration capabilities:

| Component                        | Type                           | Purpose                                                               |
| -------------------------------- | ------------------------------ | --------------------------------------------------------------------- |
| **Visual Logic Generator**       | Quick Action                   | Generate visual logic for individual products with interactive scenes |
| **Revenue Cloud Configuration**  | Flow Screen / Custom Component | Real-time 2D/3D visualization during product configuration            |
| **Revenue Cloud Bulk Generator** | Standalone Tool                | Batch generate visual logic for multiple products simultaneously      |

All components integrate with the **RDraw** namespace for rendering capabilities.

***

### Visual Logic Generator <a href="#visual-logic-generator" id="visual-logic-generator"></a>

#### Purpose <a href="#purpose" id="purpose"></a>

The Visual Logic Generator is a wizard-based tool that automates the creation of visual interaction logic for Product2 records. It generates change events for product attributes and product-related components, linking them to 2D or 3D scene interactions.

#### Use Case <a href="#use-case" id="use-case"></a>

Use this component when configuring individual products that require visual representation during the quote/order process. The component reads product attributes, picklist values, and product components, then generates interaction events that control visual scene behavior.

#### Setup Instructions <a href="#setup-instructions" id="setup-instructions"></a>

**Step 1: Add as Quick Action to Product2**

1. Navigate to **Setup → Object Manager → Product2**
2. Select **Buttons, Links, and Actions**
3. Click **New Action**
4. Configure the action:
   * **Action Type**: Lightning Component
   * **Lightning Component**: `c:visualLogicGenerator`
   * **Height**: 600
   * **Label**: "Generate Visual Logic"
   * **Name**: `Generate_Visual_Logic`
5. Click **Save**

**Step 2: Add Action to Product2 Page Layout**

1. Navigate to **Setup → Object Manager → Product2 → Page Layouts**
2. Select the page layout(s) where you want the action available
3. Click **Layout Properties → Quick Actions**
4. Drag the **Generate Visual Logic** action into the **Salesforce Mobile and Lightning Experience Actions** section
5. Click **Save**

**Step 3: Verify Prerequisites**

Ensure the following data exists:

* Product must have a relationship to RDraw scene settings field (typically `RDraw__X3DSceneSettings__c` or `RDraw__2DSceneSettings__c`)
* Product has attributes defined via:
  * Product Classification → Attribute Definitions
  * Direct Product Attribute Definitions
* Product has Product Related Components configured (optional)

#### How to Use <a href="#how-to-use" id="how-to-use"></a>

1. Navigate to a **Product2** record
2. Click the **Generate Visual Logic** quick action button
3. Follow the wizard steps:

**Phase 1: Select Visual Scene Type**

* Choose between **2D Scene** or **3D Scene**
* This determines which scene settings field will be updated

**Phase 2: Pick Options**

* Select whether to generate logic for:
  * **Product Attributes** (includes picklist values)
  * **Product Related Components** (includes child products)
* Configure options:
  * **Generate Both Conditions**: Creates both checked/unchecked states for components

**Phase 3: Pick Values**

* Review the list of available attributes and component groups
* Check the boxes for items you want to include in generation
* Use **Select All** / **Select None** for bulk selection
* **Selected Count** shows your current selections

**Phase 4: Generate Logic**

* Review the generation plan showing:
  * Attributes to add
  * Picklist values to process
  * Component groups to add
  * Estimated time saved (10 min per attribute, 5 min per value, etc.)
* Click **Next** to generate

**Phase 5: Review**

* Review generated interaction events and actions
* View any collision warnings (existing interactions with same names)
* Click **Save** to persist the scene settings to the product record
* Click **Close** when complete

#### Key Features <a href="#key-features" id="key-features"></a>

* **Collision Detection**: Warns if interaction events already exist with the same name
* **Picklist Integration**: Automatically fetches picklist values and creates actions for each
* **Component Grouping**: Groups related product components by ProductComponentGroup
* **Time Estimation**: Calculates estimated manual configuration time saved
* **Notifications**: Real-time status updates during processing

#### Field Mappings <a href="#field-mappings" id="field-mappings"></a>

The component interacts with these Salesforce objects:

* `Product2` - Source product record
* `AttributeDefinition` - Product attributes
* `AttributePicklistValue` - Picklist options
* `ProductRelatedComponent` - Child product relationships
* `ProductComponentGroup` - Component groupings

***

### Revenue Cloud Configuration <a href="#revenue-cloud-configuration" id="revenue-cloud-configuration"></a>

#### Purpose <a href="#purpose-1" id="purpose-1"></a>

The Revenue Cloud Configuration component provides real-time 2D/3D visualization within the Salesforce Revenue Cloud product configurator. As users select options, attributes, and components, the visual scene updates dynamically.

#### Use Case <a href="#use-case-1" id="use-case-1"></a>

Embed this component in:

* Lightning Flows (Product Configuration screens)
* Custom configurator pages
* Quote Line Editor customizations

It displays a visual representation that updates based on:

* Attribute field changes
* Product component selections
* Transaction item updates

#### Setup Instructions <a href="#setup-instructions-1" id="setup-instructions-1"></a>

**Option 1: Add to Lightning Flow (Recommended)**

1. Navigate to **Setup → Flows**
2. Open or create a Product Configuration flow
3. Add a **Screen** element where you want visualization
4. Add a **Lightning Web Component** to the screen:
   * Component: RDrawConfig`:revenueCloudConfiguration`
5. Configure the component properties:

| Property                | Type            | Description                            | Example                                            |
| ----------------------- | --------------- | -------------------------------------- | -------------------------------------------------- |
| `configuratorContext`   | Apex Object     | Product configurator context from flow | `{!ConfiguratorContext}`                           |
| `salesTransactionItems` | Apex Collection | Current quote line items               | `{!SalesTransactionItems}`                         |
| `optionGroups`          | Apex Collection | Available option groups                | `{!OptionGroups}`                                  |
| `renderContext`         | String          | Rendering mode                         | `"3D"` or `"2D"`                                   |
| `visualUpdateType`      | String          | Update trigger type                    | `"both"`, `"inputChange"`, or `"transactionItems"` |
| `size`                  | String          | Component size                         | `"Medium"`, `"Large"`, `"Jumbo"`                   |
| `allowPinning`          | Boolean         | Enable pin to viewport                 | `true` or `false`                                  |
| `overrideRecordId`      | String          | Optional Product2 ID override          | Product2 record ID                                 |

6. Wire the configurator context variables to the component inputs
7. Save and activate the flow

**Option 2: Add to Custom Lightning Page**

1. Navigate to the **Lightning App Builder**
2. Open the Product Configuration page or create a custom page
3. Drag the **revenueCloudConfiguration** component onto the page
4. Configure the component properties in the right panel
5. Set up visibility rules if needed
6. Save and activate the page

#### Component Properties Explained <a href="#component-properties-explained" id="component-properties-explained"></a>

**`configuratorContext`**

* Receives the product configuration session context
* Contains current product, transaction line ID, and configuration state
* Automatically populated by Revenue Cloud flows

**`salesTransactionItems`**

* Array of transaction line items (quote lines)
* Component watches for changes and updates visualization accordingly
* Includes attributes, components, quantities, and selections

**`renderContext`**

* `"3D"` - Displays 3D canvas renderer
* `"2D"` - Displays 2D canvas renderer

**`visualUpdateType`**

* `"both"` - Updates on both input changes AND transaction item changes (default)
* `"inputChange"` - Only updates when attribute/component fields change manually
* `"transactionItems"` - Only updates when transaction items array changes

**`allowPinning`**

* When `true`, displays a pin icon that fixes the canvas to the viewport
* Useful for keeping visualization visible while scrolling through options

#### How It Works <a href="#how-it-works" id="how-it-works"></a>

**Interaction Flow**

1. **Initialization**
   * Component loads change detection
   * Subscribes to Message channels
   * Fetches Product from configuratorContext or quote line item
2. **Change Detection**
   * Monitors `salesTransactionItems` for changes&#x20;
   * Detects additions, deletions, and edits to transaction items
   * Processes changes sequentially with 100ms delay between updates
3. **Visual Updates**
   * Retrieves attribute definitions and picklist values
   * Maps attribute/component IDs to interaction event names
   * Raises interaction events on the canvas (2D or 3D)
   * Canvas renderer applies visual logic (show/hide, transform, etc.)

**Message Channel Integration**

The component subscribes to Standard Revenue Cloud notification channel

When attribute values or component selections change:

1. Notification is published to message channel
2. Component receives notification
3. Component calls `updateVisualLogicForAttribute()` or `updateVisualLogicForProductRelatedComponent()`
4. Canvas interaction event is raised
5. Visual scene updates based on scene settings

#### Advanced Configuration <a href="#advanced-configuration" id="advanced-configuration"></a>

**Custom Interaction Events**

Scene settings (stored in `RDraw__X3DSceneSettings__c` or `RDraw__2DSceneSettings__c`) define interaction events:

```json
{
  "interactions": [
    {
      "id": "unique-id",
      "name": "Color",
      "type": "change",
      "actions": [
        {
          "name": "Red Selected",
          "condition": {
            "and": [
              { "resource": "value", "operator": "==", "value": "Red" }
            ]
          },
          "steps": [
            { "method": "setColor", "objectId": "body", "color": "#FF0000" }
          ]
        }
      ]
    }
  ]
}
```

The component raises events using:

```javascript
canvas.raiseInteractionEvent(
  "Color",        // Event name
  "change",       // Action type
  "Color",        // Field name
  "Red",          // Field value
  []              // Key-value pairs
);
```

**Pinning Behavior**

When pinned:

* Component fixes to viewport at 58% left, 18% top
* Maintains position during page scroll
* Useful for long configuration forms

#### Troubleshooting <a href="#troubleshooting" id="troubleshooting"></a>

**Canvas doesn't update:**

* Verify `visualUpdateType` is set correctly
* Check that Product2Id is resolved from configuratorContext
* Ensure scene settings exist on the product record
* Check browser console for error messages

**Attribute changes don't reflect:**

* Verify attribute exists on the product
* Check that picklist values are correctly mapped
* Ensure interaction event names match attribute names in scene settings

**Performance issues:**

* Reduce transaction item processing frequency
* Use `visualUpdateType="transactionItems"` to disable input change monitoring
* Check for large scene settings with many interactions

***

### Revenue Cloud Bulk Generator <a href="#revenue-cloud-bulk-generator" id="revenue-cloud-bulk-generator"></a>

#### Purpose <a href="#purpose-2" id="purpose-2"></a>

The Revenue Cloud Bulk Generator is a standalone tool for generating visual logic across multiple products simultaneously. It's optimized for bulk operations on 100-1000+ products.

#### Use Case <a href="#use-case-2" id="use-case-2"></a>

Use this tool when:

* Deploying visual configuration to an existing product catalog
* Standardizing visual logic across product families
* Migrating products to visual configuration
* Applying common interaction patterns to multiple products

#### Setup Instructions <a href="#setup-instructions-2" id="setup-instructions-2"></a>

**Add as Utility Bar Component (Recommended)**

1. Navigate to **Setup → App Manager**
2. Select your Lightning app (e.g., "Sales Console")
3. Click **Utility Items (Desktop)**
4. Click **Add Utility Item**
5. Configure:
   * **Utility Item**: Lightning Component
   * **Lightning Component API Name**: `RDrawConfig:revenueCloudBulkGenerator`
   * **Label**: "Bulk Visual Logic"
   * **Icon**: `task`
   * **Panel Width**: 600
   * **Panel Height**: 600
6. Click **Save**

**Add to Custom Tab (Alternative)**

1. Navigate to **Setup → Tabs**
2. Click **New** under Lightning Component Tabs
3. Configure:
   * **Lightning Component**: RDrawConfig`:revenueCloudBulkGenerator`
   * **Tab Label**: "Bulk Visual Logic Generator"
   * **Tab Name**: `Bulk_Visual_Logic_Generator`
   * **Tab Style**: Select an icon
4. Click **Save**
5. Add the tab to relevant apps

#### How to Use <a href="#how-to-use-1" id="how-to-use-1"></a>

**Phase 1: Select Products**

1. **Load Products**: Component automatically loads up to 2000 active products
2. **Search**: Filter by product name or code
3. **Filter by Classification**: Select a specific product classification
4. **Select Products**:
   * Check individual product checkboxes
   * Use **Select All** to select all filtered products
   * **Selected Count** shows total selections

**Tips:**

* Use classification filter to process product families together
* Search for specific product codes to target subsets
* Select 10-50 products initially to test your configuration

**Phase 2: Configure Attributes & Components**

The component analyzes selected products to identify common elements.

**Common Attributes Tab**

* Shows attributes present in >50% of selected products
* Select attributes to include in generation
* Use **Select All** / **Deselect All** for bulk selection
* Each attribute shows:
  * Label and description
  * Developer name
  * Occurrence count across products

**Common Components Tab**

* Shows component groups present in >50% of selected products
* Select component groups to include
* Component groups represent ProductComponentGroup records
* Each group may contain multiple child products

**Product-Specific Configuration Tab**

* Shows products with unique attributes not found in others
* These attributes are automatically included
* Informational only - no action required

**Analysis Logic:**

* Threshold: 50% occurrence (e.g., if 10 products selected, attribute must appear in 5+)
* Product-specific attributes below threshold are auto-included per product
* Component groups are matched by `ProductComponentGroup.Name`

**Phase 3: Select Default Actions**

Configure renderer method templates to apply to all generated interactions.

1. Click **Add Renderer Method Template**
2. Select methods from the modal:
   * Camera movements
   * Object transformations
   * Color changes
   * Visibility toggles
   * Custom renderer methods
3. Methods are added as steps to every action in every interaction
4. Remove methods by clicking the delete icon

**Example:** If you add a "Rotate Camera" method:

* Every attribute value change will trigger camera rotation
* Every component selection will trigger camera rotation
* Useful for standardized visual feedback

**Phase 4: Review & Generate**

**Generation Summary**

* Products: Total count of products to process
* Common Attributes: Count of attributes per product
* Common Component Groups: Count of component groups per product
* Renderer Methods: Count of methods per action
* Estimated Time: Calculation based on 5 sec/product + 2 sec/attribute + 2 sec/component

**Generation Process**

1. Click **Start Generation**
2. Monitor progress bar and status
3. View current product being processed
4. Process continues until all products complete

**Progress Indicators:**

* **Progress Bar**: Overall completion percentage
* **Product Index**: "Processing product X of Y"
* **Product Name**: Current product being processed
* **Status Message**: Current operation

**Completion Summary:**

* **Successfully Generated**: Count of products updated
* **Failed**: Count of products with errors
* **Failed Products List**: Product names and error messages

#### Generation Details <a href="#generation-details" id="generation-details"></a>

For each product, the component:

1. **Loads Scene Settings**
   * Retrieves existing scene settings from product record
   * Creates default structure if none exists
2. **Checks for Collisions**
   * Identifies existing interactions with matching names
   * Skips generation for collisions to prevent overwriting
3. **Generates Attribute Interactions**
   * Creates change event for each selected attribute
   * Fetches picklist values if attribute has a picklist
   * Creates action item for each picklist value with condition
4. **Generates Component Interactions**
   * Creates change event for each selected component group
   * Creates checked/unchecked actions for each child product
   * Sets label and value conditions
5. **Applies Renderer Methods**
   * Adds selected renderer method steps to each action
   * Methods execute in order when action condition is met
6. **Saves Scene Settings**
   * Serializes scene settings to JSON
   * Updates product record field via `updateSceneSetup` Apex method

#### Data Caching <a href="#data-caching" id="data-caching"></a>

The component caches data to improve performance:

* **Product Attribute Cache**: Stores attributes per Product2Id
* **Product Component Cache**: Stores components per Product2Id
* **Picklist Value Cache**: Stores picklist values per PicklistId

Caching reduces redundant Apex calls during bulk processing.

#### Error Handling <a href="#error-handling" id="error-handling"></a>

Common errors and solutions:

| Error                           | Cause                                    | Solution                                                                    |
| ------------------------------- | ---------------------------------------- | --------------------------------------------------------------------------- |
| "Could not load scene settings" | Product missing RDraw field relationship | Verify product has scene settings field configured                          |
| "Could not get render context"  | RDraw renderer context not configured    | Check RDraw\_\_RenderContext\_\_c metadata                                  |
| "Insufficient permissions"      | User lacks FLS/CRUD on objects           | Grant read access to Product2, AttributeDefinition, ProductRelatedComponent |
| "No attributes found"           | Product has no attributes                | Add attributes via classification or direct assignment                      |

#### Performance Considerations <a href="#performance-considerations" id="performance-considerations"></a>

**Batch Size Recommendations:**

* **10-50 products**: Interactive testing and configuration refinement
* **50-200 products**: Small-scale deployments
* **200-1000 products**: Large-scale rollouts (monitor governor limits)
* **1000+ products**: Consider breaking into multiple sessions

**Governor Limits:**

* Component runs in user context (not async)
* Stay under Apex CPU time limits (\~10 seconds per transaction)
* 100ms delay between products prevents overwhelming the platform
* Total runtime: \~0.5-2 seconds per product

**Optimization Tips:**

* Process products with similar classifications together
* Pre-load picklist values by running picklist queries before bulk processing
* Run during off-peak hours for large batches
* Monitor debug logs for performance bottlenecks

***

### Apex Helper Class <a href="#apex-helper-class" id="apex-helper-class"></a>

#### UTIL\_ConfigHelper <a href="#util_confighelper" id="util_confighelper"></a>

Located at: `force-app/main/default/classes/UTIL_ConfigHelper.cls`

This Apex class provides utility methods for retrieving product configuration data.

**Key Methods**

**`getProductAttributesForProduct(String product2Id)`**

* Returns all active attributes for a product
* Includes attributes from product classification and direct product attributes
* Cacheable for Lightning components
* Returns: `List<AttributeDefinition>`

**`getPicklistValuesForPicklistIds(List<String> picklistIds)`**

* Batch retrieves picklist values for multiple picklists
* Used by bulk generator for performance
* Returns: `List<AttributePicklistValue>`

**`getPicklistValuesForPicklistId(String Id)`**

* Retrieves picklist values for a single picklist
* Returns: `List<AttributePicklistValue>`

**`getProductRelatedComponentsFromProduct(String productId)`**

* Returns all product components for a parent product
* Includes child product details and component groups
* Returns: `List<ProductRelatedComponent>`

**`getChildProductForRelatedComponentId(String Id)`**

* Retrieves child product details for a component relationship
* Returns: `Product2`

**`getProduct2IdFromQuoteLineItem(String quoteLineItemId)`**

* Extracts Product2Id from a QuoteLineItem
* Used by revenueCloudConfiguration component
* Returns: `String` (Product2Id)

**`getProductsForBulkGeneration(Integer limitRecords, String searchTerm, String classificationId)`**

* Queries active products for bulk operations
* Supports filtering by search term and classification
* Maximum 2000 records
* Cacheable
* Returns: `List<Product2>`

**Security Features**

All methods include:

* **CRUD Checks**: Validates object accessibility
* **FLS Checks**: Validates field-level security
* **USER\_MODE Queries**: Enforces record-level security
* **Input Validation**: Prevents null/invalid parameters
* **Error Handling**: Returns AuraHandledException with clear messages

**Test Coverage**

The class includes comprehensive test support:

* `@TestVisible` annotations on helper methods
* Test-specific query logic
* Mock data handling
* Security permission testing

***

### Best Practices <a href="#best-practices" id="best-practices"></a>

#### General Guidelines <a href="#general-guidelines" id="general-guidelines"></a>

1. **Start Small**: Test on 5-10 products before bulk operations
2. **Backup Scene Settings**: Export existing scene settings before regenerating
3. **Use Classifications**: Organize products by classification for consistent configuration
4. **Document Naming Conventions**: Use consistent names for interaction events and actions
5. **Monitor Performance**: Watch for governor limit warnings in large operations

#### Naming Conventions <a href="#naming-conventions" id="naming-conventions"></a>

**Interaction Event Names:**

* Use attribute DisplayName or DeveloperName
* Use component group name for component interactions
* Examples: "Color", "Size", "Wheels", "Accessories"

**Action Item Names:**

* Descriptive names for conditions
* Examples: "Red Selected", "Large Size", "Sport Package Added"

**Renderer Method Names:**

* Match method names in RDraw renderer
* Examples: "setColor", "toggleVisibility", "rotateObject", "moveCamera"

#### Security Considerations <a href="#security-considerations" id="security-considerations"></a>

1. **User Permissions**: Ensure users have:
   * Read on Product2, AttributeDefinition, ProductRelatedComponent
   * Edit on Product2 (for updating scene settings)
   * Access to RDraw custom objects
2. **Sharing Rules**: Verify product records are visible to configuration users
3. **Field-Level Security**: Grant access to:
   * `RDraw__X3DSceneSettings__c`
   * `RDraw__2DSceneSettings__c`
   * Product2 custom fields referenced in configurations

#### Maintenance <a href="#maintenance" id="maintenance"></a>

**Regular Tasks:**

* Review and clean up unused interaction events
* Update renderer methods when RDraw versions change
* Refresh bulk generation when new products are added
* Monitor error logs for configuration issues

**Version Control:**

* Track scene settings in source control as custom metadata
* Document renderer method libraries
* Maintain changelog for configuration updates

***

### Troubleshooting <a href="#troubleshooting-1" id="troubleshooting-1"></a>

#### Common Issues <a href="#common-issues" id="common-issues"></a>

**Quick Action doesn't appear:**

* Verify action is added to page layout
* Check user profile has access to Lightning Components
* Ensure RDraw namespace is installed

**Flow component shows blank canvas:**

* Verify configuratorContext is wired correctly
* Check that Product2Id is resolved
* Ensure scene settings exist on product
* Verify user has read access to scene settings field

**Bulk generation fails:**

* Check for governor limit exceptions in debug logs
* Reduce batch size
* Verify all products have required field relationships
* Ensure user has edit permissions on Product2

**Visual updates don't trigger:**

* Verify interaction event names match scene settings
* Check attribute/component names match exactly
* Review console logs for change detection
* Ensure canvas is fully loaded before changes

#### Debug Tips <a href="#debug-tips" id="debug-tips"></a>

1. **Enable Debug Mode**: Set `debug = true` in visualLogicGenerator
2. **Monitor Console**: Check browser console for detailed logs
3. **Review Notifications**: Watch component notification messages
4. **Check Apex Logs**: Review Apex logs for server-side errors
5. **Validate Scene Settings**: Export and validate JSON structure

***

### Support <a href="#support" id="support"></a>

For issues, questions, or feature requests:

1. Check debug logs and browser console
2. Verify all prerequisites and permissions
3. Test with simplified configuration
4. Contact your Salesforce administrator or implementation partner

***

### Appendix <a href="#appendix" id="appendix"></a>

#### Required Salesforce Objects <a href="#required-salesforce-objects" id="required-salesforce-objects"></a>

* Product2
* AttributeDefinition
* AttributePicklistValue
* ProductRelatedComponent
* ProductComponentGroup
* ProductClassificationAttr
* QuoteLineItem (for flow integration)

#### Required RDraw Objects (Namespace: RDraw) <a href="#required-rdraw-objects-namespace-rdraw" id="required-rdraw-objects-namespace-rdraw"></a>

* RDraw\_\_RenderContext\_\_c
* RDraw\_\_X3DSceneSettings\_\_c
* RDraw\_\_2DSceneSettings\_\_c
* RDraw\_\_RendererMethodTemplate\_\_c

#### Required Permissions <a href="#required-permissions" id="required-permissions"></a>

**Object Permissions:**

* Read: All listed objects above
* Edit: Product2 (for scene settings updates)

**System Permissions:**

* View Setup and Configuration (for admins)
* Customize Application (for admins)

#### Change Log <a href="#change-log" id="change-log"></a>

| Version | Date | Changes         |
| ------- | ---- | --------------- |
| 1.0     | 2024 | Initial release |

***
