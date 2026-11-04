# Business Clarification — Update displayed notification when selecting plant W2C1 - 6000 (Hajj 1448 - 2027)
**Date**: 2026-11-03
**Source**: https://devops.nupco.com/NUPCOCollection/iNUPCO/_workitems/edit/234822
**Business review(s)**: [US-234822-QC-review.md](US-234822-QC-review.md)
**Answered by**: Mohamed Sabry (QC) — 2026-11-03

---

## In Short
Mohamed Sabry (QC) answered all 10 questions on 2026-11-03, so testing can start. Because the answers came from QC, the PO should check all 10 (🔎) and fill in "PO check". The most important are Q-01 (the alert opens only on PO details), Q-04 (the image in the story is the reference text) and Q-05 (narcotic items go to Hadda only). No question is waiting for a PO decision.

---

## Answered Questions
PO: please check each row flagged 🔎 and fill in "PO check".

| Q | Priority | Question | Answer | Answered by | Date | PO review | PO check | Where (story · AC) | Finding IDs |
|---|---|---|---|---|---|---|---|---|---|
| Q-01 | 🔴 High | The PO lists no longer let the supplier choose a plant, so where must the alert open? | Only on PO details, when the supplier chooses a Ship-to with plant W2C1 and storage location 6000. The PO lists show no alert. | Mohamed Sabry (QC) | 2026-11-03 | 🔎 Yes — PO to verify | | 234822 · AC-1 | 234822-AC1-CON-1 |
| Q-02 | 🔴 High | How does the alert behave? | It opens every time that Ship-to is chosen, closes with one button and does not block the next step. The map links open in a new tab. | Mohamed Sabry (QC) | 2026-11-03 | 🔎 Yes — PO to verify | | 234822 · AC-1 | 234822-AC1-MIS-1 |
| Q-03 | 🔴 High | Which shipments does "all types of shipments" cover? | The normal ASN only, raised from the NUPCO POs list with destination plant W2C1 and storage location 6000. (was: normal and direct delivery — corrected by Mohamed Sabry on 2026-11-03; the live run showed a Hajj destination offers "Request ASN" only) | Mohamed Sabry (QC) | 2026-11-03 | 🔎 Yes — PO to verify | | 234822 · AC-2 | 234822-AC2-AMB-1 |
| Q-04 | 🔴 High | The written notice and the image in the story differ. Which is the reference? | The image, except that it was cropped: row 1 reads "Maersk Logistics Park (MLP), Nupco WH", the colon ends the second line, and the notice ends with "شكرًا لتعاونكم / مع أطيب التحيات" as the written text says. (was: the image with no closing lines — corrected by Mohamed Sabry on 2026-11-03 after the live run showed the greeting) | Mohamed Sabry (QC) | 2026-11-03 | 🔎 Yes — PO to verify | | 234822 · AC-5 | 234822-AC5-AMB-1, 234822-AC5-TST-1 |
| Q-05 | 🔴 High | Maersk takes "all items" and Hadda takes "narcotic drug items". Where do narcotic items go? | Hadda only. All other items go to Maersk Logistics Park. | Mohamed Sabry (QC) | 2026-11-03 | 🔎 Yes — PO to verify | | 234822 · AC-5 | 234822-AC5-COR-1 |
| Q-06 | 🔴 High | Is the Arabic-only notice intended? | Yes. The notice is Arabic only, in every language setting. | Mohamed Sabry (QC) | 2026-11-03 | 🔎 Yes — PO to verify | | 234822 · AC-5 | 234822-AC5-QST-1 |
| Q-07 | 🟡 Medium | How does the notice appear on the ASN request creation page? | As a fixed box at the top of the create page. It is not shown on the ASN pages after submission. | Mohamed Sabry (QC) | 2026-11-03 | 🔎 Yes — PO to verify | | 234822 · AC-3 | 234822-AC3-MIS-1 |
| Q-08 | 🟡 Medium | Which exported PDF gets the notice, and where? | Only the ASN PDF of a W2C1 / 6000 destination, under the PDF header, with the table and clickable map links. | Mohamed Sabry (QC) | 2026-11-03 | 🔎 Yes — PO to verify | | 234822 · AC-4 | 234822-AC4-MIS-1 |
| Q-09 | 🟡 Medium | From when does the 1448 notice apply, and to which ASNs? | From release, with no end date, including re-exported PDFs of earlier ASNs. Tamer Logistics is no longer a Hajj site. | Mohamed Sabry (QC) | 2026-11-03 | 🔎 Yes — PO to verify | | 234822 · story | 234822-ST-MIS-1 |
| Q-10 | 🟢 Low | Do NUPCO staff see the notice too? | No, only suppliers. | Mohamed Sabry (QC) | 2026-11-03 | 🔎 Yes — PO to verify | | 234822 · story | 234822-ST-QST-1 |

---

## Note to the PO
Hello, we reviewed **US 234822 — Hajj 1448 notice for W2C1 - 6000**. Please check the 10 answers above; QC answered them, not the PO. Please also update the story in three places:
1. Make the written notice match the image (row 1 "…, Nupco WH"; remove the closing lines; put the colon at the end of the second line). Better still, keep only the image.
2. Change "selects plant W2C1 - 6000 from NUPCO POs screen" to "chooses a Ship-to with plant W2C1 and storage location 6000 on PO details".
3. Change the Maersk row to "all items except narcotic drug items".

The spelling of "إستلام", "ادناه" and "الادوية" also needs a check (finding 234822-AC5-AMB-2). When you reply, give the answers to the skill ("the PO confirmed Q-01", "the PO corrected Q-03: …"), and it will update the review.
