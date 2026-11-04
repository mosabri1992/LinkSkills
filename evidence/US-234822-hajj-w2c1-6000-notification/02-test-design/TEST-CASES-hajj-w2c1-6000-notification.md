# Test Cases — hajj-w2c1-6000-notification

**Status:** APPROVED
**Scope:** The Hajj 1448 notice opens when a supplier chooses the W2C1 / 6000 destination on PO details, carries the approved Arabic content and its two map links, follows through to the ASN request creation page and the exported ASN PDF, and appears nowhere else.
**Generated:** 2026-11-03
**Review page language:** English — see TC-REVIEW-hajj-w2c1-6000-notification.html
**Entry case:** fresh design — story retrieved from Azure DevOps (revision 29); the 7 Azure DevOps test cases of the predecessor story US 202637 were read as input but not reused
**Implementation status:** Implemented — tester's answer 2026-11-03
**Requirement IDs covered:** REQ-234822-01, REQ-234822-02, REQ-234822-03, REQ-234822-04, REQ-234822-05, REQ-234822-06, REQ-234822-07, REQ-234822-08, REQ-234822-09, REQ-234822-10
**Total test cases:** 14 (6 happy-path / 3 edge-case / 5 negative, all en)
**Run-stage mapping:** happy-path + edge-case → @positive · rejection/guard assertions → @negative
**Patterns applied / skipped:** P1 applied (the Ship-to lookup is opened before use) · P2 applied (the destination choice reloads the line items; the notice is read only after the loading indicator clears) · P3 applied (Request ASN and Submit are their own steps with load-then-clear confirmation) · P4 applied (TC-HAJJ-05 re-chooses the destination on the same page; TC-HAJJ-10 checks the ASN page after a full navigation) · P5 applied (every TC confirms its screen is loaded before interacting) · E1 skipped — not applicable: choosing a destination creates nothing · E2, E3 skipped — not applicable: the notice is read-only content with no save of its own · E4 → Q-4 (the story does not say what the page shows when the notice content fails to load) · E5 applied in TC-HAJJ-05 (the notice returns after a reload) · E6 skipped — not applicable: the notice holds no form
**MCP validation:** 4 validated / 6 enhanced / 0 inferred / 1 discrepancy / 0 not-implemented / 3 draft — not app-validated — by 3c on 2026-11-04, env Staging, scope full, tool cli, re-run 2
**App validation progress:** 11/14 TCs observed live (79%)
**Smoke TCs:** 3
**Automation candidates:** 13 of 14
**Requirement coverage (weighted):** 90.9% — Full 10 / Partial 0 / None 1 of 11 acceptance criteria
**Manual-only scenarios:** 3 (High 1 · Medium 2 · Low 0)
**Tag convention:** ASN, purchasing
**Test layers:** ui

## Summary

| ID | Type | Locale | Requirement | Stage | Smoke | Automation Candidate | Data effect | Shared data | Tags | Validation | Description |
|---|---|---|---|---|---|---|---|---|---|---|---|
| TC-HAJJ-01 | happy-path | en | REQ-234822-01, REQ-234822-07 | @positive | YES | YES | read-only | — | — | enhanced | Validate that the Hajj notice opens when the supplier chooses the W2C1 storage location 6000 destination on PO details |
| TC-HAJJ-02 | happy-path | en | REQ-234822-05, REQ-234822-09 | @positive | YES | YES | read-only | — | — | validated | Validate that the notice content matches the approved text, including both delivery sites, their item classifications and the closing lines |
| TC-HAJJ-03 | happy-path | en | REQ-234822-06 | @positive | NO | YES | read-only | — | — | enhanced | Validate that the notice reads right to left with the colon, brackets, Hijri year and links in the approved places |
| TC-HAJJ-04 | happy-path | en | REQ-234822-05 | @positive | NO | NO | read-only | — | — | draft — not app-validated (external map site not opened in this run) | Validate that both map links open their delivery sites in a new tab |
| TC-HAJJ-05 | edge-case | en | REQ-234822-07 | @positive | NO | YES | read-only | — | — | enhanced | Validate that the notice can be closed, reopens on the next destination choice and after a page reload, and never blocks the supplier |
| TC-HAJJ-06 | negative | en | REQ-234822-02 | @negative | NO | YES | read-only | — | — | validated | Check that no Hajj notice opens for plant W2C1 with a storage location other than 6000 |
| TC-HAJJ-07 | negative | en | REQ-234822-02 | @negative | NO | YES | read-only | — | — | enhanced | Check that no Hajj notice opens for a destination on another plant |
| TC-HAJJ-08 | happy-path | en | REQ-234822-02, REQ-234822-03 | @positive | YES | YES | read-only | — | — | enhanced | Validate that the notice is shown on the ASN request creation details page for a normal ASN |
| TC-HAJJ-10 | negative | en | REQ-234822-03 | @negative | NO | YES | creates | ASN raised on the W2C1 storage location 6000 destination [D5] | — | enhanced | Check that the notice is not shown on the ASN details page after the ASN is submitted |
| TC-HAJJ-11 | happy-path | en | REQ-234822-04 | @positive | NO | YES | creates | ASN raised on the W2C1 storage location 6000 destination [D5] | — | discrepancy | Validate that the exported ASN PDF carries the notice with its table and both map links |
| TC-HAJJ-12 | edge-case | en | REQ-234822-10 | @positive | NO | YES | read-only | — | — | draft — not app-validated (data missing — D7) | Validate that re-exporting the PDF of an ASN created before the release shows the Hajj 1448 notice |
| TC-HAJJ-13 | negative | en | REQ-234822-10 | @negative | NO | YES | read-only | — | — | validated | Check that no Hajj 1447 content, including the Tamer Logistics site, appears anywhere the notice is shown |
| TC-HAJJ-14 | negative | en | REQ-234822-01 | @negative | NO | YES | read-only | — | — | validated | Check that the Hajj notice does not open on the NUPCO PO list before a destination is chosen |
| TC-HAJJ-15 | edge-case | en | REQ-234822-08 | @positive | NO | YES | read-only | — | — | draft — not app-validated (screen could not be driven — no portal language control found) | Validate that the notice stays in Arabic when the portal is switched to another language |

## Test Cases

### TC-HAJJ-01 — Validate that the Hajj notice opens when the supplier chooses the W2C1 storage location 6000 destination on PO details
- **Type:** happy-path
- **Locale:** en
- **Requirement:** REQ-234822-01, REQ-234822-07
- **Stage:** @positive
- **Preconditions:**
  1. The Hajj notice feature switch is on for this environment [E2].
  2. An ASN supplier account is available [A1].
  3. A bookable NUPCO purchase order whose Ship-to list offers plant W2C1 with storage location 6000 is available [D1].
  4. The portal language is English.
- **Steps:**
  1. Open the portal [E1] and sign in as the ASN supplier [A1] — assert the home page loads and the header names the supplier's company.
  2. Select the app-grid icon at the right of the header, then the "NUPCO POs" tile — assert a loading indicator appears on the PO list area.
  3. Wait for the loading indicator on the PO list area to clear — assert the PO list table is visible with no spinner. If an "SFDA Announcement" window covers the list, select its "Cancel" button and assert no overlay remains.
  4. Select the PO number of the purchase order [D1] — assert the PO Details page opens with the breadcrumb "ASN › NUPCO POs › PO Details".
  5. Read the page before choosing a destination — assert the heading "Select a destination to display the line items." is shown and no Hajj notice is on the page.
  6. Select the "Select Ship To" control — assert the "Ship To" lookup window opens with its result table loaded, showing the columns Plant code, Ship-to code, Ship-to name, Warehouse name, Inventory type and Region.
  7. In the lookup, tick the radio button at the start of the row whose Plant code is "W2C1" and whose Ship-to code is "6000" [D1] — assert the row's radio button is ticked and the "Select" button is available.
  8. Select the "Select" button in the lookup — assert the lookup closes, the Ship To field reads "W2C1 / 6000  MOH - Al Hajj", and a loading indicator appears on the line items area.
  9. Wait for the loading indicator on the line items area to clear — assert the line items table is shown for the chosen destination.
  10. Read the top of the PO Details page — assert the Hajj notice panel is visible, its title reads "تنبيه", and it carries a close control.
