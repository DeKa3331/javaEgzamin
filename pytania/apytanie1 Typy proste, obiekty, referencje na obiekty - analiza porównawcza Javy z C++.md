#gotowe GPT
Typy proste, obiekty i referencje na obiekty – analiza porównawcza Javy i C++
1. Typy danych prymitywne
Java posiada 8 typów prymitywnych:
byte, short, int, long (liczby całkowite),
float, double (liczby zmiennoprzecinkowe),
char (znak Unicode),
boolean (wartość logiczna true lub false).

Wartości prymitywne są przechowywane bezpośrednio na stosie (stack).

Przy kopiowaniu zmiennej prymitywnej tworzona jest nowa, niezależna kopia, więc zmiany w kopii nie wpływają na oryginał.

C++ również posiada typy prymitywne (int, char, float, double, bool itd.) przechowywane na stosie.

Kopiowanie tworzy oddzielną kopię wartości, identycznie jak w Javie.

2. Typy obiektowe (referencyjne)
Java:

Wszystkie obiekty są tworzone na stercie (heap).

Zmienne obiektowe przechowują referencję (odpowiednik wskaźnika) do obiektu na stosie.

Przy kopiowaniu zmiennej obiektowej kopiowana jest referencja, czyli dwie zmienne wskazują na ten sam obiekt.

Zmiany dokonane przez jedną referencję są widoczne przez drugą.

Java nie posiada jawnych wskaźników ani arytmetyki wskaźników.

Zarządzanie pamięcią odbywa się automatycznie przez garbage collector.

Nie ma destruktorów.

C++:

Obiekty mogą być tworzone zarówno na stosie, jak i na stercie (przy użyciu new).

Zmienne mogą przechowywać obiekty bezpośrednio (na stosie) lub wskaźniki do obiektów na stercie.

Kopiowanie wskaźników skutkuje wskazywaniem obu zmiennych na ten sam obiekt (podobnie jak referencje w Javie).

Kopiowanie obiektu (np. przez konstruktor kopiujący) tworzy nową, niezależną kopię.

Programista musi ręcznie zarządzać pamięcią (new/delete) lub stosować wzorce RAII.

W C++ dostępne są jawne wskaźniki i arytmetyka wskaźników.

Klasy mogą definiować destruktory, które są wywoływane przy usuwaniu obiektów.

| Aspekt                                    | Java                                               | C++                                                               |
| ----------------------------------------- | -------------------------------------------------- | ----------------------------------------------------------------- |
| Typy prymitywne                           | 8 predefiniowanych (`int`, `char`, `boolean` itd.) | Podobne (`int`, `char`, `bool` itd.)                              |
| Typy obiektowe                            | Obiekty na stercie, zmienne przechowują referencje | Obiekty na stosie lub stercie, zmienne mogą być wskaźnikami       |
| Przechowywanie prymitywów                 | Na stosie                                          | Na stosie                                                         |
| Przechowywanie obiektów                   | Obiekty na stercie, referencje na stosie           | Stos lub sterta, wskaźniki i obiekty bezpośrednie                 |
| Kopiowanie prymitywów                     | Tworzy nową kopię wartości                         | Tworzy nową kopię wartości                                        |
| Kopiowanie obiektów                       | Kopiuje referencję (wskazują na ten sam obiekt)    | Kopiuje wskaźnik lub tworzy kopię obiektu (konstruktor kopiujący) |
| Zarządzanie pamięcią                      | Automatyczne (garbage collector)                   | Ręczne (`new`/`delete`) lub automatyczne (RAII)                   |
| Jawne wskaźniki                           | Brak                                               | Są dostępne wraz z arytmetyką wskaźników                          |
| Destruktory                               | Brak                                               | Obecne w klasach                                                  |
| Bezpieczeństwo pamięci                    | Wyższe – brak arytmetyki wskaźników, brak wycieków | Niższe – ryzyko błędów wskaźnikowych i wycieków pamięci           |
| Domyślna wartość zmiennych referencyjnych | `null`                                             | `nullptr`                                                         |


Przykładowe zachowanie na przykładzie kopiowania
Java (typ prymitywny):

```
int x = 10;
int y = x;  // kopia wartości
y = 30;
System.out.println(x); // 10 (bez zmian)
Java (typ obiektowy):
```
```
int[] c = {10, 20, 30};
int[] d = c;  // obie referencje wskazują na ten sam obiekt
d[1] = 50;
System.out.println(c[1]); // 50 (zmiana widoczna przez obie referencje)
C++ (obiekt na stercie i wskaźnik):
```
```
int* p1 = new int(10);
int* p2 = p1; // oba wskaźniki wskazują na ten sam obiekt
*p2 = 20;
std::cout << *p1; // 20
C++ (obiekt na stosie, kopiowanie):
```
```
int x = 10;
int y = x;  // kopia wartości
y = 20;
std::cout << x; // 10

```
# notatki
Typy danych prymitywne vs. obiektowe w Javie z przykładami
Ostatnia aktualizacja: 23 lipca 2024

