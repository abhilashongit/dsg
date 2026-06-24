# ALYGNR Design System
**Version 1.0 · June 2026 · Canonical Reference for Animation, Website, and Product UI**

> This document governs every visual and UX decision in ALYGNR's product, marketing website,
> and animation work. It is derived from CLAUDE.md, ALYGNR-Brand-Voice.md, the Platform Brief,
> and the production codebase design tokens. When this document conflicts with an older spec,
> this document wins.

---

## 0. Guiding Principles

Five principles govern all design decisions. When in doubt, return to these.

**1. The system, not the feature.**  
Design surfaces what the system does for the user, not what a feature is called. Every screen asks: "What is the user's outcome here?"

**2. Breathable by default.**  
Apple-inspired spatial restraint. White space is structure, not emptiness. Never crowd a surface.

**3. Document feel, not form feel.**  
In-app editors and review screens should feel like editing a document, not filling out a form. Fields have no border at rest. Borders appear on focus. Labels are section headings, not field labels.

**4. Earned warmth.**  
The system acknowledges milestones when they matter. It does not perform enthusiasm. Celebrations are specific, forward-pointing, brief.

**5. Orange is decisive.**  
Orange `#E8521A` is not a decoration colour. It signals a decision point, an active state, or a brand anchor. Never scatter it. Every orange element on a screen should be intentional and non-redundant.

---

## 1. Colour System

### Primary Palette

| Token | Hex | Usage |
|---|---|---|
| `--black` | `#0A0A0A` | Primary dark background (marketing, loading screens, sidebars) |
| `--cream` | `#F7F7F5` | Light backgrounds (onboarding screens, Foundation setup) |
| `--orange` | `#E8521A` | Accent only — CTAs, eyebrow bars, active states, brand emphasis |
| `--app-bg` | `#F3F4F6` | In-app page background |
| `--card-bg` | `#FFFFFF` | Cards, panels, elevated surfaces |
| `--dark-mid` | `#1C1C1A` | Secondary dark (browser chrome, dark cards, deep panels) |
| `--cream-deep` | `#E8E6DE` | Framework pills, secondary surface on light backgrounds |

### Text Colours (light surfaces)

| Token | Hex | Usage |
|---|---|---|
| `--text-primary` | `#111827` | Primary body text on light backgrounds |
| `--text-secondary` | `#6B7280` | Supporting text, subheadlines, descriptors |
| `--text-muted` | `#9CA3AF` | Labels, placeholders, timestamps, secondary metadata |

### Text Colours (dark surfaces)

| Token | Hex | Usage |
|---|---|---|
| `--text-primary-dark` | `#F9FAFB` | Primary text on black/dark-mid backgrounds |
| `--text-secondary-dark` | `#9CA3AF` | Supporting text on dark backgrounds |
| `--text-muted-dark` | `#4B5563` | Muted text on dark backgrounds |

### Border Colours

| Token | Hex | Usage |
|---|---|---|
| `--border` | `#E5E7EB` | Standard card and input borders (light surfaces) |
| `--border-dark` | `#2A2A28` | Borders on dark backgrounds |
| `--border-focus` | `#E8521A` | Bottom border only, on focused input fields |

### Status Colours (in-product only, never in marketing)

| Status | Background | Text | Border |
|---|---|---|---|
| `draft` | `#F3F4F6` | `#6B7280` | `#E5E7EB` |
| `ready` | `#FFFBEB` | `#B45309` | `#FDE68A` |
| `approved` | `#F0FDF4` | `#15803D` | `#BBF7D0` |
| `rejected` | `#FEF2F2` | `#DC2626` | `#FECACA` |

### Colour Rules (non-negotiable)

- Orange `#E8521A` never appears on more than two elements per screen simultaneously.
- Never use orange as a background on a large surface. It is an accent, not a fill.
- Never use gradient backgrounds. Solid only.
- Never use stock-photo backgrounds. Text on solid colour or UI on solid colour only.
- The cream `#F7F7F5` and black `#0A0A0A` are the only two primary backgrounds.
  The app grey `#F3F4F6` is for in-product only, never marketing surfaces.
