# Solario Residence documentation

## Access

After installation, start Solario Residence and open it through the protected Home Assistant Ingress interface.

Optional direct LAN administration access is disabled by default. It can be enabled by assigning a host port to `3000/tcp` in the app Network settings. Do not forward this port from your router to the public internet.

## Initial setup

Open **Správa / Residence Studio** and verify that Home Assistant is connected. Then:

1. Set the real Residence and building name and address.
2. Run assisted entity discovery.
3. Review and confirm the real entities for PV power, building consumption, grid flow, battery values and daily energy totals.
4. Confirm the daily grid meters separately: **Odběr ze sítě dnes** and **Přetok do sítě dnes**. Discovery keeps the two directions apart, but check that the proposed entity really measures the direction its name claims.
5. Enter your purchase price in **Ceny elektřiny**, and the feed-in price if you are paid for surplus production.
6. Add the actual apartments or other units and assign their meter entities where available.
7. Confirm that the dashboard shows live values from those mappings. Unmapped or unavailable measurements are displayed as unavailable, not replaced with sample data.
8. When the local configuration is correct, start Solario Cloud pairing from the same administration screen.

The installation ID is stored persistently under `/data`, so a normal add-on restart does not create a new Residence identity.

## Economics

Self-consumption, self-sufficiency and today's saving are calculated from the mapped daily totals and the prices entered in Residence Studio:

- **Vlastní využití** — the share of today's production the residence kept, from production minus export.
- **Soběstačnost** — the share of today's consumption covered without buying from the grid, from consumption minus import.
- **Úspora dnes** — the energy that was not bought, valued at the purchase price, plus the feed-in revenue for exported energy when a feed-in price is set.

Each figure needs its own inputs. Without a purchase price the saving stays unavailable, and Residence never substitutes an assumed tariff. If a daily reading contradicts the rest of the day — for example an export total larger than the production total — the affected figure is reported as unavailable rather than estimated, because that combination means a meter is mapped incorrectly.

## Units

**Byty** lists the units configured in Residence Studio, their daily consumption and each unit's share of the consumption actually measured by the submeters. Units without a submeter are excluded from that share, so the visible percentages still add up. Allocating production between owners, monthly statements and billing exports are part of Solario Residence Cloud.

## Data handling

Solario Residence reads Home Assistant state data through the Supervisor API. The Supervisor token remains local to the add-on and is not sent to Solario Cloud. Cloud synchronization uses its own installation/device credentials after activation.

## Updates

Home Assistant will offer an update after this repository publishes a newer version and the matching multi-architecture container image is available.

## Security

Do not post credentials, access codes, tokens, private addresses or detailed security reports in public issues. Report suspected security issues privately.
