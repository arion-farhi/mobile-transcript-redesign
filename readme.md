# swivl Mobile Transcript Redesign

A mobile-first redesign of swivl's transcript review page, built as a Claude Code exercise demonstrating AI-assisted frontend development.

## Project Overview

**Problem:** Operators couldn't effectively review AI conversation transcripts on mobile devices. Text appeared as one word per line, the message container was only 1/3 of the screen, and the channel selector was cut off.

**Solution:** Three layout options optimized for different use cases:
- **Chat View** — Deep review (comprehension over speed)
- **List View** — Quick check (speed over comprehension)
- **Raw View** — Export (copy/paste to emails, tickets, docs)

## Files Included

```
├── CLAUDE.md              # Project context and constraints for Claude Code
├── swivl.html             # Working demo with all three layouts
├── llm-conversation.md    # Development conversation log (23 prompts)
├── README.md              # This file
└── images/
    └── swivl.png          # Favicon
```

## CLAUDE.md Development

The CLAUDE.md file was developed before implementation using the **CRISP framework**:

- **Context** — Problem statement, current issues, target users
- **Role** — Senior frontend engineer with product thinking and mobile UI/UX expertise
- **Instructions** — Three layouts with specific use cases, channel filter requirements
- **Specifics** — Tech stack, design language, accessibility requirements
- **Pitfalls** — Explicit constraints to avoid common mistakes

**Key principle:** Keep it concise (<100 lines) to avoid wasting context window tokens. Front-load critical constraints and let Claude ask clarifying questions rather than over-specifying upfront.

## Tech Stack Decision

**Choice:** Single HTML file with Tailwind via CDN, React via CDN, vanilla JavaScript

**Why this approach:**
- No build step means it opens directly in any browser (ideal for demo)
- Single file is portable and easy to share
- Fast iteration with no compile time
- Challenge is about mobile design, not infrastructure

**In production, I would use:**
- React/Next.js with TypeScript for type safety
- Proper build pipeline with bundling and minification
- Modular component architecture
- Unit and integration tests

## LLM Collaboration Strategy

### Prompting Techniques

**Context-first prompting** — Started by having Claude read CLAUDE.md and transcript-data.txt, confirm understanding, and ask clarifying questions before writing any code.

**Chain of thought** — For complex features, asked Claude to walk through its plan before implementation. Examples: bubble styling approach (Prompt 4), List View trade-offs (Prompt 7).

**Tree of thought** — For decisions with multiple valid approaches, had Claude evaluate options and pick the best. Examples: Raw View text format (Prompt 10), accordion animation technique (Prompt 16).

**Scoped iterations** — One feature at a time with validation between each. Built foundation first, then each layout individually, then shared features, then polish.

**Self-critique** — Asked Claude to audit its own work. Examples: accessibility check (Prompt 21), UX consistency verification (Prompt 23).

**Progressive refinement** — Built in phases: foundation → layouts → features → polish. Each phase validated before moving to the next.

### Multi-Model Validation

Gemini 2.0 was used periodically to cross-check UI/UX decisions and verify accessibility compliance.

### Presentation Development

Claude was also used in a separate session to structure the presentation narrative, refine slide content, and develop the rollout strategy.

## Code Structure

The demo is organized into sections:

```
1. External Dependencies (React, Tailwind via CDN)
2. Tailwind Configuration (swivl brand colors)
3. Custom Styles (animations, native select, accordion)
4. Transcript Data (conversation organized by channel)
5. Utility Components (ScrollButton, EmptyState, Footer)
6. Layout Components (ChatLayout, ListLayout, RawLayout)
7. Feature Components (AISummary, SettingsDropdown)
8. Main App Component (state management, routing)
```

Each layout component includes comments documenting:
- **Use case** it's optimized for
- **Trade-offs** compared to other layouts
- **Key design decisions** and rationale

## Design Decisions

| Decision | Rationale |
|----------|-----------|
| Native `<select>` | Better mobile UX, accessibility, and performance than custom dropdowns |
| CSS Grid accordion | Smooth height animation without JavaScript DOM measurement |
| Staggered animations | Perceived performance improvement on channel switch |
| 44px touch targets | WCAG accessibility requirement for mobile |
| swivl cream for AI bubbles | Orange background would hurt readability; cream maintains brand while being readable |
| 14px font in Raw View | Intentional for `<pre>` block displaying plain text, distinct from conversational layouts |

## Running the Demo

Open `swivl.html` in any modern browser. No installation or build step required.

For mobile testing:
1. Open in Chrome DevTools (Cmd+Opt+I → Cmd+Shift+M)
2. Select iPhone or Android device preset
3. Or serve locally and test on actual device

## Author

**Arion Farhi**  
arionfarhi@gmail.com