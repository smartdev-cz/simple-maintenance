# Maintenance v1 (2025-11-11)

* POUZE PRODUKCE - udelat snapshot pres DigitalOcean web
* prihlasit se pres vzdalenou plochu na 33333
* zapnout VPN
* spustit terminal
* prihlasit se pomoci SSH na vybrany server
```shell
ssh <nazev-serveru-z-excelu>
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
Use% musi byt 80% nebo mene. **Pokud je vice nez 80 tak nepokracovat**

* aktualizace repozitaru 
```shell
sudo mcedit /etc/apk/repositories
```
Zmenit `v3.xx` na `v3.22` a ulozit
	
* aktualizace balicku a systemu
```shell
sudo apk update
sudo apk upgrade
```

* restartovat server po aktualizaci
```shell
sudo reboot
```
zkontrolovat ze web bezi - nejpozdeji do 5 minut musi bezet

* prihlasit se zpet pres SSH
* overit ze docker bezi jak ma
```shell
docker ps -q | wc -l
```
**pokud vrati nulu tak nepokracovat**

* procisteni dockeru
	* **nedelat u serveru ze skupiny OPS a INFRA**
```shell
docker system prune -af --volumes
```
* overit ze web bezi jak ma
