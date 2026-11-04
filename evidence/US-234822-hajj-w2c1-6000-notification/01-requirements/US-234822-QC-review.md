# Business Review — Update displayed notification when selecting plant W2C1 - 6000 (Hajj 1448 - 2027) · Reviewed as: QC
**Reviewed as**: QC — can a tester check where and when the Hajj 1448 notice appears and exactly what it says, and does the notice send each supplier's shipment to the right warehouse?
**Date**: 2026-11-03 · **Language**: English · **Scope**: Business only — technical assessment skipped
**Source**: https://devops.nupco.com/NUPCOCollection/iNUPCO/_workitems/edit/234822 (User Story, Resolved, Priority 2, module Purchasing; parent Feature 74589 "Hajj Storage location Notification")
**Source version**: Azure DevOps revision 29 (acceptance criteria last changed 2026-10-14) · 2 discussion comments read · 1 image embedded in the acceptance criteria read
**Technical review**: not requested
**Business clarification**: [business-clarification-US-234822-hajj-w2c1-6000-notification.md](business-clarification-US-234822-hajj-w2c1-6000-notification.md)
**Reviewer**: Claude Code QC Agent

---

## In Short
This story replaces last year's Hajj notice (Hajj 1447, US 202637) with the Hajj 1448 version. Suppliers who ship to plant W2C1, storage location 6000, now see two delivery sites with map links: Maersk Logistics Park for all items and Hadda for narcotic drug items. Mohamed Sabry (QC) answered all 10 questions on 2026-11-03, so testing can start. The main answers: the alert opens only when the supplier chooses a W2C1 / 6000 Ship-to on PO details; the image embedded in the story is the reference text; narcotic items go to Hadda only. The PO should check the 10 QC answers (🔎) and correct the story wording in three small places (Appendix A).

## Dashboard

