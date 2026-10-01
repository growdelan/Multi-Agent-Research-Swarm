# Multi-Agent Research Swarm

Prosty prompt do rozwiązywania problemów przy pomocy **zespołu współpracujących agentów AI** zamiast pojedynczego modelu szukającego jednej odpowiedzi.

System dzieli problem na kilka niezależnych kierunków, porównuje rozwiązania, próbuje je podważyć, prowadzi drugą rundę badań i na końcu niezależnie weryfikuje najlepszą odpowiedź.

Można go używać zarówno do zwykłych problemów zawodowych, jak i znacznie trudniejszych problemów badawczych.

---

## Jak działa?

W skrócie:

**Problem → 6 niezależnych podejść → 2 krytyków → 2–4 follow-up agentów → weryfikacja → końcowa synteza**

Główna sesja Codexa pełni rolę **Orchestratora** i zarządza całym procesem.

---

## Kiedy warto go użyć?

Najlepiej sprawdza się, gdy problem:

* ma kilka możliwych rozwiązań;
* wymaga podjęcia ważnej decyzji;
* jest niejasny lub złożony;
* wymaga porównania kilku podejść;
* może zawierać ukryte ryzyka;
* skorzysta na niezależnej krytyce rozwiązania.

### Przykłady

**Zwykła praca**

> Mamy problem z procesem obsługi klienta. Gdzie jest wąskie gardło i jak najlepiej przebudować proces?

> Firma chce obniżyć koszty operacyjne o 15%, ale bez pogorszenia jakości usług. Jak to zrobić?

> Musimy wybrać najlepszy sposób wdrożenia AI do naszego działu.

**Codzienne decyzje**

> Mam kilka możliwych sposobów rozwiązania problemu i nie wiem, który będzie najlepszy.

> Chcę przeanalizować dużą decyzję, jej ryzyka i możliwe alternatywy.

**IT**

> Zaprojektuj najlepszą architekturę systemu dla podanych wymagań.

> Znajdź źródło problemu wydajnościowego i najlepszą metodę jego rozwiązania.

> Porównaj kilka możliwych technologii i wybierz najlepszą.

**Badania**

> Zbadaj problem, dla którego nie znamy jeszcze oczywistego rozwiązania.

> Przetestuj kilka konkurencyjnych hipotez i spróbuj znaleźć kontrprzykłady.

---

# Konfiguracja modeli

Prompt pozwala określić osobno modele i reasoning effort dla poszczególnych etapów.

**Aktualizacja: 1 października 2026, po DevDay 2026.** Używaj pełnych identyfikatorów modeli zamiast samych nazw „Sol”, „Terra” i „Astra”:

| Model | Identyfikator | Rola w tym swarmie |
| --- | --- | --- |
| GPT-6.1 Sol | `gpt-6.1-sol` | Główna praca, otwarta eksploracja, krytyka i rozwijanie rozwiązań |
| GPT-6 Luna | `gpt-6-luna` | Prostsze, jasno określone zadania pomocnicze |
| GPT-6 Astra | `gpt-6-astra` | Koordynacja, krytyka i weryfikacja najtrudniejszych badań |

Dobór ról poniżej jest rekomendacją dla tego promptu, nie wynikiem benchmarku. OpenAI zaleca GPT-6.1 Sol do złożonej pracy agentowej, Lunę do wąskich, powtarzalnych zadań, a Astrę do najbardziej wymagających problemów. Dlatego dawne role Terry dzielimy między Lunę i Sol zależnie od trudności; nie zakładamy zamienności tych modeli.

