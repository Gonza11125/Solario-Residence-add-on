# Solario Residence documentation

## Access

After installation, start Solario Residence and open it through the protected Home Assistant Ingress interface.

Optional direct LAN administration access is disabled by default. It can be enabled by assigning a host port to `3000/tcp` in the app Network settings. Do not forward this port from your router to the public internet.

## Initial setup

Open **Správa / Residence Studio** and verify that Home Assistant is connected. Then:

1. Set the real Residence and building name and address.
2. Run assisted entity discovery.
3. Review and confirm the real entities for PV power, building consumption, grid flow, battery values and daily energy totals.
4. Add the actual apartments or other units and assign their meter entities where available.
5. Confirm that the dashboard shows live values from those mappings. Unmapped or unavailable measurements are displayed as unavailable, not replaced with sample data.
6. When the local configuration is correct, start Solario Cloud pairing from the same administration screen.

The installation ID is stored persistently under `/data`, so a normal add-on restart does not create a new Residence identity.

## Data handling

Solario Residence reads Home Assistant state data through the Supervisor API. The Supervisor token remains local to the add-on and is not sent to Solario Cloud. Cloud synchronization uses its own installation/device credentials after activation.

## Updates

Home Assistant will offer an update after this repository publishes a newer version and the matching multi-architecture container image is available.

## Security

Do not post credentials, access codes, tokens, private addresses or detailed security reports in public issues. Report suspected security issues privately.