- No green, blue, or purple in the primary UI. Status colours are confined to badges.

---

## 2. Typography

### Typeface Stack

| Font | Role | Weights used |
|---|---|---|
| **Inter Tight** | Display, headlines, screen titles, large numbers | Medium 500, Bold 700, Black 900 |
| **Inter** | Body, UI copy, labels, tooltips, form fields, buttons | Regular 400, Medium 500, SemiBold 600 |
| **Ethnocentric Regular** | ALYGNR wordmark / logo only | Regular — never body use |

### Type Scale

| Scale name | Size | Weight | Font | Line-height | Usage |
|---|---|---|---|---|---|
| `display-xl` | 64px | Bold | Inter Tight | 1.05 | Marketing hero headlines |
| `display-lg` | 48px | Bold | Inter Tight | 1.1 | Section headlines, CTA screens |
| `display-md` | 36px | Bold | Inter Tight | 1.15 | Screen headlines, milestone copy |
| `display-sm` | 28px | Bold | Inter Tight | 1.2 | Page headings, wizard headlines |
| `heading-lg` | 22px | SemiBold | Inter Tight | 1.3 | Card headings, subsection titles |
| `heading-md` | 18px | SemiBold | Inter | 1.4 | Secondary headings |
| `body-lg` | 16px | Regular | Inter | 1.65 | Primary body copy, descriptions |
| `body-md` | 15px | Regular | Inter | 1.65 | Form field text, card body |
| `body-sm` | 14px | Regular | Inter | 1.6 | Supporting text, secondary labels |
| `label` | 12px–13px | Medium | Inter | 1.4 | Button text, UI labels |
| `eyebrow` | 10px–11px | Medium | Inter | 1.2 | Section eyebrows, step labels |
| `micro` | 11px | Regular | Inter | 1.4 | Timestamps, metadata, micro-copy |

### Eyebrow Label Rules

Every section eyebrow follows this exact spec. No exceptions.

```
Font: 10px–11px Inter Medium
Case: UPPERCASE
Letter-spacing: 0.10em–0.12em
Color on dark backgrounds: var(--orange)
Color on light backgrounds: var(--orange) for primary eyebrows,
                            var(--text-muted) for secondary labels
Prefix: 3px-wide orange vertical bar, height = cap height, sits 8px left of text
```

Example Tailwind equivalent:
```html
<div class="flex items-center gap-2">
  <div class="w-[3px] h-[14px] bg-[var(--orange)]"></div>
  <span class="text-[11px] font-medium uppercase tracking-[0.12em] text-[var(--orange)]">
    FOUNDATION
  </span>
</div>
```

### Section Label Rules (in-product — inside cards, above content fields)

```
Font: 10px Inter Medium
Case: UPPERCASE
Letter-spacing: 0.08em
Color: var(--text-muted) #9CA3AF
No prefix bar — distinct from eyebrows
Margin-bottom: 6px before the content it labels
```

---

## 3. Spacing & Layout

### Base Unit

All spacing uses multiples of 4px.

| Token name | Value | Usage |
|---|---|---|
| `space-1` | 4px | Micro gaps (icon to label, badge padding) |
| `space-2` | 8px | Internal component gaps |
| `space-3` | 12px | Tight section gaps |
| `space-4` | 16px | Standard gaps between elements |
| `space-6` | 24px | Gaps between card sections |
| `space-8` | 32px | Content padding inside panels |
| `space-12` | 48px | Section gaps in app |
| `space-16` | 64px | Major section breaks |
| `space-24` | 96px | Marketing section padding |

### Layout Grid

**Marketing website:** Max-width 1200px centered, 40px horizontal padding.  
**In-app:** Sidebar 220px fixed left + fluid content area. Max content width 1080px.  
**Modals:** Max-width 560px, centered, backdrop `rgba(0,0,0,0.6)`.  
**Onboarding (Foundation) screens:** No sidebar. Single centered column, max-width 560px.

