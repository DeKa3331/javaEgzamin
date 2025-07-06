| Metoda   | Opis                         | Przykładowe zastosowania         |
| -------- | ---------------------------- | -------------------------------- |
| `filter` | filtruje elementy wg warunku | tylko parzyste, aktywni          |
| `map`    | przekształca elementy        | uppercase, DTO                   |
| `sorted` | sortuje elementy             | według wartości, długości tekstu |

Trzy metody pośrednie w strumieniach
Metody pośrednie (intermediate operations):
– przetwarzają elementy strumienia i zwracają nowy strumień,
– są leniwe (lazy) – wykonują się dopiero przy operacji terminalnej.

filter(Predicate<T> predicate)
Zastosowanie:
– odfiltrowanie danych np. tylko parzyste liczby, tylko użytkownicy z aktywnym kontem.
```
Stream.of(1, 2, 3, 4, 5)
      .filter(n -> n % 2 == 0)
      .forEach(System.out::println); // 2, 4
```

map(Function<T,R> mapper)
Zastosowanie:
– przekształcanie danych np. konwersja stringów do uppercase, obiektów do DTO, wyciąganie pól z obiektów.
```
Stream.of("ala", "kot", "java")
      .map(String::toUpperCase)
      .forEach(System.out::println); // ALA, KOT, JAVA
```

sorted() oraz sorted(Comparator<T> comparator)
Zastosowanie:
– sortowanie list danych np. według wieku użytkownika, długości tekstu
```
Stream.of(5, 3, 1, 4, 2)
      .sorted()
      .forEach(System.out::println); // 1, 2, 3, 4, 5
```
ewentualnie wersja z komperatorem:
```
Stream.of("a", "ccc", "bb")
      .sorted(Comparator.comparing(String::length))
      .forEach(System.out::println); // a, bb, ccc
```
