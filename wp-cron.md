# Aktualizace na WP cron (2025-12-16)

## Prihlaseni na jumphost
* prihlasit se pres vzdalenou plochu na 33333
* zapnout VPN
* odkazy na dulezite weby jsou ve firefoxu

## Pro kazdy WP server ze seznamu:

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
* nalezeni spravne slozky s WP
```shell
cd /data/<slozka>
```

* aktualizace compose.yaml 
```shell
mcedit compose.yaml
```
Do souboru doplnit mezi wordpress a database sekci viz nize a ulozit

```yaml
  cron:
    image: bash:latest
    restart: always
    command: bash -c "while true; do echo cron - $${INTERVAL}s; wget -qO- http://wordpress/wp-cron.php?cron; sleep $$INTERVAL; done"
    environment:
      INTERVAL: 300
```
	
* spusteni nove konfigurace
```shell
docker-compose up -d
```

* overweni ze vse funguje jak ma
```shell
docker-compose ps | grep -E "cron|STATUS"
```
ve sloupci status musi byt "UP a pocet vterin"... pockat alespon minutu poklud stale pobezi pak vse ok
