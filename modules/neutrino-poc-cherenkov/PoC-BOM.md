# Neutrino PoC — Underwater Cherenkov Detector (Prasonisi)

> Reset z trybu "deck dla VC" na "BOM dla hackerów". Projekt na ~€5k materiałów + 6 miesięcy pracy zespołu, który już ma cashflow gdzie indziej.

## Kluczowy insight, który zmienia budżet

**Cherenkov w wodzie NIE wymaga scyntylatora.** Woda *jest* medium. Tylko detektory fotonów + ciemność + ciśnienie. Wykasowane €25k scyntylatora.

40 m głębokości = 5 bar — trywialne dla dowolnej obudowy. Wyrzucone Vitrovex za €5k.

---

## 5 modułów optycznych — elektronika

| Pozycja | Skąd | Cena |
|---------|------|------|
| 80× SiPM Onsemi MicroFJ-30035 (16/moduł) | LCSC / Mouser EU | ~€10–15/szt = **€1000** |
| 5× SiPM bias/amp PCB ([Flux.ai](https://www.flux.ai) AI-assisted → JLCPCB) | JLCPCB | **€150** |
| Komponenty bierne, op-ampy, ADC (AD9220 / LTC2245) | LCSC + retail PL | **€200** |
| 5× MCU STM32H743 albo ESP32-S3 | LCSC | **€50** |
| 5× FPGA Tang Nano 9K (pico-sec timing) | AliExpress | **€100** |
| TDC chip TDC7200 (jeśli MCU nie wystarcza) | Mouser | **€50** |

**Subtotal elektronika: ~€1,550**

## Obudowy ciśnieniowe (5 sztuk)

| Opcja | Cena |
|-------|------|
| **DIY** aluminium Ø160 mm × 250 mm CNC Wro + akrylowe okno + o-ringi NBR | **€80–150/szt** |
| Surplus Vitrovex z dekomisjonowanego oceanograficznego (eBay UK/DE) | €200–500/szt |
| **Najtaniej** PCV PN10 + zaślepki + okno akrylowe | **€30–50/szt** (test do ~6 bar) |

**Realnie: 5× DIY aluminium = €500–750**

> Hardbox **już buduje obudowy ciśnieniowe** do dronów — marginal cost ~zero.

## Złącza podwodne

| Opcja | Cena |
|-------|------|
| Subconn Micro nowe | €120–250/szt — **nie kupujcie** |
| Subconn używane (Ocean Solutions UK) | €30–60/szt |
| **DIY** PG29 + epoksyd 2K (Loctite EA 9492) | **€3–10/szt + 1h** |
| Cobra (AliExpress) | €15–30/szt |

PoC: 5× DIY + 2× kupione porządne = **€100–150**.

## Kabel tether

- 50 m hybrid power+Ethernet komercyjny: €25k — **idiotyczne**.
- CAT6 outdoor (€2/m) + 2×2.5mm² zasilanie (€1.5/m), zip-tie, opcjonalnie wąż PCV: **€250**
- Albo używany ROV umbilical z OLX/Allegro/eBay: **€100–300**

## Mooring i deployment

- Beton 30 kg odlany w Hardboxie: **€20**
- Lina yacht 8 mm × 50 m: **€50**
- Pływak + bojka: **€50**

**Subtotal: €120**

## Powierzchniowa platforma

- Skrzynia Peli-knockoff (Allegro): €50
- Akumulator 12 V 100 Ah AGM/LiFePO4: €150–300
- Inwerter/DC-DC: €30
- Huawei LTE + antena: €80
- Switch + Raspberry Pi 5 edge gateway: €100

**Subtotal: €450**

## Software / DAQ

- Hetzner CCX22 (4 vCPU, 16 GB, 200 GB): **€13/mies**
- InfluxDB / TimescaleDB self-hosted: €0
- Grafana + PyTorch/JAX pipeline: €0
- uBlox NEO-M8T GPS-PPS (subnanosec timing, NO atomic clock needed): **€40**

**Subtotal 6 mies: ~€100**

## Wyjazdy Prasonisi

Lecicie i tak na testy dronów. Marginal: bagaż + 2 dni × 3 osoby × €100 = **€600 × 2 trips = €1,200**.

---

## REALNY TOTAL: ~€4,500–6,000

| Kategoria | Koszt |
|-----------|-------|
| Elektronika | €1,550 |
| Obudowy (marginal ~0 z Hardbox leverage) | €0–500 |
| Złącza | €150 |
| Tether | €250 |
| Mooring | €120 |
| Surface platform | €450 |
| Software/infra | €100 |
| Wyjazdy marginalne | €1,200 |
| Bufor 20% | €750 |
| **Razem** | **~€4,500–5,500** |

---

## Plan zakupów — kolejność (lead-time critical)

### Tydzień 1
- **LCSC**: 100× SiPM zapas, bias R, kondensatory, op-ampy, MCU, FPGA. Lead 10–14 dni. ~€800.
- **JLCPCB**: pierwszy obrót front-end PCB (Adam projektuje w weekend w **[Flux.ai](https://www.flux.ai)** — AI Copilot generuje schemat, Parts AI dobiera substytuty, eksport Gerber+BOM+CPL prosto do JLCPCB). 5 płytek + SMD pasywne: €50–100, lead 7–10 dni.
- **AliExpress**: Tang Nano, GPS, akcesoria. Lead 14–21 dni. ~€150.

### Tydzień 2
- **Mouser EU**: krytyczne komponenty jeśli LCSC nie ma na stanie.
- **Allegro/OLX**: codzienne sprawdzanie używanych obudów, kabli, akumulatorów, anten.
- **eBay UK/DE**: filter "scientific surplus / vitrovex / subconn / ROV umbilical".
- **CNC Wrocław**: zamówienie 5× cylindrów Al. Lead 2–3 tygodnie.

### Tydzień 3–4
- Akrylowe okna (lokalna plexi Wro)
- O-ringi NBR komplet €20
- Marine line + mooring hardware

### Tydzień 5+
- Druga iteracja po pierwszych testach in-air.

---

## Triki obniżające budżet

1. **SiPM jako bare die z LCSC**, nie spakowane — różnica 5×. Onsemi C-Series SMD ~$3–8/szt CN.
2. **Beton C30/37 odlewany w Hardboxie**, forma z kartonu — Kamil zna.
3. **PCV PN10 do 6 bar**, sklep hydrauliczny, klejone PCV cement, test pneumatyczny w basenie.
4. **Wynajem komory ciśnieniowej UMW/PW Wro** — taniej niż jednorazowa zalewa złego designu.
5. **PPS z GPS jest ZA DARMO** — uBlox €30, sub-ns jitter. **NO atomic clock, NO White Rabbit.**
6. **Doktorant fizyki cząstek (NCBJ)** zamiast konsultanta:
   - Współautorstwo na preprint
   - Tydzień w Prasonisi (sierpień, sponsorowane nurkowanie)
   - 5–10k EUR za 6 miesięcy "po godzinach"
   - Możliwa pełna etatówka po PhD
7. **Meissner za free** — co-founder z equity, nie konsultant na fakturę.
8. **Hetzner CCX22 zamiast AWS** — 1/8 ceny.
9. **AGM z FAS / OLX-used EV battery** zamiast LiFePO4. Cięższe, ale na boi nieważne.
10. **Hardbox lab marginal cost zero** — oscyloskop, lutownice, multimetry, druk 3D — już macie.

---

## Czego NIE kupujemy

| ❌ Nie kupujemy | ✅ Zamiast |
|---|---|
| Vitrovex sfera (€5k) | DIY aluminium €100 |
| Hamamatsu R7081 PMT (€500) | Onsemi SiPM €15 |
| Subconn nowe (€250) | DIY epoxy potting / Cobra |
| White Rabbit master clock (€20k) | uBlox PPS €30 |
| Komercyjne DAQ (€10k) | STM32 + FPGA + custom firmware |
| Płatny konsultant fizyk (€25k) | Doktorant za współautorstwo |
| Stratos Industries housings (€2k/szt) | Wasz własny proces (Hardbox) |

---

## Pitch dla VC

NIE: *"Daj nam €100k na PoC."*

TAK:
> **"Zbudowaliśmy działający podwodny detektor neutrin za 5 tysięcy euro. Wykryliśmy miony w Prasonisi. Mamy Meissnera w cap table. Teraz dajcie €2M, żebyśmy zrobili to w 100 modułach i podpisali kontrakt z KM3NeT."**

Capital efficiency + scrappiness + execution speed. VC kupują dokładnie to.

---

## Następny krok jutro rano

1. **Adam** — [Flux.ai](https://www.flux.ai) design front-end PCB (weekend, ~1–2 dni z AI Copilot vs 3–4 w KiCad)
2. **Maksym** — Hetzner, repo, podstawowy DAQ stack
3. **Kamil** — dzwoni do warsztatów CNC Wro + szuka surplus na OLX/eBay
4. **Meissner** — 4h science case session w przyszłym tygodniu

## Milestones

- Pierwsza dostawa LCSC → **tydzień 2**
- Pierwszy działający SiPM-kanał na stole → **tydzień 3**
- Pierwszy mion in-air → **tydzień 5**
- Pierwszy mion w Prasonisi → **tydzień 12**

Reszta to lutowanie i listing latania.
