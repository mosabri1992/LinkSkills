---
source_document: TEST-CASES-hajj-w2c1-6000-notification.md
source_sha256: 15be41c03353cf8cf9fe424570ab730b132bfb803b1d3339469f362fadffb2af
beautified_on: 2026-11-04
feature: hajj-w2c1-6000-notification
requirement_ids_covered: REQ-234822-01, REQ-234822-02, REQ-234822-03, REQ-234822-04, REQ-234822-05, REQ-234822-06, REQ-234822-07, REQ-234822-08, REQ-234822-09, REQ-234822-10
tc_prefix: TC-HAJJ
---

# Test Cases (upload shape) — hajj-w2c1-6000-notification

Build artefact for Azure DevOps. Generated from the approved document named above; do not edit
by hand — edit the source and run the publish skill again. Every test case below is readable on
its own: references to other test cases have been expanded inline.

**Test data:** `TEST-DATA-hajj-w2c1-6000-notification.md` · sha256 `36f8a2dd1c494f02`

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
  1. Login with ASN supplier [A1] on the portal [E1].
  2. Check that the home page loads and the header names the supplier's company.
  3. Click on the app-grid icon at the right of the header.
  4. Click on the "NUPCO POs" tile.
  5. Check that a loading indicator appears on the PO list area.
  6. Wait for the loading indicator on the PO list area to clear.
  7. Check that the PO list table is visible with no spinner.
  8. Click on the "Cancel" button of the "SFDA Announcement" window, only if that window covers the list, and check that no overlay remains.
  9. Click on the PO number of the purchase order [D1].
  10. Check that the PO Details page opens with the breadcrumb "ASN › NUPCO POs › PO Details".
  11. Check that the heading "Select a destination to display the line items." is shown and no Hajj notice is on the page.
  12. Click on the "Select Ship To" control.
  13. Check that the "Ship To" lookup window opens with its result table loaded, showing the columns Plant code, Ship-to code, Ship-to name, Warehouse name, Inventory type and Region.
  14. Click on the radio button at the start of the row whose Plant code is "W2C1" and whose Ship-to code is "6000" [D1].
  15. Check that the row's radio button is ticked and the "Select" button is available.
  16. Click on the "Select" button in the lookup.
  17. Check that the lookup closes, the Ship To field reads "W2C1 / 6000  MOH - Al Hajj", and a loading indicator appears on the line items area.
  18. Wait for the loading indicator on the line items area to clear.
  19. Check that the line items table is shown for the chosen destination.
  20. Check that the Hajj notice panel is visible at the top of the PO Details page, its title reads "تنبيه", and it carries a close control.
- **Expected Result:** Choosing the W2C1 / storage location 6000 destination on PO details opens the Hajj notice panel, titled "تنبيه", above the line items; nothing on the page blocks the supplier from continuing.
- **Data Oracle:** NUPCO purchase order with a W2C1 / 6000 Ship-to [D1] — the PO number and the Ship-to row (plant "W2C1", storage location "6000") as recorded in TEST-DATA
- **Smoke:** YES
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —

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
  1. Login with ASN supplier [A1] on the portal [E1].
  2. Click on the app-grid icon at the right of the header, then on the "NUPCO POs" tile.
  3. Wait for the loading indicator on the PO list area to clear.
  4. Click on the "Cancel" button of the "SFDA Announcement" window, only if that window covers the list.
  5. Click on the PO number of the purchase order [D1].
  6. Click on the "Select Ship To" control.
  7. Click on the radio button of the row whose Plant code is "W2C1" and whose Ship-to code is "6000" [D1], then on the "Select" button.
  8. Wait for the loading indicator on the line items area to clear.
  9. Check that the Hajj notice panel is visible.
  10. Check that the notice title reads "تنبيه".
  11. Check that the intro sentence reads "إشعار هام: يرجى التنويه بأنه سيكون مقر إستلام الشحنات الخاصة بالحج لعام 1448 هـ لموقع توريد (SLOC W2C1-6000) في المواقع ادناه:" word for word, naming the year 1448 and the storage location W2C1-6000, and ending with the colon.
  12. Check that the table column headers read, from right to left, "التصنيف", "مكان التوريد" and "الموقع".
  13. Check that the first site row has the classification "جميع البنود", the delivery place "مستودعات نوبكو (الميناء)" with "Nupco WH" beneath it, and the location "Maersk Logistics Park (MLP), Nupco WH" with its map link beneath it — ref: https://maps.app.goo.gl/zbWJWBYQbWRjqmaWA
  14. Check that the second site row has the classification "بنود الادوية المخدرة", the delivery place "مستودعات نوبكو (حدا)" with "Nupco Haddah WH" beneath it, and the location "Hadda" with its map link beneath it — ref: https://maps.google.com/?q=21.448376,39.568314
  15. Check that the table holds exactly two site rows, so narcotic drug items have one destination (Hadda) and every other item one destination (Maersk Logistics Park).
  16. Check that the notice closes with the two lines "شكرًا لتعاونكم" and "مع أطيب التحيات", in that order, and that no further line follows them [D4].
