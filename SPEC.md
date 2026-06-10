# catcatz.cc — Front Page Spec

**Version:** 2.0
**Date:** 2026-06-10
**Status:** Approved — Ready for implementation

## Goal

Create a terminal / retro-futuristic personal homepage for `catcatz.cc` that serves as a central hub showing all personal projects, styled like https://on9claw.com/.

## Design Direction

- **Terminal / hacker aesthetic** — monospace fonts, dark background, neon accent colors
- **Boot-sequence intro** — fake terminal boot log / status output as hero section
- **Project listing** — `ls`-style directory listing with emoji icons, descriptions, and colored status badges
- **System status bar** — show uptime, project count, etc. (static for v1)
- **Command-prompt footer** — connection info line at bottom
- Fully responsive (mobile-first), but keep terminal vibe on all screen sizes
- Fast loading (minimal dependencies)

## Color Palette

| Element | Color |
|---------|-------|
| Background | Deep black `#0a0a0a` |
| Primary text | White / light grey |
| Accent (title/links) | Neon cyan `#00ffff` |
| Status: LIVE/READY | Green `#00ff00` |
| Status: BETA/WIP | Yellow/amber `#ffaa00` |
| Dim text (paths, prompts) | Grey `#888888` |

## Tech Stack

- Pure HTML + Tailwind CSS (via CDN)
- Vanilla JavaScript (no heavy framework)
- Single `index.html` file (no build step)
- Hosted via Caddy `file_server` at root of `catcatz.cc`
- Monospace font: JetBrains Mono (via Google Fonts) or system monospace fallback

## Page Structure

### 1. Top Panel — Boot Sequence
- Fake terminal window with macOS-style window controls (red/yellow/green dots)
- Title: **"catcatZ"** in large neon cyan text
- Subtitle: "catcatZ の HomeLab"
- Fake boot log lines (e.g. `[OK] Initializing kernel modules...`, `[OK] SSH daemon listening on :22`)
- Ends with a command prompt: `./status.sh`

### 2. System Status Bar
- Horizontal strip showing:
  - STATUS: ONLINE (green)
  - PROJECTS: <count>
  - NODE: hkg (Hong Kong)

### 3. Project Listing
- Header: `# /home/catcatz/projects`
- `ls -la` style listing. Each row is a **full clickable link** with:
  - Emoji icon
  - Project name (e.g. `ai-english-tutor`)
  - Short description
  - Colored status badge on the right

**Initial Projects:**

| Emoji | Project | Link | Description | Status |
|-------|---------|------|-------------|--------|
| 🗣️ | ai-english-tutor | `/tutor/` | Cantonese + English voice conversation practice | READY |
| 🍜 | nagoya-travel | `/trip/` | Nagoya trip planner & food guide | WIP |

### 4. Footer
- Command-prompt style line:
  `[catcatz@homelab] ~ connection: secure | node: hkg | catcatz.cc`

## Future Extensibility

- Add new projects by adding one more `<a>` row to the listing
- Status badges can be updated per project
- Support for both internal subfolder links and external links
- Optional: real system stats from API (v2)

## Non-Goals (v1)

- No backend / API
- No user authentication
- No analytics
- No real-time system stats (static data only)
- No contact/social links
- No infrastructure exposure (no mention of Caddy/Cloudflare)

## Acceptance Criteria

- [ ] Page loads under 1s on 4G
- [ ] Terminal aesthetic maintained on mobile (320px+)
- [ ] All project rows clickable and correct
- [ ] Dark theme, monospace typography
- [ ] Status badges visible and color-coded
- [ ] Works behind Cloudflare Tunnel + Caddy

## Changes from v1 → v2

| Change | v1 | v2 |
|--------|----|----|
| Design style | Card-based minimal | Terminal / hacker (on9claw) |
| Project display | Card grid | `ls -la` listing |
| Status badges | Future (v2) | Included in v1 |
| Tagline | 小強的玩意兒 | catcatZ の HomeLab |
| Footer infra line | Included | Removed |
| Contact links | Not mentioned | Explicitly excluded |
| Row behavior | "Open" button | Entire row clickable |

## Next Steps

1. Create `index.html` based on this spec
2. Update Caddyfile to serve `file_server` at root
3. Deploy and test on `https://catcatz.cc`
4. Add more projects later by adding rows
