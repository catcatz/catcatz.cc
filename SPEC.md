# catcatz.cc — Front Page Spec

**Version:** 1.0  
**Date:** 2026-06-10  
**Status:** Draft for review

## Goal

Create a clean, modern personal homepage for `catcatz.cc` that serves as a central hub showing all personal projects with easy shortcuts, similar to https://on9claw.com/.

## Design Direction

- Minimal, modern, slightly playful
- Dark theme preferred (with optional light toggle)
- Card-based project grid
- Smooth hover effects and subtle animations
- Fully responsive (mobile-first)
- Fast loading (minimal dependencies)

## Tech Stack

- Pure HTML + Tailwind CSS (via CDN)
- Vanilla JavaScript (no heavy framework)
- Single `index.html` file (no build step)
- Hosted via Caddy `file_server` at root of `catcatz.cc`

## Page Structure

### 1. Hero Section
- Big headline: "catcatz"
- Short tagline (e.g. "小強的玩意兒")
- Subtle scroll indicator

### 2. Projects Grid
Display projects as nice cards with:
- Project name
- Short description (1-2 lines)
- Tech / category tag
- "Open" button that links to the subfolder

**Initial Projects:**

| Project | Path | Description | Tag |
|---------|------|-------------|-----|
| AI English Tutor | `/tutor/` | Cantonese + English conversation practice with voice | AI / Language |
| Nagoya Travel | `/trip/` | Nagoya trip planner & food guide | Travel |

### 3. Footer
- Simple copyright
- Link to GitHub (optional)
- "Built with Caddy + Cloudflare Tunnel"

## Future Extensibility

- Easy to add new project cards (just add one more `<div>` in the grid)
- Support for both internal subfolder links and external links
- Optional: status badges (e.g. "Live", "WIP")

## Non-Goals (v1)

- No backend / API
- No user authentication
- No analytics
- No complex animations or 3D effects

## Acceptance Criteria

- [ ] Page loads under 1s on 4G
- [ ] Looks good on mobile (320px+)
- [ ] All project cards clickable and correct
- [ ] Dark theme, clean typography
- [ ] Works behind Cloudflare Tunnel + Caddy

## Next Steps (after approval)

1. Create `index.html` based on this spec
2. Update Caddyfile to serve this at root
3. Deploy and test on `https://catcatz.cc`
4. Add more projects later via simple PRs

---
**Review Checklist for 小強:**
- 設計方向 OK 嗎？
- Projects 描述同 tag 滿唔滿意？
- 有冇想加/改嘅項目？
- 想用 light theme 定 dark theme 定兩樣都有？