# EcoPralnia: DESIGN

## Wersja 3 (2026-10-22, uwagi Fabiana)
- Sekcja „Zajrzyj na metkę” skrócona z ok. 80 rem do ok. 40 rem i zamieniona w interaktywną etykietę: trzy przyciski symboli (W, P, miska) zmieniają opis, bez JS wszystkie opisy widoczne. Cztery fakty o metodzie w dwóch zdaniach każdy.
- Tła sekcji 2 i 3: woda (img/water-soft.webp, RGBA) i duże kontury symboli; draperia (img/drape.webp) i kołyszące się kontury wieszaków.
- Wieszaki usług kołyszą się w 3D (perspective + rotateY/rotateX, pivot na szynie, różne fazy, pauza na hover); metka w hero po pierwszym huśtaniu kołysze się dalej.
- Perły przerobione z rastra na wektorowy SVG (gradient, cień, nitka, migot, kołysanie), tiul zostaje rastrem.
- Ruch dodatkowy: dryf wody w hero, taśma wjeżdża ze scrollem, ścieg dojazdu rysuje się ze scrollem, karteczki opinii lekko się unoszą. Wszystko wyłączone przy prefers-reduced-motion, ruch ze scrollem tylko w @supports.

## Wersja 2 (redesign 2026-10-22): łamanie schematów
Powód: wersja 1 wyglądała jak szablon (jeden kontener, równe odstępy, rzędy kart, płaskie tła). Wywołane skille: frontend-design, ui-ux-pro-max (design system z --variance 9; styl „brutalizm” z wyniku odrzucony jako niepasujący do pralni, wzięta asymetria i skala), web-build-standards.
- Kompozycja: hero z gigantycznym W (obraca się ze scrollem, tylko w @supports i bez reduced motion) i metką zwisającą z nitki przez granicę sekcji; nagłówki w schodkach; każda sekcja z innymi marginesami.
- Granice sekcji: zygzak nożyczek krawieckich (maska CSS z SVG) na 5 przejściach.
- Usługi: metki na wieszaku (różne szerokości, obroty, nitki), tryby prania jako centymetr krawiecki przecinający granicę z sekcją sukien.
- Suknie: tiul z perłami (grafika tła). Opinie: gigantyczne 4,5 i nakładające się karteczki. Dojazd: ścieg prowadzący między zdjęciami. Kontakt: numer 14 rem, karta godzin na skos.
- Grafiki tła (proceduralne, tools/gen_textures.py, seed 7, bez AI): img/hero-water(.tall), img/pearls(.tall), img/fabric. Maski ciemne pod tekst wypieczone w obrazie. Skrypt do Gemini (tools/gen_bg_openrouter.py) gotowy, nieużyty (OpenRouter niedostępny w środowisku).
- Kontrast tekstu na grafikach zmierzony (próbkowanie tła pod liniami tekstu): min. 4,57:1 (jasny i ciemny), duży numer telefonu 10,7:1.
- Ruch: huśtanie metki raz na starcie i obrót W ze scrollem; reszta statyczna.

## Podmiot i cel
Pralnia wodna (wet cleaning) w domu jednorodzinnym, ul. Tarasa Szewczenki 42, Wrocław. Cel strony: telefon z zapytaniem o cenę, łatwe trafienie pod adres i drugi kanał kontaktu (Messenger), bo opinie skarżą się na nieoznakowane wejście i nieodbierany telefon.

## Kombinacja: A. Metka
| Oś | Wybór | Ziarno |
|---|---|---|
| Układ | katalog-indeks: usługi jako metki | metka ubrania |
| Typografia | wąski grotesk z metek: Sofia Sans Condensed 600/800 + Sofia Sans 400/600/700 (hostowane lokalnie, OFL) | nadruk na metce |
| Źródło koloru | materiał metki (biel tasiemki, granat nadruku) + kolory logo jako detal | metka, logo firmy |
| Hero | typografia + metka z symbolem W (HTML/SVG) | W w kółku = profesjonalne pranie wodne (ISO 3758) |
| Sygnatura | „Zajrzyj na metkę”: symbole W, P, miska; plus „Jak do nas trafić” krok po kroku | metoda firmy; problem z opinii |

Złamana konwencja: zamiast bąbelków, złożonych ręczników i zielonych listków strona mówi językiem metki z szafy klienta.

## Tokeny
| Token | Jasny | Ciemny | Rola |
|---|---|---|---|
| --paper | #fbfaf6 | #10161d | tło (biel tasiemki) |
| --label | #ffffff | #18212b | powierzchnie metek i kart |
| --ink | #12263a | #e9edf2 | tekst, nadruk |
| --muted | #4a5868 | #a9b5c1 | tekst pomocniczy (6,96:1 / 8,72:1) |
| --line | #d9d4c8 | #2c3743 | szwy, ramki |
| --action | #0b5fa5 | #6cbcf0 | jedyny kolor akcji (6,57:1 / 8,46:1) |
| --brand-blue | #0090d8 | #3fb0ec | tylko w znaku „PRALNIA” (logo) |
| --brand-green | #009038 | #3cbf6b | tylko w znaku „eco” (logo) |
| --deep | #12263a | #0a2236 | suknie ślubne, kontakt, stopka |

