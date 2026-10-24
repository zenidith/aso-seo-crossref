# Example: a plant care app (ILLUSTRATIVE)

> **Every app, ID and number on this page is invented** to show the shape of the inputs and
> outputs. None of it is real Astro or Google data. Don't reuse these figures.

## Inputs

**apps.md**
- name: Fernly
- app_store_id: 1000000001 (made up)
- store: us · google_geo: US · csv_site: fernly
- what it does: watering reminders per plant, plus a photo log of plant health
- does NOT do: plant identification from photos

**google-keywords.csv** (excerpt)
```
site,keyword,volume,difficulty,cpc,priority,intent,target_page,note
fernly,how often to water succulents,2900,22,0.40,A,info,/guides/watering-succulents,
fernly,plant watering schedule,880,18,0.90,A,commercial,app landing page,
fernly,why are my plant leaves turning yellow,6600,35,0.20,B,info,/guides/yellow-leaves,
fernly,best plant care app,390,41,1.80,A,commercial,app landing page,
```

## A) Crossref (excerpt)

| keyword | astro_pop | astro_diff | rank | google_vol | google_diff | tag | use_for | note |
|---|---:|---:|---:|---:|---:|---|---|---|
| plant care | 48 | 62 | 1000 | | | ASO_ONLY | title | provisional: no Google data; rank 1000 = not in charts |
| plant watering reminder | 21 | 18 | 34 | | | ASO_ONLY | title | provisional: no Google data |
| watering schedule | 14 | 15 | 12 | 880 | 18 | BOTH | subtitle; landing page | exact-text join (see note*) |
| plant identifier | 55 | 70 | 1000 | | | SKIP | — | app has no identification feature; dropped |
| how often to water succulents | 5 | 9 | | 2900 | 22 | SEO_ONLY | blog | popularity 5 = floor, low signal |
| why are my plant leaves turning yellow | 5 | 5 | | 6600 | 35 | SEO_ONLY | blog | |

\*Exact-text rule in action: "watering schedule" only gets a Google number if that exact phrase
was looked up. Here it was (step 5 lookup, same tool and country, 880). "plant watering schedule" keeps its own CSV row.

## B) Plan

**Title (27/30):** Fernly: Plant Care Reminder
**Subtitle (29/30):** Watering Schedule & Plant Log
**Keyword field (96/100):** `houseplant,indoor,tracker,journal,succulent,fertilizer,repotting,humidity,garden,monstera,orchid`

No word from the title or subtitle is repeated in the keyword field; no spaces; "identifier" is
left out because the app can't identify plants.

**Top SEO_ONLY topics:** why are my plant leaves turning yellow (6,600 / 35) → guide;
how often to water succulents (2,900 / 22) → guide; plus three more from the crossref.

**Competitors (invented):** "PlantPal" #1 for plant care and plant watering reminder;
"Leafline" #2 for watering schedule; "GreenID" #1 for plant identifier (a different intent:
identification, not care).

## C) Surprises (the kind of thing to look for)

- The app already ranks #12 for "watering schedule" without having it in the title. Moving it
  into the subtitle is a cheap test.
- "plant identifier" has the biggest store demand but returns ID apps; it's not this app's
  keyword until the feature exists.
- The biggest Google topic (yellow leaves) has no store demand at all: content, not metadata.
