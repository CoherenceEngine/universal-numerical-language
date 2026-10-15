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


## Follow-up full workflow audit, 15 October 2026

### Browser and download checks
- **Two-location workflow: PASS, Chrome.** A single browser session explicitly consented to geocoding and confirmed London, England, United Kingdom (51.50853, -0.12574, Europe/London) and Raleigh, North Carolina, United States (35.77210, -78.63861, America/New_York).
- **Geographic distance: PASS.** The page displayed 6235.3 km great-circle distance between the two city-center coordinates.
- **Historical local-time conversion: PASS for tested examples.** London 1815-12-10 08:38 local produced 1815-12-10T08:39:15Z. This historical local-mean-time offset contains seconds, which the implementation preserved.
- **Independent implementation comparison: PASS for four selected examples against Python zoneinfo.** New York 1985-05-10 08:38 -> 12:38Z; New York 2024-03-10 02:30 -> nonexistent time; New York 2024-11-03 01:30 -> ambiguous time; London 1815-12-10 08:38 -> 08:39:15Z. This is an independent software implementation comparison using IANA time-zone data, **not** archival verification of historical civil-time practice.
- **Actual downloaded JSON: PASS, Chrome.** The browser downloaded UNL-field-node-research.json; the file was read back from disk and parsed as JSON. A populated export contained mode birth-local-time and both confirmed locations.
- **Observation-date update: PASS, Chrome.** Changing 1815-12-10 to 1815-12-11 recalculated the astronomical result for 1815-12-11 in observation-noon-UTC mode.
- **Rapid date changes: PASS in tested sequence.** Three rapid changes ended on 1815-12-12 and the completed astronomy result matched the selected date. The code now clears stale astronomy data when a new date is selected.
- **Mobile-sized Chrome: PASS basic smoke.** A 390x844 touch-emulated Chrome viewport generated an atlas, opened Field Node Explorer, and completed an astronomy calculation.

### Not fully closed
- **Mobile Safari:** not executed on iOS Safari. Chrome mobile emulation is not a substitute.
- **Archival time-zone verification:** independent IANA zoneinfo agreement is not documentary historical verification. Dates with historical local-mean-time offsets and older jurisdictional practices need archival review before publication as definitive natal civil times.
- **Broader reliability:** more repeated stress tests, browser-version coverage, network failure and privacy testing are needed for production readiness.

### Model boundary
These tests validate website behavior and documented calculations. They do not validate numerology as science, astrological interpretations, a physical Field Node coherence metric, or Δ.72 post-entropy behavior.
