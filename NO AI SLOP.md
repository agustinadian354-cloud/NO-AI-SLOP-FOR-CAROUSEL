# Carousel Slop Check

Deteksi 8 pola AI tells di carousel captions Indonesia. Jangan rewrite—cuma identify + suggest fix minimal.

## Invocation

`/carousel-slop-check [captions]`

Tangkas semua captions (bisa multi-slide). Output: pola yang ditemukan, quoted line, fix 1-kalimat, severity.

---

## 8 AI Tell Patterns untuk Carousel

### 1. **Forced Swipe/Urgency Bait**
Pola: "Swipe up untuk", "Lihat slide berikutnya", "Tunggu sampai slide terakhir", "Jangan lewatkan"

**Kenapa slop?** Audience sudah tahu cara carousel works. Kata-kata ini screams "AI bantu saya dulu sampe 10 slides." Authentic captions let visual do the work.

```
❌ "Swipe up untuk lihat rahasia terbesar di slide 3"
✓ "Slide 3: rahasia terbesar. Baca sampe habis."
```

### 2. **Generic Benefit Stack** 
Pola: "5 cara untuk", "Lihat semua keuntungan di sini", "Berikut strategi yang bakal mengubah segalanya"

**Kenapa slop?** Setiap benefit terasa equal/interchangeable. Tidak ada single credible detail.

```
❌ "3 cara mengubah hidup kamu pakai AI: produktivitas, efisiensi, kesuksesan"
✓ "Kami timun waktu email dari 2 jam jadi 20 menit. Ini caranya:"
```

### 3. **Emoji Oversaturation**
Pola: 3+ emoji per slide, random emoji placement, emoji bukan visual anchor

**Kenapa slop?** Terlihat desperate untuk engagement. Authentic carousel jarang banget emoji-heavy.

```
❌ "Slide 1 ✨🎯💪🔥 Strategi terbaru ✨ Jangan lewatkan 🚀🎉"
✓ "Slide 1: Strategi terbaru (visual: simple icon, 0-1 emoji max)"
```

### 4. **FOMO/Hype Stacking**
Pola: "mengubah segalanya", "revolutionary", "yang semua orang bilang", "ini gede banget", beberapa urgency word per caption

**Kenapa slop?** Kalo setiap claim adalah "mengubah segalanya", tidak ada yang dramatic lagi. Audience expect claims di-tone down.

```
❌ "Ini mengubah segalanya. Revolutionary. Semua orang bakal lihat bedanya. Jangan sia-siakan kesempatan ini."
✓ "Ini berhasil di 200+ orang. Lihat hasilnya di slide 4."
```

### 5. **Zero Specificity**
Pola: "cara terbaik", "solusi sempurna", "tips gila", "ini mencengangkan", klaim tanpa detail/proof

**Kenapa slop?** AI paling sering generate ini. Specific details = trust. Vague = slop.

```
❌ "Cara terbaik yang akan mengubah permainan bisnis kamu"
✓ "Format: mini-course (5 email). Harga: Rp 500k. Hasil: rata-rata 40% lead increase."
```

### 6. **Filler Openers**
Pola: "Perhatian!", "Dengarkan baik-baik", "Ini penting", "Kalian harus tahu", "Begini caranya"

**Kenapa slop?** Waste precious first line. Audience udah stopping scroll—bicarain value, bukan "perhatian".

```
❌ "Perhatian! Kamu perlu tahu hal ini 👇"
✓ Lead langsung dengan point atau question: "Kamu tau berapa jam yang hilang dalam email?"
```

### 7. **Unnatural CTA Stacking**
Pola: "Klik link di bio" / "Follow" / "Share ini" di SETIAP slide, atau di setiap caption tanpa konteks

**Kenapa slop?** Once per carousel cukup. Setiap slide paksa CTA terasa spammy + AI-generated.

**Rule:** CTA max 2x per carousel. Link di bio cukup 1x (akhir). Follow request only at specific moments (after value, not every slide).

```
❌ Slide 1-5: setiap slide end dengan "Follow untuk lebih banyak tips 👆"
✓ Slide 5 aja, atau hanya di slide terakhir after value delivery.
```

### 8. **Flatness / No Voice**
Pola: Sentences yang semua length sama, all formal tone, no contractions, no casual language, robotic rhythm

**Kenapa slop?** Authentic captions punya personality. AI sering default ke neutral/formal.

