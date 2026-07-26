# Profile README — Development Guide

A comprehensive guide for maintaining and customizing this GitHub Profile repository.

## Repository Structure

```
fadd3079-prog/
├── README.md                    # Main profile page
├── LICENSE                      # MIT License
├── assets/
│   └── svg/
│       ├── divider.svg          # Section divider (gradient line)
│       ├── divider-thin.svg     # Sub-section divider (subtle line)
│       └── footer-wave.svg      # Decorative footer wave
├── .github/
│   └── workflows/
│       ├── snake.yml            # Daily snake contribution animation
│       └── metrics.yml          # Weekly profile metrics
└── docs/
    ├── README-DEVELOPMENT.md    # This file
    ├── README-ASSETS.md         # Asset catalog and usage
    └── CONTRIBUTING.md          # Contribution guidelines
```

## Design Principles

1. **GitHub-Compatible Only** — No inline `style` attributes (GitHub strips them). All visual design uses SVG images, badge services, or native Markdown.
2. **Dark & Minimal** — Color palette: `#0F766E` (primary teal), `#111827` (dark), `#334155` (gray), `#F8FAFC` (white).
3. **Curated Content** — Show only relevant technologies, projects, and metrics. Quality over quantity.
4. **Maintainability** — Modular structure, clear comments, and documented patterns.

## External Services

| Service | URL | Purpose |
|---------|-----|---------|
| Capsule Render | `capsule-render.vercel.app` | Animated header and footer banners |
| Readme Typing SVG | `readme-typing-svg.demolab.com` | Animated typing text |
| Shields.io | `img.shields.io` | Badge generation |
| Skill Icons | `skillicons.dev` | Technology stack icons |
| GitHub Readme Streak Stats | `github-readme-streak-stats.herokuapp.com` | Streak counter |
| GitHub Profile Summary Cards | `github-profile-summary-cards.vercel.app` | Stats, languages, activity |
| GitHub Readme Activity Graph | `github-readme-activity-graph.vercel.app` | Contribution activity graph |
| Komarev Profile Views | `komarev.com/ghpvc` | Visitor counter |
| Platane/snk | GitHub Action | Snake contribution animation |
| lowlighter/metrics | GitHub Action | Comprehensive metrics SVG |

## Customization Guide

### Changing Colors

The primary teal color `#0F766E` appears in:
- Badge `color` and `logoColor` parameters in shields.io URLs
- Capsule Render `color` gradient stops
- Typing SVG `color` parameter
- Streak Stats `ring`, `fire`, and `currStreakLabel` parameters
- Activity Graph `color`, `line` parameters
- SVG asset fills in `assets/svg/`

To change the accent color, search and replace `0F766E` across all files.

The dark background `#111827` appears in badge `labelColor` and capsule render gradients.

### Adding a New Project Card

Add a new `<td>` element inside the projects `<table>`:

```html
<td width="50%" valign="top">
  <h3>Project Name</h3>
  <p>Brief description of the project.</p>
  <strong>Highlights</strong>
  <ul>
    <li>Feature one</li>
    <li>Feature two</li>
  </ul>
  <a href="https://github.com/fadd3079-prog/repo-name">
    <img src="https://img.shields.io/badge/Repository-111827?style=for-the-badge&logo=github&logoColor=F8FAFC" alt="Repository" />
  </a>
</td>
```

For more than two projects, add additional `<tr>` rows.

### Adding a Tech Stack Category

Add a new block in the Tech Stack section:

```markdown
**Category Name**

<img src="https://skillicons.dev/icons?i=icon1,icon2,icon3&perline=13" alt="Category" />
```

Available icons: [skillicons.dev](https://skillicons.dev)

### Updating Social Links

Social badges appear in two places: the hero section and the connect section. Update both when changing links.

## Workflow Management

### Snake Animation (`snake.yml`)

- **Schedule**: Daily at 00:00 UTC
- **Trigger**: Also supports manual dispatch
- **Output**: Deploys SVGs to the `output` branch
- **Referenced as**: `https://raw.githubusercontent.com/fadd3079-prog/fadd3079-prog/output/github-snake-dark.svg`

### Profile Metrics (`metrics.yml`)

- **Schedule**: Weekly on Sundays at 06:00 UTC
- **Trigger**: Also supports manual dispatch
- **Requires**: `METRICS_TOKEN` repository secret (personal access token with `read:user` scope)
- **Output**: Deploys to the `output` branch

#### Setting Up the Metrics Token

1. Go to [GitHub Settings → Developer Settings → Personal Access Tokens](https://github.com/settings/tokens)
2. Generate a new token with `read:user` scope
3. Go to your profile repository → Settings → Secrets and variables → Actions
4. Add a new secret named `METRICS_TOKEN` with the token value

## Local Preview

Preview `README.md` using:
- VS Code with the Markdown Preview extension
- GitHub itself (push to a branch and preview)
- Any Markdown renderer that supports HTML

> **Note**: Some elements (badge images, external service renders) will only display correctly when viewed on GitHub or with an internet connection.

## Maintenance Checklist

- [ ] Update project cards when new work ships
- [ ] Curate tech stack as skills evolve
- [ ] Verify all external service URLs periodically
- [ ] Check that GitHub Actions are running successfully
- [ ] Keep social links current
