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
5. In **Ekonomika domu** choose how the building is connected, enter its price lists (and the HDO low-tariff hours, if any) and the investment. See *Economics* below.
   For the economics of the whole history, map the daily energy counters (production, consumption, import, export), not only the power sensors.
6. Add the actual apartments or other units and assign their meter entities where available.
7. Confirm that the dashboard shows live values from those mappings. Unmapped or unavailable measurements are displayed as unavailable, not replaced with sample data.
8. When the local configuration is correct, start Solario Cloud pairing from the same administration screen.

The installation ID is stored persistently under `/data`, so a normal add-on restart does not create a new Residence identity.

## Economics

The **Ekonomika** page shows what the building's photovoltaics saved and earned, what electricity cost with and without them, where the energy went, how far the investment has paid back, and each flat's share. Pick a day, a month, a year or the whole life of the installation, and step back to any earlier period.

Everything is computed hour by hour from Home Assistant's long-term statistics (the Recorder's hourly totals of the mapped energy counters), so it covers the history from the day the installation was commissioned (at most five years back), not only the time since the add-on was installed. The add-on reads the latest month first and then the older history in the background; the page fills in as it goes. Each hour is priced by the price list in force that day, with the high or low tariff by the HDO schedule; an hour split between the two is priced proportionally.

Set it up in **Správa → Ekonomika domu** (Solario Admin only):

1. **Jak je dům připojený**
   - *Jedno odběrné místo pro celý dům*: the building buys electricity and re-bills the flats from their submeters. The solar energy of each hour is divided among the flats by what each used in that hour. Optionally enter what the flats pay the SVJ for a kWh of solar energy; otherwise they pay the grid price and the benefit stays with the building.
   - *Každý byt má vlastní odběrné místo*: the photovoltaics cover the common areas. If the building shares its surplus through EDC, each flat's share is proportional to its consumption in that hour, at most what it used.
2. **Ceníky elektřiny**: a simple price list (the final price per kWh including VAT and the monthly fixed payments) or a detailed one as on the invoice (energy, distribution and fees per kWh without VAT, VAT, fixed payments to the supplier and the distributor), plus the feed-in price. When prices change, add a new price list valid from that date; earlier periods keep their prices. Days before the first price list's date are not priced, so date it to the commissioning day or earlier.
3. **Nízký tarif (HDO)**: the low-tariff hours on weekdays, and different ones for the weekend if needed. Find them on the distributor's website by your HDO code.
4. **Investice a návratnost**: the commissioning date, the costs, subsidies, annual maintenance, and for the outlook the lifetime, the yearly loss of panel output and the yearly growth of electricity prices. A benefit from before Solario measured the installation can be added.
5. **Data a přepočet**: the grid's emission factor (0.45 kg CO₂ per kWh for the Czech Republic by default) and the state of the hourly history, with **Načíst historii znovu** to read it from Home Assistant again.

What the figures mean:

- **Přínos** — the purchase avoided (solar energy used in the building, valued at the price of that hour) plus the feed-in revenue.
- **Elektřina stála / bez FVE by stála** — the bill with the photovoltaics (purchase minus feed-in plus fixed payments) and what it would have been if all consumption had been bought.
- **Vlastní využití** and **Soběstačnost** — the share of production used in the building and the share of consumption not bought from the grid.
- **Návratnost** — how much of the net investment (costs minus subsidies) the recorded benefit has returned, after maintenance; the expected payback date uses the last twelve months, or a seasonal estimate while there is less than a year of data.

Nothing is assumed: without a price list the money stays unavailable, hours without data are left out and said so, and the outlook is labelled as an estimate. Today's figures match the overview. Every period can be downloaded as CSV (semicolons and decimal commas, opens directly in Czech Excel), as can each flat's share.

## Editing pages

As Solario Admin, open any page and choose **Upravit stránku**. Every page — Přehled, Energie, Ekonomika, Byty, Automatizace, Zařízení, Analytika and Upozornění — is made of cards:

- **Přidat kartu** opens the card library: energy, economics, flats, devices, alerts, and your own cards — a text for the residents (paragraphs, "- " lists and **bold**), a value of any Home Assistant entity, or a link (https only).
- Drag a card by its handle or move it with the arrows, set its width (a quarter, half, three quarters or the full row) and its title, open its settings (for example the period of an economics card or the entity of a measurement), hide it, or delete it.
- **Kdo kartu vidí** keeps a card for the Solario Admin only. The SVJ receives the value of a measured entity only when a card it can see shows it.
- The page's heading, title and subtitle are edited in place. **Obnovit výchozí** brings the page's original layout back.

Changes are saved at once and the SVJ sees them on its next refresh.

## Units

**Byty** lists the units configured in Residence Studio, their daily consumption and each unit's share of the consumption actually measured by the submeters. Units without a submeter are excluded from that share, so the visible percentages still add up. The economics of each flat — its solar energy, its cost and its saving — are on the **Ekonomika** page and in its CSV export.

## Tarif

The **Tarif** page shows the building's Solario plan. The SVJ and the Solario Admin both see it and may change it, because the building pays.

- **Residence Local** — 499 Kč a month. The overview, flats, meters, automations and alerts in the add-on, Solario support and automatic updates. Measurements and operational data stay in the building and are not sent to Solario Cloud.
- **Residence Cloud** — 999 Kč a month. Everything in Residence Local, plus Solario Residence Cloud on the web: the building's overview from anywhere, history in the Cloud, and access for the committee and the manager by invitation.

Choosing a plan opens the secure payment page; the plan switches on by itself within about a minute of the payment. A move up to Residence Cloud applies at once (only the difference for the rest of the period is charged), a move down to Residence Local and a cancellation at the end of the paid period. **Platební karta a faktury** opens the payment provider's page for the card and the invoices.

Without a plan the overview keeps running in the building, but without Solario Cloud, Solario support and automatic updates. A one-time RESIDENCE PRO key, entered by the Solario Admin in Správa, is Residence Cloud without an end.

Until Solario Cloud starts selling Residence plans, nothing is charged and the add-on runs in full.

## Data handling

Solario Residence reads Home Assistant state data through the Supervisor API. The Supervisor token remains local to the add-on and is not sent to Solario Cloud. Cloud synchronization uses its own installation/device credentials after activation.

## Updates

Home Assistant will offer an update after this repository publishes a newer version and the matching multi-architecture container image is available.

Once Residence plans are on sale, the add-on keeps its automatic updates on while the building has a plan and switches them off when it has none; you can still update by hand at any time.

## Security

Do not post credentials, access codes, tokens, private addresses or detailed security reports in public issues. Report suspected security issues privately.
