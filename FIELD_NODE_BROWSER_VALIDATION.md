# UNL Field Node Explorer — Browser Validation, 15 October 2026

## Changes tested
- The observation-date control now requests a fresh astronomy and lunar calculation even if no earlier calculation was performed.
- The calculation result records observationDate, UTC instant, calculation mode, time-zone information, aspect orb, astronomical positions, lunar phase and calculation timestamp.
- The research export records the observation date and whether the astronomy result matches it.
- Local birth-time conversion now enumerates historical time-zone offsets and rejects nonexistent or ambiguous local clock times instead of silently choosing an offset.

## Actual checks
1. **Numerical regression**: six core personal arithmetic outputs and three original-script sample calculations passed in the JavaScript execution harness.
2. **Hosted Chrome navigation**: generated an atlas, opened Field Node Explorer, and successfully completed the astronomy calculation.
3. **Date control**: previous-day button changed 1815-12-10 to 1815-12-09 in Chrome.
4. **Geocoding**: with explicit consent, searched for London and displayed a selectable location match. Confirmation returned London, England, United Kingdom, 51.50853, -0.12574, Europe/London.
5. **Historical time**: entered a local birth time, confirmed the birthplace and completed a birth-local-time astronomy calculation.
6. **Research export structure**: evaluated the live browser's export object and verified format UNL-field-node-research-v2, mode birth-local-time, London birthplace and observation date.
7. **Guard**: when a birth time was present but only current residence was confirmed, the astronomy calculation correctly rejected the attempt to use an unconfirmed birthplace.

## Remaining validation
- Automated end-to-end test of both birthplace and current-residence confirmation in one session, including distance calculation.
- Verification of downloaded JSON bytes via a browser download event, rather than checking the in-browser export object.
- Verification that the selected observation date and completed astronomy result stay synchronized under rapid repeated changes.
- Tests around daylight-saving transitions, including duplicated clock hours and missing hours, against independent historical time-zone references.
- Mobile Safari interaction and populated report pagination.

## Boundaries
This is a symbolic and astronomical visualization, not evidence of a physical personal field or of Δ.72 post-entropy threshold behavior. Historical time-zone data can differ between implementations and require archival verification for older dates.
