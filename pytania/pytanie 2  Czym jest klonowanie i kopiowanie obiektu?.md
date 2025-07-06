Cloneable Interface w Javie
Ostatnia aktualizacja: 24 listopada 2020

Co to jest Cloneable?
Interfejs java.lang.Cloneable to interfejs znacznikowy (marker interface) w Javie, wprowadzony w JDK 1.0.
Klasa Object posiada metodę clone(). Implementacja interfejsu Cloneable przez klasę umożliwia legalne użycie metody Object.clone(), pozwalając na kopiowanie pola-po-polu obiektu (shallow copy).

Dzięki temu możliwe jest klonowanie obiektów bez użycia operatora new.
```
public interface Cloneable
```
Przykład 1: Klonowanie obiektu bez implementacji Cloneable
Jeśli spróbujesz sklonować obiekt klasy, która nie implementuje interfejsu Cloneable, otrzymasz wyjątek CloneNotSupportedException.
```
// Java program demonstrating CloneNotSupportedException

import java.io.*;
import java.util.*;

class Student {
    String name = null;
    int id = 0;

    Student() {}

    Student(String name, int id) {
        this.name = name;
        this.id = id;
    }

    public static void main(String[] args) {
        Student s1 = new Student("Ashish", 121);
        Student s2 = s1.clone(); // Błąd
    }
}
```

Przykład 2: Poprawne użycie Cloneable
Klasy implementujące Cloneable powinny nadpisać metodę clone() (która w Object jest chroniona), aby umożliwić jej wywołanie.

```
// Java program illustrating Cloneable interface

import java.lang.Cloneable;

class A implements Cloneable {
    int i;
    String s;

    public A(int i, String s) {
        this.i = i;
        this.s = s;
    }

    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}

public class Test {
    public static void main(String[] args) throws CloneNotSupportedException {
        A a = new A(20, "GeeksForGeeks");

        // Klonowanie obiektu 'a'
        A b = (A) a.clone();

        System.out.println(b.i);
        System.out.println(b.s);
    }
}
```
Deep Copy za pomocą clone()
Deep Copy (głębokie kopiowanie) polega na utworzeniu dokładnej kopii oryginalnego obiektu, z alokacją osobnej pamięci i skopiowaniem zawartości obiektu, tak aby zmiany w oryginalnym obiekcie nie wpływały na sklonowany obiekt.

Metoda clone() może tworzyć zarówno kopię płytką (shallow copy), jak i głęboką (deep copy), w zależności od implementacji.

Przykład Deep Copy:
```
// Java program demonstrating deep copy using clone()

class Test {
    int x, y;
}

class Test2 implements Cloneable {
    int a, b;
    Test c = new Test();

    public Object clone() throws CloneNotSupportedException {
        Test2 t = (Test2) super.clone();
        t.c = new Test(); // alokacja nowego obiektu
        return t;
    }
}

public class Main {
    public static void main(String args[]) throws CloneNotSupportedException {
        Test2 t1 = new Test2();
        t1.a = 10;
        t1.b = 20;
        t1.c.x = 30;
        t1.c.y = 40;

        Test2 t3 = (Test2) t1.clone();
        t3.a = 100;
        t3.c.x = 300; // zmiana w sklonowanym obiekcie

        System.out.println(t1.a + " " + t1.b + " " + t1.c.x + " " + t1.c.y);
        System.out.println(t3.a + " " + t3.b + " " + t3.c.x + " " + t3.c.y);
    }
}
```

Ważne uwagi:
✅ Interfejs Cloneable nie zawiera metody clone() – umożliwia jedynie, aby Object.clone() działał bez wyjątku.

✅ Aby klasa mogła być klonowana:

musi implementować interfejs Cloneable,

powinna nadpisać metodę clone().

✅ Wywołanie clone() poprzez refleksję nie gwarantuje sukcesu, jeśli obiekt nie implementuje Cloneable.

✅ Domyślnie metoda clone() wykonuje shallow copy (kopiuje pola-po-polach, bez głębokiego kopiowania referencji). Aby wykonać deep copy, należy jawnie sklonować pola obiektowe wewnątrz metody clone().



Czy klonowanie to to samo co kopiowanie?
1️⃣ Kopiowanie
Ogólne pojęcie oznaczające tworzenie nowej zmiennej z taką samą zawartością jak w oryginale.

W typach prymitywnych kopiowanie tworzy nową zmienną z identyczną wartością.

W przypadku typów obiektowych kopiowanie może być:

płytkie (shallow copy) – kopiuje referencję (obie zmienne wskazują na ten sam obiekt),

głębokie (deep copy) – tworzy osobny obiekt w pamięci z taką samą zawartością.

2️⃣ Klonowanie
W Javie oznacza specjalny mechanizm kopiowania obiektów za pomocą metody clone().

Wykorzystywane do kopiowania obiektów typu referencyjnego bez new, automatycznie przez JVM.

Wymaga:
✅ implementacji interfejsu Cloneable,
✅ nadpisania metody clone().

Domyślnie wykonuje płytką kopię (shallow copy), ale można zaimplementować deep copy w metodzie clone().

🪐 Podsumowanie:
✅ Kopiowanie jest szerszym pojęciem (kopiowanie wartości, referencji, obiektów ręcznie).

✅ Klonowanie w Javie jest specyficznym sposobem kopiowania obiektów przez clone(), który może realizować shallow lub deep copy, ale zawsze wymaga Cloneable.

✅ Klonowanie = forma kopiowania obiektów w Javie.
