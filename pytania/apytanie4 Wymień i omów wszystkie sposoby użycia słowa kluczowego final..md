Sposoby użycia słowa kluczowego final w Javie
Słowo kluczowe final służy do ograniczenia możliwości modyfikacji klas, metod, zmiennych i parametrów. Zapewnia większe bezpieczeństwo i stabilność kodu, chroniąc przed niezamierzonymi zmianami.

1. final przy deklaracji klasy
Klasa oznaczona jako final nie może być dziedziczona.

Zapobiega to tworzeniu podklas i nadpisywaniu zachowania klasy.

Przykład:
```
public final class Cat { }
// public class BlackCat extends Cat { } // Błąd kompilacji!
```
Przykład z Javy: String jest klasą final – nie można jej rozszerzać.
final przy metodach
Metoda oznaczona jako final nie może być nadpisana w klasach potomnych.

Pozwala na zabezpieczenie kluczowej logiki metody przed modyfikacją.

Przykład:
```
public class Dog {
    public final void sound() { /* ... */ }
}

public class BlackDog extends Dog {
    public void sound() { } // Błąd: nie można nadpisać metody final
}
```
 final przy zmiennych (prymitywnych)
Zmienna final może być przypisana tylko raz – po inicjalizacji nie można zmieniać jej wartości.

Przykład:
```
final int i = 1;
i = 2; // Błąd: przypisanie do zmiennej final jest niedozwolone
```
. final przy referencjach do obiektów
Referencja oznaczona jako final nie może być zmieniona, aby wskazywać na inny obiekt.

Jednak można modyfikować stan obiektu, na który wskazuje referencja.

Przykład:
```
final Cat cat = new Cat();
cat.setWeight(5);   // OK, zmieniamy stan obiektu
cat = new Cat();    // Błąd: nie można zmienić referencji final
```
5. final przy polach klasy (stałe i write-once)
Pola oznaczone jako final muszą być zainicjalizowane tylko raz – mogą pełnić rolę stałych lub pól zapisywanych tylko raz.

Pola static final można inicjalizować przy deklaracji lub w bloku statycznym.

Pola instancyjne final można inicjalizować przy deklaracji, w bloku inicjalizacyjnym lub w konstruktorze.

Przykład:
```
static final int MAX_WIDTH = 999;
final int instanceValue;

public MyClass(int val) {
    instanceValue = val;  // inicjalizacja final pola w konstruktorze
}
```
final przy parametrach metody
Parametr oznaczony jako final nie może być zmieniony wewnątrz metody.

Zapewnia to, że wartość przekazana do metody pozostanie niezmienna.

Przykład:
```
public void methodWithFinalArg(final int x) {
    x = 1; // Błąd: nie można zmienić parametru final
}
```
| Zakres użycia             | Znaczenie                               | Przykład                       | Efekt                                           |
| ------------------------- | --------------------------------------- | ------------------------------ | ----------------------------------------------- |
| **Klasa**                 | Klasa **nie może być dziedziczona**     | `public final class Cat {}`    | Nie można utworzyć podklasy                     |
| **Metoda**                | Metoda **nie może być nadpisana**       | `public final void sound() {}` | Podklasa nie może nadpisać metody               |
| **Zmienna prymitywna**    | Wartość **nie może być zmieniona**      | `final int x = 5;`             | Próba zmiany powoduje błąd                      |
| **Referencja do obiektu** | Referencja **nie może zmienić obiektu** | `final Cat cat = new Cat();`   | Można zmieniać stan obiektu, ale nie referencję |
| **Pole klasy**            | Pole **musi być zainicjalizowane raz**  | `static final int MAX = 100;`  | Stała, wartość niezmienna                       |
| **Parametr metody**       | Parametr **nie może być zmieniony**     | `void foo(final int x) {}`     | Próba zmiany parametru – błąd                   |


Warto zapamiętać
final to narzędzie do zabezpieczenia kodu przed niepożądanymi zmianami.

Ogranicza elastyczność (np. uniemożliwia dziedziczenie lub nadpisanie metody), ale zwiększa bezpieczeństwo i przewidywalność działania.

Jest szeroko stosowane w bibliotekach standardowych Javy (np. String, Thread.isAlive()).

# notatki

Dziedziczenie pozwala nam na ponowne wykorzystanie istniejącego kodu, ale czasami musimy ograniczyć możliwość rozszerzania klas z różnych powodów. Słowo kluczowe final umożliwia dokładnie takie ograniczenie.

W tym materiale omówimy, co oznacza słowo final w kontekście klas, metod i zmiennych.

Klasy oznaczone jako final nie mogą być rozszerzane (dziedziczone). W bibliotekach standardowych Javy znajdziesz wiele klas oznaczonych jako final. Przykładem jest klasa String.