- **Expected Result:** The notice shows the approved title, intro sentence and three-column table with exactly the two 1448 delivery sites, each with its classification and map link, and closes with "شكرًا لتعاونكم" and "مع أطيب التحيات" [D4].
- **Data Oracle:** approved Hajj 1448 notice text [D4] — intro sentence, the three column headers, two site rows with classifications "جميع البنود" and "بنود الادوية المخدرة", the two map links and the two closing lines as recorded in TEST-DATA
- **Smoke:** YES
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —

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
  1. Login with ASN supplier [A1] on the portal [E1].
  2. Click on the app-grid icon at the right of the header, then on the "NUPCO POs" tile.
  3. Wait for the loading indicator on the PO list area to clear.
  4. Click on the "Cancel" button of the "SFDA Announcement" window, only if that window covers the list.
  5. Click on the PO number of the purchase order [D1].
  6. Click on the "Select Ship To" control.
  7. Click on the radio button of the row whose Plant code is "W2C1" and whose Ship-to code is "6000" [D1], then on the "Select" button.
  8. Wait for the loading indicator on the line items area to clear.
  9. Check that the Hajj notice panel is visible.
  10. Check that the title, the intro text and the table are aligned to the right and the text runs right to left.
  11. Check that the colon closes the intro sentence after "في المواقع ادناه" and does not sit before "(SLOC W2C1-6000)", as in [D4].
  12. Check that the brackets enclose the storage location as "(SLOC W2C1-6000)", with the opening bracket on the right of the bracketed text.
  13. Check that the Hijri year reads "1448 هـ" with the year digits to the left of "هـ".
  14. Check that each of the two map links reads left to right inside the right-to-left row, with no reversed or broken characters.
  15. Check that "التصنيف" is the rightmost table column and "الموقع" the leftmost, matching [D4].
- **Expected Result:** The whole notice is laid out right to left, and the colon, the brackets around the storage location, the Hijri year and both links sit exactly where the approved image [D4] shows them.
- **Data Oracle:** approved Hajj 1448 notice image [D4] — the right-to-left layout, the closing colon, the bracketed "(SLOC W2C1-6000)", the Hijri year "1448 هـ" and the column order as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —

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
  1. Login with ASN supplier [A1] on the portal [E1].
  2. Click on the app-grid icon at the right of the header, then on the "NUPCO POs" tile.
  3. Wait for the loading indicator on the PO list area to clear.
  4. Click on the "Cancel" button of the "SFDA Announcement" window, only if that window covers the list.
  5. Click on the PO number of the purchase order [D1].
  6. Click on the "Select Ship To" control.
  7. Click on the radio button of the row whose Plant code is "W2C1" and whose Ship-to code is "6000" [D1], then on the "Select" button.
  8. Wait for the loading indicator on the line items area to clear.
  9. Check that the Hajj notice panel is visible.
  10. Click on the link in the first site row ("Maersk Logistics Park (MLP), Nupco WH").
  11. Check that a new browser tab opens and the PO Details page stays open and unchanged in the first tab.
  12. Wait for the new tab to finish loading.
  13. Check that the map site opens on the Maersk Logistics Park location and shows no error page.
  14. Click on the close control of the new tab and return to the PO Details tab.
  15. Check that the Hajj notice is still shown and the chosen destination is unchanged.
  16. Click on the link in the second site row ("Hadda").
  17. Check that a new browser tab opens.
  18. Wait for the new tab to finish loading.
  19. Check that the map site opens on the coordinates 21.448376, 39.568314 (the Hadda warehouse) and shows no error page.
