# Egyedi képfájl készítése

Egyedi képfájl készítése a különböző felhő szolgáltatók virtuális gépeihez

Dokumentumok

- "Generalize": https://learn.microsoft.com/en-us/azure/virtual-machines/linux/create-upload-ubuntu

Legfontosabb:

```bash
sudo cloud-init clean --logs --seed
sudo rm -rf /var/lib/cloud/
sudo systemctl stop walinuxagent.service
sudo rm -rf /var/lib/waagent/
sudo rm -f /var/log/waagent.log
```

```bash
sudo waagent -force -deprovision+user
sudo rm -f ~/.bash_history
sudo export HISTSIZE=0
```

Utána lépjünk ki a gépből és állítsuk le (Leállítva - felszabadítva)

- Virtuális gép képének létrehozása a portálon: https://learn.microsoft.com/hu-hu/azure/virtual-machines/capture-image-portal
- Gelériához adás: https://learn.microsoft.com/hu-hu/azure/virtual-machines/shared-image-galleries?tabs=azure-cli

## Weboldal előkészítés

[Teszt weboldal virtuálisgéphez](scripts/teszt-weboldal.md)

## Weboldal + SQL előkészítés

[Teszt weboldal + SQL kapcsolat virtuálisgéphez](scripts/teszt-weboldal-sql.md)
