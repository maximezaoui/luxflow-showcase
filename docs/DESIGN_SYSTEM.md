# LuxFlow Design System

The LuxFlow design system is built to keep projects visually consistent while reducing duplicated UI work.

It is based on three main layers:

```txt
Tokens → UI Components → Sections
```

Each layer has a specific role.

---

## Purpose

The design system exists to help LuxFlow projects share the same foundation while still allowing project-specific branding.

It should help avoid:

```txt
Repeated component creation
Hardcoded styles
Inconsistent spacing
Inconsistent colors
Duplicate navbars and footers
Theme drift between projects
Uncontrolled CSS overrides
```

The goal is to make projects faster to build and easier to maintain.

---

## Design System Layers

```txt
packages/tokens
→ packages/ui
→ packages/sections
→ project theme
→ final website or app
```

---

## 1. Tokens

Tokens define the visual contract.

They can include:

```txt
Colors
Typography
Spacing
Radius
Borders
Surfaces
States
Shadows
Motion values
```

A project should customize the theme by overriding token values instead of rewriting shared components.

Simplified example:

```css
:root {
  --lf-bg: #ffffff;
  --lf-surface: #f8f8f8;
  --lf-text: #111111;
  --lf-muted: #666666;

  --lf-brand: #7c3aed;
  --lf-brand-contrast: #ffffff;

  --lf-radius-sm: 0.375rem;
  --lf-radius-md: 0.75rem;
  --lf-radius-lg: 1rem;
}
```

---

## 2. UI Components

The UI package contains reusable building blocks.

Examples:

```txt
Button
Card
Input
Textarea
Select
Navbar
Footer
Container
Section Header
Tabs
Accordion
Modal
Dropdown
App Shell
Dashboard Card
Pricing Card
Article Card
Product Card
```

Components should be generic enough to work across several projects.

Example:

```tsx
import { FormButton, PrimitivesCard } from "@luxflow/ui";

export function ExampleCard() {
  return (
    <PrimitivesCard>
      <h2>Reusable UI</h2>
      <p>This card uses shared LuxFlow primitives.</p>
      <FormButton>Continue</FormButton>
    </PrimitivesCard>
  );
}
```

---

## 3. Sections

Sections are larger reusable page blocks.

A section is usually made of several UI components.

Examples:

```txt
Hero section
Feature grid
Services section
Testimonials section
FAQ section
Contact CTA
Pricing section
Blog preview
Local business information
Process timeline
```

Sections make project generation more flexible than fixed templates.

Example registry:

```ts
export const sectionRegistry = {
  hero: {
    component: "HeroSection",
    package: "@luxflow/sections",
    required: true,
  },
  featureGrid: {
    component: "FeatureGridSection",
    package: "@luxflow/sections",
    required: false,
  },
  faq: {
    component: "FaqSection",
    package: "@luxflow/sections",
    required: false,
  },
  contactCta: {
    component: "ContactCtaSection",
    package: "@luxflow/sections",
    required: false,
  },
};
```

---

## Token-Based Theming

LuxFlow projects should use tokens as the theming boundary.

A project should define its theme in a dedicated file, for example:

```txt
src/styles/theme.css
```

The theme should override the public token contract.

Example:

```css
:root {
  --lf-bg: #050816;
  --lf-surface: #0f172a;
  --lf-text: #f8fafc;
  --lf-muted: #94a3b8;

  --lf-brand: #38bdf8;
  --lf-brand-contrast: #020617;
}
```

This allows the same components to be reused across different brands.

---

## Shared-First Rule

LuxFlow follows a shared-first rule.

Before creating a local component, a project should check:

```txt
Can this be done with @luxflow/ui?
Can this be done with @luxflow/sections?
Can this be configured through props?
Can this be handled by tokens?
Is this truly project-specific?
```

Local components should be reserved for real project-specific needs.

---

## Good Local Component

A local component is acceptable when it depends on unique project context.

Example:

```txt
A custom editorial hero that matches a specific brand layout
A project-specific timeline
A unique interactive visual
A highly specific client section
```

---

## Bad Local Component

A local component is usually not acceptable when it duplicates shared UI.

Examples:

```txt
Custom Button
Custom Card
Custom Navbar
Custom Footer
Custom Form Field
Custom Container
Custom Section Header
```

These should normally come from the shared UI package.

---

## CSS Contract

The design system should expose a stable CSS contract.

Simplified import order:

```css
@import "@luxflow/tokens/contract.css";
@import "@luxflow/ui/styles/components.css";
@import "./theme.css";
```

The exact implementation can evolve, but the principle stays the same:

```txt
Base contract first
Shared components second
Project theme overrides last
```

---

## Design System Benefits

The LuxFlow design system improves:

```txt
Visual consistency
Development speed
Theme switching
Component reuse
Maintenance
Client project quality
Portfolio coherence
```

It also reduces the risk of each project becoming a separate design system.

---

## Example Project Theme

```css
:root {
  --lf-bg: #ffffff;
  --lf-surface: #f7f7f8;
  --lf-text: #111827;
  --lf-muted: #6b7280;

  --lf-brand: #2563eb;
  --lf-brand-hover: #1d4ed8;
  --lf-brand-contrast: #ffffff;

  --lf-border: #e5e7eb;
  --lf-radius-md: 0.75rem;
  --lf-radius-lg: 1rem;
}
```

---

## Design System and LuxFlow OS

LuxFlow OS should also consume the shared design system where possible.

This prevents the internal console from becoming visually disconnected from the projects it produces.

The same design principles should apply to:

```txt
Project starter wizard
Cards
Forms
Navigation
Preview panels
Run preparation views
System dashboards
```

---

## Design System and Template Composer

The Template Composer depends on the design system.

When a user selects sections, variants or themes, LuxFlow should be able to map those choices to:

```txt
Reusable sections
Reusable UI components
Token overrides
Project configuration
Expected file structure
Validation gates
```

This keeps composition structured instead of manually assembled.

---

## Design System Quality Rules

A good LuxFlow project should respect these rules:

```txt
Use shared UI when possible
Use shared sections when possible
Use tokens for theme values
Avoid hardcoded colors
Avoid duplicate primitives
Keep project-specific components minimal
Document exceptions
Validate theme and CSS usage
```

---

## Final Principle

A design system is not only about visuals.

For LuxFlow, the design system is also a production tool.

It makes projects:

```txt
Faster to build
Easier to theme
Easier to maintain
More consistent
More professional
More reusable
```
