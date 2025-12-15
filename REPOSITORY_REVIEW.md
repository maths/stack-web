# STACK Website Repository Review

**Review Date:** December 5, 2025  
**Repository:** maths/stack-web  
**Reviewer:** GitHub Copilot Code Review Agent

---

## A. Architecture Summary (3-5 sentences)

The STACK website repository is a documentation-focused static site generator built with MkDocs and the Bootstrap theme. The architecture consists of markdown and HTML content in `website_files/` (108MB, 110+ files) that gets compiled into a static site and deployed via GitHub Actions to GitHub Pages on the `gh-pages` branch. Content is organized hierarchically with custom templates in `theme/` for specialized page types (case studies, projects), custom CSS styling, and JavaScript for interactive features. The site uses external CDN dependencies for MathJax (mathematical rendering) and Google Fonts/Maps, with MkDocs configuration in `mkdocs.yml` controlling the navigation structure and build process. Deployment is automated through a GitHub Actions workflow (`.github/workflows/deploy-mk-docs.yml`) that rebuilds and deploys the site on every push to the master branch.

---

## B. Top 5 Issues to Fix (Priority + Short Rationale)

### 1. **CRITICAL: Outdated GitHub Actions Checkout Version**
**Priority:** HIGH  
**Files:** `.github/workflows/deploy-mk-docs.yml` (line 10)  
**Issue:** Uses deprecated `actions/checkout@v2` which is no longer maintained  
**Impact:** Security vulnerabilities, missing features, potential workflow failures  
**Rationale:** GitHub has deprecated v2 and recommends v4. This is a simple upgrade with significant security benefits  
**Fix:** Update to `actions/checkout@v4` and `actions/setup-python@v5`

### 2. **CRITICAL: Missing Dependency Version Pinning**
**Priority:** HIGH  
**Files:** `.github/workflows/deploy-mk-docs.yml` (lines 14-16)  
**Issue:** Dependencies installed without version constraints (mkdocs-bootstrap, mkdocs-include-dir-to-nav, python-markdown-math)  
**Impact:** Build reproducibility issues, potential breaking changes from upstream updates  
**Rationale:** Unpinned dependencies can break the site unexpectedly when packages update  
**Fix:** Create a `requirements.txt` file with pinned versions and update workflow to use it

### 3. **MEDIUM: Broken Internal Links**
**Priority:** MEDIUM  
**Files:** Multiple files across `website_files/` directory  
**Issue:** Build warnings show numerous absolute links that should be relative (e.g., `/CaseStudies/` instead of `CaseStudies/index.md`), broken links to missing PDF files  
**Impact:** Poor user experience, broken navigation, SEO issues  
**Rationale:** Affects usability and link rot over time  
**Examples:**
- `website_files/CaseStudies/2025/Mechlib.md` links to missing `References/STACK 2022 Kraska V2.pdf`
- `website_files/Events/2025-11-27-MeclibSeminar.md` links to missing PDF
- Multiple absolute links in `Community.md`, `Conference.md`, `Training_and_events.md`

### 4. **MEDIUM: Missing Test Infrastructure**
**Priority:** MEDIUM  
**Files:** None exist  
**Issue:** No automated tests for link validation, accessibility, or build integrity  
**Impact:** Manual testing burden, potential for undetected regressions  
**Rationale:** A documentation site of this size needs automated validation  
**Fix:** Add link checker, HTML validator, and accessibility tests

