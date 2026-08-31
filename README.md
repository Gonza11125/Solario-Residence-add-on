# Solario Residence for Home Assistant

Public installation repository for the Solario Residence Home Assistant app.

The application source code, synchronization runtime, tests, release workflow and security implementation are maintained privately. This repository contains only the metadata and user documentation required by Home Assistant.

## Installation

Add this repository to the Home Assistant app store:

`https://github.com/Gonza11125/Solario-Residence-add-on`

Then install **Solario Residence**.

## Current release

Version **0.2.0** is the first functional Residence integration foundation. It reads Home Assistant entities through the protected Home Assistant API, supports persistent Residence configuration and unit/meter mapping, and can activate and synchronize a Residence site with `solario.cloud`.

The Home Assistant/Supervisor credential stays local to the add-on and is not exported to Solario Cloud.
