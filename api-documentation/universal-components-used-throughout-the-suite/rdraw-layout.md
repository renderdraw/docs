# RDraw-layout

## Layout Component Documentation

### Overview

The `layout` component is a flexible, responsive Lightning Web Component that provides a grid-based layout system for Salesforce applications. It supports multiple content areas including context panels, sidebars, main content, and action information panes with configurable sizing and responsive behavior.

### Features

* **Responsive Grid System**: Uses Salesforce Lightning Design System (SLDS) grid for consistent responsive behavior
* **Multiple Content Areas**: Supports context panels, sidebars, main content, and action information panes
* **Dynamic Sizing**: Automatically calculates content area sizes based on visible panels
* **Context Details**: Expandable context details with navigation controls
* **Flexible Configuration**: Customizable panel sizes and display options
* **Smooth Animations**: CSS transitions and animations for panel show/hide operations

### Component Structure

```
┌─────────────────────────────────────────────────────────────┐
│                    Advanced Body                            │
├──────────────┬─────────────────────────┬──────────────────┤
│   Context    │      Main Content       │     Sidebar      │
│   Panel      │  ┌─────────────────────┐ │     Panel        │
│              │  │ Action Info Pane    │ │                  │
│              │  └─────────────────────┘ │                  │
│              │  ┌─────────────────────┐ │                  │
│              │  │   Render Wrapper    │ │                  │
│              │  │   (Main Content)    │ │                  │
│              │  └─────────────────────┘ │                  │
└──────────────┴─────────────────────────┴──────────────────┘
```

### API Reference

#### Public Properties

| Property                       | Type    | Default   | Description                             |
| ------------------------------ | ------- | --------- | --------------------------------------- |
| `sidebarContent`               | Boolean | `false`   | Controls sidebar content display        |
| `contextDetailHeaderText`      | String  | `''`      | Header text for context details panel   |
| `displaySidebar`               | Boolean | `false`   | Shows/hides the sidebar panel           |
| `displayActionInformationPane` | Boolean | `false`   | Shows/hides the action information pane |
| `size`                         | String  | `'Large'` | Sets the overall size of the layout     |
| `displayContext`               | Boolean | `false`   | Shows/hides the context panel           |
| `displayContextDetails`        | Boolean | `false`   | Shows/hides the context details view    |
| `mainContentSize`              | Number  | `12`      | Grid size for main content (1-12)       |
| `contextSize`                  | Number  | `3`       | Grid size for context panel (1-12)      |
| `sidebarSize`                  | Number  | `4`       | Grid size for sidebar panel (1-12)      |

#### Size Options

The `size` property accepts the following values:

* `'Small'` - 25vh height
* `'SmallPlus'` - 35vh height
* `'Medium'` - 50vh height
* `'MediumPlus'` - 60vh height
* `'Large'` - 70vh height (default)
* `'LargePlus'` - 85vh height
* `'Jumbo'` - 100vh height
* `'Stretch'` - 100% height

#### Slots

| Slot Name               | Description                             |
| ----------------------- | --------------------------------------- |
| `contextContent`        | Content for the context panel           |
| `contextDetailContent`  | Content for the context details view    |
| `actionInformationPane` | Content for the action information area |
| `mainContent`           | Primary content area                    |
| `sidebarContent`        | Content for the sidebar panel           |

#### Events

| Event Name            | Description                                | Event Detail |
| --------------------- | ------------------------------------------ | ------------ |
| `contextdetailsclose` | Fired when context details panel is closed | None         |

#### Public Methods

| Method                        | Description                                                         |
| ----------------------------- | ------------------------------------------------------------------- |
| `resetContentSize()`          | Recalculates and updates content area sizes based on visible panels |
| `handleCloseContextDetails()` | Closes the context details panel and fires the close event          |

### Usage Examples

#### Basic Layout with Main Content

```html
<c-layout>
    <div slot="mainContent">
        <h1>Main Content Area</h1>
        <p>Your primary content goes here.</p>
    </div>
</c-layout>
```

#### Layout with Sidebar

```html
<c-layout display-sidebar="true" sidebar-size="3">
    <div slot="mainContent">
        <h1>Main Content with Sidebar</h1>
    </div>
    <div slot="sidebarContent">
        <h2>Sidebar</h2>
        <ul>
            <li>Navigation Item 1</li>
            <li>Navigation Item 2</li>
        </ul>
    </div>
</c-layout>
```

#### Full Layout with All Panels

