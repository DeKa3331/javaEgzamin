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

