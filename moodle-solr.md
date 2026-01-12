# Odstraneni SOLR z Moodlu (2026-01-12)

## Prihlaseni na jumphost
* prihlasit se pres vzdalenou plochu na 33333

## Pro kazdy Moodle server ze seznamu:

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
* nalezeni spravne slozky
```shell
cd /data/<slozka>
```

* aktualizace compose.yaml 
```shell
mcedit compose.yaml
```
Pokud je v souboru sekce `solr` pak odstranit a ulozit

```yaml
  solr:
    image: solr:9.0.0
    restart: always
    command: ['solr-precreate', 'moodle']
    volumes:
      - ./data/solr:/var/solr/data:delegated
```
	
* spusteni nove konfigurace
```shell
docker-compose up -d
```
