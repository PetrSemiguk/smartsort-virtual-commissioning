# vfd-sim

Python model of a variable frequency drive (VFD) for the conveyor motor.

- Implemented with `pymodbus` as a Modbus TCP server that emulates a drive register map (control word, status word, speed setpoint, actual speed).
- Models acceleration/deceleration ramps and fault states so the PLC drive logic can be tested without hardware.
