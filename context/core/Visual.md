# LiquidGlassKit Visual Design Context

**Purpose**: Complete visual design system and UI specifications  
**Version**: 1.1  
**Design Language**: WWDC25 Liquid Glassmorphism  
**Last Updated**: July 31, 2025

## Visual Hierarchy
```
Z-LAYERS (back→front):
├─[0] Background (Color.black.opacity(0.9) or system)
├─[1] Glass Base (.thinMaterial or .ultraThinMaterial)
├─[2] Glass Tint (Color.white.opacity(0.1))
├─[3] Glass Border (Color.white.opacity(0.05))
├─[4] Glass Overlay (Color.white.opacity(0.05))
├─[5] Content Layer (text, icons, controls)
├─[6] Shadow Effects (Color.black.opacity(0.1), radius: 4)
└─[7] Animation Layer (hover glows, transitions)
```

## Material Specifications

### Glass Material Stack
```yaml
standard_glass:
  base: ".thinMaterial"
  tint: "Color.white.opacity(0.1)"
  border: "Color.white.opacity(0.05)"
  overlay: "Color.white.opacity(0.05)"
  shadow: "color: .black.opacity(0.1), radius: 4, y: 2"

elevated_glass:
  base: ".regularMaterial"
  tint: "Color.white.opacity(0.15)"
  border: "Color.white.opacity(0.1)"
  overlay: "Color.white.opacity(0.08)"
  shadow: "color: .black.opacity(0.15), radius: 8, y: 4"

subtle_glass:
  base: ".ultraThinMaterial"
  tint: "Color.white.opacity(0.05)"
  border: "Color.white.opacity(0.03)"
  overlay: "none"
  shadow: "color: .black.opacity(0.05), radius: 2, y: 1"
```

### Opacity Reference Table
| Element | Base | Hover | Active | Disabled |
|---------|------|-------|--------|----------|
| **Glass Tint** | 0.1 | 0.15 | 0.2 | 0.05 |
| **Glass Border** | 0.05 | 0.1 | 0.15 | 0.02 |
| **Glass Overlay** | 0.05 | 0.08 | 0.1 | 0.02 |
| **Text on Glass** | 1.0 | 1.0 | 1.0 | 0.5 |
| **Icons on Glass** | 0.9 | 1.0 | 1.0 | 0.4 |

## Color System

### Primary Palette
```yaml
glass_colors:
  primary: 
    hex: "#007AFF"
    rgb: "0, 122, 255"
    usage: "Primary actions, selected states"
    
  secondary:
    hex: "#5856D6"
    rgb: "88, 86, 214"
    usage: "Secondary actions, accents"
    
  tertiary:
    hex: "#AF52DE"
    rgb: "175, 82, 222"
    usage: "Special highlights, premium features"
    
  success:
    hex: "#34C759"
    rgb: "52, 199, 89"
    usage: "Positive states, confirmations"
    
  warning:
    hex: "#FF9500"
    rgb: "255, 149, 0"
    usage: "Warnings, important notices"
    
  error:
    hex: "#FF3B30"
    rgb: "255, 59, 48"
    usage: "Errors, destructive actions"
    
  accent:
    hex: "#FF2D92"
    rgb: "255, 45, 146"
    usage: "Special accents, notifications"
```

### Glass-Specific Tints
```yaml
glass_tints:
  white_tints:
    glassTint: "rgba(255, 255, 255, 0.1)"
    glassBorder: "rgba(255, 255, 255, 0.05)"
    glassOverlay: "rgba(255, 255, 255, 0.05)"
    glassHighlight: "rgba(255, 255, 255, 0.35)"
    
  color_tints:
    primary: "rgba(0, 122, 255, 0.1)"
    success: "rgba(52, 199, 89, 0.1)"
    error: "rgba(255, 59, 48, 0.1)"
    warning: "rgba(255, 149, 0, 0.1)"
```

## Typography System

### Type Scale
```yaml
glass_typography:
  largeTitle:
    size: "34pt"
    weight: ".bold"
    lineHeight: "41pt"
    tracking: "0.374pt"
    
  title:
    size: "28pt"
    weight: ".bold"
    lineHeight: "34pt"
    tracking: "0.364pt"
    
  title2:
    size: "22pt"
    weight: ".bold"
    lineHeight: "28pt"
    tracking: "0.352pt"
    
  title3:
    size: "20pt"
    weight: ".semibold"
    lineHeight: "25pt"
    tracking: "0.38pt"
    
  headline:
    size: "17pt"
    weight: ".semibold"
    lineHeight: "22pt"
    tracking: "-0.408pt"
    
  body:
    size: "17pt"
    weight: ".regular"
    lineHeight: "22pt"
    tracking: "-0.408pt"
    
  callout:
    size: "16pt"
    weight: ".regular"
    lineHeight: "21pt"
    tracking: "-0.32pt"
    
  subheadline:
    size: "15pt"
    weight: ".regular"
    lineHeight: "20pt"
    tracking: "-0.24pt"
    
  footnote:
    size: "13pt"
    weight: ".regular"
    lineHeight: "18pt"
    tracking: "-0.078pt"
    
  caption:
    size: "12pt"
    weight: ".regular"
    lineHeight: "16pt"
    tracking: "0pt"
    
  caption2:
    size: "11pt"
    weight: ".regular"
    lineHeight: "13pt"
    tracking: "0.066pt"
```

