# US-234822 — Hajj 1448 notice for destination W2C1 / 6000

A worked example of the Link QC pipeline, applied to one Azure DevOps user story from first
reading to a finished manual test run. Every file here was produced by a skill; nothing was
written by hand afterwards.

**The story.** When a supplier chooses the delivery destination "plant W2C1, storage location
6000" on a purchase order, the portal must show an Arabic notice naming the two warehouses that
will receive Hajj 1448 shipments. It has to appear on the purchase order details page, again on
the ASN request creation page, and in the exported ASN PDF — and nowhere else.

## The trail, stage by stage

### `01-requirements/` — skill 2, requirement review

- `US-234822-QC-review.md` — the review of the story as written, with the gaps found
- `REQ-234822-hajj-w2c1-6000-notification.md` — 11 numbered requirements derived from it
- `business-clarification-...md` — the questions put to the business, and their answers

Ten open questions came out of the review. Two were settled later by evidence during live
validation rather than by discussion.

### `02-test-design/` — skill 3 (design) and skill 3c (live validation)

- `TEST-CASES-hajj-w2c1-6000-notification.md` — 14 test cases, `Status: APPROVED`
- `TEST-DATA-hajj-w2c1-6000-notification.md` — every account, environment and data item the cases
  reference, as plain-English rows
- `TEST-CASES-...-beautified.md` — the upload shape produced by skill 4: every delegation
  expanded inline so each case stands alone in Azure DevOps
- `TC-REVIEW-hajj-w2c1-6000-notification.html` — the rendered page used for human approval
- `evidence/` — screenshots and the PDF captured while validating against the running application

A fifteenth case was designed and then withdrawn: live validation showed the direct-delivery
route it covered is never offered for this destination.

### `03-azure-publish/` — skill 4, publication to Azure DevOps

- `ADO-MAP.md` — the map from test case id to Azure DevOps work item, with the source hash, the
  tags the skill owns and the automation status it set

All 14 cases were created as Test Case work items, linked to the story with *Tested By*, then
read back and verified: **PUBLISHED AND VERIFIED, 14 of 14**.

### `04-test-run-phase-1/` — skill 5b, manual run

- `TEST-RUN-REPORT-...md` / `.html` — the run report and its rendered page
- `BUG-REPORT-...md` — the bug report
- `phase-1.json` — the machine-readable run record
- `run-progress-...log` — a timestamped line for every observation made during the run
- `screenshots/` — one assertion-point image per executed case, plus failure images

Every one of the 14 cases was executed in full against the running application through
`playwright-cli`.

## Outcome

**10 passed · 2 failed · 1 incomplete · 1 partial.** Smoke gate passed at 0% failure.

**No defect was found in the feature.** One candidate was raised during the run and then
withdrawn after checking it properly: a ship-to lookup appeared to return nothing, which turned
out to be correct behaviour — it lists only destinations not yet chosen, and that purchase order
had just one left to offer.

Both failures are the test cases' own wording, not the application:

- **TC-HAJJ-03** asks for the Hijri year's digits to sit to the left of "هـ". Measured on screen,
  "1448" sits at x 623-658 and "هـ" at x 604-618 — digits on the right, which is what correct
  right-to-left rendering produces, and what the approved notice text shows.
- **TC-HAJJ-15** assumes a portal language control. There is none anywhere in the supplier portal.

Both are recorded as open questions in the run report and routed back to the design skill for
revision, rather than filed as defects.

The remaining two cases could not finish: one stops at a step a human must perform (reading an
exported PDF), and one was lost when the VPN dropped mid-submission. The skill forbids re-running
an interrupted case in the same phase, so it carries over to phase 2.

The run also found that two recorded data items had drifted since they were written — a purchase
order had lost one of its destinations — and that a third, recorded as unavailable, does in fact
exist on the environment.
