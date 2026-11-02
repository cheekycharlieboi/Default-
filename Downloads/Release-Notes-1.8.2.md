# Armstrong BoM 1.8.2

- B005 places Parent Phantom in the left heading column and its number in the right value column.
- B042 is taller, with a larger Software Setting area. At the default size all software controls fit without a vertical scrollbar; scrolling remains a fallback on smaller/high-DPI displays.
- Locked PDF overwrites offer Retry/Cancel. Retry repeats the write after the file is released. PDF data is first written to a temporary file and then replaces the destination; Cancel preserves the previous file. Other errors retain their original diagnostics.
- Continuation-page column headings start farther below the project information. This also applies to revision-history continuation headings.
- B040 has a Start cost summary on its own sheet option, checked by default when including costs. The selected cost summary begins on a new PDF page. Summary-only prints do not receive an empty preceding page.
- Routing section headings include the number and configured name, for example Routing 10 - Mechanical Assembly. Un-Routed Parts remains the heading for routing zero.
- The actual B001 return button is tested through its Click action, including the discard-edits confirmation, to reach an empty session with only Log In. Additional guards prevent late background loading, file opens or workspace requests from restoring a logged-out screen.

191 automated checks pass under Linux/Mono/Xvfb. Locked-file Cancel and Retry are exercised with a real local locked target; independent PDF text/geometry checks verify a four-page report with three clear item headings and a separate summary page. Native Windows setup/update/uninstall, UNC permissions/locking and DPI scaling remain unverified. The installer is unsigned. Back up shared/project files before updating.

The unified application retains engineer/default PIN1234, public no-cost view-only and costed view-only PIN1934. Shared account and manual-currency requirements are unchanged from1.8.0/1.8.1.