### Text on Glass Rules
- **Contrast**: Minimum 7:1 for body text
- **Weight**: Increase by one level on glass
- **Shadow**: Subtle text shadow for legibility
- **Color**: Pure white or high contrast colors only

## Spacing & Layout

### Spacing Tokens
```yaml
glass_constants:
  # Micro spacing
  spacing_2: "2pt"    # Hairline gaps
  spacing_4: "4pt"    # Tight grouping
  
  # Component spacing
  spacing_8: "8pt"    # itemSpacing - between related elements
  spacing_12: "12pt"  # itemPadding - internal component padding
  spacing_16: "16pt"  # cardPadding - card content padding
  spacing_20: "20pt"  # Extended card padding
  spacing_24: "24pt"  # sectionSpacing - between sections
  
  # Layout spacing
  spacing_32: "32pt"  # Major section gaps
  spacing_48: "48pt"  # Page margins (desktop)
  spacing_64: "64pt"  # Hero sections
```

### Corner Radius System
```yaml
radius_tokens:
  small: "8pt"     # Buttons, badges
  medium: "12pt"   # Cards, panels (standard)
  large: "16pt"    # Modals, sheets
  xlarge: "20pt"   # Hero cards
  round: "50%"     # Circular elements
```

### Grid System
```yaml
adaptive_grid:
  compact:
    columns: 1
    margin: "16pt"
    gutter: "16pt"
    
  regular:
    columns: "2-3"
    margin: "24pt"
    gutter: "20pt"
    
  desktop:
    columns: "3-4"
    margin: "32pt"
    gutter: "24pt"
```

## Animation Specifications

### Core Animation Presets
```yaml
liquid_animations:
  # Appearance animations
  glass_appear:
    duration: "600ms"
    curve: "spring(response: 0.6, dampingFraction: 0.8)"
    properties: ["opacity: 0→1", "scale: 0.9→1", "blur: 10→0"]
    
  glass_disappear:
    duration: "400ms"
    curve: "easeIn"
    properties: ["opacity: 1→0", "scale: 1→0.9", "blur: 0→10"]
    
  # Interaction animations
  hover_feedback:
    duration: "200ms"
    curve: "easeOut"
    properties: ["scale: 1→1.02", "shadow: increase", "tint: +0.05 opacity"]
    
  press_feedback:
    duration: "100ms"
    curve: "easeOut"
    properties: ["scale: 1→0.98", "brightness: -10%"]
    
  # State transitions
  status_change:
    duration: "800ms"
    curve: "spring(stiffness: 300, damping: 30)"
    properties: ["color transition", "glow pulse", "icon rotation"]
    
  # Navigation
  navigation_transition:
    duration: "500ms"
    curve: "interpolatingSpring(stiffness: 300, damping: 30)"
    properties: ["slide", "fade", "blur transition"]
    
  # Liquid effects
  liquid_morph:
    duration: "1000ms"
    curve: "timingCurve(0.4, 0.0, 0.2, 1.0)"
    properties: ["shape morph", "color flow", "opacity wave"]
```

### Animation Timing Reference
| Animation Type | Duration | Use Case |
|----------------|----------|----------|
| **Micro** | 100-200ms | Hover, tap feedback |
| **Short** | 200-400ms | State changes, toggles |
| **Medium** | 400-600ms | Card appearances, transitions |
| **Long** | 600-1000ms | Complex morphs, page transitions |

## Glass Effect Specifications

### Standard Glass Card
```swift
// Visual implementation
ZStack {
    // Base glass
    RoundedRectangle(cornerRadius: 12)
        .fill(.thinMaterial)
    
    // Tint layer
    RoundedRectangle(cornerRadius: 12)
        .fill(LinearGradient(
            colors: [
                Color.white.opacity(0.1),
                Color.white.opacity(0.05)
            ],
            startPoint: .topLeading,
            endPoint: .bottomTrailing
        ))
    
    // Border
    RoundedRectangle(cornerRadius: 12)
        .stroke(
            LinearGradient(
                colors: [
                    Color.white.opacity(0.1),
                    Color.white.opacity(0.05)
                ],
                startPoint: .topLeading,
                endPoint: .bottomTrailing
            ),
            lineWidth: 1
        )
}
.shadow(color: .black.opacity(0.1), radius: 4, x: 0, y: 2)
```

### Platform-Specific Enhancements

