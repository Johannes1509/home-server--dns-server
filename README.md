# ansible-pihole (für DNS-Pi)

## Wie benutze ich das Repo?
Es gibt zwei Modi, wie das Repo genutzt werden kann:
1. "Full Mode" füt die komplette Installation aus und setzt lokale DNS-Einträge
2. "Update DNS Entries" Setzt nur die lokalen DNS-Einträge neu


### 1. Full Mode
#### 1.1 Voraussetzungen
- Per Raspberry Pi Imager Pi-SD-Karte bespielen:
  - OS: Raspberry Pi OS (Legacy) Debian Bullseye mit Desktop env und Security updates
  - SSH aktivieren (in Pi Imager Einstellungen)
  - WLAN aktivieren (in Pi Imager Einstellungen)
  - Hostname `dnspi` setzen (in Pi Imager Einstellungen)
- PI booten lassen
- Wichtig: PI ist in Fritzbox Netzwerk sichtbar (Checken)
- Pi in Fritzbox als 
- Variablen in [inventory.yaml](inventory.yaml) pflegen
- Lokale DNS-Einträge in der [var/dns-entries](var/dns-entries) pflegen

#### 1.2 Playbook ausrollen
- Playbook ausrollen mit `ansible-playbook -i inventory.yaml setup_pi.yml` 
Hinweis: Wenn die Meldung kommt ala "Hostkey umbekannt" einmal kurz per ssh auf dnspi schalten und host-fingerprint speichern

#### 1.3 Nachbereitung
- Fritzbox konfigurieren wie [hier](https://docs.pi-hole.net/routers/fritzbox-de/#pi-hole-als-dns-server-via-dhcp-an-clients-verteilen-lan-seite) beschrieben
- Fritzbox konfigurieren: PI-IPv6 Adresse als DNS-Server hinterlegen (unter Heimnetz > Netzwerk > Netzwerkeinstellungen > IPv6-Einstellungen (weiter unten) > DNSv6-Server im Heimnetz) 
- Frotzbox konfigurieren: IPv4 + IPv6-Adresse des dnspis unter Internet > Zugangsdaten für DNS-Server eintragen


### 2. Update DNS Entries

#### 2.1 Voraussetzungen
- Lokale DNS-Einträge in der [var/dns-entries](var/dns-entries) pflegen

#### 2.2 Playbook ausrollen
- Playbook ausrollen mit `ansible-playbook -i inventory.yaml setup_pi.yml --tags "set_dns_entries"` 
Hinweis: Wenn die Meldung kommt ala "Hostkey unbekannt" einmal kurz per ssh auf dnspi schalten und host-fingerprint speichern