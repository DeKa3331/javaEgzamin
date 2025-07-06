W C++ std::multimap to kontener mapy, który pozwala na przechowywanie wielu wartości pod tym samym kluczem (czyli klucze mogą się powtarzać).

W Javie nie ma dokładnego odpowiednika multimap w standardowej bibliotece, ale można łatwo zrekonstruować jego działanie na kilka sposobów:

Sposób 1: Map<K, List<V>>
Używamy mapy, gdzie wartością jest lista wartości przypisanych do danego klucza.
K-klucz
list<v>-lista jakiegos typu np List<Intinger>
```
Map<K, List<V>> multimap = new HashMap<>();

// Dodawanie wartości
void put(K key, V value) {
    multimap.computeIfAbsent(key, k -> new ArrayList<>()).add(value);
}

// Pobieranie wartości
List<V> get(K key) {
    return multimap.getOrDefault(key, Collections.emptyList());
}

// Usuwanie konkretnej wartości dla klucza
boolean remove(K key, V value) {
    List<V> values = multimap.get(key);
    if (values != null) {
        boolean removed = values.remove(value);
        if (values.isEmpty()) {
            multimap.remove(key);
        }
        return removed;
    }
    return false;
}
```

```
public class Main {
    public static void main(String[] args) {
        MultiMap<String, Integer> multimap = new MultiMap<>();

        multimap.put("a", 1);
        multimap.put("a", 2);
        multimap.put("b", 3);

        System.out.println(multimap.get("a")); // [1, 2]
        System.out.println(multimap.get("b")); // [3]

        multimap.remove("a", 1);
        System.out.println(multimap.get("a")); // [2]
    }
}
```


| Cecha              | `std::multimap` w C++ | `Map<K, List<V>>` w Javie           |
| ------------------ | --------------------- | ----------------------------------- |
| Duplikaty kluczy   | Tak                   | Tak (lista może zawierać duplikaty) |
| Duplikaty wartości | Tak                   | Tak                                 |
| API                | Wbudowane             | Trzeba ręcznie pisać                |
| Wydajność          | Bardzo wydajne        | Zależy od implementacji listy       |
