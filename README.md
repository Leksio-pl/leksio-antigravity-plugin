# Leksio dla Antigravity

Wtyczka łączy Google Antigravity z bazą prawną SIP Leksio: aktami prawnymi, orzeczeniami sądów,
interpretacjami podatkowymi i dokumentami organów z oficjalnych źródeł (Dziennik Ustaw, CBOSA, SAOS,
EUREKA, ZUS, KNF, UODO oraz rejestr klauzul niedozwolonych UOKiK). Agent wyszukuje dokumenty po
problemie, sygnaturze albo oznaczeniu przepisu, czyta sentencję i uzasadnienie, sprawdza brzmienie
przepisu na wskazany dzień i podaje każde źródło z linkiem do sip.leksio.pl.

## Co zawiera

- **Serwer Leksio** (`https://mcp.leksio.pl/sip`, w Antigravity serwer `sip`): 9 narzędzi tylko do
  odczytu, logowanie kontem Leksio przez OAuth.
- **Zasady `rules/AGENTS.md`**: krótkie zasady researchu, ochrony danych i cytowania.
- **Umiejętność `research-prawny`**: pełna metoda pracy ze źródłami, włączana, gdy zadanie jej dotyczy.
- **Umiejętności uruchamiane przez użytkownika**: `/research-podatkowy`, `/przepis-na-dzien`,
  `/linia-orzecznicza`, `/sprawdz-cytaty`. Każda zużywa research, dlatego agent nie włącza ich sam.

## Wymagania

- Google Antigravity (aplikacja, IDE albo CLI `agy`).
- Konto Leksio z potwierdzonym adresem e-mail i akceptacja
  [Zasad Leksio MCP](https://leksio.pl/zasady/leksio-mcp) przy pierwszym połączeniu.
- Pula researchy wynika z planu konta: darmowe 5, SIP Pro 50, SIP Pro+ 150 na okres puli. Okres trwa
  miesiąc od rocznicy założenia konta (konto darmowe) albo od odnowienia okresu rozliczeniowego (SIP Pro,
  SIP Pro+). Jeden research obejmuje do 50 wywołań narzędzi.

## Instalacja

Antigravity CLI:

```
agy plugin install https://github.com/Leksio-pl/leksio-antigravity-plugin
```

Aplikacja i IDE: skopiuj zawartość repozytorium do katalogu `~/.gemini/config/plugins/leksio`
(dla wszystkich projektów) albo `.agents/plugins/leksio` w projekcie.

## Logowanie

W Customizations otwórz wtyczkę Leksio, kartę Accounts, i przy `sip` wybierz Sign in. Przeglądarka
otworzy logowanie Leksio i ekran zgody „Leksio dla Google Antigravity”. Po zalogowaniu skopiuj kod
z przeglądarki, wklej go w polu „Paste code” i wybierz Submit. Do wklejenia kodu zostań na karcie
Accounts: po przejściu na inny ekran logowanie trzeba zacząć od nowa. Potem zadaj pytanie, np.
„Jakie było brzmienie art. 15 ust. 1 ustawy o CIT na 1 stycznia 2024 r.?”. Antigravity pyta o zgodę
przy pierwszym użyciu każdego narzędzia Leksio; możesz zezwolić na nie w całej rozmowie.

Odłączenie: usunięcie wtyczki kasuje ją z tego komputera, a panel Leksio MCP w koncie SIP Leksio
(https://sip.leksio.pl/konto/mcp) cofa dostęp dla wszystkich urządzeń.

## Prywatność i zakres

Leksio nie zapisuje treści pytań. Przechowuje dostawcę, znaczniki czasu, liczniki operacji
i identyfikatory pobranych dokumentów. Zasady wtyczki prowadzą agenta tak, by do narzędzi trafiało samo
zagadnienie prawne, bez danych osób i kontrahentów. Pytania i pobrane fragmenty przetwarza też model
wybrany w Antigravity, na warunkach usługi, z której korzysta użytkownik. Wyniki to materiał do analizy,
nie porada prawna. Szczegóły: [pomoc](https://leksio.pl/pomoc?temat=leksio-mcp),
[polityka prywatności](https://leksio.pl/zasady/prywatnosc).

## Licencja

Pliki wtyczki są dostępne na licencji Apache 2.0 (`LICENSE`). Licencja nie obejmuje usługi Leksio,
bazy SIP Leksio, serwera MCP ani nazwy i logo Leksio (`NOTICE`). Google i Antigravity to znaki towarowe
Google LLC; nazwy występują wyłącznie jako opis zgodności.

---

# Leksio for Antigravity (English)

This plugin connects Google Antigravity to the Leksio SIP database of Polish legal acts, court
judgments, tax rulings and regulator documents from official sources (ZUS, the Polish Financial
Supervision Authority KNF, the data protection authority UODO and the UOKiK register of unfair contract
terms). The agent searches by topic, case number or statutory citation, reads the disposition and
reasoning, checks the wording of a provision as at a given date and cites every source with a link to
sip.leksio.pl.

It bundles the Leksio server (`sip`, 9 read-only tools, OAuth sign-in with a Leksio account),
short rules in `rules/AGENTS.md`, the `research-prawny` skill with the full research and citation method,
and four user-invoked skills for tax research, provision-on-date checks, case-law lines and citation
verification. Install with `agy plugin install https://github.com/Leksio-pl/leksio-antigravity-plugin`
or copy the repository to `~/.gemini/config/plugins/leksio`, then open the Leksio plugin in Customizations,
choose Sign in next to `sip` on the Accounts tab and paste the code shown in the browser (stay on that tab
until you paste it). A verified Leksio
account and acceptance of the Leksio MCP Rules are required. Monthly research allowance: free 5,
SIP Pro 50, SIP Pro+ 150; each research includes up to 50 tool calls. Leksio does not store the content
of your questions; the rules keep personal and counterparty data out of tool calls. Results are not
legal advice.

The plugin files are licensed under Apache 2.0 (`LICENSE`); the Leksio service, database, MCP server,
name and logo are not (`NOTICE`). Google and Antigravity are trademarks of Google LLC, used only to
describe compatibility.

Operated by Leksio sp. z o.o. Support: https://leksio.pl/pomoc?temat=leksio-mcp
