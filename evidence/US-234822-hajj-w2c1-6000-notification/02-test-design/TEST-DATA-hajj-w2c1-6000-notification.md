# Test Data — hajj-w2c1-6000-notification
**Story:** US-234822 · **TC document:** TEST-CASES-hajj-w2c1-6000-notification.md (2026-11-03, revision 1) · **Environment:** Staging checked 2026-11-03 by link-qc-3c
**Data items:** 6 — ready 5 · missing 0 · not creatable 0 · impossible 0 · unknown 1
**Accounts needed:** 1 account — 1 confirmed · 0 unknown
**Environment rows:** 2 — 2 ready · 0 unknown

**Required flags:** planetSLOC=true

link-qc-3c looked at Staging on 2026-11-03 with account [A1]. On its re-run, with the user's
go-ahead, it created one ASN — **5060-261103-19820** — which is kept in Staging as [D5].

The key item [D1] is now found and confirmed: **purchase order 4300000831** offers the Hajj
destination. Its Ship-to lookup holds exactly two rows, which is why [D2] is missing and why the
direct-delivery item was dropped. Purchase orders arrive from SAP and change over time, so re-check these values
before a run if they are more than a few days old.

## 0. Environment

| ID | What | Value | Status |
|---|---|---|---|
| E1 | application base URL | https://in-stag.nupco.com/ | READY |
| E2 | the Hajj notice feature switch for this environment — it lives in the release settings, and a change needs a redeploy by the release owner | Azure DevOps variable group "Feature Flag Toggle Variable (Stag)", switch `planetSLOC`, recorded as on for Staging on 2026-10-29 | READY |

E1 comes from the learning file: all testing runs on Staging in Google Chrome on the desktop, and
every NUPCO host needs the VPN. Supplier sign-in goes through the NUPCO single sign-on page; on
the public home page it is the "Login" button under "Supplier Management".

## 1. Accounts

| ID | Role | Username | Status | Used by TCs | Note |
|---|---|---|---|---|---|
| A1 | ASN supplier | user1@yahoo.com (`asn-supplier`) | READY | TC-HAJJ-01, TC-HAJJ-02, TC-HAJJ-03, TC-HAJJ-04, TC-HAJJ-05, TC-HAJJ-06, TC-HAJJ-07, TC-HAJJ-08, TC-HAJJ-10, TC-HAJJ-11, TC-HAJJ-12, TC-HAJJ-13, TC-HAJJ-14, TC-HAJJ-15 | Salehiya Trading Co. Confirmed on 2026-11-03: this account reaches purchase order 4300000831, which offers the W2C1 / 6000 destination [D1]. The role label was supplied by the user and is not verified in the application. |

## 2. Test data at a glance

