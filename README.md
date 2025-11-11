# Maintenance v1 (2025-11-11)

* udelat snapshot pres DigitalOcean web
* otevrit si web v prohlizeci a sledovat jestli jede
* prihlasit se pomoci SSH na vybrany server
```shell
ssh <nazev-serveru>
```
* overeni ze jde o Alpine Linux
```shell
cat /etc/alpine-release
```
vraci verzi Alpine Linuxu, napr. `3.20.3`.
Pokud predchozi prikaz nevrati cislo pak nepokracovat

* overeni volneho mista
```shell
df -h /
```
Use% musi byt 80% nebo mene. Pokud je vice tak nepokracovat

* aktualizace repozitaru 
```shell
sudo mcedit /etc/apk/repositories
```
Zmenit `v3.xx` na `v3.22` a ulozit
	
* aktualizace balicku
```shell
sudo apk update
```

* aktualizace systemu
```shell
sudo apk upgrade
```

* restart
```shell
sudo reboot
```
nejpozdeji do 5 minut musi web bezet

* prihlasit se zpet pres SSH
* overit ze docker bezi jak ma
```shell
docker ps -q | wc -l
```
pokud vrati nulu tak nepokracovat

* procisteni dockeru
	* nedelat u serveru ze skupiny OPS a INFRA
```shell
docker system prune -af --volumes
```
* overit ze web bezi jak ma
