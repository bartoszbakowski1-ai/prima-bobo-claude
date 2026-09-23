# AI w Prima Bobo: materiały ze szkolenia 23.09.2026

Prowadzący: Bartek Bąkowski. Materiały przygotowane pod **Codex** (tego używacie na co dzień). Te same pliki działają w Claude Code, ChatGPT i Claude.

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
