# Google Analytics 4 w Claude: instrukcja krok po kroku

**Po co:** żeby zapytać Claude po polsku „ile sprzedaży z Meta, a ile z Google w sierpniu?” i porównać to z Menedżerem reklam, bez chodzenia po pięciu panelach.

**Gdzie to działa:** w aplikacji Claude na komputerze (Claude Desktop) albo w Claude Code. W Claude w przeglądarce tego serwera nie da się podpiąć, bo działa lokalnie na komputerze.

**Czas:** ok. 30 minut, jednorazowo. **Uprawnienia:** tylko odczyt. Claude niczego w GA4 nie zmieni.

**Czy nie wystarczy dodać Claude jako użytkownika w GA4?** Prawie tak. Claude nie ma własnego konta Google, więc w GA4 dodajecie „konto usługi” z Google Cloud (krok 3-4), a Claude łączy się przez nie. Dlatego są kroki w Google Cloud.

---

## Droga szybka: od dziś, bez konfiguracji
1. GA4 → **Raporty** → np. **Pozyskiwanie** → **Pozyskiwanie ruchu**, ustaw zakres dat.
2. Ikona **Udostępnij** (prawy górny róg) → **Pobierz plik** → **Pobierz CSV**.
3. Wgraj plik do Claude (także w przeglądarce) i zapytaj, np. „Pokaż przychód i transakcje według źródła/medium. Co z Facebooka i Instagrama?”.

Minus: za każdym razem ręczny eksport. Dlatego niżej droga stała.

---

## Droga stała: Claude czyta GA4 sam

## Krok 1. Projekt w Google Cloud (10 min)
1. Wejdź na **console.cloud.google.com**, zaloguj się kontem firmowym.
2. Na górze: wybór projektu → **Nowy projekt** → nazwa np. `prima-bobo-claude` → Utwórz.
3. Zapisz **ID projektu** (np. `prima-bobo-claude-123456`). Przyda się w kroku 5.

## Krok 2. Włącz dwa API (2 min)
W wyszukiwarce konsoli wpisz i kliknij **Włącz** przy obu:
- **Google Analytics Data API**
- **Google Analytics Admin API**

## Krok 3. Konto usługi i klucz (5 min)
1. Menu → **Uprawnienia i administracja (IAM)** → **Konta usługi** → **Utwórz konto usługi**.
2. Nazwa: `claude-ga4`. Role pomiń, kliknij Gotowe.
3. Wejdź w utworzone konto → zakładka **Klucze** → **Dodaj klucz** → **Utwórz nowy klucz** → **JSON**.
4. Pobrany plik przenieś w bezpieczne miejsce, np. `Dokumenty/klucze/ga4-claude.json`. **Nie wysyłaj go mailem ani nie wrzucaj na wspólny dysk.**
5. Skopiuj adres konta usługi, wygląda tak: `claude-ga4@prima-bobo-claude-123456.iam.gserviceaccount.com`.

## Krok 4. Dostęp w GA4 (3 min)
1. **analytics.google.com** → Administracja (koło zębate) → **Zarządzanie dostępem do usługi**.
2. **+** → Dodaj użytkownika → wklej adres konta usługi z kroku 3.
3. Rola: **Wyświetlający**. Odznacz „Powiadom e-mailem”. Dodaj.
4. W Administracji → **Szczegóły usługi** zapisz **identyfikator usługi** (same cyfry, np. `412345678`). To nie jest `G-QFVS42LQ9R`.

## Krok 5. Podpięcie do Claude Desktop (10 min)
1. Zainstaluj **uv** (menedżer Pythona). Terminal na Macu: `curl -LsSf https://astral.sh/uv/install.sh | sh`
2. Claude Desktop → **Ustawienia** → **Developer** → **Edit Config**. Otworzy się plik `claude_desktop_config.json`.
3. Wklej (podmień dwie ścieżki i ID projektu):

```json
{
  "mcpServers": {
    "google-analytics": {
      "command": "uvx",
      "args": ["--python", "3.12", "analytics-mcp"],
      "env": {
        "GOOGLE_APPLICATION_CREDENTIALS": "/Users/TWOJA_NAZWA/Documents/klucze/ga4-claude.json",
        "GOOGLE_PROJECT_ID": "prima-bobo-claude-123456"
      }
    }
  }
}
```

4. Zapisz, zamknij Claude Desktop całkiem (Cmd+Q) i otwórz ponownie.
5. Jeśli `uvx` nie zostanie znaleziony: w Terminalu wpisz `which uvx` i wklej pełną ścieżkę zamiast `"uvx"`.

## Krok 6. Test
Napisz w Claude:
> Pokaż moje konta i usługi Google Analytics.

Potem:
> Usługa GA4 [identyfikator z kroku 4]. Pokaż przychód i liczbę transakcji z ostatnich 30 dni według źródła/medium. Osobno wypisz ruch z Facebooka i Instagrama.

## Prompty do pracy
- „Porównaj przychód z GA4 według źródła/medium z tym, co pokazuje konto reklamowe Meta za ten sam okres. Gdzie liczby się rozjeżdżają i dlaczego to normalne?”
- „Które strony produktów mają najwięcej wejść, a najmniej dodań do koszyka w ostatnich 30 dniach?”
- „Zrób tabelę: kanał, sesje, transakcje, przychód, współczynnik konwersji. Sierpień i wrzesień obok siebie.”

## Uwaga do liczb
GA4, Meta i WooCommerce zawsze pokażą trochę inne liczby: inne okna atrybucji, zgody na cookies, blokery reklam. Źródłem prawdy o sprzedaży jest sklep i wasz wewnętrzny panel. GA4 i Meta służą do porównań i trendów.