- **Expected Result:** Each map link opens its own delivery site in a new browser tab without an error, and the PO Details page with the notice stays open behind it.
- **Data Oracle:** approved Hajj 1448 notice image [D4] — the Maersk Logistics Park link and the Hadda link with coordinates 21.448376, 39.568314 as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** NO
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —

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
  1. Login with ASN supplier [A1] on the portal [E1].
  2. Click on the app-grid icon at the right of the header, then on the "NUPCO POs" tile.
  3. Wait for the loading indicator on the PO list area to clear.
  4. Click on the "Cancel" button of the "SFDA Announcement" window, only if that window covers the list.
  5. Click on the PO number of the purchase order [D1].
  6. Click on the "Select Ship To" control.
  7. Click on the radio button of the row whose Plant code is "W2C1" and whose Ship-to code is "6000" [D1], then on the "Select" button.
  8. Wait for the loading indicator on the line items area to clear.
  9. Check that the Hajj notice panel is visible.
  10. Click on the checkbox of a line item in the line items table while the notice is open.
  11. Check that the line is selected, so the notice does not block the page.
  12. Click on the close control of the notice.
  13. Check that the notice panel disappears and the line items table stays as it was, with the line still selected.
  14. Click on the "Select Ship To" control, then on the radio button of another destination of [D1], then on the "Select" button.
  15. Wait for the loading indicator on the line items area to clear.
  16. Check that no Hajj notice is shown for that destination.
  17. Click on the "Select Ship To" control, then on the radio button of the W2C1 / storage location 6000 row, then on the "Select" button.
  18. Wait for the loading indicator on the line items area to clear.
  19. Check that the Hajj notice is shown again, so it returns on each choice of this destination.
  20. Click on the browser reload control on the PO Details page.
  21. Wait for the line items table to be shown.
  22. Check that the Hajj notice is shown again after the reload.
- **Expected Result:** The notice can be closed, never stops the supplier from selecting lines, and comes back each time the W2C1 / 6000 destination is chosen again or the page is reloaded.
- **Data Oracle:** NUPCO purchase order with a W2C1 / 6000 Ship-to and at least one other destination [D1] — as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —

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
  1. Login with ASN supplier [A1] on the portal [E1].
  2. Check that the home page loads.
  3. Click on the app-grid icon at the right of the header, then on the "NUPCO POs" tile.
  4. Wait for the PO list table to be shown with no spinner.
  5. Click on the PO number of the purchase order [D2].
  6. Check that the PO Details page opens.
  7. Click on the "Select Ship To" control.
  8. Check that the "Ship To" lookup window opens with its result table loaded.
  9. Click on the radio button of the row whose Plant code is "W2C1" and whose Ship-to code is not "6000" [D2], then on the "Select" button.
  10. Check that the lookup closes and a loading indicator appears on the line items area.
  11. Wait for the loading indicator on the line items area to clear.
  12. Check that the line items table is shown.
  13. Check that no Hajj notice panel is shown anywhere on the PO Details page and the title "تنبيه" appears nowhere on it.
- **Expected Result:** A destination on plant W2C1 with a storage location other than 6000 shows no Hajj notice; the page opens its line items as usual.
- **Data Oracle:** NUPCO purchase order with a W2C1 Ship-to on a storage location other than 6000 [D2] — the PO number and the storage location as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —

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
  1. Login with ASN supplier [A1] on the portal [E1].
  2. Check that the home page loads.
  3. Click on the app-grid icon at the right of the header, then on the "NUPCO POs" tile.
  4. Wait for the PO list table to be shown with no spinner.
  5. Click on the PO number of the purchase order [D3].
  6. Check that the PO Details page opens.
  7. Click on the "Select Ship To" control.
  8. Click on the radio button of a row whose Plant code is not "W2C1" [D3], then on the "Select" button.
  9. Wait for the loading indicator on the line items area to clear.
  10. Check that the line items table is shown.
  11. Check that no Hajj notice panel is shown anywhere on the PO Details page and the title "تنبيه" appears nowhere on it.
  12. Click on the checkbox of a line item.
  13. Click on the request control the toolbar offers for this destination — it reads "Request Direct Delivery ASN" for a plant 1100 destination and "Request ASN" for others.
  14. Wait for the ASN request creation page to load.
  15. Check that no Hajj notice is shown on the ASN request creation page either.
