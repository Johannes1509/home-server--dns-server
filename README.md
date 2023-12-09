# ansible-pihole (für DNSPI)

WICHTIG: Raspberry Pi OS (Legacy) Debian Bullseye mit desktop env und security updates nehmen

### Wie benutze ich das Repo?

### Voraussetzungen
- Per Raspberry Pi Imager Pi-SD-Karte bespielen:
  - OS: Raspberry Pi OS (Legacy) Debian Bullseye mit Desktop env und Security updates
  - SSH aktivieren (in Pi Imager Einstellungen)
  - WLAN aktivieren (in Pi Imager Einstellungen)
  - Hostname `dnspi` setzen (in Pi Imager Einstellungen)
- PI booten lassen
- Wichtig: PI ist in Fritzbox Netzwerk sichtbar (Checken)
- Pi in Fritzbox
- Variablen in [inventory.yaml](inventory.yaml) pflegen

#### Playbook ausrollen
- Playbook ausrollen mit `ansible-playbook -i inventory.yaml setup_pi.yml` 
Hinweis: Wenn die Meldung kommt ala "Hostkey umbekannt" einmal kurz per ssh auf dnspi schalten und host-fingerprint speichern