Typy danych w Javie
Każda zmienna w Javie ma określony typ danych. Typy danych określają rozmiar i rodzaj wartości, jakie mogą być przechowywane w identyfikatorze. Język Java jest bogaty w typy danych, co pozwala programiście dobrać typ odpowiedni do potrzeb aplikacji.

W Javie typy danych dzielimy na dwie kategorie:

Typy danych prymitywne (inaczej wbudowane)

Typy danych nieprymitywne (inaczej referencyjne lub złożone)

Typ danych prymitywnych
W Javie typy danych prymitywnych to predefiniowane typy danych języka. Określają one rozmiar i rodzaj wartości standardowych. Java posiada 8 typów prymitywnych:

byte, short, int, long

float, double

char

boolean

W przypadku typów prymitywnych wartości przechowywane są na stosie. Podczas kopiowania zmiennej tworzona jest nowa kopia, a zmiany w kopii nie wpływają na wartość oryginalnej zmiennej.

Grupa: Liczby całkowite
byte: 1 bajt (8 bitów), zakres od -128 do 127, domyślna wartość: 0
przykład: byte b = 10;

short: 2 bajty (16 bitów), zakres od -32768 do 32767, domyślna wartość: 0
przykład: short s = 11;

int: 4 bajty (32 bity), zakres od -2147483648 do 2147483647, domyślna wartość: 0
przykład: int i = 10;

long: 8 bajtów (64 bity), zakres od -9,223,372,036,854,775,808 do 9,223,372,036,854,775,807, domyślna wartość: 0
przykład: long l = 100012;
```
public class Demo {
    public static void main(String[] args) {
        byte b = 20;
        System.out.println("b= " + b);

        short s = 20;
        System.out.println("s= " + s);

        int i = 20;
        System.out.println("i= " + i);

        long l = 20;
        System.out.println("l= " + l);
    }
}
```

Grupa: Liczby zmiennoprzecinkowe
float: 4 bajty (32 bity), domyślna wartość: 0.0f
przykład: float f = 10.3f;

double: 8 bajtów (64 bity), domyślna wartość: 0.0d
przykład: double d = 11.123;

```
public class Demo {
    public static void main(String[] args) {
        float f = 20.25f;
        System.out.println("f= " + f);

        double d = 20.25;
        System.out.println("d= " + d);
    }
}
```

Grupa: Znaki
Reprezentowana przez typ char, który służy do przechowywania znaków w Unicode (litery, cyfry, symbole).

char: 2 bajty (16 bitów, bez znaku), zakres: 0 do 65,535
przykład: char c = 'a';
```
public class Demo {
    public static void main(String[] args) {
        char ch = 'S';
        System.out.println(ch);

        char ch2 = '&';
        System.out.println(ch2);

        char ch3 = '$';
        System.out.println(ch3);
    }
}
```
Typ Boolean
Typ boolean używany jest, gdy chcemy sprawdzić warunek w trakcie wykonywania programu. Może przyjąć tylko dwie wartości: true lub false.

Typ ten używa tylko 1 bitu pamięci.
```
public class Demo {
    public static void main(String[] args) {
        boolean t = true;
        System.out.println(t);

        boolean f = false;
        System.out.println(f);
    }
}
```
Typ danych obiektowych (referencyjnych)
Typy danych obiektowych, zwane także typami referencyjnymi, odnoszą się do obiektów w Javie. W odróżnieniu od typów prymitywnych są tworzone przez użytkowników i mogą przechowywać odniesienia do obiektów.

Przykłady:
tablice (array),
łańcuchy znaków (String),
klasy,
interfejsy.
W przypadku typów referencyjnych:
referencja zmiennej przechowywana jest na stosie, a właściwy obiekt przechowywany jest na stercie (heap).
chociaż tworzone są dwie zmienne referencyjne, obie wskazują na ten sam obiekt, więc zmiany dokonane za pomocą jednej referencji są widoczne również przez drugą.

```
import java.util.Arrays;

public class GeeksForGeeks {
    public static void main(String[] args) {
        System.out.println("PRIMITIVE DATA TYPES\n");

        int x = 10;
        int y = x;
        System.out.println("Initially: x = " + x + ", y = " + y);

        y = 30;
        System.out.println("After changing y to 30: x = " + x + ", y = " + y);
        System.out.println("**Zmiana dotyczy tylko y, ponieważ to typ prymitywny\n");

        System.out.println("REFERENCE DATA TYPES\n");

        int[] c = {10, 20, 30, 40};
        int[] d = c;

        System.out.println("Initially");
        System.out.println("Array c: " + Arrays.toString(c));
        System.out.println("Array d: " + Arrays.toString(d));

        System.out.println("\nModifying the value at index 1 to 50 in array d\n");
        d[1] = 50;

        System.out.println("After modification");
        System.out.println("Array c: " + Arrays.toString(c));
        System.out.println("Array d: " + Arrays.toString(d));
        System.out.println("**Tutaj wartość c[1] także się zmieniła, ponieważ to typ referencyjny\n");
    }
}
```

