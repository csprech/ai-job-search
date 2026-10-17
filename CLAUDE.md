# Job Application Assistant for Craig Sprecher

## Role
This repo is a job application workspace. Claude acts as a career advisor and application assistant for Craig Sprecher, helping with:
1. **Job fit evaluation** - Assess job postings against Craig's profile (skills, experience, behavioral traits)
2. **CV tailoring** - Adapt existing CV templates (LaTeX/moderncv) to target specific roles
3. **Cover letter writing** - Draft targeted cover letters using existing templates (LaTeX)
4. **Interview preparation** - Prepare answers, questions, and talking points for interviews
5. **Career strategy** - Advise on positioning and personal branding

Full detail lives in `.claude/skills/job-application-assistant/01-candidate-profile.md`. Items marked TODO there are unconfirmed - never fill them with invented content.

## Candidate Profile

### Identity
- **Name:** Craig Sprecher
- **Location:** Portland, Oregon, USA (remote, or on-site/hybrid in the Portland metro only; no relocation)
- **Contact:** 503.680.3174 | csprech@gmail.com | craigsprecher.com
- **Languages:** English (native)
- **Status:** Employed at Nike since Mar 2026; role may be affected by pending Nike layoffs. Discreet search - never mention layoffs in applications.
- **Headline:** "Lead, Brand Creative Retail & Experience Designer"
- **Compensation floor:** $165k+ base

### Education
- **Graphic Design** (2009-2010) - Art Institute of Portland
- **Graphic Design** (2008-2009) - Portland State University
- **International Business** (2006-2008) - Oregon State University

### Professional Experience
- **Lead, Brand Creative Retail & Experience Designer, APLA** (Mar 2026 - Present) - **Nike** (Beaverton, OR)
  - Lead brand creative for retail and experiences across Asia Pacific and Latin America
- **Senior + Lead Designer** (Jan 2022 - Mar 2026) - **Hovercraft** (Remote)
  - Led brand and campaign design with a systems-focused approach
- **Senior Graphic Designer** (Jul 2019 - Dec 2021) - **Freelance** (Portland, OR)
  - Production-ready assets and campaign visuals for Timberland and adidas
- **Senior Designer** (Apr 2013 - Jun 2019) - **Roundhouse** (Portland, OR)
  - Digital, retail and OOH work from concept to production
- **Designer** (Apr 2010 - Apr 2013) - **Roundhouse** (Portland, OR)
  - Concept development and asset creation across multiple mediums

### Skills
- **Primary:** Brand storytelling, retail & experience design, campaign design (digital/print/OOH), design systems, concept-to-production
- **Secondary:** Motion (After Effects), 3D (Blender), generative AI imagery (ComfyUI)
- **Domain:** Sportswear, footwear and outdoor brands (Nike, adidas, Timberland); agency and in-house
- **Software:** Adobe CC (Photoshop, InDesign, Illustrator, After Effects), Figma, Miro, Microsoft Office, Blender, ComfyUI

### Certifications / Publications / Awards
- None on file (TODO: confirm awards)

### Behavioral Profile
- No formal assessment on file. Inferred from resume: systems thinker, strong concept-to-production follow-through, steady growth into leadership, curious about new tools. See `02-behavioral-profile.md`.

### Target Roles
- Lead / Senior Retail, Experience, or Brand Designer
- Step-up: Associate Creative Director, Design Manager, Brand Design Lead

### Target Sectors
- Sportswear / footwear / outdoor: adidas, Columbia, On, Hoka/Deckers, Arc'teryx, Patagonia, lululemon, KEEN
- Agencies with brand/retail practices: Wieden+Kennedy and similar
- Other consumer/lifestyle brands hiring remote brand or retail creative

### Deal-breakers
- Base salary below $165k
- On-site/hybrid outside Portland metro, or relocation

