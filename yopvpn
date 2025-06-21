#!/bin/bash

# get IP value from input
# Usage: ./yopvpn.sh <IP_ADDRESS>
if [ -z "$1" ]; then
  echo "Usage: $0 <IP_ADDRESS>"
  exit 1
fi

IP="$1"

ssh root@$IP "apt update && apt upgrade -y"
ssh root@$IP "apt install -y docker.io docker-compose"
ssh root@$IP "systemctl enable --now docker"

ssh root@$IP "mkdir -p /opt/wireguard/config"

ssh root@$IP "docker run -d \
  --name=wireguard \
  --cap-add=NET_ADMIN \
  --cap-add=SYS_MODULE \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Etc/UTC \
  -e SERVERURL=$IP \
  -e SERVERPORT=51820 \
  -e PEERS=1 \
  -e PEERDNS=auto \
  -e INTERNAL_SUBNET=10.13.13.0 \
  -e ALLOWEDIPS=0.0.0.0/0 \
  -e LOG_CONFS=true \
  -p 51820:51820/udp \
  -v /opt/wireguard/config:/config \
  -v /lib/modules:/lib/modules \
  --sysctl="net.ipv4.conf.all.src_valid_mark=1" \
  --restart unless-stopped \
  lscr.io/linuxserver/wireguard:latest"

scp root@$IP:/opt/wireguard/config/peer1/peer1.conf ~/Downloads/peer1.conf
scp root@$IP:/opt/wireguard/config/peer1/peer1.png ~/Downloads/peer1.png