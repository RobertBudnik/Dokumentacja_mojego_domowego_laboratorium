# Homelab RACK 19"

Projekt budowy własnego, energooszczędnego laboratorium sieciowo-serwerowego w szafie RACK 19" (6U) w budżecie 2500 zł.

## Po co powstaje ten projekt?

Od dłuższego czasu interesuję się sieciami komputerowymi oraz tym, jak działa infrastruktura IT w praktyce. Zamiast ograniczać się wyłącznie do teorii czy symulatorów, postanowiłem zbudować fizyczne środowisko testowe w domu, na którym mogę swobodnie eksperymentować i popełniać błędy bez wpływu na resztę domowników.

Główne cele tego homelaba:

* **Praktyczna nauka sieci** — zabawa z segmentacją ruchu (VLAN 802.1Q na zarządzalnym switchu), izolacją urządzeń IoT od sieci głównej, routingiem, zaporą sieciową oraz tunelowaniem ruchu (WireGuard).
* **Wirtualizacja i konteneryzacja** — nauka administracji środowiskiem **Proxmox VE** oraz wdrażania usług w oparciu o **Docker** i kontenery LXC.
* **Niezależność (Self-Hosting)** — przeniesienie codziennych usług (prywatna chmura zdjęć, multimedia, lokalny DNS blokujący reklamy, automatyka domowa) na własny sprzęt zamiast korzystania z komercyjnych subskrypcji.
* **Kultura pracy i niski pobór mocy** — zbudowanie cichej, uporządkowanej szafy wiszącej na fabrycznie nowych podzespołach, która pobiera ~10–15 W w spoczynku i może pracować 24/7.

## Zawartość repozytorium

* **Specyfikacja i dobór sprzętu** *(folder w repozytorium)* — pełna lista wybranych komponentów (Beelink SER5 32GB, szafa Lanberg 6U, switch TP-Link TL-SG108E, UPS CyberPower) wraz z linkami i podziałem budżetu.
* **Kolejne etapy** — dokumentacja z fizycznego montażu szafy, zarabiania patch panelu, konfiguracji sieci VLAN oraz wdrożenia konkretnych usług na Proxmoxie.
