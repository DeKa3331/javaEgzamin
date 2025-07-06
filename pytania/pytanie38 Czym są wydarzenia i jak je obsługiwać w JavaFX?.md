Co to są wydarzenia (events)?
Wydarzenia to sygnały informujące o zdarzeniach zachodzących w aplikacji, np. kliknięcie przycisku, ruch myszy, wpisanie tekstu, zmiana rozmiaru okna.

W JavaFX są podstawą interakcji użytkownika z GUI

Rodzaje wydarzeń w JavaFX
MouseEvent — kliknięcia, ruch myszy

KeyEvent — naciśnięcie klawisza

ActionEvent — np. kliknięcie przycisku

WindowEvent — zdarzenia okna (otwarcie, zamknięcie)

i inne...
Jak obsługiwać wydarzenia?
Dodanie nasłuchiwacza (EventHandler) do komponentu GUI

Metoda: node.setOnEventType(handler)

Przykład dla przycisku:
```
Button btn = new Button("Kliknij mnie");
btn.setOnAction(e -> {
    System.out.println("Przycisk został kliknięty");
});
```
Implementacja EventHandler (można jako lambda, anonimowa klasa lub osobna klasa)

Dodatkowe możliwości
Można obsługiwać różne typy zdarzeń na jednym komponencie (np. kliknięcie, ruch myszy)

Można zatrzymać propagację zdarzenia (event.consume())

Wydarzenia w JavaFX działają zgodnie z modelem propagacji zdarzeń:

Capturing (przechwytywanie) → Target (cel) → Bubbling (bąbelkowanie)

Podsumowanie
Wydarzenia to sposób komunikacji GUI z logiką programu w reakcji na działania użytkownika.

W JavaFX obsługa wydarzeń polega na przypisaniu handlera (metody lub lambda) do komponentu GUI.

To kluczowa część programowania interfejsów użytkownika.
