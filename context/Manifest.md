# LiquidGlassKit Context Engineering Manifest

**Purpose**: Master reference for AI systems to understand the context module structure  
**Last Updated**: July 31, 2025  
**Manifest Version**: 1.1  
**Framework**: SwiftUI Glassmorphism Component Library (3,543 LOC)

## Module Version Registry

| Module | Version | Last Modified | Size | Health |
|--------|---------|--------------|------|---------|
| ARCHITECTURE.md | 1.1 | July 31, 2025 | 8KB | ✅ |
| IMPLEMENTATION.md | 1.1 | July 31, 2025 | 12KB | ✅ |
| VISUAL.md | 1.1 | July 31, 2025 | 10KB | ✅ |
| NAVIGATION.md | 1.1 | July 31, 2025 | 6KB | ✅ |
| INTEGRATION.yaml | 1.1 | July 31, 2025 | 4KB | ✅ |
| EVOLUTION.md | 1.1 | July 31, 2025 | 6KB | ✅ |
| session.json | - | DYNAMIC | 3KB | ✅ |

## Quick Reference Matrix

| Information Needed | Primary Module | Secondary Module |
|-------------------|----------------|------------------|
| How glassmorphism works | ARCHITECTURE.md | VISUAL.md |
| Current component status | IMPLEMENTATION.md | session.json |
| Glass effects & colors | VISUAL.md | ARCHITECTURE.md |
| Navigator flow | NAVIGATION.md | IMPLEMENTATION.md |
| XCFramework setup | INTEGRATION.yaml | ARCHITECTURE.md |
| Design decisions | EVOLUTION.md | ARCHITECTURE.md |
| Recent changes | session.json | EVOLUTION.md |

## Context Loading Strategy

### For Bug Fixes
1. IMPLEMENTATION.md (current state)
2. session.json (recent changes)
3. ARCHITECTURE.md (design constraints)

### For New Features
1. ARCHITECTURE.md (component patterns)
2. NAVIGATION.md (user flow)
3. VISUAL.md (glass effects)
4. IMPLEMENTATION.md (integration points)

### For UI Polish
1. VISUAL.md (glass specifications)
2. ARCHITECTURE.md (component hierarchy)
3. IMPLEMENTATION.md (current components)

### For XCFramework Work
1. INTEGRATION.yaml (build settings)
2. ARCHITECTURE.md (module structure)
3. IMPLEMENTATION.md (file organization)