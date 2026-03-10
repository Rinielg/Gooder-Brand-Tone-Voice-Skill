<p align="center">
  <img src="https://img.shields.io/badge/version-1.0.0-blue" alt="Version 1.0.0" />
  <img src="https://img.shields.io/badge/platform-Claude%20Code-8A2BE2" alt="Claude Code" />
  <img src="https://img.shields.io/badge/skills-3-green" alt="3 Skills" />
  <img src="https://img.shields.io/badge/license-proprietary-lightgrey" alt="License" />
</p>

# Gooder — Brand Voice Skills for Claude Code

**Train your brand voice from real documents. Validate every piece of copy automatically. Write UX copy grounded in behavioral science - all in your brand's voice.**

Gooder is a three-skill system that turns Claude Code into a brand-aware writing and QA partner. Upload your brand guidelines, style guides, or marketing materials, and Gooder extracts a structured voice profile that persists across sessions. From that point on, everything Claude writes gets scored against your brand — and every UX writing request draws on 900+ lines of research-backed frameworks covering onboarding, error states, CTAs, forms, modals, notifications, and more.

---

## Table of Contents

- [Why Gooder](#why-gooder)
- [How It Works](#how-it-works)
- [The Three Skills](#the-three-skills)
  - [1. Brand Tone & Voice Trainer](#1-brand-tone--voice-trainer)
  - [2. Tone Validator](#2-tone-validator)
  - [3. UX Writing Guide](#3-ux-writing-guide)
- [Skill Architecture](#skill-architecture)
- [Installation](#installation)
- [Usage](#usage)
  - [Training a Brand Profile](#training-a-brand-profile)
  - [Validating Copy](#validating-copy)
  - [Writing UX Copy](#writing-ux-copy)
  - [Recommended Workflow](#recommended-workflow)
- [Brand Profile Schema](#brand-profile-schema)
- [Validation Scoring System](#validation-scoring-system)
- [UX Component Coverage](#ux-component-coverage)
- [Multi-Brand Support](#multi-brand-support)
- [Requirements](#requirements)
- [File Structure](#file-structure)
- [FAQ](#faq)
- [Contributing](#contributing)
- [License](#license)

---

## Why Gooder

Every team that produces copy at scale hits the same wall: the brand guidelines live in a PDF that nobody opens, new writers guess at the voice, and QA is a subjective review that catches some issues and misses others. AI writing tools make this worse, not better — they generate fluent copy that sounds like every other brand.

Gooder solves this with a system-level approach:

- **Voice becomes data.** Your brand guidelines, marketing materials, and website copy get extracted into a structured profile with scored dimensions, pillar definitions, tone maps, grammar rules, and terminology tables — not a vague prompt, but a machine-readable voice specification.
- **Validation is automatic.** Once a profile exists, Claude scores every piece of copy it writes across 8 weighted dimensions before you see it. No manual QA step. No "does this feel right?" — you get a number, a pass/fail, and actionable flags.
- **UX writing is grounded in research.** The UX guide isn't a template library. It's a comprehensive framework built on findings from Nielsen Norman Group, Baymard Institute, Google Material Design, Apple HIG, Shopify Polaris, the Fogg Behavior Model, and hundreds of documented A/B tests. Your brand voice gets layered on top of proven patterns, not thrown at a blank page.

---

## How It Works

```
┌─────────────────────┐      ┌────────────────────┐      ┌─────────────────────┐
│   Brand Materials    │      │   Brand Profile     │      │   Validated Copy     │
│                      │      │                     │      │                      │
│  PDFs, DOCX, TXT,   │─────▶│  Voice pillars,     │─────▶│  Scored against 8    │
│  HTML, images, URLs  │      │  tone maps, grammar │      │  dimensions with     │
│                      │      │  rules, terminology │      │  severity flags      │
└─────────────────────┘      └────────┬────────────┘      └─────────────────────┘
                                      │
                              ┌───────▼───────┐
                              │  UX Writing    │
                              │                │
                              │  Research-      │
                              │  backed copy    │
                              │  in your voice  │
                              └────────────────┘
```

1. **Train** — Feed your brand documents into the Brand Tone & Voice Trainer. It extracts voice pillars, archetype, tone architecture, grammar preferences, channel adaptation rules, and terminology into a persistent markdown profile.
2. **Write** — Use the UX Writing Guide for any screen or component. It applies behavioral psychology frameworks and UX best practices, then layers your brand voice on top.
3. **Validate** — The Tone Validator scores output across 8 weighted dimensions, flags issues by severity, and offers targeted rewrites. This runs automatically after training — you don't have to ask for it.

---

## The Three Skills

### 1. Brand Tone & Voice Trainer

**Skill name:** `gooder-brand-tone-voice`

Extracts brand voice patterns from source materials and builds a structured profile file using the BVST-2026 schema.

**What it accepts:**
- PDF, DOCX, TXT, HTML files
- PNG and JPG images (analyses visual design language, typography, and personality signals)
- Web URLs (fetches and analyses page content)
- Pasted text directly in chat

**What it extracts:**

| Profile Section | What's Captured |
|----------------|----------------|
| **Voice Pillars** | 3–5 named pillars with meaning, examples, anti-patterns, and dial ranges |
| **Brand Archetype** | Primary and secondary archetype with description and example phrasing |
| **Voice Spectrum** | 5-axis scoring: formality, seriousness, technicality, enthusiasm, authority |
| **Situational Tone Map** | 3–5 context-specific tone prescriptions (onboarding, errors, celebration, etc.) |
| **Grammar & Style** | Voice, tense, person, contractions, sentence length, punctuation, capitalisation |
| **Channel Adaptation** | Per-channel guidance for email, SMS, push notifications, and UX copy |
| **Terminology** | Canonical terms, competitor terms to avoid, product names with capitalisation |

**Completeness scoring:** Each section contributes weighted points to a 100-point completeness score. The skill requires 80+ to activate the profile and runs targeted follow-up questions to fill gaps.

**Companion skill activation:** Once a profile reaches 80%+, the validator and UX guide activate automatically for that brand. Claude scores every piece of copy it writes and applies UX frameworks with the brand voice — no manual invocation required.

---

### 2. Tone Validator

**Skill name:** `gooder-tone-validator`

Independently scores any piece of copy against a trained brand profile across 8 weighted dimensions.

**Scoring dimensions:**

| Dimension | Weight | What It Measures |
|-----------|--------|-----------------|
| Voice Consistency | 20% | Are voice pillars expressed? Anti-patterns avoided? |
| Tone Accuracy | 15% | Does the tone match the situation and emotional context? |
| Compliance | 20% | Are all tone rules, grammar rules, and required disclosures followed? |
| Terminology | 10% | Canonical terms used correctly? Competitor terms absent? |
| Platform Optimisation | 10% | Does length, format, and structure match the content type? |
| Objective Alignment | 10% | Does the copy serve stated business objectives? |
| Pattern Adherence | 10% | Does the content follow brand structural patterns? |
| Overall Quality | 5% | Readability, grammar, clarity, sentence variety |

**Pass threshold:** 75/100. Below 75 requires revision before publishing.

**Severity system:** Every flagged issue gets a severity label — `INFO`, `WARNING`, `FAIL`, or `AUTOMATIC FAIL`. Compliance scores below 7 trigger an automatic fail regardless of the overall score.

**Supported content types:** Email, SMS, push notifications, UX journey copy, social, concept copy, and general copy.

**Output:** A structured validation report with per-dimension scores, weighted calculations, severity-flagged issues, top 3 improvement priorities, and an optional rewrite of flagged sections.

---

### 3. UX Writing Guide

**Skill name:** `gooder-ux-guide`

A comprehensive UX content strategy system grounded in behavioral psychology, conversion science, accessibility standards, and industry research.

**Strategic objective frameworks:**

The guide supports 8 strategic objectives, each with dedicated behavioral levers, copy principles, and anti-patterns: Conversion, Retention, Acquisition, Re-engagement, Activation, Trust & Credibility, Education, and Delight. The user can set an objective per-session or let the guide auto-detect from context.

**Component-level frameworks:**

| Component | Key Metric | Framework Depth |
|-----------|-----------|----------------|
| Onboarding | Activation rate | Patterns, objective modifiers, anti-patterns |
| Error Messages | Error recovery rate | 3-part formula, severity-to-tone guide, inline validation rules |
| Empty States | First action rate | Type-specific patterns (first-time, search, filtered, completed) |
| CTAs | Click-through / conversion rate | CTA hierarchy, first-person framing, destructive action patterns |
| Form Copy | Form completion rate | Labels, placeholders, helper text, inline validation — with accessibility |
| Success States | Next-action rate | 3-part formula, celebration intensity calibration |
| Loading States | Abandonment rate | Time-based guidance (under 2s, 2–10s, 10s+) |
| Permission Requests | Permission grant rate | Just-in-time pattern, benefit-first framing |
| Tooltips & Modals | — | Tooltip length limits, destructive modal patterns |
| Notifications | Open rate / action rate | Channel-specific rules (toast, banner, email, SMS, push) |
| Conversational UI | Task completion rate | Bot persona, fallback hierarchy, human handoff |
| Landing Pages | Conversion rate | Above-the-fold formula, message match, FAQ objection handling |
| Offboarding | Reactivation rate | Respectful cancellation flow, feedback capture, return path |
| Settings | Support ticket reduction | Outcome-based labels, consequence-aware helper text |

**Behavioral psychology reference:** Documented frameworks for loss aversion, social proof, the Fogg Behavior Model, anchoring, endowed progress effect, goal-gradient effect, and cognitive load theory — each with ethical use guidelines.

**Accessibility & inclusive language:** WCAG-relevant copy requirements, screen reader considerations, plain language standards, inclusive language principles, and internationalisation awareness.

**Works without a brand profile** using universal UX writing principles. When a brand profile is loaded, voice is layered on top of the frameworks.

---

## Skill Architecture

Gooder uses a three-skill separation-of-concerns architecture:

```
gooder-brand-tone-voice (Setup)
        │
        │  Saves profile to ~/.claude/gooder/profiles/<brand>.md
        │
        ├──▶ gooder-tone-validator (QA)
        │      Reads profile → scores copy → flags issues → rewrites
        │
        └──▶ gooder-ux-guide (Generation)
               Reads profile → applies UX frameworks → writes in brand voice
```

- **Setup** handles extraction and profile management. Run once per brand, update anytime.
- **QA** runs independently or automatically after generation. Strict scoring — designed to catch, not flatter.
- **Generation** combines research-backed frameworks with brand voice for any UX surface.

The skills communicate through the brand profile file. There's no runtime dependency between them — each can operate standalone, but they're designed to work as a system.

---

## Installation

### Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed and running
- macOS or Linux (Windows: substitute `~` with your user home path)

### Step 1 — Copy the plugin files

```bash
# Create the plugin directory
mkdir -p ~/.claude/plugins/cache/local/gooder/1.0.0

# From the root of this repo, copy the plugin and skills
cp -r .claude-plugin ~/.claude/plugins/cache/local/gooder/1.0.0/
cp -r skills ~/.claude/plugins/cache/local/gooder/1.0.0/
```

### Step 2 — Register the plugin

Open (or create) `~/.claude/plugins/installed_plugins.json` and add the Gooder entry:

```json
{
  "version": 2,
  "plugins": {
    "gooder@local": [
      {
        "scope": "user",
        "installPath": "/Users/YOUR_USERNAME/.claude/plugins/cache/local/gooder/1.0.0",
        "version": "1.0.0",
        "installedAt": "2026-01-01T00:00:00.000Z",
        "lastUpdated": "2026-01-01T00:00:00.000Z"
      }
    ]
  }
}
```

Replace `YOUR_USERNAME` with your system username (run `whoami` to check).

If you already have other plugins registered, add the `"gooder@local"` key inside the existing `"plugins"` object.

### Step 3 — Restart Claude Code

Close and reopen Claude Code, or start a new session.

### Step 4 — Verify

Ask Claude: *"What skills do you have available?"* — you should see all three Gooder skills listed.

---

## Usage

### Training a Brand Profile

Tell Claude: **"Use the gooder-brand-tone-voice skill"**

Claude will ask for your brand name, then guide you through uploading or pasting materials. It extracts voice patterns, scores profile completeness, and asks targeted follow-up questions for any gaps below the 80% activation threshold.

```
You: Use the gooder-brand-tone-voice skill
Claude: What's the name of the brand you're training?
You: acme-corp
Claude: Starting a fresh profile for Acme Corp. Please share your brand materials...
You: [paste text, share file paths, or provide URLs]
Claude: I've analysed 4 sources. Extracting brand voice patterns now...
```

Supported inputs: PDF, DOCX, TXT, HTML, PNG, JPG, and web URLs. You can provide as many as you have — more materials produce richer profiles.

### Validating Copy

Tell Claude: **"Use the gooder-tone-validator skill"**

Paste any copy and Claude returns a structured validation report with per-dimension scores, flags, and improvement suggestions.

```
Validation Report: Acme Corp — Email

Overall Score: 82/100 — PASS ✓

| Dimension             | Score /10 | Weighted | Notes                          |
|-----------------------|-----------|----------|--------------------------------|
| Voice Consistency     | 9         | 18       | All pillars expressed           |
| Tone Accuracy         | 8         | 12       | Appropriate for context         |
| Compliance            | 7         | 14       | One minor grammar rule slip     |
| ...                   |           |          |                                |

Flags:
- [WARNING] Compliance: Contraction used in formal context — expand to full form
```

### Writing UX Copy

Tell Claude: **"Use the gooder-ux-guide skill"**

Claude loads your brand profile (if available), asks for the strategic objective, and produces copy with framework citations, behavioral rationale, and alternative variants.

Works for: onboarding, error messages, empty states, CTAs, forms, modals, tooltips, notifications, landing pages, chatbot copy, settings, offboarding, and more.

### Recommended Workflow

1. **Train** your brand profile from your strongest materials. Aim for 90%+ completeness.
2. **Write** with the UX guide for any screen or component — the brand voice is applied automatically.
3. **Validate** runs automatically post-training. Review flags, accept or revise, and publish with confidence.

---

## Brand Profile Schema

Profiles are saved as markdown files to `~/.claude/gooder/profiles/<brand-name>.md` and follow the BVST-2026 schema:

```
Brand Profile: [Name]
├── Voice Identity
│   ├── Voice Pillars (3–5, with examples and anti-patterns)
│   ├── Brand Archetype (primary + secondary)
│   └── Voice Spectrum (5-axis, scored 1–10)
├── Tone Architecture
│   ├── Situational Tone Map (3–5 contexts)
│   └── Tone Rules
├── Grammar & Style
│   └── 7 preference categories
├── Channel Adaptation
│   └── Email / SMS / Push / UX Journey
├── Terminology & Definitions
│   └── Canonical terms, avoid terms, product names
├── Training Log
│   └── Source tracking with type and date
└── Companion Skill Activation
    └── Auto-validate + auto-guide status
```

---

## Validation Scoring System

The validator uses a weighted scoring formula:

```
overall = (voice × 0.20) + (tone × 0.15) + (compliance × 0.20) +
          (terminology × 0.10) + (platform × 0.10) + (objectives × 0.10) +
          (patterns × 0.10) + (quality × 0.05)

overall_percent = round(overall × 10)
```

Voice Consistency and Compliance carry the highest weight (20% each) because off-brand voice and rule violations are the most damaging to brand integrity.

The severity system operates independently of scores — a compliance score below 7 triggers `AUTOMATIC FAIL` regardless of the overall number. This prevents a high-scoring piece of copy from passing when it contains a prohibited term or missing disclosure.

---

## UX Component Coverage

The UX Writing Guide provides structured frameworks for 14 component types, each with:

- Goal statement and key metric
- Research-backed rules with source citations
- Copy patterns (templates with variable slots)
- Strategic objective modifiers (how the copy changes per business goal)
- Anti-patterns to flag during review
- Behavioral psychology integration

Additionally, the guide includes a 7-principle behavioral psychology reference, WCAG-aligned accessibility requirements, inclusive language standards, and ethical boundaries for persuasive copy.

---

## Multi-Brand Support

Each brand gets its own profile file. Train as many as you need:

```
~/.claude/gooder/profiles/
├── acme-corp.md
├── acme-foundation.md
└── client-brand.md
```

When invoking the validator or UX guide, specify which brand to use. Profiles can be updated incrementally — new materials merge into the existing profile without overwriting previous training.

---

## File Structure

```
gooder/
├── .claude-plugin/
│   └── plugin.json            # Plugin manifest (name, version, metadata)
├── skills/
│   ├── gooder-brand-tone-voice/
│   │   └── SKILL.md           # Brand training skill (~14K chars)
│   ├── gooder-tone-validator/
│   │   └── SKILL.md           # Validation skill (~9K chars)
│   └── gooder-ux-guide/
│       └── SKILL.md           # UX writing skill (~59K chars)
├── INSTALL.md                 # Step-by-step installation guide
└── README.md                  # This file
```

---

## FAQ

**Do I need all three skills?**
No. Each skill works independently. The brand trainer is the starting point — the other two are most powerful with a profile, but the UX guide also works standalone using universal best practices.

**How long does training take?**
10–20 minutes for a first profile, depending on how many materials you provide and how many follow-up questions are needed to reach 80% completeness.

**Can I update a profile later?**
Yes. Run the brand trainer again with the same brand name. New materials are merged into the existing profile. You can also ask to update specific fields.

**Does validation happen automatically?**
After training, yes. Claude runs the tone validator on every piece of copy it writes for a brand with an active profile. You can pause this with "skip tone check" for a single response, or remove the activation block from the profile to disable it permanently.

**What if I don't have brand guidelines?**
The trainer can work from any brand material — marketing emails, website copy, social posts, product packaging photos. The more varied the sources, the more complete the profile. You can also answer the follow-up questions manually to build a profile from scratch.

**Can I use this with Claude.ai (chat) instead of Claude Code?**
The skills are designed for Claude Code's plugin system. In Claude.ai chat, you can paste the SKILL.md content as part of your prompt or project instructions to get similar behaviour, but the file I/O (saving profiles, reading documents) requires Claude Code.

---

## Contributing

This is a proprietary skill suite. If you have feedback, feature requests, or bug reports, contact your Gooder account manager or open an issue in this repository.

---

## License

Proprietary. See [LICENSE](LICENSE) for terms.

---

<p align="center">
  Built by <strong>Gooder</strong>.
</p>
