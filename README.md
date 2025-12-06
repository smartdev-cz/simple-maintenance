# Maintenance 2025-12-06

## Prihlaseni na jumphost
* prihlasit se pres vzdalenou plochu na 33333
* zapnout VPN
* odkazy na dulezite weby jsou ve firefoxu

## Pro kazdy server ze seznamu:

* udelat snapshot pres DigitalOcean web
* spustit terminal
* prihlasit se pomoci SSH na vybrany server
```shell
ssh <nazev-serveru-z-excelu>
```
* prihlaseni jako root
```shell
sudo bash
```
* overit ze jde o Alpine Linux
```shell
cat /etc/alpine-release
```
musi vratit verzi, napr. `3.20.3`
**Pokud predchozi prikaz nevrati cislo pak nepokracovat**

* overeni volneho mista
```shell
df -h /
```
Use% musi byt 80% nebo mene.
**Pokud je vice nez 80% tak nepokracovat**

* aktualizace repozitaru 
```shell
mcedit /etc/apk/repositories
```
Zmenit `v3.xx` na `v3.22` a ulozit
	
* aktualizace balicku a systemu
```shell
apk update
apk upgrade
```

* overit ze docker bezi jak ma
```shell
docker ps -q | wc -l
```
**pokud vrati nulu pak preskocit dalsi krok**

* procisteni dockeru
```shell
docker system prune -af --volumes
```

* restartovat server po aktualizaci
```shell
reboot
```
zkontrolovat ze web bezi - nejpozdeji do 5 minut musi bezet jinak nahlasit