| Story | Priority | Verdict | Cmp · Clr · Tst · Con · Cor · SQ | Risk | QC view | Open H / M / L | Waiting questions |
|---|---|---|---|---|---|---|---|
| [234822 — Hajj 1448 notice for W2C1 - 6000](#story-234822--update-displayed-notification-when-selecting-plant-w2c1---6000-hajj-1448---2027) | 2 | ✅ Ready for Testing | ✅ · ✅ · ✅ · ✅ · ✅ · ✅ | 🔴 | ✅ | 0 / 0 / 3 | — |
| Spec level | — | — | — | — | — | 0 / 0 / 0 | — |

Cmp = Completeness · Clr = Clarity · Tst = Testability · Con = Consistency · Cor = Correctness ·
SQ = Story Quality. Ratings count answered findings as filled. QC view = the Perspective-Based Reading rating: ✅ Can work with it / ⚠️ Gaps for this role / ❌ Blocked for this role.

**Totals**: 0 High · 0 Medium · 3 Low open findings · 0 open Questions · status 3 Open · 0 Accepted · 0 Rejected · 8 Answered (2 Questions closed as answered — intended).

## Questions to Answer

### ✅ Answered (10)

| Q | Priority | Question | Where (story · AC) | Finding IDs | Answered by / who answers | Status |
|---|---|---|---|---|---|---|
| Q-01 | 🔴 High | Where must the alert open, now that the PO lists have no plant choice? | 234822 · AC-1 | 234822-AC1-CON-1 | Mohamed Sabry (QC) (🔎 PO to verify) | ✅ Answered — only on PO details, when the supplier chooses a W2C1 / 6000 Ship-to |
| Q-02 | 🔴 High | How does the alert behave? | 234822 · AC-1 | 234822-AC1-MIS-1 | Mohamed Sabry (QC) (🔎 PO to verify) | ✅ Answered — opens every time, one Close button, does not block, links open in a new tab |
| Q-03 | 🔴 High | Which shipments does "all types of shipments" cover? | 234822 · AC-2 | 234822-AC2-AMB-1 | Mohamed Sabry (QC) (🔎 PO to verify) | ✅ Answered — every ASN from the NUPCO POs list (normal and direct delivery), W2C1 with storage location 6000 only |
| Q-04 | 🔴 High | The written notice and the embedded image differ; which is the reference? | 234822 · AC-5 | 234822-AC5-AMB-1, 234822-AC5-TST-1 | Mohamed Sabry (QC) (🔎 PO to verify) | ✅ Answered — the image wins |
| Q-05 | 🔴 High | Where do narcotic items go? | 234822 · AC-5 | 234822-AC5-COR-1 | Mohamed Sabry (QC) (🔎 PO to verify) | ✅ Answered — Hadda only; all other items to Maersk |
| Q-06 | 🔴 High | Is the Arabic-only notice intended? | 234822 · AC-5 | 234822-AC5-QST-1 | Mohamed Sabry (QC) (🔎 PO to verify) | ✅ Answered — yes, Arabic only |
| Q-07 | 🟡 Medium | How does the notice appear on the ASN request creation page? | 234822 · AC-3 | 234822-AC3-MIS-1 | Mohamed Sabry (QC) (🔎 PO to verify) | ✅ Answered — fixed box at the top of the create page only |
| Q-08 | 🟡 Medium | Which PDF gets the notice, and where? | 234822 · AC-4 | 234822-AC4-MIS-1 | Mohamed Sabry (QC) (🔎 PO to verify) | ✅ Answered — ASN PDF only, under the header, links clickable |
| Q-09 | 🟡 Medium | From when does the 1448 notice apply, and to which ASNs? | 234822 · story | 234822-ST-MIS-1 | Mohamed Sabry (QC) (🔎 PO to verify) | ✅ Answered — at release, no end date, earlier ASNs too |
| Q-10 | 🟢 Low | Do NUPCO staff see the notice too? | 234822 · story | 234822-ST-QST-1 | Mohamed Sabry (QC) (🔎 PO to verify) | ✅ Answered — suppliers only |

## Spec Level

**Document checks**: Assumptions ✅ (answered in Q-09) · Constraints ✅ (none needed) · Out of scope ✅ (answered in Q-03, Q-10) · Shared speed, security, availability and accessibility needs ✅ (none needed for a notice) · Priority ✅ (2) · Goal / feature traced ✅ (Feature 74589)
**Clarifications**: none in the story; the 2 comments only list release numbers and the switch name, and say "Test on Purchasing".

**Dependencies**

| Dependency | Resolved path | Status | Result |
|---|---|---|---|
| Feature 74589 "Hajj Storage location Notification" (parent; states the goal) | Azure DevOps 74589 | Found | ✅ Consistent — gives the "why" this story lacks (234822-ST-STQ-1) |
| US 202637 — Hajj 1447 notice (the version this story replaces) | Azure DevOps 202637 (Closed, 7 test cases linked) | Found | ✅ Consistent after Q-09 — Tamer Logistics is no longer a Hajj site |
| US 74590 and US 79177 — the 2024 notices | Azure DevOps 74590, 79177 (Closed) | Found | ✅ Consistent after Q-06 — the English text was dropped on purpose |
| US 227711 / Feature 227640 — PO Selection UX (PO lists open without a plant choice) | `Testing/Requirements/US-227711-list-bookable-purchase-orders/` | Reused existing review | ✅ Consistent after Q-01 — the alert moves to the Ship-to choice on PO details |

**Cross-story findings**: 234822-AC1-CON-1 (234822 ↔ 227711) — answered.

**Journeys**

| Journey | Steps (story → story) | Ending | Result | Break point / Finding ID |
|---|---|---|---|---|
| Supplier books a W2C1 / 6000 PO and ships to the right Hajj site | 227711 (PO list) → PO details Ship-to → 234822 alert → ASN create page → ASN PDF | ASN raised, PDF carries the notice | ✅ Completes | — (answers Q-01, Q-05) |

---

## Story 234822 — Update displayed notification when selecting plant W2C1 - 6000 (Hajj 1448 - 2027)

**Priority 2** · **✅ Ready for Testing** · Risk 🔴 (3 High · 2 Medium · 0 Low ACs) · Questions: all answered (🔎 PO to verify) · Also affected by: none

**Why**: no open High finding, no ⚠️ or ❌ dimension, fewer than 3 open Medium findings; 3 Low findings remain. **Next**: the PO checks the 10 QC answers and fixes the story wording (Appendix A); design test cases against the embedded image.

AC numbers used in this review (the story does not number them): AC-1 alert on selecting W2C1 - 6000 from NUPCO POs · AC-2 all types of shipments · AC-3 ASN request creation details page · AC-4 exported PDF · AC-5 message text and right-to-left note.

### Issues Found

| ID | AC | Issue Type | Severity | Status | Description | Suggestion |
|----|----|------------|----------|--------|-------------|------------|
| 234822-AC1-CON-1 | AC-1 | Conflict | High | Answered | (QC) AC-1 says the supplier "selects plant W2C1 - 6000 from NUPCO POs screen". Since PO Selection UX (US 227711), that list has no plant or destination choice; the supplier picks the Ship-to on PO details. | "The alert opens when the supplier chooses a Ship-to with plant W2C1 and storage location 6000 on PO details." |
| 234822-AC1-MIS-1 | AC-1 | Missing | Medium | Answered | (QC) The "prompt alert" has no behaviour: when it opens, whether it opens again, how the supplier closes it, and whether it blocks the next step. | "The alert opens each time the W2C1 / 6000 Ship-to is chosen, shows a Close button, and does not stop the supplier from continuing; the map links open in a new tab." |
| 234822-AC2-AMB-1 | AC-2 | Ambiguous | High | Answered | "All types of shipments" is an open list. AC-2 also says "plant W2C1 - 6000" while the notice says "SLOC W2C1-6000", so it is unclear whether other storage locations of W2C1 show it. | "The notice shows for every ASN from the NUPCO POs list, normal or direct delivery, whose destination is plant W2C1 with storage location 6000, and for no other destination." |
| 234822-AC3-MIS-1 | AC-3 | Missing | Medium | Answered | (QC) AC-3 does not say how the notice appears on the ASN request creation page, or whether it stays after submission. | "On the ASN request creation page the notice shows as a fixed box at the top of the page; it does not show on the ASN pages after submission." |
| 234822-AC4-MIS-1 | AC-4 | Missing | Medium | Answered | (QC) "The exported PDF file" is not named, and its position and link format are not stated. The PDF is the record suppliers keep, so a wrong PDF misleads deliveries. | "The ASN PDF for a W2C1 / 6000 destination shows the notice, with its table and the two map links as clickable text, under the PDF header." |
| 234822-AC5-AMB-1 | AC-5 | Ambiguous | High | Answered | The written notice and the image embedded in the story differ: row 1 says "Maersk Logistics Park (MLP)" in the text but "Maersk Logistics Park (MLP), Nupco WH" in the image, and the closing lines "شكرًا لتعاونكم / مع أطيب التحيات" are only in the text. A tester cannot tell which one passes. | "The notice matches the attached image word for word"; remove the written copy or make it match the image. |
| 234822-AC5-TST-1 | AC-5 | Testability | Medium | Answered | (QC) "Make sure that the text direction is correct … so the symbols be in the correct place" has no clear pass or fail. The written text itself puts the colon on the wrong side (":(SLOC W2C1-6000) في المواقع ادناه"); the image has it right ("(SLOC W2C1-6000) في المواقع ادناه:"). | "The notice reads right to left, and the colon, brackets, Hijri year and links appear exactly as in the attached image." |
| 234822-AC5-COR-1 | AC-5 | Correctness | High | Answered | (QC · business) The table sends "جميع البنود" (all items) to Maersk Logistics Park and "بنود الادوية المخدرة" (narcotic drug items) to Hadda. A narcotic item matches both rows. See Notes. | Change the Maersk row to "all items except narcotic drug items". |
| 234822-AC5-AMB-2 | AC-5 | Ambiguous | Low | Open | Small wording errors appear in both the text and the image: no space after the colon in "إشعار هام:يرجى", and "إستلام", "ادناه", "الادوية" are usually spelled "استلام", "أدناه", "الأدوية". The text also has spaces inside "( حدا )". Testers will compare against the image as it is. | Correct the spelling in the image and the text, or confirm the current spelling is the approved one. |
| 234822-AC5-ATM-1 | AC-5 | Atomicity | Low | Open | AC-5 mixes the message text, the right-to-left rule and a repeat of AC-3 and AC-4 ("Message to be added in ASN request creation details page and exported PDF file"). In Azure DevOps the table header "الموقع" is white on white, so it cannot be seen. | Split AC-5 into "Notice text" (the attached image) and "Text direction", drop the repeated line, and make the header visible. |
| 234822-ST-STQ-1 | story | Story Quality | Low | Open | The story is written for "System", with no role, need or benefit; the reason is only in Feature 74589. It is a copy of US 202637 with new table rows. | "As a supplier shipping to plant W2C1 / storage location 6000, I want to see the Hajj 1448 delivery sites, so that I deliver each item to the right warehouse." |
| 234822-ST-MIS-1 | story | Missing | Medium | Answered | (QC · business) The story does not say from when the 1448 notice replaces the 1447 one, when it stops, or what an ASN raised earlier shows when its PDF is exported again. It also drops last year's Tamer Logistics site without saying so. | "From release, all W2C1 / 6000 notices show the 1448 text, including PDFs of earlier ASNs; the notice stays until replaced. Tamer Logistics is no longer a Hajj delivery site." |

**Notes — 234822-AC5-COR-1** (as written, before the answer)

| Item type | Maersk Logistics Park ("all items") | Hadda ("narcotic drug items") | Result |
|---|---|---|---|
| Narcotic drug item | matches | matches | ❌ two sites — answered: Hadda only |
| Any other item | matches | — | ✅ Maersk |

### Risk (P1 ACs)

| AC | Impact | Why (impact) | C | A | N | D | Likelihood |
|---|---|---|---|---|---|---|---|
| AC-1 | High | A supplier who misses the notice sends Hajj stock to the wrong warehouse | 2 | 1 | 3 | 2 | 8 → Medium |
| AC-2 | High | A shipment type left out means its suppliers never see the Hajj sites | 3 | 1 | 3 | 2 | 9 → Medium |
| AC-5 | High | Wrong text sends items, including narcotics, to the wrong site | 2 | 2 | 3 | 1 | 8 → Medium |

AC-3 (Medium impact, 7 → Medium) and AC-4 (Medium impact, 7 → Medium) are 🟡 P2.

### Test Coverage Scope

| Area | ACs | Priority | Notes |
|------|-----|----------|-------|
| Alert when choosing the W2C1 / 6000 Ship-to on PO details | AC-1, AC-2 | P1 | Positive with W2C1 / 6000; negative with W2C1 and another storage location, and with another plant; the alert opens again on each choice; Close works; no alert on the PO list itself. |
| Notice text, table and links | AC-5 | P1 | Compare against the embedded image; both map links open the named sites in a new tab; right-to-left layout; no 1447 text (Tamer Logistics) remains; Arabic in every language setting. |
| Shipment types | AC-2 | P1 | Normal and direct-delivery ASNs from the NUPCO POs list. Last year's 7 test cases on US 202637 can be reused as a base. |
| ASN request creation page | AC-3 | P2 | Fixed box at the top for W2C1 / 6000 only; not on the ASN pages after submission. |
| Exported ASN PDF | AC-4 | P2 | Notice under the header with table and clickable links; an ASN created before the release shows the 1448 notice when exported again. |

### Recommended Acceptance Criteria

- **Given** a supplier on PO details of a NUPCO PO, **when** they choose a Ship-to with plant W2C1 and storage location 6000, **then** the Hajj 1448 notice opens, matching the attached image.
- **Given** a supplier on PO details, **when** they choose any other plant or storage location, **then** no Hajj notice opens.
- **Given** the Hajj notice, **when** the supplier reads the table, **then** narcotic drug items go to Hadda and all other items go to Maersk Logistics Park, each with a map link that opens that site.

---

## Appendix

### A. Clarified Rules

| Finding ID | Story | Rule as answered | Answered by | Date | In source yet? |
|---|---|---|---|---|---|
| 234822-AC1-CON-1 | 234822 | The alert opens only on PO details, when the supplier chooses a Ship-to with plant W2C1 and storage location 6000; the PO lists show no alert. | Mohamed Sabry (QC) | 2026-11-03 | No — clarified: 234822-AC1-CON-1, not yet in source |
| 234822-AC1-MIS-1 | 234822 | The alert opens every time that Ship-to is chosen, closes with one button, does not block the next step; map links open in a new tab. | Mohamed Sabry (QC) | 2026-11-03 | No — clarified: 234822-AC1-MIS-1, not yet in source |
| 234822-AC2-AMB-1 | 234822 | "All types of shipments" means the normal ASN only, raised from the NUPCO POs list with destination plant W2C1 and storage location 6000. (Corrected 2026-11-03 from "normal and direct delivery".) | Mohamed Sabry (QC) | 2026-11-03 | No — clarified: 234822-AC2-AMB-1, not yet in source |
| 234822-AC3-MIS-1 | 234822 | On the ASN request creation page the notice is a fixed box at the top; it is not shown on the ASN pages after submission. | Mohamed Sabry (QC) | 2026-11-03 | No — clarified: 234822-AC3-MIS-1, not yet in source |
| 234822-AC4-MIS-1 | 234822 | Only the ASN PDF of a W2C1 / 6000 destination carries the notice, under the PDF header, with the table and clickable map links. | Mohamed Sabry (QC) | 2026-11-03 | No — clarified: 234822-AC4-MIS-1, not yet in source |
| 234822-AC5-AMB-1, 234822-AC5-TST-1 | 234822 | The image embedded in the story is the reference: row 1 reads "Maersk Logistics Park (MLP), Nupco WH", there are no closing lines, and the colon ends the second line. | Mohamed Sabry (QC) | 2026-11-03 | No — clarified: 234822-AC5-AMB-1, not yet in source (the written text still differs) |
| 234822-AC5-COR-1 | 234822 | Narcotic drug items go to Hadda only; all other items go to Maersk Logistics Park. | Mohamed Sabry (QC) | 2026-11-03 | No — clarified: 234822-AC5-COR-1, not yet in source |
| 234822-AC5-QST-1 | 234822 | The notice is Arabic only, in every language setting; the English text of 2024 was dropped on purpose. | Mohamed Sabry (QC) | 2026-11-03 | No — clarified: 234822-AC5-QST-1, not yet in source |
| 234822-ST-MIS-1 | 234822 | The 1448 notice replaces the 1447 one at release, with no end date, including re-exported PDFs of earlier ASNs; Tamer Logistics is no longer a Hajj site. | Mohamed Sabry (QC) | 2026-11-03 | No — clarified: 234822-ST-MIS-1, not yet in source |
| 234822-ST-QST-1 | 234822 | Only suppliers see the notice. | Mohamed Sabry (QC) | 2026-11-03 | No — clarified: 234822-ST-QST-1, not yet in source |

### B. Reviewer Replies

| Finding ID | Issue Type | Reply author | Date | Source | Classification → Status | Reply text | Effect on rating |
|------------|------------|--------------|------|--------|-------------------------|------------|------------------|
| 234822-AC1-CON-1 | Conflict | Mohamed Sabry (QC) | 2026-11-03 | resolution gate | Answered → Answered | "PO details Ship-to only" | Consistency ⚠️ → ✅ |
| 234822-AC1-MIS-1 | Missing | Mohamed Sabry (QC) | 2026-11-03 | resolution gate | Answered → Answered | "Every time, Close button" | Completeness ⚠️ → ✅ |
| 234822-AC2-AMB-1 | Ambiguous | Mohamed Sabry (QC) | 2026-11-03 | resolution gate | Answered → Answered | "NUPCO POs ASNs only" | Clarity ⚠️ → ✅ |
| 234822-AC5-AMB-1 | Ambiguous | Mohamed Sabry (QC) | 2026-11-03 | resolution gate | Answered → Answered | "there is no reference, check what is broken and tell me", then, after the comparison with the embedded image: "The image wins" | Clarity ⚠️ → ✅; description corrected (the table is a real table; the image was missed in the first pass) |
| 234822-AC5-TST-1 | Testability | Mohamed Sabry (QC) | 2026-11-03 | resolution gate | Answered → Answered | "The image wins" | Testability ⚠️ → ✅ |
| 234822-AC5-COR-1 | Correctness | Mohamed Sabry (QC) | 2026-11-03 | resolution gate | Answered → Answered | "Hadda only" | Correctness ⚠️ → ✅ |
| 234822-AC5-QST-1 | Question | Mohamed Sabry (QC) | 2026-11-03 | resolution gate | Answered → closed (answered — intended) | "Arabic only is intended" | none |
| 234822-AC3-MIS-1 | Missing | Mohamed Sabry (QC) | 2026-11-03 | resolution gate | Answered → Answered | "Fixed box, create page only" | none |
| 234822-AC4-MIS-1 | Missing | Mohamed Sabry (QC) | 2026-11-03 | resolution gate | Answered → Answered | "ASN PDF, under header" | none |
| 234822-ST-MIS-1 | Missing | Mohamed Sabry (QC) | 2026-11-03 | resolution gate | Answered → Answered | "Replace at release, no end" | Completeness ⚠️ → ✅ |
| 234822-ST-QST-1 | Question | Mohamed Sabry (QC) | 2026-11-03 | resolution gate | Answered → closed (answered — intended) | "Suppliers only" | none |

### C. Closed Findings

| Finding ID | Closed on | Reason |
|------------|-----------|--------|
| 234822-AC5-QST-1 | 2026-11-03 | answered — intended |
| 234822-ST-QST-1 | 2026-11-03 | answered — intended |
