| Lp. | `extends` (dziedziczenie klas)                                                                  | `implements` (implementacja interfejsów)                                                  |
| --- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| 1.  | Klasa może dziedziczyć po jednej klasie nadrzędnej (single inheritance).                        | Klasa może implementować dowolną liczbę interfejsów (multiple inheritance of types).      |
| 2.  | Podklasa dziedziczy właściwości i metody klasy nadrzędnej.                                      | Klasa musi zaimplementować wszystkie metody interfejsu (chyba że sama jest abstrakcyjna). |
| 3.  | Klasa dziedzicząca może nadpisywać (override) metody klasy nadrzędnej.                          | Metody interfejsu są domyślnie abstrakcyjne i nie mają implementacji (do Javy 8).         |
| 4.  | Słowo kluczowe `extends` używane jest również, gdy interfejs dziedziczy po innych interfejsach. | Słowo kluczowe `implements` jest używane tylko przez klasy do implementacji interfejsów.  |
| 5.  | Brak wielodziedziczenia klas — klasa może mieć tylko jedną bezpośrednią klasę bazową.           | Możliwość implementacji wielu interfejsów przez jedną klasę.                              |
| 6.  | Konstruktor klasy nadrzędnej można wywołać w konstruktorze podklasy za pomocą `super()`.        | Interfejsy nie mają konstruktorów.                                                        |

Szczegóły dotyczące extends
Służy do dziedziczenia implementacji i stanu (pól, metod) z klasy bazowej.

Pozwala na rozszerzenie lub modyfikację funkcjonalności klasy bazowej.

Przykład:
```
class One {
    public void methodOne() {
        System.out.println("Metoda z klasy One");
    }
}

class Two extends One {
    public static void main(String[] args) {
        Two t = new Two();
        t.methodOne();  // dziedziczenie metody
    }
}
```
Klasa może rozszerzać tylko jedną klasę nadrzędną ze względu na uniknięcie problemów z wielodziedziczeniem.
Szczegóły dotyczące implements
Służy do implementacji metod zadeklarowanych w interfejsie, który definiuje tylko sygnatury metod (pełna abstrakcja).

Klasa implementująca interfejs musi dostarczyć definicje wszystkich metod interfejsu (chyba że jest abstrakcyjna).

Przykład implementacji wielu interfejsów:
```
interface One {
    void methodOne();
}

interface Two {
    void methodTwo();
}

class Three implements One, Two {
    public void methodOne() {
        System.out.println("Implementacja methodOne");
    }

    public void methodTwo() {
        System.out.println("Implementacja methodTwo");
    }
}
```
Interfejsy mogą rozszerzać wiele innych interfejsów za pomocą extends.

| Cecha                             | `extends` (dziedziczenie klas)                  | `implements` (implementacja interfejsów)                       |
| --------------------------------- | ----------------------------------------------- | -------------------------------------------------------------- |
| Liczba dziedziczonych typów       | Jedna klasa bazowa                              | Dowolna liczba interfejsów                                     |
| Co dziedziczone / implementowane  | Implementacja i stan (metody i pola)            | Deklaracje metod (od Javy 8 też domyślne i statyczne)          |
| Nadpisywanie metod                | Tak                                             | Implementacja obowiązkowa wszystkich metod interfejsu          |
| Konstruktor                       | Możliwość wywołania konstruktora klasy bazowej  | Brak konstruktorów w interfejsach                              |
| Wielodziedziczenie                | Nie (Java nie wspiera wielodziedziczenia klas)  | Tak (klasa może implementować wiele interfejsów)               |
| Dziedziczenie między interfejsami | Tak (interfejs może rozszerzać inne interfejsy) | Nie (interfejs implementuje inne interfejsy) — używa `extends` |


# notatki
Extends vs Implements w Javie
Ostatnia aktualizacja: 27 marzec 2025

W Javie słowo kluczowe extends jest używane do dziedziczenia wszystkich właściwości i metod klasy nadrzędnej, natomiast słowo kluczowe implements służy do implementacji metod zdefiniowanych w interfejsie.

| Lp. | Extends                                                                                                                | Implements                                                                           |
| --- | ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| 1.  | Używając słowa „extends” klasa może dziedziczyć po innej klasie, lub interfejs może dziedziczyć po innych interfejsach | Używając słowa „implements” klasa może implementować interfejs                       |
| 2.  | Podklasa rozszerzająca klasę nadrzędną nie musi nadpisywać wszystkich metod klasy nadrzędnej                           | Klasa implementująca interfejs musi zaimplementować wszystkie metody tego interfejsu |
| 3.  | Klasa może rozszerzać tylko jedną klasę nadrzędną                                                                      | Klasa może implementować dowolną liczbę interfejsów jednocześnie                     |
| 4.  | Interfejs może rozszerzać dowolną liczbę innych interfejsów                                                            | Interfejs może rozszerzać inne interfejsy, ale nie może ich implementować            |


Słowo kluczowe extends w Javie
W Javie słowo kluczowe extends służy do oznaczenia, że definiowana klasa pochodzi z klasy bazowej za pomocą dziedziczenia. Innymi słowy, extends służy do rozszerzenia funkcjonalności klasy rodzica w klasie potomnej. W Javie nie ma wielodziedziczenia klas ze względu na możliwość powstawania niejednoznaczności, dlatego klasa może rozszerzać tylko jedną klasę.

Przykład: Poniżej przykład użycia słowa kluczowego extends w Javie:
```
class One {
    public void methodOne() {
        // jakaś funkcjonalność
    }
}

class Two extends One {
    public static void main(String args[]) {
        Two t = new Two();

        // Wywołanie metody methodOne
        t.methodOne();
    }
}
```
Uwaga: Klasa może rozszerzać jedną klasę oraz implementować dowolną liczbę interfejsów jednocześnie.

Słowo kluczowe implements w Javie
W Javie słowo kluczowe implements służy do implementacji interfejsu. Interfejs to specjalny typ klasy, który reprezentuje pełną abstrakcję i zawiera tylko metody abstrakcyjne (bez implementacji). Aby korzystać z metod interfejsu, klasa musi go „zaimplementować” za pomocą słowa implements i dostarczyć implementację wszystkich metod tego interfejsu. Ponieważ interfejs nie zawiera implementacji metod, klasa może implementować wiele interfejsów naraz.

Przykład: Poniżej przykład użycia słowa kluczowego implements w Javie:
```
// Definicja interfejsu One
interface One {
    public void methodOne();
}

// Definicja drugiego interfejsu Two
interface Two {
    public void methodTwo();
}

// Klasa implementująca oba interfejsy
class Three implements One, Two {
    public void methodOne() {
        // Implementacja metody
    }

    public void methodTwo() {
        // Implementacja metody
    }
}
```
Uwaga: Interfejs może rozszerzać dowolną liczbę innych interfejsów jednocześnie.
