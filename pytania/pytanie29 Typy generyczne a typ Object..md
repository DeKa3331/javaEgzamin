 Typy generyczne a typ Object (Java)
1️⃣ Klasa bez generyków (typ Object)
Klasa:
```
public class Box {
    private Object object;
    public void set(Object object) { this.object = object; }
    public Object get() { return object; }
}
```

Pozwala przechowywać dowolny obiekt.
❌ Brak sprawdzania typu w czasie kompilacji.
❌ Potrzeba rzutowania przy pobieraniu obiektu, co może prowadzić do błędów w czasie wykonania (ClassCastException).

 Klasa generyczna
Definicja:

```
public class Box<T> {
    private T t;
    public void set(T t) { this.t = t; }
    public T get() { return t; }
}
```
✅ Typ zmiennej T określany przy tworzeniu obiektu (np. Box<Integer>).
✅ Zapewnia bezpieczeństwo typów w czasie kompilacji.
✅ Brak potrzeby rzutowania przy odczycie wartości.

Tworzenie obiektów generycznych
```
Box<Integer> integerBox = new Box<>();
```
✅ Kompilator automatycznie wnioskuje typ argumentu.
4️⃣ Konwencje nazw typów generycznych
T – Type

E – Element

K – Key

V – Value

N – Number


| Typ `Object`              | Typy generyczne                |
| ------------------------- | ------------------------------ |
| Dowolny obiekt            | Obiekt określonego typu        |
| Potrzebne rzutowanie      | Brak rzutowania                |
| Brak bezpieczeństwa typów | Bezpieczeństwo typów           |
| Błędy wykrywane w runtime | Błędy wykrywane w compile-time |

7️⃣ Podsumowanie
✅ Typy generyczne zwiększają bezpieczeństwo typów i czytelność kodu w porównaniu do użycia Object.
✅ Ułatwiają tworzenie wielokrotnego użytku klas i metod działających na różnych typach danych.
✅ W nowoczesnej Javie zaleca się stosowanie generyków zamiast Object w kolekcjach i strukturach danych.


# BETTER NOTATKA
 Typy generyczne a typ Object (Java)
1️⃣ Problem z używaniem typu Object
Przykład:

```
public class Box {
    private Object object;
    public void set(Object object) { this.object = object; }
    public Object get() { return object; }
}
```
Przechowuje dowolny obiekt, ale:
❌ Brak bezpieczeństwa typów – kompilator nie sprawdza, jaki typ wstawiasz i odbierasz.
❌ Potrzebne ręczne rzutowanie przy odczycie:

```
Box box = new Box();
box.set("tekst");
Integer liczba = (Integer) box.get(); // Błąd w runtime: ClassCastException
```
❌ Błędy ujawniają się dopiero w czasie uruchomienia.

2️⃣ Rozwiązanie: Typy generyczne
Definicja:

```
public class Box<T> {
    private T t;
    public void set(T t) { this.t = t; }
    public T get() { return t; }
}
```
Zalety:
✅ Kompilator wymusza spójność typu:

```
Box<Integer> integerBox = new Box<>();
integerBox.set(123);
Integer liczba = integerBox.get(); // brak rzutowania
```
✅ Brak potrzeby rzutowania.
✅ Błędy wykrywane w czasie kompilacji, a nie w runtime.
✅ Poprawia czytelność kodu i zrozumienie intencji (np. Box<Integer>).

| Typ `Object`              | Typy generyczne                 |
| ------------------------- | ------------------------------- |
| Przyjmie dowolny obiekt   | Przyjmie tylko określony typ    |
| Wymaga rzutowania         | Brak rzutowania                 |
| Brak bezpieczeństwa typów | Bezpieczeństwo typów            |
| Błędy w runtime           | Błędy wykrywane przy kompilacji |
| Nie wiadomo, co trzyma    | Wiadomo, jaki typ przechowuje   |


4️⃣ Dlaczego wprowadzono generyki?
🔹 W Javie przed generics kolekcje (List, Set, Map) przechowywały elementy jako Object.
🔹 Prowadziło to do błędów rzutowania i nieczytelnego kodu.
🔹 Generyki umożliwiły:
✅ Określanie typu przechowywanych elementów w kolekcjach.
✅ Zwiększenie bezpieczeństwa typów.
✅ Brak konieczności rzutowania przy odczycie.

5️⃣ Podsumowanie
✅ Typ Object pozwala na przechowywanie dowolnych obiektów, ale kosztem bezpieczeństwa typów i potrzeby rzutowania.
✅ Typy generyczne eliminują te problemy, zapewniając:

bezpieczeństwo typów,

brak rzutowania,

błędy wykrywane w czasie kompilacji,

czytelniejszy, łatwiejszy w utrzymaniu kod.

➡️ Dlatego w nowoczesnej Javie preferujemy generyki nad typem Object wszędzie tam, gdzie chcemy przechowywać obiekty określonego typu.


