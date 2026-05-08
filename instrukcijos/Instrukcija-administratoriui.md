# Instrukcija administratoriui

## Prisijungimas

Administratorius prisijungia per **`/admin`** adresą (ne per `/login`).

---

## Naudotojų valdymas

**Admin panelis → Naudotojai**

- **Peržiūra:** naudotojai atvaizduojami dviejuose tabsuose — *Administratoriai* ir *Paprasti naudotojai*
- **Sukūrimas:** mygtukas „Naujas naudotojas" — įvesti vardą, el. paštą, slaptažodį, pasirinkti rolę
- **Importas:** naudotojai gali būti importuojami iš Excel failo (mygtukas „Importuoti")
- **Rolės:** kiekvienam naudotojui priskiriama viena rolė: `super_admin`, `admin`, `instructor`, `user`
- **Redagavimas / šalinimas:** per veiksmų meniu šalia kiekvieno įrašo

> Pastaba: tik `super_admin` gali keisti rolių teises ir valdyti kitus administratorius.

---

## Komandų valdymas

**Admin panelis → Komandos**

- Sukurti komandą → suteikti pavadinimą
- Priskirti naudotojus prie komandos
- Komanda naudojama kontroliuoti prieigą prie scenarijaus

---

## Scenarijų valdymas

**Admin panelis → Scenarijai**

Administratorius gali:
- **Kurti** naują scenarijų (pavadinimas LT + EN, aprašymas, ar viešas)
- **Redaguoti** scenarijų ir jo konstantas bei parametrus
- **Priskirti komandas** prie scenarijaus (tik priskirtų komandų nariai mato scenarijų)
- **Viešas scenarijus** (varnelė „Viešas") — matomas visiems prisijungusiems naudotojams

### Konstantos (Scenarijai → Redaguoti → Konstantos)

Kiekvienas scenarijus turi savo konstantų rinkinį (žaliavų kainos, defektų normos, pristatymo terminai ir kt.). Jos kopijuojamos iš globalių numatytųjų reikšmių kuriant scenarijų ir gali būti keičiamos atskirai.

### Parametrai (Scenarijai → Redaguoti → Parametrai)

Bazinė paklausa ir sezoniškumas kiekvienam mėnesiui (M1–M6).

---

## Globalios konstantos (numatytosios)

**Admin panelis → Nustatymai → Konstantos**

Šios reikšmės naudojamos kaip numatytosios kuriant naują scenarijų. Keičiant čia, jau esančių scenarijų konstantos **nesikeičia**.

---

## Žaidimų sesijų peržiūra

**Admin panelis → Žaidimų sesijos**

- Matomi visi žaidėjų bandymai (visi scenarijai, visi naudotojai)
- Kiekviena sesija turi tabs: M1–M6 su sprendimais ir rezultatais
- Galima filtruoti pagal scenarijų, naudotoją, statusą

---

## Feedback

Administratorius gauna el. pašto pranešimus, kai naudotojai pateikia atsiliepimus per feedback mygtukus sistemoje.
