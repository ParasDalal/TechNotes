# Home Network

## VLANs

- 10.0.10.1/24 - (Default) Main
- 10.0.30.1/24 - IoT
- 10.0.50.1/24 - Guest

## Hosts

- [10.0.10.1](https://10.0.10.1/) - Router (root / BadlaiGayu5171)
- 10.0.10.10 - 19 - Access Points (SSH - Paras / BadlaiGayu5171)
- 10.0.10.20 - 29 - Printers
  - 10.0.10.21 - Brother LaserJet (admin / BadlaiGayu)
  - 10.0.10.22 - Epson
- 10.0.10.31-49 - Proxmox VMs (see below)
- 10.0.10.50 - MEDIA
- 10.0.10.51 - DESKTOP
- 10.0.10.52 - GAMEPC
- 10.0.10.51-99 - Other static computers/IPs
- 10.0.10.100 - 254 - DHCP

## VMs

- [10.0.10.30:8006](https://10.0.10.30:8006) / [pve.home.arpa:8006](https://pve.home.arpa:8006) - Proxmox Host (root / proxmox)
- [10.0.10.31:81](http://10.0.10.31:81) / [npm.home.arpa:81](http://npm.home.arpa:81) - Nginx Proxy Manager (admin@findpatterns.com / HANS6commando@bugeyed)
- [10.0.10.33:9000](http://10.0.10.33:9000) - Portainer Docker (admin / docker-contain)
  - SSH - root / docker-contain
  - SSH - apps / disable
  - [10.0.10.33:13378](http://10.0.10.33:13378) - AudiobookShelf (audio / listen)
- [10.0.10.40:8123](http://10.0.10.40:8123) / [home.findpatterns.com](https://home.findpatterns.com) - Home Assistant OS (dalal / smart-ghar)
- ubuntu - root/ubuntu
- Windows 10 - Dalal / MoreInfo1! 10.0.10.35

## NextDNS

```
cache-max-age 0s
detect-captive-portals false
max-inflight-requests 256
use-hosts true
debug false
control /var/run/nextdns.sock
report-client-info true
hardened-privacy false
listen localhost:53
mdns all
bogus-priv true
auto-activate true
setup-router true
profile f0:b3:ec:18:df:93=ea16d6
profile ac:f1:08:58:a8:bc=ea16d6
profile 00:04:4b:ba:d1:80=ea16d6
profile 00:06:78:42:15:dc=ea16d6
profile 58:fd:b1:d5:f3:7f=ea16d6
profile 10.0.30.0/24=d423a9
profile 2c72e7
log-queries false
cache-size 0
max-ttl 0s
discovery-dns
timeout 5s
```

## Unifi

Unifi Protect Recovery Code - 04UTaGRE3gHGOeIR4Sdb

## DDNS

Cloudflare API token - T3_3PW5RUq6SvxD9jFCGGnYxnkgGoeusxoc0niRn

## HomeAssistant

MQTT user: mqtt / yule7SCORIA-amicable

Z-Wave Security Keys

```
"S2_Unauthenticated": "B18F6C250B94D2318A626EA2B563B0A3"
"S2_Authenticated": "4E958C9A98531BCF9D441A3361E9B437"
"S2_AccessControl": "66C0361B3D06A1F03C1137B9F0C046B7"
"S0_Legacy": "D7F15A5698C3F8ED4B1AB0AEEA5773D3"
```

## Update

[Proxmox Helper Scripts](https://tteck.github.io/Proxmox/)

### Proxmox

```bash
# proxmox update
apt update && apt dist-upgrade

# on pve (hypervisor) console, run
bash -c "$(wget -qLO - https://github.com/tteck/Proxmox/raw/main/misc/update-lxcs.sh)"

# on npm container console, run
bash -c "$(wget -qLO - https://github.com/tteck/Proxmox/raw/main/misc/npm_update.sh)"
```

### Portainer

```bash
docker stop portainer
docker rm portainer

docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 --name=portainer --restart=always --pull=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ee:latest
```

### Additional Information for Portainer:

Teams: Dev

User: Paras/Unfazed4-Monetary



### Calibre 

Using images from the following:

https://docs.linuxserver.io/images/docker-calibre

https://docs.linuxserver.io/images/docker-calibre-web

For the calibre: user: abc pw: bookshelf

For calibre-web: user: admin pw: Scapegoat-Unnamed1

