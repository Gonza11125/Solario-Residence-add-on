# Solario Residence documentation

## Access

After installation, start Solario Residence and open it through the protected Home Assistant Ingress interface.

Optional direct LAN administration access is disabled by default. It can be enabled by assigning a host port to `3000/tcp` in the app Network settings. Do not forward this port from your router to the public internet.

## Version 0.2.0

The add-on now uses a real Home Assistant runtime instead of the Rezidence Javorová mock preview. It can read sanitized Home Assistant entity metadata, suggest energy mappings, persist the Residence structure and unit/meter assignments, and connect the installation to the dedicated Solario Residence Cloud flow.

The stable installation identity and local configuration are stored in `/data`, which is included in hot backups. Home Assistant/Supervisor credentials stay local to the add-on.

Cloud synchronization requires `cloud_url` to point to Solario Cloud. The default is `https://solario.cloud`. The synchronization interval can be adjusted in the add-on configuration.

## Updates

Home Assistant will offer an update after this repository publishes a newer version and the matching multi-architecture container image is available.

## Security

Do not post credentials, tokens, private addresses or detailed security reports in public issues. Report suspected security issues privately.