- **Expected Result:** Choosing the W2C1 / storage location 6000 destination on PO details opens the Hajj notice panel, titled "تنبيه", above the line items; nothing on the page blocks the supplier from continuing.
- **Data Oracle:** NUPCO purchase order with a W2C1 / 6000 Ship-to [D1] — the PO number and the Ship-to row (plant "W2C1", storage location "6000") as recorded in TEST-DATA
- **Smoke:** YES
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —
- **Validation:** enhanced
<!-- tc-evidence
validated-on: 2026-11-03
env: Staging
build: unknown
scope: full-tail
tool: cli
outcome-check: chose the Ship-to row plant W2C1 / storage location 6000 ("MOH - Al Hajj", warehouse MAERSK) on PO 4300000831; the notice panel appeared above the line items with the title "تنبيه" and a close control; no notice was on the page before the destination was chosen
content-sha256: fbcb5b9c9c2fd446
req-sha256: e92df9f574b0a0ba
open-questions: —
checked-in-run: 2026-11-03
-->

### TC-HAJJ-02 — Validate that the notice content matches the approved text, including both delivery sites, their item classifications and the closing lines
- **Type:** happy-path
- **Locale:** en
- **Requirement:** REQ-234822-05, REQ-234822-09
- **Stage:** @positive
- **Preconditions:**
  1. The Hajj notice feature switch is on for this environment [E2].
  2. An ASN supplier account is available [A1].
  3. A bookable NUPCO purchase order whose Ship-to list offers plant W2C1 with storage location 6000 is available [D1].
  4. The approved Hajj 1448 notice image is at hand for comparison [D4].
- **Steps:**
  1. Open the portal [E1], sign in as the ASN supplier [A1] and open the PO Details page of [D1] with the W2C1 / 6000 destination chosen, as in TC-HAJJ-01 — assert the Hajj notice panel is visible.
  2. Read the notice title — assert it reads "تنبيه".
  3. Read the intro sentence — assert it reads "إشعار هام: يرجى التنويه بأنه سيكون مقر إستلام الشحنات الخاصة بالحج لعام 1448 هـ لموقع توريد (SLOC W2C1-6000) في المواقع ادناه:" word for word, naming the year 1448 and the storage location W2C1-6000, and ending with the colon.
  4. Read the table column headers from right to left — assert they are "التصنيف", "مكان التوريد" and "الموقع".
  5. Read the first site row — assert its classification cell reads "جميع البنود", its delivery place reads "مستودعات نوبكو (الميناء)" with "Nupco WH" beneath it, and its location cell reads "Maersk Logistics Park (MLP), Nupco WH" with the link https://maps.app.goo.gl/zbWJWBYQbWRjqmaWA beneath it.
  6. Read the second site row — assert its classification cell reads "بنود الادوية المخدرة", its delivery place reads "مستودعات نوبكو (حدا)" with "Nupco Haddah WH" beneath it, and its location cell reads "Hadda" with the link https://maps.google.com/?q=21.448376,39.568314 beneath it.
  7. Count the site rows — assert the table holds exactly two, so narcotic drug items have one destination (Hadda) and every other item one destination (Maersk Logistics Park).
  8. Read the whole panel to its end — assert the notice closes with the two lines "شكرًا لتعاونكم" and "مع أطيب التحيات", in that order, and that no further line follows them [D4].
- **Expected Result:** The notice shows the approved title, intro sentence and three-column table with exactly the two 1448 delivery sites, each with its classification and map link, and closes with "شكرًا لتعاونكم" and "مع أطيب التحيات" [D4].
- **Data Oracle:** approved Hajj 1448 notice text [D4] — intro sentence, the three column headers, two site rows with classifications "جميع البنود" and "بنود الادوية المخدرة", the two map links and the two closing lines as recorded in TEST-DATA
- **Smoke:** YES
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —
- **Validation:** validated
<!-- tc-evidence
validated-on: 2026-11-04
env: Staging
build: unknown
scope: full-tail
tool: cli
outcome-check: on PO 4300000831 with W2C1 / 6000 chosen, the notice read: title "تنبيه"; intro "إشعار هام: يرجى … في المواقع ادناه:" ending with the colon; exactly two site rows; the last two lines "شكرًا لتعاونكم" and "مع أطيب التحيات"; no "Tamer Logistics"
content-sha256: 52d46cfdc67e1431
req-sha256: e92df9f574b0a0ba
open-questions: —
checked-in-run: 2026-11-04
-->

### TC-HAJJ-03 — Validate that the notice reads right to left with the colon, brackets, Hijri year and links in the approved places
- **Type:** happy-path
- **Locale:** en
- **Requirement:** REQ-234822-06
- **Stage:** @positive
- **Preconditions:**
  1. The Hajj notice feature switch is on for this environment [E2].
  2. An ASN supplier account is available [A1].
  3. A bookable NUPCO purchase order whose Ship-to list offers plant W2C1 with storage location 6000 is available [D1].
  4. The approved Hajj 1448 notice image is at hand for comparison [D4].
- **Steps:**
  1. Open the portal [E1], sign in as the ASN supplier [A1] and open the PO Details page of [D1] with the W2C1 / 6000 destination chosen, as in TC-HAJJ-01 — assert the Hajj notice panel is visible.
  2. Read the panel layout — assert the title, the intro text and the table are aligned to the right and the text runs right to left.
  3. Read the end of the intro sentence — assert the colon closes the sentence after "في المواقع ادناه" and does not sit before "(SLOC W2C1-6000)", as in [D4].
  4. Read the storage location in the intro — assert the brackets enclose it as "(SLOC W2C1-6000)", with the opening bracket on the right of the bracketed text.
  5. Read the Hijri year — assert it reads "1448 هـ" with the year digits to the left of "هـ".
  6. Read each of the two map links — assert each link reads left to right inside the right-to-left row, with no reversed or broken characters.
  7. Read the table column order — assert "التصنيف" is the rightmost column and "الموقع" the leftmost, matching [D4].
- **Expected Result:** The whole notice is laid out right to left, and the colon, the brackets around the storage location, the Hijri year and both links sit exactly where the approved image [D4] shows them.
- **Data Oracle:** approved Hajj 1448 notice image [D4] — the right-to-left layout, the closing colon, the bracketed "(SLOC W2C1-6000)", the Hijri year "1448 هـ" and the column order as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —
- **Validation:** enhanced
<!-- tc-evidence
validated-on: 2026-11-03
env: Staging
build: unknown
scope: full-tail
tool: cli
outcome-check: the notice content element carries right-to-left direction and the table is right-aligned, so التصنيف is the rightmost column; the colon closes the sentence after "في المواقع ادناه", the brackets enclose "(SLOC W2C1-6000)" and the year reads "1448 هـ"; both links render left-to-right inside the right-to-left row
content-sha256: 469b6bd54b42592a
req-sha256: e92df9f574b0a0ba
open-questions: —
checked-in-run: 2026-11-03
-->

### TC-HAJJ-04 — Validate that both map links open their delivery sites in a new tab
- **Type:** happy-path
- **Locale:** en
- **Requirement:** REQ-234822-05
- **Stage:** @positive
- **Preconditions:**
  1. The Hajj notice feature switch is on for this environment [E2].
  2. An ASN supplier account is available [A1].
  3. A bookable NUPCO purchase order whose Ship-to list offers plant W2C1 with storage location 6000 is available [D1].
  4. The browser may open an external map site from this network.
