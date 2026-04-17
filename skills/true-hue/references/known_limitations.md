# Known Limitations

This skill operates via photos and text, which means some things a professional analyst catches in person will not be detectable here. Claude should acknowledge these limitations honestly in the deliverable rather than pretend they don't exist.

---

## Fundamental technical limitations

### Monitor and camera color variance

- Every display renders color slightly differently (calibration, age, brightness setting, blue-light filter, HDR mode)
- Every camera captures color slightly differently (sensor, firmware, auto-correction)
- A hex code that looks one way on Claude's rendering may look different on the user's monitor, and different again in physical fabric
- **Implication**: the palette is a high-quality approximation, not an absolute truth. Users should verify items in natural daylight before committing.

### JPEG compression artifacts

- Most phone cameras save photos as compressed JPEGs, which slightly shifts color values (especially in smooth skin gradients)
- Analysis accuracy is meaningfully higher with uncompressed RAW photos, but most users don't have the capability to shoot or share RAW
- **Implication**: high-confidence analyses still carry 5-10% uncertainty from compression alone

### No physical draping

- A professional analyst physically drapes fabric against the face in calibrated lighting and observes real-time reaction
- This skill simulates draping analytically (via the adjacent-season comparison) but can't fully replicate the physical test
- **Implication**: the most accurate outcome is still in-person professional analysis. This skill targets 70-85% of that accuracy.

---

## Skin-tone coverage limitations

### Vein-test unreliability on deep skin

- See `undertone_cross_checks.md`
- For Fitzpatrick V-VI skin, the vein test is usually skipped
- The skill compensates with other tests (fabric draping, jewelry, questionnaire) but users should know a signal was unavailable

### Deep-skin palette research gaps

- Published 12-season palettes historically developed on predominantly European features
- Palette adjustments for deep skin (adjusting saturation/luminosity for how colors render against higher melanin) are less standardized
- The skill produces a palette appropriate to the determined season, but hex codes are not always tested on the full range of skin depths within that season
- **Implication**: deep-skin users should especially verify recommendations against their lived compliment/fail experience

### Olive complexion complexity

- Olive doesn't fit the warm/cool binary cleanly
- The skill handles olive as a noted variant within seasons but doesn't have a fully separate system
- **Implication**: olive-complexion users may find they function best in "borrowed" colors across two adjacent seasons

---

## Lifecycle factors the skill doesn't address deeply

### Age-related shifts

- Hair greying shifts apparent value (a Deep Autumn with grey hair functions more like a Soft Autumn)
- Skin pigment changes with age (melanin loss, capillary changes)
- The skill notes this in the deliverable but doesn't re-analyze automatically when hair changes dramatically

### Hormonal and pregnancy changes

- Pregnancy can change skin pigment (melasma) and undertone temporarily
- Menopause can shift skin tone over years
- Neither is handled as a special case — users in these transitions should note it and potentially re-analyze after stabilization

### Medical factors affecting color

- Anemia (paler appearance)
- Jaundice (yellow cast)
- Medication side effects
- Certain cancers and autoimmune conditions affecting skin color
- These can confound analysis; the skill isn't equipped to detect them

---

## Cases the skill does not handle

### Self-analysis for others

- A parent submitting photos of a child
- Adult children submitting photos of an elderly parent
- The protocol technically works but the questionnaire assumes first-person knowledge of compliment/fail history. When subject ≠ submitter, the analysis confidence drops meaningfully.

### Users under 18

- Children's coloring is still developing — eye color not stable until ~7, hair color may shift through puberty
- A season identified at age 14 may not apply at 30
- Not a hard block, but should be noted with extra humility

### Extreme lighting-only environments

- People who work night shifts, live in windowless environments, or have mobility constraints limiting access to natural daylight
- The photo protocol is often infeasible for these users
- Fallback: outdoor photography on overcast days is the least-bad alternative; flashless front camera near any window is next

### Heavy tattoos or medical marks on face

- Large facial tattoos, facial scarring, or medical conditions that dominate skin area can make skin reading difficult
- Cite the reading source specifically (unaffected areas) and note lower confidence

---

## What this skill is NOT

- **Not medical advice**: if the user mentions skin conditions, Claude discusses them only in the context of their relevance to color analysis, not treatment
- **Not a replacement for in-person professional analysis**: for high-stakes decisions (bridal styling, professional image reinvention), recommend in-person professional consultation as an upgrade path
- **Not a brand or retailer guide**: Claude produces hex codes and descriptions, not "buy this specific sweater from this specific brand"
- **Not a personal style system**: color is one element of style; this skill doesn't cover body type, face shape, aesthetic identity, or wardrobe curation beyond color

---

## What "high confidence" actually means

When Claude marks an analysis as "high confidence," it means:

- Photo quality met the protocol
- Undertone had three or more converging signals
- Value and chroma readings were consistent between photo evidence and questionnaire answers
- Adjacent-season comparison clearly favored one result
- No major contradictions between signals

It does NOT mean:
- The result is definitely correct (no AI color analysis can claim this)
- The user will love every color in the palette (individual preference varies)
- The result matches what an in-person professional would say (~15-30% of cases may differ at the sub-season level)

---

## Honest language the skill should use

Use phrasings like:
- "Based on available signals, you are likely a [season] with high confidence"
- "Your strongest results will come from verifying this palette against your actual compliment/fail experience over 2-3 weeks of wear"
- "If results feel off once you start wearing the palette, consider a re-analysis with improved photos or an in-person consultation"

Avoid phrasings like:
- "You ARE a Soft Autumn"
- "These are DEFINITELY your colors"
- "This palette is perfect for you"
