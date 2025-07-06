Readery w Javie – podział, różnice i zastosowanie
Reader to abstrakcyjna klasa w pakiecie java.io służąca do czytania znaków (charów). Jest podstawą dla wszystkich czytników znakowych w Javie.

1. Podział Readerów
A) Podstawowa klasa abstrakcyjna:
java.io.Reader — abstrakcyjna klasa bazowa dla czytników znakowych.

B) Najczęściej używane implementacje:

| Klasa               | Opis                                                                                  | Zastosowanie                                                                       |
| ------------------- | ------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `FileReader`        | Czyta znaki z pliku.                                                                  | Odczyt plików tekstowych (domyślne kodowanie platformy).                           |
| `BufferedReader`    | Buforowany Reader, zwiększa efektywność odczytu, posiada metodę `readLine()`.         | Czytanie tekstu linia po linii, efektywne czytanie.                                |
| `InputStreamReader` | Adapter do konwersji bajtów (InputStream) na znaki (Reader), z określonym kodowaniem. | Odczyt znaków z dowolnego strumienia bajtowego z kontrolą kodowania (np. z sieci). |
| `StringReader`      | Reader do czytania znaków ze Stringa.                                                 | Przetwarzanie tekstów w pamięci.                                                   |


| Cecha            | `FileReader`             | `BufferedReader`                   | `InputStreamReader`                   |
| ---------------- | ------------------------ | ---------------------------------- | ------------------------------------- |
| Źródło danych    | Plik                     | Inny Reader (owija inny Reader)    | Strumień bajtów (InputStream)         |
| Buforowanie      | Nie (czyta bezpośrednio) | Tak (buforuje, poprawia wydajność) | Nie (ale można owinąć BufferedReader) |
| Kodowanie znaków | Domyślne platformowe     | N/D (dziedziczy od Reader)         | Umożliwia ustawienie kodowania znaków |
| Metody dodatkowe | Podstawowe `read()`      | `readLine()` i inne                | Podstawowe `read()`                   |

 Szczegółowe informacje
Buforowanie
BufferedReader buforuje znaki w pamięci, więc nie odczytuje każdego znaku z fizycznego źródła osobno. To znacznie poprawia wydajność odczytu, szczególnie przy operacjach linia-po-linii.

Kodowanie znaków
FileReader domyślnie używa kodowania systemowego (np. CP1250 na Windows w Polsce), co może powodować problemy z odczytem plików w innym kodowaniu. Z tego powodu często preferuje się użycie InputStreamReader z jawnie podanym kodowaniem, np. UTF-8.

Adaptacja bajtów na znaki
InputStreamReader jest niezbędny, gdy czytamy dane z surowych strumieni bajtowych, np. z sieci lub plików, których kodowanie musimy określić.

Zamknięcie strumienia
Każdy Reader powinien być zamknięty po użyciu (najlepiej z użyciem try-with-resources), aby zwolnić zasoby systemowe.
 Przykłady zastosowania
A) Odczyt pliku tekstowego z buforowaniem i kodowaniem UTF-8
```
try (BufferedReader br = new BufferedReader(new InputStreamReader(new FileInputStream("plik.txt"), StandardCharsets.UTF_8))) {
    String line;
    while ((line = br.readLine()) != null) {
        System.out.println(line);
    }
}

```
Podsumowanie
Reader to abstrakcyjna klasa dla czytania znaków w Javie.

Najczęściej korzysta się z BufferedReader (efektywne czytanie linii), FileReader (prosty odczyt plików, ale z ograniczeniem kodowania) oraz InputStreamReader (elastyczność kodowania).

Dobrą praktyką jest łączenie InputStreamReader z BufferedReader dla czytania plików z określonym kodowaniem i buforowaniem.

StringReader i podobne klasy są wygodne do testowania i pracy z tekstem w pamięci.
