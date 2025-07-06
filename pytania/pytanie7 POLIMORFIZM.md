1. Przegląd
Wszystkie języki programowania obiektowego (OOP) mają cztery podstawowe cechy: abstrakcję, enkapsulację, dziedziczenie oraz polimorfizm.

W tym artykule omówimy dwa główne typy polimorfizmu: statyczny (kompilacyjny) oraz dynamiczny (w czasie wykonania). Polimorfizm statyczny jest rozstrzygany na etapie kompilacji, natomiast dynamiczny realizowany jest podczas działania programu.

2. Polimorfizm statyczny
Według Wikipedii polimorfizm statyczny to imitacja polimorfizmu rozstrzygana podczas kompilacji, dzięki czemu unikamy odwołań do wirtualnych tabel podczas działania programu.

Na przykład, klasa TextFile w aplikacji do zarządzania plikami może mieć trzy różne metody o nazwie read():
Podczas kompilacji, kompilator sprawdza, czy wywołania read pasują do jednej z tych trzech wersji.
```
public class TextFile extends GenericFile {
    //...

    public String read() {
        return this.getContent().toString();
    }

    public String read(int limit) {
        return this.getContent().toString().substring(0, limit);
    }

    public String read(int start, int stop) {
        return this.getContent().toString().substring(start, stop);
    }
}
```
3. Polimorfizm dynamiczny
Polimorfizm dynamiczny polega na tym, że maszyna wirtualna Javy (JVM) wybiera odpowiednią metodę do wykonania, gdy obiekt podklasy jest przypisany do zmiennej typu klasy nadrzędnej. Jest to konieczne, ponieważ podklasa może nadpisać metody klasy bazowej.

Przykład: klasa nadrzędna GenericFile:
```
public class GenericFile {
    private String name;

    public String getFileInfo() {
        return "Generic File Impl";
    }
}

```
Podklasa ImageFile nadpisująca metodę getFileInfo():
```
public class ImageFile extends GenericFile {
    private int height;
    private int width;

    //... gettery i settery
    
    public String getFileInfo() {
        return "Image File Impl";
    }
}
```
Tworząc instancję ImageFile przypisaną do GenericFile:
```
GenericFile genericFile = new ImageFile("SampleImageFile", 200, 100, ...);
logger.info("File Info: \n" + genericFile.getFileInfo());
```
Metoda getFileInfo() wywoła implementację z ImageFile, a nie z GenericFile.


. Inne cechy polimorficzne w Javie
4.1. Koercja
Polimorficzna koercja to automatyczna konwersja typów wykonywana przez kompilator, np. konkatenacja łańcucha znaków i liczby:

```
String str = "string" + 2;
4.2. Przeciążanie operatorów
Operator lub metoda może mieć różne znaczenia w zależności od kontekstu. Na przykład operator + może oznaczać dodawanie lub łączenie łańcuchów znaków:
```
```
String str = "2" + 2;
int sum = 2 + 2;
System.out.printf("str = %s\nsum = %d\n", str, sum);
Wynik:
```
```
str = 22
sum = 4
```
4.3. Polimorficzne parametry
Parametry lub zmienne mogą mieć różne znaczenia w różnych kontekstach, co może prowadzić do ukrywania zmiennych. Przykład:

```
public class TextFile {
    private String content = "Tekst oryginalny";

    public void setContent() {
        String content = "Nowa wartość lokalna";  // zmienna lokalna "content"
        System.out.println(content);  // wyświetli "Nowa wartość lokalna"
        System.out.println(this.content);  // wyświetli "Tekst oryginalny"
    }
}

```
Aby uniknąć problemów, używa się słowa kluczowego this do odwołania do pola klasy.

4.4. Polimorficzne podtypy
Możemy mieć kolekcję obiektów klasy nadrzędnej, gdzie każdy element jest innego podtypu i wywołanie metody wywoła odpowiednią wersję w zależności od faktycznego typu obiektu:
```
class GenericFile {
    public String getInfo() {
        return "Informacje ogólne o pliku";
    }
}

class ImageFile extends GenericFile {
    @Override
    public String getInfo() {
        return "Informacje o pliku graficznym";
    }
}

class TextFile extends GenericFile {
    @Override
    public String getInfo() {
        return "Informacje o pliku tekstowym";
    }
}
```

Możemy mieć tablicę obiektów typu GenericFile, ale faktycznie przechowujących różne podtypy:

```
GenericFile[] files = {
    new ImageFile(),
    new TextFile()
};
```
Kiedy wywołamy metodę getInfo() na każdym z tych obiektów:

```
for (GenericFile file : files) {
    System.out.println(file.getInfo());
}
```
Wywołanie zostanie przekierowane do metody odpowiedniej klasy (podtypu), dzięki czemu dostaniemy:
```
Informacje o pliku graficznym
Informacje o pliku tekstowym
```
