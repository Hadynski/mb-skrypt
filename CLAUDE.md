# Skrypt sprzedażowy — M&B Biuro Rachunkowe

Interaktywny skrypt rozmowy handlowej dla zespołu M&B. Jedna strona HTML (`index.html`),
bez frameworków i bez builda — cała aplikacja (style + logika + treści) siedzi w tym pliku.

## Produkcja i deploy

- **Adres: https://hadynski.github.io/mb-skrypt/**
- Hosting: GitHub Pages, repo `Hadynski/mb-skrypt`, workflow `.github/workflows/static.yml`
- **Deploy = `git push` na `main`.** Po ~1 minucie zmiana jest na produkcji, użytkownicy tylko odświeżają stronę.
- To repo NIE ma nic wspólnego ze stroną hadynski.pl — nie mieszać.

## Dostęp

- Wejście do aplikacji jest za hasłem zespołowym (ekran blokady, hasło zapamiętywane w przeglądarce).
- **Linki bez wpisywania hasła** — hasło podane w adresie po `#` odblokowuje automatycznie:
  - zespół: `https://hadynski.github.io/mb-skrypt/#<hasło>`
  - właściciel: `.../#MKD2026` — odblokowuje **i** pokazuje przycisk „Ustawienia" (edycja treści)
- Handlowiec z gołym linkiem nie widzi Ustawień w ogóle.
- To bariera przed przypadkowymi osobami, nie kryptografia — repo jest publiczne.

## Zasady pracy nad treścią (ważne)

- **W skrypcie ląduje wyłącznie to, co Mikołaj zatwierdził na czacie.** Nie dopisywać obietnic,
  nie „wygładzać" faktów handlowych, nie wstawiać rzeczy „w przygotowaniu" — jak coś nie jest gotowe,
  po prostu tego nie ma.
- Propozycje treści dawać najpierw w rozmowie do akceptu, dopiero potem wdrażać.
- Ton: krótko, mówionym językiem, szczerze („mamy w tym interes"), bez korporacyjnej waty.
- Ceny mówione **raz**, zawsze **netto**.

## Jak działa kod

- `DEFAULT_CONFIG` — wszystkie treści skryptu (ścieżki A–D, obszary prezentacji, obiekcje, cennik,
  zamknięcie, SMS). Edytowalne też z poziomu Ustawień (zapis w localStorage).
- **Podbicie `DEFAULT_CONFIG.version` unieważnia lokalne edycje** u wszystkich — robić przy każdej
  zmianie zatwierdzonych treści, żeby zespół dostał nową wersję.
- Numer wersji w stopce (`.footer-note`) — podbijać przy każdej publikacji, po nim poznajemy,
  czy ktoś ma aktualną wersję.
- **Formy żeńskie generują się automatycznie** (`toFemale` + odmiana imion przez przypadki).
  Nowe teksty pisać w formie męskiej. Uwaga na słowa typu „sam" w pobliżu zwrotu do klienta —
  automat je feminizuje (użyć „automatycznie" zamiast „sam", jeśli chodzi o system).
- Znaczniki w treściach: `{K}` = imię klienta (odmienia się samo), `{H}` = handlowiec.

## Testowanie przed pushem

Sprawdzić składnię JS i przeklikać przepływ lokalnie (`python3 -m http.server`), zanim pójdzie na produkcję —
jeden błąd w `<script>` wywala całą stronę, bo wszystko jest w jednym pliku.
