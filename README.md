# Karnet — filtry w modalu

Interaktywny prototyp portalu Karnet Kraków (widok: filtry wydarzeń w modalu),
wyeksportowany z Claude Design.

## Uruchomienie lokalne

To statyczna strona, ale **nie otwieraj `index.html` bezpośrednio przez `file://`**
— strona doczytuje samą siebie przez `fetch()`, co wymaga serwera HTTP.

```bash
python3 -m http.server 8811
```

Następnie otwórz [http://localhost:8811](http://localhost:8811).

Do działania strony (React, ReactDOM, Babel, mapa Leaflet) potrzebne jest
połączenie z internetem — biblioteki doczytywane są z CDN (unpkg.com).

## Struktura

- `index.html` — dokument prototypu (format `.dc.html` z Claude Design:
  szablon w `<x-dc>` + logika komponentu w `<script data-dc-script>`)
- `support.js` — silnik renderujący dokumenty `.dc.html` (wygenerowany,
  nie edytować ręcznie)
- `image-slot.js` — komponent `<image-slot>` do podmiany zdjęć w edytorze
  Claude Design (na produkcji tylko odczytuje zapisany stan)
- `.image-slots.state.json` — zapisane zdjęcia dla `<image-slot>`
- `EventCardKarnet.jsx` — komponent karty wydarzenia (`<x-import>`)
- `_ds/karnet-krak-w-design-system-.../` — design system: tokeny (kolory,
  typografia, odstępy, promienie, cienie, motion) i komponenty
- `assets/`, `pdfs/` — zdjęcia i pliki PDF użyte w prototypie
- `sa/` — biblioteka zdjęć wydarzeń (współdzielona z innymi widokami projektu)

## Uwaga

To prototyp projektowy, nie gotowa do produkcji aplikacja — część interakcji
(zapis ulubionych, powiadomienia) działa tylko lokalnie w przeglądarce.
