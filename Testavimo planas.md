# Res Matrica – Testavimo strategija

Išsami instruktorių ir žaidėjų testavimo instrukcija pagal sistemos funkcionalumą.

---

## INSTRUKTORIAI (Filament panelė `/admin` + app `/app`)

### 1. Prisijungimas

- [ ] Prisijungti su instruktoriaus el. paštu ir slaptažodžiu (`/login`)
- [ ] Patikrinti, kad nukreipia į `/admin` panelę
- [ ] Patikrinti, kad meniu matomi: Naudotojai, Komandos, Scenarijai, Žaidimų sesijos
- [ ] Patikrinti, kad **nematomi**: Rolės, Globalūs konstantai, Globalūs parametrai

---

### 2. Naudotojų valdymas

#### 2a. Naudotojo kūrimas rankiniu būdu

- [ ] Spausti **Naudotojai → Sukurti**
- [ ] Įvesti vardą, el. paštą, slaptažodį
- [ ] Priskirti rolę `gamer`
- [ ] Priskirti grupę (pvz. „A grupė")
- [ ] Priskirti komandą (pirmiau sukurti komandą)
- [ ] Išsaugoti → patikrinti, kad naudotojas atsiranda sąraše

#### 2b. Masinis naudotojų importas iš XLSX

- [ ] Spausti **Naudotojai → Importuoti**
- [ ] Įkelti XLSX failą su stulpeliais: `name`, `email`, `password`, `group`, `team` (komandos raktas)
- [ ] Patikrinti, kad visi importuoti naudotojai turi rolę `gamer`
- [ ] Patikrinti, kad teisingai priskirtos komandos pagal raktą
- [ ] Bandyti importuoti su trūkstamais laukais – patikrinti klaidų pranešimus

#### 2c. Naudotojo redagavimas

- [ ] Atidaryti naudotoją → pakeisti vardą, el. paštą
- [ ] Pakeisti grupę / komandą
- [ ] Išsaugoti → patikrinti pakeitimus sąraše

---

### 3. Komandų valdymas

- [ ] Spausti **Komandos → Sukurti**
- [ ] Įvesti pavadinimą, **unikalų raktą** (pvz. `team-a`), aprašymą
- [ ] Pridėti žaidėjus (filtruojami tik `gamer` rolės)
- [ ] Išsaugoti → patikrinti komandos rodymą sąraše su žaidėjų skaičiumi
- [ ] Redaguoti komandą: pridėti/pašalinti žaidėjus
- [ ] Patikrinti, kad tas pats žaidėjas gali būti keliose komandose

---

### 4. Scenarijų kūrimas ir konfigūracija

#### 4a. Naujo scenarijaus kūrimas

- [ ] Spausti **Scenarijai → Sukurti**
- [ ] Įvesti pavadinimą (LT) ir pavadinimą angliškai
- [ ] Pasirinkti tipą
- [ ] Išsaugoti → sistema nukreipia į redagavimo puslapį

#### 4b. Skirtukas „Bendroji informacija"

- [ ] Patikrinti, kad rodomi laukai: pavadinimas LT, pavadinimas EN, aprašymas, bandymų skaičius
- [ ] Nustatyti leidžiamų bandymų skaičių (pvz. 2)
- [ ] Išsaugoti → patikrinti, kad pakeitimai išliko

#### 4c. Skirtukas „Konstantos" (50+ laukų)

- [ ] Pakeisti kelis konstantų reikšmes (pvz. kainos elastingumas, defektų norma)
- [ ] Išsaugoti
- [ ] Perkrauti puslapį → patikrinti, kad reikšmės išliko
- [ ] Bandyti įvesti neteisingą reikšmę (pvz. tekstą vietoj skaičiaus) – tikėtina validacija

#### 4d. Skirtukas „Parametrai" (6 mėnesiai)

- [ ] Nustatyti bazinę paklausą kiekvienam mėnesiui (m1–m6)
- [ ] Nustatyti sezoniškumo koeficientus
- [ ] Išsaugoti → patikrinti reikšmes po perkrovimo

#### 4e. Skirtukas „Informacija"

- [ ] Įvesti turtingo teksto instrukciją LT kalba
- [ ] Įvesti instrukciją EN kalba
- [ ] Naudoti teksto formatavimą (paryškinimas, sąrašai)
- [ ] Išsaugoti → peržiūrėti žaidėjo puslapyje `/app/scenarios/{id}/info`

#### 4f. Skirtukas „Žaidėjai"

- [ ] Perjungti **Viešas scenarijai** → ON → patikrinti, kad žaidėjai mato be priskyrimo
- [ ] Perjungti **Viešas** → OFF
- [ ] Priskirti individualius žaidėjus
- [ ] Priskirti komandą → patikrinti, kad visi komandos nariai gauna prieigą
- [ ] Priskirti grupę → patikrinti grupės prieigą
- [ ] Pašalinti priskyrimus → patikrinti, kad žaidėjas nebemato scenarijaus

---

### 5. Žaidimų sesijų peržiūra

- [ ] Eiti į **Žaidimų sesijos** sąrašą
- [ ] Patikrinti, kad matomi tik savo scenarijų sesijos (ne kitų instruktorių)
- [ ] Atidaryti sesiją → peržiūrėti sprendimų skirtukus (m1–m6)
- [ ] Kiekvieno mėnesio skirtuke patikrinti:
  - Žaidėjo sprendimus (kaina, marketingas, gamyba, personalas ir kt.)
  - Rezultatų KPI rodiklius (žaidėjo versiją)
  - Vidinius skaičiavimus (instruktoriaus versiją)
- [ ] Patikrinti, kad sesija **neredaguojama** iš panelės

---

### 6. Instruktoriaus prieiga prie `/app`

- [ ] Eiti į `/app/scenarios` → patikrinti, kad matomi savo sukurti scenarijai
- [ ] Atidaryti scenarijų → peržiūrėti `/app/scenarios/{id}/info`
- [ ] Peržiūrėti žaidimų sąrašą `/app/scenarios/{id}/games`
- [ ] Eiti į `/app/reports` → patikrinti ataskaitų puslapį
- [ ] Eiti į `/app/settings` → pakeisti kalbą (LT/EN) → patikrinti, kad sąsaja persijungia

---

## ŽAIDĖJAI (App `/app`)

### 1. Prisijungimas

- [ ] Prisijungti su žaidėjo el. paštu ir slaptažodžiu
- [ ] Patikrinti, kad **nenukreipia** į `/admin` panelę
- [ ] Patikrinti, kad nukreipia į `/app/scenarios`
- [ ] Bandyti rankiniu būdu eiti į `/admin` → turi gauti 403 arba būti nukreiptas

---

### 2. Scenarijų sąrašas

- [ ] `/app/scenarios` rodo tik prieinamus scenarijus (viešus + priskirtus per vartotoją/komandą/grupę)
- [ ] Scenarijus, kuriam nėra prieigos, **nematomas**
- [ ] Spausti ant scenarijaus → sistema nukreipia į `/app/scenarios/{id}/info`

---

### 3. Scenarijaus informacija

- [ ] Puslapis rodo scenarijaus aprašymą ir instrukciją
- [ ] Perjungti kalbą nustatymuose (LT/EN) → patikrinti, kad tekstas keičiasi
- [ ] Patikrinti, kad rodomas leidžiamų bandymų skaičius
- [ ] Patikrinti esamų bandymų sąrašą (jei yra)

---

### 4. Naujos žaidimų sesijos pradėjimas

- [ ] Spausti „Pradėti naują bandymą"
- [ ] Sistema sukuria sesiją ir nukreipia į `/app/scenarios/{id}/games/{session}/dashboard`
- [ ] Patikrinti, kad rodoma 1 mėnesio apžvalga
- [ ] Jei bandymų limitas pasiektas → patikrinti, kad negalima pradėti naujo

---

### 5. Prietaisų skydelis (Dashboard)

- [ ] Rodomas dabartinio mėnesio numeris
- [ ] Rodoma informacija apie išsaugotus ir juodraščio sprendimus
- [ ] Navigacija į sprendimų puslapius veikia

---

### 6. Sprendimų įvedimas (7 kategorijos × 6 mėnesiai)

#### 6a. Kainodara (`/decisions/price-markup`)

- [ ] Įvesti kainos antkainį
- [ ] Tikrinti Alpine.js skaičiuoklę realiu laiku (rodo preliminarią kainą)
- [ ] Įvesti pastabas
- [ ] Spausti „Išsaugoti kaip juodraštį" → patikrinti, kad neperkraunant duomenys išlieka
- [ ] Spausti „Išsaugoti" → grįžti į puslapį ir patikrinti išsaugotą reikšmę

#### 6b. Marketingo biudžetas (`/decisions/marketing-budget`)

- [ ] Įvesti marketingo išlaidas
- [ ] Patikrinti skaičiuoklę
- [ ] Išsaugoti → patikrinti

#### 6c. Žaliavų įsigijimas (`/decisions/procurement`)

- [ ] Pasirinkti tiekėją (celiuliozė / danga)
- [ ] Įvesti kiekius
- [ ] Stebėti skaičiuoklės rodomus kaštus ir pristatymo terminus
- [ ] Išsaugoti → patikrinti

#### 6d. Gamybos pajėgumas (`/decisions/production-capacity`)

- [ ] Įvesti planuojamą gamybos kiekį
- [ ] Patikrinti skaičiuoklės rodomas ribas (personalo, energijos)
- [ ] Išsaugoti → patikrinti

#### 6e. Personalas (`/decisions/workforce`)

- [ ] Įvesti FTE (etatų) skaičių
- [ ] Stebėti samdymo/atleidimo kaštų skaičiuoklę
- [ ] Išsaugoti → patikrinti

#### 6f. Darbo užmokestis (`/decisions/gross-salary`)

- [ ] Įvesti vidutinį bruto atlyginimą
- [ ] Stebėti darbo kaštų skaičiuoklę
- [ ] Išsaugoti → patikrinti

#### 6g. Viršvalandžiai (`/decisions/overtime`)

- [ ] Įvesti viršvalandžių procentą
- [ ] Stebėti papildomų kaštų skaičiuoklę
- [ ] Išsaugoti → patikrinti

#### 6h. Juodraščio automatinis išsaugojimas

- [ ] Pradėti pildyti formą → nespausti „Išsaugoti"
- [ ] Pereiti į kitą puslapį → grįžti atgal
- [ ] Patikrinti, kad juodraščio reikšmės išliko (PHP sesija)

---

### 7. Rezultatų peržiūra

- [ ] Eiti į `/app/scenarios/{id}/games/{session}/results`
- [ ] Patikrinti, kad rodomi KPI rodikliai dabartiniam mėnesiui
- [ ] Jei dar nėra išsaugotų sprendimų → rodomas tuščias arba pradinės būsenos vaizdas
- [ ] Po išsaugojimo patikrinti konkrečius KPI:
  - Paklausa ir pardavimai
  - Pelnas ir pinigų srautai
  - Aptarnavimo lygis
  - Kokybė (defektų norma)
  - Atsargų lygiai
  - Žaliavų likučiai

---

### 8. Pereiti į kitą mėnesį

- [ ] Įsitikinti, kad visi 7 sprendimai išsaugoti 1 mėnesiui
- [ ] Pereiti į 2 mėnesio sprendimus
- [ ] Patikrinti, kad pradinės reikšmės atspindi 1 mėnesio pabaigos būseną (atsargos, personalas, kasos likutis)
- [ ] Pakartoti sprendimų įvedimą m2–m6

---

### 9. Sesijos pateikimas (submit)

- [ ] Įvesti visus 6 mėnesių sprendimus
- [ ] Spausti „Pateikti / Baigti" (`POST /submit`)
- [ ] Patikrinti, kad sesija užrakinama (nebegalima redaguoti)
- [ ] Patikrinti, kad sesija atsiranda istorijoje `/app/scenarios/{id}/games`
- [ ] Patikrinti, kad galima peržiūrėti pateiktos sesijos rezultatus

---

### 10. Kelių bandymų testavimas

- [ ] Jei leidžiami ≥2 bandymai: pradėti antrą sesiją → patikrinti, kad ji nepriklausoma nuo pirmos
- [ ] Jei leidžiamas tik 1 bandymas: patikrinti, kad „Pradėti naują" mygtukas yra išjungtas arba rodoma klaida
- [ ] Patikrinti, kad ankstesnių sesijų rezultatai išlieka

---

### 11. Nustatymai

- [ ] Eiti į `/app/settings`
- [ ] Pakeisti kalbą: LT → EN → patikrinti, kad visas `/app` sąsajos turinys perjungiamas
- [ ] Grąžinti LT
- [ ] Patikrinti kitas nustatymų parinktis (pranešimai, eksporto formatas)
- [ ] Išsaugoti → patikrinti, kad nustatymai išlieka po perkrovimo

---

## KRAŠTUTINIAI ATVEJAI (edge cases)

| Situacija | Ko tikėtis |
|-----------|-----------|
| Žaidėjas bando atidaryti `/admin` | 403 arba nukreipimas į login |
| Žaidėjas bando atidaryti kito žaidėjo sesiją | 403 arba 404 |
| Žaidėjas bando pateikti sesiją su neužpildytais sprendimais | Validacija arba numatytosios reikšmės |
| Instruktorius redaguoja scenarijų, kai žaidėjas jau yra aktyvus | Sprendimai perskaičiuojami pagal naujus konstantus? (patikrinti) |
| XLSX importas su dubliuotu el. paštu | Klaidos pranešimas |
| Bandymas prisijungti su negaliojančiais duomenimis | „Neteisingi prisijungimo duomenys" pranešimas |
| Kalbos keitimas sprendimų pildymo metu | Puslapis perkraunamas, juodraščio duomenys išlieka |

---

## TESTAVIMO TVARKA (rekomenduojama seka)

```
1. Adminas sukuria instruktorių
2. Adminas / Instruktorius sukuria žaidėjus (arba importuoja)
3. Instruktorius sukuria scenarijų su konstantomis ir parametrais
4. Instruktorius priskiria žaidėjus / komandas scenarijui
5. Žaidėjas prisijungia → mato scenarijų
6. Žaidėjas pradeda sesiją → įveda sprendimus (m1)
7. Žaidėjas peržiūri rezultatus (m1)
8. Žaidėjas kartoja m2–m6
9. Žaidėjas pateikia sesiją
10. Instruktorius peržiūri sesiją panelėje
```
