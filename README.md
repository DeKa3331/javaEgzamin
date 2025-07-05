# javaEgzamin
notatkidoEgzaminu

Podstawy Javy
1Typy proste, obiekty, referencje na obiekty - analiza porównawcza Javy z C++.
https://www.geeksforgeeks.org/primitive-data-type-vs-object-data-type-in-java-with-examples/






2Czym jest klonowanie i kopiowanie obiektu?
https://www.geeksforgeeks.org/cloneable-interface-in-java/
https://www.baeldung.com/java-copy-constructor

Klonowanie i kopiowanie obiektu w Javie
Klonowanie obiektu w Javie to proces tworzenia nowego obiektu, który ma takie same wartości pól jak obiekt istniejący. Aby umożliwić klonowanie, klasa musi implementować interfejs Cloneable oraz nadpisać metodę clone() z klasy Object.

Przykład:

java
public class Person implements Cloneable {
    String name;
    public Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}
Wywołanie Person p2 = (Person) p1.clone(); tworzy kopię obiektu p1.

Rodzaje klonowania:

Płytkie (shallow copy): kopiowane są wartości pól prymitywnych oraz referencje do obiektów, ale same obiekty zagnieżdżone nie są kopiowane.

Głębokie (deep copy): kopiowane są także obiekty referencyjne wewnątrz, dzięki czemu nowy obiekt jest całkowicie niezależny od oryginału.

Kopiowanie obiektu można również realizować poprzez:

Konstruktor kopiujący: tworzenie nowego obiektu i przypisanie wartości pól ręcznie.

Metodę kopiującą: np. public Person copy(), która zwraca nowy obiekt z tymi samymi wartościami pól.

Różnica:

Klonowanie wykorzystuje clone(), wymaga Cloneable, jest zautomatyzowane, ale mniej elastyczne.

Kopiowanie przez konstruktor/metodę daje pełną kontrolę nad procesem kopiowania (np. głębokiego), ale wymaga ręcznego napisania logiki kopiowania.

Podsumowanie: Klonowanie i kopiowanie w Javie służy do tworzenia nowej instancji z takimi samymi danymi jak obiekt źródłowy, ale różnią się sposobem realizacji oraz zakresem kontroli nad procesem kopiowania.

## 3. Omów składnię i działanie konstruktora. Przedstaw przykład wywołania w ramach konstruktora, konstruktora tej samej klasy oraz klasy nadrzędnej

**Źródła do nauki:**
- [Constructors](https://docs.oracle.com/javase/tutorial/java/javaOO/constructors.html)
- [Arguments](https://docs.oracle.com/javase/tutorial/java/javaOO/arguments.html)
- [this keyword](https://docs.oracle.com/javase/tutorial/java/javaOO/thiskey.html)
- [super keyword](https://docs.oracle.com/javase/tutorial/java/IandI/super.html)

---

### Czym jest konstruktor?

Konstruktor to **specjalna metoda uruchamiana podczas tworzenia obiektu za pomocą `new`**. Konstruktor:

- nosi nazwę klasy,
- **nie posiada typu zwracanego (nawet `void`),**
- służy do inicjalizacji pól obiektu.

---

### Przykład podstawowego konstruktora:

```java
public class Person {
    String name;
    int age;

    public Person(String name, int age) { // konstruktor
        this.name = name;
        this.age = age;
    }
}
Przykład konstruktora tej samej klasy:

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
Przykład konstruktora klasy nadrzednej (super)
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

4Wymień i omów wszystkie sposoby użycia słowa kluczowego final.
https://www.baeldung.com/java-final
