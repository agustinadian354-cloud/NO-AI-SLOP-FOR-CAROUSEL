# Carousel Slop Check - Quality Checklist

Gunakan checklist ini untuk validate detection output sebelum berikan ke user.

## Detection Quality

- [ ] Setiap pattern yang dideteksi **jelas** ke salah satu dari 8 kategori di SKILL.md?
- [ ] Ada quoted line dari original caption? (Bukan paraphrase.)
- [ ] Fix suggestion **1 kalimat max**, tidak full rewrite caption?
- [ ] Output tidak aggressive—tone-nya neutral ("this hits pattern X"), bukan judgmental ("this is bad")?
- [ ] Tidak ada false positive? (Carousel vernacular yang authentic diakomodasi, bukan diflag sebagai slop.)

## Format

- [ ] Output punya header "🚩 CAROUSEL SLOP CHECK"?
- [ ] Setiap pattern punya: Pattern Name | Line (quoted) | Fix (1-line)?
- [ ] Ada severity call: Low / Medium / High?
- [ ] Ada "VERDICT" section: which slides to keep, which to rewrite, quick wins?

## Scope

- [ ] Detection hanya check captions, bukan visual/design?
- [ ] Tidak suggest emoji changes? (Yang ditarget: quantity + placement, bukan choice.)
- [ ] Tidak rewrite punchlines atau voice markers?
- [ ] Jika caption punya ZERO slop, output bilang "No slop detected"—jangan force findings?

## Edge Cases Handled

- [ ] Jika visual-only slide, skip detection tanpa error?
- [ ] Jika carousel genre/niche justify hype language (e.g., crypto, motivational), acknowledge context instead of flag?
- [ ] Jika multilingual, check both languages independently?

## Do NOT Do

- [ ] Rewrite captions (user's job).
- [ ] Score overall "AI probability" (unreliable, out of scope).
- [ ] Fix grammar/spelling (not this tool).
- [ ] Change tone or voice (preserve original).
- [ ] Suggest strategic repositioning of slides (detection only).

---

## Quick Self-Check Before Output

Ask yourself:
1. **Would the writer recognize this as their captions?** (Avoid aggressive rewrites in suggestions.)
2. **Is every flagged pattern real?** (No false positives from platform norms.)
3. **Could user fix this with 1-2 words?** (If not, suggestion too complex.)
4. **Am I detecting, not rewriting?** (Quoted lines, not paraphrased fixes.)

If any answer is "no"—revise output.
