# Connor Pink - Resume

My professional resume built with LaTeX using the popular Jake's Resume template. This repository contains both the source `.tex` file and the compiled PDF, with automated builds and versioned releases.

---

## Preview

<div align="center">
  
### [Download PDF](resume.pdf) | [View PDF](../../blob/main/resume.pdf) | [All Releases](../../releases)

<a href="resume.pdf">
  <img src="https://img.shields.io/badge/Resume-PDF-red?style=for-the-badge&logo=adobe-acrobat-reader" alt="Resume PDF"/>
</a>
<a href="../../releases">
  <img src="https://img.shields.io/github/v/release/connorpink/Connors-Resume?style=for-the-badge" alt="Latest Release"/>
</a>

<br><br>

<img src="preview.jpg" alt="Resume Preview" width="700"/>

<br>

**Click on `resume.pdf` above to view the full resume in your browser**

</div>

---

## About

**Current Position:** M.Sc. Computer Science Student & Graduate Research Assistant  
**Institution:** Guelph University  
**Research Focus:** Computer Vision, Image Segmentation, Generative AI, Synthetic Data, Explainable AI

---

## Automated Workflow

This repository uses **GitHub Actions** to automatically build and release your resume whenever `main.tex` is updated.

### How It Works

1. **Edit** `main.tex` with your changes
2. **Commit** with an optional job tag (see below)
3. **Push** to GitHub
4. **Workflow automatically:**
   - Compiles LaTeX to PDF
   - Generates preview.jpg
   - Commits PDF and preview back to repo
   - Creates a tagged release

### Tagging Releases for Specific Jobs

When tailoring your resume for a specific position, include `[job: Company/Position]` in your commit message:

```bash
# For a specific job application
git add main.tex
git commit -m "Tailor experience section [job: Google SWE]"
git push
```

**Result:** Creates release tagged as `Google-SWE-2025.01.07-1430`

```bash
# For a different position
git commit -m "Update skills for ML role [job: Meta Research Scientist]"
git push
```

**Result:** Creates release tagged as `Meta-Research-Scientist-2025.01.07-1445`

```bash
# For general updates (no job tag)
git commit -m "Fix typo in education section"
git push
```

**Result:** Creates release tagged as `v2025.01.07-1500`

### Example Release History

Your releases page will show a complete history:

```
Google-SWE-2025.01.15-0930
   Resume - Google SWE (2025.01.15-0930)

Meta-Research-Scientist-2025.01.10-1445
   Resume - Meta Research Scientist (2025.01.10-1445)

Microsoft-Cloud-Engineer-2025.01.08-1620
   Resume - Microsoft Cloud Engineer (2025.01.08-1620)

v2025.01.07-2100
   Resume - 2025.01.07-2100 (general update)
```

### Manual Trigger (Backup Option)

If you need to create a release without pushing changes:

1. Go to **Actions** tab
2. Click **Build and Release Resume**
3. Click **Run workflow**
4. (Optional) Enter job description
5. Click **Run workflow** button

---

## Building from Source (Local)

### Prerequisites

- LaTeX distribution (TeX Live, MiKTeX, or MacTeX)
- Required packages: `latexsym`, `fullpage`, `titlesec`, `enumitem`, `hyperref`, `fancyhdr`, `babel`, `tabularx`

### Compilation

```bash
# Using pdflatex
pdflatex main.tex
pdflatex main.tex  # Run twice for proper formatting

# Or using latexmk (recommended)
latexmk -pdf main.tex
```

### Generate Preview Image

```bash
# Requires ImageMagick
magick convert -density 300 resume.pdf[0] -quality 90 preview.jpg
```

### Quick Compilation Scripts

**Linux/macOS:**

```bash
#!/bin/bash
pdflatex main.tex && pdflatex main.tex
magick convert -density 300 resume.pdf[0] -quality 90 preview.jpg
```

**Windows (PowerShell):**

```powershell
pdflatex main.tex; pdflatex main.tex
magick convert -density 300 resume.pdf[0] -quality 90 preview.jpg
```