- **Steps:**
  1. Open the portal [E1], sign in as the ASN supplier [A1] and open the PO Details page of [D1] with the W2C1 / 6000 destination chosen, as in TC-HAJJ-01 — assert the Hajj notice panel is visible.
  2. Select the link in the first site row ("Maersk Logistics Park (MLP), Nupco WH") — assert a new browser tab opens and the PO Details page stays open and unchanged in the first tab.
  3. Wait for the new tab to finish loading — assert the map site opens on the Maersk Logistics Park location and shows no error page.
  4. Close the new tab and return to the PO Details tab — assert the Hajj notice is still shown and the chosen destination is unchanged.
  5. Select the link in the second site row ("Hadda") — assert a new browser tab opens.
  6. Wait for the new tab to finish loading — assert the map site opens on the coordinates 21.448376, 39.568314 (the Hadda warehouse) and shows no error page.
- **Expected Result:** Each map link opens its own delivery site in a new browser tab without an error, and the PO Details page with the notice stays open behind it.
- **Data Oracle:** approved Hajj 1448 notice image [D4] — the Maersk Logistics Park link and the Hadda link with coordinates 21.448376, 39.568314 as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** NO
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —
- **Validation:** draft — not app-validated (external map site not opened in this run)

### TC-HAJJ-05 — Validate that the notice can be closed, reopens on the next destination choice and after a page reload, and never blocks the supplier
- **Type:** edge-case
- **Locale:** en
- **Requirement:** REQ-234822-07
- **Stage:** @positive
- **Preconditions:**
  1. The Hajj notice feature switch is on for this environment [E2].
  2. An ASN supplier account is available [A1].
  3. A bookable NUPCO purchase order whose Ship-to list offers plant W2C1 with storage location 6000, and at least one other destination, is available [D1].
- **Steps:**
  1. Open the portal [E1], sign in as the ASN supplier [A1] and open the PO Details page of [D1] with the W2C1 / 6000 destination chosen, as in TC-HAJJ-01 — assert the Hajj notice panel is visible.
  2. Select a line item in the line items table while the notice is open — assert the line is selected, so the notice does not block the page.
  3. Select the close control on the notice — assert the notice panel disappears and the line items table stays as it was, with the line still selected.
  4. Open the Ship-to lookup and choose another destination of [D1] — assert a loading indicator appears on the line items area, then clears, and no Hajj notice is shown for that destination.
  5. Open the Ship-to lookup again and choose the W2C1 / storage location 6000 destination — assert the loading indicator appears on the line items area, then clears.
  6. Read the top of the page — assert the Hajj notice is shown again, so it returns on each choice of this destination.
  7. Reload the PO Details page in the browser and wait until the line items table is shown — assert the Hajj notice is shown again after the reload.
- **Expected Result:** The notice can be closed, never stops the supplier from selecting lines, and comes back each time the W2C1 / 6000 destination is chosen again or the page is reloaded.
- **Data Oracle:** NUPCO purchase order with a W2C1 / 6000 Ship-to and at least one other destination [D1] — as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —
- **Validation:** enhanced
<!-- tc-evidence
validated-on: 2026-11-03
env: Staging
build: unknown
scope: full-tail
tool: cli
outcome-check: selected a line item while the notice was open (the notice never blocked the page), closed the notice with its close control and the line stayed selected; choosing the plant 1100 destination showed no notice, choosing W2C1 / 6000 again showed it, and it returned again after a page reload
content-sha256: 61bccb304ad08586
req-sha256: e92df9f574b0a0ba
open-questions: —
checked-in-run: 2026-11-03
-->

### TC-HAJJ-06 — Check that no Hajj notice opens for plant W2C1 with a storage location other than 6000
- **Type:** negative
- **Locale:** en
- **Requirement:** REQ-234822-02
- **Stage:** @negative
- **Preconditions:**
  1. The Hajj notice feature switch is on for this environment [E2].
  2. An ASN supplier account is available [A1].
  3. A bookable NUPCO purchase order whose Ship-to list offers plant W2C1 with a storage location other than 6000 is available [D2].
- **Steps:**
  1. Open the portal [E1] and sign in as the ASN supplier [A1] — assert the home page loads.
  2. Open the "NUPCO POs" tile from the app-grid icon and wait until the PO list table is shown — assert no spinner remains.
  3. Select the PO number of the purchase order [D2] — assert the PO Details page opens.
  4. Select the "Select Ship To" control — assert the "Ship To" lookup window opens with its result table loaded.
  5. Tick the radio button of the row whose Plant code is "W2C1" and whose Ship-to code is not "6000" [D2], then select the "Select" button — assert the lookup closes, a loading indicator appears on the line items area, then clears and the line items table is shown.
  6. Read the whole PO Details page — assert no Hajj notice panel is shown and the title "تنبيه" appears nowhere on it.
- **Expected Result:** A destination on plant W2C1 with a storage location other than 6000 shows no Hajj notice; the page opens its line items as usual.
- **Data Oracle:** NUPCO purchase order with a W2C1 Ship-to on a storage location other than 6000 [D2] — the PO number and the storage location as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —
- **Validation:** validated
<!-- tc-evidence
validated-on: 2026-11-04
env: Staging
build: unknown
scope: full-tail
tool: cli
outcome-check: on PO 4300000834 chose W2C1 / 1000 "MOH Stock": the Ship To field and the page address show W2C1 / 1000, the line items opened, and no notice and no "تنبيه" appeared; spot check on PO 4300000833, W2C1 / 4000 "MOH - Makkah": no notice either
content-sha256: 71ba9b1abc4e0a3e
req-sha256: e92df9f574b0a0ba
open-questions: —
checked-in-run: 2026-11-04
-->

### TC-HAJJ-07 — Check that no Hajj notice opens for a destination on another plant
- **Type:** negative
- **Locale:** en
- **Requirement:** REQ-234822-02
- **Stage:** @negative
- **Preconditions:**
  1. The Hajj notice feature switch is on for this environment [E2].
  2. An ASN supplier account is available [A1].
  3. A bookable NUPCO purchase order whose Ship-to list offers a plant other than W2C1 is available [D3].
- **Steps:**
  1. Open the portal [E1] and sign in as the ASN supplier [A1] — assert the home page loads.
  2. Open the "NUPCO POs" tile from the app-grid icon and wait until the PO list table is shown — assert no spinner remains.
  3. Select the PO number of the purchase order [D3] — assert the PO Details page opens.
  4. Select the "Select Ship To" control, tick the radio button of a row whose Plant code is not "W2C1" [D3], then select the "Select" button — assert a loading indicator appears on the line items area, then clears and the line items table is shown.
  5. Read the whole PO Details page — assert no Hajj notice panel is shown and the title "تنبيه" appears nowhere on it.
  6. Select a line item, then select the request control the toolbar offers for this destination — it reads "Request Direct Delivery ASN" for a plant 1100 destination and "Request ASN" for others — and wait for the ASN request creation page to load — assert no Hajj notice is shown there either.
- **Expected Result:** A destination on any plant other than W2C1 shows no Hajj notice, on PO details or on the ASN request creation page.
- **Data Oracle:** NUPCO purchase order with a Ship-to on a plant other than W2C1 [D3] — the PO number and the plant code as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —
- **Validation:** enhanced
<!-- tc-evidence
validated-on: 2026-11-03
env: Staging
build: unknown
scope: full-tail
tool: cli
outcome-check: chose the plant 1100 / 120364 destination (KAMC) on the same PO: no notice on PO details and none on the ASN creation page reached from it
content-sha256: 6554f6790a227db2
req-sha256: e92df9f574b0a0ba
open-questions: —
checked-in-run: 2026-11-03
-->

