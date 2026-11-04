# Test Run Report — hajj-w2c1-6000-notification

**User Story:** US-234822 — System | Update displayed notification when selecting plant W2C1 - 6000 (Hajj 1448 -2027)
**Source document:** ../../../Manual_Test/TestCases/US-234822-hajj-w2c1-6000-notification/TEST-CASES-hajj-w2c1-6000-notification.md · revision 15be41c03353 · Status APPROVED
**Latest phase:** 1
**Latest run:** 2026-11-04
**Status:** FAILURES
**Latest results:** 10 passed · 2 failed · 1 incomplete · 0 skipped · 0 not run · 1 partial of 14 TCs
**Bugs:** none
**Compliance:** — (manual run)
**Azure DevOps:** linked
**Run file:** .runs/phase-1.json
**Screenshots:** ../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/
**Progress log:** ../../automation-logs/US-234822-hajj-w2c1-6000-notification/run-progress-2026-11-04-0705.log
**Earlier phases:** none

## Run history

| Phase | Date | Outcome | Total | Passed | Failed | Incomplete | Skipped | Not run | Partial |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-04 | FAILURES | 14 | 10 | 2 | 1 | 0 | 0 | 1 |

## Phase 1 — 2026-11-04

### Run
- **Outcome:** FAILURES
- **Environment:** Staging
- **Build:** unknown
- **Run command:** manual run — playwright-cli 0.1.22 (skill 5b)
- **Headed / workers:** headed · one session per account
- **Login method:** A1 secrets file
- **Started:** 2026-11-04 07:05 UTC
- **Duration:** 06:40:00 (manual run · one session per account)
- **Run file:** .runs/phase-1.json
- **Progress log:** ../../automation-logs/US-234822-hajj-w2c1-6000-notification/run-progress-2026-11-04-0705.log
- **Screenshots:** ../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/
- **Compliance:** — (manual run)
- **Azure DevOps:** linked
- **Data changes:** authorized · 1 made (1 by TCs · 0 preparations) · 0 cleaned up · 1 kept · 1 left
- **Previous phase:** none

### Stages

| Stage | Total | Passed | Failed | Incomplete | Skipped | Not run | Partial |
|---|---|---|---|---|---|---|---|
| Smoke | 3 | 3 | 0 | 0 | 0 | 0 | 0 |
| Positive | 6 | 2 | 2 | 1 | 0 | 0 | 1 |
| Negative | 5 | 5 | 0 | 0 | 0 | 0 | 0 |
| **Total** | 14 | 10 | 2 | 1 | 0 | 0 | 1 |

**Smoke gate:** passed — fail% 0% — no action needed

### Results

