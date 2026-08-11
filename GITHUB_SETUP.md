# Push ke GitHub - Step by Step

Panduan lengkap untuk push repo `carousel-slop-check` ke GitHub.

---

## Step 1: Buat Repository di GitHub

1. Go ke https://github.com/new
2. **Repository name:** `carousel-slop-check`
3. **Description:** "Deteksi AI tells di carousel captions Indonesia"
4. **Visibility:** Public (recommended, supaya orang bisa pakai)
5. **Initialize:** Jangan—akan kami push dari lokal
6. Click **Create repository**

GitHub sekarang kasih kamu URL: `https://github.com/YOUR-USERNAME/carousel-slop-check.git`

---

## Step 2: Setup Local Repository

Buka terminal / command prompt di folder `carousel-slop-check-repo/`:

```bash
# Initialize git (if not done yet)
git init

# Add all files
git add .

# Commit
git commit -m "Initial commit: Carousel Slop Check skill v1.0.0"

# Add GitHub remote
git remote add origin https://github.com/YOUR-USERNAME/carousel-slop-check.git

# Rename branch to main (if on master)
git branch -M main

# Push ke GitHub
git push -u origin main
```

**Ganti `YOUR-USERNAME` dengan username GitHub kamu.**

---

## Step 3: Verify Files di GitHub

Go ke https://github.com/YOUR-USERNAME/carousel-slop-check

Kamu harus lihat:
```
carousel-slop-check/
├── skills/
│   └── carousel-slop-check/
│       ├── SKILL.md ✓
│       └── eval.md ✓
├── README.md ✓
├── LICENSE ✓
├── package.json ✓
├── .gitignore ✓
├── CONTRIBUTING.md ✓
└── GITHUB_SETUP.md ✓
```

---

## Step 4: Update `package.json` dengan GitHub URL Kamu

Edit `package.json`, line 14:

```json
"repository": {
  "type": "git",
  "url": "https://github.com/YOUR-USERNAME/carousel-slop-check"
},
```

Push perubahan:

```bash
git add package.json
git commit -m "Update repository URL in package.json"
git push
```

---

## Step 5: Verify Installation Works

Test apakah orang bisa install skill kamu:

```bash
npx skills add YOUR-USERNAME/carousel-slop-check --skill carousel-slop-check --global
```

Jika berhasil, kamu lihat:
```
✓ Installed carousel-slop-check v1.0.0
✓ Skill available as /carousel-slop-check
```

---

## Step 6: Add GitHub Topics (Optional tapi recommended)

1. Go ke repo GitHub kamu
2. Click **Settings** (di header sebelah Code, Issues, etc.)
3. Scroll ke **Topics**
4. Add:
   - `ai-detection`
   - `carousel`
   - `instagram`
   - `tiktok`
   - `indonesian`
   - `writing-tool`
   - `skill`

Ini membuat skill kamu lebih discoverable.

---

## Step 7: Create GitHub Release (Optional)

Untuk cleaner version management:

1. Go ke repo, click **Releases** (di side bar)
2. Click **Create a new release**
3. **Tag version:** `v1.0.0`
4. **Title:** `Carousel Slop Check v1.0.0`
5. **Description:**
   ```markdown
   Initial release: Carousel Slop Check skill
   
   - 8 AI tell patterns for Indonesian carousel captions
   - Detection-only workflow (no rewriting)
   - Ready for Claude Code, Claude Projects, CLI installation
   
   See README.md for usage.
   ```
6. Click **Publish release**

---

## Step 8: Share & Market

Once pushed, kamu bisa:

- ✅ Link di LinkedIn / Twitter: "Open-source skill for carousel detection"
- ✅ Add ke portfolio / personal site
- ✅ Reference dalam content strategy guides
- ✅ Submit ke skill registries (jika ada public registry)

---

## Troubleshooting

### Error: "fatal: not a git repository"
```bash
cd carousel-slop-check-repo/
git init
```

### Error: "Permission denied (publickey)"
Kamu belum setup SSH keys. Use HTTPS instead:
```bash
git remote set-url origin https://github.com/YOUR-USERNAME/carousel-slop-check.git
```

### Error: "nothing to commit"
Files already committed? Push:
```bash
git push -u origin main
```

### Files not showing on GitHub
Check `.gitignore`—pastikan tidak exclude important files:
```bash
git status
```

Jika file ter-list but tidak di GitHub:
```bash
git add -f skills/carousel-slop-check/SKILL.md
git commit -m "Force add SKILL.md"
git push
```

---

## Done!

Repo kamu sekarang public dan installable. 

Users bisa:
```bash
npx skills add YOUR-USERNAME/carousel-slop-check --skill carousel-slop-check --global
```

Atau manual:
- Copy `skills/carousel-slop-check/SKILL.md`
- Paste ke Claude Projects / Code / Custom Instructions

---

## Next: Maintenance

- Monitor issues / PRs
- Update version jika ada improvements
- Keep README updated
- Credit contributors

---

## Questions?

Check GitHub docs: https://docs.github.com/en/get-started
