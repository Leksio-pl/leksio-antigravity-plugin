---
name: linia-orzecznicza
description: "Linia orzecznicza w kwestii prawnej: stanowiska sądów, rozbieżności i chronologia. Uruchamia ją użytkownik, bo zużywa research."
disable-model-invocation: true
---

Użycie: `/linia-orzecznicza <kwestia prawna> [przepis, sądy, rok początkowy]`

Opracuj linię orzeczniczą w kwestii wskazanej przez użytkownika:

[pytanie albo tekst, który użytkownik wpisał razem z wywołaniem tej umiejętności (jeśli go brak, poproś o nie jednym zdaniem)]

Jeśli użytkownik podał przepis, użyj lookup_citation, potem get_provision_materials z category: "judgments". Sądy przekaż filtrem issuingBodyCodes albo courtIds w search_legal, rok początkowy filtrem issuedFrom.
Kroki: 1) search_legal z kinds: ["judgment"], sortowanie newest, kilka stron; 2) przeczytaj uzasadnienia kluczowych orzeczeń (read_document_text), zwłaszcza NSA i uchwał; 3) pogrupuj stanowiska, podaj chronologię, wskaż orzeczenia odmienne i to, czy linia jest ugruntowana; 4) zaznacz, które wyroki WSA mogą być nieprawomocne. Każde orzeczenie: sąd, data, sygnatura, adres SIP. Stanowisko sądu podawaj z przeczytanej sentencji i uzasadnienia, nie z samego fragmentu wyniku.

Przed wywołaniem narzędzi usuń z zapytań dane osobowe i dane kontrahentów (imiona, nazwy firm, PESEL, NIP, numery umów i faktur); opisuj osoby i firmy przez rolę. Nazwy stron publikowanych orzeczeń (np. C-277/14 PPUH Stehcemp) zostaw bez zmian.
Narzędzia Leksio są na serwerze sip wtyczki Leksio. Zacznij od start_research z nowym requestKey i przekazuj research.id jako researchId do każdego narzędzia.
