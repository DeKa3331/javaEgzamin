# Interfejs `Collection<E>` w Java

Pakiet: `java.util`

---

## Opis ogólny

`Collection<E>` to podstawowy interfejs w hierarchii kolekcji w Javie, reprezentujący grupę elementów typu `E`. Dziedziczy po `Iterable<E>`, więc wszystkie kolekcje można iterować.

- Może zawierać duplikaty (np. `List`), lub nie (np. `Set`).
- Kolekcje mogą być uporządkowane lub nieuporządkowane.
- Interfejs nie dostarcza bezpośrednich implementacji — to rola podinterfejsów (`List`, `Set`, `Queue`) oraz ich klas implementujących (`ArrayList`, `HashSet` itd.).
- Projektowanie z użyciem `Collection` pozwala pisać metody operujące na dowolnych kolekcjach, niezależnie od ich konkretnej implementacji.

---

## Główne cechy

- **Brak synchronizacji**: Implementacje nie są synchronizowane domyślnie — współbieżne modyfikacje mogą prowadzić do nieokreślonego zachowania. Synchronizację należy zapewnić zewnętrznie lub korzystając z klas z pakietu `java.util.concurrent`.
  
- **Obsługa wyjątków przy operacjach niedozwolonych**: 
  - Metody zmieniające kolekcję mogą rzucać `UnsupportedOperationException`, jeśli dana operacja nie jest wspierana.
  - Dodanie elementu niedozwolonego (np. `null` w kolekcji tego nie pozwalającej) może spowodować `NullPointerException` lub `ClassCastException`.

- **Standardowe konstruktory w implementacjach**: 
  - Pusty konstruktor tworzący pustą kolekcję.
  - Konstruktor kopiujący, który przyjmuje inną kolekcję i tworzy jej kopię.

- **Równość i hashCode**:
  - Metody `equals()` i `hashCode()` mogą być oparte na elementach kolekcji.
  - Dla klas implementujących `List` i `Set` obowiązują konkretne zasady porównywania.

- **Obsługa metod strumieniowych** (Java 8+):
  - `stream()` zwraca sekwencyjny strumień elementów.
  - `parallelStream()` zwraca potencjalnie równoległy strumień.

- **Samoodwołujące się kolekcje**: 
  - Niektóre metody (np. `equals()`, `toString()`) mogą rzucać wyjątki w przypadku kolekcji zawierających same siebie (bezpośrednio lub pośrednio).

---

## Najważniejsze metody interfejsu

| Metoda                                      | Opis                                                                                         | Wyjątki / Uwagi                                                  |
|---------------------------------------------|----------------------------------------------------------------------------------------------|-----------------------------------------------------------------|
| `int size()`                                | Zwraca liczbę elementów w kolekcji                                                         |                                                                 |
| `boolean isEmpty()`                         | Sprawdza, czy kolekcja jest pusta                                                           |                                                                 |
| `boolean contains(Object o)`                | Sprawdza, czy kolekcja zawiera element `o`                                                  | Może rzucać `ClassCastException`, `NullPointerException` (opcjonalnie) |
| `Iterator<E> iterator()`                     | Zwraca iterator do iteracji po elementach kolekcji                                          | Kolejność zwracanych elementów nie jest gwarantowana            |
| `Object[] toArray()`                         | Zwraca tablicę zawierającą wszystkie elementy kolekcji                                      | Zwrotna tablica jest kopią (bez powiązania z kolekcją)          |
| `<T> T[] toArray(T[] a)`                     | Zwraca tablicę określonego typu z elementami kolekcji                                       | Może rzucić `ArrayStoreException`, `NullPointerException`       |
| `boolean add(E e)`                           | Dodaje element `e` do kolekcji (opcjonalne)                                                 | Może rzucić `UnsupportedOperationException`, `NullPointerException`, `ClassCastException`, `IllegalArgumentException`, `IllegalStateException` |
| `boolean remove(Object o)`                    | Usuwa jedno wystąpienie elementu `o` (opcjonalne)                                           | Może rzucić `UnsupportedOperationException`                      |
| `boolean containsAll(Collection<?> c)`       | Sprawdza, czy kolekcja zawiera wszystkie elementy z podanej kolekcji                        | Może rzucać `ClassCastException`, `NullPointerException`         |
| `boolean addAll(Collection<? extends E> c)` | Dodaje wszystkie elementy z podanej kolekcji (opcjonalne)                                  | Może rzucić `UnsupportedOperationException`                      |
| `boolean removeAll(Collection<?> c)`          | Usuwa z kolekcji wszystkie elementy zawarte w podanej kolekcji (opcjonalne)                 | Może rzucić `UnsupportedOperationException`                      |
| `boolean retainAll(Collection<?> c)`          | Zachowuje w kolekcji tylko elementy zawarte w podanej kolekcji (opcjonalne)                 | Może rzucić `UnsupportedOperationException`                      |
| `void clear()`                               | Usuwa wszystkie elementy z kolekcji (opcjonalne)                                           | Może rzucić `UnsupportedOperationException`                      |
| `boolean removeIf(Predicate<? super E> filter)` | Usuwa elementy spełniające warunek (domyślna implementacja od Java 8)                       | Może rzucić `UnsupportedOperationException`                      |
| `boolean equals(Object o)`                    | Sprawdza równość z innym obiektem                                                          | Implementacja może opierać się na elementach kolekcji            |
| `int hashCode()`                             | Zwraca hashCode kolekcji                                                                    | Powinna być spójna z `equals()`                                  |
| `Stream<E> stream()`                         | Zwraca sekwencyjny strumień elementów kolekcji                                             | Java 8+                                                         |
| `Stream<E> parallelStream()`                 | Zwraca równoległy strumień elementów kolekcji                                              | Java 8+                                                         |
| `Spliterator<E> spliterator()`               | Zwraca spliterator do efektywnej iteracji elementów                                        | Java 8+                                                         |

---

## Implementacje

Typowe implementacje `Collection` to:

- **List**: `ArrayList`, `LinkedList`, `Vector`, `Stack`
- **Set**: `HashSet`, `LinkedHashSet`, `TreeSet`, `EnumSet`
- **Queue**: `PriorityQueue`, `ArrayDeque`, `LinkedBlockingQueue`

---

## Synchronizacja i współbieżność

- Standardowe implementacje nie są bezpieczne dla wielu wątków.
- Dla potrzeb współbieżnych warto używać klas z pakietu `java.util.concurrent` lub stosować mechanizmy synchronizacji zewnętrznej (`Collections.synchronizedCollection()`).

---

## Dodatkowe informacje

- Kolekcje mogą mieć ograniczenia na elementy (np. nie dopuszczają `null`).
- Wiele metod jest domyślnie opcjonalnych i może rzucać `UnsupportedOperationException`.
- Kolejność elementów zależy od konkretnej implementacji.
- Interfejs jest fundamentem całego Frameworka Kolekcji w Javie.

---