#### macOS Hover Effects
```yaml
hover_state:
  scale: "1.02"
  shadow: "radius: 8, opacity: 0.15"
  glow: "Color.white.opacity(0.1), radius: 10"
  duration: "200ms easeOut"
  cursor: "pointingHand"
```

#### iOS Touch Feedback
```yaml
touch_state:
  scale: "0.98"
  opacity: "0.8"
  haptic: "light impact"
  duration: "100ms easeOut"
```

## Icon Guidelines

### SF Symbol Configuration
```yaml
icon_specifications:
  sizes:
    small: 
      pointSize: "16"
      weight: ".medium"
      scale: ".medium"
    medium:
      pointSize: "20"
      weight: ".medium"  
      scale: ".medium"
    large:
      pointSize: "28"
      weight: ".semibold"
      scale: ".large"
      
  rendering:
    mode: "hierarchical"
    primary_color: "from context"
    secondary_opacity: "0.8"
    tertiary_opacity: "0.6"
    
  common_icons:
    dashboard: "square.grid.2x2"
    status: "circle.fill"
    metric: "chart.line.uptrend.xyaxis"
    action: "arrow.right.circle"
    progress: "circle.lefthalf.filled"
    settings: "gear"
    close: "xmark"
    success: "checkmark.circle"
    error: "exclamationmark.circle"
    warning: "exclamationmark.triangle"
```

## Component Visual Specifications

### Glass Action Button
```yaml
visual_spec:
  height: "44pt minimum"
  padding: "horizontal: 16pt, vertical: 10pt"
  
  states:
    normal:
      background: ".ultraThinMaterial"
      tint: "Color.white.opacity(0.05)"
      border: "Color.white.opacity(0.1)"
      
    hover:
      background: ".thinMaterial"
      tint: "Color.white.opacity(0.1)"
      border: "Color.white.opacity(0.15)"
      scale: "1.02"
      
    pressed:
      scale: "0.98"
      opacity: "0.8"
      
    disabled:
      opacity: "0.4"
      interaction: "disabled"
```

### Modern Status Card
```yaml
visual_spec:
  dimensions:
    minHeight: "120pt"
    padding: "20pt"
    cornerRadius: "12pt"
    
  layout:
    icon: "top-left, 28pt"
    title: "17pt semibold"
    subtitle: "15pt regular, 0.8 opacity"
    status: "top-right, 8pt indicator"
    
  glass_layers:
    1_base: ".thinMaterial"
    2_gradient: "diagonal white 0.1→0.05"
    3_border: "white 0.05, 1pt"
    4_shadow: "black 0.1, radius 4"
```

### Progress Indicators
```yaml
circular_progress:
  size: "60pt"
  stroke_width: "4pt"
  background: "Color.white.opacity(0.1)"
  foreground: "accent color"
  animation: "continuous rotation for indeterminate"
  
segmented_progress:
  height: "8pt"
  segment_gap: "2pt"
  inactive: "Color.white.opacity(0.1)"
  active: "accent color with glow"
  animation: "liquid fill transition"
```

## Accessibility Visual Guidelines

### Contrast Requirements
```yaml
wcag_compliance:
  text_on_glass:
    normal: "7:1 minimum"
    large_text: "4.5:1 minimum"
    
  interactive_elements:
    normal: "4.5:1 minimum"
    hover: "maintain or increase contrast"
    
  status_indicators:
    color_blind_safe: true
    secondary_indicator: "shape or icon"
```

### Focus Indicators
```yaml
focus_state:
  outline: "3pt"
  color: "system accent"
  offset: "2pt"
  shape: "follows component shape"
  animation: "subtle pulse"
```

### Motion Preferences
```yaml
reduced_motion:
  animations: "instant transitions"
  hover_effects: "opacity only"
  progress_indicators: "static display"
  liquid_effects: "disabled"
```

## Dark Mode Adaptations

### Material Adjustments
```yaml
dark_mode:
  glass_base: ".ultraThinMaterial"
  tint_opacity: "reduce by 50%"
  border_opacity: "increase by 50%"
  shadow: "less prominent"
  
  color_adjustments:
    increase_vibrancy: true
    boost_contrast: true
```

## Visual Quality Checklist

### Glass Effect Quality
- [ ] All glass layers properly stacked
- [ ] Opacity values precisely matched
- [ ] Borders subtle but visible
- [ ] Shadows provide depth without heaviness

### Animation Quality  
- [ ] All animations 60 FPS
- [ ] Spring animations feel natural
- [ ] No jarring transitions
- [ ] Platform-specific optimizations applied

### Consistency
- [ ] All components use design tokens
- [ ] Spacing consistent throughout
- [ ] Typography hierarchy clear
- [ ] Color usage semantic

This comprehensive visual design specification ensures LiquidGlassKit maintains the highest quality glassmorphism effects while providing clear implementation guidelines for all visual aspects.