Nie wszystkie starsze modele zostały wycofane: GPT-5.6 Terra pozostaje dostępna podczas wdrażania nowych modeli. Dostępność zależy od konta, klienta i ustawień organizacji. Sprawdź model picker w swojej sesji; dostępność modelu w API nie gwarantuje dostępu w Codexie z logowaniem ChatGPT. Źródło: [modele w Codexie i ChatGPT Work](https://learn.chatgpt.com/docs/models).

## 🟢 Typowy problem zawodowy

To jest zalecany **domyślny preset**.

| Etap | Model | Effort |
| --- | --- | --- |
| Orchestrator / główna sesja | `gpt-6.1-sol` | `medium` |
| FAZA 2 — B + C + D + F | `gpt-6.1-sol` | `medium` |
| FAZA 2 — A + E | `gpt-6-luna` | `high` |
| Critic 1 — Adversarial | `gpt-6.1-sol` | `high` |
| Critic 2 — Comparative | `gpt-6.1-sol` | `high` |
| FAZA 4 — 2–4 Follow-up Agents | `gpt-6.1-sol` | `high` |
| FAZA 5 — Verification | `gpt-6.1-sol` | `high` |
| FAZA 6 — Final Synthesis | główna sesja (`gpt-6.1-sol`) | `medium` |

Używaj tej konfiguracji do większości problemów zawodowych, technicznych, organizacyjnych i decyzyjnych.

Luna w rolach A i E ma sens, gdy koordynator może zlecić konkretną analizę standardowego rozwiązania lub optymalizację z jasnymi kryteriami. Jeżeli te zadania wymagają otwartych badań, wielu niepewnych założeń lub złożonego rozumowania, ustaw dla nich `gpt-6.1-sol` z `medium` albo `high`. Agenci B i D oraz obaj krytycy korzystają z Sol, ponieważ szukanie alternatyw, kontrprzykładów i rozstrzyganie sprzeczności nie są prostymi zadaniami pomocniczymi.

---

## 🔴 Trudny problem badawczy

Preset przeznaczony dla problemów, gdzie **jakość rozwiązania jest znacznie ważniejsza od kosztu obliczeń**.

| Etap | Model | Effort |
| --- | --- | --- |
| Orchestrator / główna sesja | `gpt-6-astra` | `high` |
| FAZA 2 — B + C + D + F | `gpt-6.1-sol` | `high` |
| FAZA 2 — A + E | `gpt-6.1-sol` | `high` |
| Critic 1 — Adversarial | `gpt-6-astra` | `high` |
| Critic 2 — Comparative | `gpt-6.1-sol` | `high` |
| FAZA 4 — 2–4 Follow-up Agents | `gpt-6.1-sol` | `high` |
| FAZA 5 — Verification | `gpt-6-astra` | `xhigh` |
| FAZA 6 — Final Synthesis | główna sesja (`gpt-6-astra`) | `high` |

Używaj go do trudnych problemów naukowych, matematycznych, badawczych lub szczególnie ważnych problemów strategicznych.

`medium`, `high` i `xhigh` są identyfikatorami poziomów reasoning effort; `xhigh` odpowiada Extra High w interfejsie. Wszystkie trzy modele obsługują poziomy użyte w tabelach, ale kontrolki dostępne w kliencie mogą zależeć od konta. Wyższy effort zwiększa czas i zużycie tokenów. To punkty startowe do oceny na własnych zadaniach.

Źródła: [GPT-6.1 Sol](https://developers.openai.com/api/docs/models/gpt-6.1-sol), [GPT-6 Luna](https://developers.openai.com/api/docs/models/gpt-6-luna), [GPT-6 Astra](https://developers.openai.com/api/docs/models/gpt-6-astra), [modele i reasoning subagentów](https://learn.chatgpt.com/docs/agent-configuration/subagents#choosing-models-and-reasoning).

---

# Jak używać?

1. Otwórz nową sesję Codexa.
2. Wybierz w interfejsie model i effort dla głównej sesji zgodnie z wybranym presetem. Sam tekst promptu nie przełącza modelu koordynatora.
3. Skopiuj [Prompt.md](Prompt.md) i uzupełnij:

```text
[PROBLEM]
[CONTEXT]
[CEL]
```

4. Prompt ma już wpisany preset typowego problemu zawodowego. Dla trudnego problemu badawczego zmień model i effort koordynatora oraz ustawienia poszczególnych faz zgodnie z drugą tabelą.
5. Uruchom prompt.

Orchestrator zajmie się dalszym podziałem pracy.

W promptcie jawnie żądamy delegowania do subagentów i wskazujemy ich modele. Ustawienia trzeba zastosować przy ich uruchamianiu; bez jawnej konfiguracji subagent może odziedziczyć model i effort rodzica. Jeżeli środowisko nie obsługuje wybranego modelu, effortu lub liczby równoległych agentów, koordynator powinien podać faktycznie użyte ustawienia i ograniczenia. Przy mniejszym limicie równoległości uruchom agentów partiami, zachowując niezależność pierwszej rundy.

---

# Kiedy NIE używać?

Swarm jest niepotrzebny, jeśli zadanie jest proste i ma oczywistą odpowiedź.

Nie warto uruchamiać go do rzeczy takich jak:

> „Popraw ten regex.”

> „Dodaj pole do tego JSON-a.”

> „Przetłumacz ten tekst.”

> „Wyjaśnij mi, co robi ta funkcja.”

> „Zmień kolor przycisku.”

W takich przypadkach pojedynczy agent będzie szybszy i tańszy.

---

## Prosta zasada

**Jeżeli potrzebujesz wykonania zadania → jeden agent.**

**Jeżeli potrzebujesz znalezienia najlepszego rozwiązania → Multi-Agent Research Swarm.**

Im większa niepewność, liczba możliwych dróg i koszt błędnej decyzji, tym bardziej użyteczny staje się swarm.

---

## Uwaga

Podane modele i poziomy reasoning effort są sugerowanymi presetami, a nie wymaganiem systemu.

Wraz z pojawianiem się nowych modeli konfigurację można swobodnie zmieniać bez zmiany samej architektury promptu.
