
# LiquidGlassKit — AI Context Document

**Date**: July 2025  
**Status**: Active Development – Flagship Glassmorphic UI Complete  
**Purpose**: Accurate context for AI systems and developers working with the LiquidGlassKit XCFramework.

---

## 🎯 Project Identity

**LiquidGlassKit** is a **WWDC26–style SwiftUI glassmorphic UI framework** providing **Atomic, Foundation, Molecular, and Organism** components with a full **System Settings–like Tahoe Navigator**.

**Key Facts:**
- Built exclusively for **Apple Silicon** (iOS 18 / macOS 15 – OS26)  
- 100% **SwiftUI-native** (no UIKit required)  
- Distributed as **LiquidGlassKit.xcframework**  
- Includes **flagship adaptive previews** for iPhone, iPad, and Mac  
- Modularized into **Atomic → Foundation → Molecular → Organism**

---

## 🏗️ Current Architecture

### Directory Structure
```
LiquidGlassKit/
├── GlassComponents/
│   ├── Atomic/                  # Smallest reusable UI pieces
│   ├── Foundation/              # Core colors, constants, trends
│   ├── Molecular/               # Composite buttons, headers, progress bars
│   ├── Organism/                # Complex card-based UI
│   ├── Navigation/
│   │   └── GlassSystemNavigator.swift  # Tahoe Navigator
│   └── Pages/                   # Dashboard + component previews
│
├── Previews/
│   ├── AtomicPreviews.swift
│   ├── FoundationPreviews.swift
│   ├── MolecularPreviews.swift
│   ├── OrganismPreviews.swift
│   └── PagesPreviews.swift      # Unified preview system
│
└── Shared/
    ├── GlassConstants.swift     # Global spacing and style constants
    ├── GlassColors.swift        # Core glass palette
    ├── TrendDirection.swift     # Up, down, stable indicators
    └── LineCounter.swift        # LOC + script counter
```

### XCFramework Output
```
LiquidGlassKit.xcframework
├── macos-arm64
└── ios-arm64
```

---

## 🧩 Component Hierarchy

**Atomic → Foundation → Molecular → Organism**

| Layer        | Example Components |
|--------------|--------------------|
| **Atomic**   | `GlassCircularProgress`, `GlassStatusIndicator`, `GlassIcon`, `glassTypography` |
| **Foundation** | `GlassColors`, `TrendDirection`, `GlassConstants`, `ComponentStatus` |
| **Molecular**  | `GlassActionButton`, `GlassCardHeader`, `GlassProgressSection`, `Advanced Buttons` |
| **Organism**   | `ModernStatusCard`, `ModernActionCard`, `ModernMetricCard`, `PhaseProgressCard` |

---

## 🔧 Integration Context

### **XCFramework Setup**
1. Drag **LiquidGlassKit.xcframework** into Xcode.
2. Set “**Embed & Sign**”.
3. Add `import LiquidGlassKit` where needed.

### **Example Project Use**
```swift
import LiquidGlassKit

struct ContentView: View {
    var body: some View {
        GlassSystemNavigator() // Tahoe Navigator entry point
    }
}
```

---

## 🎨 UI/UX Philosophy

### Adaptive Design
- **Compact (iPhone)** → Vertical, grouped cards.  
- **Regular (iPad)** → Sidebar navigation with larger cards.  
- **Desktop (Mac)** → Full **System Settings–style** Tahoe Navigator.

### macOS Polishing
- Subtle hover glow (`.hoverEffectOnMac()`)
- Animated entrance transitions for cards and sections

---

## 🚧 Current Development Focus

### Immediate Goals
- Full polish pass on Organism and Pages components
- Expand Dashboard charts (modular vs inline analysis)
- Improve adaptive layout transitions

### Long-Term Goals
- Theme customization (dynamic glass colors)
- Possible cross-XCFramework bridging for other engines

---

*This document reflects the actual current state as of July 2025*
