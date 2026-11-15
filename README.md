# EcoPralnia: strona wizytówka

Statyczna strona wizytówka pralni wodnej **EcoPralnia** z Wrocławia (ul. Tarasa Szewczenki 42, Psie Pole, tel. 603 708 002).
Czysty HTML, CSS i JS, bez frameworków i bez kroku budowania. Strona leży w korzeniu repo, więc GitHub Pages (gałąź `main`, folder `/ (root)`) serwuje ją od razu. Na inny hosting wystarczy wgrać pliki z korzenia, bez `docs/`, `src/` i `README.md`.

Wersja: **v9** (listopad 2026).

## Co jest na stronie

- **Pierwszy ekran** z hasłem „Pierzemy w wodzie to, co zwykle trafia do chemii”, telefonem i paskiem faktów.
- **01 Metoda**: pranie wodne (wet cleaning) na maszynach Girbau i trzy karty ze zdjęciami.
- **02 Co przyjmujemy**: 9 kafli z rzeczami, kafel „Nie ma tu Twojej rzeczy?” i tryby prania (36–48 h, 24 h, ten sam dzień).
- **Jak to działa**: trzy kroki (zadzwoń, przynieś, odbierz).
- **03 Suknie ślubne**: kolaż i opinia klientki.
- **04 Opinie**: średnia 4,5 z 22 opinii w Google, duży cytat i dwa mniejsze.
- **05 Jak trafić**: kroki dojazdu i mapa Google, która ładuje się dopiero po kliknięciu (bez baneru o ciasteczkach).
- **06 Kontakt**: duży numer, Messenger, e-mail i godziny z informacją „otwarte teraz” liczoną według czasu we Wrocławiu.
- **Stopka** z kontaktem, godzinami i linkami.

Na komputerze po lewej stronie jest przyklejona kolumna z logo, spisem treści, telefonem i godzinami. Spis treści zaznacza aktualną sekcję i ma pasek postępu przewijania. Na telefonie zamiast niej jest górny pasek z menu, a na dole pasek z przyciskami „Zadzwoń” i „Jak trafić”.

## Marka

- Kolory z reklam firmy: niebieski (`#0b6cb0`, `#09558f`, `#08497c`) na duże powierzchnie i zieleń (`#0f7d38`) na przyciski, numery i ikony.
- Font: Sofia Sans i Sofia Sans Condensed, wgrane lokalnie w `fonts/`.
- Strona ma jasny i ciemny motyw (`prefers-color-scheme`). Kontrast tekstu sprawdzony na co najmniej 4,5:1.
- Zdjęcia wygenerowano w Gemini i pokazują tylko ubrania, tkaniny i wodę. Nie przedstawiają pralni, ludzi ani efektów jej pracy.

## Struktura

```
index.html             gotowa strona (GitHub Pages serwuje korzeń)
img/                   zdjęcia w AVIF i WebP (tła CSS, image-set)
fonts/                 woff2
favicon.svg, og.jpg, robots.txt, sitemap.xml, .nojekyll
src/index.tpl.html     szablon źródłowy (fonty wstawiane w miejsce {{FONTFACES}})
docs/
  podglad-jeden-plik.html   cała strona w jednym pliku (zdjęcia i fonty w base64), do wysłania klientowi
  DESIGN.md                 decyzje projektowe v4–v9
  RESEARCH.md               źródła danych o firmie
  DO-UZUPELNIENIA.md        lista rzeczy do potwierdzenia z firmą
  PROMPTY-GEMINI*.md        prompty do zdjęć
  brief.json                dane firmy
```

Oryginały zdjęć z Gemini (`media/`, ok. 56 MB) nie są w repozytorium.

## Podgląd lokalny

```
python -m http.server 8000
```

Potem otwórz http://localhost:8000.

## Do uzupełnienia przed publikacją

Wszystkie miejsca są oznaczone w kodzie komentarzem `TODO`:

- plik logo firmy (teraz jest znak zastępczy),
- prawdziwe zdjęcia domu od ulicy oraz furtki z dzwonkiem (trafią obok mapy),
- opis wejścia (furtka, dzwonek, tabliczka),
- cennik,
- docelowa domena (`canonical`, `og:url`, `og:image`, `sitemap.xml`),
- działający adres e-mail, potwierdzenie Messengera, NIP i podpis autora strony,
- potwierdzenie trybów prania i usługi odbioru dywanów.
