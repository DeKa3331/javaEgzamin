Wyrażenie try-with-resources w Javie
✅ Co to jest?
try-with-resources to konstrukcja wprowadzona w Java 7, która automatycznie zamyka zasoby (np. pliki, strumienie, czy połączenia z bazą), po zakończeniu działania bloku try.

Nie musisz ręcznie wywoływać close(), bo zasoby są zamykane automatycznie, nawet jeśli wystąpi wyjątek.
```
try (ResourceType resource = new ResourceType()) {
    // użycie zasobu
} catch (ExceptionType e) {
    // obsługa wyjątku
}
```
Przykład – odczyt pliku
```
try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
    String line;
    while ((line = br.readLine()) != null) {
        System.out.println(line);
    }
} catch (IOException e) {
    e.printStackTrace();
}
```
Co się dzieje?

BufferedReader zostaje automatycznie zamknięty po wyjściu z bloku try.

Jeśli wystąpi wyjątek, zasób i tak zostanie zamknięty.
Zalety
✅ Brak wycieków zasobów – zasoby są zawsze zwalniane.
✅ Kod jest krótszy i czytelniejszy – nie trzeba pisać finally { resource.close(); }.
✅ Możliwość deklarowania wielu zasobów w try:
 Typowe zastosowania
📌 Odczyt i zapis plików (FileReader, BufferedReader, FileWriter, PrintWriter)
📌 Obsługa strumieni (InputStream, OutputStream)
📌 Obsługa połączeń z bazami danych (Connection, Statement, ResultSet)
📌 Każda klasa implementująca AutoCloseable, np. Scanner.

# przypadki:

 Odczyt pliku
 ```
try (BufferedReader br = new BufferedReader(new FileReader("dane.txt"))) {
    String line;
    while ((line = br.readLine()) != null) {
        System.out.println(line);
    }
} catch (IOException e) {
    e.printStackTrace();
}
```
 Zapis do pliku
 ```
try (PrintWriter pw = new PrintWriter(new FileWriter("wynik.txt"))) {
    pw.println("Hello World!");
} catch (IOException e) {
    e.printStackTrace();
}
```
 Obsługa strumieni sieciowych
 ```
try (Socket socket = new Socket("example.com", 80);
     PrintWriter out = new PrintWriter(socket.getOutputStream(), true);
     BufferedReader in = new BufferedReader(new InputStreamReader(socket.getInputStream()))) {

    out.println("GET / HTTP/1.1");
    out.println("Host: example.com");
    out.println();
    
    String responseLine;
    while ((responseLine = in.readLine()) != null) {
        System.out.println(responseLine);
    }
} catch (IOException e) {
    e.printStackTrace();
}
```
✅ Dlaczego warto używać?
✅ Uniknięcie wycieków pamięci i zasobów.
✅ Czytelny, krótszy kod – bez ręcznego close() w finally.
✅ Bezpieczeństwo w przypadku wystąpienia wyjątków.
✅ Działa z każdą klasą implementującą AutoCloseable (pliki, strumienie, sockety, bazy danych, zasoby własne).
