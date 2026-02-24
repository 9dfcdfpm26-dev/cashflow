# cashflow
# CashFlow Tracker — Navodila za namestitev na telefon

## Kaj dobiš

Polno funkcionalno aplikacijo za sledenje stroškov z:
- ✅ **Dodajanje transakcij** (prihodki + odhodki) z zneskom, kategorijo, opombo, datumom, sliko računa
- ✅ **Swipe za brisanje** — podrsaj transakcijo v levo, pojavi se rdeč gumb "Delete"
- ✅ **Klikni za urejanje** — klikni na transakcijo, uredi ali izbriši (ikona koša)
- ✅ **Potrditev pred brisanjem** — vedno te vpraša "Are you sure?"
- ✅ **Ponavljajoči se vnosi** — dnevno, tedensko, mesečno, letno. Generira samo od danes naprej!
- ✅ **Offline delovanje** — aplikacija deluje brez interneta. Shranjuje v IndexedDB na tvojem telefonu
- ✅ **Mesečni pregled** — donut graf, kategorije, cash flow
- ✅ **Cilj varčevanja** — nastavi mesečni cilj, app ti pove koliko moraš še varčevat na dan
- ✅ **Export/Import** — varnostna kopija v JSON

---

## Datoteke v ZIP-u

```
cashflow-app.zip
├── index.html          ← Glavna aplikacija (vsa koda)
├── manifest.json       ← PWA manifest (ime, ikona, barve)
├── sw.js               ← Service Worker (offline podpora)
└── icons/
    ├── icon-192.png    ← Ikona 192x192
    ├── icon-512.png    ← Ikona 512x512
    └── apple-touch-icon.png ← Ikona za iPhone
```

---

## KORAK 1: Prenesi ZIP datoteko

Prenesi `cashflow-app.zip` iz Claude-a na svoj računalnik.

---

## KORAK 2: Razpakiraj ZIP

Razpakiraj ZIP datoteko. Dobiš mapo `cashflow-app` s 4 datotekami + `icons` mapo.

---

## KORAK 3: Naloži na brezplačen hosting

Aplikacija mora biti na URL-ju, da jo telefon prepozna kot PWA. Imaš 3 brezplačne opcije:

### Opcija A: GitHub Pages (priporočam — trajno brezplačno, zanesljivo)