| TC-ID | REQ | Name | Status | Group | Duration | Classification | Evidence |
|---|---|---|---|---|---|---|---|
| TC-HAJJ-01 | REQ-234822-01, REQ-234822-07 | Notice opens when the W2C1 storage location 6000 destination is chosen | PASS | smoke | 00:04:00 | — | [attempt-1.png](../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/TC-HAJJ-01/manual-cli--none--r0/attempt-1.png) |
| TC-HAJJ-02 | REQ-234822-05, REQ-234822-09 | Notice content matches the approved text, both sites and the closing lines | PASS | smoke | 00:02:00 | — | [attempt-1.png](../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/TC-HAJJ-02/manual-cli--none--r0/attempt-1.png) |
| TC-HAJJ-03 | REQ-234822-06 | Notice reads right to left with colon, brackets, Hijri year and links in place | FAIL | positive | 00:03:00 | assertion_failure | [attempt-1.png](../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/TC-HAJJ-03/manual-cli--none--r0/attempt-1.png) · [failed](../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/TC-HAJJ-03/manual-cli--none--r0/attempt-1-failed.png) |
| TC-HAJJ-04 | REQ-234822-05 | Both map links open their delivery sites in a new tab | PASS | positive | 00:02:00 | — | [attempt-1.png](../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/TC-HAJJ-04/manual-cli--none--r0/attempt-1.png) |
| TC-HAJJ-05 | REQ-234822-07 | Notice closes, reopens on the next choice and after a reload, never blocks | PASS | positive | 00:06:00 | — | [attempt-2.png](../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/TC-HAJJ-05/manual-cli--none--r0/attempt-2.png) |
| TC-HAJJ-06 | REQ-234822-02 | No notice for plant W2C1 with a storage location other than 6000 | PASS | negative | 00:02:00 | — | [attempt-1.png](../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/TC-HAJJ-06/manual-cli--none--r0/attempt-1.png) |
| TC-HAJJ-07 | REQ-234822-02 | No notice for a destination on another plant | PASS | negative | 00:03:00 | — | [attempt-1.png](../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/TC-HAJJ-07/manual-cli--none--r0/attempt-1.png) |
| TC-HAJJ-08 | REQ-234822-02, REQ-234822-03 | Notice shown on the ASN request creation details page | PASS | smoke | 00:03:00 | — | [attempt-1.png](../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/TC-HAJJ-08/manual-cli--none--r0/attempt-1.png) |
| TC-HAJJ-10 | REQ-234822-03 | No notice on the ASN details page after the ASN is submitted | PASS | negative | 00:08:00 | — | [attempt-1.png](../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/TC-HAJJ-10/manual-cli--none--r0/attempt-1.png) |
| TC-HAJJ-11 | REQ-234822-04 | Exported ASN PDF carries the notice with its table and both map links | INCOMPLETE | positive | 00:09:00 | interrupted: session lost at step 6 | — |
| TC-HAJJ-12 | REQ-234822-10 | Re-exporting the PDF of a pre-release ASN shows the Hajj 1448 notice | PARTIAL — human step pending | positive | 00:04:00 | human step: 4 | [attempt-1.png](../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/TC-HAJJ-12/manual-cli--none--r0/attempt-1.png) |
| TC-HAJJ-13 | REQ-234822-10 | No Hajj 1447 content, including the Tamer Logistics site, anywhere | PASS | negative | 00:03:00 | — | [attempt-1.png](../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/TC-HAJJ-13/manual-cli--none--r0/attempt-1.png) |
| TC-HAJJ-14 | REQ-234822-01 | Notice does not open on the NUPCO PO list before a destination is chosen | PASS | negative | 00:03:00 | — | [attempt-1.png](../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/TC-HAJJ-14/manual-cli--none--r0/attempt-1.png) |
| TC-HAJJ-15 | REQ-234822-08 | Notice stays in Arabic when the portal is switched to another language | FAIL | positive | 00:03:00 | assertion_failure | [attempt-1.png](../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/TC-HAJJ-15/manual-cli--none--r0/attempt-1.png) · [failed](../../screenshots/US-234822-hajj-w2c1-6000-notification/phase-1/TC-HAJJ-15/manual-cli--none--r0/attempt-1-failed.png) |

### Bugs

none

### Skips and residual failures

| TC-ID | Status | Reason |
|---|---|---|
| TC-HAJJ-03 | FAIL | assertion_failure — the application renders the Hijri year correctly for right-to-left text; step 5's wording asks for the opposite. See Q-1 |
| TC-HAJJ-11 | INCOMPLETE | interrupted: session lost at step 6 — the VPN dropped as the request was submitted; not re-run this phase |
| TC-HAJJ-15 | FAIL | assertion_failure — the supplier portal has no language control, so step 2 cannot be performed. See Q-2 |

### Open questions

| # | Source | Ambiguity | TCs | Decision | By |
|---|---|---|---|---|---|
| Q-1 | TC-HAJJ-03 step 5 | The step asks for the year digits to sit to the left of "هـ". Measured on screen, "1448" is at x 623-658 and "هـ" at x 604-618, so the digits are to the right. That is what correct right-to-left rendering produces, it matches the approved text and it matches step 4's own bracket convention. Should step 5 be reworded to the right-to-left reading? | TC-HAJJ-03 | pending | skill 3 --revision |
| Q-2 | TC-HAJJ-15 steps 2-6 | The test case assumes a portal language control. None exists anywhere in the supplier portal — not in the header, the account menu, the application grid or the footer, and no element carries a language class, id, aria-label or test id. Should the test case be withdrawn, or rewritten for whatever audience does have a language switch? | TC-HAJJ-15 | pending | skill 3 --revision |

### Test-data readiness

**Verdict:** READY

