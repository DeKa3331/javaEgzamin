1. Kopiowanie obiektu
Kopiowanie to ogólne pojęcie oznaczające tworzenie nowej zmiennej lub obiektu o takiej samej zawartości jak oryginał.

W przypadku typów prymitywnych kopiowanie tworzy nową zmienną z niezależną kopią wartości.

W przypadku typów obiektowych kopiowanie może być:

Płytkie (shallow copy) – kopiuje tylko referencję, więc obie zmienne wskazują na ten sam obiekt.

Głębokie (deep copy) – tworzy nowy, niezależny obiekt z taką samą zawartością.

2. Klonowanie obiektu w Javie
Klonowanie to specjalny mechanizm kopiowania obiektów za pomocą metody clone() z klasy Object.

Aby można było legalnie użyć metody clone(), klasa musi implementować interfejs Cloneable (marker interface).

Jeżeli klasa nie implementuje Cloneable, wywołanie clone() skutkuje wyrzuceniem wyjątku CloneNotSupportedException.

Metoda clone() domyślnie wykonuje shallow copy (kopiuje pola po polu, ale nie tworzy nowych obiektów dla pól będących referencjami).

Aby wykonać deep copy, należy nadpisać metodę clone() tak, by jawnie sklonować pola obiektowe (utworzyć nowe instancje).

3. Interfejs Cloneable
Jest to interfejs znacznikowy (marker interface) – nie zawiera metod, służy tylko do oznaczenia, że klasa wspiera klonowanie.

Implementacja Cloneable zezwala na wywołanie Object.clone() bez wyjątku.

Klasa powinna również nadpisać metodę clone(), ponieważ oryginalna metoda w Object jest chroniona (protected).

4. Przykład poprawnego klonowania
```
class A implements Cloneable {
    int i;
    String s;

    public A(int i, String s) {
        this.i = i;
        this.s = s;
    }

    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone(); // wykonuje shallow copy
    }
}
```
5. Przykład deep copy z użyciem clone()
```
class Test {
    int x, y;
}

class Test2 implements Cloneable {
    int a, b;
    Test c = new Test();

    @Override
    public Object clone() throws CloneNotSupportedException {
        Test2 t = (Test2) super.clone(); // shallow copy
        t.c = new Test();                // nowy obiekt – deep copy pola c
        t.c.x = this.c.x;
        t.c.y = this.c.y;
        return t;
    }
}
```
ROZNICE
| Aspekt            | Kopiowanie                                     | Klonowanie (Java)                                           |
| ----------------- | ---------------------------------------------- | ----------------------------------------------------------- |
| Zakres            | Ogólne pojęcie kopiowania danych               | Specyficzny mechanizm kopiowania obiektów                   |
| Wykonanie         | Można robić ręcznie (np. new + kopiowanie pól) | Poprzez metodę `clone()` z `Cloneable`                      |
| Typ kopiowania    | Płytkie lub głębokie, zależne od implementacji | Domyślnie płytkie, można nadpisać do głębokiego             |
| Wymagania w Javie | Brak                                           | Implementacja interfejsu `Cloneable` i nadpisanie `clone()` |

Podsumowanie
Cloneable to marker interface pozwalający na użycie metody clone() bez błędu.

Domyślna metoda clone() wykonuje shallow copy, czyli kopiuje pola po polu, ale nie tworzy nowych obiektów dla referencji.

Aby wykonać deep copy, trzeba nadpisać metodę clone() i jawnie sklonować pola obiektowe.

Klonowanie jest więc szczególnym sposobem kopiowania obiektów w Javie, ściśle powiązanym z interfejsem Cloneable.

Jeśli klasa nie implementuje Cloneable, wywołanie clone() skutkuje wyjątkiem CloneNotSupportedException.


# notatki

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
