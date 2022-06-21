
# Workadventure Open Source Virtual Space

Trying to deploy open source virtual space on google cloud platform compute engine.


## Tech Stack

- Workadventure
- Jitsi
- Docker Compose
- Nginx Reverse Proxy
- Tiled 32x32 Map Editor


## Installation

Install Workadventure

```bash
sudo apt update && sudo apt upgrade -y
sudo apt-get install docker docker-compose
sudo -i
cd /opt
git clone https://github.com/thecodingmachine/workadventure.git
cd /workadventure
nano .env
rm docker-compose.yaml
nano docker-compose.yaml
docker-compose up -d
```

Install Jitsi

```bash
sudo apt update && sudo apt upgrade -y
sudo -i
hostnamectl set-hostname meet.matthewbd.my.id
hostname
nano /etc/hosts
127.0.0.1	meet.matthewbd.my.id	

wget https://download.jitsi.org/jitsi-key.gpg.key
apt-key add jitsi-key.gpg.key
nano /etc/apt/sources.list.d/jitsi-stable.list

deb https://download.jitsi.org stable/	

apt update
apt install jitsi-meet

meet.matthewbd.my.id
Generate self-signed

snap install --classic certbot
ln -s /snap/bin/certbot /usr/bin/certbot
/usr/share/jitsi-meet/scripts/install-letsencrypt-cert.sh

brandondani33@gmail.com

setting butuh auth untuk ruang

nano /etc/prosody/conf.avail/meet.matthewbd.my.id.cfg.lua

authentication = "anonymous" -> authentication = "internal_plain"

baris paling bawah ->
VirtualHost "guest.meet.matthewbd.my.id" 
	authentication = "anonymous" 
	c2s_require_encryption = false	

nano /etc/jitsi/meet/meet.matthewbd.my.id-config.js

uncomment -> // anonymousdomain: 'guest.example.com',	-> anonymousdomain: 'guest.meet.matthewbd.my.id',

nano /etc/jitsi/jicofo/sip-communicator.properties

org.jitsi.jicofo.auth.URL=XMPP:meet.matthewbd.my.id

prosodyctl register brandon meet.matthewbd.my.id popsila2016
systemctl restart prosody
systemctl restart jicofo
systemctl restart jitsi-videobridge2
```