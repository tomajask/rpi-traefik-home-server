# Troubleshooting

## read udp [::1]:43296->[::1]:53: read: connection refused
```bash
$ docker-compose up -d --build
Creating network "traefik_default" with the default driver
Creating volume "traefik_nextcloud" with default driver
Creating volume "traefik_db" with default driver
Pulling nextcloud-redis (redis:alpine)...
ERROR: Get https://registry-1.docker.io/v2/: dial tcp: lookup registry-1.docker.io on [::1]:53: read udp [::1]:43296->[::1]:53: read: connection refused
```
Solution:
```bash
systemctl restart systemd-resolved.service
```

## Error starting userland proxy: listen tcp 0.0.0.0:53: bind: address already in use

```bash
ERROR: for pihole  Cannot start service pihole: driver failed programming external connectivity on endpoint pihole (82cab4cdf3751e64cb6831b948a057ee34a02852f7461c35501b8bb98d65c022): Error starting userland proxy: listen tcp 0.0.0.0:53: bind: address already in use
ERROR: Encountered errors while bringing up the project.
```
Solution:
```bash
sudo systemctl stop systemd-resolved
sudo systemctl disable systemd-resolved
```
