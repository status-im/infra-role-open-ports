# Description

This is a small helper role that just opens ports in `iptables` firewall rules.

# Configuration

For a service running locally use:
```yaml
open_ports_protocol: tcp
open_ports_comment: 'Local service X'
open_ports_list: [443]
```
For a docker service ports use:
```yaml
open_ports_protocol: tcp
open_ports_comment: 'Docker service Y'
open_ports_action: 'insert'
open_ports_chain: 'DOCKER-USER'
open_ports_list: [8080]
```
__WARNING__: If you are opening a Docker container port, you need to open the one __in__ the container, no the one mapped on the host.
