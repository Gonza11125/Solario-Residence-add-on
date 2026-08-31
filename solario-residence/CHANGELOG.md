# Changelog

## 0.2.1

- Fixed a crash when Home Assistant Ingress requests the app root as `//`.
- Added request-target normalization for double-slash Ingress asset and API paths.
- Added a regression test for the exact `ERR_INVALID_URL` failure seen on Home Assistant.

## 0.2.0

- Replaced the static Residence preview with a real Home Assistant add-on runtime.
- Added persistent installation identity and Residence configuration stored under `/data`.
- Added safe Home Assistant entity discovery and automatic mapping suggestions for PV, consumption, grid and battery data.
- Added configurable buildings, units and metering mappings with live Residence values instead of hard-coded demo data.
- Added the dedicated Solario Residence Cloud activation flow and authenticated live synchronization.
- Added automatic Cloud pairing maintenance and persistent device identity.
- Added production-ready multi-architecture GHCR publishing for `amd64` and `aarch64`.
- Kept Home Assistant/Supervisor credentials local; they are not exported to Solario Cloud.

## 0.1.0

- Added the first experimental Solario Residence Home Assistant preview.
- Added the Rezidence Javorová mock project with 24 apartments, 50 kWp PV and a 40 kWh battery.
- Added responsive dashboard, energy, apartments, devices, analytics and alerts screens.
- Added role previews and the initial Residence Studio configuration interface.
- Added pre-built image metadata for `amd64` and `aarch64` Home Assistant systems.