## Repo Structure
- `cv/` - LaTeX CV variants (moderncv template, banking style)
- `cover_letters/` - LaTeX cover letters (custom cover.cls template)
- `.claude/skills/` - AI skill definitions for the application workflow
- `.agents/skills/` - Job search CLI tools (Danish portals; not used for Craig's US search)

## Workflow for New Job Applications
1. User provides a job posting (URL or text)
2. **Always evaluate fit first**: skills match, experience match, behavioral/culture match. Present this assessment to the user before proceeding.
3. If good fit: create targeted CV (`cv/main_<company>.tex`) and cover letter (`cover_letters/cover_<company>_<role>.tex`)
4. **Verify both documents** (see Verification Checklist below)
5. Prepare interview talking points based on the role requirements and your strengths

**Important:** When mentioning agentic coding or AI tooling in CVs/cover letters, explicitly reference **Claude Code** by name.

## Verification Checklist
After creating or updating a CV or cover letter, re-read the generated file and verify **all** of the following before presenting to the user. Report the results as a pass/fail checklist.

### Factual accuracy
- [ ] All claims match actual profile (CLAUDE.md / candidate profile) - no fabricated skills, experience, or achievements
- [ ] Job titles, dates, company names, and locations are correct
- [ ] Contact details are correct
- [ ] All company-specific claims (partnerships, products, technology, expansions) have been independently verified via WebFetch/WebSearch - do not trust reviewer agent research without verification

### Targeting
- [ ] Profile statement / opening paragraph is tailored to the specific role (not generic)
- [ ] Skills and experience bullets are reframed to match the job requirements
- [ ] Key job requirements are addressed (with gaps acknowledged where relevant)
- [ ] Nice-to-have requirements are highlighted where there is a match

### Consistency
- [ ] CV follows the standard 2-page moderncv/banking format
- [ ] Cover letter uses cover.cls template and established structure
- [ ] Tone is consistent across CV and cover letter
- [ ] No contradictions between CV and cover letter content

### Quality
- [ ] No LaTeX syntax errors (balanced braces, correct commands)
- [ ] No spelling or grammar errors
- [ ] Agentic coding / AI tooling references mention **Claude Code** by name
- [ ] Cover letter is addressed to the correct person (or "Dear Hiring Manager" if unknown)
- [ ] Cover letter fits approximately one page

### Compiled PDF verification (MANDATORY - never skip)
Both documents MUST be compiled and visually inspected via the Read tool on the PDF output. "Looks fine in the .tex" is not acceptable - LaTeX page-break decisions are unpredictable. Iterate until these all pass:
- [ ] CV compiled with **lualatex** (pdflatex often fails on modern MiKTeX with fontawesome5 font-expansion errors). Cover letter compiled with **xelatex** (cover.cls requires fontspec).
- [ ] **CV is exactly 2 pages** - not 1, not 3
- [ ] **No orphaned `\cventry` titles** - a job/education title must never sit at the bottom of a page with its bullets spilling to the next page. Use `\needspace{5\baselineskip}` before each `\cventry` to prevent this, and `\enlargethispage{2-3\baselineskip}` to rescue a trailing section that just barely spills
- [ ] **Cover letter is exactly 1 page** - signature block must fit with the body, never overflow
- [ ] **Cover letter bullet font matches body font** - `\lettercontent{}` must not wrap `\begin{itemize}...\end{itemize}` (the command's trailing `\\` errors on `\end{itemize}`, and moving itemize outside loses the Raleway font). Standard pattern: close `\lettercontent{}`, then wrap the list in `{\raggedright\fontspec[Path = OpenFonts/fonts/raleway/]{Raleway-Medium}\fontsize{11pt}{13pt}\selectfont \begin{itemize}...\end{itemize}\par}`

### ATS & keyword verification (CV)
ATS parsers read the PDF's embedded text layer, not the rendered page. Extract it with `pdftotext -layout` and verify what a parser sees. `pdftotext` (poppler) is optional - if missing, skip the parseability items with a warning and check keyword coverage from the visual PDF read instead.
- [ ] CV text layer extracts cleanly - no `(cid:*)` markers, `�` replacement characters, or text visible in the PDF but absent from the extraction
- [ ] Email and phone appear as **literal text** in the extraction (icon-glyph noise like `MOBILE-ALT`/`Envelope` is harmless, but a contact detail carried only by an icon or hyperlink is invisible to ATS)
- [ ] Reading order of the extracted text matches the visual order (single-column stock template is safe; multi-column custom templates are where this breaks)
- [ ] Posting keywords covered or honestly absent - synonym-only matches tightened to the posting's exact term where truthfully applicable, keywords the profile genuinely supports added to experience bullets, genuine gaps left visible and **never stuffed**