| Gap | TCs | Decision | Source | Provisioning | Identifiers / names | Effective stamped values | Verified on | Cleanup |
|---|---|---|---|---|---|---|---|---|
| A bookable purchase order offering W2C1 / 6000 [D1] | TC-HAJJ-01, 02, 03, 04, 08, 10, 13, 14, 15 | READY | found on Staging | — | purchase order 4300000831 | — | the PO list and its Ship-to lookup | kept |
| A purchase order offering W2C1 / 6000 AND a second destination [D1 for TC-HAJJ-05] | TC-HAJJ-05 | READY | found on Staging | — | purchase order 4300000838 (W2C1 / 6000, E3C1 / 2000, W3C1 / 1000) | substituted for 4300000831, whose second destination has gone | its Ship-to lookup | kept |
| A purchase order offering W2C1 on another storage location [D2] | TC-HAJJ-06 | READY | found on Staging | — | purchase order 4300000834, W2C1 / 1000 "MOH Stock" | — | its Ship-to lookup | kept |
| A purchase order with a destination on another plant [D3] | TC-HAJJ-07 | READY | found on Staging | — | purchase order 4300000834, 1100 / 120215 "MOH - Aseer Health Directorate" | substituted for 4300000831 / 1100 / 120364, which is no longer offered | its Ship-to lookup | kept |
| The approved Hajj 1448 notice text [D4] | TC-HAJJ-02, 03, 04, 08, 11, 12, 13, 15 | READY | the story's acceptance criteria | — | — | — | the notice panel on PO details | kept |
| An ASN raised on the W2C1 / 6000 destination [D5] | TC-HAJJ-10, TC-HAJJ-11 | READY | created by TC-HAJJ-10 | ui | ASN 5060-261104-19824, invoice QA5B-234822-B | — | the ASN list and its details page | kept |
| An ASN created before the Hajj 1448 release on W2C1 / 6000 [D7] | TC-HAJJ-12 | READY | found on Staging | — | ASN 5060-260630-8452 (30-06-2026); also 5060-260505-4017, 5060-260426-3602, 5060-260426-3601 | — | the ASN list filtered to plant W2C1 / storage location 6000 | kept |

### Deviations

- Purchase order 4300000831 no longer offers the second destination 1100 / 120364 that TEST-DATA recorded on 2026-11-03; its Ship-to lookup now holds only W2C1 / 6000. TC-HAJJ-05 was run on purchase order 4300000838 instead — route to skill 3 --revision so [D1] and [D3] are re-recorded.
- [D3] "purchase order 4300000831, destination 1100 / 120364": that destination no longer exists, so TC-HAJJ-07 used purchase order 4300000834, destination 1100 / 120215 — route to skill 3 --revision.
- [D7] is recorded as UNKNOWN in TEST-DATA but exists on Staging: ASN 5060-260630-8452 (30-06-2026) and three others on W2C1 / 6000 from April and May 2026 — route to skill 3 --revision to set it READY.
- TC-HAJJ-08's Expected Result calls the notice "a fixed box at the top", while its own step 6 asserts it is page content that does not cover the form. The application shows it as ordinary page content that scrolls away, so step 6 holds and the Expected Result's wording should follow it — route to skill 3 --revision.
- TC-HAJJ-07 step 6 says the toolbar reads "Request Direct Delivery ASN" for a plant 1100 destination and "Request ASN" for others. On purchase order 4300000834, destination 1100 / 120215, both controls were offered — route to skill 3 --revision.
- TC-HAJJ-14 precondition 3 expects [D1] on the first page of the NUPCO PO list. It is not; the PO Number filter was used to bring it on screen — route to skill 3 --revision.
- The 3b / 3c state of TC-HAJJ-04 was "draft — not app-validated (external map site not opened in this run)"; this run opened both map sites and the test case passed.
- The 3b / 3c state of TC-HAJJ-15 was "draft — not app-validated (screen could not be driven — no portal language control found)"; this run confirms no such control exists anywhere in the supplier portal.
- Transient loading indicators (TC-HAJJ-01 steps 2 and 8, TC-HAJJ-06 step 5) cannot be sampled between two command-line calls. The loaded state each one precedes was observed instead — route to skill 3 --revision if the wording should say so.
- Left in Staging: ASN 5060-261104-19824 — created by TC-HAJJ-10. ASN cancelling is switched off on this environment, so there is no way to remove it through the application.
- The run was interrupted for about five hours (07:40 to 12:59 UTC) while the VPN was down, which is included in the phase duration. TC-HAJJ-11's first attempt failed when the calendar micro-frontend timed out loading, and its second attempt ended when the browser session was lost as the request was submitted.
