Ograniczenia typów generycznych (Java)
Typy generyczne nie wspierają dziedziczenia między List<Object> a List<String>, więc trudno przekazywać różne kolekcje do jednej metody.

Rozwiązaniem są wildcards (?):

List<?> – lista dowolnych typów, można odczytywać jako Object, ale nie można dodawać (poza null).

List<? extends T> – elementy są typu T lub podtypów, można odczytywać, ale nie można dodawać.

List<? super T> – elementy są typu T lub nadtypów, można dodawać elementy typu T, ale odczyt daje Object.

Wildcards umożliwiają elastyczne przekazywanie kolekcji przy zachowaniu bezpieczeństwa typów, ale ograniczają możliwość zapisu lub odczytu elementów w zależności od użycia extends lub super.

# cos wiecej

Ograniczenia typów generycznych (Java)
Problem:

W Javie List<Object> ≠ List<String>, więc metoda z parametrem List<Object> nie przyjmie List<String>.

Typy generyczne w czasie działania są usuwane (erasure), więc brak informacji o typie w runtime.


Rozwiązanie: Wildcards (?)
Wildcards pozwalają na elastyczne przekazywanie kolekcji przy zachowaniu bezpieczeństwa typów, ale wprowadzają ograniczenia przy odczycie/zapisie.

1️⃣ List<?> – unbounded wildcard
Reprezentuje listę dowolnego typu.

✅ Można odczytywać elementy jako Object.

❌ Nie można dodawać elementów (poza null), bo nie znamy typu.

Przykład:
```
void printList(List<?> list) { 
   for (Object e : list) System.out.println(e);
}
```
2️⃣ List<? extends T> – bounded wildcard (upper bound)
Dopuszcza listy typu T lub podtypów T.

✅ Można odczytywać elementy jako T.

❌ Nie można dodawać elementów, bo nie znamy dokładnego typu.

Przykład:
```
void drawAll(List<? extends Shape> shapes) { 
   for (Shape s : shapes) s.draw();
}
```
Metoda przyjmie zarówno List<Shape>, jak i List<Circle>.
 List<? super T> – bounded wildcard (lower bound)
Dopuszcza listy typu T lub nadtypów T.

✅ Można dodawać elementy typu T.

❌ Odczyt daje typ Object.
```
void addInteger(List<? super Integer> list) { 
   list.add(5); 
}
```
| Typ wildcard    | Co umożliwia        | Odczyt     | Zapis |
| --------------- | ------------------- | ---------- | ----- |
| `<?>`           | dowolny typ         | ✅ `Object` | ❌     |
| `<? extends T>` | `T` lub podtypy `T` | ✅ `T`      | ❌     |
| `<? super T>`   | `T` lub nadtypy `T` | `Object`   | ✅ `T` |

✅ Wildcards zwiększają elastyczność generyków, ale ograniczają możliwość odczytu/zapisu w zależności od użycia.
