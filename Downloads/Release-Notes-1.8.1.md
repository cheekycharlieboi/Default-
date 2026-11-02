# Armstrong BoM 1.8.1

Implements the follow-up B000/B001/B005/B040/B042 and PDF comments.

- B001 has one Return to project selection & log out control, with no separate logout button. Both it and B000 Log out clear the session and project and leave a single Log In button. Logging in is a separate action.
- Revision choices use `Rev-A, yyyy-mm-dd, Engineer`, with no internal version number. Current remains the working selection.
- LN Cost unit hides and returns with the other financial columns under B042 Show project costs. View-only access restrictions continue to apply.
- Bucket/phantom/routing filters are wider and adapt to the window. Their opened dropdowns provide extra width for long names.
- Nested quantity, description and routing cells use the same six-space-per-level indentation as the part number. The master table shows `-` for inherited child routing, while B005 retains the disabled actual routing and explains `(Line Routing set by parent phantom)`.
- B005 identifies ordinary Part, Phantom, and a contained Part with its Parent Phantom separately.
- Printing compares material BoM content with the saved revision. Quantities, routing, item/phantom contents, descriptions and notes still require a revision; B042 currency, cost visibility, budget and other settings alone do not. A first saved revision is still required for a new project. Settings remain part of the in-memory project and are retained on its next save; leaving can still warn about unsaved project settings.
- PDFs embed the supplied Armstrong banner picture with white titles. Project information sits below the banner with clear vertical separation.
- Cost summaries are bordered tables with all configured buckets, including empty buckets, and totals for cost, unpriced lines, budget and remaining values. Routing summaries use routing rows, preserving the no-buckets routing report rule. Full/unpacked report summaries retain the original bucket breakdown.
- Unassigned routing groups are headed Un-Routed Parts in the item list and summary.

One unified installer continues to provide engineer and both view-only login levels. Defaults and manual rate entry introduced in 1.8.0 are retained. The old separate Viewer is not distributed or automatically removed.

See Validation-1.8.1.txt for executed checks. Tests use Linux/Mono/Xvfb; native Windows setup/update/uninstall, UNC permissions/locking and DPI scaling remain unverified. The installer is unsigned. Back up projects/shared files before updating.