### TC-HAJJ-08 — Validate that the notice is shown on the ASN request creation details page for a normal ASN
- **Type:** happy-path
- **Locale:** en
- **Requirement:** REQ-234822-02, REQ-234822-03
- **Stage:** @positive
- **Preconditions:**
  1. The Hajj notice feature switch is on for this environment [E2].
  2. An ASN supplier account is available [A1].
  3. A bookable NUPCO purchase order whose Ship-to list offers plant W2C1 with storage location 6000, with at least one line item that can be requested, is available [D1].
- **Steps:**
  1. Open the portal [E1], sign in as the ASN supplier [A1] and open the PO Details page of [D1] with the W2C1 / 6000 destination chosen, as in TC-HAJJ-01 — assert the Hajj notice panel is visible.
  2. Select one line item in the line items table — assert the line's checkbox is ticked and the "Request ASN" control is available in the line items toolbar (for a W2C1 / 6000 destination the toolbar offers "Request ASN" only, never "Request Direct Delivery ASN").
  3. Select "Request ASN" — assert the browser navigates away from PO Details to the ASN creation page, titled "ASN | Create".
  4. Wait until the ASN creation page has loaded — assert the page shows its "Request Details" form with the fields "Invoice number", "Delivery Date" and "Delivery Time", and no spinner.
  5. Read the top of the ASN creation page — assert the Hajj notice is shown there above "Request Details", with the title "تنبيه", the same intro sentence and the same two site rows as on PO details [D4], and that "Shipped to Location" reads "MOH - Al Hajj".
  6. Scroll through the request details form — assert the notice stays at the top of the page as page content, and does not cover the form fields.
- **Expected Result:** The ASN request creation details page for a W2C1 / 6000 destination shows the Hajj notice as a fixed box at the top, with the same approved content as on PO details.
- **Data Oracle:** approved Hajj 1448 notice image [D4] — title, intro sentence and the two site rows as recorded in TEST-DATA
- **Smoke:** YES
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —
- **Validation:** enhanced
<!-- tc-evidence
validated-on: 2026-11-03
env: Staging
build: unknown
scope: full-tail
tool: cli
outcome-check: from the W2C1 / 6000 destination, selected a line and used Request ASN; the ASN creation page opened and showed the notice as page content at the top with the same intro, table and both map links
content-sha256: c0bef0bc741bebfb
req-sha256: e92df9f574b0a0ba
open-questions: —
checked-in-run: 2026-11-03
-->

### TC-HAJJ-10 — Check that the notice is not shown on the ASN details page after the ASN is submitted
- **Type:** negative
- **Locale:** en
- **Requirement:** REQ-234822-03
- **Stage:** @negative
- **Preconditions:**
  1. The Hajj notice feature switch is on for this environment [E2].
  2. An ASN supplier account is available [A1].
  3. A bookable NUPCO purchase order whose Ship-to list offers plant W2C1 with storage location 6000 is available [D1].
  4. This test case creates an ASN [D5]; the run must be allowed to create data on this environment.
- **Steps:**
  1. Open the portal [E1], sign in as the ASN supplier [A1] and reach the ASN request creation page for a W2C1 / 6000 destination of [D1], as in TC-HAJJ-08 — assert the Hajj notice is shown on that page.
  2. Fill "Delivery Date" (date picker), "Delivery Time" (a dropdown of hourly slots, for example "10:00 am") and "No. of Pallets" on the line — assert each field shows its value. The "NUPCO GLN" field fills itself and is read-only.
  3. Select the expand arrow at the end of the line row, then the expand arrow at the end of the line-item row inside it — assert a batch row opens with the fields "GTIN", "Batch Number", "Quantity", "Manufacturing date" and "Expiry date".
  4. Fill the batch row: "GTIN" with the item's 14-digit GTIN (a 13-digit GTIN is written with a leading zero), "Batch Number" (letters and digits only), "Quantity", "Manufacturing date" and "Expiry date" — assert each field shows its value.
  5. Type the "Invoice number" last (at most 16 characters; the date pickers can clear it) — assert it shows the full value.
  6. Select "Create" and read the page at once — assert no short-lived message such as "Please fill GTIN for trade …" or "GTIN must be exactly 14 digits." appears, and the window "Your Request Has Been Sent" opens with the request number of the new ASN [D5].
  7. Select "Back To My Requests", then the new request number in the "My Requests" list — assert the ASN page titled "ASN | Details" opens for [D5], showing "Shipped to Location" as "MOH - Al Hajj".
  8. Read the whole ASN details page — assert no Hajj notice is shown and the title "تنبيه" appears nowhere on it.
- **Expected Result:** The Hajj notice belongs to the ASN request creation page only; once the ASN is submitted, its details page shows no notice.
- **Data Oracle:** the ASN created by this test case [D5] — its ASN number as shown in the success message
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** creates
- **Shared data:** ASN raised on the W2C1 storage location 6000 destination [D5]
- **Tags:** —
- **Validation:** enhanced
<!-- tc-evidence
validated-on: 2026-11-03
env: Staging
build: unknown
scope: full-tail
tool: cli
outcome-check: submitted ASN 5060-261103-19820 (invoice QA3C-234822-1103) on the W2C1 / 6000 destination of PO 4300000831; the success window "Your Request Has Been Sent" named the request number; the submitted ASN opened from My Requests as "ASN | Details" (Approval Pending, shipped to MOH - Al Hajj) and showed no notice and no "تنبيه"
content-sha256: e1cf630355d1ad5d
req-sha256: e92df9f574b0a0ba
open-questions: —
checked-in-run: 2026-11-03
-->

### TC-HAJJ-11 — Validate that the exported ASN PDF carries the notice with its table and both map links
- **Type:** happy-path
- **Locale:** en
- **Requirement:** REQ-234822-04
- **Stage:** @positive
- **Preconditions:**
  1. The Hajj notice feature switch is on for this environment [E2].
  2. An ASN supplier account is available [A1].
  3. A bookable NUPCO purchase order whose Ship-to list offers plant W2C1 with storage location 6000 is available [D1].
  4. The approved Hajj 1448 notice image is at hand for comparison [D4].
  5. This test case creates an ASN [D5]; the run must be allowed to create data on this environment.
- **Steps:**
  1. Open the portal [E1], sign in as the ASN supplier [A1] and submit an ASN for a W2C1 / 6000 destination of [D1], as in TC-HAJJ-10 — assert the success message naming the new ASN is shown [D5].
  2. Select the export PDF control in the success message — assert the PDF file downloads and its name names the ASN [D5].
  3. [HUMAN] Open the downloaded PDF and read the area under the document header — assert the Hajj notice is printed there, with the title "تنبيه" and the intro sentence naming Hajj 1448 and the storage location W2C1-6000, matching [D4].
  4. [HUMAN] Read the notice table in the PDF — assert it holds the three column headers and both site rows, with "جميع البنود" against Maersk Logistics Park and "بنود الادوية المخدرة" against Hadda, in the same right-to-left order as [D4].
  5. [HUMAN] Read the two map links in the PDF — assert each link text is complete and unbroken, and that selecting it opens its delivery site.
