---
name: sprawdz-cytaty
description: "Sprawdza sygnatury, publikatory i przepisy z tekstu w bazie SIP Leksio. Uruchamia ją użytkownik, bo zużywa research."
disable-model-invocation: true
---

Użycie: `/sprawdz-cytaty <tekst z cytowaniami do sprawdzenia>`

Sprawdź każde cytowanie w poniższym tekście w SIP Leksio. Wyciągnij sygnatury orzeczeń, numery interpretacji, publikatory (Dz.U., M.P.) i przepisy (art., §, ust., pkt z nazwą aktu). Dla każdego wywołaj lookup_citation. Gdy dokument istnieje, porównaj datę, sąd albo organ i przypisane mu stanowisko z tym, co twierdzi tekst. Stanowisko sprawdź w treści dokumentu przez read_document_text (section: disposition, uzasadnienie albo find z frazą z tekstu).
Numer wpisu rejestru klauzul niedozwolonych UOKiK, decyzję Prezesa UODO albo pismo KNF, których lookup_citation nie rozpozna, szukaj przez search_legal z sourceCodes: ["UOKIK"], ["UODO"] albo ["KNF"] i porównaj numer, datę oraz organ.
Zwróć tabelę: cytowanie | wynik (potwierdzone / brak w SIP / rozbieżne) | co się zgadza albo nie zgadza | adres SIP. Brak w SIP nie dowodzi, że dokument nie istnieje; zaznacz to. Nie poprawiaj cytowań zgadywaniem.

Narzędzia Leksio są na serwerze sip wtyczki Leksio. Zacznij od start_research z nowym requestKey i przekazuj research.id jako researchId do każdego narzędzia.

Tekst do sprawdzenia:
[pytanie albo tekst, który użytkownik wpisał razem z wywołaniem tej umiejętności (jeśli go brak, poproś o nie jednym zdaniem)]
