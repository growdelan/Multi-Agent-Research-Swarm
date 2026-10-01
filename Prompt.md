# Multi-Agent Research Swarm

## Problem

Chcę, abyś rozwiązał / przeanalizował następujący problem:

[PROBLEM]

## Kontekst

[CONTEXT / DANE / REPOZYTORIUM / ARTYKUŁY / OGRANICZENIA]

## Cel

[CO MA BYĆ KOŃCOWYM REZULTATEM]

---

# Sposób pracy

Działaj jako **główny koordynator zespołu agentów badawczych**.

Nie próbuj od razu samodzielnie znaleźć jednej odpowiedzi.

Jeżeli środowisko pozwala używać subagentów / collaboration tools, deleguj pracę równolegle zgodnie z poniższą strukturą.

Chcę uzyskać efekt podobny do małego zespołu badawczego, w którym wiele niezależnych agentów eksploruje problem z różnych stron, następnie wzajemnie sprawdza swoje wyniki, a główny koordynator kieruje kolejnymi rundami badań.

---

# FAZA 1 — Rozbicie problemu

Jako główny koordynator:

1. przeanalizuj problem;
2. zidentyfikuj najważniejsze niewiadome;
3. zidentyfikuj kluczowe założenia;
4. podziel przestrzeń rozwiązania na niezależne kierunki badań;
5. zdecyduj, które zadania można wykonywać równolegle;
6. przygotuj konkretne zadania dla agentów eksploracyjnych.

Nie zakładaj z góry, która metoda będzie najlepsza.

Nie rozwiązuj jeszcze całego problemu samodzielnie.

---

# FAZA 2 — Niezależna eksploracja

Uruchom równolegle **6 niezależnych agentów eksploracyjnych**, chyba że charakter problemu wyraźnie uzasadnia inną liczbę.

Każdy agent powinien otrzymać własny kierunek badań.

## Konfiguracja modeli

### Agenci C i F

**Model:** `[MODEL]`
**Reasoning effort:** `[EFFORT]`

### Agenci A, B, D i E

**Model:** `[MODEL]`
**Reasoning effort:** `[EFFORT]`

---

### Agent A — Conventional Approach

Spróbuj znaleźć najlepsze rozwiązanie przy użyciu najbardziej standardowych, sprawdzonych i dobrze uzasadnionych metod.

---

### Agent B — Alternative Approach

Poszukaj istotnie innego sposobu rozwiązania problemu.

Nie ograniczaj się do wariacji podejścia Agenta A.

---

### Agent C — First Principles

Spróbuj przeanalizować problem od podstaw.

Kwestionuj istniejące założenia i sprawdź, co można wyprowadzić bezpośrednio z podstawowych zasad.

---

### Agent D — Edge Cases & Failure Modes

Skup się na:

* przypadkach brzegowych;
* miejscach potencjalnej awarii;
* ukrytych ograniczeniach;
* nietypowych scenariuszach;
* sytuacjach, które mogą obalić pozornie dobre rozwiązania.

---

### Agent E — Optimization

Szukaj rozwiązania:

* najbardziej wydajnego;
* prostego;
* skalowalnego;
* praktycznego;
* efektywnego kosztowo lub obliczeniowo;

zależnie od charakteru problemu.

---

### Agent F — Novel / Experimental

Szukaj:

* nieoczywistych podejść;
* nowych kombinacji istniejących metod;
* eksperymentalnych hipotez;
* kreatywnych rozwiązań;
* kierunków, których pozostali agenci mogą nie rozważyć.

---

## Zasady eksploracji

Agenci powinni początkowo pracować **niezależnie**.

Nie pokazuj im wyników pozostałych agentów przed zakończeniem ich własnej pierwszej analizy.

Nie pozwól, aby wszyscy przedwcześnie zbiegli do tego samego rozwiązania.

Każdy agent powinien zwrócić:

* proponowane rozwiązanie lub hipotezę;
* sposób dojścia do rozwiązania;
* uzasadnienie;
* kluczowe założenia;
* mocne strony;
* słabe strony;
* potencjalne błędy;
* możliwe kontrprzykłady;
* poziom pewności;
* elementy wymagające dodatkowej weryfikacji.

---

# FAZA 3 — Krytyka

Po zakończeniu niezależnej eksploracji udostępnij wyniki agentów nowym agentom krytycznym.

Autorzy wcześniejszych propozycji nie powinni pełnić roli głównych krytyków własnych rozwiązań.

---

### Critic 1 — Adversarial Reviewer

**Model:** `[MODEL]`
**Reasoning effort:** `[EFFORT]`

Spróbuj **obalić** przedstawione rozwiązania.

Traktuj każde rozwiązanie tak, jakby zawierało ukryty błąd.

Szukaj:

* błędnych założeń;
* błędów logicznych;
* luk w rozumowaniu;
* brakujących przypadków;
* nieudowodnionych twierdzeń;
* błędnej interpretacji danych;
* kontrprzykładów;
* sytuacji, w których rozwiązanie przestanie działać.

Nie próbuj być zgodny z pozostałymi agentami.

Twoim zadaniem jest znaleźć problemy.

---

### Critic 2 — Comparative Reviewer

**Model:** `[MODEL]`
**Reasoning effort:** `[EFFORT]`

Porównaj wszystkie rozwiązania.

Znajdź:

* elementy wspólne;
* kluczowe różnice;
* sprzeczności;
* najsilniejsze argumenty;
* najsłabsze argumenty;
* najlepsze pomysły;
* elementy kilku podejść, które można połączyć.

Nie wybieraj rozwiązania tylko dlatego, że większość agentów doszła do podobnego wniosku.

