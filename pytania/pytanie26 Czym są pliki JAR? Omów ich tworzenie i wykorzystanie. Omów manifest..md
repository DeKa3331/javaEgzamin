Pliki JAR – co to jest?
JAR (Java ARchive) to archiwum w formacie ZIP, które służy do pakowania wielu plików klas (.class), zasobów (np. obrazków, plików konfiguracyjnych) oraz innych danych w jeden plik. Dzięki temu można łatwo dystrybuować i uruchamiać aplikacje Java lub biblioteki.

Pliki JAR są wykorzystywane przede wszystkim do:

Dystrybucji aplikacji i bibliotek Java.

Grupowania kodu i zasobów w jednej paczce.

Ułatwiania uruchamiania aplikacji Java (np. poprzez podanie klasy głównej w manifeście).

![image](https://github.com/user-attachments/assets/04dc13a5-1e34-4d9c-8de7-c6c8a69ec786)



Manifest pliku JAR
Manifest to specjalny plik tekstowy umieszczony w archiwum JAR w katalogu META-INF pod nazwą MANIFEST.MF.

Zawiera metadane dotyczące archiwum, takie jak:

Main-Class — wskazuje klasę z metodą main(), która będzie uruchamiana po wywołaniu java -jar plik.jar.

Class-Path — definiuje ścieżki do dodatkowych bibliotek (plików JAR), których aplikacja potrzebuje.

Inne opcjonalne atrybuty, np. wersja manifestu, informacje o autorze, podpis cyfrowy itp.

Przykładowa zawartość manifestu:
```
Manifest-Version: 1.0
Main-Class: com.example.MainApp
Class-Path: lib/library1.jar lib/library2.jar
```

Wykorzystanie plików JAR
Uruchamianie aplikacji: jeśli manifest zawiera Main-Class, można uruchomić program poleceniem:

```
java -jar myapp.jar
```
Biblioteki: pliki JAR można dodawać do classpath innych projektów, aby korzystać z udostępnionych klas.

Dystrybucja: pliki JAR są standardowym formatem dystrybucji programów i komponentów w Javie.
