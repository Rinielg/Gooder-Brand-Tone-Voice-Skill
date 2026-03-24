# Install Guide

## Requirements

- [Claude Pro, Team, or Enterprise plan](https://claude.ai) with skills support
- **or** [Claude Code](https://docs.claude.com) CLI

---

## Install the base skills

### Option 1: Claude.ai (recommended)

1. Download all three `.skill` files from [Releases](https://github.com/Rinielg/gooder/releases):
   - `gooder-brand-tone-voice.skill`
   - `gooder-tone-validator.skill`
   - `gooder-ux-guide.skill`

2. Open **Claude.ai** → **Settings** → **Skills**

3. Upload all three `.skill` files

4. Verify installation — start a new conversation and type:

```
Train a brand voice for My Brand
```

If the trainer responds with the brand training flow, you're set.

### Option 2: Claude Code

Clone the repo and point Claude Code at the skills directory:

```bash
git clone https://github.com/Rinielg/gooder.git
cd gooder
```

Add the skills to your Claude Code configuration:

```json
{
  "skills": [
    "./gooder-brand-tone-voice",
    "./gooder-tone-validator",
    "./gooder-ux-guide"
  ]
}
```

### Option 3: Manual install

Copy the skill folders into your Claude skills directory:

```bash
# Copy each skill folder
cp -r gooder-brand-tone-voice/ ~/.claude/skills/
cp -r gooder-tone-validator/ ~/.claude/skills/
cp -r gooder-ux-guide/ ~/.claude/skills/
```

Each folder must contain its `SKILL.md` and any `references/` subdirectory.

---

## Train your first brand

Once the base skills are installed:

1. Gather your brand materials — guidelines, tone of voice docs, existing copy across channels, screenshots, URLs
2. Start a conversation and say:

```
Train a brand voice for [Your Brand Name]
```

3. Upload your materials when prompted. Accepted formats:
   - **Documents:** PDF, DOCX, TXT, HTML
   - **Images:** PNG, JPG (analyzed for design language and tone signals)
   - **URLs:** fetched and extracted automatically
   - **Pasted text:** analyzed inline

4. Answer follow-up questions if the trainer identifies gaps (it scores completeness out of 100 and asks the highest-value questions first)

5. Download the three generated `.skill` files:
   - `gooder-voice-[brand].skill`
   - `gooder-audience-[brand].skill`
   - `gooder-platform-[brand].skill`

6. Install them the same way you installed the base skills

---

## Install the generated brand skills

After training, install all three generated skills alongside the base skills. The full set for one brand is:

```
Base skills (install once):
  gooder-brand-tone-voice
  gooder-tone-validator
  gooder-ux-guide

Brand skills (per brand):
  gooder-voice-[brand]
  gooder-audience-[brand]
  gooder-platform-[brand]
```

All six skills chain automatically. No additional configuration needed.

---

## Verify everything works

Start a new conversation and try:

```
Write a welcome email for [Your Brand]
```

You should see:
1. The brand voice skill activate
2. Copy generated in your brand's voice
3. A tone validation score appear automatically after the copy

If you specify an audience segment:

```
Write a VIP welcome email for [Your Brand]
```

The audience engine should apply segment-specific tone adjustments.

---

## Updating a trained brand

To retrain with new materials:

1. Upload the existing `.skill` file(s) alongside new materials
2. Say: `Retrain [Brand Name]`

The trainer merges new data with the existing profile and regenerates the skill files. Download and replace the old ones.

---

## Uninstall

Remove the `.skill` files from your Claude skills library or delete the skill folders from your Claude Code configuration. No other cleanup needed.
