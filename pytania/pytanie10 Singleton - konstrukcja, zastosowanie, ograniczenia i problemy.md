# Singleton w Javie

## 1. Wprowadzenie
W tym krótkim poradniku omówimy dwa najpopularniejsze sposoby implementacji Singletona w czystej Javie.

## 2. Singleton oparty na klasie
Najpopularniejszym podejściem jest implementacja Singletona przez utworzenie zwykłej klasy, która ma:

- prywatny konstruktor,
- statyczne pole przechowujące jedyną instancję klasy,
- statyczną metodę fabrykującą do pobierania tej instancji.

Dodamy również pole `info` na potrzeby demonstracji. Implementacja wygląda tak:

```
java
public final class ClassSingleton {

    private static ClassSingleton INSTANCE;
    private String info = "Initial info class";
    
    private ClassSingleton() {        
    }
    
    public static ClassSingleton getInstance() {
        if (INSTANCE == null) {
            INSTANCE = new ClassSingleton();
        }
        return INSTANCE;
    }

    // gettery i settery
}
```
 Singleton oparty na enumeracji (enum)
Drugim ciekawym podejściem jest użycie wyliczeń (enum):
```
public enum EnumSingleton {
    
    INSTANCE("Initial class info"); 
 
    private String info;
 
    private EnumSingleton(String info) {
        this.info = info;
    }
 
    public EnumSingleton getInstance() {
        return INSTANCE;
    }
    
    // gettery i settery
}
```
To rozwiązanie gwarantuje bezpieczeństwo wątkowe i poprawną serializację, ponieważ enum w Javie wewnętrznie zapewnia, że istnieje tylko jedna instancja.

4. Użycie
ClassSingleton
```
ClassSingleton classSingleton1 = ClassSingleton.getInstance();
System.out.println(classSingleton1.getInfo()); // Initial info class

ClassSingleton classSingleton2 = ClassSingleton.getInstance();
classSingleton2.setInfo("New class info");

System.out.println(classSingleton1.getInfo()); // New class info
System.out.println(classSingleton2.getInfo()); // New class info
```
EnumSingleton
```
EnumSingleton enumSingleton1 = EnumSingleton.INSTANCE.getInstance();
System.out.println(enumSingleton1.getInfo()); // Initial class info

EnumSingleton enumSingleton2 = EnumSingleton.INSTANCE.getInstance();
enumSingleton2.setInfo("New enum info");

System.out.println(enumSingleton1.getInfo()); // New enum info
System.out.println(enumSingleton2.getInfo()); // New enum info
```
 Najczęstsze problemy
Singleton to pozornie prosty wzorzec, ale łatwo popełnić błędy, które doprowadzą do powstania wielu instancji.

5.1 Problemy egzystencjalne
Singleton to w gruncie rzeczy zmienna globalna. Globalne zmienne powinny być unika­- ne, zwłaszcza jeśli ich stan jest zmienny.

Zamiast korzystać ze singletona, lepiej przekazywać potrzebne zależności przez parametry metod. Ułatwia to testowanie i mockowanie.

5.2 Problemy implementacyjne
Synchronizacja:
Implementacja z prywatnym konstruktorem nie jest bezpieczna wątkowo. Bez synchronizacji dwa wątki mogą utworzyć dwie różne instancje:


   
   
# dodatkowa notatka
     

Singleton – konstrukcja, zastosowanie, ograniczenia i problemy

Konstrukcja:
Singleton to wzorzec projektowy zapewniający istnienie dokładnie jednej instancji klasy w całym programie. Typowa implementacja w Javie zawiera:

prywatny konstruktor,

statyczne pole przechowujące jedyną instancję klasy,

statyczną metodę (np. getInstance()), która zwraca tę instancję, tworząc ją na żądanie (lazy initialization).

Alternatywnie można użyć enum do implementacji Singletona, co zapewnia automatyczne bezpieczeństwo wątkowe i poprawną serializację.

Zastosowanie:
Singleton jest używany, gdy potrzebujemy jednego globalnego punktu dostępu do zasobu, np. konfiguracji aplikacji, puli połączeń z bazą danych, loggera itp.

Ograniczenia i problemy:

Problemy z wielowątkowością: bez synchronizacji metoda getInstance() może stworzyć więcej niż jedną instancję, co łamie wzorzec. Synchronizacja może spowalniać działanie.

Globalny stan: Singletony są jak zmienne globalne, co utrudnia testowanie i prowadzi do ukrytych zależności.

Wielokrotne instancje: w środowiskach z wieloma class loaderami lub przy serializacji mogą powstać dodatkowe instancje.

Trudności z testowaniem: Singleton utrudnia izolację i mockowanie podczas testów jednostkowych.

Podsumowanie:
Singleton zapewnia unikalną instancję klasy i globalny dostęp, ale należy stosować go ostrożnie, dbając o bezpieczeństwo wątkowe i konsekwencje związane z globalnym stanem.
