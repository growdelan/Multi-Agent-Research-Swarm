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

## 🟢 Typowy problem zawodowy

To jest zalecany **domyślny preset**.

| Etap                          | Model        | Effort     |
| ----------------------------- | ------------ | ---------- |
| Orchestrator / główna sesja   | **Sol**      | **Medium** |
| FAZA 2 — C + F                | **Sol**      | **Medium** |
| FAZA 2 — A + B + D + E        | **Terra**    | **Medium** |
| Critic 1 — Adversarial        | **Sol**      | **High**   |
| Critic 2 — Comparative        | **Terra**    | **High**   |
| FAZA 4 — 2–4 Follow-up Agents | **Terra**    | **High**   |
| FAZA 5 — Verification         | **Sol**      | **High**   |
| FAZA 6 — Final Synthesis      | główna sesja | **Medium** |

Używaj tej konfiguracji do większości problemów zawodowych, technicznych, organizacyjnych i decyzyjnych.

---

## 🔴 Trudny problem badawczy

Preset przeznaczony dla problemów, gdzie **jakość rozwiązania jest znacznie ważniejsza od kosztu obliczeń**.

| Etap                          | Model        | Effort           |
| ----------------------------- | ------------ | ---------------- |
| Orchestrator / główna sesja   | **Astra**    | **High**         |
| FAZA 2 — C + F                | **Sol**      | **High**         |
| FAZA 2 — A + B + D + E        | **Terra**    | **High**         |
| Critic 1 — Adversarial        | **Astra**    | **High**         |
| Critic 2 — Comparative        | **Sol**      | **High**         |
| FAZA 4 — 2–4 Follow-up Agents | **Sol**      | **High**         |
| FAZA 5 — Verification         | **Astra**    | **xHigh**        |
| FAZA 6 — Final Synthesis      | główna sesja | **High / xHigh** |

Używaj go do trudnych problemów naukowych, matematycznych, badawczych lub szczególnie ważnych problemów strategicznych.

---

# Jak używać?

1. Otwórz nową sesję Codexa.
2. Wybierz model i effort dla głównej sesji.
3. Uzupełnij w promptcie:

```text
[PROBLEM]
[CONTEXT]
[CEL]
```

4. Ustaw modele dla poszczególnych faz.
5. Uruchom prompt.

Orchestrator zajmie się dalszym podziałem pracy.

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