```
❌ "Strategi ini telah terbukti efektif. Ribuan pengguna telah merasakan manfaatnya. Kesuksesan Anda adalah prioritas kami."
✓ "Udah cobain? Works. 3000+ orang udah lihat hasilnya. Kamu bisa juga."
```

---

## Detection Output Format

**Invoke:** `/carousel-slop-check [paste all captions]`

**Output:**
```
🚩 CAROUSEL SLOP CHECK

Found: [X patterns]
Severity: [Low / Medium / High]

PATTERN FOUND: [Pattern Name]
Line: "[quoted text]"
Fix: [1-sentence suggestion]
---

[repeat for each pattern]

VERDICT: 
- Keep slides: [list which ones]
- Rewrite: [list which ones]
- Quick wins: [easiest fixes]
```

---

## Workflow: Detection Only

1. User paste carousel captions (all slides).
2. You scan against 8 patterns above.
3. Output: quoted offending lines, pattern name, fix idea (don't rewrite).
4. No scoring, no "AI probability." Just: here's the slop.

**Critical rules:**
- Don't rewrite the whole caption. Quote one line, suggest one-line fix.
- Don't be aggressive. Carousel captions are short—some "slop" might be necessary brevity.
- Don't call captions "bad." Say "this hits this pattern."
- If caption has ZERO patterns, say: "No slop detected. Looks native."

---

## Edge Cases

**Carousel di niche tertentu (motivational, e-course, hype products)** → Tone akan naturally lebih "hyped." Don't flag urgency language if it's audience-native. Contoh: crypto carousel EXPECT hype language. Deteksi bukan judge.

**Captions berbahasa campuran (Indo+English)** → Check both. English often imports American slop patterns. Flag if it jars with audience expectations.

**Visual-only slides** → Bilang "visual slide—no copy to check" dan skip.

---

## Examples: Before/After

### Example 1: High Slop
```
Slide 1: "Perhatian! 🔥 Jangan lewatkan tips yang akan mengubah hidup kamu selamanya! 🚀✨"
Slide 2: "3 cara untuk sukses: produktivitas, efisiensi, kesuksesan. Klik link di bio untuk tahu lebih lanjut! 👆"
Slide 3: "Ini revolutionary. Tunggu sampai slide terakhir. Kamu gak akan percaya apa yang akan kamu lihat. Follow untuk lebih! 💪"
```

Detection:
- **Filler opener** → "Perhatian!" → Delete, lead dengan value.
- **Forced urgency** → "Jangan lewatkan tips yang akan mengubah hidup" → Cut "mengubah hidup," lead dengan specific claim.
- **Emoji oversaturation** → 4 emoji slide 1 → Max 1, visual anchor only.
- **Generic benefit stack** → "3 cara untuk sukses" → Add specificity. Apa 3 cara? Link ke slide, bukan generic benefit.
- **Unnatural CTA stacking** → "Klik link bio" slide 2, "Follow" slide 3 → 1 CTA max per carousel. Move to last slide.
- **Hype stacking** → "revolutionary," "gak akan percaya" → Replace with specific claim.

### Example 2: Low Slop (Native)
```
Slide 1: "Jumlah email yang kamu buang per hari: 47. Solusinya sederhana."
Slide 2: "Kami cut processing time jadi 20 menit. Satu tools. Three steps."
Slide 3: "Done. Klik link untuk daftar beta (gratis 14 hari)."
```

Detection:
- No slop detected. Specific, short, conversational. Natural cadence.

---

## What This Skill DOES NOT Do

- Rewrite captions. (User does that.)
- Score "how AI" a carousel is. (Too unreliable.)
- Fix grammar or punctuation. (Not this skill's job.)
- Judge visual design. (Copy-only tool.)
- Generate alternative captions. (Detection only.)

---

## How to Integrate

**Claude Code / Codex / Claude Projects:**
1. Paste this SKILL.md into your project knowledge.
2. When user invoke `/carousel-slop-check`, this activates.
3. You scan their carousel captions, output detection (no rewrite).

**Custom Instructions:**
1. Add this as reference document.
2. Tell Claude: "When user ask to check carousel for AI tells, use Carousel Slop Check SKILL.md."

**API / Function Calls:**
1. Include this SKILL.md in system prompt.
2. When user says "check carousel," trigger detection workflow.
