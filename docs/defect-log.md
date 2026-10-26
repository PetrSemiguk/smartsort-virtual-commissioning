# Defect Log

| ID | Found in | Description | Root cause | Fix | Status |
|---|---|---|---|---|---|
| DEF-001 | HMI test, step 4 | E-STOP button on HMI was displayed as "pressed" while E-stop was healthy (misleading operator feedback) | Toggle button drawn as pressed when its variable is TRUE; it was bound directly to NC input `xEStop_NC` (TRUE = healthy) | Added simulation variable `xSim_EStopPressed` (TRUE = pressed) bound to HMI button; separate Ladder network converts it to NC signal `xEStop_NC` | Closed, retested OK |
