# Teszt weboldal + SQL kapcsolat virtuálisgéphez

## Előfeltételek

- Ubuntu 20.04

## Parancsok

### Webalkalmazás előkészítése

1. Root módra váltunk és lefrissítjük a szervert

```bash
sudo -i
```

```bash
apt update && apt upgrade -y
```


2. Web mappa létrehozása

```bash
mkdir -p /var/www
```

3. `.env` fájl létrehozása az adatkapcsolathoz

```bash
nano /var/www/.env
```

_.env tartalma_:

```.env
# .env file
PORT=80
DB_USER="adatgazda"
DB_PASSWORD="<SQL adatgazda jelszava>"
DB_SERVER="<SQL szerver neve>.database.windows.net"
DB_NAME="<SQL adatbázis neve>"
DB_PORT="1433"
```
_Oktatási példa:_
```
DB_SERVER="trn-azure-sql-01.database.windows.net"
DB_NAME="webshop"
```

Mentés: `CTRL + o` majd `CTRL + x`


### Háttérfolyamat (daemon) előkészítése

1. Egy új fájlt hozunk létre, ami majd a szükséges web tartalmat létrehozza, ha elindul a gépünk

```bash
nano /usr/local/bin/mentor-sql.sh
```

2. Másoljuk a fájlba a [mentor-sql.sh](mentor-sql.sh) fájl tartalmát

3. Mentsük el a fájlt az alábbi módon:

- CTRL + o
- CTRL + x

4. Állítsuk be a megfelelő jogosultságot a fájlon

```bash
chmod 744 /usr/local/bin/mentor-sql.sh
```

5. Hozzunk létre egy új szolgáltatás fájlt a kis script-ünknek

```bash
nano /etc/systemd/system/mentor-sql.service
```

6. Másoljuk a fájlba a [mentor-sql.service](mentor-sql.service) fájl tartalmát

7. Mentsük el a fájlt az alábbi módon:

- CTRL + o
- CTRL + x

8. Hozzuk létre a deamon-t is

```bash
cd /etc/systemd/system/
systemctl daemon-reload
systemctl enable mentor-sql.service
```

10. Ellenőrizzük és indítsuk el

```bash
systemctl status mentor-sql.service
systemctl restart mentor-sql.service
systemctl status mentor-sql.service
```



Nagyjából 30 másodperc múlva el is érhető az alkalmazásunk.
Innen már csak az van hátra, hogy ebből egy újrafelhasználható `VM Image`-t készítünk.
