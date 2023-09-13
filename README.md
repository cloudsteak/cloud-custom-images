# Egyedi képfájl készítése

Egyedi képfájl készítése a különböző felhő szolgáltatók virtuális gépeihez

Dokumentumok

- "Generalize": https://learn.microsoft.com/en-us/azure/virtual-machines/linux/create-upload-ubuntu
  - Legfontosabb:

```bash
sudo cat >> /etc/waagent.conf << EOF
# For Azure Linux agent version >= 2.2.45, this is the option to configure,
# enable, or disable the provisioning behavior of the Linux agent.
# Accepted values are auto (default), waagent, cloud-init, or disabled.
# A value of auto means that the agent will rely on cloud-init to handle
# provisioning if it is installed and enabled, which in this case it will.
Provisioning.Agent=auto
EOF
```

```bash
sudo cloud-init clean --logs --seed
sudo rm -rf /var/lib/cloud/
sudo systemctl stop walinuxagent.service
sudo rm -rf /var/lib/waagent/
sudo rm -f /var/log/waagent.log
```

``bash
sudo waagent -force -deprovision+user
sudo rm -f ~/.bash_history
sudo export HISTSIZE=0

```

Utána lépjünk ki a gépből és állítsuk le (Leállítva - felszabadítva)

- Pillanatkép: https://learn.microsoft.com/en-us/azure/virtual-machines/capture-image-portal
- Gelériához adás: https://learn.microsoft.com/en-us/azure/virtual-machines/image-version?tabs=portal%2Ccli2

## Weboldal előkészítés

[Teszt weboldal virtuálisgéphez](scripts/teszt-weboldal.md)

## Weboldal + SQL előkészítés

[Teszt weboldal + SQL kapcsolat virtuálisgéphez](scripts/teszt-weboldal-sql.md)
```
