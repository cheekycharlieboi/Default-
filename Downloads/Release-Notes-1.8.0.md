# Armstrong Bill of Materials 1.8.0

One installer and application now provide engineer editing and both view-only access levels through the B000 login. The previous separate Viewer package is no longer produced.

## Login and shared working
- Engineer names include the existing engineers and Andrei Cojocaru, Dilani Rajapakshe, Aaron Hindmarsh, Abdel Mumem Elmeselaty, Andrew Taylor and Mohammed Salam. Initial engineer PIN is 1234; each engineer can reset their own four-digit PIN under B042. Reset requires their current PIN. Accounts are stored as salted password hashes in Engineer-Accounts.xml in the default shared project folder; protect that folder using your server's normal permissions. These application access levels do not replace Windows file permissions.
- Public View Only (Without Costing) needs no password. View Only (with Costings) uses 1934. Both prevent project edits; the latter can show/hide costs in B042. Engineers are fixed to the logged-in identity in project details and B003; historical revisions display their saving engineer. Log out from B000 or the project toolbar to change identity.
- The shared project folder must be available for engineer authentication. Project creation/load also warns when the default server folder is unavailable. Public view-only login remains available without server authentication.
- Revision saving uses a bounded file-lock retry and an atomic version check/write. A stale writer is rejected rather than overwriting another engineer's revision. A backup queue failure is reported separately after a successful native revision save. Native Windows/UNC locking still requires workstation validation; the original reported Windows sharing error could not be reproduced here.

## Editing and revision workflow
- B010 shared phantom definitions have no routing controls. Routing belongs to project placements and is inherited through each complete phantom subtree.
- B001 quantity is before the part number and displays `6x` or `6 sets`. The destination placement/bucket has a bold red row border, in addition to the red Add to text.
- Change Selected Routings sits below Copy line. It changes selected placements in one operation. A partially selected phantom warns before changing the entire host; rejecting the warning preserves its routing. Matching placements consolidate quantities.
- Current project printing requires a recorded revision; unrevised changes require an up-revision before printing. Leaving a project or exiting offers revision saving or discarding, with a large bold red warning. Already-saved global shared phantom edits are not rolled back by discarding a project's local edits.
- B005 notes are stored with entries. Its dated history is derived from saved revisions and lists quantity/routing/notes changes and engineers, rather than logging intermediate clicks. The change history includes removal records and saved snapshot values.

## Catalogue and currency
- LN column D is source unit price; column E is its currency code, displayed as Cost unit beside Cost each. The target currency is B042 Project Currency. Unit and total BoM costs are converted using the saved matrix. Missing currency/rate information is treated as unpriced, never silently converted 1:1.
- Currency Conversions provides manual rates per EUR, an editable rate date, a computed source-to-target matrix and a reference webpage link to ECB. There is no automatic web update. Defaults are dated 2 November 2026 from the public Currency API dataset; source/date are bundled. Saved manual entries take precedence. The matrix includes currencies in the loaded LN list and supported project currencies.
- The supplied historical LN workbook contains 275,763 parts but no column-D prices or E-G metadata. Load your updated priced workbook to use source currencies and document links. Existing binary catalogues remain readable.
- B030 has Item Photo and Item Data Sheet link sections from F/G. Links are opened externally only on an explicit click; images/documents are not loaded into the screen. Plain-text links, Excel hyperlink relationships and HYPERLINK formulas are supported.

## PDF output
- B040 BoM output uses A3 portrait pages, a full-width red banner and white title: Project Master Bill of Materials (BoM) - Sorted by Full/Buckets/Routing.
- Bucket output combines matching part numbers within each bucket across routing placements and omits routing. Packed output preserves phantom hierarchy; unpacked output combines component totals.
- Routing output selects Unpack automatically and combines parts within each routing, with routing headings rather than buckets. Quantities, totals, selected costs and sorting are retained.

## Installation and validation limits
Close old application windows and back up project/shared files before updating. The unified installer updates the existing BoM Studio 1 application folder and includes source and the catalogue. An older separately installed Viewer is not removed automatically; uninstall it separately if no longer needed. Project/shared catalogue/backup files remain outside the application folder.

Automated tests run under Linux/Mono/Xvfb. See Validation-1.8.0.txt for executed suites and counts. Native Windows installation, update/uninstall, force-close, registry, shortcuts, server access and DPI scaling are not validated by those tests. The installer is unsigned.