- **Expected Result:** A destination on any plant other than W2C1 shows no Hajj notice, on PO details or on the ASN request creation page.
- **Data Oracle:** NUPCO purchase order with a Ship-to on a plant other than W2C1 [D3] — the PO number and the plant code as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —

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
  1. Login with ASN supplier [A1] on the portal [E1].
  2. Click on the app-grid icon at the right of the header, then on the "NUPCO POs" tile.
  3. Wait for the loading indicator on the PO list area to clear.
  4. Click on the "Cancel" button of the "SFDA Announcement" window, only if that window covers the list.
  5. Click on the PO number of the purchase order [D1].
  6. Click on the "Select Ship To" control.
  7. Click on the radio button of the row whose Plant code is "W2C1" and whose Ship-to code is "6000" [D1], then on the "Select" button.
  8. Wait for the loading indicator on the line items area to clear.
  9. Check that the Hajj notice panel is visible on PO Details.
  10. Click on the checkbox of one line item in the line items table.
  11. Check that the line's checkbox is ticked and the "Request ASN" control is available in the line items toolbar, and that for a W2C1 / 6000 destination the toolbar offers "Request ASN" only, never "Request Direct Delivery ASN".
  12. Click on "Request ASN".
  13. Check that the browser navigates away from PO Details to the ASN creation page, titled "ASN | Create".
  14. Wait for the ASN creation page to load.
  15. Check that the page shows its "Request Details" form with the fields "Invoice number", "Delivery Date" and "Delivery Time", and no spinner.
  16. Check that the Hajj notice is shown at the top of the ASN creation page above "Request Details", with the title "تنبيه", the same intro sentence and the same two site rows as on PO details [D4], and that "Shipped to Location" reads "MOH - Al Hajj".
  17. Scroll to the end of the request details form.
  18. Check that the notice stays at the top of the page as page content and does not cover the form fields.
- **Expected Result:** The ASN request creation details page for a W2C1 / 6000 destination shows the Hajj notice as a fixed box at the top, with the same approved content as on PO details.
- **Data Oracle:** approved Hajj 1448 notice image [D4] — title, intro sentence and the two site rows as recorded in TEST-DATA
- **Smoke:** YES
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —

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
  1. Login with ASN supplier [A1] on the portal [E1].
  2. Click on the app-grid icon at the right of the header, then on the "NUPCO POs" tile.
  3. Wait for the loading indicator on the PO list area to clear.
  4. Click on the "Cancel" button of the "SFDA Announcement" window, only if that window covers the list.
  5. Click on the PO number of the purchase order [D1].
  6. Click on the "Select Ship To" control.
  7. Click on the radio button of the row whose Plant code is "W2C1" and whose Ship-to code is "6000" [D1], then on the "Select" button.
  8. Wait for the loading indicator on the line items area to clear.
  9. Click on the checkbox of one line item, then on "Request ASN".
  10. Wait for the ASN creation page to load.
  11. Check that the Hajj notice is shown on the ASN creation page.
  12. Enter value for "Delivery Date" through its date picker.
  13. Select the "Delivery Time" from its dropdown of hourly slots, for example "10:00 am".
  14. Enter value for "No. of Pallets" on the line.
  15. Check that each of these fields shows its value, and that the "NUPCO GLN" field fills itself and is read-only.
  16. Click on the expand arrow at the end of the line row, then on the expand arrow at the end of the line-item row inside it.
  17. Check that a batch row opens with the fields "GTIN", "Batch Number", "Quantity", "Manufacturing date" and "Expiry date".
  18. Enter value for "GTIN" with the item's 14-digit GTIN — a 13-digit GTIN is written with a leading zero.
  19. Enter value for "Batch Number", using letters and digits only.
  20. Enter value for "Quantity".
  21. Enter value for "Manufacturing date".
  22. Enter value for "Expiry date".
  23. Check that each batch field shows its value.
  24. Enter value for "Invoice number" last, at most 16 characters — the date pickers can clear it.
  25. Check that the "Invoice number" field shows the full value.
  26. Click on "Create" and read the page at once.
  27. Check that no short-lived message such as "Please fill GTIN for trade …" or "GTIN must be exactly 14 digits." appears, and that the window "Your Request Has Been Sent" opens with the request number of the new ASN [D5].
  28. Click on "Back To My Requests".
  29. Click on the new request number in the "My Requests" list.
  30. Check that the ASN page titled "ASN | Details" opens for [D5], showing "Shipped to Location" as "MOH - Al Hajj".
  31. Check that no Hajj notice is shown anywhere on the ASN details page and the title "تنبيه" appears nowhere on it.
