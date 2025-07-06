Wyjątki w Javie — składnia i zastosowanie
1. Co to jest wyjątek?
Wyjątek (ang. exception) to zdarzenie, które pojawia się podczas działania programu i zakłóca jego normalny przepływ. Może być spowodowane np.:

błędem logicznym,

nieprawidłowymi danymi,

problemem z dostępem do pliku,

błędem sieciowym,

itp.

Wyjątki pozwalają na wykrycie i obsłużenie błędów w kontrolowany sposób.

2. Hierarchia wyjątków
Throwable — klasa bazowa dla wszystkich błędów i wyjątków.

Error — błędy systemowe (np. OutOfMemoryError), których zwykle nie obsługujemy.

Exception — wyjątki, które możemy przechwycić i obsłużyć.

RuntimeException — wyjątki niekontrolowane (unchecked), np. NullPointerException, ArithmeticException.

wyjątki kontrolowane (checked), np. IOException, SQLException.

3. Składnia obsługi wyjątków
Blok try-catch
```
try {
    // kod, który może rzucić wyjątek
} catch (TypWyjątku nazwa) {
    // obsługa wyjątku
}
```
Można mieć wiele bloków catch na różne typy wyjątków.

Blok finally
Opcjonalny blok wykonywany zawsze, niezależnie czy wyjątek został rzucony, np. do zamknięcia zasobów.

```
try {
    // kod
} catch (Exception e) {
    // obsługa
} finally {
    // kod wykonywany zawsze
}
```
Rzucanie wyjątków
throw — do rzucania pojedynczego wyjątku.
```
throw new IOException("Błąd odczytu pliku");
```
throws — w sygnaturze metody deklaruje, że metoda może rzucić wyjątek.
```
public void readFile() throws IOException {
    // kod
}
```
5. Zastosowanie wyjątków
Obsługa błędów wejścia/wyjścia (np. odczyt pliku, sieć)

Weryfikacja poprawności danych (np. sprawdzanie zakresów, formatów)

Zarządzanie zasobami (zwalnianie plików, połączeń)

Programowanie defensywne — przewidywanie i kontrolowanie błędnych sytuacji

Propagacja błędów do wyższych warstw programu

# Podsumowanie
Wyjątki służą do obsługi błędów podczas działania programu.

Kontrolowane wyjątki (checked) trzeba obsłużyć lub zadeklarować w throws.

Nieobsłużone wyjątki (runtime) mogą spowodować zakończenie programu.

try-catch-finally to podstawowy mechanizm obsługi wyjątków.
