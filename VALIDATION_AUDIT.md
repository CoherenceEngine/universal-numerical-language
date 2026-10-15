# UNL Validation Audit — 15 October 2026

## Scope
The hosted site responded HTTP 200. Its JavaScript parsed successfully under Node.js. A controlled JavaScript execution harness exercised the live page's calculation function with supplied inputs. A headless Chrome PDF was produced from the initial blank page, confirming basic browser print capability, **not** a complete populated-report visual acceptance test.

## Verified arithmetic
Using **Allison Louise Hensgen**, 1985-05-10:
- Pythagorean name: 91 → 10 → 1
- Chaldean name: 79 → 16 → 7
- Pythagorean vowels: 49 → 13 → 4
- Pythagorean consonants: 42 → 6
- Birth-date digit sum: 29 → 11/2
- Birth number: 10 → 1
- Lo Shu grid counts, ordered [4,9,2,3,5,7,8,1,6]: [0,1,0,0,2,0,1,2,0]

Native-script arithmetic checks:
- Hebrew אב = 1 + 2 = 3
- Greek αβ = 1 + 2 = 3
- Arabic اب = 1 + 2 = 3
- An unsupported symbol in the Hebrew field was rejected.

## Explicit conventions and limitations
- Hebrew: standard 22-letter ordinary gematria, final forms assigned the same values as nonfinal forms. Not Mispar Gadol or other variants.
- Greek: standard 27-value isopsephy alphabet with stigma, koppa and sampi; accents stripped. Some historic spelling and archaic character alternatives are unsupported.
- Arabic: eastern (Mashriqi) Abjad ordering; tatweel and common diacritics ignored. Hamza-bearing forms and regional orthographies require explicit normalization decisions.
- All three require user-supplied original-script spellings. The software does not translate or transliterate Latin names.
- The 15-item registry includes overlapping and modern symbolic systems, not 15 independent historical arithmetic methods.
- Current residence and birth time are recorded, not used in the currently implemented number calculations.
- Δ.72 is excluded from the numerical bridge and is a separate post-entropy research question.

## Report validation status
- Headless Chrome generated a PDF from the site's blank initial page.
- Print CSS was improved for A4 pages, white background, reduced font sizing and avoiding page breaks inside report sections.
- **Not yet verified:** populated report print rendering, pagination, clipping, browser differences, and mobile print behavior.
- Do not describe the report as professionally validated until a populated test is rendered and visually inspected.

## Next acceptance tests
1. Generate a populated report with long names, Hebrew/Greek/Arabic input and current residence.
2. Save it as PDF in Chrome and Safari, visually inspect every page for clipping and missing text.
3. Test tabs, click targets, clipboard, JSON export, and print on desktop and mobile.
4. Compare native-script calculations against cited scholarly or primary reference tables before asserting historical completeness.