### Border-radius Scale

| Value | Usage |
|---|---|
| 4px | Small badges, pills |
| 6px | Framework pills, small chips |
| 8px | Form inputs, buttons, small cards |
| 10px–12px | Standard cards, panels |
| 16px | Large feature cards |
| Full (9999px) | Status badges, avatar circles |

---

## 4. Component Library

### 4.1 Buttons

**Primary Button**
```
Background: #111318
Text: white
Border-radius: 8px
Height: 44px (large), 36px (medium), 32px (small)
Font: 14px Inter Medium
Padding: 0 20px (medium), 0 28px (large)
Hover: background #000000, transition 150ms
Active: scale 0.97, 100ms
Disabled: opacity 0.4, cursor not-allowed
```

**Orange CTA Button (marketing / end screens only)**
```
Background: #E8521A
Text: white
Border-radius: 8px
Height: 50px (hero), 44px (standard)
Font: 15px Inter Medium
Padding: 0 36px (hero), 0 24px (standard)
Hover: background #d44917, transition 150ms
Active: scale 0.97
Never use inside the product app — Primary Button for in-app CTAs.
```

**Secondary Button**
```
Background: transparent
Border: 1px solid #D1D5DB
Text: #374151
Border-radius: 8px
Height: 36px
Font: 13px Inter Medium
Hover: border-color #9CA3AF, background rgba(0,0,0,0.02)
```

**Destructive Button**
```
Background: transparent
Border: 1px solid #FECACA
Text: #DC2626
Border-radius: 8px
Height: 36px
Font: 13px Inter Medium
```

**Text Button (ghost)**
```
No background, no border
Text: #6B7280
Font: 13px Inter Regular
Hover: text-color #374151
Used for: "Save Draft", "Cancel", secondary actions
```

**Button Rules:**
- Never more than one Primary or Orange CTA button per screen.
- Button labels are actions, not descriptions. "Confirm Foundation →" not "Submit your Foundation to continue".
- Arrow suffix `→` on forward-navigation CTAs only.
- No exclamation marks in button labels ever.

---

### 4.2 Form Inputs (Document Feel)

The in-app editor experience is deliberately document-like, not form-like. Fields behave as text in a document until they need attention.

**Text Input — Standard**
```
Background: white
Border-radius: 8px
Border: 1px solid var(--border)  ← at rest
Focus: bottom border 2px solid var(--orange), all other borders transparent
       This creates the "underline on focus" document feel.
Hover: background rgba(0,0,0,0.01)
Height: 40px–44px
Padding: 0 12px
Font: 14px Inter Regular, var(--text-primary)
Placeholder: 14px Inter Regular, var(--text-muted)
```

**Text Input — Large / Headline**
```
Same as above, but:
Font: 18px–20px Inter Tight Medium
Height: 52px
Used for: Intent Name, primary headline fields
```

**Dropdown / Select**
```
Same shell as text input
Right-side: chevron-down icon, 16px, var(--text-muted)
Selected value: 14px Inter Regular, var(--text-primary)
Placeholder: var(--text-muted)
Dropdown panel: bg-white, border: 1px solid var(--border), border-radius 8px,
                box-shadow: 0 4px 24px rgba(0,0,0,0.08)
Option hover: bg-[#F9FAFB]
Option selected: bg-amber-50, orange left bar 3px
```

**Textarea / Long-form**
```
Same border behaviour as text input
Resize: vertical only
Min-height: 120px
Padding: 12px
Line-height: 1.65
```

**Field Label (section label format)**
```
10px Inter Medium, UPPERCASE, letter-spacing 0.08em, var(--text-muted)
Margin-bottom: 6px
Never floated, never placeholder-as-label
```

---

### 4.3 Cards

**Standard Card**
```
Background: #FFFFFF
Border: 1px solid var(--border) — NEVER box-shadow on in-app cards
Border-radius: 12px
Padding: 24px–32px
No elevation/shadow on light (app) surfaces.
```

