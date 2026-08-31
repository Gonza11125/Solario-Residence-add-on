# Solario Residence

Solario Residence is the Home Assistant companion for apartment buildings, housing associations and residential communities using Solario energy management.

## Current status

Version 0.2.2 is a functional experimental integration foundation. The add-on connects to the local Home Assistant instance, discovers energy entities, allows manual or assisted mapping of the actual building data, stores Residence configuration under `/data`, and can activate authenticated synchronization with Solario Cloud.

The dashboard uses only the configured installation's real data. If a value is not mapped or its entity is unavailable, the UI shows it as unavailable instead of filling in a sample number.

The app is distributed as a pre-built container image for `amd64` and `aarch64`. Internal source code is not included in this installation repository.