- **Expected Result:** The Hajj notice belongs to the ASN request creation page only; once the ASN is submitted, its details page shows no notice.
- **Data Oracle:** the ASN created by this test case [D5] — its ASN number as shown in the success message
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** creates
- **Shared data:** ASN raised on the W2C1 storage location 6000 destination [D5]
- **Tags:** —

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
  1. Login with ASN supplier [A1] on the portal [E1].
  2. Click on the app-grid icon at the right of the header, then on the "NUPCO POs" tile.
  3. Wait for the loading indicator on the PO list area to clear.
  4. Click on the "Cancel" button of the "SFDA Announcement" window, only if that window covers the list.
  5. Click on the PO number of the purchase order [D1].
  6. Click on the "Select Ship To" control.
  7. Click on the radio button of the row whose Plant code is "W2C1" and whose Ship-to code is "6000" [D1], then on the "Select" button.
  8. Wait for the loading indicator on the line items area to clear.
  9. Click on the checkbox of one line item, then on "Request ASN".
  10. Wait for the ASN creation page to load.
  11. Enter value for "Delivery Date", select the "Delivery Time" and enter value for "No. of Pallets" on the line.
  12. Click on the expand arrow at the end of the line row, then on the expand arrow at the end of the line-item row inside it.
  13. Enter value for "GTIN" (14 digits), "Batch Number", "Quantity", "Manufacturing date" and "Expiry date" in the batch row.
  14. Enter value for "Invoice number" last, at most 16 characters.
  15. Click on "Create".
  16. Check that the success window "Your Request Has Been Sent" names the new ASN [D5].
  17. Click on the export PDF control in the success message.
  18. Check that the PDF file downloads and its name names the ASN [D5].
  19. [HUMAN] Open the downloaded PDF and read the area under the document header — assert the Hajj notice is printed there, with the title "تنبيه" and the intro sentence naming Hajj 1448 and the storage location W2C1-6000, matching [D4].
  20. [HUMAN] Read the notice table in the PDF — assert it holds the three column headers and both site rows, with "جميع البنود" against Maersk Logistics Park and "بنود الادوية المخدرة" against Hadda, in the same right-to-left order as [D4].
  21. [HUMAN] Read the two map links in the PDF — assert each link text is complete and unbroken, and that selecting it opens its delivery site.
- **Expected Result:** The exported ASN PDF of a W2C1 / 6000 destination carries the whole Hajj notice under the document header: title, intro sentence, the three-column table with both sites and both working map links.
- **Data Oracle:** approved Hajj 1448 notice image [D4] — the intro sentence, column headers, the two site rows and the two map links as recorded in TEST-DATA; the ASN created by this test case [D5]
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** creates
- **Shared data:** ASN raised on the W2C1 storage location 6000 destination [D5]
- **Tags:** —

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
  1. Login with ASN supplier [A1] on the portal [E1].
  2. Check that the home page loads.
  3. Go to the ASN list.
  4. Check that the row of the ASN created before the release [D7] is shown, with its creation date before the release date.
  5. Click on that ASN.
  6. Click on the export PDF control.
  7. Check that the PDF file downloads.
  8. [HUMAN] Open the downloaded PDF and read the notice area — assert it shows the Hajj 1448 intro sentence and the two 1448 sites, not the Hajj 1447 content, matching [D4].
