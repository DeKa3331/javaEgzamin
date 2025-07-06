Java AWT, Swing i JavaFX — podstawy i porównanie
1. Java AWT (Abstract Window Toolkit)
Najstarszy framework GUI w Javie.

Bazuje na natywnych komponentach systemu operacyjnego (np. Windows, macOS).

Prosty, lekki, ale ma ograniczoną liczbę komponentów i mniej nowoczesny wygląd.

Dobrze sprawdza się w prostych aplikacjach.

2. Java Swing
Rozszerzenie AWT, napisane w całości w Javie (nie bazuje na natywnych komponentach).

Bogaty zestaw komponentów: tabele, drzewa, panele, zaawansowane kontrolki.

Umożliwia pełną kontrolę nad wyglądem (skórki, personalizacja).

Popularny i szeroko stosowany, ale starszy i mniej nowoczesny niż JavaFX.

3. JavaFX
Najnowszy framework GUI, zaprojektowany jako następca Swing.

Obsługuje nowoczesne UI: multimedia, animacje, grafikę 2D/3D, CSS do stylowania.

Umożliwia tworzenie aplikacji na desktop, web i częściowo na mobile.

Posiada FXML — język XML do definiowania interfejsu, oddziela UI od logiki.

Wysoka wydajność dzięki akceleracji sprzętowej.


| Cecha                   | AWT                           | Swing                                | JavaFX                                        |
| ----------------------- | ----------------------------- | ------------------------------------ | --------------------------------------------- |
| **Data powstania**      | Najstarszy (Java 1.0)         | Średni (Java 1.2)                    | Najnowszy (Java 8 i dalej)                    |
| **Rodzaj komponentów**  | Natywne systemowe             | W 100% Java                          | W 100% Java, z multimedialnymi i nowoczesnymi |
| **Zestaw komponentów**  | Podstawowy                    | Rozbudowany                          | Bardzo bogaty, nowoczesny                     |
| **Wygląd i stylizacja** | Natychmiastowy wygląd systemu | Możliwość stylizacji, ale starsze UI | Stylowanie przez CSS, animacje, multimedia    |
| **Wydajność**           | Lekki, prosty                 | Dobra dla złożonych UI               | Wysoka dzięki akceleracji GPU                 |
| **Zastosowania**        | Proste aplikacje              | Aplikacje biznesowe, desktop         | Nowoczesne aplikacje desktop/web/mobile       |
| **Łatwość nauki**       | Najprostszy                   | Średni poziom                        | Może wymagać nauki CSS i FXML                 |
| **Obsługa multimedia**  | Brak                          | Ograniczona                          | Pełna, w tym audio, wideo, 3D                 |


Przykład "Hello World"
AWT: Frame, Label

Swing: JFrame, JLabel

JavaFX: Stage, Scene, Label

Podsumowanie
AWT — prosty, lekki, ale przestarzały.

Swing — wszechstronny, stabilny, nadal szeroko stosowany.

JavaFX — nowoczesny, polecany do nowych projektów z bogatym UI i multimediami.
