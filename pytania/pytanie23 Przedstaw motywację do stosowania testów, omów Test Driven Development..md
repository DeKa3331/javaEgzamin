Oto zwięzła, czytelna notatka:

🩺 Motywacja do stosowania testów
✅ Wczesne wykrywanie błędów – testy pozwalają wykryć błędy zaraz po ich wprowadzeniu, co zmniejsza koszty naprawy.
✅ Bezpieczne wprowadzanie zmian (refaktoryzacja) – posiadanie testów daje pewność, że zmiana kodu nie popsuje istniejącej funkcjonalności.
✅ Dokumentacja zachowania kodu – testy opisują, co kod ma robić, pełniąc rolę żywej dokumentacji.
✅ Wymuszają modularność – pisanie testowalnego kodu sprzyja dobrym praktykom projektowym, jak niska zależność między komponentami.
✅ Zwiększają pewność działania – zmniejszają ryzyko awarii na produkcji.
✅ Ułatwiają rozwój zespołowy – testy jasno pokazują, jeśli ktoś przypadkowo złamie istniejącą funkcję.

🚦 Test Driven Development (TDD)
TDD (Test Driven Development) – to technika tworzenia oprogramowania, w której piszemy testy zanim napiszemy kod produkcyjny.

🔹 Etapy TDD:
![image](https://github.com/user-attachments/assets/120a9df9-f50a-428f-ba5d-dd95f4139cf5)

1️⃣ Red – napisz test jednostkowy opisujący nową funkcję lub poprawkę (test początkowo nie przechodzi).
2️⃣ Green – napisz minimalny kod produkcyjny, aby test przeszedł.
3️⃣ Refactor – popraw kod, zachowując przechodzenie testów (czytelność, usunięcie duplikacji).

🔄 Proces powtarzany jest cyklicznie, dla kolejnych funkcji.

📌 Korzyści TDD
✅ Lepsze zrozumienie wymagań – zmusza do przemyślenia, jak dokładnie funkcja powinna działać, zanim ją zaimplementujesz.
✅ Większe pokrycie testami – ponieważ testy są pisane od razu, system ma od początku automatyczne pokrycie testami.
✅ Łatwiejsza refaktoryzacja – szybki feedback, czy zmiany nie psują działania.
✅ Projektowanie modularne – wymusza pisanie kodu łatwego do testowania.

🚩 Podsumowanie
Testy zwiększają jakość, pewność działania i bezpieczeństwo zmian.

TDD wymusza pisanie testów przed kodem, co prowadzi do lepszego designu i wysokiego pokrycia testami.
