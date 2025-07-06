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
