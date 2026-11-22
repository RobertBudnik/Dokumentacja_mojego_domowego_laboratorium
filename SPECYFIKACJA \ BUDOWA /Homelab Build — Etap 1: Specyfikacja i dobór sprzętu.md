<div align="center">

# Homelab Build — Etap 1: Specyfikacja i dobór sprzętu

**Kompletna dokumentacja nowego zestawu w standardzie RACK 19" w budżecie 2500 zł**

![Budżet](https://img.shields.io/badge/Budżet-2500_PLN-2ea44f?style=flat-square)
![Standard](https://img.shields.io/badge/Standard-RACK_19%22_6U-0366d6?style=flat-square)
![Hypervisor](https://img.shields.io/badge/Hypervisor-Proxmox_VE-E57000?style=flat-square&logo=proxmox&logoColor=white)
![Status](https://img.shields.io/badge/Etap_1-Zakończony-success?style=flat-square)

*Dokumentacja budowy domowego laboratorium od zera. Ten etap opisuje architekturę sprzętową, założenia projektowe oraz ostateczną listę zakupową fabrycznie nowych podzespołów.*

</div>

---

## Spis treści
- [Założenia projektowe](#założenia-projektowe)
- [Architektura zestawu (RACK 6U)](#architektura-zestawu-rack-6u)
- [1. Serce zestawu — Wybrany Mini PC (1350 zł)](#1-serce-zestawu--wybrany-mini-pc-1350-zł)
- [2. Szafa RACK 19" i osprzęt montażowy (520 zł)](#2-szafa-rack-19-i-osprzęt-montażowy-520-zł)
- [3. Sieć i zasilanie awaryjne (530 zł)](#3-sieć-i-zasilanie-awaryjne-530-zł)
- [Podsumowanie budżetu i pełna lista linków](#podsumowanie-budżetu-i-pełna-lista-linków)
- [Planowany stos technologiczny (Software)](#planowany-stos-technologiczny-software)

---

## Założenia projektowe

Projekt powstał z myślą o uzyskaniu maksymalnej wydajności w wirtualizacji przy zachowaniu niskiego poboru energii i pełnej kulturze pracy w warunkach domowych.

* **Tylko fabrycznie nowy sprzęt** — wszystkie komponenty pochodzą z oficjalnej dystrybucji i posiadają pełną gwarancję producenta.
* **Pełnowymiarowy standard RACK 19"** — wisząca szafa o głębokości `450 mm` gwarantuje wygodny montaż osprzętu oraz zapas miejsca na przyszłą rozbudowę.
* **Energooszczędność 24/7** — priorytetem był niski pobór mocy w spoczynku (`10–15 W`) oraz pasywne lub niemal bezgłośne chłodzenie.
* **Gotowość na wirtualizację** — baza sprzętowa wyposażona w `32 GB RAM` na start, pozwalająca na swobodne uruchamianie maszyn wirtualnych i kontenerów w **Proxmox VE**.

---

## Architektura zestawu (RACK 6U)

Rozmieszczenie poszczególnych komponentów wewnątrz wiszącej szafy teletechnicznej:

```text
┌─────────────────────────────────────────────────────────┐
│                  SZAFA RACK 19" (6U)                    │
│                 Lanberg WF01-6406-10B                   │
├─────────────────────────────────────────────────────────┤
│ [1U] Patch Panel 24-port Cat.6 (Lanberg PPU6-1024-B)    │
│ [2U] Półka stała 19" ──► Beelink SER5 32GB + Switch 8p  │
│ [3U] Wolna przestrzeń wentylacyjna / rozbudowa          │
│ [4U] Wolna przestrzeń / organizacja kabli               │
│ [5U] Listwa zasilająca PDU 7x Schuko (Lanberg)          │
│ [6U] Dno szafy ────────► Zasilacz awaryjny UPS 650VA    │
└─────────────────────────────────────────────────────────┘
```

---

## 1. Serce zestawu — Wybrany Mini PC (`1350 zł`)

Zamiast sprzętu poleasingowego padł wybór na fabrycznie nową jednostkę **[Beelink SER5 (AMD Ryzen 5 / 32 GB RAM)](https://www.morele.net/komputer-beelink-beelink-mini-komputer-pc-ser5-z-amd-ryzen-5-5500u-32g-15595910/)**. Kompaktowa obudowa bez problemu mieści się na półce RACK obok switcha, a procesor z serii Ryzen 5 zapewnia świetny stosunek wydajności wielowątkowej do poboru prądu.

| Parametr | Wybrana konfiguracja | Uwagi techniczne |
| :--- | :--- | :--- |
| **Wybrany model** | **[Beelink SER5 32GB](https://www.morele.net/komputer-beelink-beelink-mini-komputer-pc-ser5-z-amd-ryzen-5-5500u-32g-15595910/)** | Fabrycznie nowy, pełen komplet (zasilacz + uchwyt VESA) |
| **Procesor** | `AMD Ryzen 5` (6 rdzeni / 12 wątków) | Wysoka kultura pracy i bardzo dobra wydajność pod Proxmox VE |
| **Pamięć RAM** | `32 GB DDR4 SO-DIMM` | Konfiguracja Dual Channel `2x16 GB` (możliwość rozbudowy do 64 GB) |
| **Dysk główny** | `1 TB SSD M.2 NVMe PCIe` | Przestrzeń na system, obrazy ISO, maszyny wirtualne oraz kontenery |
| **Rozbudowa dysków** | Wolna zatoka `2.5" SATA` | Możliwość dołożenia drugiego dysku w przyszłości |
| **Pobór mocy (Idle)** | `~10–15 W` | Minimalne koszty utrzymania przy pracy ciągłej 24/7 |

<details>
<summary><b>Bezpośrednie linki do ofert (Mini PC)</b></summary>
<br>

* **Wybrany model:** [Beelink Mini PC SER5 (AMD Ryzen 5 / 32GB RAM) — Morele.net](https://www.morele.net/komputer-beelink-beelink-mini-komputer-pc-ser5-z-amd-ryzen-5-5500u-32g-15595910/)
* **Alternatywny wariant / porównanie cen:** [Beelink Mini PC SER5 — Ceneo.pl](https://www.ceneo.pl/168468743)

</details>

---

## 2. Szafa RACK 19" i osprzęt montażowy (`520 zł`)

Podstawą całej konstrukcji jest wisząca szafa **[Lanberg WF01-6406-10B](https://proline.pl/szafa-instalacyjna-rack-wiszaca-19-cali-6u-600x450-czarna-flat-pack-lanberg-wf01-6406-10b-p1169470)** o głębokości **450 mm**. Taka głębokość pozwala na bezproblemowe zmieszczenie na dolnej płycie zasilacza awaryjnego UPS, a na półce obok serwera – przełącznika sieciowego.

| Element | Wybrany model (kliknij, aby otworzyć) | Przeznaczenie | Koszt |
| :--- | :--- | :--- | :---: |
| **Szafa wisząca 19"** | **[Lanberg WF01-6406-10B (6U, 600x450 mm, czarna)](https://proline.pl/szafa-instalacyjna-rack-wiszaca-19-cali-6u-600x450-czarna-flat-pack-lanberg-wf01-6406-10b-p1169470)** | Główna obudowa mieszcząca całą infrastrukturę | **290 zł** |
| **Półka stała 19"** | **[Lanberg AK-1001-B (1U, gł. 250 mm, stalowa)](https://www.x-kom.pl/p/507387-akcesorium-do-szafy-rack-lanberg-polka-do-szaf-wiszacych-19-450mm-1u-czarna.html)** | Podstawa pod Mini PC, zasilacz oraz switch | **50 zł** |
| **Listwa zasilająca (PDU)** | **[Lanberg PDU-07E-0200-BK (1U, 7 gniazd z wyłącznikiem)](https://www.ceneo.pl/126833493)** | Bezpieczna dystrybucja zasilania wewnątrz szafy | **85 zł** |
| **Patch panel** | **[Lanberg PPU6-1024-B (1U, 24 porty Cat.6, czarny)](https://www.ceneo.pl/47635225)** | Estetyczne zakończenie okablowania strukturalnego | **95 zł** |

<details>
<summary><b>Porównanie cen i alternatywne sklepy (Szafa i osprzęt)</b></summary>
<br>

* **Szafa Lanberg WF01-6406-10B:** [Proline.pl](https://proline.pl/szafa-instalacyjna-rack-wiszaca-19-cali-6u-600x450-czarna-flat-pack-lanberg-wf01-6406-10b-p1169470) | [Ceneo.pl](https://www.ceneo.pl/43083972)
* **Półka stała Lanberg AK-1001-B:** [x-kom.pl](https://www.x-kom.pl/p/507387-akcesorium-do-szafy-rack-lanberg-polka-do-szaf-wiszacych-19-450mm-1u-czarna.html) | [Ceneo.pl](https://www.ceneo.pl/43084036)
* **Listwa zasilająca Lanberg PDU 7x Schuko:** [Ceneo.pl (PDU-07E-0200-BK)](https://www.ceneo.pl/126833493) | [Ceneo.pl (wersja PRO)](https://www.ceneo.pl/124505991)
* **Patch panel Lanberg PPU6-1024-B:** [Ceneo.pl](https://www.ceneo.pl/47635225)

</details>

---

## 3. Sieć i zasilanie awaryjne (`530 zł`)

### Przełącznik zarządzalny i okablowanie (`180 zł`)
* **Wybrany Switch Smart/Managed:** **[TP-Link TL-SG108E](https://www.eltrox.pl/p/8104-switch-tp-link-tl-sg108e)** (**130 zł**) — 8 portów Gigabit Ethernet (`10/100/1000 Mb/s`), solidna metalowa obudowa, pełna obsługa **VLAN 802.1Q** (separacja sieci IoT, serwerów i gości) oraz całkowicie bezwentylatorowa (pasywna) konstrukcja.
* **Wybrane Patchcordy krosowe:** Zestaw krótkich przewodów **Lanberg UTP Cat.6** o długości **[0.25 m](https://www.ceneo.pl/95459323)** oraz **[0.5 m](https://www.ceneo.pl/87416361)** (**50 zł** za komplet) do schludnego spięcia portów między patch panelem, switchem a serwerem.

### Zasilanie awaryjne UPS (`350 zł`)
* **Wybrany model UPS:** **[CyberPower UT650EG-FR (650VA / 360W)](https://www.x-kom.pl/p/507248-zasilacz-awaryjny-ups-cyberpower-ups-ut650eg-fr-650va-360w-3xpl-avr.html)** — wyposażony w 3 polskie gniazda z bolcem, układ **AVR** (automatyczna regulacja napięcia) oraz zabezpieczenie linii Ethernet, pozwalający na podtrzymanie pracy serwera i routera przy zanikach prądu.

<details>
<summary><b>Porównanie cen i alternatywne sklepy (Sieć i UPS)</b></summary>
<br>

* **Switch TP-Link TL-SG108E:** [Eltrox.pl](https://www.eltrox.pl/p/8104-switch-tp-link-tl-sg108e) | [Ceneo.pl](https://www.ceneo.pl/30586918)
* **Patchcordy Lanberg Cat.6:** [Wersja 0.25 m (Ceneo)](https://www.ceneo.pl/95459323) | [Wersja 0.5 m (Ceneo)](https://www.ceneo.pl/87416361)
* **UPS CyberPower UT650EG-FR:** [x-kom.pl](https://www.x-kom.pl/p/507248-zasilacz-awaryjny-ups-cyberpower-ups-ut650eg-fr-650va-360w-3xpl-avr.html) | [Ceneo.pl](https://www.ceneo.pl/72925273)

</details>

---

## Podsumowanie budżetu i pełna lista linków

| Kategoria | Wybrany podzespół (bezpośredni link) | Koszt | Udział |
| :--- | :--- | :---: | :---: |
| **Serwer** | [Beelink SER5 Mini PC (Ryzen 5 / 32 GB RAM / 1 TB)](https://www.morele.net/komputer-beelink-beelink-mini-komputer-pc-ser5-z-amd-ryzen-5-5500u-32g-15595910/) | **1350 zł** | `54.0%` |
| **Szafa RACK** | [Lanberg WF01-6406-10B 19" 6U 600x450](https://proline.pl/szafa-instalacyjna-rack-wiszaca-19-cali-6u-600x450-czarna-flat-pack-lanberg-wf01-6406-10b-p1169470) | **290 zł** | `11.6%` |
| **Półka RACK** | [Lanberg AK-1001-B 19" 1U (gł. 250 mm)](https://www.x-kom.pl/p/507387-akcesorium-do-szafy-rack-lanberg-polka-do-szaf-wiszacych-19-450mm-1u-czarna.html) | **50 zł** | `2.0%` |
| **Listwa PDU** | [Lanberg PDU-07E-0200-BK 19" 1U (7 gniazd)](https://www.ceneo.pl/126833493) | **85 zł** | `3.4%` |
| **Patch panel** | [Lanberg PPU6-1024-B 19" 1U 24-port Cat.6](https://www.ceneo.pl/47635225) | **95 zł** | `3.8%` |
| **Zasilanie UPS** | [CyberPower UT650EG-FR (650VA / 360W)](https://www.x-kom.pl/p/507248-zasilacz-awaryjny-ups-cyberpower-ups-ut650eg-fr-650va-360w-3xpl-avr.html) | **350 zł** | `14.0%` |
| **Switch** | [TP-Link TL-SG108E (8x 1GbE, Smart/VLAN)](https://www.eltrox.pl/p/8104-switch-tp-link-tl-sg108e) | **130 zł** | `5.2%` |
| **Okablowanie** | Patchcordy Lanberg Cat.6 ([0.25 m](https://www.ceneo.pl/95459323) + [0.5 m](https://www.ceneo.pl/87416361)) | **50 zł** | `2.0%` |
| **Rezerwa** | Śruby RACK M6 z koszyczkami, opaski rzepowe, wysyłki | **100 zł** | `4.0%` |
| **RAZEM** | **Kompletny, fabrycznie nowy zestaw** | **2500 zł** | **100%** |

---

## Planowany stos technologiczny (Software)

Po fizycznym złożeniu szafy w kolejnym etapie, na serwerze wdrożony zostanie następujący ekosystem usług:

> [!IMPORTANT]
> **Hypervisor:** **Proxmox VE** — otwartoźródłowa platforma wirtualizacji typu *bare-metal* do zarządzania maszynami wirtualnymi (KVM) oraz lekkimi kontenerami (LXC).

* **AdGuard Home / Pi-hole** — lokalny serwer DNS z filtrowaniem reklam i trackerów dla całej sieci domowej.
* **Home Assistant** — centralny hub automatyki domowej i integracji urządzeń IoT (w odseparowanej sieci VLAN).
* **Docker + Portainer** — środowisko kontenerowe obsługujące serwer multimediów (**Jellyfin** + stos `*arr`) oraz prywatną chmurę zdjęć (**Immich**).
* **WireGuard / Tailscale** — bezpieczny, szyfrowany tunel VPN zapewniający zdalny dostęp do zasobów homelaba spoza domu.
* **NUT (Network UPS Tools)** — demon monitorujący stan baterii UPS-a CyberPower, inicjujący bezpieczne zamknięcie systemu przed całkowitym rozładowaniem akumulatora.

---

<div align="right">

**Następny krok:** `Etap 2 — Montaż szafy RACK, układanie okablowania i pierwsze uruchomienie`

</div>