**Dark Feature Card (marketing / CTA sections)**
```
Background: #1C1C1A
Border-radius: 12px
Padding: 40px
Hover: left border 3px solid var(--orange), translateY -4px, 180ms ease
No box-shadow.
```

**Framework Pill Card (used in Platform page)**
```
Background: var(--cream-deep) #E8E6DE
Border-radius: 8px
Padding: 20px 24px
Label: 16px Inter SemiBold, var(--text-primary)
Description: 14px Inter Regular, var(--text-secondary), line-height 1.6
```

**Card Rules:**
- In-app: always white background, always bordered, never shadowed.
- Marketing dark sections: dark-mid background, no border, hover lift.
- Never nest cards (card inside a card).
- Cards do not have a title bar with a different background — title is just bold text at the top of the card padding.

---

### 4.4 Status Badges

```css
/* Base */
text-xs font-medium px-2.5 py-0.5 rounded-full border

/* Draft */
bg-gray-100 text-gray-500 border-gray-200

/* Ready (submitted for review) */
bg-amber-50 text-amber-700 border-amber-200

/* Approved */
bg-green-50 text-green-700 border-green-200

/* Rejected */
bg-red-50 text-red-700 border-red-200
```

Status labels always use title case: "Draft", "Ready", "Approved", "Rejected".  
Never "IN REVIEW" (this status does not exist in v1).  
Never custom status names — only these four.

---

### 4.5 Sidebar Navigation

```
Width: 220px
Background: #0A0A0A
Height: full viewport
Position: fixed left

ALYGNR wordmark: top 20px, left 20px, 88px wide, white version

Nav section label (optional):
  10px Inter Medium, #4B5563, uppercase, letter-spacing 0.1em
  12px above first item, 8px below label

Nav item (each):
  Height: 36px
  Padding: 0 20px
  Font: 13px Inter Medium
  Icon: 16px, left of text, 10px gap
  Default: text #6B7280, icon #4B5563
  Hover: text #D1D5DB, background rgba(255,255,255,0.04)
  Active: text #F9FAFB, left border 3px solid #E8521A, background rgba(232,82,26,0.08)
  Active icon: #F9FAFB

Bottom of sidebar:
  Company workspace badge: avatar circle 28px, company name 12px Inter Medium #6B7280
  User initials in avatar: 11px Inter Medium #9CA3AF
```

**Sidebar rules:**
- Hidden on all Foundation onboarding screens.
- Always visible on all main app screens.
- Never collapses or toggles in v1.
- No section dividers — nav items flow continuously.

---

### 4.6 Progress Indicators

**Step Progress (wizard steps)**
```
Row of step pills, 8px gap.
Each pill: 28px height, 90px width, border-radius 9999px

Completed: bg-green-50, text-green-700, border-green-200, ✓ prefix
Active: bg-[#111318], text-white
Upcoming: bg-white, border: 1px solid var(--border), text-[#9CA3AF]
```

**Linear Progress Bar (onboarding steps 1 of N)**
```
Bar: 3px tall, border-radius 9999px
Track: #E5E7EB
Fill: #E8521A
Animated: width transition 400ms ease-out
Above bar: step label, 10px Inter Medium, var(--orange), uppercase
```

**GTM Readiness Score Arc**
```
SVG semi-circle arc
Outer diameter: 180px–220px (in card), 72px (compact/loading)
Stroke-width: 10px (full), 3px (compact)
Track colour: #F3F4F6 (light surface) or #2A2A28 (dark surface)
Fill colour: #E8521A
Score number: Inter Tight Bold, 36px (full), 18px (compact)
"out of 100" label: 11px Inter Regular, var(--text-muted)
```

**Loading Spinner (inline)**
```
Circle border, 2px, var(--orange) on top arc, transparent on remainder
Diameter: 12px (inline), 20px (full-screen)
Animation: spin 0.8s linear infinite
```

---

### 4.7 Scoring & Completeness Thresholds

Two distinct threshold states exist in Foundation:

