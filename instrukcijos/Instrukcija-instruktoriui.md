# Instrukcija instruktoriui

## Prisijungimas

Instruktorius prisijungia per **`/admin`** adresą. Matoma tik su jo komandomis ir scenarijais susijusi informacija.

---

## Scenarijų kūrimas

**Admin panelis → Scenarijai → Naujas scenarijus**

1. Įvesti **pavadinimą** lietuviškai ir angliškai
2. Įvesti **aprašymą / instrukcijas** žaidėjams (rodoma žaidėjui informaciniame puslapyje)
3. Pasirinkti, ar scenarijus **viešas** (matomas visiems) ar **ribotas** (tik priskirtoms komandoms)
4. Išsaugoti — sistema automatiškai sukuria konstantų ir parametrų rinkinį

---

## Scenarijaus konfigūracija

### Konstantos

**Scenarijai → Redaguoti → Konstantos**

Ekonominiai parametrai, kurie nesikeičia žaidimo metu:

- Žaliavų kainos (PULP, COAT tiekėjai A ir B)
- Defektų normos pagal tiekėją
- Pristatymo terminai (lead times)
- Sandėliavimo kaštai, darbo valandų normos, ir kt.

### Parametrai

**Scenarijai → Redaguoti → Parametrai**

- **Bazinė paklausa** — rinkos paklausos lygis
- **Sezoniškumas** kiekvienam mėnesiui M1–M6 (daugiklis)

---

## Komandų priskyrimas

**Scenarijai → Redaguoti → Komandos**

- Priskirti vieną ar kelias komandas prie scenarijaus
- Tik priskirtų komandų nariai matys šį scenarijų (jei jis nėra viešas)

> Instruktorius mato tik savo sukurtas ar jai priskirtas komandas ir tik savo žaidėjus (arba administratoriaus sukurtus).

---

## Žaidimų sesijų stebėjimas

**Admin panelis → Žaidimų sesijos**

Instruktorius mato savo scenarijų žaidimų sesijas:

- Žaidėjo vardas, bandymo numeris, statusas (aktyvus / pateiktas)
- Pateikimo data
- Kiekvienas bandymas turi tabs **M1–M6** su žaidėjo sprendimais ir apskaičiuotais rezultatais

---

## Dažni klausimai

**Ar galiu keisti konstantas po to, kai žaidėjai pradėjo žaisti?**
Galite, tačiau tai paveiks tik naujus skaičiavimus — jau išsaugoti rezultatai nepersiskaičiuoja.

**Kiek bandymų gali atlikti žaidėjas?**
Sistemoje nėra apribojimo — žaidėjas gali kurti naujus bandymus tiek kartų, kiek reikia.

**Kaip žaidėjas pateikia galutinį sprendimą?**
Žaidėjas turi užpildyti visus 6 mėnesių sprendimus ir paspausti mygtuką „Pateikti". Po pateikimo sesija tampa read-only.
