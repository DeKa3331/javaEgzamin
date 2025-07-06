Parametryzacja testów
Co to jest?
Parametryzacja testów to technika, dzięki której możemy uruchomić ten sam test wielokrotnie z różnymi zestawami danych wejściowych i oczekiwanymi wynikami. Pozwala to unifikować i skrócić testy, unikając powielania kodu.

Parametryzacja testów w JUnit 5
1. Wprowadzenie
JUnit 5 to nowa generacja popularnego frameworka do testowania w Javie, która wprowadza wiele nowych funkcjonalności ułatwiających pisanie testów. Jedną z nich są testy parametryzowane (ang. parameterized tests). Dzięki nim możemy uruchomić pojedynczą metodę testową wielokrotnie, za każdym razem z innymi danymi wejściowymi.

test parametryzowany oznacza się adnotacją @ParameterizedTest zamiast zwykłego @Test.

Testy parametryzowane pozwalają uniknąć duplikacji kodu testowego i ułatwiają testowanie różnych wariantów zachowania metod.

Dane wejściowe dostarczamy za pomocą źródeł parametrów, np.:

@ValueSource – lista prostych wartości (liczby, stringi itp.).

@CsvSource – lista wartości w formacie CSV (wiele parametrów).

@MethodSource – metoda zwracająca strumień argumentów.

@NullSource, @EmptySource, @NullAndEmptySource - Null i puste wartości

@EnumSource – dla wartości enum.

```
public class Numbers {
    public static boolean isOdd(int number) {
        return number % 2 != 0;
    }
}

@ParameterizedTest
@ValueSource(ints = {1, 3, 5, -3, 15, Integer.MAX_VALUE})
void isOdd_ShouldReturnTrueForOddNumbers(int number) {
    assertTrue(Numbers.isOdd(number));
}
```
