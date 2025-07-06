Interfejsy funkcyjne (Java)
Interfejsy funkcyjne – interfejsy z jedną metodą abstrakcyjną, używane w wyrażeniach lambda i strumieniach.

1️⃣ Supplier<T>
Dostarcza wartość typu T.

Metoda: T get()

Przykład:
```
Supplier<String> s = () -> "Hello";
```
Predicate<T>
Sprawdza warunek dla T, zwraca boolean.

Metoda: boolean test(T t)

Przykład:
```
Predicate<Integer> p = x -> x > 0;
```
Consumer<T>
Przyjmuje T i wykonuje operację (nic nie zwraca).

Metoda: void accept(T t)

Przykład:
```
Consumer<String> c = s -> System.out.println(s);
```
Function<T, R>
Przyjmuje T, zwraca R.

Metoda: R apply(T t)

Przykład:
```
Function<String, Integer> f = s -> s.length();
```
| Interfejs   | Metoda            | Co robi                  |
| ----------- | ----------------- | ------------------------ |
| `Supplier`  | `T get()`         | Dostarcza wartość        |
| `Predicate` | `boolean test(T)` | Sprawdza warunek         |
| `Consumer`  | `void accept(T)`  | Wykonuje operację na `T` |
| `Function`  | `R apply(T)`      | Zamienia `T` na `R`      |


Używane w:

strumieniach (stream(), filter, map, forEach),

programowaniu funkcyjnym w Javie,

wyrażeniach lambda i metodach referencyjnych.