## Typografia i skala
h1 clamp(2.6–5 rem) 800; h2 clamp(2–3.25 rem) 800; h3 1.5 rem 600; tekst 1.0625 rem. Promień 6 px (karty), pigułka dla przycisków.

## Komponenty
Navbar fixed 64 px (zmienia się tylko linia), metka hero (obrót −3°, na hover −1°, wyłączone przy reduced motion), karty symboli, karty-metki z chipami, tryby prania, cytaty z Google, kroki dojazdu z miejscami na zdjęcia, kontakt z dużym numerem i tabelą godzin, dolny pasek na telefonie.

## CTA per sekcja
| Sekcja | Akcja |
|---|---|
| Navbar | Zadzwoń / 603 708 002 |
| Hero | Zadzwoń (główna), Jak do nas trafić |
| Usługi | ostatnia karta: zadzwoń |
| Suknie | Zapytaj o suknię |
| Opinie | link do wszystkich opinii |
| Jak trafić | Zadzwoń, Wyznacz trasę |
| Kontakt | Zadzwoń, Messenger, kopiuj e-mail |
| Telefon | dolny pasek: Zadzwoń, Jak trafić |

Formularz pominięty świadomie: skrzynka e-mail niepotwierdzona, a klienci i tak dzwonią przed oddaniem rzeczy.

## Zdjęcia
- Brak zdjęć z wizyty. Od właściciela w Google: logo (do podmiany w navbarze, plik nie został pobrany) i zdjęcie punktu w Galerii Kiełczowskiej. To drugie nie zostało użyte, bo pokazuje dawną lokalizację, nie dom przy Szewczenki 42.
- Miejsca na zdjęcia: dom od ulicy, furtka i dzwonek, lada lub wnętrze.
- og.jpg wygenerowany z metki i nagłówka, bez zdjęć.
- Grafiki tła są proceduralne (patrz wersja 2), nie przedstawiają firmy, ludzi ani efektów pracy.

## Psychologia
Hick: 4 linki + telefon. Fitts: cele ≥ 44 px, dolny pasek. Von Restorff: tylko akcja w --action. Jakob: logo lewo, telefon prawo, kontakt na końcu. Dowód społeczny: 4,5 / 22 opinie w hero, cytaty o sukniach. Pierwszy ekran: co (pranie wodne), gdzie (Szewczenki 42), kiedy (godziny), kontakt.

## Lista zakazana i odrzucone
Bez zielonych listków i bąbelków jako dekoracji, bez cennika z 2019, bez zdjęcia dawnej lokalizacji, bez oceny w JSON-LD (samodzielnie publikowane oceny są niezgodne z wytycznymi Google), bez Google Fonts z serwerów Google.

## Do uzupełnienia przez firmę
Logo (plik), opis wejścia i zdjęcia furtki, aktualność trybów, dywanów i poprawek, e-mail, NIP i nazwa działalności, domena, kto obsługuje Messengera, zgoda na podpis autora.

