# Description

This is a small helper role that just opens ports in NFTables firewall rules.

# Configuration

For a service running locally use:
```yaml
open_ports_nftables: true
open_ports_list:
  nginx:
    - { port: 443,  protocol: 'tcp' }
  service-x:
    - { port: 8001, protocol: 'tcp', iif: 'tun0' }
    - { port: 9100, protocol: 'tcp', comment: 'Protocol XYZ' }
    - { port: 9200, protocol: 'tcp', ipset: 'hq.metrics' }
    # It's possible to define raw rules in NFTables format.
    - 'tcp dport {3001, 3002} iif lo accept comment "Raw rule"'
```
