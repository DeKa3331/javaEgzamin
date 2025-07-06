Szablon Optional (Java)
✅ Optional<T> – opakowanie na obiekt typu T, które może być obecne lub nieobecne (null), zapobiega NullPointerException.

Podstawowe metody:
Optional.of(value) – tworzy Optional z wartością (nie może być null).

Optional.ofNullable(value) – tworzy Optional, akceptuje null.

Optional.empty() – pusty Optional.

isPresent() – sprawdza, czy wartość jest obecna.

get() – pobiera wartość (rzuca wyjątek, jeśli brak).

orElse(default) – zwraca wartość lub domyślną.

ifPresent(consumer) – wykonuje kod, jeśli wartość jest obecna.
```
Optional<String> name = Optional.ofNullable(getName());
System.out.println(name.orElse("Brak danych"));
```
Korzyści:
✅ Unikanie null i NullPointerException.
✅ Wymusza jawne sprawdzenie obecności wartości.
✅ Poprawia czytelność kodu i bezpieczeństwo.

Gdzie używać:
✅ Zwracanie wyniku z metod, gdzie brak wyniku jest możliwy i oczekiwany.
✅ Jako alternatywa dla null w API.

Podsumowanie:
Optional pozwala bezpiecznie pracować z wartościami opcjonalnymi, wymuszając jawne zarządzanie brakiem danych, co zwiększa czytelność i bezpieczeństwo kodu w Javie.

# tutaj sie niby duzo dzieje w tym przykładowym, ale cuhj wie czy on tyle tego chhce

Optional – zasada działania
✅ Optional to klasa w Javie (od Java 8) do bezpiecznego reprezentowania wartości, która może być obecna lub nie, zamiast null.
✅ Wymusza jawne sprawdzenie obecności wartości → chroni przed NullPointerException.

Podstawowe użycie:
Tworzenie:

Optional.of(value) – wartość nie może być null.

Optional.ofNullable(value) – akceptuje null.

Optional.empty() – pusty Optional.

Sprawdzanie:

isPresent() / isEmpty() – czy wartość jest obecna.

ifPresent(v -> ...) – wykonaj akcję, jeśli wartość jest obecna.

Pobieranie wartości:

get() – zwraca wartość (rzuca wyjątek, jeśli brak).

orElse(default) – zwraca wartość lub domyślną.

orElseGet(() -> default) – zwraca wartość lub wynik z lambdy.

orElseThrow() – rzuca wyjątek, jeśli brak wartości.

Transformacja i filtrowanie:

map() – przekształca wartość wewnątrz.

flatMap() – jak map, ale unika zagnieżdżonych Optional.

filter() – filtruje wartość wg predykatu.

Po co?
✅ Zapewnia czytelny, bezpieczny sposób obsługi braku wartości.
✅ Ułatwia pisanie czystego kodu bez if (x != null).
```
Optional<String> opt = Optional.ofNullable(getName());
String name = opt.orElse("Brak danych");
```
