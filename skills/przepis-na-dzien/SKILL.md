---
name: przepis-na-dzien
description: "Brzmienie przepisu ustawy obowiązujące w podanym dniu, z porównaniem do innej daty. Uruchamia ją użytkownik, bo zużywa research."
disable-model-invocation: true
---

Użycie: `/przepis-na-dzien <przepis, np. art. 15 ust. 1 CIT> <dzień RRRR-MM-DD> [druga data do porównania]`

Ustal brzmienie przepisu na dzień wskazany przez użytkownika:

[pytanie albo tekst, który użytkownik wpisał razem z wywołaniem tej umiejętności (jeśli go brak, poproś o nie jednym zdaniem)]

Kroki: 1) lookup_citation, żeby znaleźć akt i jednostkę; 2) get_act_wording z documentId, articlePath (np. art:15) i datą; podaj status complete/partial i okres obowiązywania (from, until) oraz źródła publikacji;
Jeśli użytkownik podał drugą datę, powtórz get_act_wording na ten dzień i wskaż różnice w treści (dodane, usunięte, zmienione ustępy) oraz akty zmieniające z historii (includeHistory: true). Bez drugiej daty:
3) jeśli przepis zmieniał się w ostatnich latach (includeHistory: true), wskaż daty zmian.
Cytuj brzmienie dosłownie z odpowiedzi narzędzia. Jeśli brzmienie jest niedostępne (WORDING_UNAVAILABLE, WORDING_UNSUPPORTED), powiedz to wprost i pokaż tekst bieżący z zastrzeżeniem.

Narzędzia Leksio są na serwerze sip wtyczki Leksio. Zacznij od start_research z nowym requestKey i przekazuj research.id jako researchId do każdego narzędzia.
