1️⃣ <project> – element główny pliku POM.

2️⃣ <modelVersion> – wersja modelu POM (zwykle 4.0.0).

3️⃣ Identyfikatory projektu (koordynaty):

<groupId> – identyfikator grupy (np. organizacji, firmy).

<artifactId> – identyfikator artefaktu (nazwa projektu).

<version> – wersja artefaktu.

<packaging> – sposób pakowania (np. jar, war), domyślnie jar.

4️⃣ <dependencies> – lista zewnętrznych bibliotek używanych w projekcie.

5️⃣ <repositories> – miejsca, z których Maven pobiera zależności (dziedziczone z Super POM, jeśli brak w projekcie).

6️⃣ <parent> – określenie projektu nadrzędnego w celu dziedziczenia konfiguracji.

7️⃣ <modules> – lista modułów w ramach agregacji projektów (multi-module).

8️⃣ <build> – konfiguracja procesu budowania:

cele domyślne,

katalogi build,

nazwa wynikowego artefaktu,

wtyczki (plugins).

9️⃣ <properties> – definiowanie zmiennych/stałych używanych w POM, np.:

wersje zależności,

ścieżki build.

1️⃣0️⃣ <profiles> – profile umożliwiające różną konfigurację budowania w zależności od środowiska (np. dev, prod).
```
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.mycompany.app</groupId>
  <artifactId>my-app</artifactId>
  <version>1.0</version>
</project>
```
