# Description

This is a small helper role that just opens ports in `iptables` firewall rules.

# Configuration

For a service running locally use:
```yaml
open_ports_default_comment: 'Local service X'
open_ports_list:
  - { port: 443,  protocol: 'tcp' }
  - { port: 8001, protocol: 'tcp', in_iface: 'tun0' }
  - { port: 9100, protocol: 'tcp', comment: 'Local service Y' }
  - { port: 9200, protocol: 'tcp', ipset: 'metrics.hq' }
```
For a docker service ports use:
```yaml
open_ports_default_comment: 'Docker service Y'
open_ports_default_action: 'insert'
open_ports_default_chain: 'DOCKER-USER'
open_ports_list:
  - { port: 8080, protocol: 'tcp' }
  - { port: 8080, protocol: 'udp' }
  - { port: 2220, protocol: 'tcp', state: 'absent' }
```
__WARNING__: If you are opening a Docker container port, you need to open the one __in__ the container, no the one mapped on the host.

Any variables starting with `open_ports_default_` can be overriden with a specific value in `open_ports_list`.
