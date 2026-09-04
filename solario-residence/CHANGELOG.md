# Changelog

## 0.3.7

- Added a separate read-only Residence automation snapshot sync from Local to Solario Residence Cloud.
- Cloud automation transport sends only sanitized `automation.*` observability fields already exposed by Residence Local; it does not expose Home Assistant credentials or control actions.
- Unsupported stop time, duration, action, daily count, energy and CZK savings remain null instead of being estimated.
- Automation sync failure is isolated from the existing energy synchronization so it cannot interrupt normal Residence Cloud telemetry.

## 0.3.6

- Hid the legacy apartment/unit surface from the current Residence product UI while preserving all stored unit data and runtime support for future use.
- Removed the apartment consumption widget from the default and persisted visible dashboard configuration.
- Hid the unit editor from Residence Studio so apartments no longer appear in normal Local or Solario Admin web views.

## 0.3.5

- Replaced the visible apartment navigation with a new read-only Automations view while keeping apartment/unit code and stored configuration available for future use.
- Added a role-gated Residence automation endpoint backed only by real Home Assistant `automation.*` entities.
- Shows enabled/disabled state, availability, currently running executions, `last_triggered`, execution mode and last Home Assistant update.
- Added a nullable automation data model for last action, stop time, run duration, daily run count, saved energy and CZK savings; unsupported values remain empty instead of being estimated.
- Added a minimal last-known activity entry only when Home Assistant supplies a real trigger timestamp, with no controls for starting, stopping or modifying automations.

## 0.3.4

- Replaced the Local role-preview switch with real, backend-enforced SVJ and Solario Admin authentication.
- Added separate random recovery codes for SVJ and Solario Admin; plaintext codes are shown only when created and persistent storage contains only scrypt-derived credentials.
- Added signed HttpOnly Local sessions, login throttling, named/revocable identities and Solario Admin-only access to technical configuration, mapping and service operations.
- Added optional passkey sign-in using Windows Hello, Face ID, Touch ID or device PIN on secure origins; the server stores only the public passkey material and the recovery code remains available as a fallback.
- Restricted first Local credential bootstrap to the Home Assistant ingress administration surface and prevented public auth status from disclosing identity names or roles.

## 0.3.3

- Increased undersized Residence labels, status text, chart annotations, device details and configuration hints for better readability.
- Raised the smallest 8–10 px secondary text to an approximately 11–12 px readability floor while keeping primary values, layout and Residence visual design unchanged.
- Applied the same readability pass to Residence Studio, entity mapping, runtime facts and one-time activation-code guidance.

## 0.3.2

- Replaced the temporary Residence checkout/pairing UX with the same partner-key model used by Solario Home.
- Added one-time `RESIDENCE-...` license key activation for the single paid Residence PRO tier.
- Home SMART/PRO keys are rejected by Residence and Residence keys are product-isolated in Solario Cloud.
- Successful activation enables lifetime Residence PRO, links the installation to Solario Residence Cloud and returns a separate one-time Cloud access code.
- The readable Cloud access code is shown only once; persistent state stores only its scrypt-derived credential.
- Home Assistant and Supervisor credentials remain local and are never included in the Cloud activation request.

## 0.3.1

- Made Residence Cloud connection a clear, user-driven code flow in Residence Studio.
- Added an explicit generated cloud code step, copy action and button to continue to Solario Residence Cloud instead of opening checkout immediately.
- Added clearer pairing status, Cloud site ID and last synchronization information.
- Kept Home Assistant and Supervisor credentials local; only the Residence export and cloud device identity are used for synchronization.
- Kept the existing secure activation backend and automatic completion/polling behavior.

## 0.3.0

- Introduced the shared Solario ecosystem visual language for Residence while preserving the existing Residence layout and information architecture.
- Added the dark slate Solario navigation shell, amber/orange brand accent and light slate/white workspace.
- Kept Residence-specific energy-flow, apartment, device and management layouts intact.
- Kept green as a semantic health/self-energy color, with distinct battery and grid accents.
- Renamed the visible local surface to Solario Residence Local without changing the technical slug, product type or pairing identity.
- Includes the Home Assistant Ingress API routing fix from 0.2.3.

## 0.2.3

- Fixed Residence frontend API requests under Home Assistant Ingress so they stay inside the add-on instead of being sent to the Home Assistant root API.
- Kept direct LAN access using the same local `/api` endpoints.
- Added regression coverage for Ingress URLs with and without a trailing slash.

## 0.2.2

- Removed the Rezidence Javorová demo dataset from the production frontend bundle.
- Removed the automatic demo fallback when the local Residence runtime cannot be reached.
- The dashboard now waits for real Home Assistant data and keeps only the last real snapshot during a temporary runtime outage.
- Unmapped or unavailable Home Assistant measurements are displayed as unavailable instead of being presented as measured zeroes.
- Apartment consumption rankings now require real mapped meter values.
- Updated public documentation for the real Home Assistant mapping and Cloud pairing workflow.

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
