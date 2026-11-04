# REQ-234822 — Hajj 1448 notification for plant W2C1 - 6000

**Story:** US-234822 "System | Update displayed notification when selecting plant W2C1 - 6000 (Hajj 1448 -2027)"
**Source:** https://devops.nupco.com/NUPCOCollection/iNUPCO/_workitems/edit/234822 — Azure DevOps revision 29
**Parent feature:** 74589 "Hajj Storage location Notification"
**Module:** Purchasing · **Priority:** 2 · **State:** Resolved
**Impacted areas (from the story):** PO list · ASN Creation · ASN exported PDF
**Business review:** [US-234822-QC-review.md](US-234822-QC-review.md) · **Clarifications:** [business-clarification-US-234822-hajj-w2c1-6000-notification.md](business-clarification-US-234822-hajj-w2c1-6000-notification.md)
**Generated:** 2026-11-03 by link-qc-3-generate-manual-test-cases (entry case 2 — no requirement file existed)

---

## 1. Description

Suppliers who send Hajj stock to storage location 6000 of plant W2C1 must be told where to deliver
it. Every year the delivery sites change, so the notice is replaced. This story replaces the Hajj
1447 notice (US 202637) with the Hajj 1448 version: two delivery sites instead of three, each with
a map link. The notice is shown to the supplier while they prepare the shipment, and is carried
into the ASN PDF so it stays with the paperwork.

**As a** supplier shipping to plant W2C1, storage location 6000,
**I want** to see the Hajj 1448 delivery sites while I prepare the shipment,
**so that** I deliver each item to the right warehouse.

## 2. Roles

| Role | Involvement |
|---|---|
| Supplier | Sees the notice on PO details, on the ASN request creation page and in the exported ASN PDF. |
| NUPCO staff | Out of scope — see REQ-234822-11. |

## 3. Acceptance criteria and requirement IDs

Ten of the eleven statements below come from the story's acceptance criteria. Where the story was
unclear, the rule is the answer Mohamed Sabry (QC) gave in the business clarification on
2026-11-03; those answers are marked **(clarified)** and still need the PO's verification.

| REQ ID | Requirement | Source |
|---|---|---|
| REQ-234822-01 | The Hajj notice opens when the supplier chooses a Ship-to with plant W2C1 and storage location 6000 on the PO details page. It does not open on the PO lists. | AC-1 + **(clarified)** Q-01 |
| REQ-234822-02 | The notice applies to the normal ASN raised from the NUPCO POs list whose destination is plant W2C1 with storage location 6000 — and to no other plant or storage location. A Hajj destination offers no Direct Delivery ASN. | AC-2 + **(clarified)** Q-03, corrected 2026-11-03 |
| REQ-234822-03 | The notice is shown as a fixed box at the top of the ASN request creation details page. It is not shown on the ASN pages after the ASN is submitted. | AC-3 + **(clarified)** Q-07 |
| REQ-234822-04 | The exported ASN PDF of a W2C1 / 6000 destination carries the notice, with its table and both map links as clickable text, under the PDF header. | AC-4 + **(clarified)** Q-08 |
| REQ-234822-05 | The notice content matches the image attached to the story: the title, the intro sentence naming Hajj 1448 and storage location W2C1-6000, a three-column table (التصنيف · مكان التوريد · الموقع) and two site rows, each with its map link. | AC-5 + **(clarified)** Q-04 |
| REQ-234822-06 | The notice reads right to left, and the colon, the brackets, the Hijri year and the links appear exactly as in the attached image. | AC-5 (text-direction note) |
| REQ-234822-07 | The notice opens every time the W2C1 / 6000 destination is chosen, closes with one control, does not stop the supplier from continuing, and its map links open in a new tab. | **(clarified)** Q-02 |
| REQ-234822-08 | The notice is shown in Arabic only, whatever language the portal is set to. | **(clarified)** Q-06 |
| REQ-234822-09 | Narcotic drug items are delivered to Hadda (Nupco Haddah WH); all other items go to Maersk Logistics Park (MLP), Nupco WH. | AC-5 table + **(clarified)** Q-05 |
| REQ-234822-10 | From release, every W2C1 / 6000 notice shows the Hajj 1448 text, including a re-exported PDF of an ASN created earlier. The Hajj 1447 content, including the Tamer Logistics site, no longer appears. | **(clarified)** Q-09 |
| REQ-234822-11 | Only suppliers see the notice. | **(clarified)** Q-10 |

## 4. The approved notice (reference content)

The reference is the image embedded in the story's acceptance criteria, not the written copy
beside it — the two differ (business review finding 234822-AC5-AMB-1). The image shows:

- Title: **تنبيه**, with an information icon, on a light blue panel, aligned right.
- Intro, over two lines, ending with a colon:
  **إشعار هام:يرجى التنويه بأنه سيكون مقر إستلام الشحنات الخاصة بالحج لعام 1448 هـ لموقع توريد (SLOC W2C1-6000) في المواقع ادناه:**
- A table with three column headers, right to left: **التصنيف · مكان التوريد · الموقع**.

| التصنيف (classification) | مكان التوريد (delivery place) | الموقع (location) |
|---|---|---|
| جميع البنود | مستودعات نوبكو (الميناء) · Nupco WH | Maersk Logistics Park (MLP), Nupco WH · https://maps.app.goo.gl/zbWJWBYQbWRjqmaWA |
| بنود الادوية المخدرة | مستودعات نوبكو (حدا) · Nupco Haddah WH | Hadda · https://maps.google.com/?q=21.448376,39.568314 |

- The notice ends with two closing lines, **"شكرًا لتعاونكم"** and **"مع أطيب التحيات"**. The written
  copy in the story has them; the image does not, because it was cropped (confirmed by Mohamed
  Sabry, QC, on 2026-11-03 — PO to verify).

## 5. Out of scope

- NUPCO staff screens (REQ-234822-11 states suppliers only).
- The Customer PO list — the predecessor behaviour never showed the notice there.
- Any change to how a Ship-to is chosen, or to the ASN flow itself.

## 6. Open questions

| # | Question | Status |
|---|---|---|
| 1 | Does the notice also appear on the NUPCO and Return PO lists? The project's Purchasing knowledge base records that it does; the clarified answer Q-01 says PO details only. | Open — the TC set is designed to "PO details only" (Q-1 in the TC document) |
| 2 | Can a W2C1 / 6000 destination raise a Direct Delivery ASN at all? The project's recorded plant rules suggest the Direct Delivery control is not offered for plant W2C1. | Open — Q-2 in the TC document |
| 3 | Is the spelling in the approved image correct (إستلام, ادناه, الادوية)? | Open — business review finding 234822-AC5-AMB-2 |
| 4 | Do NUPCO staff see the notice on their own screens? Declared out of scope, so no test case covers REQ-234822-11. | Open — Q-5 in the TC document |

## 7. Predecessor stories

| Story | What it delivered | Note for testing |
|---|---|---|
| US 74590 (2024) | The first notice: English and Arabic, one site (MOH Makkah — Haddah). | Closed |
| US 79177 (2024) | Added a GPS link to the same notice. | Closed |
| US 202637 (Hajj 1447) | Three sites: Tamer Logistics, Maersk Logistics Park, Hadda. Has 7 test cases (202916–202922). | The 7 test cases were read as input for this design; they describe the pre-PO-Selection-UX flow and the 1447 sites, so they are not reused as they stand. |
