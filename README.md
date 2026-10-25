# SmartSort Line — Virtual Commissioning of a Conveyor Sorting Line

> PLC-controlled conveyor line that sorts parts by type, commissioned virtually: CODESYS logic, a Factory I/O digital twin, a simulated VFD and an Ignition SCADA, verified by a FAT protocol.

**Status: 🚧 In progress**

![CODESYS](https://img.shields.io/badge/CODESYS-V3.5-red)
![IEC 61131-3](https://img.shields.io/badge/IEC_61131--3-LD_%7C_ST-blue)
![Factory I/O](https://img.shields.io/badge/Factory_I%2FO-3D_Simulation-orange)
![Ignition](https://img.shields.io/badge/Ignition-Maker_Edition-purple)
![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![Modbus TCP](https://img.shields.io/badge/Modbus-TCP-green)
![OPC UA](https://img.shields.io/badge/OPC-UA-teal)

<p align="center">
  <img src="media/gif/demo.gif" alt="SmartSort Line demo" width="800">
  <br><em>TODO: add hero GIF (media/gif/demo.gif)</em>
</p>

---

## Table of Contents

- [Overview](#overview)
- [Demo](#demo)
- [Architecture](#architecture)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [PLC Program Structure](#plc-program-structure)
- [FAT Results](#fat-results)
- [How to Run](#how-to-run)
- [Roadmap](#roadmap)
- [Disclaimer](#disclaimer)
- [Author](#author)

---

## Overview

SmartSort Line is a virtual commissioning project of a conveyor line that sorts parts by type. The PLC program is
developed in CODESYS and tested against a 3D simulation in Factory I/O instead of real hardware.
The conveyor drive is represented by a Python VFD model, and the line is operated and monitored
from an Ignition SCADA. The control logic is verified with a Factory Acceptance Test (FAT) protocol.

TODO: describe the part types, sorting criteria (sensors) and number of outlets.

## Demo

TODO: add screenshots and video links.

| Factory I/O scene | Ignition HMI | CODESYS program |
|---|---|---|
| TODO `media/screenshots/` | TODO `media/screenshots/` | TODO `media/screenshots/` |

## Architecture

TODO: add architecture diagram (see [`docs/`](docs/)).

```
 ┌──────────────────┐   Modbus TCP   ┌──────────────────┐
 │   Factory I/O    │◄──────────────►│                  │
 │  (3D line twin)  │                │  CODESYS PLC     │   OPC UA   ┌──────────────────┐
 └──────────────────┘                │  (soft-PLC,      │◄──────────►│ Ignition SCADA   │
 ┌──────────────────┐   Modbus TCP   │   LD + ST)       │            │ (Maker Edition)  │
 │  VFD model       │◄──────────────►│                  │            └──────────────────┘
 │ (Python/pymodbus)│                └──────────────────┘
 └──────────────────┘
```

## Features

- [ ] TODO: operating modes (Auto / Manual / Maintenance)
- [ ] TODO: sorting sequence implemented as a state machine
- [ ] TODO: conveyor drive control via simulated VFD (start/stop, speed setpoint, ramps, faults)
- [ ] TODO: alarm handling and acknowledgment
- [ ] TODO: emergency stop (functional model)
- [ ] TODO: production counters and SCADA trends

## Tech Stack

| Layer | Technology |
|---|---|
| PLC | CODESYS V3.5, IEC 61131-3 (Ladder Diagram + Structured Text) |
| Process simulation | Factory I/O (Modbus TCP driver) |
| Drive simulation | Python, pymodbus (Modbus TCP server) |
| SCADA / HMI | Ignition Maker Edition (OPC UA) |
| Testing | FAT protocol |

## PLC Program Structure

Readable code exports are in [`plc/export/`](plc/export/); the native project is in [`plc/codesys/`](plc/codesys/).

TODO: fill in actual POUs.

| POU | Language | Purpose |
|---|---|---|
| `PLC_PRG` | TODO | TODO |
| TODO | LD | TODO |
| TODO | ST | TODO |

## FAT Results

Full protocol: [`docs/`](docs/) (fat).

TODO: summary table.

| # | Test case | Expected result | Result |
|---|---|---|---|
| 1 | TODO | TODO | ⬜ |

## How to Run

TODO: verify steps and versions.

1. **PLC** — open `plc/codesys/*.project` in CODESYS V3.5, start CODESYS Control Win (soft-PLC), download and run.
2. **VFD model** — `cd vfd-sim`, install dependencies (`pip install -r requirements.txt`), run the model.
3. **Factory I/O** — open the scene from `factoryio/`, select the Modbus TCP driver, connect to the PLC.
4. **SCADA** — import the project from `scada/ignition/` into Ignition, configure the OPC UA connection to the PLC.

## Roadmap

- [x] Repository structure
- [ ] Architecture and I/O list
- [ ] State machine design
- [ ] Factory I/O scene
- [ ] PLC logic in CODESYS (LD + ST)
- [ ] Python VFD model
- [ ] Ignition SCADA
- [ ] FAT protocol and test execution
- [ ] Demo GIF, screenshots and video

## Disclaimer

This is a **simulation project created for learning and portfolio purposes**. It is not an industrial
installation and has not been validated for use with real equipment.

The emergency stop is implemented only as a **functional model** in the PLC logic. In a real machine,
the E-stop must be a hardware safety circuit (safety relay / safety PLC) designed according to the
applicable safety standards — not standard PLC software.

## Author

**Petr Semiguk** — BEng (Hons) Robotics and AI, University of Hertfordshire

TODO: add LinkedIn / email / other links.