- **Expected Result:** The exported ASN PDF of a W2C1 / 6000 destination carries the whole Hajj notice under the document header: title, intro sentence, the three-column table with both sites and both working map links.
- **Data Oracle:** approved Hajj 1448 notice image [D4] — the intro sentence, column headers, the two site rows and the two map links as recorded in TEST-DATA; the ASN created by this test case [D5]
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** creates
- **Shared data:** ASN raised on the W2C1 storage location 6000 destination [D5]
- **Tags:** —
- **Validation:** discrepancy
<!-- tc-evidence
validated-on: 2026-11-04
env: Staging
build: unknown
scope: full-tail
tool: cli
outcome-check: steps 1-2 observed by the tool: ASN 5060-261103-19820 submitted and its PDF exported as request_5060-261103-19820.pdf. Steps 3-5 (human) read by the reviewer Mohamed Sabry on 2026-11-04: the notice is printed under the ASN header with its title, table, both sites, both links and the closing lines, but the colon that ends the intro ("… في المواقع ادناه:") is missing in the PDF while the screen shows it (PB-2)
content-sha256: 649184c9c51024e6
req-sha256: e92df9f574b0a0ba
open-questions: —
checked-in-run: 2026-11-04
-->

### TC-HAJJ-12 — Validate that re-exporting the PDF of an ASN created before the release shows the Hajj 1448 notice
- **Type:** edge-case
- **Locale:** en
- **Requirement:** REQ-234822-10
- **Stage:** @positive
- **Preconditions:**
  1. The Hajj notice feature switch is on for this environment [E2].
  2. An ASN supplier account is available [A1].
  3. An ASN on a W2C1 / storage location 6000 destination, created before the Hajj 1448 release, is available [D7].
  4. The approved Hajj 1448 notice image is at hand for comparison [D4].
- **Steps:**
  1. Open the portal [E1] and sign in as the ASN supplier [A1] — assert the home page loads.
  2. Open the ASN list and find the ASN created before the release [D7] — assert its row is shown with its creation date before the release date.
  3. Open that ASN and export its PDF again — assert the PDF file downloads.
  4. [HUMAN] Open the downloaded PDF and read the notice area — assert it shows the Hajj 1448 intro sentence and the two 1448 sites, not the Hajj 1447 content, matching [D4].
- **Expected Result:** Re-exporting the PDF of an ASN created before the release shows the current Hajj 1448 notice, so every exported document carries the same delivery sites.
- **Data Oracle:** ASN created before the Hajj 1448 release on a W2C1 / 6000 destination [D7] — its ASN number and creation date as recorded in TEST-DATA; approved Hajj 1448 notice image [D4]
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —
- **Validation:** draft — not app-validated (data missing — D7)

### TC-HAJJ-13 — Check that no Hajj 1447 content, including the Tamer Logistics site, appears anywhere the notice is shown
- **Type:** negative
- **Locale:** en
- **Requirement:** REQ-234822-10
- **Stage:** @negative
- **Preconditions:**
  1. The Hajj notice feature switch is on for this environment [E2].
  2. An ASN supplier account is available [A1].
  3. A bookable NUPCO purchase order whose Ship-to list offers plant W2C1 with storage location 6000 is available [D1].
- **Steps:**
  1. Open the portal [E1], sign in as the ASN supplier [A1] and open the PO Details page of [D1] with the W2C1 / 6000 destination chosen, as in TC-HAJJ-01 — assert the Hajj notice panel is visible.
  2. Read the whole notice on PO details — assert the text "Tamer Logistics" appears nowhere in it, and no row names "مستودعات نوبكو (حي الخمرة)".
  3. Read the intro sentence — assert it names the year 1448 and that the year 1447 appears nowhere in the notice.
  4. Count the site rows — assert there are two, not the three of the previous year.
  5. Select Request ASN with one line selected and wait for the ASN request creation page to load — assert the notice there also names 1448 only, with no "Tamer Logistics" row.
- **Expected Result:** Neither the PO details notice nor the ASN request creation notice carries any Hajj 1447 content: no Tamer Logistics site, no third row and no 1447 year.
- **Data Oracle:** approved Hajj 1448 notice image [D4] — exactly two site rows, Maersk Logistics Park and Hadda, with no Tamer Logistics row, as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —
- **Validation:** validated
<!-- tc-evidence
validated-on: 2026-11-03
env: Staging
build: unknown
scope: full-tail
tool: cli
outcome-check: the notice on PO details and on the ASN creation page holds exactly two site rows, names only the year 1448, and carries no "Tamer Logistics" row and no "مستودعات نوبكو (حي الخمرة)"
content-sha256: 5d6d6e3657a57a24
req-sha256: e92df9f574b0a0ba
open-questions: —
checked-in-run: 2026-11-03
-->

### TC-HAJJ-14 — Check that the Hajj notice does not open on the NUPCO PO list before a destination is chosen
- **Type:** negative
- **Locale:** en
- **Requirement:** REQ-234822-01
- **Stage:** @negative
- **Preconditions:**
  1. The Hajj notice feature switch is on for this environment [E2].
  2. An ASN supplier account is available [A1].
  3. A bookable NUPCO purchase order whose Ship-to list offers plant W2C1 with storage location 6000 is available [D1], and it is on the first page of the NUPCO PO list.
  4. The expected result of this test case depends on Q-1 — the project's recorded screen knowledge says the notice does appear on this list.
- **Steps:**
  1. Open the portal [E1] and sign in as the ASN supplier [A1] — assert the home page loads.
  2. Open the "NUPCO POs" tile from the app-grid icon — assert a loading indicator appears on the PO list area.
  3. Wait for the loading indicator on the PO list area to clear — assert the PO list table is shown. If an "SFDA Announcement" window covers the list, select its "Cancel" button and assert no overlay remains.
  4. Confirm the purchase order [D1] is listed on the current page — assert its PO number is in the table, so a W2C1 / 6000 purchase order is on screen.
  5. Read the whole PO list page — assert no Hajj notice panel is shown and the title "تنبيه" appears nowhere on it.
- **Expected Result:** The NUPCO PO list shows no Hajj notice, even when a W2C1 / 6000 purchase order is listed; the notice belongs to the destination choice on PO details.
- **Data Oracle:** NUPCO purchase order with a W2C1 / 6000 Ship-to [D1] — its PO number as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —
- **Validation:** validated
<!-- tc-evidence
validated-on: 2026-11-03
env: Staging
build: unknown
scope: full-tail
tool: cli
outcome-check: filtered the NUPCO PO list by PO number 4300000831 so the W2C1 / 6000 purchase order was the only row on the page: no notice panel and no "تنبيه" anywhere on the list; the unfiltered first page showed none either
content-sha256: 7c87a608fafa9af2
req-sha256: e92df9f574b0a0ba
open-questions: —
checked-in-run: 2026-11-03
-->

### TC-HAJJ-15 — Validate that the notice stays in Arabic when the portal is switched to another language
- **Type:** edge-case
- **Locale:** en
- **Requirement:** REQ-234822-08
- **Stage:** @positive
- **Preconditions:**
  1. The Hajj notice feature switch is on for this environment [E2].
  2. An ASN supplier account is available [A1].
  3. A bookable NUPCO purchase order whose Ship-to list offers plant W2C1 with storage location 6000 is available [D1].
  4. The approved Hajj 1448 notice image is at hand for comparison [D4].
- **Steps:**
  1. Open the portal [E1], sign in as the ASN supplier [A1] and open the PO Details page of [D1] with the W2C1 / 6000 destination chosen, as in TC-HAJJ-01 — assert the Hajj notice panel is visible in Arabic.
  2. Open the portal language control in the header — the exact label of this control is not recorded for the supplier portal and is to be captured live (Q-3) — assert the language options are shown.
  3. Switch the portal to Arabic — assert the page reloads or re-renders and the shell labels change language.
  4. Return to the PO Details page of [D1] with the W2C1 / 6000 destination chosen and wait until the line items table is shown — assert the Hajj notice is shown.
  5. Read the notice — assert its title, intro sentence and both site rows are the same Arabic text as in step 1 and match [D4], with no translated or duplicated version beside it.
  6. Switch the portal back to English and reopen the same destination — assert the notice is still the same Arabic text.
