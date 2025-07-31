# LiquidGlassKit Navigation Context

**Purpose**: Screen flow, user journeys, and state management  
**Version**: 1.1  
**Navigation Pattern**: Tahoe Navigator with Glass Polish  
**Last Updated**: July 31, 2025

## Navigation State Machine
```
┌─────────────────┐
│   App Launch    │
└────────┬────────┘
         │ Animation: Glass appear (600ms)
         ▼
┌─────────────────┐     Navigation State
│ Tahoe Navigator │     ┌──────────────┐
│  (Idle State)   │────▶│   Loading    │
└────────┬────────┘     └──────┬───────┘
         │                      │ Data ready
         ▼                      ▼
┌─────────────────┐     ┌──────────────┐
│   Dashboard     │────▶│    Active    │
│  (Default View) │     └──────┬───────┘
└─────────────────┘            │ Selection change
         │                      ▼
         │              ┌──────────────┐
         └─────────────▶│ Transitioning│
                        └──────────────┘
                               │ Complete
                               ▼
                        ┌──────────────┐
                        │     Idle     │
                        └──────────────┘
```

## Screen Hierarchy
```
GlassSystemNavigator (Root Container)
├── Dashboard [Default]
│   ├── Overview Section
│   │   ├── Status Cards Grid
│   │   ├── Metric Cards Grid
│   │   └── Activity Chart (Placeholder)
│   │
│   ├── Quick Actions Section
│   │   ├── Primary Action Cards
│   │   └── Secondary Actions
│   │
│   └── Progress Tracking Section
│       └── Phase Progress Cards
│
├── Components Library [Organized View]
│   ├── Foundation
│   │   ├── Colors Gallery
│   │   ├── Typography Showcase
│   │   ├── Constants Reference
│   │   └── Status/Trends Demo
│   │
│   ├── Atomic Preview
│   │   ├── Effects Playground
│   │   ├── Materials Gallery
│   │   ├── Layout Components
│   │   ├── Typography Examples
│   │   └── Basic Components
│   │
│   ├── Molecular Preview
│   │   ├── Button Variants
│   │   ├── Card Headers
│   │   ├── Content Sections
│   │   └── Progress Components
│   │
│   └── Organism Preview
│       ├── Status Cards
│       ├── Metric Cards
│       ├── Action Cards
│       └── Progress Cards
│
└── About & Documentation
    ├── Framework Info
    ├── Integration Guide
    ├── Version History
    └── Credits
```

## User Journey Flows

### Primary Flow: Component Discovery
```
START 
  ↓ (Launch app)
Dashboard View 
  ↓ (Tap Components in nav)
Components Library [300ms slide]
  ↓ (Select category)
Category Preview [200ms push]
  ↓ (Tap component)
Component Detail [Inline expand]
  ↓ (View code example)
Code Preview [Modal presentation]
  ↓ (Copy code)
END → Return to library
```

### Integration Flow: New Developer
```
START
  ↓ (Launch from Xcode)
Dashboard View
  ↓ (Tap About)
Documentation [300ms transition]
  ↓ (Read integration guide)
Copy Import Statement
  ↓ (View examples)
Components Library
  ↓ (Test components)
Interactive Preview
  ↓ (Implement in app)
END
```

### Exploration Flow: Designer Review
```
START
  ↓ (Open framework)
Dashboard Overview
  ↓ (Review cards)
Visual Inspection [Hover effects on macOS]
  ↓ (Navigate to components)
Component Gallery
  ↓ (Test interactions)
State Previews [All states visible]
  ↓ (Check animations)
Animation Playground
END
```

## Navigation Components Detail

### GlassSystemNavigator
```swift
// Core navigation container
struct GlassSystemNavigator: View {
    @State private var selectedPage: Page = .dashboard
    @State private var navigationPath = NavigationPath()
    @State private var columnVisibility: NavigationSplitViewVisibility = .automatic
    
    // Platform-adaptive layout
    var body: some View {
        #if os(macOS)
        // Desktop: Always visible sidebar
        NavigationSplitView(columnVisibility: $columnVisibility) {
            GlassSidebar(selection: $selectedPage)
                .navigationSplitViewColumnWidth(
                    min: 200,
                    ideal: 250,
                    max: 300
                )
        } detail: {
            DetailView(page: selectedPage)
                .glassNavigationTransition()
        }
        .glassNavigatorStyling()
        
        #else
        // iOS: Adaptive navigation
        if horizontalSizeClass == .regular {
            // iPad: Collapsible sidebar
            NavigationSplitView { ... }
        } else {
            // iPhone: Tab bar
            TabView(selection: $selectedPage) { ... }
        }
        #endif
    }
}
```

### GlassSystemNavigator+Polish
```swift
// Platform-specific enhancements
extension GlassSystemNavigator {
    // macOS hover effects
    func glassNavigatorStyling() -> some View {
        self
            .if(ProcessInfo.processInfo.isMacCatalystApp) { view in
                view
                    .hoverEffectOnMac()
                    .glassNavigationCursor()
            }
    }
    
    // Smooth transitions
    func glassNavigationTransition() -> some View {
        self.transition(
            .asymmetric(
                insertion: .move(edge: .trailing)
                    .combined(with: .opacity),
                removal: .move(edge: .leading)
                    .combined(with: .opacity)
            )
        )
        .animation(.spring(response: 0.5, dampingFraction: 0.8))
    }
}
```