```html
<c-layout 
    display-sidebar="true"
    display-context="true"
    display-action-information-pane="true"
    size="Large"
    context-size="3"
    sidebar-size="4">
    
    <div slot="contextContent">
        <h2>Context Panel</h2>
        <p>Contextual information and controls</p>
        <lightning-button label="Show Details" onclick={showContextDetails}></lightning-button>
    </div>
    
    <div slot="actionInformationPane">
        <lightning-card title="Action Information">
            <p>Important action-related information</p>
        </lightning-card>
    </div>
    
    <div slot="mainContent">
        <lightning-card title="Main Application">
            <p>Primary application content</p>
        </lightning-card>
    </div>
    
    <div slot="sidebarContent">
        <lightning-card title="Tools">
            <lightning-button-group>
                <lightning-button label="Tool 1"></lightning-button>
                <lightning-button label="Tool 2"></lightning-button>
            </lightning-button-group>
        </lightning-card>
    </div>
</c-layout>
```

#### Dynamic Context Details

```html
<c-layout 
    display-context="true"
    display-context-details={showDetails}
    context-detail-header-text="Detailed View"
    oncontextdetailsclose={handleDetailsClose}>
    
    <div slot="contextContent">
        <h2>Context Menu</h2>
        <lightning-button label="View Details" onclick={showDetails}></lightning-button>
    </div>
    
    <div slot="contextDetailContent">
        <lightning-card title="Detailed Information">
            <p>Detailed context information goes here</p>
            <lightning-button label="Edit" variant="brand"></lightning-button>
        </lightning-card>
    </div>
    
    <div slot="mainContent">
        <h1>Main Content</h1>
    </div>
</c-layout>
```

### JavaScript Controller Examples

#### Basic Controller Setup

```javascript
import { LightningElement, track } from 'lwc';

export default class MyComponent extends LightningElement {
    @track showSidebar = false;
    @track showContext = false;
    @track showContextDetails = false;
    @track layoutSize = 'Large';
    
    handleToggleSidebar() {
        this.showSidebar = !this.showSidebar;
    }
    
    handleShowContextDetails() {
        this.showContextDetails = true;
    }
    
    handleDetailsClose() {
        this.showContextDetails = false;
    }
    
    handleSizeChange(event) {
        this.layoutSize = event.target.value;
    }
}
```

#### Advanced Controller with Dynamic Sizing

```javascript
import { LightningElement, track, api } from 'lwc';

export default class AdvancedLayoutExample extends LightningElement {
    @track layoutConfig = {
        showSidebar: false,
        showContext: false,
        showActionPane: false,
        size: 'Large',
        contextSize: 3,
        sidebarSize: 4
    };
    
    @api
    togglePanel(panelName) {
        switch(panelName) {
            case 'sidebar':
                this.layoutConfig.showSidebar = !this.layoutConfig.showSidebar;
                break;
            case 'context':
                this.layoutConfig.showContext = !this.layoutConfig.showContext;
                break;
            case 'actionPane':
                this.layoutConfig.showActionPane = !this.layoutConfig.showActionPane;
                break;
        }
        // Trigger reactivity
        this.layoutConfig = { ...this.layoutConfig };
    }
    
    handlePanelResize(panelName, newSize) {
        if (panelName === 'context') {
            this.layoutConfig.contextSize = newSize;
        } else if (panelName === 'sidebar') {
            this.layoutConfig.sidebarSize = newSize;
        }
        this.layoutConfig = { ...this.layoutConfig };
    }
    
    get contextSize() {
        return this.layoutConfig.contextSize;
    }
    
    get sidebarSize() {
        return this.layoutConfig.sidebarSize;
    }
}
```

### Responsive Behavior

The layout component automatically adjusts content areas based on:

1. **Available Panels**: Main content size decreases as panels are shown
2. **Panel Sizes**: Custom sizes for context and sidebar panels
3. **Screen Size**: Uses SLDS responsive grid classes
4. **Content Flow**: Flexbox layout ensures proper content distribution

#### Size Calculations

* **Base Size**: 12 grid columns
* **With Context**: Main content = 12 - contextSize
* **With Sidebar**: Main content = 12 - sidebarSize
* **With Both**: Main content = 12 - contextSize - sidebarSize

### Best Practices

1. **Size Configuration**: Choose appropriate sizes based on content needs
2. **Responsive Design**: Test with different screen sizes and panel combinations
3. **Content Organization**: Use slots appropriately for different content types
4. **Performance**: Avoid frequent size changes that trigger recalculations
5. **Accessibility**: Ensure proper focus management when panels open/close

### Common Use Cases

1. **Dashboard Layout**: Main dashboard with sidebar navigation and context filters
2. **Detail Pages**: Record details with related information panels
3. **Workflow Applications**: Multi-step processes with contextual guidance
4. **Data Visualization**: Charts with filtering options and detail panels
5. **Form Layouts**: Complex forms with help text and validation information
