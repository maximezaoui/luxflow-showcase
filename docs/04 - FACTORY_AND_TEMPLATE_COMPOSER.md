# Factory and Template Composer

The LuxFlow Factory is the layer responsible for preparing project generation.

It connects project types, templates, sections, packs, themes, integrations and output rules into a structured production system.

---

## Purpose

The Factory exists to avoid starting every project from scratch.

It helps answer:

```txt
What kind of project is this?
What base variant should be used?
What sections are needed?
What packs are required?
What integrations are expected?
What theme should be applied?
What files should be generated?
What gates should be passed?
```

---

## From Templates to Composition

A classic template system usually works like this:

```txt
Choose one fixed template
→ Edit content
→ Customize manually
```

LuxFlow is moving toward a more flexible model:

```txt
Choose project type
→ Choose base variant
→ Compose sections
→ Select packs
→ Configure theme
→ Generate ProjectConfig
→ Compile output
```

This is the Template Composer direction.

---

## Factory Responsibilities

The Factory can manage:

```txt
Template variants
Reusable packs
Section registries
Project configuration schemas
Prompt compiler logic
Export bundle logic
Template metadata
Integration requirements
Validation rules
```

The Factory should make project generation more predictable.

---

## Template Variant

A template variant is a predefined project starting point.

Examples:

```txt
next-landing-campaign
next-vitrine-service-business
next-vitrine-local-business
next-cms-local-content
next-ecommerce-base
next-saas-base
```

A variant can define:

```txt
Site type
Default sections
Required packs
Content mode
Recommended integrations
Expected routes
Default gates
Readiness status
```

---

## Pack

A pack is a reusable feature or capability group.

Examples:

```txt
marketing-core
content-local
content-supabase
booking-lite
commerce-base
auth
billing
seo
analytics
```

A pack can provide:

```txt
Files
Routes
Helpers
Schemas
Configuration
Documentation
Integration requirements
Validation expectations
```

---

## Section Composition

Sections are selected and ordered by the composer.

Example:

```ts
const composition = {
  sections: [
    { id: "hero", enabled: true },
    { id: "feature_grid", enabled: true },
    { id: "testimonials", enabled: true },
    { id: "faq", enabled: true },
    { id: "contact_cta", enabled: true },
  ],
};
```

The goal is to generate a page structure based on explicit choices.

---

## ProjectConfig

The ProjectConfig is the structured source of truth for one project instance.

Simplified example:

```ts
const projectConfig = {
  project: {
    name: "Premium Service Website",
    slug: "premium-service-website",
  },
  template: {
    site_type: "vitrine",
    variant: "next-vitrine-service-business",
  },
  composition_v1: {
    sections: [
      { id: "hero", enabled: true },
      { id: "feature_grid", enabled: true },
      { id: "testimonials", enabled: true },
      { id: "faq", enabled: true },
      { id: "contact_cta", enabled: true },
    ],
  },
  theme_v1: {
    mode: "brand",
    radius: "soft",
    density: "comfortable",
  },
};
```

This is more reliable than a vague prompt because it gives the system concrete data.

---

## Compiler

The compiler transforms structured project configuration into execution-ready instructions.

It can produce:

```txt
Prompt bundle
Expected artefacts
Implementation notes
Required packages
Required routes
Required sections
Gate list
Warnings
Delivery notes
```

Simplified flow:

```txt
ProjectConfig
→ Compiler
→ Prompt
→ ExportBundle
→ Execution
```

---

## ExportBundle

The ExportBundle is the portable output of the Factory.

Simplified example:

```ts
const exportBundle = {
  version: "v2",
  project_config: projectConfig,
  generated_prompt: "...",
  expected_artifacts: [
    "app/page.tsx",
    "src/styles/theme.css",
    "docs/DELIVERY.md",
  ],
  gates: [
    "typecheck",
    "build",
    "token-usage",
    "template-composer",
  ],
};
```

The ExportBundle makes the generation process traceable.

---

## Template Composer Flow

```txt
1. Select project family
2. Select variant
3. Select sections
4. Configure theme
5. Add integrations
6. Review generated configuration
7. Compile project output
8. Export bundle
9. Run gates
```

---

## User Experience Direction

The Template Composer should be selection-first.

It should rely on:

```txt
Cards
Toggles
Checkboxes
Radio groups
Dropdowns
Chips
Presets
Pre-filled values
Simple previews
```

Free text should be limited to what is really necessary:

```txt
Project name
Short description
Domain or URL
Optional notes
```

The user should not need to understand every internal technical detail.

---

## Example Composer Choices

```txt
Project family:
Service website

Variant:
Service business

Goal:
Generate leads

Sections:
Hero
Services
Proof
FAQ
Contact CTA

Theme:
Premium dark/light

Integrations:
Contact form
Map

Output:
ProjectConfig
Prompt bundle
Expected file tree
Required gates
Delivery checklist
```

---

## Readiness Levels

Template variants can have readiness levels.

Example:

```txt
available
warning
hidden
deferred
```

### Available

The variant is usable.

### Warning

The variant can be used but has known limitations.

### Hidden

The variant should not be shown in the main user interface.

### Deferred

The variant is planned but not ready.

This protects the user from selecting unfinished options.

---

## Why Not Only Fixed Templates?

Fixed templates are useful but limited.

They often create problems:

```txt
Too many duplicated files
Difficult customization
Rigid page structure
Manual changes after generation
Harder maintenance
Template explosion
```

The Template Composer helps reduce this by separating:

```txt
Base variant
Sections
Packs
Theme
Integrations
Content mode
```

---

## Factory Quality Rules

The Factory should follow these rules:

```txt
No hidden project logic
No unclear template status
No duplicated section logic without reason
No project generation without config
No export without gates
No user-facing option that cannot be executed
```

---

## Relationship With Design System

The Factory depends on the design system.

When a section is selected, it should map to:

```txt
@luxflow/sections
@luxflow/ui
@luxflow/tokens
Project theme
Expected file structure
```

This makes composition reliable.

---

## Relationship With LuxFlow OS

LuxFlow OS is the interface.  
The Factory is the production logic.

```txt
LuxFlow OS
→ lets the user make choices

Factory
→ turns those choices into structured project output
```

This separation keeps the system easier to maintain.

---

## Final Principle

The Factory should make project creation feel simple for the user while keeping the technical output structured.

```txt
Simple interface
Structured configuration
Reusable parts
Controlled generation
Validated output
```
