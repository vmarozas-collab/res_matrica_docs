# Resursų Matrica — Techninė Dokumentacija

## Projekto tikslas

Verslo simuliacijos edukacinė platforma. Studentai priima mėnesinius verslo sprendimus 6 mėnesiams (M1–M6) ir gauna KPI rezultatus. Instruktoriai kuria scenarijus, administratoriai valdo naudotojus ir komandas.

---

## Techninis Stack

| Komponentas | Technologija |
|---|---|
| Backend | Laravel 13, PHP 8.3 |
| Admin panelis | Filament v5 + FilamentShield (RBAC) |
| Frontend reaktyvumas | Alpine.js v3 |
| Assets build | Vite 8 |
| DB | MySQL, SESSION_DRIVER=database |
| Rolės/teisės | Spatie Laravel-Permission |
| Feedback | `vm/feedback-widget` paketas |
| Lokalizacija | LT + EN |

---

## Rolės

- **super_admin** — viskas
- **admin** — viskas, išskyrus rolių valdymą
- **instructor** — kuria ir valdo scenarijus, mato tik savo komandas ir žaidėjus
- **user** — žaidžia per `/app`

---

## Pagrindiniai modeliai

| Modelis | Aprašas |
|---|---|
| `Scenario` | Scenarijus; `hasOne` Constants + Parameters; `hasMany` GameSession |
| `ScenarioConstants` | ~20+ konstantų (kainos, defect rates, lead times) |
| `ScenarioParameters` | Bazinė paklausa + sezoniškumas kiekvienam mėnesiui |
| `GameSession` | Vienas bandymas (user + scenario + attempt); status: active/submitted |
| `GameDecision` | Visi 7 sprendimų tipai vienoje eilutėje mėnesiui |
| `GameResult` | 90+ apskaičiuotų KPI stulpelių mėnesiui |
| `Team` | Naudotojų grupavimas scenarijaus priėjimui |

---

## Dviguba skaičiavimo logika (sinchronizuota)

| Sluoksnis | Failas | Paskirtis |
|---|---|---|
| Kliento pusė | `resources/js/game-calculator.js` (629 eilučių) | Alpine.js reaktyvi peržiūra |
| Serverio pusė | `app/Services/GameCalculator.php` (~600 eilučių) | Autoritatyvus skaičiavimas, rašo į DB |

Formulės atspindi Excel modelį (komentarai kode nurodo Excel eilutės numerius).

---

## Sprendimų tipai (7)

`price` · `marketing` · `procurement` · `production` · `workforce` · `salary` · `overtime`

Kiekvienas turi savo Blade puslapį. Auto-save juodraščiai į PHP sesiją per AJAX (`/decisions/draft-session`).

---

## Pagrindiniai routes (`/app`)

```
/app/scenarios                                    → scenarijų sąrašas
/app/scenarios/{scenario}/games                   → bandymų sąrašas
/app/scenarios/{scenario}/games/{session}/dashboard
/app/scenarios/{scenario}/games/{session}/decisions/{type}
/app/scenarios/{scenario}/games/{session}/results
/app/scenarios/{scenario}/games/{session}/submit  POST
```

---

## Filament admin panelis (`/admin`)

- **Resources:** UserResource, TeamResource, ScenarioResource, GameSessionResource
- **Pages:** ManageConstants (globalios numatytosios konstantos), ManageParameters
- **GameSessionResource:** ViewRecord su M1–M6 tabs — sprendimai + rezultatai
- **Feedback widget:** įjungtas Filament panelėje, siunčia email pranešimus

---

## Svarbūs servisai / traitai

- `GameCalculator` — pagrindinis skaičiavimo servisas
- `ResolvesCurrentMonth` trait — aktyvaus mėnesio valdymas sesijoje
- `EnsureAppRole` middleware — rolių tikrinimas `/app`
- `EnsureScenarioAccess` middleware — scenarijaus priėjimo tikrinimas
- `ScenarioObserver` — automatiškai sukuria `ScenarioConstants` ir `ScenarioParameters` kuriant scenarijų

---

## Kas padaryta (commit chronologija)

1. Filament shield + RBAC sukonfigūruotas
2. Naudotojų importas (Excel), rolių atskyrimas tabais
3. Blade šablonai iš prototipo, prisijungimo langas
4. Alpine.js scenarijai, mygtukų logika
5. Komandos, User atributai, nuorodos tarp panelių
6. Excel importas patobulinta, SH skriptas deploy'ui
7. Sprendimų puslapiai, indikatorių blokeliai
8. GameResult skaičiavimai + duomenų įvedimo valdymas
9. Rezultatai/KPI langas + išsaugojimas
10. Išsaugojimo pranešimas
11. Lokalizacija LT + EN
12. UI pataisymai (laukų išdėstymas)
13. Rolių pataisymai (instruktorius mato tik savo)
14. Viešas scenarijus (is_public varnelė)
15. Mėnesių sesijos logika pataisyta
16. Žaidimų bandymų logika (GameSession CRUD)
17. Tooltipai, KPI informacija dashboarde
18. Scenarijaus informacinis puslapis
19. Navigacijos pataisymai
20. Scenarijų valdymas Filament
21. GameSession Filament resursas
22. Feedback paketas (`vm/feedback-widget`) integruotas
23. Saugumo patikros atliktos
24. Bugfix'ai po pirmojo siuntimo

---

## Naudotojų reikalavimai

- **Studentai:** prisijungti, pasirinkti scenarijų, sukurti bandymą, vesti sprendimus 7 kategorijose kiekvienam mėnesiui, peržiūrėti KPI rezultatus, pateikti galutinį sprendimą
- **Instruktoriai:** kurti/redaguoti scenarijus (su konstantomis ir parametrais), priskirti komandas, peržiūrėti studentų žaidimų sesijas
- **Administratoriai:** valdyti naudotojus (importas, rolės), komandas, visus scenarijus ir žaidimų sesijas
- **Visi:** UI lietuvių kalba; realaus laiko skaičiavimų peržiūra prieš išsaugant
