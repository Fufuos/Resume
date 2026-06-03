<div align="center">

# 📄 Awesome-CV

**Privacy-first, industry-ready LaTeX CV & Cover Letter template for engineers in the EU and beyond**

[![Build](https://github.com/yuanweize/Awesome-CV/actions/workflows/integration.yaml/badge.svg)](https://github.com/yuanweize/Awesome-CV/actions/workflows/integration.yaml)
[![License: LPPL v1.3c](https://img.shields.io/badge/License-LPPL_v1.3c-blue.svg)](http://www.latex-project.org/lppl)
[![LaTeX](https://img.shields.io/badge/Made_with-LuaLaTeX-008080.svg?logo=latex)](https://www.luatex.org/)
[![GitHub stars](https://img.shields.io/github/stars/yuanweize/Awesome-CV?style=social)](https://github.com/yuanweize/Awesome-CV)
[![Upstream](https://img.shields.io/badge/Upstream-posquit0%2FAwesome--CV-lightgrey.svg?logo=github)](https://github.com/posquit0/Awesome-CV)

[![Download Resume](https://img.shields.io/badge/📥_Example_Resume-PDF-EC1C24.svg?style=for-the-badge)](https://github.com/yuanweize/Awesome-CV/releases/latest/download/Awesome-CV_Example_Resume.pdf) [![Download Cover Letter](https://img.shields.io/badge/📥_Cover_Letter-PDF-EC1C24.svg?style=for-the-badge)](https://github.com/yuanweize/Awesome-CV/releases/latest/download/Awesome-CV_Example_Cover_Letter.pdf)

<br>

Forked from [posquit0/Awesome-CV](https://github.com/posquit0/Awesome-CV) — restructured for **engineering roles** in EU & international markets. Code stays public; your personal data stays private (gitignored).

[![Report Bug](https://img.shields.io/badge/🐛_Report_Bug-grey.svg?style=flat-square)](https://github.com/yuanweize/Awesome-CV/issues) [![Request Feature](https://img.shields.io/badge/💡_Request_Feature-grey.svg?style=flat-square)](https://github.com/yuanweize/Awesome-CV/issues)

</div>

---

## Table of Contents

- [📄 Awesome-CV](#-awesome-cv)
  - [Table of Contents](#table-of-contents)
  - [⚙️ Prerequisites](#️-prerequisites)
  - [🚀 Quick Start](#-quick-start)
    - [Step 1: Initialize](#step-1-initialize)
    - [Step 2: Edit your data](#step-2-edit-your-data)
    - [Step 3: Build](#step-3-build)
  - [🗂️ Project Structure](#️-project-structure)
  - [🔧 How It Works](#-how-it-works)
  - [📦 Make Commands](#-make-commands)
  - [📝 Profile Management](#-profile-management)
    - [What's in a profile](#whats-in-a-profile)
    - [Commands](#commands)
    - [Typical workflow](#typical-workflow)
  - [🎨 Customization](#-customization)
    - [Change accent color](#change-accent-color)
    - [Change section order](#change-section-order)
    - [Add/remove sections](#addremove-sections)
  - [🔒 Privacy Model](#-privacy-model)
  - [🤖 CI/CD](#-cicd)
  - [🧰 Tools](#-tools)
  - [📚 Background: CV vs Resume vs Cover Letter](#-background-cv-vs-resume-vs-cover-letter)
  - [🔀 Comparison with Upstream](#-comparison-with-upstream)
    - [Document Types](#document-types)
    - [Section Comparison](#section-comparison)
    - [Architecture Comparison](#architecture-comparison)
    - [Style Tweaks](#style-tweaks)
    - [Files Removed from Upstream](#files-removed-from-upstream)
  - [📜 License](#-license)

---

## ⚙️ Prerequisites

You need **LuaLaTeX** (part of TeX Live or MiKTeX).

| Platform          | Install command                                                                   |
| ----------------- | --------------------------------------------------------------------------------- |
| **macOS**         | `brew install --cask mactex` or install [TeX Live](https://www.tug.org/texlive/)  |
| **Ubuntu/Debian** | `sudo apt install texlive-full`                                                   |
| **Windows**       | Install [MiKTeX](https://miktex.org/) or [TeX Live](https://www.tug.org/texlive/) |

Verify installation:

```bash
lualatex --version
```

---

## 🚀 Quick Start

### Step 1: Initialize

```bash
git clone https://github.com/yuanweize/Awesome-CV.git
cd Awesome-CV
make init
```

This copies template files into your **private** working copies:

| Template (tracked)                    | →   | Your copy (gitignored) |
| ------------------------------------- | --- | ---------------------- |
| `templates/config.tex.example`        | →   | `config.tex`           |
| `templates/letter_config.tex.example` | →   | `letter_config.tex`    |
| `templates/sections/*.tex`            | →   | `sections/*.tex`       |

### Step 2: Edit your data

| File                        | What to edit                               |
| --------------------------- | ------------------------------------------ |
| `config.tex`                | Name, phone, email, address, GitHub, quote |
| `letter_config.tex`         | Target company, position, greeting         |
| `sections/summary.tex`      | Professional summary                       |
| `sections/education.tex`    | Education history                          |
| `sections/experience.tex`   | Work experience                            |
| `sections/skills.tex`       | Technical & language skills                |
| `sections/certificates.tex` | Certifications                             |
| `sections/honors.tex`       | Awards & publications                      |
| `sections/letter_body.tex`  | Cover letter body text                     |

### Step 3: Build

```bash
make all          # Build both resume + cover letter
make resume       # Resume only   → build/<Name>_CV.pdf
make coverletter  # Letter only   → build/<Name>_Cover_Letter.pdf
```

Output PDFs are in the `build/` directory, **automatically named from your `config.tex`** (e.g., `Weize_Yuan_CV.pdf`).

---

## 🗂️ Project Structure

```
Awesome-CV/
├── Makefile                    # Build system
├── cv                          # Profile manager CLI (./cv --help)
│
├── src/                        # LaTeX source files
│   ├── awesome-cv.cls          # Style engine (fonts, colors, layout)
│   ├── main.tex                # Resume entry point
│   └── coverletter.tex         # Cover letter entry point
│
├── templates/                  # [TEMPLATE] Public placeholders
│   ├── config.tex.example      # Personal info template
│   ├── letter_config.tex.example # Letter target template
│   └── sections/               # CV content templates
│       ├── summary.tex
│       ├── education.tex
│       ├── experience.tex
│       ├── skills.tex
│       ├── certificates.tex
│       ├── honors.tex
│       └── letter_body.tex
│
├── config.tex                  # [PRIVATE] Your personal info
├── letter_config.tex           # [PRIVATE] Your letter target
├── sections/                   # [PRIVATE] Your CV content
│   └── (same files as above)
│
├── build/                      # [PRIVATE] PDF outputs
├── profiles/                   # [PRIVATE] Per-company versions
│
├── tools/                      # CV building utilities
│   └── tech-stack-collector/   # Server tech stack scanner
│
├── .gitignore                  # Protects all private files
├── .github/                    # CI workflows
├── .yamllint.yaml              # YAML linting config
├── LICENCE                     # LPPL v1.3c
└── README.md                   # This file
```

> Files marked `[PRIVATE]` are gitignored and **never** pushed to the remote repository.

---

## 🔧 How It Works

```
config.tex ─────────┐
  (who you are)      ├──→ src/main.tex ──────→ build/<Name>_CV.pdf
                     │
                     ├──→ src/coverletter.tex → build/<Name>_Cover_Letter.pdf
letter_config.tex ──┘
  (who you apply to)  ↑
                       │
sections/*.tex ────────┘
  (what you write)

src/awesome-cv.cls ← shared style engine
```

> **Auto-naming**: The Makefile extracts `\name{First}{Last}` from `config.tex` to produce `First_Last_CV.pdf`. If `config.tex` doesn't exist yet, it falls back to `Awesome_CV.pdf`.

- **`src/main.tex`** — assembles Resume by importing `config.tex` + `sections/*.tex`
- **`src/coverletter.tex`** — assembles Cover Letter by importing `config.tex` + `letter_config.tex` + `sections/letter_body.tex`
- **`src/awesome-cv.cls`** — defines all visual styles (fonts, colors, commands like `\cventry`)
- **`config.tex`** — your real name, phone, email (shared by both documents)
- **`letter_config.tex`** — target company, position (change per application)

---

## 📦 Make Commands

| Command            | Description                                          |
| ------------------ | ---------------------------------------------------- |
| `make init`        | First-time setup: copy templates to private files    |
| `make resume`      | Build resume → `build/<Name>_CV.pdf`                 |
| `make coverletter` | Build cover letter → `build/<Name>_Cover_Letter.pdf` |
| `make all`         | Build both                                           |
| `make clean`       | Remove all build artifacts                           |
| `make help`        | Show available targets                               |

---

## 📝 Profile Management

When applying to multiple companies, each application needs different emphasis — a different quote, cover letter, skill ordering, and experience bullets. The `cv` CLI manages these **profiles** so you can switch between company-specific versions instantly without breaking your working files.

### What's in a profile

Each profile stores only the files that change between applications:

| File                | Purpose                               |
| ------------------- | ------------------------------------- |
| `config.tex`        | Quote, personal branding              |
| `letter_config.tex` | Recipient, position title             |
| `sections/*.tex`    | All 7 section files                   |
| `*.pdf`             | Compiled output (auto-saved on build) |

Structural files (`src/main.tex`, `src/coverletter.tex`, `src/awesome-cv.cls`) are **shared** — they define the layout and are tracked by git.

### Commands

| Command              | Description                                            |
| -------------------- | ------------------------------------------------------ |
| `./cv list`          | List all profiles (active marked with ▸)               |
| `./cv use <name>`    | Load a profile into the working directory              |
| `./cv save [name]`   | Save current working files to a profile                |
| `./cv build [name]`  | Build PDFs — current if omitted, or a specific profile |
| `./cv new <name>`    | Create a new profile from current files                |
| `./cv diff <a> [b]`  | Compare two profiles, or a profile vs working files    |
| `./cv current`       | Show the active profile                                |
| `./cv delete <name>` | Delete a profile                                       |

### Typical workflow

```bash
# Start a new application
./cv new bosch                    # Creates profile from current files

# Edit config.tex, letter_config.tex, sections/ for the new target...

./cv save                         # Save changes to active profile
./cv build                        # Build PDFs

# Switch to a different version
./cv use porsche                  # Instantly loads Porsche version

# Build another profile without switching
./cv build valeo                  # Temp swap → build → restore
```

> **Note**: The `profiles/` directory and `.active_profile` are gitignored — your per-company versions stay private.

---

## 🎨 Customization

### Change accent color

Edit `src/main.tex` (or `src/coverletter.tex`):

```latex
% Built-in options:
% awesome-emerald, awesome-skyblue, awesome-red, awesome-pink,
% awesome-orange, awesome-nephritis, awesome-concrete, awesome-darknight
\colorlet{awesome}{awesome-red}

% Or use a custom hex color:
% \definecolor{awesome}{HTML}{3E6D9C}
```

### Change section order

Rearrange the `\input` lines in `src/main.tex`:

```latex
\input{\contentpath/summary.tex}
\input{\contentpath/education.tex}
\input{\contentpath/skills.tex}
\input{\contentpath/experience.tex}
\input{\contentpath/certificates.tex}
\input{\contentpath/honors.tex}
```

### Add/remove sections

1. Create `sections/newsection.tex` (and optionally `templates/sections/newsection.tex`)
2. Add `\input{\contentpath/newsection.tex}` in `src/main.tex`

---

## 🔒 Privacy Model

| Public (tracked by git)                                     | Private (gitignored)                                  |
| ----------------------------------------------------------- | ----------------------------------------------------- |
| `templates/config.tex.example`                              | `config.tex`                                          |
| `templates/letter_config.tex.example`                       | `letter_config.tex`                                   |
| `templates/sections/`                                       | `sections/`                                           |
| `src/awesome-cv.cls`, `src/main.tex`, `src/coverletter.tex` | `build/`, `*.pdf`, `meta/`                            |
| `tools/tech-stack-collector/*.py`, `*.sh`                   | `tools/tech-stack-collector/reports/`, `targets.yaml` |
| `.github/`, `Makefile`, `README.md`                         | `PROJECT_HANDOFF.md`                                  |

**Key principle**: All files containing real personal information are listed in `.gitignore`. The repository only contains the structural code and placeholder templates.

---

## 🤖 CI/CD

The project includes GitHub Actions CI (`.github/workflows/integration.yaml`) that:

1. **Copy templates** to simulate private files
2. **Compile** both resume and cover letter with LuaLaTeX
3. **Upload** PDFs as build artifacts
4. **Release** example PDFs to the `latest` GitHub Release (auto-updated on every push to `main`)
5. **Lint** YAML configuration files

A separate workflow (`.github/workflows/sync.yml`) syncs upstream changes from `posquit0/Awesome-CV:master` into the `upstream-original` branch daily.

This ensures the template always builds correctly, even without your private data.

---

## 🧰 Tools

The `tools/` directory contains standalone utilities that help build and maintain your CV content. Each tool is self-contained with its own README.

| Tool                                                  | Description                                                                                                                                                                                          |
| ----------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`cv`](cv)                                            | Profile manager CLI — switch between per-company CV/Cover Letter versions. Run `./cv --help` for usage.                                                                                              |
| [`tech-stack-collector`](tools/tech-stack-collector/) | Scans your servers and generates AI-friendly Markdown reports of installed software, Docker containers, services, etc. Three modes: `curl\|python3` one-liner, local execution, SSH batch execution. |

---

## 📚 Background: CV vs Resume vs Cover Letter

> If you already know the difference, skip to [Quick Start](#-quick-start).

| Term                      | What it is                                                                                            | Length        | When to use                                                                 |
| ------------------------- | ----------------------------------------------------------------------------------------------------- | ------------- | --------------------------------------------------------------------------- |
| **CV** (Curriculum Vitae) | A **complete** academic/professional record: every degree, publication, talk, committee, award.       | 2 – 10+ pages | Academia, research positions, EU/UK job markets (where "CV" often = resume) |
| **Resume** (Résumé)       | A **concise** highlight reel targeted at one role: key skills, recent experience, measurable results. | 1 – 2 pages   | Industry jobs (US, Canada, most of Asia), any role where brevity is valued  |
| **Cover Letter**          | A one-page letter explaining _why you_ + _why this company/role_, with a personal tone.               | 1 page        | Paired with either a CV or resume when the application asks for it          |

**Regional note**: In Germany, Austria, and much of the EU, the word "CV" is used interchangeably with "resume" — a 1–2 page document is expected for most industry roles. A multi-page academic CV is only for research positions. This fork follows the **EU/industry convention**: one concise document + cover letter.

---

## 🔀 Comparison with Upstream

This fork is derived from [posquit0/Awesome-CV](https://github.com/posquit0/Awesome-CV). The original code is preserved in the `upstream-original` branch for reference.

### Document Types

|                        | Upstream                                      | This Fork                                    |
| ---------------------- | --------------------------------------------- | -------------------------------------------- |
| **CV** (full academic) | ✅ `examples/cv.tex` — 9 sections, multi-page | ❌ Removed (not needed for industry)         |
| **Resume** (concise)   | ✅ `examples/resume.tex` — 5 active sections  | ✅ `src/main.tex` — 6 sections, restructured |
| **Cover Letter**       | ✅ `examples/coverletter.tex` — inline body   | ✅ `src/coverletter.tex` — externalized body |

Upstream provides three separate documents for different audiences. This fork keeps only the **resume** and **cover letter** — the two documents needed for industry job applications in EU/international markets.

### Section Comparison

The table below shows every content section across all upstream documents and this fork:

| Section             | Upstream CV | Upstream Resume | This Fork | Notes                                                      |
| ------------------- | ----------- | --------------- | --------- | ---------------------------------------------------------- |
| **summary**         | ❌          | ✅              | ✅        | Professional summary                                       |
| **education**       | ✅          | ✅              | ✅        | Degrees & universities                                     |
| **skills**          | ✅          | ❌              | ✅        | Technical & language skills (added to resume in this fork) |
| **experience**      | ✅          | ✅              | ✅        | Work history                                               |
| **certificates**    | ✅          | ✅              | ✅        | Professional certifications                                |
| **honors**          | ✅          | ✅              | ✅        | Awards, scholarships                                       |
| **extracurricular** | ✅          | ❌ (commented)  | ❌        | Clubs, volunteering                                        |
| **presentation**    | ✅          | ❌ (commented)  | ❌        | Conference talks                                           |
| **writing**         | ✅          | ❌ (commented)  | ❌        | Publications, blog posts                                   |
| **committees**      | ✅          | ❌ (commented)  | ❌        | Academic/org committees                                    |
| **letter_body**     | —           | —               | ✅        | Externalized cover letter body                             |

**What changed**:

- **Kept**: summary, education, experience, certificates, honors — the five pillars of an industry resume
- **Promoted**: skills — moved from CV-only to the main resume (important for engineering roles)
- **Removed**: extracurricular, presentation, writing, committees — academic sections not needed for industry applications (can be re-added if needed)
- **Added**: letter_body.tex — cover letter body extracted to its own file for cleaner separation

### Architecture Comparison

| Aspect               | Upstream                                     | This Fork                                                                                                    |
| -------------------- | -------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **Personal info**    | Hardcoded in each `.tex` file                | Centralized in `config.tex` (gitignored)                                                                     |
| **Letter recipient** | Hardcoded in `coverletter.tex`               | Extracted to `letter_config.tex` (gitignored)                                                                |
| **Letter body**      | Inline in `coverletter.tex`                  | External `sections/letter_body.tex`                                                                          |
| **Privacy model**    | ❌ None — real info pushed to git            | ✅ 3-layer: config / letter_config / sections all gitignored                                                 |
| **Template system**  | N/A                                          | `.example` files + `templates/sections/` → `make init` copies                                                |
| **LaTeX engine**     | XeLaTeX                                      | LuaLaTeX (better Unicode, OpenType)                                                                          |
| **Output directory** | Same as source (`examples/`)                 | Separate `build/` directory                                                                                  |
| **File layout**      | All in `examples/` subdirectory              | Root-level entry points, cleaner structure                                                                   |
| **Build targets**    | `make cv`, `make resume`, `make coverletter` | `make resume`, `make coverletter`, `make init`, `make clean`, `make help` — auto-named output via `-jobname` |
| **CI/CD**            | ❌ No workflow                               | ✅ GitHub Actions: build + lint + artifact upload                                                            |

### Style Tweaks

Three modifications were made to `src/awesome-cv.cls`:

| Change                       | Upstream                | This Fork                    | Why                                               |
| ---------------------------- | ----------------------- | ---------------------------- | ------------------------------------------------- |
| Header social info font size | `\fontsize{6.8pt}{...}` | `\fontsize{9pt}{...}`        | Better readability for contact details            |
| `\cventry` date column width | `4.5cm`                 | `6.5cm`                      | Fits longer date ranges like "Oct 2022 – Present" |
| `\cvsection` page break      | No protection           | `\needspace{5\baselineskip}` | Prevents orphaned section titles at page bottom   |

### Files Removed from Upstream

These upstream files were removed as they are not needed in this fork:

| Removed file                          | Reason                                                                     |
| ------------------------------------- | -------------------------------------------------------------------------- |
| `examples/` (entire directory)        | Replaced by `src/main.tex` + `src/coverletter.tex` + `templates/sections/` |
| `icon.png`                            | Upstream branding, not needed                                              |
| `CODEOWNERS`                          | Upstream team config                                                       |
| `.github/labeler.yaml`, `labels.yaml` | Upstream issue labeling                                                    |
| 2 upstream-specific workflows         | Replaced by fork's own CI                                                  |

---

## 📜 License

[LPPL v1.3c](http://www.latex-project.org/lppl) — The LaTeX Project Public License.

Original template by [posquit0](https://github.com/posquit0/Awesome-CV).