- **Expected Result:** The Hajj notice is shown in Arabic only; switching the portal language does not translate it, duplicate it or remove it.
- **Data Oracle:** approved Hajj 1448 notice image [D4] — the Arabic title, intro sentence and both site rows as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —
- **Validation:** draft — not app-validated (screen could not be driven — no portal language control found)

## Enhancement Log

| TC-ID | Validation | What changed | Why (what the app showed) | Run |
|---|---|---|---|---|
| TC-HAJJ-01 | enhanced | Split the destination choice into three steps: open "Select Ship To", tick the row's radio button, then select "Select". Added the lookup's column names and the Ship To field's value after the choice. | The lookup is a window whose rows are chosen with a radio button and confirmed with a "Select" button; clicking the row text alone changes nothing. | 3c 2026-11-03 |
| TC-HAJJ-03 | enhanced | Kept the assertions, confirmed live. | The notice content element carries right-to-left direction and the table is right-aligned; the colon, brackets and Hijri year sit as the approved image shows them. | 3c 2026-11-03 |
| TC-HAJJ-05 | enhanced | Same lookup correction as TC-HAJJ-01 for the destination switch steps. | Same lookup behaviour. The close control, the line staying selected and the return after reload all behaved as designed. | 3c 2026-11-03 |
| TC-HAJJ-07 | enhanced | Named the request control per destination and added the line-item selection step. | On a plant 1100 destination the toolbar offers "Request Direct Delivery ASN", not "Request ASN"; the control is destination-dependent. | 3c 2026-11-03 |
| TC-HAJJ-08 | enhanced | Replaced the toolbar assertion "1 items selected", named the ASN page title and its form fields, and added the "Shipped to Location" check. | The toolbar shows no "1 items selected" title; the ASN page is titled "ASN \| Create" and its form asks for Invoice number, Delivery Date and Delivery Time. | 3c 2026-11-03 |
| TC-HAJJ-10 | enhanced | Replaced "fill the request details the form requires" with the real fields: delivery date and time, pallets, the two expand arrows that open the batch row, GTIN (14 digits), batch number, quantity and the two dates, the invoice typed last; named the success window and the "My Requests" route to the submitted ASN. | Without the batch row "Create" shows only a short-lived message ("Please fill GTIN for trade …", then "GTIN must be exactly 14 digits.") and creates nothing. Submitted ASNs are listed under "My Requests", and their page is titled "ASN \| Details". | 3c 2026-11-03 re-run 1 |

## Traceability Matrix

| Requirement | Requirement in short | Test cases | Coverage |
|---|---|---|---|
| REQ-234822-01 | Notice opens on the PO details destination choice, not on the lists | TC-HAJJ-01, TC-HAJJ-14 | Fully covered |
| REQ-234822-02 | Applies to the normal ASN from the NUPCO POs list, W2C1 / 6000 only | TC-HAJJ-06, TC-HAJJ-07, TC-HAJJ-08 | Fully covered |
| REQ-234822-03 | Fixed box on the ASN request creation page, not after submission | TC-HAJJ-08, TC-HAJJ-10 | Fully covered |
| REQ-234822-04 | Notice in the exported ASN PDF | TC-HAJJ-11 | Fully covered |
| REQ-234822-05 | Content matches the approved image, with both map links | TC-HAJJ-02, TC-HAJJ-04 | Fully covered |
| REQ-234822-06 | Right-to-left layout and symbol placement | TC-HAJJ-03 | Fully covered |
| REQ-234822-07 | Opens every time, closes, does not block, links in a new tab | TC-HAJJ-01, TC-HAJJ-05 | Fully covered |
| REQ-234822-08 | Arabic only, whatever the portal language | TC-HAJJ-15 | Fully covered |
| REQ-234822-09 | Narcotics to Hadda, all other items to Maersk Logistics Park | TC-HAJJ-02 | Fully covered |
| REQ-234822-10 | Hajj 1448 replaces 1447 everywhere, including earlier ASNs | TC-HAJJ-12, TC-HAJJ-13 | Fully covered |
| REQ-234822-11 | Only suppliers see the notice | — | Not covered — NUPCO staff screens were declared out of scope (Q-5) |

## Negative Coverage

| L1 §4 category | Covered by | Note |
|---|---|---|
| Invalid inputs | — | N/A — the notice takes no input from the supplier; it is content shown by the system. |
| Boundary conditions | TC-HAJJ-06, TC-HAJJ-07 | The boundary is the destination itself: the same plant with another storage location, and another plant. Both sides of the rule are tested. |
| Missing required inputs | TC-HAJJ-01 step 5, TC-HAJJ-14 | The destination not yet chosen: no notice on PO details before the choice, and none on the list. |
| Unauthorized access | — | N/A — the notice is shown to every supplier who reaches the destination; NUPCO staff screens are out of scope (Q-5). |
| Error recovery | TC-HAJJ-05 | The notice returns after being closed, after another destination is chosen and after a page reload. A failure to load the notice content is not defined by the story — see Q-4. |

## Standards Alignment

| Standard | Where it is met |
|---|---|
| L1 — happy path per acceptance criterion | Every requirement except REQ-234822-11 has at least one positive test case (Traceability Matrix). |
| L1 — negative categories | Negative Coverage table above; two categories are N/A with the reason stated. |
| L1 — localization is a quality dimension equal to function | TC-HAJJ-03 (right-to-left layout and symbol placement) and TC-HAJJ-15 (the notice stays Arabic across a language switch). |
| L1 — test names carry subject, condition and expected outcome | Every description starts "Validate that" or "Check that" and names the screen, the condition and the outcome. |
| L2 — RTL checks apply where an RTL language is configured | The notice is hard-coded right-to-left Arabic content, so the RTL checks are in scope even though the Purchasing screens are English. |
| L3 — environment readiness before execution | The required feature switch is recorded in TEST-DATA `## 0. Environment`, so the readiness script can check it before a run. |

## Requirement Coverage Score

| AC | REQ-ID | TC-IDs | Status | Missing |
|---|---|---|---|---|
| AC-1 notice opens on the destination choice | REQ-234822-01 | TC-HAJJ-01, TC-HAJJ-14 | Fully Covered | — |
| AC-2 the normal ASN from the NUPCO POs list, W2C1 / 6000 only | REQ-234822-02 | TC-HAJJ-06, TC-HAJJ-07, TC-HAJJ-08 | Fully Covered | — |
| AC-3 ASN request creation page, not after submission | REQ-234822-03 | TC-HAJJ-08, TC-HAJJ-10 | Fully Covered | — |
| AC-4 exported ASN PDF | REQ-234822-04 | TC-HAJJ-11 | Fully Covered | — |
| AC-5 content matches the approved image | REQ-234822-05 | TC-HAJJ-02, TC-HAJJ-04 | Fully Covered | — |
| AC-5 right-to-left layout and symbol placement | REQ-234822-06 | TC-HAJJ-03 | Fully Covered | — |
| AC-1 alert behaviour (reopens, closes, does not block) | REQ-234822-07 | TC-HAJJ-01, TC-HAJJ-05 | Fully Covered | — |
| AC-5 Arabic only | REQ-234822-08 | TC-HAJJ-15 | Fully Covered | — |
| AC-5 narcotics to Hadda, all other items to Maersk | REQ-234822-09 | TC-HAJJ-02 | Fully Covered | — |
| story 1448 replaces 1447 everywhere | REQ-234822-10 | TC-HAJJ-12, TC-HAJJ-13 | Fully Covered | — |
| story only suppliers see the notice | REQ-234822-11 | — | Not Covered | NUPCO staff screens were declared out of scope (Q-5) — an Open Finding, not a silent gap |