```
Threshold 1 — "Ready to create assets" (minimum viable)
  Indicator: ✓ checkmark (green #16A34A)
  Badge: bg-amber-50, text-amber-700, border-amber-200, "Minimum viable"
  Meaning: primary offering + 1 value pillar + primary ICP + tone direction present

Threshold 2 — "Ready to run campaigns" (full completeness)
  Indicator: ✓ checkmark (green) when complete, ○ ring when incomplete
  Badge: bg-green-50, text-green-700, "Fully configured" (when complete)
  Meaning: full Foundation fields complete; Blueprint generation gated here
```

Both thresholds are always visible simultaneously on the Foundation setup screen.

---

## 5. Animation & Motion

### Principles

- Motion is functional. Every animation communicates state change, progress, or completion.
- Motion is never decorative. No looping idle animations on non-loading states.
- Transitions are short. The system feels fast and precise.
- Milestone moments earn a brief flourish. All other transitions are invisible.

### Easing Tokens

| Token | Value | Usage |
|---|---|---|
| `ease-out` | `cubic-bezier(0, 0, 0.2, 1)` | Elements entering the screen |
| `ease-in` | `cubic-bezier(0.4, 0, 1, 1)` | Elements leaving the screen |
| `ease-in-out` | `cubic-bezier(0.4, 0, 0.2, 1)` | State changes (tab switches, toggles) |
| `spring` | `cubic-bezier(0.34, 1.56, 0.64, 1)` | Milestone checkmarks and success indicators |

### Timing Tokens

| Token | Value | Usage |
|---|---|---|
| `duration-fast` | 150ms | Hover states, micro-transitions |
| `duration-base` | 200–220ms | Standard state changes, screen element fades |
| `duration-moderate` | 300ms | Screen-level transitions, panel entrances |
| `duration-slow` | 400ms | Progress bars, large animations |

### Standard Patterns

**Element entering a screen (staggered list)**
```
Initial: opacity 0, translateY +6px
Final: opacity 1, translateY 0
Duration: 220ms ease-out
Stagger: 80ms between items (maximum stagger: 5 items; after that, no stagger)
```

**Screen transition (between demo slides)**
```
Outgoing: opacity 1 → 0, translateY 0 → -4px, 180ms ease-in
Gap: 60ms
Incoming: opacity 0 → 1, translateY +8px → 0, 200ms ease-out
```

**Milestone icon (Foundation complete, first Intent set)**
```
Initial: scale 0, opacity 0
Final: scale 1, opacity 1
Duration: 300ms spring (cubic-bezier(0.34, 1.56, 0.64, 1))
Followed by: subtle background glow fade-in (300ms, rgba(232,82,26,0.08))
```

**Button click (simulated in demo)**
```
scale 1 → 0.97, 100ms ease-in
scale 0.97 → 1, 100ms ease-out
Then: screen transition begins
```

**Typing animation (form field)**
```
Characters insert one at a time: 80ms per character
Cursor blinks at insertion point: 500ms interval, opacity toggle
After completion: 300ms pause, then focus state appears (bottom border turns orange)
```

**Checklist row (loading screen)**
```
Active row: spinner appears, text colour lightens to #D1D5DB
Complete row: spinner morphs to ✓ (scale 0→1.2→1, 200ms spring), text goes white
Duration between rows activating: 700ms average
```

---

## 6. Onboarding / Foundation Screens

Foundation onboarding is distinct from the main app. It has its own visual register.

### Rules specific to Foundation screens

- No sidebar. Full viewport is available for the Foundation experience.
- Step progress indicator always present (linear bar, top of content column).
- Maximum content width: 560px centered.
- Background: `var(--cream)` for setup and review screens; `var(--black)` for loading and finish screens.
- The alternation between cream and black creates rhythm and marks distinct phases.
- Every screen has exactly one primary action button — no secondary CTAs competing with it.
- The Foundation review screen is the only screen with two columns (content + score).

### Foundation Screen Sequence

