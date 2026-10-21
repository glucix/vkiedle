# Vkiedle 2.0

Statyczna gra o zgadywaniu oficjalnie wydanych utworów Vkie.

## Publikacja na GitHub Pages

1. Skopiuj `index.html`, `style.css`, `app.js`, `tracks.json` do głównego katalogu repozytorium `vkiedle` (plik `make_data.py` nie jest potrzebny do działania).
2. W repozytorium GitHub otwórz **Settings → Pages → Build and deployment**.
3. Wybierz **Deploy from a branch**, `main`, katalog `/ (root)` i zapisz.
4. Wejdź na `https://glucix.github.io/vkiedle/`.

Lokalnie testuj przez `python -m http.server 8000`, potem otwórz `http://localhost:8000`.

## Dane muzyczne

W `tracks.json` znajduje się 66 rekordów zebranych na podstawie publicznych widoków oficjalnych wydawnictw i list utworów artysty na Spotify. **To nie jest kompletna dyskografia.** Dla albumów link Spotify kieruje do wydania, **nie bezpośrednio do nagrania** (weryfikacja indywidualnych URL wymaga dodatkowej pracy). Niezweryfikowane pola mają pusty string albo `null`; daty z dokładnością jedynie do roku pozostały zapisane jako rok. Na dzień 2026-10-21 zewnętrzne pokrycie katalogu pozostaje niepełne.

Źródła albumów: https://open.spotify.com/album/6DxnoEOQHFCGgWceRgAAlr ; https://open.spotify.com/album/1k1ZDegC0mcnwi65LGa0p6 ; https://open.spotify.com/album/6moOhfkBs95i1E3CIE1uoM ; https://open.spotify.com/album/3qFXw0hg8bYqBrplcvFDWl . Dodatkowe nagrania: https://open.spotify.com/artist/3DPog7Ux8hRgsTWdlFDl7v .

Dla czterech głównych wydawnictw dodano oficjalne okładki z CDN Spotify. Cover Challenge działa dla tych wydań; rozszerzenie wymaga zweryfikowania okładek innych wydawnictw. Nie tworzono fałszywych linków do YouTube.

## Rozbudowa

Dopisuj do `tracks.json` zweryfikowane rekordy według schematu obecnych pozycji i podawaj oryginalne źródło. `trackNumber: null` oznacza singiel poza albumem. Zmieniaj identyfikatory tylko wtedy, gdy zaktualizujesz zapisane gry — istniejące partie odwołują się do `id`.

Daily działa deterministycznie wg daty w strefie Europe/Warsaw i tej samej bazy dla wszystkich. Przechowywanie w localStorage oznacza, że blokada powtórek i statystyki są **lokalne**, a nie odporne na czyszczenie pamięci. Po zmianie bazy wszystkie instancje muszą mieć tę samą wersję, aby zagadka pozostała wspólna.
