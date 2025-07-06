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
