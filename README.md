# Example Button Theme

A minimal Home Assistant theme that focuses only on styling modal confirmation buttons while preserving all other UI elements from your current theme.

## Features

- **Ultra-Targeted**: ONLY modifies card tap_action confirmation modal buttons  
- **Complete Theme Preservation**: Inherits ALL existing theme variables
- **Visual Clarity**: Green confirm buttons, red cancel buttons for better UX
- **Bigger Buttons**: 48px height, larger padding, occupy more modal space
- **Zero Side Effects**: Doesn't touch sidebar, cards, or any other UI elements

## Button Styling

- **Confirm/OK Buttons**: Green (`#4CAF50`) with white text, 48px height
- **Cancel/Close Buttons**: Red (`#f44336`) with white text, 48px height  
- **Enhanced Size**: Bigger buttons with more padding for easier interaction
- **Better Layout**: Buttons take up approximately half the modal width each
- **Card Actions Only**: Specifically targets `tap_action: confirmation:` modals

## Installation

### Method 1: Via HACS (Recommended)

1. Install HACS if not already installed
2. Go to HACS → Frontend → ⋮ → Custom repositories  
3. Add this URL: `https://github.com/jo4santos/hass-repo-theme`
4. Select category: Theme → Add → Install
5. **Download the CSS file**: Save `button-modal-styling.css` to `/config/www/`
6. **Add CSS resource**: Go to Settings → Dashboards → Resources → Add Resource:
   - **URL**: `/local/button-modal-styling.css`
   - **Resource Type**: Stylesheet
7. Restart Home Assistant
8. Go to Profile → Theme → Select "Example Button Theme"

### Method 2: Manual Installation

1. Download both `example_button_theme.yaml` and `button-modal-styling.css`
2. Copy theme file to `/config/themes/example_button_theme.yaml`
3. Copy CSS file to `/config/www/button-modal-styling.css`
4. Add to your `configuration.yaml`:

```yaml
frontend:
  themes: !include_dir_merge_named themes
```

5. **Add CSS resource**: Settings → Dashboards → Resources → Add:
   - **URL**: `/local/button-modal-styling.css`  
   - **Resource Type**: Stylesheet
6. Restart Home Assistant
7. Go to Profile → Theme → Select "Example Button Theme"

### Method 3: Via File Editor Add-on

1. Install the File Editor add-on if not already installed
2. Navigate to `/config/themes/`
3. Create `example_button_theme.yaml` and paste the theme content
4. Add the frontend configuration to `configuration.yaml`
5. Restart Home Assistant

## Configuration

Add this to your `configuration.yaml`:

```yaml
frontend:
  themes: !include_dir_merge_named themes
```

Or if you already have themes configured, just restart Home Assistant.

## Usage

1. **Apply Theme**: Profile → Theme → "Example Button Theme"
2. **Test**: Open any modal dialog (delete entity, restart HA, etc.)
3. **Observe**: Confirm buttons will be green, cancel buttons red

## Target Usage

This theme is specifically designed for card configurations like:

```yaml
type: entity
entity: light.living_room
tap_action:
  action: toggle
  confirmation:
    text: "Are you sure you want to toggle the light?"
```

### Targeted HTML Structure

The theme targets this specific modal structure:
```html
<ha-md-dialog type="alert">
  <div slot="actions">
    <ha-button appearance="plain">Cancelar</ha-button>
    <ha-button appearance="accent">OK</ha-button>
  </div>
</ha-md-dialog>
```

### Results

The confirmation modal that appears will have:
- ✅ **Green "OK" button** (48px height, enhanced padding)
- ❌ **Red "Cancel" button** (48px height, enhanced padding)  
- 📏 **Bigger layout** - buttons occupy ~45% modal width each
- 🎯 **Perfect targeting** - only affects `ha-md-dialog[type="alert"]` modals

## Compatibility

- **Home Assistant Core**: 2023.1+  
- **All Themes**: Works as an overlay on any existing theme
- **Target**: Card `tap_action` confirmation modals specifically
- **Zero Conflicts**: Preserves all other UI styling completely

## Customization

To modify button colors, edit the theme file:

```yaml
Example Button Theme:
  mdc-theme-primary: "#your-confirm-color"      # Confirm button color
  mdc-theme-secondary: "#your-cancel-color"     # Cancel button color
```

Common color options:
- **Green Confirm**: `#4CAF50`, `#2E7D32`, `#66BB6A`
- **Red Cancel**: `#f44336`, `#D32F2F`, `#EF5350`
- **Blue Confirm**: `#2196F3`, `#1976D2`, `#42A5F5`

## Examples

### Modal Dialogs Affected
- Entity deletion confirmations
- Restart/reload confirmations  
- Configuration save dialogs
- Automation/script execution confirmations
- Add-on installation/removal dialogs

### Visual Impact
- ✅ **Before**: Generic blue buttons
- ✅ **After**: Green confirm + red cancel for clarity

## Reverting

To remove the theme:
1. Go to Profile → Theme → Select your previous theme
2. Or select "Auto" to use Home Assistant default

## Support

This is an example theme for demonstration purposes. For issues or customizations, visit the [repository](https://github.com/jo4santos/hass-repo).