### 5. **LOW-MEDIUM: Non-HTTPS External Resource**
**Priority:** LOW-MEDIUM  
**Files:** `website_files/index.md` (references http://docs.stack-assessment.org)  
**Issue:** Mixed content warning potential and insecure resource loading  
**Impact:** Browser warnings, security concerns for users  
**Rationale:** All external resources should use HTTPS  
**Fix:** Update to HTTPS URLs where available

---

## C. Documentation Gaps and Suggested README Additions

### Current State
The README.md is comprehensive for basic usage but lacks several important aspects for contributors and maintainers.

### Documentation Gaps Identified:

1. **Missing Contributing Guidelines**
   - No CONTRIBUTING.md file
   - No pull request template
   - No issue templates
   - No code of conduct

2. **Missing Development Setup Instructions**
   - Python version requirements not specified
   - No troubleshooting section for common setup issues
   - No mention of development vs production builds

3. **Missing CI/CD Documentation**
   - No explanation of the GitHub Actions workflow
   - No documentation on deployment process
   - No rollback procedures

4. **Missing Dependency Documentation**
   - No requirements.txt or similar file
   - No documentation of why specific versions are needed
   - No upgrade path documentation

5. **Missing Architecture Documentation**
   - No diagram of site structure
   - No explanation of custom templates
   - No documentation of the plugin system

### Suggested README Additions:

```markdown
## Prerequisites

- Python 3.8 or higher
- pip (Python package manager)
- Git

## Quick Start for Contributors

1. Fork and clone the repository
2. Install dependencies: `pip install -r requirements.txt`
3. Run local server: `mkdocs serve`
4. Make changes in `website_files/`
5. Test locally at http://127.0.0.1:8000/
6. Submit a pull request

## Project Structure

```
stack-web/
├── .github/workflows/    # CI/CD automation
├── theme/               # Custom MkDocs theme overrides
│   ├── includes/       # Reusable template components
│   └── js/             # Custom JavaScript
├── website_files/      # All content (Markdown + HTML)
│   ├── CaseStudies/   # User case studies
│   ├── Communities/   # Community pages
│   ├── Events/        # Event information
│   └── Projects/      # Project descriptions
└── mkdocs.yml         # MkDocs configuration
```

## Continuous Integration

This repository uses GitHub Actions to automatically build and deploy changes:
- Trigger: Push to `master` branch
- Process: Install dependencies → Build site → Deploy to `gh-pages`
- View status: [Actions tab](https://github.com/maths/stack-web/actions)

## Troubleshooting

### Build fails with "No module named 'mdx_math'"
Run: `pip install https://github.com/mitya57/python-markdown-math/archive/master.zip`

### Local server shows 404 errors
Ensure you're running `mkdocs serve` from the repository root directory.

### Images not loading
Check that image paths are relative to the current file location.

## Contributing

We welcome contributions! Please:
1. Create an issue for significant changes
2. Follow existing content formatting conventions
3. Test changes locally before submitting
4. Ensure accessibility guidelines are followed (see Accessibility section)

## License

Content is licensed under CC BY-SA 4.0 (see COPYING.txt)
```

### Additional Recommended Documentation Files:

1. **CONTRIBUTING.md** - Detailed contribution guidelines
2. **ARCHITECTURE.md** - Technical architecture overview
3. **requirements.txt** - Python dependencies with versions
4. **.github/PULL_REQUEST_TEMPLATE.md** - PR template
5. **.github/ISSUE_TEMPLATE/** - Issue templates for bugs/features

---

## D. Test Coverage Gaps and Suggested Tests

### Current State
**NO AUTOMATED TESTS EXIST** - This is a significant gap for a public-facing documentation site.

### Recommended Test Infrastructure:

#### 1. **Link Validation Tests**
**Purpose:** Detect broken internal and external links  
**Tool:** `pytest` + `pytest-check-links` or `linkchecker`  
**Implementation:**
```yaml
# .github/workflows/test-links.yml
name: Check Links
on: [push, pull_request]
jobs:
  link-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: '3.x'
      - run: pip install linkchecker
      - run: mkdocs build
      - run: linkchecker --check-extern site/
```

#### 2. **HTML Validation Tests**
**Purpose:** Ensure generated HTML is valid and standards-compliant  
**Tool:** `html5validator`  
**Test Coverage:**
- Valid HTML5 markup
- Proper heading hierarchy
- Alt text on images
- Valid ARIA attributes

#### 3. **Accessibility Tests**
**Purpose:** Ensure WCAG 2.1 AA compliance  
**Tool:** `pa11y-ci` or `axe-core`  
**Test Coverage:**
- Color contrast ratios (minimum 4.5:1)
- Keyboard navigation
- Screen reader compatibility
- Semantic HTML structure
- Skip links presence

**Implementation Example:**
```yaml
# .github/workflows/accessibility.yml
name: Accessibility Tests
on: [push, pull_request]
jobs:
  a11y:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
      - run: npm install -g pa11y-ci
      - uses: actions/setup-python@v5
      - run: pip install -r requirements.txt
      - run: mkdocs build
      - run: pa11y-ci --sitemap http://localhost:8000/sitemap.xml
```

#### 4. **Build Validation Tests**
**Purpose:** Ensure site builds successfully  
**Current:** Implicitly tested by deployment workflow  
**Enhancement:** Add explicit test job that runs on PRs before merge

**Implementation:**
```yaml
# .github/workflows/build-test.yml
name: Build Test
on: [pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: '3.x'
      - run: pip install -r requirements.txt
      - run: mkdocs build --strict
      - run: test -d site
```

#### 5. **Markdown Linting**
**Purpose:** Ensure consistent markdown formatting  
**Tool:** `markdownlint-cli`  
**Test Coverage:**
- Consistent heading styles
- Proper list formatting
- No trailing whitespace
- Consistent link formats

#### 6. **Image Optimization Tests**
**Purpose:** Ensure images are appropriately sized  
**Tool:** Custom script to check image file sizes  
**Test Coverage:**
- Images under reasonable size limits (e.g., 500KB)
- Images have appropriate dimensions
- SVGs are optimized

### Suggested Test Files Structure:

```
tests/
├── test_links.py           # Internal link validation
├── test_external_links.py  # External link validation (slower)
├── test_images.py          # Image alt text and size checks
├── test_structure.py       # Navigation structure validation
└── conftest.py            # Pytest configuration
```

### Priority Order for Implementation:

1. **Build validation** (Immediate - catches breaking changes)
2. **Link checker** (High - prevents broken links)
3. **Accessibility tests** (High - stated goal in Accessibility.md)
4. **HTML validation** (Medium - ensures quality)
5. **Markdown linting** (Low - improves consistency)

---

## E. Security and Secret Risks with Remediation

### Security Analysis Summary
**Overall Risk Level: LOW-MEDIUM**  
No hardcoded secrets or credentials found in the repository. Primary concerns are around dependency management and external resource loading.

### Identified Security Issues:

#### 1. **Unpinned Dependencies in CI/CD**
**Risk Level:** MEDIUM  
**Location:** `.github/workflows/deploy-mk-docs.yml`  
**Issue:** Installing packages without version constraints allows arbitrary code execution if upstream packages are compromised  
**Attack Vector:** Supply chain attack through compromised PyPI packages  
**Remediation:**
```yaml
# Create requirements.txt:
mkdocs==1.6.1
mkdocs-bootstrap==1.1.1
mkdocs-include-dir-to-nav==1.2.0
python-markdown-math==0.9

# Update workflow:
- run: pip install -r requirements.txt
```
**Additional:** Enable Dependabot for automated security updates

#### 2. **External CDN Dependencies**
**Risk Level:** LOW-MEDIUM  
**Location:** 
- `mkdocs.yml` line 4: `https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.9/`
- `theme/main.html` line 62: `https://fonts.googleapis.com/icon?family=Material+Icons`
- `website_files/CaseStudies/index.md`: Google Maps embed

**Issue:** Reliance on third-party CDNs introduces potential:
- Privacy concerns (user tracking)
- Availability risks (CDN outage)
- Security risks (CDN compromise)
- GDPR compliance concerns for European users

**Remediation Options:**

**Option 1: Self-host critical resources**
```yaml
# Download and host MathJax locally
extra_javascript: 
    - js/mathjax/MathJax.js?config=TeX-AMS-MML_HTMLorMML
```

**Option 2: Add Subresource Integrity (SRI)**
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.9/MathJax.js"
        integrity="sha384-..."
        crossorigin="anonymous"></script>
```

**Option 3: Add Content Security Policy**
```html
<!-- In theme/main.html -->
<meta http-equiv="Content-Security-Policy" 
      content="script-src 'self' https://cdnjs.cloudflare.com https://www.google.com; 
               style-src 'self' https://fonts.googleapis.com;">
```

**Recommendation:** Implement Option 2 (SRI) as immediate fix, consider Option 1 for critical resources long-term

#### 3. **Outdated MathJax Version**
**Risk Level:** LOW  
**Location:** `mkdocs.yml` line 4  
**Issue:** Using MathJax 2.7.9 (released 2019), current version is 3.x  
**Security Concern:** Missing 5+ years of security patches  
**Performance Impact:** v3 is significantly faster  
**Remediation:**
```yaml
extra_javascript: 
    - https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js
```
**Note:** May require markdown syntax updates

#### 4. **No Security Headers**
**Risk Level:** LOW  
**Location:** GitHub Pages configuration  
**Issue:** Missing security headers (CSP, X-Frame-Options, X-Content-Type-Options)  
**Remediation:** GitHub Pages has limited header control. Consider:
- Adding `_headers` file (if supported)
- Or migrating to Netlify/Vercel for better header control
- Or adding CSP via meta tag in theme templates

#### 5. **Executable Files in Repository**
**Risk Level:** INFORMATIONAL  
**Finding:** No suspicious executable files found  
**Action:** Add `.gitignore` entries to prevent accidental commits:
```gitignore
*.exe
*.dll
*.so
*.dylib
*.key
*.pem
*.env
.env.local
```

#### 6. **Mixed Content Risk**
**Risk Level:** LOW  
**Location:** `website_files/index.md`  
**Issue:** One HTTP link: `http://docs.stack-assessment.org/static/2019-STACK-Guide.pdf`  
**Remediation:** Update to HTTPS:
```markdown
<a href="https://docs.stack-assessment.org/static/2019-STACK-Guide.pdf">
```

### Secrets Scanning Results:
✅ **No hardcoded secrets found**  
✅ **No API keys or tokens in code**  
✅ **No password or credential files**  
✅ **No SSH keys or certificates**  

**Recommendation:** Enable GitHub Secret Scanning and push protection in repository settings.

### Additional Security Recommendations:

#### 1. **Enable Branch Protection**
- Require pull request reviews before merging to `master`
- Require status checks to pass before merging
- Require branches to be up to date before merging

#### 2. **Add Dependabot Configuration**
```yaml
# .github/dependabot.yml
version: 2
updates:
  - package-ecosystem: "pip"
    directory: "/"
    schedule:
      interval: "weekly"
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: "weekly"
```

#### 3. **Add Security Policy**
Create `SECURITY.md`:
```markdown
# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability, please email:
C.J.Sangwin@ed.ac.uk

Please do not report security vulnerabilities through public GitHub issues.
```

#### 4. **Add CODEOWNERS File**
```
# .github/CODEOWNERS
* @maths/stack-maintainers
/.github/ @maths/stack-admins
```

---

## Summary of Immediate Actions Required

### Critical (Do First):
1. ✅ Update GitHub Actions to use `actions/checkout@v4` and `actions/setup-python@v5`
2. ✅ Create `requirements.txt` with pinned versions
3. ✅ Update workflow to use `requirements.txt`
4. ✅ Enable Dependabot for security updates

### High Priority (Do Next):
5. ✅ Fix broken internal links and missing PDF references
6. ✅ Add link checker CI workflow
7. ✅ Update MathJax to v3 with SRI
8. ✅ Change HTTP link to HTTPS

### Medium Priority (Do Soon):
9. Create CONTRIBUTING.md and issue/PR templates
10. Add build validation tests for PRs
11. Implement accessibility testing
12. Add Content Security Policy

### Low Priority (Nice to Have):
13. Add markdown linting
14. Consider self-hosting CDN resources
15. Add image optimization checks
16. Create ARCHITECTURE.md documentation

---

## Metrics and Statistics

- **Total Markdown Files:** 110+
- **Total Image Files:** 363
- **Repository Size:** ~108MB (mostly images)
- **Built Site Size:** 112MB
- **External Dependencies:** 3 CDNs (Cloudflare, Google Fonts, Google Maps)
- **Known Accessibility Issues:** 11 (documented in website_files/Legal/Accessibility.md)
- **Build Warnings:** ~30 (mostly link-related)
- **Test Coverage:** 0% (no tests exist)

---

*This review was conducted on December 5, 2025. Repository state may have changed since then.*
