# javaEgzamin

# notatkidoEgzaminu

## Podstawy Javy

### 1. Typy proste, obiekty, referencje na obiekty - analiza porównawcza Javy z C++

**Źródło do nauki:**

* [Primitive vs Object Data Types in Java](https://www.geeksforgeeks.org/primitive-data-type-vs-object-data-type-in-java-with-examples/)

**Typy proste (primitive types):**

* `int`, `double`, `char`, `boolean`, `float`, `byte`, `short`, `long`.
* Przechowują bezpośrednio wartość, nie są obiektami.
* Szybkie, mniej pamięciożerne.
* Mają domyślne wartości (`0` dla `int`, `false` dla `boolean`).

**Typy obiektowe (reference types):**

* Obiekty klas oraz tablice.
* Zmienna przechowuje referencję (adres w pamięci) do obiektu, a nie sam obiekt.

Przykład:

```java
String s = "Hello";
```

**Java vs C++:**

* Java **nie posiada wskaźników**, ale referencje działają podobnie (odwołują się do obiektu w pamięci).
* W C++ obiekty mogą być przekazywane przez wskaźnik, referencję lub przez wartość. W Javie obiekty zawsze są przekazywane przez referencję.
* W C++ obiekty mogą być tworzone na stosie lub stercie. W Javie obiekty tworzone są zawsze na stercie.

**Podsumowanie:**

* Java oddziela typy proste od obiektowych.
* Obiekty operują na referencjach.
* Java upraszcza zarządzanie pamięcią w porównaniu do C++.

---

### 2. Czym jest klonowanie i kopiowanie obiektu?

**Źródła do nauki:**

* [Cloneable interface in Java](https://www.geeksforgeeks.org/cloneable-interface-in-java/)
* [Copy Constructor in Java](https://www.baeldung.com/java-copy-constructor)

**Klonowanie obiektu** w Javie to proces tworzenia nowego obiektu z takimi samymi wartościami pól jak obiekt istniejący.

Aby umożliwić klonowanie:

* Klasa musi implementować interfejs `Cloneable`.
* Należy nadpisać metodę `clone()` z klasy `Object`.

Przykład:

```java
public class Person implements Cloneable {
    String name;
    public Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}
```

Wywołanie `Person p2 = (Person) p1.clone();` tworzy kopię obiektu `p1`.

**Rodzaje klonowania:**

* **Płytkie (shallow copy)** – kopiowane są wartości pól prymitywnych oraz referencje, ale same obiekty zagnieżdżone nie są kopiowane.
* **Głębokie (deep copy)** – kopiowane są także obiekty referencyjne, dzięki czemu kopia jest niezależna od oryginału.

**Kopiowanie obiektu można również zrealizować poprzez:**

* Konstruktor kopiujący (copy constructor).
* Metodę kopiującą zwracającą nowy obiekt.

**Różnica:**

* `clone()` jest zautomatyzowane, wymaga `Cloneable`, ale daje mniej kontroli.
* Kopiowanie przez konstruktor lub metodę daje pełną kontrolę i możliwość tworzenia kopii głębokiej.

**Podsumowanie:** Klonowanie i kopiowanie w Javie pozwala tworzyć nowe obiekty z tymi samymi danymi, różni się jednak sposobem realizacji oraz zakresem kontroli.

---

## 3. Omów składnię i działanie konstruktora. Przedstaw przykład wywołania w ramach konstruktora, konstruktora tej samej klasy oraz klasy nadrzędnej

**Źródła do nauki:**

* [Constructors](https://docs.oracle.com/javase/tutorial/java/javaOO/constructors.html)
* [Arguments](https://docs.oracle.com/javase/tutorial/java/javaOO/arguments.html)
* [this keyword](https://docs.oracle.com/javase/tutorial/java/javaOO/thiskey.html)
* [super keyword](https://docs.oracle.com/javase/tutorial/java/IandI/super.html)

**Czym jest konstruktor?**

Konstruktor to specjalna metoda uruchamiana podczas tworzenia obiektu za pomocą `new`. Konstruktor:

* nosi nazwę klasy,
* **nie posiada typu zwracanego (nawet `void`),**
* służy do inicjalizacji pól obiektu.

**Przykład podstawowego konstruktora:**

```java
public class Person {
    String name;
    int age;

    public Person(String name, int age) { // konstruktor
        this.name = name;
        this.age = age;
    }
}
```

**Przykład konstruktora tej samej klasy (`this(...)`):**

```java
public class Person {
    String name;
    int age;

    public Person(String name) {
        this(name, 0); // wywołanie innego konstruktora tej samej klasy
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

**Przykład konstruktora klasy nadrzędnej (`super(...)`):**

```java
public class Animal {
    String species;

    public Animal(String species) {
        this.species = species;
    }
}

public class Dog extends Animal {
    String name;

    public Dog(String name) {
        super("Dog"); // wywołanie konstruktora klasy nadrzędnej
        this.name = name;
    }
}
```

**Podsumowanie:**
✅ Konstruktor służy do inicjalizacji obiektu.
✅ `this(...)` wywołuje inny konstruktor tej samej klasy.
✅ `super(...)` wywołuje konstruktor klasy nadrzędnej.
✅ Oba wywołania muszą być pierwszą instrukcją w konstruktorze.

---

## 4. Wymień i omów wszystkie sposoby użycia słowa kluczowego `final`

**Źródło do nauki:**

* [Baeldung: Java `final`](https://www.baeldung.com/java-final)

Słowo kluczowe `final` może być użyte do:

### 1️⃣ Zmiennych

* `final` zmienna nie może być zmieniona po przypisaniu wartości.
* Stosowane w polach klas, zmiennych lokalnych oraz argumentach metod.

```java
final int x = 5;
// x = 10; // błąd kompilacji
```

### 2️⃣ Metod

* `final` metoda nie może być przesłonięta (`override`) w klasach dziedziczących.

```java
public class Parent {
    public final void show() {
        System.out.println("Hello");
    }
}
```

### 3️⃣ Klas

* `final` klasa nie może być dziedziczona.
* Stosowane np. w klasach `String`, `Math`.

```java
public final class Utility {
    // metody pomocnicze
}
```

---

### Dodatkowe informacje:

✅ `final` zwiększa bezpieczeństwo i czytelność kodu.
✅ Można łączyć `final` z `static` (np. `public static final double PI = 3.1415;`).
✅ `final` w argumentach metody uniemożliwia zmianę referencji wewnątrz metody:

```java
public void process(final String data) {
    // data = "new"; // błąd kompilacji
}
```

---

### Podsumowanie:

* `final` zmienna → wartość niezmienna.
* `final` metoda → metoda nie może być przesłonięta.
* `final` klasa → klasa nie może być dziedziczona.

---

## Programowanie obiektowe

### Omów porównawczo dziedziczenie klas i implementację interfejsów

**Źródło do nauki:**

* [Extends vs Implements in Java (GeeksforGeeks)](https://www.geeksforgeeks.org/extends-vs-implements-in-java/)

**Dziedziczenie klas (`extends`)** pozwala klasie potomnej przejąć pola i metody klasy bazowej, wspiera ponowne użycie kodu oraz przesłanianie metod (`@Override`). Java nie wspiera wielodziedziczenia klas.

**Implementacja interfejsów (`implements`)** umożliwia klasie implementowanie wielu interfejsów, co pozwala na wielodziedziczenie zachowań. Interfejsy definiują kontrakty, które klasa musi zaimplementować, nie zawierają pól instancyjnych (poza `static final`).

---

### Omów porównawczo klasy abstrakcyjne i interfejsy

**Źródło do nauki:**

* [Interface vs Abstract Class in Java (Baeldung)](https://www.baeldung.com/java-interface-vs-abstract-class)

**Klasy abstrakcyjne:**

* Mogą posiadać metody abstrakcyjne i metody z implementacją.
* Mogą posiadać pola instancyjne.
* Wspierają dziedziczenie i umożliwiają częściową implementację zachowań.
* Klasa może dziedziczyć tylko po jednej klasie abstrakcyjnej.

**Interfejsy:**

* Mogą posiadać metody abstrakcyjne oraz `default` i `static` z implementacją.
* Brak pól instancyjnych poza `public static final`.
* Umożliwiają wielodziedziczenie zachowań.
* Stosowane do definiowania kontraktów między klasami.

---

### Omów polimorfizm

**Źródło do nauki:**

* [Polymorphism in Java (Baeldung)](https://www.baeldung.com/java-polymorphism)

**Polimorfizm** umożliwia wywoływanie metod obiektów różnych klas za pomocą wspólnego typu referencji (np. interfejsu lub klasy bazowej). Pozwala na późne wiązanie (dynamiczne wiązanie metod), zwiększa elastyczność kodu i umożliwia jego rozszerzanie bez zmiany istniejących implementacji.

Przykład:

```java
Animal a = new Dog(); // Dog jest Animalem
a.makeSound(); // wywoła wersję metody z klasy Dog
```

---

### Omów enkapsulację. Przedstaw modyfikatory dostępu w kontekście enkapsulacji. Uwzględnij zagnieżdżenie klas

**Źródło do nauki:**

* [Public vs Protected vs Package vs Private (GeeksforGeeks)](https://www.geeksforgeeks.org/public-vs-protected-vs-package-vs-private-access-modifier-in-java/)

**Enkapsulacja** polega na ukrywaniu implementacji klasy oraz kontrolowaniu dostępu do danych poprzez metody dostępowe (`gettery`, `settery`).

**Modyfikatory dostępu:**

* `public` – dostęp z każdego miejsca.
* `protected` – dostęp w pakiecie i w klasach dziedziczących.
* `package-private` (brak modyfikatora) – dostęp w obrębie pakietu.
* `private` – dostęp tylko w obrębie tej klasy.

**Zagnieżdżenie klas (klasy wewnętrzne):** pozwala organizować kod w logiczne całości, umożliwia dostęp do prywatnych pól klasy zewnętrznej, wspiera enkapsulację i lepsze grupowanie powiązanych elementów.

---

### Przedstaw rodzaje asocjacji między klasami. Zilustruj przykładami i schematami UML

**Źródło do nauki:**

* [Composition, Aggregation and Association in Java (Baeldung)](https://www.baeldung.com/java-composition-aggregation-association)

**Rodzaje asocjacji:**

* **Asocjacja** – ogólne powiązanie między klasami (np. `Teacher` uczy `Student`).
* **Agregacja** – "ma, ale może istnieć osobno" (np. `Team` posiada `Player`).
* **Kompozycja** – "ma i nie może istnieć osobno" (np. `House` posiada `Room`).

**Schemat UML:**

* Asocjacja: zwykła linia.
* Agregacja: linia z pustym rombem.
* Kompozycja: linia z wypełnionym rombem.

**Przykład kodu:**

```java
class Team {
    private List<Player> players; // agregacja
}

class House {
    private Room room; // kompozycja
}
```

https://www.geeksforgeeks.org/public-vs-protected-vs-package-vs-private-access-modifier-in-java/
Przedstaw rodzaje asocjacji między klasami. Zilustruj przykładami i schematami UML.
https://www.baeldung.com/java-composition-aggregation-association

## Wzorce projektowe

### Singleton - konstrukcja, zastosowanie, ograniczenia i problemy

**Źródło do nauki:**

* [Singleton (Baeldung)](https://www.baeldung.com/java-singleton)


Singleton to wzorzec projektowy, który gwarantuje, że dana klasa będzie miała tylko jedną instancję w całym programie.

Jak to osiągnąć?

Konstruktor klasy jest prywatny (private), więc obiekty nie mogą być tworzone spoza klasy.

Posiada statyczne pole przechowujące jedyną instancję.

Udostępnia statyczną metodę (np. getInstance()), która zwraca tę instancję — tworzy ją, jeśli jeszcze nie istnieje.

```
public class Singleton {
    private static Singleton instance;

    private Singleton() { }

    public static Singleton getInstance() {
        if(instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

Zastosowanie:

Zarządzanie połączeniem z bazą danych.

Logger, konfiguracja aplikacji.

Dostęp do zasobów systemowych.

Ograniczenia i problemy:

Nie jest bezpieczny wątkowo (w prostym wydaniu) — wymaga synchronizacji lub wykorzystania innych wzorców (np. enum).

Trudny do testowania (globalny stan).

Może powodować problemy w środowiskach wielowątkowych lub podczas ładowania klas.

### Budowniczy - konstrukcja i zastosowanie

**Źródło do nauki:**

* [Builder (Refactoring.Guru)](https://refactoring.guru/pl/design-patterns/builder)


Budowniczy pozwala na tworzenie złożonych obiektów krok po kroku, oddzielając konstrukcję od reprezentacji.

Umożliwia tworzenie obiektów z różnymi konfiguracjami bez konieczności definiowania wielu konstruktorów.


public class House {
    private int windows;
    private int doors;
    private boolean hasGarage;

    private House(Builder builder) {
        this.windows = builder.windows;
        this.doors = builder.doors;
        this.hasGarage = builder.hasGarage;
    }

    public static class Builder {
        private int windows;
        private int doors;
        private boolean hasGarage;

        public Builder setWindows(int windows) {
            this.windows = windows;
            return this;
        }

        public Builder setDoors(int doors) {
            this.doors = doors;
            return this;
        }

        public Builder setGarage(boolean hasGarage) {
            this.hasGarage = hasGarage;
            return this;
        }

        public House build() {
            return new House(this);
        }
    }
}
House house = new House.Builder()
                .setWindows(4)
                .setDoors(2)
                .setGarage(true)
                .build();
Zastosowanie:

Gdy konstrukcja obiektu jest skomplikowana.

Gdy chcemy uniknąć wielu przeciążonych konstruktorów.

Umożliwia czytelny i elastyczny sposób tworzenia obiektów.

### Dekorator - konstrukcja i zastosowanie

**Źródło do nauki:**

* [Decorator (Refactoring.Guru)](https://refactoring.guru/pl/design-patterns/decorator)


Dekorator pozwala na dynamiczne rozszerzanie funkcjonalności obiektów bez zmiany ich klasy.

Polega na "opakowaniu" obiektu w inny obiekt, który dodaje nowe zachowania.

```
interface Coffee {
    String getDescription();
    double getCost();
}

class SimpleCoffee implements Coffee {
    public String getDescription() { return "Simple coffee"; }
    public double getCost() { return 1.0; }
}

class MilkDecorator implements Coffee {
    private Coffee coffee;

    public MilkDecorator(Coffee coffee) {
        this.coffee = coffee;
    }

    public String getDescription() {
        return coffee.getDescription() + ", milk";
    }

    public double getCost() {
        return coffee.getCost() + 0.5;
    }
}
```

Zastosowanie:

Gdy chcemy dynamicznie dodawać funkcje do obiektów.

Alternatywa do dziedziczenia.

Popularny w GUI, streamach, obsłudze wejścia/wyjścia.

---

## Kolekcje

### Omów interfejs Collection

**Źródło do nauki:**

* [Collection (Java Docs)](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html)

Collection jest podstawowym interfejsem reprezentującym grupę obiektów, bez określonego porządku ani indeksów.

Podstawowe metody:

add(E e) — dodaje element.

remove(Object o) — usuwa element.

contains(Object o) — sprawdza, czy element jest obecny.

size() — zwraca liczbę elementów.

iterator() — zwraca iterator do przechodzenia po elementach.

Hierarchia:

Collection jest nadinterfejsem dla:

List (kolekcja z uporządkowanym dostępem, np. ArrayList, LinkedList)

Set (kolekcja bez duplikatów)

Queue (kolekcja FIFO)


### Porównaj klasy LinkedList i ArrayList

**Źródło do nauki:**

* [ArrayList vs LinkedList (Baeldung)](https://www.baeldung.com/java-arraylist-linkedlist)

Collection jest podstawowym interfejsem reprezentującym grupę obiektów, bez określonego porządku ani indeksów.

Podstawowe metody:

add(E e) — dodaje element.

remove(Object o) — usuwa element.

contains(Object o) — sprawdza, czy element jest obecny.

size() — zwraca liczbę elementów.

iterator() — zwraca iterator do przechodzenia po elementach.

Hierarchia:

Collection jest nadinterfejsem dla:

List (kolekcja z uporządkowanym dostępem, np. ArrayList, LinkedList)

Set (kolekcja bez duplikatów)

Queue (kolekcja FIFO)

### W C++ jest typ std::multimap. Jak zrekonstruować jego działanie w Javie?

**Źródła do nauki:**

* [std::multimap (C++ Reference)](https://en.cppreference.com/w/cpp/container/multimap)
* [Map (Java Docs)](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html)


Multimap to mapa, która pozwala na mapowanie jednego klucza na wiele wartości.

W Javie brak jest natywnego Multimap w standardzie, ale można zbudować podobną funkcjonalność:

Użyć Map<K, List<V>> lub Map<K, Set<V>>.

```
Map<String, List<Integer>> multimap = new HashMap<>();

// dodawanie wartości
multimap.computeIfAbsent("key1", k -> new ArrayList<>()).add(10);
multimap.computeIfAbsent("key1", k -> new ArrayList<>()).add(20);
```

---

## Pliki

### Readery - podział, różnice, zastosowanie

**Źródła do nauki:**

* [Reader Class (GeeksforGeeks)](https://www.geeksforgeeks.org/java-io-reader-class-java/)
* [BufferedReader (GeeksforGeeks)](https://www.geeksforgeeks.org/java-io-bufferedreader-class-java/)
* [InputStreamReader (GeeksforGeeks)](https://www.geeksforgeeks.org/inputstreamreader-class-in-java/)


Reader to abstrakcyjna klasa do czytania znaków z różnych źródeł.

Najczęściej używane klasy:

InputStreamReader — konwertuje bajty na znaki, pozwala czytać dane z InputStream jako znaki (np. z pliku lub sieci).

BufferedReader — buforuje dane z innego readera, poprawia wydajność oraz umożliwia czytanie po liniach (readLine()).

### Serializacja obiektów. Zapis i odczyt obiektów z pliku

```
try (BufferedReader br = new BufferedReader(new InputStreamReader(new FileInputStream("file.txt")))) {
    String line;
    while ((line = br.readLine()) != null) {
        System.out.println(line);
    }
} catch (IOException e) {
    e.printStackTrace();
}
```

**Źródło do nauki:**

* [Serialization (Baeldung)](https://www.baeldung.com/java-serialization)

Serializacja to proces zapisu obiektu do strumienia bajtów (np. do pliku), tak aby można go było później odczytać (deserializacja).

Wymagania:

Klasa musi implementować interfejs Serializable.

Pola oznaczone jako transient nie są serializowane

```
Przykład zapisu i odczytu:

java
Kopiuj
Edytuj
// zapis
try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("obj.dat"))) {
    oos.writeObject(obj);
}

// odczyt
try (ObjectInputStream ois = new ObjectInputStream(new FileInputStream("obj.dat"))) {
    MyClass obj = (MyClass) ois.readObject();
}
```

---

## Wyjątki

### Omów składnię i zastosowanie wyjątków

**Źródło do nauki:**

* [Exceptions in Java (GeeksforGeeks)](https://www.geeksforgeeks.org/exceptions-in-java/)

Wyjątek to zdarzenie, które zakłóca normalny przepływ programu.

Składnia:

try — blok kodu, który może rzucić wyjątek.

catch — blok obsługujący wyjątek.

finally — blok wykonywany zawsze, niezależnie od wystąpienia wyjątku.

throw — ręczne rzucenie wyjątku.

throws — deklaracja, że metoda może rzucić wyjątek.

### Wyjątek Exception a RuntimeException, wyjaśnij różnicę i podaj przykład

**Źródła do nauki:**

* [Exception (Java Docs)](https://docs.oracle.com/javase/8/docs/api/java/lang/Exception.html)
* [RuntimeException (Java Docs)](https://docs.oracle.com/javase/8/docs/api/java/lang/RuntimeException.html)

Exception (checked exception):

Musi być obsłużony lub zadeklarowany (np. IOException).

Wymaga jawnej obsługi.

RuntimeException (unchecked exception):

Nie wymaga deklaracji ani obsługi.

Zwykle oznacza błędy programistyczne (np. NullPointerException, ArithmeticException).

Przykład:

```
try {
    int a = 10 / 0; // rzuca ArithmeticException (RuntimeException)
} catch (ArithmeticException e) {
    System.out.println("Dzielenie przez zero");
}
```

### Wyrażenie try-with-resources, składnia, przypadki użycia

**Źródło do nauki:**

* [Try-With-Resources (Oracle)](https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html)


Try-with-resources automatycznie zamyka zasoby implementujące AutoCloseable (np. strumienie, czytniki).

Przykład:

```
try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
    String line = br.readLine();
    System.out.println(line);
} catch (IOException e) {
    e.printStackTrace();
}
// br automatycznie zamknięty po wyjściu z try
```

---

## Strumienie

### Opisz trzy metody pośrednie w strumieniu

**Źródło do nauki:**

* [Intermediate Stream Methods (GeeksforGeeks)](https://www.geeksforgeeks.org/intermediate-methods-of-stream-in-java/)

Metody pośrednie (intermediate):

filter(Predicate) — filtruje elementy, przepuszcza tylko spełniające warunek.

map(Function) — mapuje elementy na inne (transformacja).

sorted() — sortuje elementy według naturalnego porządku lub komparatora.

### Omów kolektory

**Źródło do nauki:**

* [Collectors (Baeldung)](https://www.baeldung.com/java-8-collectors)

Kolektory (Collectors) służą do agregowania elementów strumienia do kolekcji, sumowania, grupowania itp.

```
List<String> collected = list.stream()
                             .filter(s -> s.startsWith("a"))
                             .collect(Collectors.toList());
```
Popularne kolektory:

toList(), toSet() — kolekcja listy lub zbioru.

joining() — łączenie elementów w jeden String.

groupingBy() — grupowanie według klucza.

partitioningBy() — podział na dwie grupy według warunku.

counting() — zliczanie elementów.

---

## Testowanie

### Przedstaw motywację do stosowania testów, omów Test Driven Development

**Źródło do nauki:**

* [Unit Testing vs TDD (Baeldung)](https://www.baeldung.com/cs/unit-testing-vs-tdd)


Motywacje do testowania:

Wykrywanie błędów na wczesnym etapie.

Utrzymanie jakości i niezawodności kodu.

Dokumentacja działania.

Ułatwienie refaktoryzacji.

Test Driven Development (TDD):

Najpierw piszemy testy (które początkowo nie przechodzą).

Następnie piszemy kod, by testy przeszły.

Na końcu refaktoryzujemy kod bez zmiany zachowania.

### Parametryzacja testów

**Źródło do nauki:**

* [Parameterized Tests (Baeldung)](https://www.baeldung.com/parameterized-tests-junit-5)

Parametryzowane testy pozwalają uruchomić ten sam test wielokrotnie z różnymi zestawami danych.

Przykład (JUnit 5):

```
@ParameterizedTest
@ValueSource(strings = {"racecar", "radar", "madam"})
void testPalindrome(String candidate) {
    assertTrue(isPalindrome(candidate));
}
```

---

## Pakiety

### Zasady tworzenia i zastosowanie pakietów

**Źródło do nauki:**

* [Packages (Oracle)](https://docs.oracle.com/javase/tutorial/java/package/index.html)

Pakiety grupują klasy i interfejsy w logiczne jednostki.
Zalety:

Organizacja kodu.

Unikanie konfliktów nazw.

Kontrola dostępu (pakietowe widoczności).

Ułatwiają modularność.

### Czym są pliki JAR? Omów ich tworzenie i wykorzystanie. Omów manifest.

**Źródło do nauki:**

* [JAR Files (Oracle)](https://docs.oracle.com/javase/tutorial/deployment/jar/index.html)

JAR (Java ARchive) to archiwum plików klas i zasobów, umożliwiające łatwe dystrybuowanie aplikacji.

### Wymień i omów trzy zastosowania Mavena

**Źródło do nauki:**

* [Maven (Baeldung)](https://www.baeldung.com/maven)

Zastosowania:

Budowanie projektów (kompilacja, testy, pakowanie).

Zarządzanie zależnościami (automatyczne pobieranie bibliotek).

Standaryzacja struktury projektu.

### Elementy składowe pliku pom.xml

**Źródło do nauki:**

* [pom.xml Structure (Maven)](https://maven.apache.org/guides/introduction/introduction-to-the-pom.html)



Główne elementy:

project — korzeń pliku.

groupId — unikalny identyfikator organizacji/projektu.

artifactId — nazwa artefaktu (biblioteki/aplikacji).

version — wersja artefaktu.

dependencies — listy zależności.

build — konfiguracja procesu budowania.

---

## Programowanie generyczne

### Typy generyczne a typ Object

**Źródło do nauki:**

* [Generics in Java (Oracle)](https://docs.oracle.com/javase/tutorial/java/generics/types.html)

Generyki pozwalają definiować klasy i metody operujące na typach parametrów, dając bezpieczeństwo typów bez rzutowania.
Różnica:

Bez generyków kolekcje przechowują Object, wymagając rzutowania.

Generyki zapewniają typowanie już podczas kompilacji.

### Ograniczenia typów generycznych

**Źródło do nauki:**

* [Wildcards in Generics (Oracle)](https://docs.oracle.com/javase/tutorial/extra/generics/wildcards.html)

Ograniczenia:

Generyki nie działają z typami prostymi (np. int).

Typy są "usuwane" w czasie kompilacji (type erasure).

Nie można tworzyć instancji parametrów typów (new T()).

Wildcards (? extends T, ? super T) umożliwiają elastyczność typ

### Interfejsy funkcyjne: Supplier, Predicate, Consumer, Function

**Źródło do nauki:**

* [Functional Interfaces (Java Docs)](https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html)

Interfejsy funkcyjne:

Supplier<T> — dostarcza obiekt typu T, nie przyjmuje argumentów.

Predicate<T> — testuje warunek na obiekcie T, zwraca boolean.

Consumer<T> — wykonuje operację na obiekcie T, nie zwraca wyniku.

Function<T,R> — przekształca obiekt T na R.

### Interfejsy funkcyjne a funkcje lambda, implementacja własnego interfejsu funkcyjnego

**Źródła do nauki:**

* [Functional Interfaces (Javatpoint)](https://www.javatpoint.com/java-8-functional-interfaces)
* [Lambda Expressions (Oracle)](https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html)

Interfejs funkcyjny — posiada dokładnie jedną metodę abstrakcyjną.

Funkcje lambda umożliwiają tworzenie anonimowych implementacji interfejsów funkcyjnych w zwięzły sposób.

```
Przykład własnego interfejsu:

java
Kopiuj
Edytuj
@FunctionalInterface
interface MyFunction {
    int apply(int x);
}

// Lambda:
MyFunction square = x -> x * x;
```

### Omów szablon Optional

**Źródło do nauki:**

* [Optional (Baeldung)](https://www.baeldung.com/java-optional)

Optional jest kontenerem na wartość, która może być obecna lub nie (zamiast null).

Zalety:

Unika błędów NullPointerException.

Umożliwia czytelne operacje na wartościach opcjonalnych (map, filter, orElse).

Przykład:

```
Optional<String> optional = Optional.ofNullable(getName());
optional.ifPresent(name -> System.out.println(name));
```
---

## Wątki

### Tworzenie wątku, charakterystyka i porównanie Thread i Runnable

**Źródła do nauki:**

* [Implement Runnable vs Extend Thread (GeeksforGeeks)](https://www.geeksforgeeks.org/implement-runnable-vs-extend-thread-in-java/)
* [Thread start vs run (GeeksforGeeks)](https://www.geeksforgeeks.org/difference-between-thread-start-and-thread-run-in-java)

Tworzenie wątku:

Dziedzicząc po Thread i nadpisując metodę run().

Implementując interfejs Runnable i przekazując instancję do Thread.

Różnice:

Thread	Runnable
Dziedziczy po klasie Thread	Implementuje interfejs Runnable
Nie można dziedziczyć po innej klasie	Można dziedziczyć po innej klasie i implementować Runnable
Uruchamia wątek przez start()	Przekazywany do wątku, start() wywołuje run() Runnable

### Omów synchronizację wątków

**Źródło do nauki:**

* [Synchronization (GeeksforGeeks)](https://www.geeksforgeeks.org/synchronization-in-java/)

Synchronizacja służy do ochrony zasobów współdzielonych przez wiele wątków.

synchronized blok lub metoda zapewnia, że tylko jeden wątek wykonuje kod na raz.

Zapobiega problemom typu race condition.

### Omów cykl życia wątku

**Źródło do nauki:**

* [Thread Lifecycle (Baeldung)](https://www.baeldung.com/java-thread-lifecycle)

Stany wątku:

NEW — wątek utworzony, ale nie uruchomiony.

RUNNABLE — wątek gotowy do działania lub działający.

BLOCKED — czeka na dostęp do synchronizowanego zasobu.

WAITING — czeka na sygnał (np. wait()).

TIMED_WAITING — czeka z limitem czasu (np. sleep()).

TERMINATED — zakończony.

---

## JavaFX

### Porównanie frameworków do tworzenia interfejsu użytkownika

**Źródło do nauki:**

* [AWT vs Swing vs JavaFX (GeeksforGeeks)](https://www.geeksforgeeks.org/java-awt-vs-java-swing-vs-java-fx/)

Cecha	AWT	Swing	JavaFX
Model	Opakowanie nad natywnym UI	Komponenty lekkie, czysto Java	Nowoczesny, bogaty UI
Wygląd	Zależny od platformy	Uniwersalny, temat możliwy	Zaawansowany CSS, stylowanie
Obsługa multimediów	Słaba	Lepsza	Bardzo dobra
Obsługa 3D	Brak	Ograniczona	Pełna obsługa 3D
Nowoczesność	Stary, przestarzały	Popularny, ale zastępowany	Aktualnie rekomendowany


### Czym są wydarzenia i jak je obsługiwać w JavaFX?

**Źródło do nauki:**

* [JavaFX Event Handling (TutorialsPoint)](https://www.tutorialspoint.com/javafx/javafx_event_handling.htm)

Wydarzenia (events) to zdarzenia generowane przez użytkownika (kliknięcie, klawiatura) lub system.

Obsługa:

Dodaj listener (np. setOnAction(e -> { ... })).

Można obsługiwać różne typy wydarzeń (MouseEvent, KeyEvent itd.).

### Omów zależność między typami Scene i Stage w JavaFX

**Źródła do nauki:**

* [Scene (Oracle)](https://docs.oracle.com/javase/8/javafx/api/javafx/scene/Scene.html)
* [Stage (Oracle)](https://docs.oracle.com/javase/8/javafx/api/javafx/stage/Stage.html)


Stage to okno aplikacji (główne lub dodatkowe).

Scene to zawartość okna — hierarchia elementów UI (kontrolki, layouty).

Relacja:

Stage posiada jedną aktualnie wyświetlaną Scene.

Można zmieniać Scene w Stage.

Stage = okno; Scene = zawartość okna.


