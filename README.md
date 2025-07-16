
# ✨ LiquidGlassKit

*Apple-Native Glassmorphic UI Framework (XCFramework)*

![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20iOS-blue)
![Architecture](https://img.shields.io/badge/arch-Apple%20Silicon-green)
![Swift Version](https://img.shields.io/badge/swift-6.0-orange)
![Status](https://img.shields.io/badge/status-Active%20Development-yellow)

**LiquidGlassKit** is a **WWDC26-compliant SwiftUI glassmorphic framework** providing a full **Atomic → Foundation → Molecular → Organism** component hierarchy. It includes an **Apple System Settings–style Tahoe Navigator**, dynamic previews, and full adaptive design for iPhone, iPad, and Mac.

---

## ✨ Key Features

### 🎨 True Apple-Grade Glassmorphism
- **Adaptive glass components** optimized for iOS 18 & macOS 15  
- **Dynamic type support** (Apple HIG-compliant)  
- **SF Symbols only** (no custom icons, Apple-approved icons only)  
- **Automatic size-class adaptation** (compact, regular, desktop)

### ⚡ Modular Component Hierarchy
- **Atomic** – Core reusable elements (progress, icons, typography)  
- **Foundation** – Colors, constants, trends, status  
- **Molecular** – Composite UI (buttons, headers, progress sections)  
- **Organism** – Complex cards (status, metrics, project phases)

### 🧭 Tahoe Navigator & Pages
- **System Settings–style navigation**  
- **Dashboard with live script & LOC counters**  
- **Prebuilt component previews** for iPhone, iPad, Mac

### 🏗️ Built for Swift 6+
- Pure **SwiftUI** – No UIKit or AppKit  
- Designed for **XCFramework distribution**  
- Full **@MainActor** compliance where required

---

## 📱 Platform Experiences

### macOS (Desktop)
- Full **Tahoe Sidebar Navigation**  
- Hover glow and glass animations  
- System Settings–style grouped pages

### iOS (Compact)
- Vertical, card-based pages for each category  
- Optimized tap targets (≥44×44pt)  
- Dynamic type and haptic feedback

### iPad (Regular)
- Combined adaptive layout  
- Sidebar or vertical mode depending on orientation

---

## 🧩 Component Architecture

```
LiquidGlassKit/
├── GlassComponents/
│   ├── Atomic/        # GlassCircularProgress, GlassIcon, Typography
│   ├── Foundation/    # GlassColors, TrendDirection, GlassConstants
│   ├── Molecular/     # Action buttons, headers, progress sections
│   ├── Organism/      # Complex cards (status, metrics, phases)
│   ├── Navigation/    # GlassSystemNavigator (Tahoe-style)
│   └── Pages/         # Dashboard + adaptive previews
└── Shared/
    ├── GlassConstants.swift
    ├── GlassColors.swift
    └── LineCounter.swift (LOC + script counters)
```

---

## 🧭 Pages & Navigator

### GlassSystemNavigator
**Full app navigation**:

```swift
import LiquidGlassKit

struct ContentView: View {
    var body: some View {
        GlassSystemNavigator() // Tahoe sidebar navigation
    }
}
```

### Dashboard Page
- **Live Script Counter** (auto-scans XCFramework project)  
- **LOC Tracker** (Atomic → Foundation → Molecular → Organism)  
- **Modularity Pie Charts** (Inline vs Modular)

### Component Pages
- **AtomicPreviews**  
- **FoundationPreviews**  
- **MolecularPreviews**  
- **OrganismPreviews**

---

## 🛠️ Installation

### XCFramework Setup
1. Drag **`LiquidGlassKit.xcframework`** into your Xcode project.  
2. In **Frameworks, Libraries, and Embedded Content**, select **Embed & Sign**.  
3. Add `import LiquidGlassKit` where needed.

### Requirements
- **iOS 18.0+** or **macOS 15.0+**  
- **Xcode 16**  
- **Swift 6.0+**

---

## 🔧 Usage Examples

### Atomic Example
```swift
VStack {
    GlassCircularProgress(progress: 72)
    GlassStatusIndicator(isActive: true, color: .green, size: 12)
    GlassIcon(systemName: "star.fill", color: .yellow)
    Text("Welcome").glassTypography(.headline)
}
```

### Molecular Example
```swift
GlassActionButton(title: "Deploy", icon: "arrow.up.circle.fill", color: .blue) {}
```

### Organism Example
```swift
ModernMetricCard(
    title: "Active Users",
    value: "12,450",
    trend: .up,
    icon: "person.3.fill"
)
```

---

## 🚧 Development Status

### ✅ Completed
- Adaptive previews for all components  
- Script + LOC counters integrated in Dashboard  
- macOS hover effects and animations

### 🔄 In Progress
- Theme customization (dynamic glass themes)  
- Extended charts for Dashboard analytics

### 📋 Planned
- Accessibility VoiceOver labels for all components  
- Modular theme packs (Atomic → Organism)

---

## 📚 Documentation

Additional documentation provided:  
- [Guide.md](./LiquidGlassKit_Guide.md) — Integration & API Reference  
- [Design.md](./LiquidGlassKit_Design.md) — Apple HIG & WWDC26 compliance  
- [Context.md](./LiquidGlassKit_Context.md) — AI & developer context

---

## 🤝 Contributing

Currently private, but feedback is welcome:  
- Feature requests  
- Bug reports  
- Suggestions for Apple review compliance

---

## 📄 License

LiquidGlassKit will be released under an **open-source license (TBD)** once public beta is ready.

---

<p align="center">
  <i>Built with ❤️ for Apple platforms by Lithalean</i>
</p>

<p align="center">
  <a href="#-liquidglasskit">Back to top ↑</a>
</p>
