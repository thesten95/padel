# 🎾 Padel Americano — Maszyna turniejowa

Aplikacja webowa do prowadzenia turnieju **Padel Americano** (wariant indywidualny):
losuje pary zgodnie z zasadami Americano (każdy gra z każdym jako partner, bez powtórek
par tak długo, jak to możliwe), prowadzi **ranking na żywo** i zapisuje **historię turniejów**.

Aplikacja jest w 100% statyczna (jeden plik `index.html`, bez frameworków i bez budowania) —
działa od razu po wrzuceniu na **GitHub Pages**.

## ✨ Funkcje

- Konfiguracja: nazwa turnieju, punkty na mecz, korty (z numerami/nazwami), zawodnicy.
- Algorytm Americano: zmienne pary, minimalizacja powtórzeń partnerstw i przeciwników.
- Automatyczne, sprawiedliwe **pauzy**, gdy graczy nie da się równo podzielić na korty.
- Wpisywanie wyników z autouzupełnieniem do stałej puli punktów.
- **Ranking na żywo** z animowanym przesortowaniem, wskaźnikiem trendu (▲▼) i różnicą punktów.
- Remisy punktowe rozstrzygane jako **ex aequo** (to samo miejsce).
- **Historia** zakończonych turniejów z pełną tablicą wyników.
- **Udostępnianie wyników** z poziomu historii oraz udostępnionego linku:
  - **Link tylko-do-odczytu** — dane tablicy są zakodowane w samym adresie (część `#r=...`),
    więc działa bez serwera. Otwarcie linku pokazuje **wyłącznie** tablicę wyników; z tego
    poziomu nie da się uruchomić ani zmienić turnieju.
  - **Grafika PNG** tablicy wyników do pobrania (generowana w przeglądarce).
  - **Wyślij mailem** — otwiera klienta poczty z gotowym tematem, tablicą wyników i linkiem
    (statyczna strona nie wysyła maila samodzielnie; finalne „wyślij" klikasz w swoim mailu).
- Zapis w przeglądarce (`localStorage`) — odświeżenie strony nie kasuje turnieju.
- „Nowy turniej" zawsze startuje z czystym formularzem.

## 🚀 Publikacja na GitHub Pages

1. Utwórz nowe repozytorium na GitHubie (np. `padel-americano`).
2. Wrzuć do niego plik **`index.html`** (oraz opcjonalnie ten `README.md`).
3. W repozytorium wejdź w **Settings → Pages**.
4. W sekcji **Build and deployment → Source** wybierz **Deploy from a branch**.
5. Wybierz branch **`main`** i katalog **`/ (root)`**, kliknij **Save**.
6. Po chwili strona będzie dostępna pod adresem:
   `https://TWOJA-NAZWA-UZYTKOWNIKA.github.io/padel-americano/`

> Plik `index.html` musi znajdować się w głównym katalogu repozytorium (root),
> żeby Pages otworzyło go automatycznie.

## 🧮 Jak działa algorytm

- Na każdym korcie gra 4 zawodników (para vs para). Liczba kortów = liczba meczów naraz.
- W każdej rundzie aplikacja dobiera grających tak, by liczba rozegranych meczów była
  jak najbardziej wyrównana (rotacja pauz).
- Pary dobierane są greedy + wiele losowych prób, z wyborem układu o najmniejszej liczbie
  powtórzeń partnerstw; mecze para-vs-para minimalizują powtórzenia przeciwników.
- Liczba rund: `liczba_graczy − 1` (parzyste) lub `liczba_graczy` (nieparzyste).

## 🔤 Czcionka

Projekt używał oryginalnie czcionki **Sofia Pro**, która jest jednak komercyjna (płatna)
i nie może być osadzona w publicznym repozytorium ze względów licencyjnych.
Zastosowano darmowy, bardzo zbliżony zamiennik **[Mulish](https://fonts.google.com/specimen/Mulish)**
(Google Fonts, licencja SIL Open Font License) — geometryczny grotesk z miękkimi kształtami.

Jeśli posiadasz licencję na Sofia Pro, wystarczy podmienić deklarację `@font-face`
i zmienną `font-family` w sekcji `<style>`.

## 📄 Licencja

Kod aplikacji możesz używać i modyfikować dowolnie. Czcionka Mulish na licencji OFL.
