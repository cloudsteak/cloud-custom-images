# Apache 2.0 telepítése Ubuntu-ra

1. Frissítések ellenőrzése

```bash
sudo apt update
```

2. Apache telepítése

```bash
sudo apt install apache2 -y
```

3. Tűzfal ellenőrzése

```bash
sudo ufw status
```

*Megjegyzés: Inaktív legyen*

4. Apache futásának ellenőrzése

```bash
sudo systemctl status apache2
```

*Megjegyzés: `Active: active (running)` értéknek kell zöldel megjelennie

5. Apache induljon el, ha a gép elindul

```bash
sudo systemctl enable apache2
```

6. Nézzük meg az apache kezdőlapját

Böngészőben nyissuk meg az alábbiak valamelyikét:
- `http://<gép nyilvános IP címe>`
- `http://<gép nyilvános DNS neve>`