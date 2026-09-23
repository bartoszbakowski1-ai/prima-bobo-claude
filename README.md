# AI w Prima Bobo: materiały ze szkolenia 23.09.2026

Prowadzący: Bartek Bąkowski. Materiały przygotowane pod **Codex** (tego używacie na co dzień). Te same pliki działają w Claude Code, ChatGPT i Claude.

## Start w 1 minutę: wklej to do Codexa
Otwórz Codexa w folderze, w którym ma powstać „Prima Bobo AI” (np. Dokumenty albo Dysk Google), i wklej:

> Pobierz materiały z https://github.com/bartoszbakowski1-ai/prima-bobo-claude (git clone albo ZIP z https://github.com/bartoszbakowski1-ai/prima-bobo-claude/archive/refs/heads/main.zip). Utwórz folder „Prima Bobo AI” z podfolderami: produkty, zdjecia, wideo, opinie, reklamy, konkurencja, raporty. Skopiuj do głównego folderu AGENTS.md, firma.md i produkt.md z kontekst-szablony, a prompty-wywiad.md, prompty.md i instrukcja-GA4.md do podfolderu materialy. Skopiuj folder meta-copy do mojego folderu skilli Codexa (~/.codex/skills/meta-copy). Na koniec pokaż mi, co powstało, i powiedz, jak otworzyć Codexa w folderze „Prima Bobo AI”.

Codex zapyta o zgodę na pobranie z internetu i zapis plików. Trzeba ją dać.
Jeśli pobieranie nie działa: na stronie repozytorium kliknij zielony przycisk **Code**, potem **Download ZIP**, rozpakuj i napisz Codexowi, gdzie leży folder.

Potem otwórz Codexa w folderze „Prima Bobo AI” i zacznij od pierwszego wywiadu z `prompty-wywiad.md`.

## Co tu jest
| Plik | Do czego |
|---|---|
| `prompty-wywiad.md` | Prompty, dzięki którym Codex przeprowadza z wami wywiad i sam zapisuje pliki kontekstu |
| `prompty.md` | Wszystkie prompty ze szkolenia: plik produktu, konkurencja, brief, scenariusze, raport |
| `kontekst-szablony/` | Szablony do wspólnego folderu: `AGENTS.md`, `firma.md`, `produkt.md` |
| `meta-copy/` | Skill meta-copy: teksty reklam Meta na 5 poziomów świadomości klienta |
| `instrukcja-GA4.md` | Google Analytics 4 w Codexie: droga szybka (eksport CSV) i stała (konto usługi) |

## Od czego zacząć (Codex)
1. Załóżcie folder „Prima Bobo AI” (najlepiej na Dysku Google zsynchronizowanym z komputerem, żeby każdy miał ten sam).
2. Skopiujcie do niego zawartość `kontekst-szablony/`. **`AGENTS.md` musi leżeć w głównym folderze**: Codex czyta go automatycznie na starcie każdej rozmowy.
3. Otwórzcie Codexa w tym folderze (w aplikacji: wybierz folder; w terminalu: wejdź do folderu i wpisz `codex`).
4. Uruchomcie prompty z `prompty-wywiad.md`: najpierw firma, potem klient i jeden produkt. Codex zapisuje pliki w folderze.
5. Każda kolejna rozmowa w tym folderze zna już firmę i produkty.

## Skill meta-copy w Codexie
1. Skopiujcie folder `meta-copy` do `~/.codex/skills/` (na Windowsie: `C:\Users\NAZWA\.codex\skills\`). Jeśli folderu `skills` nie ma, utwórzcie go.
2. Uruchomcie Codexa ponownie.
3. W rozmowie wpiszcie `$meta-copy wanienka składana` albo „użyj skilla meta-copy dla wanienki składanej”.

Jeśli Codex nie widzi skilla, wystarczy napisać: „Przeczytaj plik meta-copy/SKILL.md i działaj według niego dla [produkt]”.

## Connector Meta Ads
Odczyt konta reklamowego i Biblioteki reklam robimy na koncie Claude z connectorem Meta (`mcp.facebook.com/ads`). 11.09 ten connector w Codexie nie zadziałał, w Claude tak.

## Claude zamiast Codexa
Ten sam folder działa w Claude Code: skopiujcie `AGENTS.md` jako `CLAUDE.md`. Skill `meta-copy` wgrywacie w Claude jako ZIP (`meta-copy.zip`) w Ustawieniach, w sekcji Skille.