| # | Data item (plain name) | Must look like | Used by TCs | Status | Best way to get it |
|---|---|---|---|---|---|
| D1 | a bookable NUPCO purchase order that can ship to plant W2C1, storage location 6000 | **purchase order 4300000831** (PO date 20-10-2026, type Z113, 10,072,000 SAR, customer KAMC). Its Ship-to lookup offers "W2C1 / 6000 — MOH - Al Hajj", warehouse MAERSK, inventory type 3PL Warehouse, region Jeddah; three line items; a second destination "1100 / 120364 — KAMC" | TC-HAJJ-01, TC-HAJJ-02, TC-HAJJ-03, TC-HAJJ-04, TC-HAJJ-05, TC-HAJJ-08, TC-HAJJ-10, TC-HAJJ-11, TC-HAJJ-13, TC-HAJJ-14, TC-HAJJ-15 | READY | — found on Staging 2026-11-03 |
| D2 | a bookable NUPCO purchase order that can ship to plant W2C1 on a storage location other than 6000 | **purchase order 4300000834**, destination "W2C1 / 1000 — MOH Stock" (warehouse MAERSK, 3PL Warehouse, Jeddah). Also offered on 4300000835, 4300000832 and 4300000829; 4300000833 offers "W2C1 / 4000 — MOH - Makkah" | TC-HAJJ-06 | READY | — found on Staging 2026-11-04 |
| D3 | a bookable NUPCO purchase order with a destination on any plant other than W2C1 | **purchase order 4300000831**, destination "1100 / 120364 — KAMC - King Abdullah Medical City"; the same purchase order as [D1] | TC-HAJJ-07 | READY | — found on Staging 2026-11-03 |
| D4 | the approved Hajj 1448 notice text | title "تنبيه", the intro sentence, three column headers, exactly two site rows with their map links, and the closing lines "شكرًا لتعاونكم" and "مع أطيب التحيات". The story's written acceptance-criteria text is the reference; the image attached beside it is cropped and omits the closing lines | TC-HAJJ-02, TC-HAJJ-03, TC-HAJJ-04, TC-HAJJ-08, TC-HAJJ-11, TC-HAJJ-12, TC-HAJJ-13, TC-HAJJ-15 | READY | — |
| D5 | an ASN this run raises on the W2C1 / 6000 destination | created by preparation: a submitted ASN for one line item of [D1], with its ASN number from the success message | TC-HAJJ-10, TC-HAJJ-11 | READY | — **ASN 5060-261103-19820** (invoice QA3C-234822-1103, batch QA3CB1, GTIN 04110410701401, 10 units, delivery 10-11-2026 10:00 am), created 2026-11-03 by TC-HAJJ-10 and kept |
| D7 | an ASN created before the Hajj 1448 release, on a W2C1 / 6000 destination | an ASN whose creation date is before the release date of this story, whose destination is plant W2C1 storage location 6000, and whose PDF can be exported again | TC-HAJJ-12 | UNKNOWN | manual — search "My Requests" (45,425 requests) for an ASN on W2C1 / 6000 created before the release; see Problems #3 |

## 3. Data item details

### D1 — a bookable NUPCO purchase order that can ship to plant W2C1, storage location 6000
- **What it is:** the purchase order almost every test case starts from. Its Ship-to lookup must offer the Hajj storage location, because that choice is what opens the notice.
- **Exact values needed:** a Ship-to row with plant code "W2C1" and storage location "6000"; at least one line item that can be selected and requested; at least one other destination, so TC-HAJJ-05 can switch away and back.
- **Used by:** TC-HAJJ-01, TC-HAJJ-02, TC-HAJJ-03, TC-HAJJ-04, TC-HAJJ-05, TC-HAJJ-08, TC-HAJJ-10, TC-HAJJ-11, TC-HAJJ-13, TC-HAJJ-14, TC-HAJJ-15
- **Where I checked:** not checked — this design run opens no browser. The learning file records the supplier's purchase order counts but not their destinations.
- **Status:** UNKNOWN — nobody has yet confirmed that this supplier has a purchase order offering the Hajj destination.
- **Shared with other TCs:** yes — these eleven test cases use the same purchase order. TC-HAJJ-14 also needs it to be listed on the first page of the NUPCO PO list.

### D2 — a bookable NUPCO purchase order that can ship to plant W2C1 on a storage location other than 6000
- **What it is:** the near-miss case. It proves the notice is tied to the storage location, not to the plant.
- **Exact values needed:** a Ship-to row with plant code "W2C1" and any storage location other than "6000"; the storage location code is recorded once found, so the test case can name it.
- **Used by:** TC-HAJJ-06
- **Where I checked:** not checked.
- **Status:** UNKNOWN — it is not known whether plant W2C1 has any other storage location this supplier can ship to. If it has none, TC-HAJJ-06 cannot run and the near-miss is covered only by TC-HAJJ-07.
- **Shared with other TCs:** no.

### D3 — a bookable NUPCO purchase order with a destination on any plant other than W2C1
- **What it is:** the plain negative case: an ordinary destination that must show no notice.
- **Exact values needed:** a Ship-to row whose plant code is not "W2C1"; at least one line item that can be requested, so step 6 can open the ASN request creation page.
- **Used by:** TC-HAJJ-07
- **Where I checked:** not checked.
- **Status:** UNKNOWN — expected to be easy to find among the supplier's 1624 purchase orders, but not confirmed.
- **Shared with other TCs:** no.