---

## Repository Structure

```
.
├── .github/
│   └── workflows/
│       └── build-resume.yml    # Automated build & release workflow
├── main.tex                     # LaTeX source file (edit this)
├── resume.pdf                     # Compiled resume PDF (auto-generated)
├── preview.jpg                  # Resume preview image (auto-generated)
└── README.md                    # This file
```

**Note:** Files marked as "auto-generated" are created by the GitHub Actions workflow and shouldn't be manually edited.

---

## Workflow Tips

### Best Practices

1. **Always tag job-specific versions** - Use `[job: Company Position]` to track applications
2. **Use descriptive commit messages** - Makes your git history more useful
3. **Check releases before applying** - Verify the PDF looks correct
4. **Download from releases** - For applications, download from the Releases page to ensure you have the exact version

### Commit Message Examples

```bash
# Good - Tagged for specific job
git commit -m "Highlight ML experience [job: OpenAI Research Engineer]"

# Good - General improvement
git commit -m "Update contact information and add new project"

# Good - Multiple changes with job tag
git commit -m "Restructure experience section and update skills [job: Amazon SDE]"

# Okay - Works but no job tracking
git commit -m "Update resume"
```

### Tracking Your Applications

Each release with a job tag creates a permanent record:

- Timestamp - When you applied
- Commit SHA - Exact code version
- PDF Archive - The exact resume you sent
- Preview - Quick visual reference

---

## Fork This Repository

Want to use this automated resume workflow for yourself? It's fully forkable!

### Quick Start Guide

1. **Fork the repository**

   - Click the "Fork" button at the top right of this repository
   - This creates your own copy under your GitHub account

2. **Edit `main.tex` with your information**

   - Replace Connor Pink's details with your own:
     - Name, contact info, location (lines 97-101)
     - Education section (lines 106-114)
     - Experience section (lines 117-171)
     - Projects section (lines 174-191)
     - Technical Skills section (lines 195-204)

3. **Update the README.md**

   - Replace the "About" section with your details (lines 32-36)
   - Update the contact section with your information (lines 220-226)
   - Customize any other sections as needed

4. **Push your changes**

   ```bash
   git add main.tex README.md
   git commit -m "Initial resume setup"
   git push
   ```

5. **That's it!** The GitHub Actions workflow will automatically:
   - Compile your LaTeX resume to PDF
   - Generate a preview image
   - Create a release with your resume
   - Commit the files back to your repo

### What Works Out of the Box

- **Automatic PDF compilation** - LaTeX builds on every push
- **Release versioning** - Tagged releases with timestamps
- **Job-specific tagging** - Track applications with `[job: Company Position]`
- **Preview generation** - Automatic JPG preview of first page
- **No setup required** - Uses `GITHUB_TOKEN` (automatically available)

### No Configuration Needed

The workflow uses only:

- Standard GitHub Actions with `GITHUB_TOKEN` (provided automatically)
- Public LaTeX packages (installed during build)
- Free ImageMagick tools

**No secrets, API keys, or additional setup required!**

### Troubleshooting

If the workflow fails on first run:

1. Go to **Settings** → **Actions** → **General**
2. Under "Workflow permissions", ensure "Read and write permissions" is selected
3. Re-run the failed workflow

---

## Template Credit

This resume is based on the Jake's Resume template, a clean and professional single-page resume format popular in the tech industry.

- **Template:** [Jake's Resume](https://www.overleaf.com/latex/templates/jakes-resume/syzfjbzwjncs)
- **License:** MIT

---

## Contact

**Connor Pink**

- Email: ConnorPink@mrpink.cloud
- Portfolio: [connorpink.me](https://connorpink.me)
- Location: Burlington, Ontario, Canada

---

## License

This resume content is © Connor Pink. The LaTeX template is licensed under MIT by Jake Gutierrez.

---

<div align="center">

**Last Updated:** January 2025

Made with love and LaTeX | Automated with GitHub Actions

</div>
