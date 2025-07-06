Kolektory to narzędzia do przekształcania strumienia w wynik końcowy: listę, mapę, zestaw, string, statystyki itp.

Stosowane w operacji terminalnej:
```
collect(Collector<T, A, R> collector)
```
```
List<String> list = stream.collect(Collectors.toList());
```
Najważniejsze kolektory
1️⃣ toList(), toSet()
Zbierają elementy strumienia do List lub Set.
```
List<String> names = stream.collect(Collectors.toList());
Set<String> unique = stream.collect(Collectors.toSet());
```
2️⃣ joining()
Łączy elementy Stream<String> w jeden napis:
```
String result = Stream.of("Ala", "ma", "kota")
    .collect(Collectors.joining(" "));  // "Ala ma kota"

```
3️⃣ counting()
Zlicza elementy w strumieniu:
```
long count = stream.collect(Collectors.counting());
```
4️⃣ summarizingInt() / averagingInt()
Podaje statystyki liczbowe (min, max, avg, suma, count) lub średnią:
```
IntSummaryStatistics stats = stream.collect(Collectors.summarizingInt(String::length));
double avg = stream.collect(Collectors.averagingInt(String::length));
```
sa tez inne:
5️⃣ groupingBy()
Grupuje elementy po kluczu:
```
Map<Integer, List<String>> grouped = stream
    .collect(Collectors.groupingBy(String::length));
```
6️⃣ partitioningBy()
Dzieli elementy na dwie grupy wg predykatu:
```
Map<Boolean, List<Integer>> parts = stream
    .collect(Collectors.partitioningBy(n -> n % 2 == 0));
```
7️⃣ toMap()
Zamienia strumień w mapę:
```
Map<String, Integer> map = stream
    .collect(Collectors.toMap(Function.identity(), String::length));
```
🎯 Zastosowania kolektorów:
✅ Zbieranie strumienia do listy, zbioru, mapy.
✅ Grupowanie danych wg cech (np. długości napisu).
✅ Liczenie elementów, obliczanie średnich, sum, statystyk.
✅ Łączenie tekstu w jeden napis (np. CSV).
✅ Wydajne agregowanie danych z kolekcji w sposób czytelny i funkcyjny.

```
List<String> result = list.stream()
    .filter(s -> s.length() > 2)
    .map(String::toUpperCase)
    .collect(Collectors.toList());
```

# napisz mi przykładowy kolektór który wezmie wszystkie wyrazy które maja patrzysta dlugosc wyrazu dluzsza niz 10, gdzie pierwsza litera jest duza litera a kazda inna normalna
✅ Filtruje wyrazy o parzystej długości > 10
✅ Konwertuje je na format: wszystkie duze litery
✅ Zbiera wynik do List<String>

List<String> result = list.stream()
    .filter(s -> s.length() > 10 && s.length() % 2 == 0)
    .map(String::toUpperCase)
    .collect(Collectors.toList());
