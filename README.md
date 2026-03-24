# Gooder - Brand Tone & Voice Skills

> Train your brand voice from real documents. Write on-brand copy across every channel. Validate automatically.

Gooder is a skill suite for Claude that turns your brand guidelines into a working voice system. Upload your docs, get three skills back, and every piece of copy — email, SMS, push, UX, social — comes out on-brand and validated.

## Quick Start

1. Download the `.skill` files from [Releases](https://github.com/Rinielg/gooder/releases)
2. Install the three base skills (see [Install Guide](INSTALL.md))
3. Train your brand:

```
Train a brand voice for [Your Brand]
```

4. Start writing:

```
Write a welcome email for [Your Brand]
```

That's it. The skills chain automatically — voice activates, copy generates, validation runs, UX best practices apply when needed.

---

## What's in the box

Gooder ships as **three base skills** that work together:

| Skill | What it does |
|-------|-------------|
| **gooder-brand-tone-voice** | Trains your brand from uploaded docs (PDF, DOCX, images, URLs, pasted text). Generates three brand-specific skills per brand. |
| **gooder-tone-validator** | Scores every piece of copy across 8 weighted dimensions. Auto-runs after generation. Flags issues by severity. |
| **gooder-ux-guide** | UX writing framework grounded in NNGroup, Baymard, Fogg Model, and 14 component patterns. Layers brand voice on top. |

When you train a brand, the trainer generates **three additional skills** customized to that brand:

| Generated skill | What it contains |
|----------------|-----------------|
| **gooder-voice-[brand]** | Full voice profile — pillars, archetype, spectrum, tone map, golden examples, vocabulary, headline formulas |
| **gooder-audience-[brand]** | Pre-populated audience segments with tone adjustments, vocabulary shifts, and example copy per tier |
| **gooder-platform-[brand]** | Channel rules — character limits, format requirements, emoji usage, CTA style — with brand-specific overrides |

**3 base skills + 3 per brand.** Two brands = 9 total. Three brands = 12.

---

## How it works

```
Upload brand docs → Train → Write → Validate
```

**Train** — Upload brand guidelines, existing copy, tone of voice documents, or even screenshots. The trainer extracts voice pillars, archetype, vocabulary preferences, audience segments, and channel behaviors. It scores completeness and asks targeted follow-ups if gaps exist.

**Write** — Ask for any type of copy. The trained voice skill activates automatically. If you specify an audience segment, the audience engine adjusts tone. If you're writing for a specific channel, platform rules enforce constraints.

**Validate** — After every piece of copy, the tone validator runs automatically. It scores across 8 dimensions (voice consistency, tone accuracy, compliance, terminology, platform optimization, objective alignment, pattern adherence, overall quality) and flags issues by severity: `INFO`, `WARNING`, `FAIL`, or `AUTOMATIC FAIL`.

**UX Guide** — For UX copy requests (onboarding, error states, CTAs, forms, modals, tooltips), the UX guide activates alongside the brand voice. It applies behavioral psychology principles first, then layers your brand voice on top.

---

## Supported channels

Email · SMS · Push notifications · WhatsApp · In-app UX · Social media · Advertising · Landing pages

Each channel has industry-standard defaults. When you train a brand, channel-specific behaviors from your materials override those defaults automatically.

---

## Validation scoring

The validator scores copy across 8 weighted dimensions:

| Dimension | Weight | What it checks |
|-----------|--------|---------------|
| Voice Consistency | 20% | Brand pillars expressed, anti-patterns absent, preferred vocabulary |
| Compliance | 20% | Tone rules, prohibited language, required disclosures |
| Tone Accuracy | 15% | Situational tone match, audience calibration |
| Terminology | 10% | Canonical terms, deprecated terms, capitalization |
| Platform Optimization | 10% | Length, format, structure for the channel |
| Objective Alignment | 10% | Business goal alignment |
| Pattern Adherence | 10% | Headline formulas, structural patterns |
| Overall Quality | 5% | Readability, grammar, clarity |

**Pass threshold: 75/100.** Compliance below 7/10 is an automatic fail regardless of overall score.

---

## Commands

### Brand training
```
Train a brand voice for [Brand Name]
```
```
Retrain [Brand] — upload updated materials alongside existing .skill files
```

### Writing
```
Write a welcome email for [Brand]
Write VIP push notification for [Brand]
Write onboarding flow for [Brand]
```

### Validation
| Command | Action |
|---------|--------|
| `/validate` | Manual validation |
| `/tone-check` | Quick validate last copy |
| `/full-report` | Detailed scoring breakdown |
| `/rewrite-flags` | Rewrite all flagged sections |
| `skip tone check` | Suppress validation once |
| `pause auto-validation` | Suppress until re-enabled |

### UX writing
| Command | Action |
|---------|--------|
| `/ux-guide` | Start UX guide |
| `/ux-write [component]` | Write specific component |
| `/ux-review` | Review existing copy |
| `/ux-audit` | Audit a user flow |
| `/ux-variants` | Generate A/B variants |

### Audience
| Command | Action |
|---------|--------|
| `/persona [Segment]` | Activate a specific segment |
| `/compare-segments` | Same copy across all segments |
| `/add-segment` | Add a new audience segment |

---

## Multi-brand support

Each brand gets its own namespaced set of skills:

```
gooder-voice-acme-corp
gooder-audience-acme-corp
gooder-platform-acme-corp
```

Claude detects which brand to use from context, or you specify with `/voice-[brand]`. Audience and platform skills for that brand activate automatically.

---

## Installation

See [INSTALL.md](INSTALL.md) for setup instructions.

---

## File structure

```
gooder/
├── gooder-brand-tone-voice/
│   ├── SKILL.md              # Brand trainer
│   └── references/
│       ├── voice-template.md
│       ├── audience-template.md
│       └── platform-template.md
├── gooder-tone-validator/
│   └── SKILL.md              # Copy validator
├── gooder-ux-guide/
│   ├── SKILL.md              # UX writing guide
│   └── references/
│       ├── component-frameworks.md
│       └── psychology-accessibility.md
└── INSTALL.md
```

After training a brand, you'll also have:

```
gooder-voice-[brand]/
├── SKILL.md
└── references/          # Golden examples, channel-specific copy
gooder-audience-[brand]/
└── SKILL.md
gooder-platform-[brand]/
└── SKILL.md
```

---

## License

Proprietary. See [LICENSE](LICENSE) for terms.

---

<p align="center">
  Built by <strong>Gooder</strong> — making every word work harder for your brand.
</p>