- **Expected Result:** Re-exporting the PDF of an ASN created before the release shows the current Hajj 1448 notice, so every exported document carries the same delivery sites.
- **Data Oracle:** ASN created before the Hajj 1448 release on a W2C1 / 6000 destination [D7] — its ASN number and creation date as recorded in TEST-DATA; approved Hajj 1448 notice image [D4]
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —

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
  1. Login with ASN supplier [A1] on the portal [E1].
  2. Click on the app-grid icon at the right of the header, then on the "NUPCO POs" tile.
  3. Wait for the loading indicator on the PO list area to clear.
  4. Click on the "Cancel" button of the "SFDA Announcement" window, only if that window covers the list.
  5. Click on the PO number of the purchase order [D1].
  6. Click on the "Select Ship To" control.
  7. Click on the radio button of the row whose Plant code is "W2C1" and whose Ship-to code is "6000" [D1], then on the "Select" button.
  8. Wait for the loading indicator on the line items area to clear.
  9. Check that the Hajj notice panel is visible.
  10. Check that the text "Tamer Logistics" appears nowhere in the notice on PO details, and that no row names "مستودعات نوبكو (حي الخمرة)".
  11. Check that the intro sentence names the year 1448 and that the year 1447 appears nowhere in the notice.
  12. Check that the table holds two site rows, not the three of the previous year.
  13. Click on the checkbox of one line item, then on "Request ASN".
  14. Wait for the ASN request creation page to load.
  15. Check that the notice on the ASN request creation page also names 1448 only, with no "Tamer Logistics" row.
- **Expected Result:** Neither the PO details notice nor the ASN request creation notice carries any Hajj 1447 content: no Tamer Logistics site, no third row and no 1447 year.
- **Data Oracle:** approved Hajj 1448 notice image [D4] — exactly two site rows, Maersk Logistics Park and Hadda, with no Tamer Logistics row, as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —

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
  1. Login with ASN supplier [A1] on the portal [E1].
  2. Check that the home page loads.
  3. Click on the app-grid icon at the right of the header, then on the "NUPCO POs" tile.
  4. Check that a loading indicator appears on the PO list area.
  5. Wait for the loading indicator on the PO list area to clear.
  6. Check that the PO list table is shown.
  7. Click on the "Cancel" button of the "SFDA Announcement" window, only if that window covers the list, and check that no overlay remains.
  8. Check that the PO number of the purchase order [D1] is in the table, so a W2C1 / 6000 purchase order is on screen.
  9. Check that no Hajj notice panel is shown anywhere on the PO list page and the title "تنبيه" appears nowhere on it.
- **Expected Result:** The NUPCO PO list shows no Hajj notice, even when a W2C1 / 6000 purchase order is listed; the notice belongs to the destination choice on PO details.
- **Data Oracle:** NUPCO purchase order with a W2C1 / 6000 Ship-to [D1] — its PO number as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —

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
  1. Login with ASN supplier [A1] on the portal [E1].
  2. Click on the app-grid icon at the right of the header, then on the "NUPCO POs" tile.
  3. Wait for the loading indicator on the PO list area to clear.
  4. Click on the "Cancel" button of the "SFDA Announcement" window, only if that window covers the list.
  5. Click on the PO number of the purchase order [D1].
  6. Click on the "Select Ship To" control.
  7. Click on the radio button of the row whose Plant code is "W2C1" and whose Ship-to code is "6000" [D1], then on the "Select" button.
  8. Wait for the loading indicator on the line items area to clear.
  9. Check that the Hajj notice panel is visible in Arabic.
  10. Click on the portal language control in the header.
  11. Check that the language options are shown.
  12. Select Arabic as the portal language.
  13. Check that the page reloads or re-renders and the shell labels change language.
  14. Go to the PO Details page of [D1] and choose the W2C1 / 6000 destination again.
  15. Wait for the line items table to be shown.
  16. Check that the Hajj notice is shown.
  17. Check that its title, intro sentence and both site rows are the same Arabic text as in step 9 and match [D4], with no translated or duplicated version beside it.
  18. Select English as the portal language and reopen the same destination.
  19. Check that the notice is still the same Arabic text.
- **Expected Result:** The Hajj notice is shown in Arabic only; switching the portal language does not translate it, duplicate it or remove it.
- **Data Oracle:** approved Hajj 1448 notice image [D4] — the Arabic title, intro sentence and both site rows as recorded in TEST-DATA
- **Smoke:** NO
- **Automation Candidate:** YES
- **Data effect:** read-only
- **Shared data:** —
- **Tags:** —

> Needs human review (TC-HAJJ-15, steps 10 to 12 and 18): the supplier portal's language control was not found on any screen walked on 2026-11-03 — no label, position or option names are confirmed. Open question Q-3 in the source document.
