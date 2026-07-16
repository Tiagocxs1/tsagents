# Typography Audit & Fix

Use when the user says "typography is not good", "fonts look bad", "fix typography", "improve readability", "text doesn't look right", or asks to audit and fix font/typography issues across a project.

## Core Principles (sourced from 20+ typography experts)

1. **Measure (line length):** 45-75 characters per line, 66 is ideal. Content wider than `max-w-2xl` (42rem = ~65 chars at 16px) is too wide.
2. **Leading (line-height):** Body text = 1.5-1.8x font-size. Never below 1.5 for paragraphs of 3+ lines. `leading-relaxed` (1.625) is the professional default.
3. **Hierarchy:** Use max 2-3 typefaces. A secondary display/serif font for headings creates contrast vs sans-serif body.
4. **Widows & Orphans:** Use `text-balance` on all headings (h1-h3). Use `text-pretty` on body paragraphs. Never leave a single word alone on the last line.
5. **Color Contrast:** Body text needs 7:1+ (WCAG AAA). Muted text needs 4.5:1+ (WCAG AA). Emerald/colored text on dark backgrounds often fails.
6. **Scale:** Use a modular type scale (1.25 or 1.333 ratio). Avoid skipping steps.
7. **Gutter (paragraph spacing):** Should equal line-height. For 16px text with 1.5 leading = 24px. The project's `space-y-6` is correct.
8. **White space:** Typography needs breathing room. Tight spacing = amateur.
9. **Variable fonts:** Configure `axes` properly when using `next/font/google` variable fonts.
10. **No stretching:** Never stretch/compress font glyphs. Choose a condensed family instead.

## Workflow

### Phase 1: Audit
Run against the project to find:
- Line length violations (containers wider than 42rem for text)
- Missing text-balance/text-pretty on headings and body
- Tight line-height (below 1.5 for body)
- Single typeface usage (no secondary font)
- Undefined or broken font classes
- Borderline contrast ratios
- Missing variable axes config

### Phase 2: Fix (Priority Order)
0. Add a display/secondary typeface (e.g., Instrument Serif, Playfair Display) for headings
1. Fix line length: change text containers to `max-w-2xl` or `max-w-prose`
2. Add `text-balance` to h1-h3, `text-pretty` to body text
3. Set body line-height to `leading-relaxed` (1.625)
4. Remove undefined classes (`text-title`, `text-caption`)
5. Fix borderline contrast (muted-foreground on muted backgrounds)
6. Configure variable font axes

### Phase 3: Verify
- Build must pass with zero errors
- Visual check on mobile and desktop
- Verify no widows/orphans in key sections
