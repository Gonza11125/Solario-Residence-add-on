# Solario Residence for Home Assistant

Public installation repository for the Solario Residence Home Assistant app.

The application source code, synchronization runtime, tests, release workflow and security implementation are maintained privately. This repository contains only the metadata and user documentation required by Home Assistant.

## Installation

Add this repository to the Home Assistant app store:

`https://github.com/Gonza11125/Solario-Residence-add-on`

Then install **Solario Residence**.

## Current release

Solario Residence 0.2.2 is a functional experimental Residence bridge. It reads real Home Assistant entities through the Supervisor API, lets an administrator map the building's actual PV, consumption, grid, battery and apartment meters, stores configuration persistently, and can pair the installation with Solario Cloud.

The production UI does not substitute a demo building or sample measurements. Unconfigured or unavailable measurements are shown as unavailable until real entities are mapped.