### D4 — the approved Hajj 1448 notice text
- **What it is:** the reference the whole content check is judged against. The story's written acceptance-criteria text is the reference: the image embedded beside it is cropped and omits the two closing lines, which the application does show (Q-6, 2026-11-03). The PO should attach a complete image.
- **Exact values needed:** title "تنبيه"; intro "إشعار هام: يرجى التنويه بأنه سيكون مقر إستلام الشحنات الخاصة بالحج لعام 1448 هـ لموقع توريد (SLOC W2C1-6000) في المواقع ادناه:"; column headers "التصنيف", "مكان التوريد", "الموقع"; row 1 "جميع البنود" · "مستودعات نوبكو (الميناء) / Nupco WH" · "Maersk Logistics Park (MLP), Nupco WH" with the link https://maps.app.goo.gl/zbWJWBYQbWRjqmaWA; row 2 "بنود الادوية المخدرة" · "مستودعات نوبكو (حدا) / Nupco Haddah WH" · "Hadda" with the link https://maps.google.com/?q=21.448376,39.568314; then the closing lines "شكرًا لتعاونكم" and "مع أطيب التحيات".
- **Used by:** TC-HAJJ-02, TC-HAJJ-03, TC-HAJJ-04, TC-HAJJ-08, TC-HAJJ-11, TC-HAJJ-12, TC-HAJJ-13, TC-HAJJ-15
- **Where I checked:** the story's acceptance criteria, Azure DevOps revision 29, read on 2026-11-03.
- **Status:** READY — the image is attached to the story and was read.
- **Shared with other TCs:** yes — nine test cases compare against the same image. It is read-only; nobody changes it.

### D5 — an ASN this run raises on the W2C1 / 6000 destination
- **What it is:** a real ASN, created by the test run itself, so the submitted-ASN page and the exported PDF can be checked.
- **Exact values needed:** created by preparation — submitted from one line item of [D1] with the W2C1 / 6000 destination; its ASN number is read from the success message and used to find it again.
- **Used by:** TC-HAJJ-10, TC-HAJJ-11
- **Where I checked:** not checked.
- **Status:** UNKNOWN — it does not exist yet and depends on [D1].
- **Shared with other TCs:** yes — TC-HAJJ-11 needs the ASN TC-HAJJ-10 creates, so TC-HAJJ-10 runs first.

### D7 — an ASN created before the Hajj 1448 release, on a W2C1 / 6000 destination
- **What it is:** the proof that an old document picks up the new notice when exported again.
- **Exact values needed:** an ASN whose creation date is before this story's release date, whose destination is plant W2C1 storage location 6000, and whose PDF can still be exported.
- **Used by:** TC-HAJJ-12
- **Where I checked:** not checked.
- **Status:** UNKNOWN — it either already exists on the environment or it does not; it cannot be made now, because any ASN created today is after the release.
- **Shared with other TCs:** no.

## 4. Problems — data that cannot be created or is unclear

| # | Data item | Problem | Why | What the QC / PO must decide |
|---|---|---|---|---|
| 1 | D5 | **Solved 2026-11-03** — the ASN was created (5060-261103-19820) once the NUPCO GLN row existed and the GTIN was typed in the line's batch row, reached through two expand arrows. The history below is kept for reference. Earlier reading: the ASN cannot be created: the line's item has no GTIN on Staging | Second attempt, 2026-11-03, after the NUPCO GLN for W2C1 / 6000 was added to the RSD GLN table (the form now fills NUPCO GLN 6286844000555 by itself). With Invoice number "QA3C-234822-1103", Delivery Date 10-11-2026, Delivery Time 10:00 am and 1 pallet, "Create" shows a short message "Please fill GTIN for trade 4110410701401." and creates nothing. The form has no GTIN field, so the GTIN must come from the item's master data. The first attempt failed the same way; the message vanished before it was read. Without this ASN, TC-HAJJ-10 and TC-HAJJ-11 cannot run. | Add a GTIN for trade code 4110410701401 (VACUTAINER HOLDER SINGLE USE BD) in Staging's item master data, the same way the GLN was added — or name another W2C1 / 6000 purchase order whose items already carry a GTIN. A GTIN is never invented by the test run. |
| 2 | D2 | **Solved 2026-11-04** — found on purchase order 4300000834 (W2C1 / 1000). Earlier reading: no second W2C1 storage location was found | Purchase order 4300000831 offers exactly two destinations: plant 1100 / 120364 and plant W2C1 / 6000. The "same plant, different storage location" case cannot be tested on it. | Look at other purchase orders' Ship-to lookups for a second W2C1 storage location. If the supplier has none, accept that TC-HAJJ-06 cannot run and rely on TC-HAJJ-07 for the negative case, or ask for suitable data from SAP. |
| 3 | D7 | An ASN from before the release cannot be created now — it has to be found | Any ASN created today is created after the release. Submitted ASNs are listed under "My Requests" (not the page checked first), which holds 45,425 requests for this account, so a suitable one very likely exists but was not searched for. | Decide whether to accept that TC-HAJJ-12 cannot run on this environment, or to check it on an environment that holds older ASNs. |
| 4 | — | **Closed 2026-11-03.** The Direct Delivery control is never offered for a Hajj destination, so the former item D6 and its test case TC-HAJJ-09 were withdrawn in the revision of 2026-11-03. | With W2C1 / 6000 chosen the toolbar offers "Request ASN" only; with plant 1100 on the same purchase order it offers "Request Direct Delivery ASN" only. | Nothing for testing. The PO still has to correct the story's scope wording. |

