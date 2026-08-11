# Contributing to Carousel Slop Check

Contributions welcome! Ini repositori kecil, tapi kami appreciate:
- Bug reports (false positives/negatives)
- Pattern suggestions (pola AI tells baru yang terlewat)
- Improvement ideas (UX, detection accuracy)
- Translations (buat bahasa lain)

---

## How to Report Issues

### False Positive
Kamu punya carousel caption yang terdeteksi sebagai AI slop tapi actually native?

```
Title: False positive - "[pattern name]"
Description:
- Original caption: [paste full caption]
- Pattern flagged: [which pattern]
- Why it's wrong: [explanation]
- Context: [carousel niche/audience]
```

### False Negative
Kamu punya carousel yang obviously AI-slop tapi skill tidak catch?

```
Title: False negative - missed slop
Description:
- Original caption: [paste full caption]
- What got missed: [what should've been flagged]
- Pattern it should hit: [which of the 8 patterns]
```

### New Pattern
Pola AI tell baru yang belum dalam skill?

```
Title: New pattern - [pattern name]
Description:
- Pattern example: [paste examples of the pattern]
- Why it's AI: [why this signals AI-generated]
- Language: [Indo/English/both]
- Frequency: [how often you see this]
```

---

## How to Contribute Code

### Setup

```bash
git clone https://github.com/YOUR-USERNAME/carousel-slop-check
cd carousel-slop-check
```

### File Structure
```
skills/carousel-slop-check/
├── SKILL.md      ← Detection rules (with YAML frontmatter)
└── eval.md       ← Quality checklist
```

### Editing SKILL.md

The file has this structure:

```markdown
---
name: [skill name]
description: [one-line description]
version: [semantic version]
invocation: "/carousel-slop-check [captions]"
---

# [Title]

[Instructions and patterns]
```

**Don't remove YAML frontmatter.** It's required for skill registration.

### Adding a Pattern

1. Add to "8 AI Tell Patterns" section:

```markdown
### N. **[Pattern Name]**
Pola: "[example text]"

**Kenapa slop?** [explanation]

\`\`\`
❌ "[bad example]"
✓ "[good example]"
\`\`\
```

2. Update eval.md checklist (if needed)
3. Test with 3-5 real carousel examples
4. Open PR with examples in description

### Updating eval.md

Quality checklist di eval.md harus accurate. Jika kamu add pattern:
- Add checkbox untuk pattern baru di "Detection Quality" section
- Link ke SKILL.md rule

---

## Testing Your Changes

### Manual Test

```
1. Paste your updated SKILL.md ke Claude Projects/Code
2. Test dengan carousel yang punya pattern baru
3. Document: Berapa pattern di-detect? Berapa accuracy?
4. Share results di PR
```

### Before Submitting PR

- [ ] YAML frontmatter intact?
- [ ] All 8 patterns documented with examples?
- [ ] eval.md updated?
- [ ] Tested dengan real carousel?
- [ ] No typos or broken formatting?

---

## PR Guidelines

- **Scope:** Satu perubahan per PR (satu pattern, satu fix, one improvement)
- **Description:** Jelaskan apa + kenapa + test results
- **Title:** Jelas dan descriptive (e.g., "Add pattern: Filler openers detection")
- **No YAML changes** unless absolutely necessary

### Example PR Template

```markdown
## Description
[What this PR adds/fixes]

## Testing
Tested dengan [X carousel samples]:
- [sample 1]: [pattern detected correctly/false positive/false negative]
- [sample 2]: [results]

## Checklist
- [ ] YAML frontmatter preserved
- [ ] eval.md updated (if applicable)
- [ ] No breaking changes
- [ ] Pattern tested with 3+ real examples
```

---

## Code of Conduct

- Be respectful and constructive
- Assume good intent
- Indonesian + English both OK
- Questions welcome

---

## Versioning

We use [Semantic Versioning](https://semver.org/):
- **Patch** (1.0.1): Bug fixes, eval updates
- **Minor** (1.1.0): New patterns, improvements
- **Major** (2.0.0): Breaking changes, rewrite

Update version in `SKILL.md` YAML + `package.json` when merging.

---

## Questions?

Open an issue or email the maintainer. We're friendly.

---

## Recognition

Contributors will be listed in README.md. Thanks for helping!
