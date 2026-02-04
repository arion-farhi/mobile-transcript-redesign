# swivl Mobile Transcript Redesign

## Context
Redesigning swivl's transcript review page for mobile. swivl is an AI-powered omni-channel platform (web, SMS, voice) for self-storage operators.

**The Problem:**
Customer conversation transcript is nearly impossible to read on mobile — text appears as one word per line, making it frustrating for operators who need to review conversations on their phones.

**Current Mobile UX Issues:**
- No mobile stacking (retains desktop side-by-side layout)
- Message container ~1/3 of screen (too narrow)
- Non-native channel selector (cut off, hard to tap)
- Footer content overflow

**Target Users:** Operators reviewing transcripts on mobile devices

**Reference Materials:**
- tryswivl.com (design language, desktop UI patterns)
- See `reference-screenshot.png` for current mobile state
- See `transcript-data.txt` for sample conversation data

## Role
Senior frontend engineer with product thinking and expert mobile UI/UX understanding (readability, accessiblity, mobile-first design). Focus on solving real user pain points, not just aesthetics. 

## Instructions
**Development Approach:**
Build incrementally. Complete and validate each feature or layout before moving to the next.

**Build three layout options, each optimized for a specific use case:**

1. **Chat View** (default) --> Deep Review use case
   - Bubble UI matching swivl desktop pattern
   - Familiar mental model (iMessage, WhatsApp)
   - Clear speaker distinction via alignment + color

2. **List View** --> Quick Check use case
   - Compact, scannable format
   - Timestamps visible inline
   - Higher information density

3. **Raw View** --> Export use case
   - Plain text, copy-ready format
   - One-tap copy button
   - No formatting to strip

**Channel Filter:**
- Voice — primary phone conversation (13 messages)
- SMS — follow-up text with lock portal link (1 message)
- Web — empty for this conversation (show empty state)
- All — Voice + SMS merged chronologically (SMS inserted after "I just sent a text message")

**Additional Features:**
- AI Summary (collapsible accordion)
- Channel filter (All / Voice / SMS / Web)
- Layout toggle (Chat / List / Raw)
- Scroll-to-bottom button

## Specifics
**Tech:**
- Single HTML file with inline CSS/JS
- Tailwind CSS via CDN
- Vanilla JavaScript
- No build step required

**swivl Design Language:**
- swivl orange `#F97316` for accents, labels, interactive elements
- swivl cream `#FEF3E2` for AI message bubbles (readable, on-brand)
- Gray `#E5E7EB` for customer messages
- swivl logo in header (from tryswivl.com)

**Mobile-First UI/UX Requirements:**
- Native `<select>` over custom dropdowns
- 44px minimum touch targets (accessibility)
- 16px base font size
- 1.5 line-height (readability)
- 4.5:1 contrast ratio (WCAG)
- Follow other mobile UI/UX best practices when applicable
- Smooth transition animations between layouts

**Documentation Standards:**
- Extensive inline comments explaining code and design decisions
- Descriptive function/variable naming
- Logical code sections with comment headers

## Pitfalls
- Do NOT use frameworks requiring build steps
- Do NOT sacrifice usability for aesthetics
- Do NOT make layouts feel disconnected — share consistent UX foundation
- Do NOT use placeholder content — use transcript data from `transcript-data.txt`
- Do NOT forget accessibility (touch targets, contrast, font size)