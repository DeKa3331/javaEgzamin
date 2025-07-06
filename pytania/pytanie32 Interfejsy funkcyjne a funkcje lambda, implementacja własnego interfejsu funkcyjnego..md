Interfejsy funkcyjne a funkcje lambda (Java)
✅ Interfejs funkcyjny – interfejs z jedną metodą abstrakcyjną, np. Predicate, Supplier, Consumer, Function.

✅ Funkcje lambda pozwalają krótko zapisać implementację tej metody bez potrzeby pisania klasy anonimowej.

Przykład:
```
Predicate<Integer> p = x -> x > 0;

ZAMIAST

Predicate<Integer> p = new Predicate<>() {
    public boolean test(Integer x) { return x > 0; }
};
```

Implementacja własnego interfejsu funkcyjnego
Aby utworzyć własny interfejs funkcyjny:

✅ Oznacz interfejs adnotacją @FunctionalInterface (opcjonalnie, ale zalecane).
✅ Zawiera jedną metodę abstrakcyjną.

Przykład:

```
@FunctionalInterface
interface Calculator {
    int compute(int a, int b);
}
```
Użycie z funkcją lambda:
```
Calculator add = (a, b) -> a + b;
System.out.println(add.compute(2, 3)); // wypisze 5
```
Podsumowanie
✅ Interfejsy funkcyjne + funkcje lambda upraszczają kod, pozwalając na przekazywanie funkcji jako argumentów i stosowanie stylu funkcyjnego w Javie.
✅ Własny interfejs funkcyjny umożliwia definiowanie własnych operacji funkcyjnych dopasowanych do potrzeb programu.

| **Interfejsy funkcyjne**                                                 | **Funkcje lambda**                                       |
| ------------------------------------------------------------------------ | -------------------------------------------------------- |
| Interfejs z jedną metodą abstrakcyjną                                    | Skrócona forma implementacji tej metody                  |
| Reprezentuje **typ funkcji** w Javie                                     | Reprezentuje **konkretne działanie (implementację)**     |
| Można używać w metodach, kolekcjach, streamach                           | Służy do przekazywania logiki do interfejsów funkcyjnych |
| Przykłady: `Predicate`, `Supplier`, `Consumer`, `Function`               | Przykład: `x -> x > 0`                                   |
| Definiowany za pomocą `interface` + (opcjonalnie) `@FunctionalInterface` | Tworzony za pomocą `->`                                  |
| Może być używany z metodami referencyjnymi                               | Często używany zamiast klas anonimowych                  |
| Np. `Predicate<Integer> p = ...`                                         | Np. `Predicate<Integer> p = x -> x > 0;`                 |


Podsumowanie:
✅ Interfejs funkcyjny = typ funkcji
✅ Lambda = implementacja tej funkcji
✅ Razem pozwalają przekazywać logikę jako argument, upraszczając kod w Javie.
