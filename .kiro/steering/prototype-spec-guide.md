---
inclusion: manual
---

# Prototype Spec Guide

This steering file guides the creation of interaction specifications — the bridge between PRD requirements and prototype implementation. The spec defines WHAT happens on each screen and HOW users interact, without making visual design decisions.

## Purpose

The Prototype Spec eliminates ambiguity for prototype builders by documenting:
- Every screen's content and interactive elements
- Every user flow with edge cases
- Component behavior contracts (how tables sort, forms validate, modals dismiss)
- State definitions (empty, loading, error, loaded)
- Navigation state machine (valid transitions between screens)

## Design Boundary

**This spec defines:** Content, behavior, interactions, states, flows, responsiveness
**This spec does NOT define:** Colors, fonts, spacing, animations, visual weight, icons

The spec says "button labeled 'Save'" — the Design System says what that button looks like.

## Input Required

Before creating the Prototype Spec, ensure you have:
- Completed PRD with screen list, user flows, and requirements
- Technology context (what's technically feasible)
- Persona definitions (who uses each screen)

## Process (7 Steps)

### Challenge Check (run BEFORE specifying)

Before inventorying screens, critically examine the PRD:
1. Are these the right screens, or are we building features nobody asked for?
2. What would a first-time user hate about this flow after 30 seconds?
3. Is there a critical user journey that's missing entirely from the screen list?
4. Which requirements are actually P2 disguised as P0?
5. What would happen if we launched with half these screens?

Use findings to focus the spec on what actually matters — flag screens that don't validate the core hypothesis, add edge cases to fragile flows.

### Step 1: Screen Inventory
- List all screens from PRD
- Group by persona (who primarily uses each)
- Identify entry points (login, dashboard) and terminal screens (confirmation, export)
- Assign filenames: `Screen_[Name]_[Product]_[Date].html`

### Step 2: Information Architecture
- Primary navigation (sidebar/top nav items)
- Secondary navigation (sub-pages within sections)
- Utility navigation (settings, profile, help, logout)
- Breadcrumb paths
- Deep-link requirements

### Step 3: Screen-by-Screen Wireframe Descriptions

For EACH screen, define:

**Header:** Screen name, purpose, primary persona, entry conditions, exit paths

**Layout Zones:** What occupies header, sidebar, content, and footer zones

**Content Inventory:** Every data element — type, data source, update frequency, empty state

**Interactive Elements:** Every button, link, form field, dropdown — what it does, where it goes, when it's enabled/disabled

**State Definitions:** Default, empty, loading, error, partial — what the user sees in each state

### Step 4: User Flows with Edge Cases

For each flow:
- **Happy path:** Step-by-step ideal journey (Screen → action → Screen → result)
- **Edge cases:** Invalid input, network failure, permission denied, stale data, session expiry
- **Error recovery:** How user gets back on track

### Step 5: Component Behavior Definitions

Define behavior contracts for reusable components:
- **Data tables:** Sort, filter, paginate, row actions, bulk actions, empty/loading states
- **Forms:** Validation timing, error display, auto-save, dirty state warnings
- **Modals:** Trigger, dismiss methods (X, backdrop, Escape), confirmation patterns
- **Chat UI:** Send flow, typing indicator, response timing, error on send
- **Notifications:** Types, duration, position, stacking, action buttons
- **Dropdowns:** Open/close triggers, search for long lists, selection behavior

### Step 6: State Transitions & Navigation Map

- Valid transitions in and out of each screen
- Conditional transitions (role-based, state-based)
- Data flow between screens (what carries forward, what's re-fetched)
- Back button and browser history behavior

### Step 7: Responsive Behavior Notes

For each screen:
- Desktop (>1024px): Full layout
- Tablet (768-1024px): What collapses, what restructures
- Mobile (<768px): What stacks, what hides, touch-specific interactions
- Minimum touch target: 44px

## Output

Save to: `./documents/PrototypeSpec_[ProductName]_[YYYY-MM-DD].html`

The HTML should include:
- Table of contents with anchor links
- Collapsible sections per screen
- Tables for interactive element inventories
- Clear heading hierarchy

## Quality Checklist

Before completing:
- [ ] Every PRD screen has a complete wireframe description
- [ ] Every user flow has happy path + edge cases
- [ ] Every interactive element has defined behavior
- [ ] Every screen has all relevant states defined
- [ ] Component behaviors defined once, referenced by screen
- [ ] Navigation map covers all valid transitions
- [ ] NO visual design decisions (no colors, fonts, spacing)
- [ ] Responsive behavior noted for each screen
- [ ] Entry/exit paths are consistent across screens
- [ ] File saved with correct naming convention

## What This Spec Does NOT Do

- Choose colors, fonts, or visual style
- Create actual screen HTML files
- Write CSS or reference design tokens
- Make aesthetic direction choices
- Skip "simple" screens without documentation
