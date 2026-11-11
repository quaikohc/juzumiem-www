# Strona www „Już umiem!” (juzumiem.app)

Statyczna strona (HTML + CSS, bez Jekylla i bez skryptów) publikowana przez GitHub Pages z gałęzi `main`.
To repo jest źródłem strony: zmiany w tekstach robimy tutaj.

## Strony

| Adres | Plik | Treść |
|---|---|---|
| `/` | `index.html` | czego uczy, zrzuty, dla rodziców, cena |
| `/prywatnosc/` | `prywatnosc/index.html` | polityka prywatności (adres podany w aplikacji, ekran „O aplikacji”, i w Google Play) |
| `/regulamin/` | `regulamin/index.html` | regulamin: wersja bezpłatna, 7 dni próby, subskrypcja, reklamacje |
| `/pomoc/` | `pomoc/index.html` | kontakt i najczęstsze pytania |
| (każdy zły adres) | `404.html` | „Nie ma takiej strony” |

Własną domenę `juzumiem.app` wpisuje się w Settings → Pages → Custom domain (GitHub sam doda plik `CNAME`); do tego czasu strona jest pod https://quaikohc.github.io/juzumiem-www/. `.nojekyll` wyłącza Jekylla, `robots.txt` + `sitemap.xml` dla wyszukiwarek.

## Do uzupełnienia przed wydaniem

Na stronie są żółte, przerywane ramki (`<span class="todo">`), wyszukaj `class="todo"`:

- dane sprzedawcy (imię i nazwisko, nazwa firmy, adres, NIP, REGON): `prywatnosc/` i `regulamin/`,
- data wejścia w życie regulaminu: `regulamin/`.

Teksty prywatności i regulaminu warto dać do przejrzenia prawnikowi. Polityka zakłada stan na premierę:
zakupy przez Google Play i bramkę dla rodzica przed zakupem.

Gdy aplikacja pojawi się w sklepie, przycisk „Wkrótce w Google Play” (`index.html`, `.btn.soon`) zamień na link
`https://play.google.com/store/apps/details?id=pl.juzumiem.app` (najlepiej z oficjalną plakietką Google Play).

## Grafiki i czcionki

Skrypt `www/_zrodla/mk_assets.py` w repo aplikacji (MatematykaCzytanie, gałąź `claude/project-thread-rduiiu`) generuje `assets/img/` i `assets/fonts/` z zasobów aplikacji (logo, ikony sekcji, tło,
czcionki Baloo 2 i Andika jako woff2, licencja OFL obok) oraz wycina zrzuty 540×960 z zestawień w folderze projektu.
Czcionki są na serwerze strony, nie z Google Fonts, żeby nie wysyłać adresów IP do Google.

## Publikacja (GitHub Pages)

1. Publiczne repo z zawartością tego folderu w katalogu głównym, gałąź `main`.
2. Settings → Pages → Build and deployment: „Deploy from a branch”, `main`, `/ (root)`.
3. Gdy DNS działa: Custom domain `juzumiem.app` → Save, po wystawieniu certyfikatu zaznaczyć „Enforce HTTPS”.

DNS w Cloudflare (rekordy „DNS only”, szara chmurka):

| Typ | Nazwa | Wartość |
|---|---|---|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| AAAA | `@` | `2606:50c0:8000::153` |
| AAAA | `@` | `2606:50c0:8001::153` |
| AAAA | `@` | `2606:50c0:8002::153` |
| AAAA | `@` | `2606:50c0:8003::153` |
| CNAME | `www` | `quaikohc.github.io` |

Domeny `.app` działają tylko przez HTTPS, więc strona otworzy się dopiero, gdy GitHub wystawi certyfikat
(zwykle kilkanaście minut po ustawieniu DNS, czasem do doby).