1. **Pojdi na** [github.com](https://github.com) in se prijavi (ali ustvari račun — brezplačno)
2. **Klikni** zeleni gumb **"New"** (nov repository)
3. **Ime repozitorija:** `cashflow` (ali kar koli)
4. **Obkljukaj** "Add a README file"
5. **Klikni** "Create repository"
6. **V repozitoriju klikni** "Add file" → "Upload files"
7. **⚠️ POMEMBNO: Povleci VSEBINO mape, NE mape same!**
   Odpri mapo `cashflow-app` na računalniku in povleci te 4 stvari POSEBEJ:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - celotno mapo `icons/` (z vsemi 3 slikami)
   
   **NE povleci celotne mape `cashflow-app/`** — datoteke MORAJO biti v korenu (root-u) repozitorija!
   
   Po uploadu mora struktura v GitHub repozitoriju izgledati takole:
   ```
   cashflow/              ← repozitorij
   ├── README.md
   ├── index.html         ← TUKAJ v root-u
   ├── manifest.json      ← TUKAJ v root-u
   ├── sw.js              ← TUKAJ v root-u
   └── icons/
       ├── icon-192.png
       ├── icon-512.png
       └── apple-touch-icon.png
   ```
   
   **NAPAČNO** (to povzroči 404 error):
   ```
   cashflow/
   ├── README.md
   └── cashflow-app/      ← NAROBE! Podmapa!
       ├── index.html
       └── ...
   ```
   
8. **Klikni** "Commit changes"
9. **Pojdi v** Settings → Pages (v levem meniju)
10. **Pod "Source"** izberi: `Deploy from a branch`
11. **Pod "Branch"** izberi: `main`, folder: `/ (root)`
12. **Klikni** Save
13. **Počakaj 1-3 minute.** Osveži stran. Pokaže se URL:
    ```
    https://TVOJUSERNAME.github.io/cashflow/
    ```
14. **Odpri ta URL v brskalniku na telefonu** — mora delovat!

**Če dobiš 404:**
- Preveri da je `index.html` RES v korenu repozitorija (ne v podmapi)
- Preveri da je Pages enabled (Settings → Pages)
- Počakaj 2-3 minute po vsakem commitu — GitHub potrebuje čas za deploy

### Opcija B: Netlify (drag & drop, zelo enostavno)

1. Pojdi na [app.netlify.com](https://app.netlify.com)
2. Prijavi se (brezplačno z GitHub ali emailom)
3. Na dashboardu spodaj vidiš "Deploy manually"
4. **Povleci celotno mapo** `cashflow-app` na to polje
5. Počakaj 10 sekund — dobiš URL kot `https://naključno-ime.netlify.app`
6. Odpri ta URL na telefonu

### Opcija C: Lokalni server (brez interneta, samo za doma)

Če imaš Python na računalniku:
```bash
cd pot/do/cashflow-app
python3 -m http.server 8080
```
Potem na telefonu (na istem WiFi) odpri: `http://IP-RACUNALNIKA:8080`

⚠️ Ta opcija deluje samo doma na WiFi. Za pravo offline izkušnjo uporabi Opcijo A ali B.

---

## KORAK 4: Namesti na telefon kot aplikacijo

### iPhone (Safari)

1. **Odpri URL** v **Safari** (NE v Chrome — PWA namestitev deluje samo v Safari na iPhonu)
2. Počakaj da se stran popolnoma naloži
3. **Pritisni ikono za deljenje** (kvadrat s puščico navzgor ⬆️) — na dnu ekrana
4. **Podrsi navzdol** v meniju in najdi **"Add to Home Screen"**
5. **Ime:** CashFlow (ali kar hočeš)
6. **Pritisni** "Add"
7. **Aplikacija se pojavi na domačem zaslonu** z zeleno ikono €

Ko jo odpreš, se odpre v polnem zaslonu — brez URL vrstice, brez Safari okvirja.
Izgleda in se obnaša kot prava aplikacija.

### Android (Chrome)

1. **Odpri URL** v **Chrome**
2. Počakaj da se stran popolnoma naloži
3. Chrome ti mogoče sam predlaga "Add to Home screen" — pritisni to
4. Če ne, **pritisni tri pike** (⋮) zgoraj desno
5. **Izberi** "Install app" ali "Add to Home screen"
6. **Potrdi** ime
7. **Aplikacija se pojavi v predalu aplikacij** kot prava app

---

## KORAK 5: Preveri offline delovanje

1. Odpri aplikacijo
2. Dodaj eno testno transakcijo (npr. €5 za Food & Drink)
3. **Vklopi letalski način** (Airplane mode)
4. Zapri aplikacijo
5. Znova odpri aplikacijo
6. ✅ Transakcija mora biti še vedno tam
7. Dodaj še eno transakcijo medtem ko si offline
8. ✅ Mora delovati normalno
9. Izklopi letalski način — podatki so varno shranjeni

---

## Kako deluje shramba

- **IndexedDB** — brskalniku vgrajena baza podatkov, shrani podatke lokalno na tvojem telefonu
- Deluje **offline** — vse se shrani takoj na telefon
- Podatki **preživijo** zaprtje aplikacije, restart telefona, itd.
- **Edini način izgube podatkov:** če izbrišeš podatke brskalnika ali odstraniš aplikacijo
- **Priporočam:** občasno naredi Export v Settings → izvozi JSON backup datoteko

---

## Kako deluje ponavljanje (recurring)

- Ko narediš transakcijo s ponavljanjem (npr. mesečno), se ustvari **predloga** (template)
- Predloga **ne generira** vnosov za nazaj — samo originalni vnos ostane
- Od **danes naprej** se avtomatsko generirajo novi vnosi na vsak ustrezen dan
- Če vneseš transakcijo za 1 leto nazaj z "monthly" — se vnese SAMO za tisti dan. Od danes naprej pa se vsak mesec na isti dan avtomatsko vnese nov vnos

### Brisanje recurring vnosov:

- **Brišeš en specifičen vnos** (npr. tistega izpred 6 mesecev): zbriše se SAMO ta en vnos. Vsi ostali generirani vnosi ostanejo. Prihodnji se še naprej generirajo.
- **Brišeš predlogo** (template): ustavi se generiranje PRIHODNJIH vnosov. Vsi dosedanji generirani vnosi OSTANEJO nedotaknjeni.
- **"Stop Future Recurring"** gumb: ko urejaš recurring vnos, imaš opcijo da ustaviš prihodnje generiranje brez da karkoli izbrišeš.

**Primer:**
1. 1. jan 2025 vneseš "Zavarovanje €50/mesec"
2. Do 1. jul 2025 se generira 6 vnosov (jan-jul)
3. Izbrišeš vnos za marec → samo marec se izbriše, ostali ostanejo
4. Ustaviš recurring → julijski vnos ostane, avg+ se ne generira več

---

## Pogosta vprašanja

**V: Ali lahko ljudje vidijo moje finančne podatke ker je repozitorij public?**
NE. Repozitorij vsebuje samo KODO aplikacije (HTML, CSS, JavaScript) — to je kot recept za torto. Vsi vidijo recept, nihče pa ne vidi tvojo torto. Tvoji finančni podatki se shranjujejo IZKLJUČNO lokalno na tvojem telefonu v IndexedDB brskalnika. Nihče drug jih ne more videti, niti GitHub. Če te kljub temu skrbi, lahko narediš repozitorij PRIVATE (Settings → Danger Zone → Change visibility). GitHub Pages deluje tudi s private repozitorijem brezplačno.

**V: Ali moram plačati za GitHub Pages / Netlify?**
Ne. Oba sta brezplačna za statične strani.

**V: Kaj če izgubim podatke?**
Redno izvažaj backup (Settings → Export). JSON datoteko shrani na Google Drive ali pošlji po emailu.

**V: Ali lahko imam app na več napravah?**
Podatki so lokalni za vsako napravo posebej. Če hočeš sinhronizacijo, bi bilo treba dodati backend (to je naslednji korak, če želiš).

**V: Zakaj ne naredim prave iOS/Android aplikacije?**
Lahko! Za to bi uporabil Capacitor — vzameš to isto kodo in jo zavijž v native shell. Ampak PWA je za osebno uporabo več kot dovolj — isti efekt, nič Apple/Google birokracije.

---

*Aplikacija je 100% tvoja. Koda teče na tvojem telefonu. Nihče drug nima dostopa do tvojih finančnih podatkov.*