## Wersja 5 (2026-11-15): profesjonalny minimalizm
- Na prośbę Fabiana: bez dekoracji (bąbelki, perły, miarka, wieszaki, zygzaki, tła wody usunięte), bez tradycyjnych pasów sekcji.
- Układ: przyklejona lewa kolumna (logo, spis treści 01–06 z zaznaczeniem bieżącego bloku, telefon, godziny, „Wyznacz trasę”); po prawej bloki na jednym tle, na 12-kolumnowej siatce, każdy przesunięty inaczej (metoda w kolumnach 4–12, usługi w dwóch kolumnach, suknie z cytatem przesuniętym w dół, opinie z cytatami na różnych wysokościach, dojazd od kolumny 5).
- Kolory: tło #fcfcfb, granat #0f1d2b, akcent #0b5fa5, kolory logo tylko w znaku; tryb ciemny. Czcionka Sofia Sans 400/600 (bez Condensed).
- Ruch: tylko wejście pierwszego ekranu i hovery; brak animacji przy scrollu. Grafiki proceduralne v2–v4 przeniesione poza paczkę.
- og.jpg: zrzut pierwszego ekranu v5.
- v5.1: kamienna lewa kolumna i panele (#efebe3), blok usług na kamiennym tle, kontakt w granacie. Miejsca na 8 grafik z Gemini (prompty: PROMPTY-GEMINI.md): hero-wool, drum-water, fabric-cashmere/linen/down, tulle-pearls, bg-linen, bg-navy-wool. Grafiki pokazują materiały, nie efekt pracy firmy; oznaczyć jako wygenerowane. Pliki ładowane jako tła CSS, więc do czasu dostarczenia widać spokojne plamy koloru.
- v5.2: wstawione grafiki wygenerowane przez Fabiana w Gemini (2026-11-15), oryginały w media/gemini/. Wszystkie dekoracyjne (tła CSS, aria-hidden), pokazują materiały, nie pracę firmy. fabric-down przycięte do samej tkaniny (na oryginale widać rękaw osoby).

## Wersja 6 (2026-11-15): strona prowadzona zdjęciami
- Fabian: ludzie przeglądają, nie czytają; zdjęcia obok napisów i w tle, minimum tekstu.
- Hero: zdjęcie na całą szerokość kolumny (hero-wide), tekst po lewej na jasnym przejściu; pod spodem pasek faktów.
- Metoda: tło z wody, 3 karty zdjęć z jednym zdaniem; symbol W jako znaczek zamiast przełącznika.
- Co przyjmujemy: 9 kafli zdjęć z nazwą na zdjęciu + kafel „Nie ma tu Twojej rzeczy?”; tryby jako 3 kadry z czasem na zdjęciu.
- Suknie: tiul w tle, kolaż dwóch zdjęć z cytatem. Opinie i kontakt z dotychczasowymi tłami.
- Teksty skrócone o ok. połowę. Plan i prompty grafik: PROMPTY-GEMINI-2.md (16 nowych). Dojazd: wyłącznie prawdziwe zdjęcia od firmy.
- v6.1: wstawione 16 grafik z partii 2 (Gemini, 2026-11-15); oryginały w media/gemini/. drum-water i fabric-down wypadły z układu (zostały w media/gemini/).

## Wersja 7 (2026-11-15): kolory i ton marki EcoPralnia
- Wersja 6 zapisana jako szablon: kit/szablony/pralnia-zdjecia-v6 (ocena Fabiana 10/10, do innej firmy).
- Źródło marki: zdjęcie ich lokalu z Google (paź 2018, dawna lokalizacja w galerii, nie używać jako zdjęcia lokalu): logo z zielonym liściem, biel, niebieskie nagłówki, kobaltowa woda z kroplami, wąski krój wersalikami, czerwony akcent („DYWANU”), drewno.
- Ton z ich reklam: „Ekspert w pielęgnacji tkanin”, „Innowacyjna metoda prania wodnego”, „Ochrona włókien / Dbałość o detale / Dbałość o klienta”, „Pranie w trybie”, „Odbierzemy, wypierzemy i odwieziemy Twój dywan”.
- Zmiany: biel + chłodne panele #edf3f8, niebieski marki #0b6cb0, zieleń #11873d, czerwień #cf3329 tylko na plakietce dywanów, kontakt w gradiencie niebieskim; nagłówki Sofia Sans Condensed 800, h2 i kafle wersalikami.
- Zdjęcia: 21 przestrojonych (chłodny balans bieli, -10% nasycenia; oryginały w media/gemini/). Do dogenerowania 5 w stylu ich wody: PROMPTY-GEMINI-3.md.

## Wersja 8 (2026-11-15): bliżej reklam
- Fabian: chce kolorystyki zbliżonej do ich reklam (wszystko niebieskie i zielone).
- Niebieski jako powierzchnie: belka faktów, sekcja „Metoda” i kontakt w pełnym niebieskim marki (gradient #09558f→#08497c), lewa kolumna i tła sekcji w błękicie #e8f2fa, nagłówki sekcji niebieskie, „Pierzemy w wodzie” w h1 niebieskie.
- Zieleń jako drugi kolor: przyciski „Zadzwoń”, numery i etykiety, telefon w kolumnie, kafel „Nie ma tu Twojej rzeczy?”, zielone kółka z ikonami przy trzech filarach (jak kółka z liściem na ich witrynie).
- Kontrast zmierzony: tekst ≥4,5 w jasnym i ciemnym motywie (390/1440/1280 dark).
- Czeka na zdjęcia z PROMPTY-GEMINI-3.md (woda w stylu ich reklam): hero-splash zastąpi hero-wide, bg-splash-blue i bg-water-deep pójdą pod Metodę i Kontakt.

## v9 (2026-11-15)
- Obrazy wody z Gemini: hero-splash (hero), bg-water-deep (Kontakt), bg-splash-blue (Jak to działa), drops-white (karta 2 Metody), nowy mode-sameday.
- Menu: aktywna pozycja jako biała pigułka, numery w kółkach, zielony pasek postępu przewijania.
- Spójność: suknie odbarwione do chłodnej tonacji, równe rzędy kart i opinii, jedno zaokrąglenie, pasek faktów bez powtórzeń godzin i adresu.
- Nowe: „Jak to działa” (3 kroki), duży cytat w opiniach, mapa Google ładowana po kliknięciu, pełna stopka (dopisek o środkach przeniesiony z Metody).
