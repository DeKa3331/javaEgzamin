Zasady tworzenia i zastosowanie pakietów w Javie
Co to jest pakiet?
Pakiet (ang. package) w Javie to sposób organizacji klas i interfejsów w logiczne grupy. Pakiety pomagają uporządkować kod źródłowy, uniknąć konfliktów nazw oraz ułatwiają zarządzanie dużymi projektami.

Tworzenie pakietu
Pakiet definiujemy na początku pliku źródłowego za pomocą instrukcji package, np.:
```
package com.example.utils;
```
Zasady tworzenia pakietów
Unikalność nazw — dzięki odpowiedniemu nazwaniu pakietu można uniknąć kolizji nazw klas w dużych systemach.

Hierarchiczna struktura — pakiety mogą być zagnieżdżone (np. com.example.utils jest podpakietem com.example).

Odzwierciedlenie struktury katalogów — układ plików w systemie plików powinien odpowiadać strukturze pakietów.

Czytelność i modularność — pakiety powinny grupować powiązane ze sobą klasy i interfejsy, ułatwiając nawigację w projekcie.

Zastosowanie pakietów
Organizacja kodu — dzięki pakietom kod staje się bardziej przejrzysty i łatwiejszy do utrzymania.

Kontrola dostępu — modyfikator dostępu protected oraz package-private (brak modyfikatora) działają na poziomie pakietu, umożliwiając ukrycie szczegółów implementacji przed innymi częściami programu.

Importowanie klas — pakiety umożliwiają importowanie konkretnych klas lub wszystkich klas z pakietu za pomocą import, co pozwala korzystać z klas w innych częściach aplikacji.

Unikanie konfliktów nazw — różne pakiety mogą zawierać klasy o tych samych nazwach, co eliminuje kolizje.
```
// Plik: com/example/utils/StringUtils.java
package com.example.utils;

public class StringUtils {
    public static boolean isEmpty(String str) {
        return str == null || str.isEmpty();
    }
}
```
przyklad uzycia w innym pliku:
```
import com.example.utils.StringUtils;

public class Main {
    public static void main(String[] args) {
        System.out.println(StringUtils.isEmpty("")); // true
    }
}
```
