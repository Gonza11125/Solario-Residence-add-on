# Solario Residence

Solario Residence is the Home Assistant companion for apartment buildings, housing associations and residential communities using Solario energy management.

## Current status

Version 0.6.0 provides the complete Solario Residence Local interface: overview, live energy, the building's economics, flats, Home Assistant automations, devices, analytics, alerts and the building's Solario plan. The add-on connects to the local Home Assistant instance, discovers energy entities, allows manual or assisted mapping of the actual building data, stores Residence configuration under `/data`, and can activate authenticated synchronization with Solario Cloud.

The Ekonomika page prices every hour of the history from Home Assistant's long-term statistics with the building's own price lists and HDO hours: savings and revenue, the electricity bill with and without photovoltaics, the payback of the investment and each flat's share. The Solario Admin can edit every page: add cards from a library, remove, move and resize them.

The dashboard uses only the configured installation's real data. If a value is not mapped or its entity is unavailable, the UI shows it as unavailable instead of filling in a sample number.

The app is distributed as a pre-built container image for `amd64` and `aarch64`. Internal source code is not included in this installation repository.
