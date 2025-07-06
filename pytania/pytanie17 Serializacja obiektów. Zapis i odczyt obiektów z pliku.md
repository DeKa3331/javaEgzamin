Serializacja obiektów w Javie – zapis i odczyt z pliku
1. Co to jest serializacja?
Serializacja to proces przekształcania obiektu w strumień bajtów, który można zapisać do pliku, przesłać po sieci lub przechować w pamięci.

Deserializacja to proces odtworzenia obiektu z tego strumienia bajtów.

Umożliwia trwałe przechowywanie stanu obiektu lub przesyłanie go między różnymi systemami.

2. Jak działa serializacja w Javie?
Klasa musi implementować interfejs java.io.Serializable (jest to interfejs markerowy – nie zawiera metod).

JVM podczas serializacji zapisuje stan wszystkich pól obiektu (poza tymi oznaczonymi jako transient).

Można kontrolować wersję serializacji przez pole private static final long serialVersionUID.

Jeśli zmieni się klasa, a serialVersionUID się nie zgadza, podczas deserializacji wystąpi wyjątek.

3. Zapis obiektu do pliku (serializacja)
Do zapisu używamy klas:

FileOutputStream – strumień bajtowy do pliku,

ObjectOutputStream – opakowuje FileOutputStream i pozwala zapisać obiekty.

Przykład zapisu obiektu:
```
import java.io.*;

public class SerializacjaPrzyklad {
    public static void main(String[] args) {
        Osoba osoba = new Osoba("Jan", 30);

        try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("osoba.ser"))) {
            oos.writeObject(osoba);
            System.out.println("Obiekt został zapisany do pliku.");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

class Osoba implements Serializable {
    private static final long serialVersionUID = 1L;

    private String imie;
    private int wiek;

    public Osoba(String imie, int wiek) {
        this.imie = imie;
        this.wiek = wiek;
    }

    @Override
    public String toString() {
        return imie + " (" + wiek + " lat)";
    }
}
```


# PRZYKLADY

Co to jest serializacja?
Serializacja to proces konwersji obiektu w ciąg bajtów, który pozwala na:

zapisanie obiektu do pliku,

przesłanie go przez sieć,

lub zapisanie w bazie danych.

Dzięki temu stan obiektu może być zachowany i odtworzony później (deserializacja) — czyli z powrotem przekształcony z ciągu bajtów do obiektu Java.

Wymagania
Klasa musi implementować interfejs Serializable (markerowy, bez metod).

Pola oznaczone jako transient nie będą serializowane.

Pola static nie są serializowane (należą do klasy, a nie do instancji).

Zaleca się deklarowanie stałej serialVersionUID dla kontroli wersji klasy.

Zapis obiektu do pliku (serializacja)
```
Person person = new Person();
person.setName("Jan");
person.setAge(30);

try (FileOutputStream fos = new FileOutputStream("person.ser");
     ObjectOutputStream oos = new ObjectOutputStream(fos)) {
    oos.writeObject(person);  // zapis obiektu do pliku
}
```
Odczyt (deserializacja)
```
try (FileInputStream fis = new FileInputStream("person.ser");
     ObjectInputStream ois = new ObjectInputStream(fis)) {
    Person personFromFile = (Person) ois.readObject();  // odczyt obiektu z pliku
    System.out.println(personFromFile.getName());
}
```
