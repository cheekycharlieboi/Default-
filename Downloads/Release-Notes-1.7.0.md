# Armstrong Bill of Materials 1.7.0

Implements the outstanding comments supplied with the 1.6.0 handover.

- Every nested phantom and component inherits the routing of its top-level placement. Changing that placement updates its complete subtree; child routing is read-only in the project line editor.
- Matching phantom placements in the same bucket and routing combine quantities. Different routings and distinct bucket identities remain separate. This also applies when loading legacy current projects, copying lines or editing a placement to match another routing. Issued historical snapshots are preserved.
- Unpacked Full BoM, Bucket and Routing reports retain host routings, keep different routings separate and multiply nested quantities. Full/Bucket PDFs show the retained routing column.
- Excel re-import accepts a shared definition repeated under different inherited routings. Definition comparisons no longer treat placement routing as part of a shared definition.
- B001 bucket descriptions are blank. The smaller LN search and normal options are separated from the right-side shared phantom/display phantom controls by a vertical line.
- B048 has Full LN Part List and Parts in current project BoM only display choices. Project-only includes nested components; PDF export uses the displayed list.
- B040 has bold Print type / Print options headings and a horizontal divider. Its action changes between Create PDF, Select Buckets and Select Routing.
- B053/B054 have vertically stacked selection controls at the right with a divider. Print to PDF and Cancel are at bottom left. Cancelling a selector returns to print options without printing.

## Validation and limitations
Built the engine, Editor, restricted Viewer, uninstaller and separate installer executables using Mono 6.12 targeting .NET Framework APIs. Passed the existing 43 engine checks, 3 focused engine/PDF checks and 12 GUI checks (expectations updated for the requested routing and labels), plus 46 focused 1.7 regression checks for inheritance, filtering, totals, unpacking, migration, Excel roundtrip and screen controls. GUI automation uses Linux/Xvfb; it is not native Windows acceptance. PDF text is independently extracted to check routing and quantities. Installer payloads have SHA-256 manifests and are extracted and independently checked before delivery; the Viewer payload excludes Editor and source.

Native Windows installation, update, uninstall/force-close, shortcuts, registry integration, UNC shares and DPI/display scaling have not been tested here. Installers are not code-signed. Back up project and shared catalogue files and try the update on a test Windows workstation first. The catalogue included is the original supplied LN dataset; it has not been refreshed from your server.

## Building
Run Source/Build-Windows.cmd to build Windows executables. With Python available on the development machine, run Source/Package-Installers.py with --compiler pointing to the .NET Framework csc.exe. It packages existing build outputs with verified hashed payloads and produces separate Editor/Viewer installers and uninstallers. End users do not need Python. The Editor installer includes the source; the Viewer installer does not.