**Weighted score:** 10.0 of 11 = **90.9%** — Full 10 / Partial 0 / None 1

## Manual-Only Scenarios

| TC-ID | Scenario | Category | Priority | Why |
|---|---|---|---|---|
| TC-HAJJ-04 | Opening both map links and confirming each shows its delivery site | External dependency | Medium | The assertion ends on an external map site, which no fixture controls and which may be blocked or slow from the test network. A person confirms the sites once per release. |
| TC-HAJJ-11 | Reading the notice inside the downloaded ASN PDF (steps 3 to 5) | Human-observed step | High | No PDF-reading interface is recorded for this project, so a person opens the PDF and compares it with the approved image. Automation runs the rest of the test case up to that step. |
| TC-HAJJ-12 | Reading the re-exported PDF of an ASN created before the release (step 4) | Human-observed step | Medium | Same reason as TC-HAJJ-11; only the final content check needs a person. |

## Potential Bugs

### PB-1 — The notice ends with a thank-you and greeting that the reference image does not show
- **Test case:** TC-HAJJ-02
- **Steps to reproduce:**
  1. Sign in as the ASN supplier [A1] and open the NUPCO PO list.
  2. Open purchase order [D1] and choose the Ship-to with plant W2C1 and storage location 6000.
  3. Read the Hajj notice to its end.
- **Expected result:** the notice matches the approved image [D4], which ends at the table with no closing greeting.
- **Actual result:** after the two site rows the notice shows "شكرًا لتعاونكم" and "مع أطيب التحيات" — on PO details, on the ASN creation page and in the exported ASN PDF.
<!-- pb-meta: first-seen: 2026-11-03; last-checked: 2026-11-03; env: Staging; build: unknown; status: resolved 2026-11-03; screenshot: evidence/PB-1-2026-11-03.png -->

**Resolution (2026-11-03): not a defect.** Mohamed Sabry (QC) confirmed the greeting belongs in
the notice and the reference image attached to the story was cropped (Q-6, PO to verify). The
greeting was observed live this run on all three places, which is now the expected behaviour.
TC-HAJJ-02 step 8 and the reference [D4] are what need correcting, through skill 3 `--revision`.

### PB-2 — The exported ASN PDF drops the colon that ends the notice's intro sentence
- **Test case:** TC-HAJJ-11
- **Steps to reproduce:**
  1. Sign in as the ASN supplier [A1] and raise a normal ASN on a destination of plant W2C1, storage location 6000 (for example on purchase order [D1]).
  2. In the window "Your Request Has Been Sent", select "Export Request Details" and open the downloaded PDF.
  3. Read the notice's intro sentence to its end, and compare it with the same notice on PO details.
- **Expected result:** the intro ends "… لموقع توريد (SLOC W2C1-6000) في المواقع ادناه:" with the colon, as on screen and as the requirement's right-to-left note asks ("the symbols be in the correct place").
- **Actual result:** in the PDF the intro ends "… في المواقع ادناه" with no colon; the screen shows the colon.
<!-- pb-meta: first-seen: 2026-11-04; last-checked: 2026-11-04; env: Staging; build: unknown; status: open; screenshot: evidence/PB-2-2026-11-04.pdf -->

Observed by the reviewer (Mohamed Sabry) in the human step of TC-HAJJ-11 on 2026-11-04, on the PDF of ASN 5060-261103-19820 (kept as `evidence/PB-2-2026-11-04.pdf`). Severity: Low — the content is complete, only the closing punctuation is lost; it is the symbol-placement case the story explicitly warns about (REQ-234822-06).

## Open Questions

### Q-1 — Does the Hajj notice also appear on the NUPCO and Return PO lists?
- **Gap:** The answer given in the business clarification (Q-01, 2026-11-03) says the notice opens only on PO details. The project's recorded screen knowledge for the PO lists says the same notice is shown on the NUPCO and Return lists whenever a W2C1 / 6000 purchase order is on the page, and not on the Customer list. Both cannot be the expected result.
- **Why it matters:** TC-HAJJ-14 asserts the notice is absent from the list. If the list notice is intended, that test case fails on a correct build and two more test cases are missing.
- **Affected TCs:** TC-HAJJ-14
- **Evidence:** business clarification answer Q-01, 2026-11-03; the project's Purchasing screen knowledge for the PO lists, written from the delivered code on 2026-10-29.
- **Recommended:** Ask the PO to confirm. If the list notice is intended, TC-HAJJ-14 becomes a positive test case, a Return-list positive is added and a Customer-list negative is added.
- **Alternatives:** Keep "PO details only" — the current design — and let the validation run report any list notice as a possible defect.
- **Pending until answered:** nothing — settled by evidence.
- **Status:** answered 2026-11-03 (by evidence: the NUPCO PO list was filtered to purchase order 4300000831, whose destination is plant W2C1 storage location 6000, and showed no notice and no "تنبيه" anywhere; the unfiltered first page showed none either). The clarified answer Q-01 — PO details only — is what the application does, and TC-HAJJ-14 is validated as designed. The project's recorded screen knowledge for the PO lists is out of date and has been corrected.

### Q-2 — Can a W2C1 / 6000 destination raise a Direct Delivery ASN?
- **Gap:** The clarified scope (Q-03) says the notice covers normal and direct-delivery ASNs. The project's recorded plant rules suggest the Direct Delivery control is offered only for certain plants, which may not include W2C1.
- **Why it matters:** If the control is never offered for this plant, the direct-delivery test case can never run and the story's scope sentence is wrong.
- **Affected TCs:** TC-HAJJ-09 (withdrawn 2026-11-03)
- **Evidence:** business clarification answer Q-03, 2026-11-03; the project's recorded plant rules for the two Request controls on the PO details toolbar.
- **Recommended:** Ask the PO to correct the scope wording: the notice covers the normal ASN flow, because that is the only one a Hajj destination can raise.
- **Alternatives:** none — the control is simply not offered for this destination.
- **Pending until answered:** nothing from testing — only the story's scope wording, which is the PO's to fix.
- **Status:** answered 2026-11-03 (by evidence: with the W2C1 / 6000 destination chosen on purchase order 4300000831, the line items toolbar offers "Request ASN" only; with the plant 1100 destination chosen on the same purchase order it offers "Request Direct Delivery ASN" only. The request control depends on the destination, and a Hajj destination never offers direct delivery). Confirmed by Mohamed Sabry on 2026-11-03: "the requests type is just normal asn". **TC-HAJJ-09 was withdrawn in the revision of 2026-11-03** and its data item [D6] dropped.

### Q-3 — What is the portal language control called, and where is it?
- **Gap:** No label or position is recorded for the supplier portal's language control, so the step cannot be written exactly.
- **Why it matters:** TC-HAJJ-15 step 2 carries a named gap instead of a label, so a tester has to find the control themselves.
- **Affected TCs:** TC-HAJJ-15
- **Evidence:** the learning file records the supplier sign-in flow and the app-grid navigation, but nothing about a language control.
- **Recommended:** Confirm with the team whether the supplier portal has a language control at all. If it has none, reduce TC-HAJJ-15 to reading the notice in the default language, which already proves the notice is Arabic.
- **Alternatives:** Keep the test case as written for a portal release that adds a language control.
- **Pending until answered:** TC-HAJJ-15 stays `draft`; REQ-234822-08 has no live evidence yet.
- **Status:** open — the 2026-11-03 run found no language control in the header of the pages it walked (dashboard, PO list, PO details, ASN list), and no "Arabic" or "عربي" control anywhere on them. That is evidence of absence on those pages, not proof the portal has none.

