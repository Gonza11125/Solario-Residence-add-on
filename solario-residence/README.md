# Solario Residence

Solario Residence is the Home Assistant companion for apartment buildings, housing associations and residential communities using Solario energy management.

## Current status

Version **0.2.0** replaces the original mock preview with a functional Home Assistant runtime. It can discover suitable Home Assistant entities, suggest mappings for PV, building consumption, grid and battery data, store Residence configuration persistently, manage units and meter mappings, and prepare live values for Solario Cloud synchronization.

Cloud activation uses the dedicated Solario Residence flow on `solario.cloud`. A stable installation identity is kept under the add-on's persistent `/data` storage so ordinary restarts do not create a new Residence identity.

The app is distributed as a pre-built container image for `amd64` and `aarch64`. Internal source code is not included in this installation repository.