| Screen | Route | Background | Sidebar | Purpose |
|---|---|---|---|---|
| Setup | `/foundation/setup` | Cream | Hidden | URL + file input |
| Loading | `/foundation/loading` | Black | Hidden | Processing feedback |
| Review | `/foundation/review` | App grey | Hidden | Review + edit generated Foundation |
| Finish | `/foundation/finish` | Black | Hidden | Milestone acknowledgement |
| Post-onboarding | `/home` or `/intents/new` | App grey | Visible | First main app screen |

The sidebar appearing for the first time at the post-onboarding transition is intentional. It signals that the setup phase is over and the operating system has begun.

---

## 7. In-App Screens

### Header (sticky)

```
Height: 52px
Background: var(--app-bg) or white (content page)
Border-bottom: 1px solid var(--border)
Position: sticky, top 0, z-index 10
Content: left (page title or breadcrumb), right (page-level actions)
Page title: 14px Inter SemiBold, var(--text-primary)
Breadcrumb: 12px Inter Regular, var(--text-muted), " / " separator
```

### Page Layout

```
[Sidebar 220px] + [Content area]
Content area: padding 32px top and sides, max-width 1080px within
Cards arranged in vertical flow with 16px gap
```

### Empty States

Every empty state follows this exact copy pattern:

```
Icon: optional, 24px, var(--text-muted)
Headline: states what is absent — "No active intents."
Body: one instruction, what to do next — max 2 sentences.
CTA: one button only (if the user can take action from this screen)

Style: centered column, max-width 360px, within the empty card area
Text: headline 15px Inter SemiBold #374151, body 14px Inter Regular #6B7280
```

**Copy rule:** Empty states are instructions, not invitations. They do not say "Get started!" or "Let's go!" They state the situation and the next step.

### In-App Milestone Copy (use verbatim — do not paraphrase)

| Moment | Copy |
|---|---|
| Foundation completed | "Foundation complete. The system has a source of truth now — and so does everything you build from here." |
| First Strategic Intent created | "Intent set. Everything from here builds on this decision." |
| First play confirmed | "Play confirmed. You're building something with real structure now." |
| First asset generated | "First asset ready. The positioning, intent, and buyer context are all in there." |
| First asset approved | "Approved. The work is moving." |
| First export | "Out the door. Bring the results back when they come in." |
| Intent marked complete | "Intent closed. You ran the full loop. The next one starts better than this one did." |

