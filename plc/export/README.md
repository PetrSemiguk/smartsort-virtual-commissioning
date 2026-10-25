# plc/export

Text exports of the PLC code so it can be read and diffed directly on GitHub.

- `*.xml` — PLCopenXML export of the project (POUs, data types, GVLs).
- `*.st` — Structured Text sources exported per POU.

Re-export after every significant change to `../codesys/` so both stay in sync.
