# Search Queries for Job Scraper

<!-- Configured for Craig Sprecher: brand / retail / experience design, Portland OR or remote (US), $165k+ base. -->
<!-- The Danish portal CLI tools in .agents/skills/ do not apply. Use WebSearch/WebFetch with the queries below. -->

## Search Sites

Primary:
- **linkedin.com/jobs** - filter: Portland, OR metro OR Remote (United States)
- **Company career pages** via Google `site:` searches (Workday, Greenhouse, Lever, Ashby boards)
- **Design-specific boards:** Coroflot, Working Not Working, Dribbble Jobs, AIGA Design Jobs, Behance Jobs
- **Indeed / Glassdoor** - secondary; good for salary ranges on postings

Job board hosts to use with `site:` for company postings:
- `boards.greenhouse.io`, `jobs.lever.co`, `jobs.ashbyhq.com`, `myworkdayjobs.com`

## Query Categories

Combine each query with "Portland" or "remote" where the site supports it.

### Priority 1: Retail & Experience Design (Lead / Senior)

Closest match to current Nike role.

```
site:linkedin.com/jobs "retail experience designer" (Portland OR remote)
site:linkedin.com/jobs "retail design lead" OR "lead retail designer" Portland
site:linkedin.com/jobs "experiential designer" OR "brand experience designer" remote
"retail creative" "lead designer" (Portland OR remote) site:myworkdayjobs.com
"environmental graphic designer" senior OR lead (Portland OR remote)
```

### Priority 2: Brand / Campaign Design Lead

```
site:linkedin.com/jobs "brand design lead" OR "lead brand designer" (Portland OR remote)
site:linkedin.com/jobs "senior brand designer" remote
"brand creative" "lead designer" site:boards.greenhouse.io
"campaign designer" senior OR lead site:jobs.lever.co
"lead designer" brand campaign site:jobs.ashbyhq.com remote
```

### Priority 3: Step-Up / Leadership Roles

Associate Creative Director and design management (check scope against confirmed experience).

```
site:linkedin.com/jobs "associate creative director" (Portland OR remote)
site:linkedin.com/jobs "art director" brand retail Portland
site:linkedin.com/jobs "design manager" brand OR retail (Portland OR remote)
"associate creative director" design retail OR brand site:myworkdayjobs.com
```

### Priority 4: Target Companies (Portland sportswear / outdoor / lifestyle cluster + remote-friendly brands)

```
site:adidas-group.com OR site:careers.adidas-group.com designer Portland
"Columbia Sportswear" designer brand OR retail
"Under Armour" OR "On Running" OR "Hoka" OR "Deckers" brand designer
"Arc'teryx" OR "Patagonia" OR "lululemon" brand designer OR retail designer
"Wieden+Kennedy" designer Portland
"KEEN" OR "Danner" OR "Dr. Martens" designer Portland
```

### Priority 5: Broader Net (3D / Generative AI angle)

```
"3D designer" brand OR retail remote "Blender"
"generative AI" designer brand "ComfyUI" OR "Stable Diffusion" remote
"visual designer" senior brand remote
```

## Location Filter

- **Ideal:** Fully remote (US) or Portland, OR
- **Acceptable:** Hybrid in Portland metro: Beaverton, Hillsboro, Tigard, Lake Oswego, Vancouver WA
- **Borderline:** Remote-first roles requiring quarterly travel to another city (flag)
- **Too far:** On-site or hybrid anywhere outside the Portland metro; relocation required

## Salary Filter

- Target: **$165k+ base**. Flag postings with a posted range whose top is below $165k as "below floor".
- Many Lead/Senior designer roles post $120-160k; ACD/Design Manager and big-brand Lead roles more often clear $165k. Note the posted range in every result.

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Exclusions

- Nike postings (current employer). Revisit if Craig asks, e.g. internal moves after the layoffs.
- Pure UX/UI product design, junior/mid-level roles, contract roles under 6 months (unless Craig opts in)

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape retail" -> Priority 1 + custom retail queries
- "/scrape acd" -> Priority 3 + custom ACD queries
