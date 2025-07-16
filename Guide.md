
# LiquidGlassKit XCFramework Usage Guide

**Version:** WWDC26 – OS26 Optimized  
**Author:** Lithalean (LiquidGlassKit Project)  
**Purpose:** This guide explains how to integrate **LiquidGlassKit** as an **XCFramework** into your SwiftUI project, providing glassmorphic UI components categorized into **Atomic, Foundation, Molecular, and Organism**, as well as the flagship **Tahoe Navigator & Pages system**.

---

## ✅ Table of Contents

1. [Installation & Setup](#1-installation--setup)  
2. [Section 1 – Components](#2-section-1--components)  
    - [Atomic](#atomic)  
    - [Foundation](#foundation)  
    - [Molecular](#molecular)  
    - [Organism](#organism)  
3. [Section 2 – Navigation & Pages](#3-section-2--navigation--pages)  
    - [GlassSystemNavigator](#glasssystemnavigator)  
    - [PagesPreviews (Tahoe Navigator Previews)](#pagespreviews-tahoe-navigator-previews)  
    - [Dashboard Page](#dashboard-page)  

---

## 1. Installation & Setup

### **Step 1: Adding the XCFramework**

1. Drag **`LiquidGlassKit.xcframework`** into your Xcode project **(Project Navigator → Frameworks, Libraries, and Embedded Content)**.
2. Ensure **“Embed & Sign”** is selected.
3. Add `import LiquidGlassKit` at the top of any SwiftUI file.

### **Step 2: Minimum Requirements**

- **Darwin OS 26**  
- **Swift 6.2+**  
- **Xcode 26**  
- RealityKit 3 compatible

### **Step 3: Basic Verification**

```swift
import LiquidGlassKit

struct TestView: View {
    var body: some View {
        Text("LiquidGlassKit Loaded!")
            .font(.title)
            .padding()
            .background(.thinMaterial, in: RoundedRectangle(cornerRadius: 12))
    }
}
```

If this builds, the framework is integrated correctly.

---

## 2. Section 1 – Components

All components are categorized for modular design: **Atomic → Foundation → Molecular → Organism**.

---

### ### Atomic

#### **Overview**
The smallest, reusable glass UI elements (e.g., icons, progress indicators, typography).

#### **How to Import**
```swift
import LiquidGlassKit
```

#### **Available Components (API List)**

| Component | Description |
|-----------|-------------|
| `GlassCircularProgress(progress: Double)` | Circular glassmorphic progress indicator (0–100%). |
| `GlassStatusIndicator(isActive: Bool, color: Color, size: CGFloat)` | Small glowing status light. |
| `GlassIcon(systemName: String, color: Color, size: Font)` | SF Symbol-based icon with glass polish. |
| `Text.glassTypography(_ style: GlassTextStyle)` | Text typography extension (headline, subheadline, caption). |

#### **Basic Usage**
```swift
VStack {
    GlassCircularProgress(progress: 72)
    GlassStatusIndicator(isActive: true, color: .green, size: 12)
    GlassIcon(systemName: "star.fill", color: .yellow, size: .title3)
    Text("Hello Glass").glassTypography(.headline)
}
```

---

### ### Foundation

#### **Overview**
Fundamental colors, constants, and trends powering the glass system.

#### **Available Components (API List)**

| Component | Description |
|-----------|-------------|
| `GlassColors.primary` / `.accent` / `.success` / `.warning` / `.error` / `.info` | Core color palette. |
| `GlassConstants.itemPadding / sectionSpacing / cardCornerRadius` | Glass spacing and sizing standards. |
| `TrendDirection.up / .down / .stable` | Trend indicator with associated color and SF Symbol. |
| `ComponentStatus.active / .inactive / .error` | Basic status states for components. |

#### **Basic Usage**
```swift
RoundedRectangle(cornerRadius: GlassConstants.cardCornerRadius)
    .fill(GlassColors.primary)
    .frame(width: 80, height: 80)

Text(TrendDirection.up.icon)
    .foregroundStyle(TrendDirection.up.color)
```

---

### ### Molecular

#### **Overview**
Combined glass components (buttons, headers, progress sections).

#### **Available Components (API List)**

| Component | Description |
|-----------|-------------|
| `GlassActionButton(title: String, icon: String, color: Color)` | Primary action button with glass glow. |
| `GlassCardHeader(icon:title:iconColor:showStatus:isActive:)` | Header with status indicator. |
| `GlassProgressSection(title:currentPhase:progress:segmentCount:)` | Horizontal phase progress tracker. |
| **Advanced Buttons (GlassButtons)**: `ModernGlassButton`, `CircularGlassButton`, `ActionCardButton`, `FloatingActionButton`, `MinimalGlassButton` | Advanced glassmorphic buttons. |

#### **Basic Usage**
```swift
GlassActionButton(title: "Deploy", icon: "arrow.up.circle.fill", color: .blue) {}
GlassProgressSection(title: "Phase 2", currentPhase: "In Progress", progress: 3.5)
```

---

### ### Organism

#### **Overview**
Complex, card-based UI components combining Atomic, Foundation, and Molecular layers.

#### **Available Components (API List)**

| Component | Description |
|-----------|-------------|
| `ModernStatusCard(title:subtitle:icon:status:)` | Status indicator card. |
| `ModernActionCard(title:subtitle:icon:color:isEnabled:action:)` | Glass action card for key operations. |
| `ModernMetricCard(title:value:trend:icon:color:)` | Metric display with trend indicator. |
| `PhaseProgressCard(title:subtitle:features:progress:currentPhase:color:)` | Multi-feature progress card. |

#### **Basic Usage**
```swift
ModernStatusCard(
    title: "Server Online",
    subtitle: "Last Checked 2 min ago",
    icon: "bolt.fill",
    status: .active
)
```

---

## 3. Section 2 – Navigation & Pages

### **GlassSystemNavigator**

#### **Overview**
A System Settings–style Tahoe Navigator for browsing Dashboard & Component pages.

#### **Usage**
```swift
import LiquidGlassKit

struct ContentView: View {
    var body: some View {
        GlassSystemNavigator() // Full sidebar + pages
    }
}
```

### **PagesPreviews (Tahoe Navigator Previews)**

Use this when building or testing LiquidGlassKit itself.

```swift
#Preview("Pages – Desktop (Mac)") {
    PagesPreviewNavigator()
        .frame(width: 1200, height: 800)
        .preferredColorScheme(.dark)
}
```

### **Dashboard Page**

The dashboard shows project health, LOC counters, and modular charts.

```swift
GlassDashboardPage()
```

---

## ✅ Closing Notes

- **Adaptive Design:** All components automatically adjust between Compact, Regular, and Desktop layouts.  
- **macOS Polishing:** Hover effects & glass animations are automatically applied.  
- **Recommended:** Keep LiquidGlassKit updated with your project for consistent spacing and glass style.

---

© 2025 Lithalean – LiquidGlassKit Project