| Właściwość                   | Typy prymitywne                                                      | Typy obiektowe                                      |
| ---------------------------- | -------------------------------------------------------------------- | --------------------------------------------------- |
| **Pochodzenie**              | Predefiniowane w języku                                              | Tworzone przez użytkownika                          |
| **Struktura przechowywania** | Przechowywane na stosie                                              | Referencja na stosie, obiekt na stercie             |
| **Podczas kopiowania**       | Tworzy nową zmienną z taką samą wartością                            | Tworzy nową referencję wskazującą na ten sam obiekt |
| **Zmiany w kopii**           | Nie wpływają na oryginał                                             | Wpływają na oryginał, jeśli obiekt jest mutowalny   |
| **Wartość domyślna**         | Nie mają `null` jako wartości domyślnej                              | Domyślnie `null`                                    |
| **Przykłady**                | `byte`, `short`, `int`, `long`, `float`, `double`, `char`, `boolean` | `array`, `String`, klasy, interfejsy                |


 Porównanie z C++
✅ W C++ również istnieją typy prymitywne (int, char, float, double, bool) i typy obiektowe (np. klasy, tablice, std::string, std::vector).
✅ W C++ typy prymitywne także przechowywane są bezpośrednio na stosie, a przy kopiowaniu tworzą osobną kopię wartości (zmiana kopii nie wpływa na oryginał).
✅ W C++ typy obiektowe są zazwyczaj przechowywane na stosie lub stercie w zależności od sposobu tworzenia:
Obiekty tworzone przez new są przechowywane na stercie (heap), a zmienne przechowują wskaźniki do nich.
Przy kopiowaniu wskaźników, obie zmienne wskazują na ten sam obiekt, więc zmiany wpływają na oryginał.
Przy kopiowaniu obiektu (bez wskaźników) tworzy się kopia obiektu (jeśli klasa posiada konstruktor kopiujący).
✅ W Javie wszystkie obiekty są alokowane na stercie, a zmienne obiektowe przechowują referencje (odpowiednik wskaźników w C++), ale Java nie posiada wskaźników jawnych ani operacji arytmetyki wskaźników jak C++.
✅ Java nie posiada destruktorów jak w C++, a zarządzanie pamięcią odbywa się automatycznie przez garbage collector, podczas gdy w C++ programista musi ręcznie zwalniać pamięć.


| **Aspekt**                      | **Java**                                                                       | **C++**                                                              |
| ------------------------------- | ------------------------------------------------------------------------------ | -------------------------------------------------------------------- |
| **Typy prymitywne**             | 8 typów (`int`, `char`, `float`, `double`, `boolean`, `byte`, `short`, `long`) | `int`, `char`, `float`, `double`, `bool`, `short`, `long`            |
| **Typy obiektowe**              | Wszystkie obiekty: `String`, `Array`, klasy, interfejsy                        | Klasy, `std::string`, `std::vector`, tablice, struktury              |
| **Przechowywanie prymitywów**   | Na stosie (stack)                                                              | Na stosie (stack)                                                    |
| **Przechowywanie obiektów**     | Obiekty zawsze na stercie (heap), referencja na stosie                         | Możliwość alokacji na stosie lub stercie (`new` + wskaźniki)         |
| **Kopiowanie prymitywów**       | Tworzy nową kopię wartości                                                     | Tworzy nową kopię wartości                                           |
| **Kopiowanie obiektów**         | Kopiuje referencję, obie zmienne wskazują na ten sam obiekt                    | Kopiuje wskaźnik (ten sam obiekt) lub obiekt (konstruktor kopiujący) |
| **Zarządzanie pamięcią**        | Automatyczne (Garbage Collector)                                               | Ręczne (`delete`), RAII                                              |
| **Wskaźniki**                   | Brak jawnych wskaźników                                                        | Wskaźniki + arytmetyka wskaźników                                    |
| **Destruktory**                 | Brak destruktorów                                                              | Destruktory w klasach                                                |
| **Domyślna wartość referencji** | `null`                                                                         | Wskaźniki mogą być `nullptr`                                         |
| **Bezpieczeństwo pamięci**      | Wyższe, brak manipulacji wskaźnikami                                           | Niższe, możliwe błędy wskaźników                                     |
