# Bug Report — hajj-w2c1-6000-notification

**User Story:** US-234822 — System | Update displayed notification when selecting plant W2C1 - 6000 (Hajj 1448 -2027)
**Latest phase:** 1 (2026-11-04)
**Bugs:** 0 open · 0 resolved · 0 not checked this run of 0

## Bugs

none

## Notes

One candidate was raised and then withdrawn during phase 1. On purchase order 4300000831 the Ship-to lookup returned "No results found" when it was reopened after a destination had been chosen. Checking the same flow on purchase order 4300000834, which still offers two destinations, showed the lookup correctly listing the remaining destination. The empty list on 4300000831 is simply that the only destination it offers today had already been chosen, so nothing was left to show. It is correct behaviour and no entry was filed.

The two failing test cases of phase 1 (TC-HAJJ-03 and TC-HAJJ-15) are `assertion_failure` rows: the application matches the requirement and the approved notice text, while the test cases' own wording does not. They are recorded as open questions Q-1 and Q-2 in the run report and routed to skill 3 `--revision`, not as defects.