### Q-4 — What should the page show if the notice content cannot be loaded?
- **Gap:** The story defines no behaviour for a failure to load the notice — error-guessing item E4.
- **Why it matters:** Without a stated behaviour, no test case can assert a pass or fail for that failure, so it stays untested by design rather than by oversight.
- **Affected TCs:** none
- **Evidence:** the story's acceptance criteria describe only the success case.
- **Recommended:** Treat a missing notice on a W2C1 / 6000 destination as a defect, and add no separate failure test case until the PO states a behaviour.
- **Alternatives:** The PO defines a fallback — for example the page loads without the notice — and a negative test case is added.
- **Pending until answered:** No test case is pending; the gap is recorded so it is not mistaken for missed coverage.

### Q-5 — Do NUPCO staff see the notice on their own screens?
- **Gap:** REQ-234822-11 says only suppliers see the notice, and the same answer declared NUPCO staff screens out of scope — so no test case covers the requirement.
- **Why it matters:** This is the one requirement scoring zero in the coverage table, which drops the weighted score to 90.9%.
- **Affected TCs:** none
- **Evidence:** business clarification answer Q-10, 2026-11-03.
- **Recommended:** Confirm that no NUPCO staff screen shows a W2C1 / 6000 destination with this notice; if one does, add a negative test case for it.
- **Alternatives:** Accept the requirement as out of scope and remove it from the story.
- **Pending until answered:** The coverage score stays at 90.9% with one requirement uncovered.
- **Status:** open

### Q-6 — Should the notice end with "شكرًا لتعاونكم / مع أطيب التحيات"?
- **Gap:** The application shows both closing lines. The approved image [D4], chosen as the reference in the business clarification (Q-04), ends at the table. The story's written acceptance-criteria text does contain them.
- **Why it matters:** It decides whether PB-1 is an application defect or a wrong reference. TC-HAJJ-02 currently fails against the image.
- **Affected TCs:** TC-HAJJ-02
- **Evidence:** observed live on 2026-11-03 on PO details and the ASN creation page for purchase order 4300000831 (screenshot `evidence/PB-1-2026-11-03.png`); the embedded image in Azure DevOps revision 29 shows no closing lines.
- **Recommended:** Ask the PO to confirm the greeting belongs in the notice. If it does, close PB-1 as "not a defect", correct TC-HAJJ-02 step 8 through skill 3 `--revision`, and ask the PO to replace the image with one that matches.
- **Alternatives:** The greeting is genuinely unwanted and the code removes it — in which case PB-1 stands as a defect.
- **Pending until answered:** nothing — answered.
- **Status:** answered 2026-11-03 by Mohamed Sabry (QC), PO to verify — the greeting "شكرًا لتعاونكم / مع أطيب التحيات" belongs in the notice; the image attached to the story was cropped. PB-1 is resolved as not a defect, and TC-HAJJ-02 step 8 must assert the two closing lines instead of their absence (skill 3 `--revision`).

## Open Findings for the Human Reviewer

### Requirement / coverage gaps
- REQ-234822-11 (only suppliers see the notice) has no test case, because NUPCO staff screens were declared out of scope. This is the one requirement at 0.0 in the coverage score — see Q-5.
- **The reference image is cropped and should be replaced** (business review finding 234822-AC5-AMB-1). The notice really ends with "شكرًا لتعاونكم" and "مع أطيب التحيات", as the story's written text says and the application shows; the image omits them (Q-6). The PO should attach an image that shows the whole notice, so [D4] is a single trustworthy reference again.
- The spelling inside the notice ("إستلام", "ادناه", "الادوية") is unusual (business review finding 234822-AC5-AMB-2). TC-HAJJ-02 asserts the text exactly as the application shows it, so a corrected text means a corrected test case.
- TC-HAJJ-06 (plant W2C1 on another storage location) — kept; data found on another purchase order on 2026-11-04 and the test case passed.

### Application defects (discrepancies)
- TC-HAJJ-11 — see PB-2: the exported ASN PDF drops the colon that ends the notice's intro sentence (REQ-234822-06). Low severity; raise it as a bug against US 234822.
- PB-1 (the closing greeting) was resolved on 2026-11-03 as not a defect — the reference image was cropped (Q-6). TC-HAJJ-02 was revised and re-validated on 2026-11-04.

### Pending implementation
none — the story is Implemented, confirmed live on 2026-11-03: the notice appears on PO details and on the ASN creation page for a W2C1 / 6000 destination.

### Environment blockers
- **Created in Staging and kept:** ASN **5060-261103-19820** (invoice QA3C-234822-1103, batch QA3CB1, 10 units) on purchase order 4300000831, destination W2C1 / 6000 — created by TC-HAJJ-10 on 2026-11-03 with the user's go-ahead. It needed the NUPCO GLN for W2C1 / 6000, which the user added to the RSD GLN table, and the GTIN 04110410701401 in the line's batch row.
- **TC-HAJJ-11 was completed by the reviewer on 2026-11-04.** The PDF of ASN 5060-261103-19820 carries the whole notice, but the colon that ends the intro is missing — recorded as PB-2 (application defects above).
- **An ASN from before the release** [D7] was not found yet. The supplier's requests are under "My Requests", which holds 45,425 requests; finding one on the W2C1 / 6000 destination created before the release needs a targeted search. TC-HAJJ-12 could not run.
- **Solved 2026-11-04 — a second W2C1 storage location was found** [D2]: purchase order 4300000834 offers W2C1 / 1000 "MOH Stock" (also on 4300000835, 4300000832 and 4300000829), and 4300000833 offers W2C1 / 4000 "MOH - Makkah". TC-HAJJ-06 ran on 4300000834 and passed.
- **The map links were not followed** to the external map sites (TC-HAJJ-04). Both links carry the right addresses and open in a new tab, which was confirmed, but the sites themselves were not opened in this run.
- The capacity ledger's hold for this run's browser session could not be released, although the browser is closed. This is the known ledger behaviour recorded in the learning file; it was reported, not forced.

### Unclear requirements
- Q-3 — whether the supplier portal has a language control at all (none found on the pages walked).
- Q-4 — the behaviour when the notice content fails to load.
- Q-5 — whether NUPCO staff screens must be checked.
- Q-6 — answered: the closing greeting belongs in the notice (PB-1 resolved, not a defect).
- Q-1 and Q-2 are answered by evidence — see Open Questions.

## Corrections Applied

Revision 1 — 2026-11-03, from the reviewer's answers in chat. Only the test cases named here were touched.

| Feedback item | TC-ID(s) | Fix applied |
|---|---|---|
| "no it isn't a bug 'شكرًا لتعاونكم / مع أطيب التحيات' — maybe it was cropped" | TC-HAJJ-02 | Step 8 and the Expected Result now require the two closing lines instead of their absence; the Data Oracle names them. PB-1 closed as not a defect. The test case is reset to `draft (stale — revised)` and its evidence stamp removed. |
| "note the requests type is just normal asn" | TC-HAJJ-09 (withdrawn) | The direct-delivery test case was removed: a Hajj destination offers "Request ASN" only (Q-2, confirmed live). Totals, automation candidates, the traceability matrix and the per-requirement coverage rows were recomputed; data item [D6] was dropped from TEST-DATA. Coverage of REQ-234822-02 and REQ-234822-03 stays full. |
| Also corrected from the live evidence of 2026-11-03, not asked for by the reviewer | TC-HAJJ-02 | Step 3 now quotes the intro with the space the application shows after the colon ("إشعار هام: يرجى…"); the earlier quote had none and would have failed on re-validation. Flagged here so the reviewer can object. |

**Not addressed** — no decision was given, so nothing was changed:
- TC-HAJJ-06 — whether to keep, re-data or withdraw it (no second W2C1 storage location on the purchase order in use).
- TC-HAJJ-11 — the reviewer's own reading of the exported PDF, including whether the closing colon is missing there.