## 5. How to prepare the missing data

### D1, D2 and D3 — the three purchase orders  (recommended: e2e scenario)

| Way | How, in plain words | Cleanup after | Availability |
|---|---|---|---|
| e2e scenario | Sign in as the ASN supplier [A1], open the "NUPCO POs" tile, and open purchase orders one by one. On each PO Details page open the Ship-to lookup and read its Plant code column: a row with "W2C1" and storage location "6000" gives [D1]; a row with "W2C1" and another storage location gives [D2]; any row with another plant gives [D3]. Write down the PO numbers and the exact storage location codes. The lookup has a filter on the Plant code column, which makes the search quicker. | nothing to clean up — this is reading only | available |
| api | Ask the development team whether a purchase order with this destination can be seeded through the project's test-data route | the same way | to be confirmed |
| db | Insert or update a purchase order's destination directly in the database | undo the change | to be confirmed |
| manual | Ask the integration team to send a purchase order with plant W2C1, storage location 6000 from SAP to the test environment | the purchase order stays | always available |

### D5 — the ASN this run raises  (recommended: e2e scenario)

| Way | How, in plain words | Cleanup after | Availability |
|---|---|---|---|
| e2e scenario | Run TC-HAJJ-10: it selects a line of [D1], fills the request details and submits the ASN, then reads the ASN number from the success message | decide with the QC whether the ASN is cancelled afterwards; it is a new record and changes no existing one | available once [D1] is found |

### D7 — the ASN from before the release  (recommended: manual search)

| Way | How, in plain words | Cleanup after | Availability |
|---|---|---|---|
| manual | Open the supplier's ASN list and sort by creation date, looking for an ASN on the W2C1 / 6000 destination created before this story's release date | nothing to clean up — this is reading only | available only if such an ASN exists |

## 6. Open questions for the QC / PO

1. **Closed 2026-11-03 by evidence** — Q-1: the notice does **not** appear on the NUPCO PO list, even with a W2C1 / 6000 purchase order on the page. No new data needed.
2. **Closed 2026-11-03 by evidence** — Q-2: a W2C1 / 6000 destination offers "Request ASN" only. The direct-delivery item and its test case TC-HAJJ-09 were withdrawn in the revision of 2026-11-03.
3. **Closed 2026-11-03 by evidence** — which supplier account to use: `asn-supplier` does hold a purchase order with the Hajj destination (4300000831), so no second account is needed for the main flow.
4. Still open — Q-5: should any NUPCO staff screen be checked for the notice? If yes, a staff account is needed and none is listed above.
5. **Closed 2026-11-03 by evidence** — why the ASN submission was not accepted: the batch row (GTIN and batch details) was not filled. ASN 5060-261103-19820 now exists and is kept.
6. **Closed 2026-11-03** — ASN 5060-261103-19820 stays in Staging (the user's decision); TC-HAJJ-10 and TC-HAJJ-11 can reuse it.