Wyobraź sobie sytuację, w której moglibyśmy dziedziczyć po klasie String, nadpisywać jej metody i zastępować wszystkie obiekty String instancjami naszej podklasy. W rezultacie operacje na obiektach String stałyby się nieprzewidywalne, co jest niedopuszczalne, ponieważ String jest używany wszędzie. Dlatego klasa String jest oznaczona jako final.

Każda próba dziedziczenia po klasie final spowoduje błąd kompilacji:
```
public final class Cat {
    private int weight;
    // standardowe gettery i settery
}

public class BlackCat extends Cat { } // Błąd: nie można dziedziczyć po klasie final
```
Uwaga: final przy deklaracji klasy nie oznacza, że obiekty tej klasy są niemutowalne. Możemy zmieniać pola obiektu:
```
Cat cat = new Cat();
cat.setWeight(1);
```
Po prostu nie możemy jej rozszerzać.

Zgodnie z zasadami dobrej praktyki powinniśmy ostrożnie tworzyć i dokumentować klasy lub oznaczać je jako final dla bezpieczeństwa. Jednak stosując final, tracimy możliwość rozszerzania klasy w celu poprawienia błędów w metodach, co jest jednym z atutów programowania obiektowego.

 Metody final
Metody oznaczone jako final nie mogą być nadpisywane. Jeśli projektujemy klasę i uznamy, że metoda nie powinna być nadpisywana, możemy ją oznaczyć jako final. W bibliotekach standardowych Javy również znajdziesz wiele takich metod.

Czasami nie chcemy całkowicie zablokować dziedziczenia klasy, a jedynie uniemożliwić nadpisanie niektórych metod. Przykładem jest klasa Thread, którą można rozszerzać, ale metoda isAlive() jest oznaczona jako final.

Metoda isAlive() sprawdza, czy wątek żyje i z różnych powodów (np. kod natywny zależny od systemu operacyjnego) nie może być poprawnie nadpisana.

Przykład:
```
public class Dog {
    public final void sound() { /* ... */ }
}

public class BlackDog extends Dog {
    public void sound() { } // Błąd: nie można nadpisać metody final
}
```

Zmienne final
Zmienne oznaczone jako final nie mogą być ponownie przypisane. Po zainicjalizowaniu wartości zmiennej final nie można jej zmienić.
```
final int i = 1;
i = 2; // Błąd: zmiennej final nie można przypisać ponownie
```

Referencje final
Dla referencji final nie możemy zmienić referencji, ale możemy modyfikować obiekt, na który wskazuje:
```
final Cat cat = new Cat();
cat.setWeight(5); // OK
cat = new Cat(); // Błąd
```
Pola final
Pola final mogą być stałymi lub polami zapisywanymi tylko raz. Zgodnie z konwencją nazwy stałych piszemy wielkimi literami z podkreśleniami:
```
static final int MAX_WIDTH = 999;
```
Pola final muszą być zainicjalizowane przed zakończeniem konstruktora.

Dla static final: możemy inicjalizować przy deklaracji lub w bloku statycznym.

Dla pól instancyjnych final: możemy inicjalizować przy deklaracji, w bloku inicjalizacyjnym lub w konstruktorze.

W przeciwnym razie pojawi się błąd kompilacji.

Parametry final
Możemy używać final przy parametrach metod. Nie można ich zmieniać wewnątrz metody:
```
public void methodWithFinalArguments(final int x) {
    x = 1; // Błąd: nie można zmienić parametru final
}
```

Podsumowanie
W tym materiale dowiedzieliśmy się, co oznacza słowo kluczowe final dla klas, metod i zmiennych. Choć w codziennym kodzie rzadko stosujemy final, jest ono przydatnym narzędziem projektowym, które może poprawić bezpieczeństwo i przewidywalność kodu.



| **Zakres użycia**         | **Co oznacza `final`?**                                         | **Przykład**                       | **Efekt**                                                        |
| ------------------------- | --------------------------------------------------------------- | ---------------------------------- | ---------------------------------------------------------------- |
| **Klasa**                 | Klasa **nie może być dziedziczona**                             | `public final class Cat {}`        | Nie można utworzyć podklasy tej klasy                            |
| **Metoda**                | Metoda **nie może być nadpisana** w podklasie                   | `public final void sound() {}`     | Podklasa nie może nadpisać tej metody                            |
| **Zmienna prymitywna**    | Wartość **nie może być zmieniona po przypisaniu**               | `final int x = 5;`                 | Próba przypisania `x = 10;` spowoduje błąd                       |
| **Referencja do obiektu** | Referencja **nie może wskazywać na inny obiekt**                | `final Cat cat = new Cat();`       | `cat = new Cat();` → błąd, ale `cat.setWeight(5);` jest poprawne |
| **Pola klas**             | Pole **musi być zainicjalizowane** raz (stała lub "write-once") | `static final int MAX_SIZE = 100;` | Wartość stała, niezmienna po przypisaniu                         |
| **Parametry metody**      | Parametr **nie może być zmieniony** w metodzie                  | `public void foo(final int x) {}`  | `x = 5;` → błąd kompilacji                                       |
