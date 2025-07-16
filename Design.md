
# LiquidGlassKit – Design Guidelines (WWDC26 Compliant)

**Date**: July 2025  
**Status**: Complete – Adaptive Glassmorphic UI for SwiftUI  
**Audience**: Developers integrating **LiquidGlassKit.xcframework** into macOS and iOS apps.  

---

## 📖 Table of Contents

1. [Design Philosophy](#1-design-philosophy)  
2. [Component Layers](#2-component-layers)  
   - [Atomic](#atomic)  
   - [Foundation](#foundation)  
   - [Molecular](#molecular)  
   - [Organism](#organism)  
3. [Apple Guidelines Compliance](#3-apple-guidelines-compliance)  
4. [Integration Rules](#4-integration-rules)  

---

## 1. Design Philosophy

LiquidGlassKit adheres strictly to **Apple Human Interface Guidelines (HIG)** and **WWDC26 glassmorphic design standards**:

- **Hierarchy of Components**: Built around **Atomic → Foundation → Molecular → Organism** layers, ensuring reusability and consistency.
- **Platform-First**: Optimized for **macOS 15** (enhanced layouts) and **iOS 18** (simplified, touch-first).
- **Adaptive Design**: Automatically adjusts based on size classes (`compact`, `regular`, `desktop`).
- **Pure SwiftUI, Swift 6+ Only**: No UIKit; designed for Swift Concurrency and composable views.

---

## 2. Component Layers

### **Atomic**

#### **Purpose**
The smallest, reusable building blocks. Minimal animations, lightweight rendering.

#### **Design Rules (Apple-Compliant)**
- **SF Symbols Only** for icons (`systemName` required).  
- Typography strictly uses **Dynamic Type** via `Font` or `.glassTypography`.  
- **Do not hardcode colors**; use provided `GlassColors`.

#### **Available Components**
- **`GlassCircularProgress(progress: Double)`** – Renders 0–100% circular indicators.  
- **`GlassStatusIndicator(isActive: Bool, color: Color)`** – Status light with glow.  
- **`GlassIcon(systemName: String, color: Color)`** – Glass-styled SF Symbol.  
- **`Text.glassTypography(_ style: GlassTextStyle)`** – Headline, subheadline, caption presets.

#### **Best Practice**
✅ Always wrap Atomic elements in **HStack** or **VStack** with Apple-standard spacing (`GlassConstants.itemPadding`).  

---

### **Foundation**

#### **Purpose**
The visual and behavioral ruleset of the design system.

#### **Design Rules**
- Colors strictly use **semantic naming** (`GlassColors.primary`, `.accent`, `.success`, etc.).  
- Trends and statuses use **SF Symbols Apple provides** (`arrow.up`, `arrow.down`, `minus`).  
- Constants must **never** be hardcoded; only use `GlassConstants`.

#### **Available Components**
- **`GlassColors`** – Primary, Accent, Success, Warning, Error, Info.  
- **`GlassConstants`** – `itemPadding`, `sectionSpacing`, `cardCornerRadius`, etc.  
- **`TrendDirection`** – Up, Down, Stable (auto-colored).  
- **`ComponentStatus`** – Active, Inactive, Error states.

---

### **Molecular**

#### **Purpose**
Composite components combining Atomic + Foundation.

#### **Design Rules**
- Buttons use **adaptive size classes** (Apple requires tap targets ≥44×44pt).  
- Progress sections display **segmented indicators** per HIG.  
- Header icons must use **SF Symbols** with semantic coloring.

#### **Available Components**
- **`GlassActionButton(title: String, icon: String, color: Color)`**  
- **`GlassCardHeader(icon:title:iconColor:showStatus:isActive:)`**  
- **`GlassProgressSection(title:currentPhase:progress:segmentCount:)`**  
- **Advanced Buttons**:  
  - `ModernGlassButton`, `CircularGlassButton`, `ActionCardButton`, `FloatingActionButton`, `MinimalGlassButton`.

#### **Best Practice**
✅ Use `.padding()` + `.background(.thinMaterial)` for consistency with Apple’s system components.

---

### **Organism**

#### **Purpose**
Full cards and large UI structures.

#### **Design Rules**
- Must adapt responsively to `compact`, `regular`, and `desktop` layouts.  
- Cards use **Apple’s HIG standard corner radius** (provided via `GlassConstants`).  
- Always animate entrance transitions using `.spring(response:dampingFraction:)`.

#### **Available Components**
- **`ModernStatusCard(title:subtitle:icon:status:)`**  
- **`ModernActionCard(title:subtitle:icon:color:isEnabled:action:)`**  
- **`ModernMetricCard(title:value:trend:icon:color:)`**  
- **`PhaseProgressCard(title:subtitle:features:progress:currentPhase:color:)`**

#### **Best Practice**
✅ Group Organism components in `LazyVGrid` for desktop layouts, vertical stacks for compact layouts.

---

## 3. Apple Guidelines Compliance

LiquidGlassKit follows **WWDC26** standards:

1. **Swift 6+ Only** – All APIs are `public`, `@MainActor` where needed.  
2. **Dynamic Type Ready** – Typography scales automatically.  
3. **SF Symbols Compliance** – No custom icons; all SF Symbols approved by Apple.  
4. **Accessibility Ready** – Color contrasts meet WCAG 2.1 AA.  
5. **Size Class Adaptive** – iPhone (Compact), iPad (Regular), Mac (Desktop).  

---

## 4. Integration Rules

1. **Always Import the XCFramework**  
   ```swift
   import LiquidGlassKit
   ```
2. **Never Modify Constants** – Do not hardcode corner radii, colors, or spacings.  
3. **Follow Component Hierarchy** – Build UI progressively: **Atomic → Foundation → Molecular → Organism**.  
4. **Navigation** – Use `GlassSystemNavigator` or `PagesPreviews` to maintain Apple’s Tahoe-style UX.

---

## ✅ Closing Notes

LiquidGlassKit was designed **from the ground up to pass Apple’s app review guidelines**.  
Follow these rules to ensure apps maintain **WWDC26-grade visual and technical fidelity**.
