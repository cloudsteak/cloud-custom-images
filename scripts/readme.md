# Teszt weboldal virtuálisgéphez

## Előfeltételek

- Ubuntu 20.04 vagy Ubuntu 22.04
- [Apache 2](apache-install.md)

## Parancsok

Feltételezzük, hogy az Apache 2 már telepítve van és fut. 

1. Root módra váltunk

```bash
sudo -i
```

2. Egy új fájlt hozunk létre, ami majd a szükséges web tartalmat létrehozza, ha elindul a gépünk

```bash
nano /usr/local/bin/mentor.sh
```

3. Másoljuk a fájlba a [mentor.sh](mentor.sh) fájl tartalmát

4. Mentsük el a fájlt az alábbi módon:

- CTRL + o
- CTRL + x

5. Állítsuk be a megfelelő jogosultságot a fájlon

```bash
chmod 744 /usr/local/bin/mentor.sh
```

6. Hozzunk létre egy új szolgáltatás fájlt a kis script-ünknek

```bash
nano /etc/systemd/system/mentor.service
```

7. Másoljuk a fájlba a [mentor.service](mentor.service) fájl tartalmát

8. Mentsük el a fájlt az alábbi módon:

- CTRL + o
- CTRL + x

9. Hozzuk létre a deamon-t is

```bash
cd /etc/systemd/system/
systemctl daemon-reload
```

10. Ellenőrizzük és indítsuk el

```bash
systemctl status mentor.service
systemctl restart mentor.service
systemctl status mentor.service
```