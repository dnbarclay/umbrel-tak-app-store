# TAK Apps for Umbrel

An Umbrel community app store containing OpenTAKServer, a TAK-compatible server
with a browser-based live map and administration UI.

## Add this store to Umbrel

Add the following repository URL under **Umbrel App Store → Community App
Stores**:

```text
https://github.com/dnbarclay/umbrel-tak-app-store
```

## Install and connect

1. Install **OpenTAKServer** from the TAK Apps community store.
2. Allow 1–2 minutes for first-run initialization.
3. Open the dashboard tile and create the first administrator account.
4. Create a user or client data package in OpenTAKServer.
5. Connect ATAK, WinTAK, or iTAK to your Umbrel hostname/IP:
   - Encrypted CoT stream: TCP `8089`
   - Certificate enrollment: TCP `8446`

For remote field clients, use a VPN when possible. If using router port
forwarding, forward only TCP 8089 and 8446 to the Umbrel. Do not expose database
or message-broker services.

## Data and backups

Persistent data lives beneath Umbrel's application data directory:

- `data/ots` — configuration, certificate authority, client certificates, logs
- `data/postgres` — application database
- `data/rabbitmq` — queued messages and broker state

Back up and restore all three directories together. Losing `data/ots` loses the
certificate authority and requires clients to be provisioned again.

## Ports

| Port | Exposure | Purpose |
| --- | --- | --- |
| Umbrel-assigned web port | Umbrel proxy | Web dashboard |
| 8089/tcp | Host/LAN | Encrypted CoT streaming |
| 8446/tcp | Host/LAN | Client certificate enrollment |

## Upstream projects

- https://github.com/brian7704/OpenTAKServer
- https://github.com/brian7704/OpenTAKServer-UI
- https://github.com/9M2PJU/9M2PJU-OpenTAKServer-Docker

The OpenTAKServer software and referenced Docker packaging are GPL-3.0 licensed.