Milestone copy appears in a transient banner: bg-[#111318], white text, 14px Inter Regular, 52px tall, slides in from top (translateY -52px → 0, 220ms ease-out), holds 3 seconds, slides back up.

### Error States

```
Message format: [What happened]. [What to do next].
Never: "Oops", "Sorry", passive voice, vague attribution.
Style: text-red-600, 13px Inter Regular
Position: below the field that caused the error, or in a banner at top of card.
```

---

## 8. Marketing Website Surfaces

The marketing website shares brand tokens but uses a distinct visual register from the app.

### Dark sections (primary)

```
Background: #0A0A0A
Headline: Inter Tight Bold, white, 52px–64px, line-height 1.05
Subhead: Inter Regular, #9CA3AF, 18px–20px, line-height 1.6
Eyebrow: orange, 11px, uppercase, letter-spacing 0.1em
```

### Light sections (contrast)

```
Background: #F7F7F5
Headline: Inter Tight Bold, #0A0A0A, 42px–52px
Subhead: Inter Regular, #6B7280, 17px–19px
```

### Section padding

```
Standard: 96px–128px top and bottom
Tight (between related sections): 64px
Max content width: 1080px
Horizontal padding: 40px (desktop), 24px (mobile)
```

### Scroll reveal (website)

Elements enter with: opacity 0 → 1, translateY +16px → 0, 400ms ease-out.  
Trigger: 100px before element enters viewport.  
Stagger for sibling groups: 100ms.

---

## 9. Logo & Brand Mark

### ALYGNR Wordmark

- Font: Ethnocentric Regular (logo only — never use for body copy)
- The `/` slash prefix is the orange diagonal element — a distinct brand mark
- Used in: app sidebar (white version), marketing site header (default or white), animation CTA screens
- Clear space: minimum equal to the height of the orange diagonal element on all sides
- Never placed on: crowded backgrounds, photos, gradients

### Logo Versions

| Version | Usage |
|---|---|
| Default (black wordmark + orange slash) | Light backgrounds |
| White (white wordmark + orange slash) | Dark backgrounds |
| Favicon (orange/black icon only) | Browser tab, small contexts |

### Logo Rules

- Never modify the logo. No recolouring, no stretching, no shadow.
- Never use only the wordmark text without the orange slash element.
- The orange slash prefix is not decorative — it is the brand mark.
- Minimum size: 72px wide (website), 80px wide (app sidebar).

---

## 10. Iconography

- Icon library: Lucide React (matches the existing frontend stack)
- Size: 16px (UI / nav), 18px (cards), 20px–24px (feature icons)
- Stroke-width: 1.5px standard, 2px for emphasis
- Colour: inherits from parent text colour — never hardcoded
- Never fill icons — always outline/stroke style
- No icon decorations, no icon backgrounds (except the milestone checkmark circle)

---

## 11. Voice & Copy Rules (applied to all UI strings)

These rules apply to every string in the product, website, animations, and emails.

### The 11 rules

1. Short sentences. 5–12 words primary.
2. Outcome-first. Lead with what changes for the user.
3. No softeners: never "helps", "enables", "allows", "empowers", "streamlines", "seamless".
4. State as facts. No hedging: not "might", "could", "potentially".
5. ALYGNR vocabulary only — see Terminology section below.
6. Never lead with the product name. Lead with the problem or outcome.
7. No exclamation marks in product or marketing copy.
8. Systems language, not feature language.
9. Never compare to "most teams" or "traditional methods."
10. Never justify or defend a feature in copy.
11. Banned words: empower, leverage (verb), streamline, unlock (generic), seamless, game-changer, revolutionary, disruptive, all-in-one, best-in-class, cutting-edge, easy to use.

### Terminology (non-negotiable)

**Always use:**
- "Strategic Intent" — never "Campaign", "Project", "Initiative"
- "GTM Play" / "GTM Plays"
- "Asset" — never "Content", "Material", "Piece"
- "Foundation" — both the onboarding flow and the living messaging document
- "Buyer Forces™" — ™ on first use in display contexts
- "GTM Readiness Score"
- "Value pillars" — never "value themes"
- "Orchestration" — never "automation" or "coordination"

**Retired — never use:**
- "Messaging Core"
- "Messaging Book"
- "Blueprint" — internal only, never user-facing
- "Mode 1" / "Mode 2"

**Internal only — never surface to users:**
- `DILIGENT_PLANNER`, `CAUTIOUS_PROTECTOR`, `TACTICAL_EXECUTOR`, `VISIONARY_CREATOR`
- "Blueprint Engine"
- "Dual-Axis GTM Readiness Scoring System"

---

## 12. Accessibility

- Minimum contrast: 4.5:1 for body text, 3:1 for large text (WCAG AA)
- Focus styles: always visible. Never `outline: none` without a custom focus style.
- Motion: respect `prefers-reduced-motion`. All animations should degrade to instant
  transitions when the user has reduced motion enabled.
- Semantic HTML: headings in order, labels associated to inputs, ARIA where native semantics
  are insufficient.
- Demo animations: `aria-hidden="true"` on the wrapper, `<p class="sr-only">` for screen reader
  description.

---

## 13. What This System Is Not

These anti-patterns are as important as the rules above.

- Not a content tool UI. No "write me a" interfaces. No prompt boxes presented as the primary action.
- Not a dashboard. ALYGNR does not lead with metrics and charts. It leads with work and action.
- Not a campaign manager. The unit of work is a Strategic Intent, not a "campaign".
- No stock photography. No generic icons in marketing. No gradient backgrounds.
- No crowded layouts. If a screen feels full, remove something before adding something.
- No floating tooltips on first visit. No onboarding tours that interrupt the first session.
  The Foundation flow IS the onboarding. Nothing else explains itself.
