# ASO x SEO crossref

> **Status: experimental.** I'm testing this on two of my own apps now; results in ~4 weeks.

**Join your App Store keyword data with your Google keyword export, and get your app's title, subtitle, 100-character keyword field and blog topics in one pass.** Store searches show what people type when they're ready to download; Google shows what they type while they're still figuring things out. This skill lines the two up keyword by keyword (BOTH / ASO_ONLY / SEO_ONLY / SKIP), tells you which words belong in your metadata and which belong on your website, shows what your top competitors rank for, and then helps you measure whether the change moved anything. Real numbers only: blanks stay blank.

## You need

- [Astro](https://tryastro.app) with the MCP server on (Settings → MCP Server) and your apps tracked
- A Google keyword CSV (Keysearch, Ahrefs, Semrush, Search Console or DataForSEO), mapped to
  `templates/input-keywords-template.csv` (mapping table in `SKILL.md`)
- `apps.md` filled in from `templates/apps.example.md`: store ID + one-line description per app

## Quick start

1. Connect Astro to your agent, e.g. Claude Code:
   `claude mcp add --transport http astro http://127.0.0.1:8089/mcp`
2. Put `SKILL.md`, your `google-keywords.csv` and `apps.md` in one folder and open it in
   Claude Code or Codex.
3. Paste:

```
Follow SKILL.md (aso-seo-crossref). Astro MCP is connected.
Inputs: apps.md (store IDs, store country, one-line descriptions, features each app does NOT have)
and google-keywords.csv (columns: site, keyword, volume, difficulty, cpc, priority, intent,
target_page, note; Google source: <tool>, <country>, <month>).

1. List the Astro MCP tools first and tell me which you'll use. Match apps by store ID.
2. Per app: CSV keywords + 20-40 short store-style variants; dedupe near-variants; drop
   keywords for features the app doesn't have.
3. Astro popularity, difficulty, current rank; top competitors for the best 5 keywords.
4. Exact-text join with the Google CSV. Tag BOTH / ASO_ONLY / SEO_ONLY / SKIP
   (popularity > 5, volume > 0; missing data = provisional).
5. Write aso-seo-crossref.csv, competitor-rankings.csv and aso-seo-plan.md: title (30),
   subtitle (30), 100-char keyword field (comma-separated, no spaces, no title/subtitle words),
   top 5 SEO_ONLY page topics, top 3 competitors, surprises.

Real numbers only; blanks, not estimates. Don't change anything in App Store Connect.
```

4. Optional: ask for the **seed pass** (ASO_ONLY + competitor keywords back through your Google
   tool for new page ideas) and the **measure** loop (baseline today, weekly re-check for 4 weeks).

See `examples/plant-care-example.md` for what the output looks like (invented app and numbers).

## Files

```
SKILL.md                                  the method, rules and output specs
templates/input-keywords-template.csv     Google keyword input columns
templates/apps.example.md                 per-app inputs
templates/crossref-output-template.csv    crossref output columns
templates/competitor-rankings-template.csv competitor output columns
examples/plant-care-example.md            illustrative run
```