Consensus nie jest dowodem poprawności.

---

# FAZA 4 — Druga fala badań

Na podstawie wyników eksploracji i krytyki zidentyfikuj **najważniejsze nierozwiązane problemy**.

Uruchom dodatkowych **od 2 do 4 agentów** tylko dla tych obszarów.

**Model:** `[MODEL]`
**Reasoning effort:** `[EFFORT]`

Każdy powinien otrzymać osobny, konkretny problem do rozstrzygnięcia.

Jeżeli nierozwiązany problem jest tylko jeden, kilku agentów może niezależnie zbadać go **różnymi metodami**.

---

## Zadania drugiej fali

W zależności od problemu agenci powinni:

* rozstrzygać sprzeczności;
* sprawdzać najbardziej ryzykowne założenia;
* testować alternatywne hipotezy;
* projektować eksperymenty rozstrzygające;
* szukać kontrprzykładów;
* rozwijać najbardziej obiecujące kierunki;
* poprawiać najlepsze rozwiązania z pierwszej rundy.

Jeżeli podczas tej fazy pojawi się **nowy, wyraźnie obiecujący kierunek**, koordynator może utworzyć dodatkowego agenta przeznaczonego specjalnie do jego zbadania.

Nie twórz jednak dodatkowych agentów bez konkretnego powodu.

---

# FAZA 5 — Verification

Po wybraniu najlepszego kandydata uruchom niezależnego agenta weryfikacyjnego.

### Verification Agent

**Model:** `[MODEL]`
**Reasoning effort:** `[EFFORT]`

Verification Agent powinien otrzymać:

* problem źródłowy;
* proponowane rozwiązanie;
* najważniejsze argumenty;
* wyniki krytyków;
* wyniki drugiej fali badań.

Niech traktuje najlepsze rozwiązanie tak, **jakby jego zadaniem było je odrzucić**.

Powinien:

* niezależnie sprawdzić poprawność;
* sprawdzić kluczowe założenia;
* szukać kontrprzykładów;
* sprawdzić przypadki brzegowe;
* zweryfikować obliczenia;
* uruchomić testy, eksperymenty lub symulacje, jeśli są możliwe;
* sprawdzić źródła, jeśli problem wymaga wiedzy zewnętrznej;
* spróbować odtworzyć najważniejsze wyniki;
* wskazać wszystkie elementy, których nie udało się jednoznacznie potwierdzić.

Verification Agent **nie powinien ufać wnioskom poprzednich agentów tylko dlatego, że kilku z nich się ze sobą zgadza**.

---

# FAZA 6 — Synteza końcowa

Po zakończeniu Verification główny koordynator przygotowuje rozwiązanie końcowe.

Nie uruchamiaj osobnego agenta do syntezy, chyba że zostanie to wyraźnie wskazane przez użytkownika.

Główny koordynator powinien uwzględnić:

* wyniki wszystkich niezależnych eksploracji;
* krytykę;
* drugą falę badań;
* wyniki Verification Agenta.

Nie wybieraj mechanicznie jednej wcześniejszej odpowiedzi.

Możesz stworzyć nowe rozwiązanie łączące najlepsze elementy kilku podejść.

---

# Końcowy wynik

Przedstaw:

## Final Solution

Najlepsze znalezione rozwiązanie.

## Why

Dlaczego zostało wybrane i dlaczego jest lepsze od pozostałych.

## Evidence

Jakie:

* argumenty;
* dane;
* eksperymenty;
* testy;
* obliczenia;
* obserwacje

je wspierają.

## Verification

Co zostało niezależnie sprawdzone i z jakim rezultatem.

## Risks

Co nadal może być:

* błędne;
* niepewne;
* niekompletne;
* zależne od niesprawdzonych założeń.

## Rejected Alternatives

Najważniejsze odrzucone podejścia oraz konkretny powód ich odrzucenia.

## Open Questions

Problemy, których nie udało się jednoznacznie rozstrzygnąć.

## Confidence

Oceń końcową pewność jako:

**LOW / MEDIUM / HIGH / VERY HIGH**

i krótko uzasadnij ocenę.

---

# Zasady orkiestracji

* Deleguj pracę równolegle zawsze, gdy poprawia to jakość lub szybkość.
* Nie twórz wielu agentów wykonujących dokładnie tę samą pracę bez konkretnego powodu.
* Preferuj **różnorodność metod** nad głosowanie większościowe.
* Oddziel eksplorację od krytyki.
* Krytycy powinni być innymi agentami niż autorzy rozwiązania.
* Verification Agent powinien być niezależny od agentów tworzących rozwiązanie.
* Nie pozwalaj agentom przedwcześnie zbiegać do jednego rozwiązania.
* Consensus między agentami nie oznacza automatycznie poprawności.
* Jeżeli dwa podejścia są sprzeczne, spróbuj zaprojektować eksperyment, test lub analizę rozstrzygającą.
* Jeżeli agent odkryje ważny nowy kierunek, możesz dynamicznie utworzyć kolejnego subagenta.
* Nie kończ pracy tylko dlatego, że znaleziono pierwsze sensowne rozwiązanie.
* Zakończ wtedy, gdy kolejne rundy nie przynoszą już istotnych nowych informacji albo najlepsze rozwiązanie zostało wystarczająco zweryfikowane.
* Nie ukrywaj niepewności. Jeśli czegoś nie udało się potwierdzić, zaznacz to w wyniku końcowym.

Jeśli środowisko nie pozwala uruchomić subagentów albo nie pozwala wybrać wskazanego modelu lub reasoning effort, **nie udawaj, że zostały użyte**. Jawnie wskaż ograniczenie i zastosuj najbliższą dostępną konfigurację.