## Navigation State Management

### State Architecture
```yaml
navigation_state:
  selected_page:
    type: "Page enumeration"
    default: ".dashboard"
    persistence: "none (fresh each launch)"
    
  navigation_path:
    type: "NavigationPath"
    purpose: "Deep navigation stack"
    max_depth: 3
    
  component_selection:
    type: "String?"
    purpose: "Selected component ID"
    animation: "withAnimation(.spring)"
    
  preview_mode:
    type: "PreviewMode"
    options: ["interactive", "static", "code"]
    default: ".interactive"
```

### State Transitions
```swift
// Page selection with glass animation
func selectPage(_ page: Page) {
    withAnimation(.spring(response: 0.5, dampingFraction: 0.8)) {
        selectedPage = page
        // Trigger glass transition effects
        isTransitioning = true
    }
    
    // Reset transition flag
    DispatchQueue.main.asyncAfter(deadline: .now() + 0.5) {
        isTransitioning = false
    }
}

// Component preview navigation
func showComponent(_ component: GlassComponent) {
    withAnimation(.easeOut(duration: 0.3)) {
        selectedComponent = component
        showingDetail = true
    }
}
```

## Platform-Specific Navigation

### macOS Navigation Features
```yaml
desktop_navigation:
  sidebar:
    always_visible: true
    width: "200-300pt"
    hover_highlight: true
    keyboard_navigation: true
    
  shortcuts:
    cmd_1: "Dashboard"
    cmd_2: "Components"
    cmd_3: "About"
    cmd_comma: "Preferences"
    
  gestures:
    trackpad_swipe: "Navigate back/forward"
    magic_mouse: "Momentum scrolling"
    
  animations:
    hover_delay: "0ms"
    hover_effect: "Scale + glow"
    selection: "Smooth highlight"
```

### iPad Navigation Features
```yaml
ipad_navigation:
  sidebar:
    collapsible: true
    swipe_to_reveal: true
    overlay_in_portrait: true
    
  multitasking:
    split_view: "Supported"
    slide_over: "Supported"
    
  gestures:
    edge_swipe: "Toggle sidebar"
    four_finger_swipe: "App switching"
```

### iPhone Navigation Features
```yaml
iphone_navigation:
  tab_bar:
    items: ["Dashboard", "Components", "About"]
    badge_support: false
    haptic_feedback: true
    
  gestures:
    swipe_back: "Edge gesture"
    pull_to_refresh: "Dashboard only"
    
  transitions:
    push_pop: "Standard iOS"
    tab_switch: "Instant"
```

## Gesture Support Matrix

| Gesture | macOS | iPad | iPhone | Action |
|---------|-------|------|---------|--------|
| **Tap** | ✅ | ✅ | ✅ | Select/Navigate |
| **Hover** | ✅ | ❌ | ❌ | Preview/Highlight |
| **Swipe** | ✅ | ✅ | ✅ | Back/Sidebar |
| **Pinch** | ✅ | ✅ | ❌ | Zoom content |
| **Long Press** | ✅ | ✅ | ✅ | Context menu |
| **Force Touch** | ✅ | ❌ | ✅ | Quick preview |

## Accessibility Navigation

### VoiceOver Support
```yaml
voiceover_navigation:
  landmarks:
    - "Main navigation"
    - "Dashboard content"
    - "Component library"
    
  announcements:
    page_change: "Navigated to [page name]"
    loading: "Loading content"
    complete: "Content loaded"
    
  grouping:
    cards: "Grouped by section"
    components: "Grouped by category"
    
  hints:
    interactive: "Double tap to activate"
    expandable: "Double tap to expand"
```

### Keyboard Navigation
```yaml
keyboard_support:
  tab_order: "Logical top-to-bottom"
  
  shortcuts:
    tab: "Next element"
    shift_tab: "Previous element"
    enter: "Activate"
    escape: "Close/Back"
    arrow_keys: "Navigate grid"
    
  focus_indicators:
    style: "Glass ring"
    color: "System accent"
    animation: "Subtle pulse"
```

## Performance Optimizations

### Navigation Performance
- **Lazy loading**: Components load on-demand
- **View caching**: Recently viewed pages cached
- **Prefetch**: Next likely navigation preloaded
- **Animation**: GPU-accelerated transitions

### Memory Management
```swift
// Automatic cleanup of navigation stack
.onDisappear {
    if navigationPath.count > 3 {
        navigationPath.removeLast(navigationPath.count - 3)
    }
}
```

## Future Navigation Enhancements

### Planned Features
1. **Smart Search**: AI-powered component search
2. **Favorites System**: Pin frequently used components
3. **History Tracking**: Recent navigation history
4. **Deep Linking**: URL scheme support
5. **Spotlight Integration**: System-wide search
6. **Breadcrumbs**: Visual navigation path
7. **Gesture Customization**: User preferences

This navigation system provides a smooth, platform-adaptive experience while showcasing the glass effects throughout the user journey.