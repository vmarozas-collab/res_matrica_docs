# Res Matrica – Sistemos funkcionalumas pagal roles

## ADMIN

**Tikslas:** Techninis sistemos valdymas ir paruošimas darbui.

| Sritis | Galimybės | Rezultatas |
|--------|-----------|------------|
| **Naudotojai** | Kurti, redaguoti, šalinti visus naudotojus; priskirti roles; importuoti iš XLSX | Sistemos dalyviai paruošti žaidimui |
| **Komandos** | Kurti komandas su raktais; priskirti žaidėjus | Žaidėjai sugrupuoti pagal grupes/komandas |
| **Scenarijai** | Kurti, redaguoti, šalinti visus scenarijus (ir svetimus) | Visi scenarijai valdomi centralizuotai |
| **Žaidimų sesijos** | Peržiūrėti visas sesijas, visus sprendimus ir KPI | Pilna žaidimo eigos kontrolė |
| **Globalūs konstantai** | Keisti sistemos numatytuosius konstantus | Visi nauji scenarijai paveldi šias reikšmes |
| **Globalūs parametrai** | Keisti numatytuosius mėnesinės paklausos parametrus | Bazinė žaidimo dinamika nustatyta |
| **Rolės ir leidimai** | Tik `super_admin`: tvarkyti Filament Shield roles | Prieigos kontrolė visai sistemai |

---

## INSTRUCTOR

**Tikslas:** Sukurti ir valdyti žaidimo scenarijų; stebėti žaidėjų eigą.

| Sritis | Galimybės | Rezultatas |
|--------|-----------|------------|
| **Savo scenarijai** | Kurti scenarijus; konfigūruoti 5 skirtukus | Paruoštas žaidimui unikalus scenarijus |
| **Konstantos** | ~90 laukų: kainos elastingumas, defektų normos, tiekėjų sąlygos, darbo kaštai, pradinio likučio reikšmės | Scenarijaus ekonominis modelis |
| **Parametrai** | Bazinė paklausa + sezoniškumas kiekvienam iš 6 mėnesių | Rinkos dinamika per žaidimo laikotarpį |
| **Informacija** | Turtingas tekstas (LT + EN) su žaidimo taisyklėmis | Žaidėjai mato instrukciją prieš žaidžiant |
| **Žaidėjų priskyrimas** | Viešas / konkretūs žaidėjai / komandos / grupės | Kontroliuoja, kas gali žaisti scenarijų |
| **Sesijų peržiūra** | Visų savo scenarijų sesijų sprendimai ir KPI (žaidėjo + vidiniai) | Debrifingo ir vertinimo medžiaga |
| **Naudotojai** | Kurti/redaguoti žaidėjus; importuoti iš XLSX | Grupės paruoštos greičiau |
| **Komandos** | Kurti komandas, priskirti žaidėjus | Grupinis valdymas |

---

## GAMER (žaidėjas)

**Tikslas:** Žaisti verslo simuliaciją – priimti mėnesinius sprendimus ir matyti rezultatus.

| Etapas | Galimybės | Rezultatas |
|--------|-----------|------------|
| **Scenarijų sąrašas** | Mato tik jam prieinamus scenarijus | Atrenkamas scenarijus žaidimui |
| **Scenarijaus informacija** | Skaito instrukciją (LT arba EN) | Supranta žaidimo taisykles |
| **Sesijos pradėjimas** | Sukuria naują bandymą (pagal leidžiamą limitą) | Pradedama nauja 6 mėnesių simuliacija |
| **Sprendimai × 7 per mėnesį** | Kainodara · Marketingas · Žaliavos · Gamyba · Personalas · Atlyginimai · Viršvalandžiai | Įvesti mėnesio valdymo parametrai |
| **Skaičiuoklė (Alpine.js)** | Realiu laiku mato preliminarius kaštus/poveikį kol pildoma forma | Galima patikrinti prieš išsaugant |
| **Juodraštis** | Auto-išsaugojimas naršyklės sesijoje, kol nespaudžiama „Išsaugoti" | Netyčia neuždarius – duomenys neprarandami |
| **Rezultatai** | Po išsaugojimo mato 50+ KPI: paklausa, pardavimai, pelnas, pinigų srautas, atsargos, kokybė | Supranta savo sprendimų pasekmes |
| **6 mėnesių ciklas** | m1 → m2 → ... → m6, kiekvienas mėnuo remiasi ankstesnio pabaigos būsena | Matoma verslo evoliucija per pusmetį |
| **Pateikimas** | Užrakina sesiją → ji atsiranda istorijoje | Baigtas vienas pilnas žaidimas |
| **Nustatymai** | Kalba (LT/EN), pranešimai, eksporto formatas | Asmeninė sąsajos konfigūracija |

---

> **Prieigos apribojimas:** Žaidėjas nemato `/admin` panelės, kitų žaidėjų sesijų, scenarijaus konfigūracijos.
