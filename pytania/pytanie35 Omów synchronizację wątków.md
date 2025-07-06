Synchronizacja wątków w Javie — Notatka skrócona
Co to jest synchronizacja?
Mechanizm zapewniający, że w danym momencie tylko jeden wątek ma dostęp do współdzielonego zasobu, zapobiegając race condition i niespójności danych.

Po co synchronizacja?
Wiele wątków operuje na tym samym zasobie — bez synchronizacji dane mogą się uszkodzić.

Synchronizacja zapewnia wzajemne wykluczanie (mutual exclusion).

Jak synchronizować w Javie?
Synchronized methods — metoda oznaczona synchronized jest blokowana przez monitor obiektu, tylko 1 wątek ją wykonuje:

```
public synchronized void inc() { c++; }
```
Synchronized blocks — synchronizacja fragmentu kodu na wybranym obiekcie:

```
synchronized(this) { c++; }
```
Monitor i blokada
Każdy obiekt ma monitor (lock).

Wątek, który zajmie monitor, blokuje inne wątki próbujące wejść do synchronizowanej sekcji.

Przykład: licznik zwiększany przez 2 wątki
Metody inc() i get() są synchronizowane, więc wynik po 1000 inkrementacjach przez dwa wątki to 2000.

Rodzaje synchronizacji:
Synchronizacja procesów — koordynacja pracy wielu procesów (rzadziej w Javie).

Synchronizacja wątków — zapewnia bezpieczny dostęp i współpracę między wątkami.

Mutual Exclusion (wykluczanie wzajemne)
Zapobiega jednoczesnemu wejściu wielu wątków do sekcji krytycznej.

Realizowane przez synchronized (metody lub bloki) lub zaawansowane mechanizmy (np. ReentrantLock).

Wskazówki
Synchronizuj tylko niezbędne fragmenty — nadmierna synchronizacja może powodować spadek wydajności i zakleszczenia (deadlock).

Można synchronizować metody, bloki, lub konkretne obiekty.

Podsumowanie
Synchronizacja to podstawowy mechanizm w programowaniu wielowątkowym w Javie, umożliwiający bezpieczne współdzielenie zasobów i zapobieganie błędom wynikającym z równoczesnego dostępu wielu wątków.





# inny koncept
Synchronizacja wątków w Javie
Co to jest synchronizacja?
Synchronizacja to mechanizm pozwalający na kontrolę dostępu wielu wątków do współdzielonych zasobów, by zapobiec konfliktom i błędom (np. uszkodzeniu danych).

Problem:
Gdy kilka wątków jednocześnie modyfikuje dane, może dojść do warunków wyścigu (race conditions) i niespójności danych.

Jak działa synchronizacja?
synchronized – słowo kluczowe blokujące dostęp do sekcji kodu lub metody, aby tylko jeden wątek mógł ją wykonać w danym momencie.
Formy synchronizacji:
Synchronizacja metody
```
public synchronized void increment() {
    count++;
}
```
Metoda zablokowana na obiekcie instancji (this).

Synchronizacja bloku kodu
```
public void increment() {
    synchronized(this) {
        count++;
    }
}
```
Blok synchronizowany na podanym obiekcie.

Kluczowe zasady:
Wątki muszą synchronizować się na tym samym monitorze (obiekcie blokady).

Synchronizacja gwarantuje:

Wyłączny dostęp (mutual exclusion) – tylko jeden wątek może wykonywać synchronizowany kod.

Widoczność zmian – zmiany dokonane przez jeden wątek są widoczne dla innych.

Inne mechanizmy synchronizacji:
volatile – zapewnia widoczność zmian zmiennej między wątkami, ale nie gwarantuje wykluczenia wzajemnego.

ReentrantLock – bardziej zaawansowana klasa blokady z dodatkowymi funkcjami (np. próba blokady, timeout).

Podsumowanie:
Synchronizacja jest konieczna, aby uniknąć problemów z dostępem współbieżnym.

Nadmierna synchronizacja może prowadzić do blokad (deadlock) i obniżenia wydajności.

Synchronizacja wątków w Javie
Co to jest synchronizacja?
Synchronizacja to mechanizm, który zapewnia bezpieczny dostęp wielu wątkom do współdzielonych zasobów. Gwarantuje, że w danym momencie tylko jeden wątek może wykonywać fragment kodu operujący na tych zasobach, zapobiegając warunkom wyścigu (race conditions) i niespójności danych.

Dlaczego synchronizacja jest potrzebna?
Bez synchronizacji wątki mogą jednocześnie modyfikować zmienne, co prowadzi do uszkodzenia danych lub błędnych wyników.

Synchronizacja zapewnia:

Mutual exclusion – wzajemne wykluczanie, tylko jeden wątek w sekcji krytycznej.

Widoczność zmian – zmiany wprowadzone przez jeden wątek są widoczne dla innych.

Jak działa synchronizacja w Javie?
Metody synchronizowane (synchronized methods)
Metoda oznaczona synchronized jest chroniona monitorem obiektu.
Przykład:

java
Kopiuj
Edytuj
public synchronized void inc() {
    c++;
}
Tylko jeden wątek może wejść do tej metody w danym czasie.

Bloki synchronizowane (synchronized blocks)
Synchronizujemy fragment kodu na wskazanym obiekcie (monitorze).
Przykład:

java
Kopiuj
Edytuj
public void inc() {
    synchronized(this) {
        c++;
    }
}
Pozwala synchronizować tylko wybrany fragment, nie całą metodę.

Monitor i blokada (lock)
Każdy obiekt w Javie ma przypisany monitor (lock).

Wątek, który wejdzie do bloku synchronizowanego lub metody synchronizowanej, zajmuje monitor.

Inne wątki próbujące wejść do tej sekcji są blokowane do czasu zwolnienia monitora.

Przykładowy program (inkrementacja licznika przez dwa wątki)
java
Kopiuj
Edytuj
class Counter {
    private int c = 0;

    public synchronized void inc() {
        c++;
    }

    public synchronized int get() {
        return c;
    }
}
Dwa wątki inkrementują licznik po 1000 razy. Synchronizacja zapobiega utracie aktualizacji, wynik zawsze jest 2000.

Rodzaje synchronizacji
Synchronizacja procesów

Koordynacja między różnymi procesami (np. w wieloprocesowym systemie).

W Javie zwykle dotyczy synchronizacji wielowątkowej dostępu do zasobów.

Synchronizacja wątków (thread synchronization)

Zapewnia wzajemne wykluczanie i współpracę między wątkami.

Dzieli się na:

Mutual Exclusion (wykluczanie wzajemne) — chroni sekcje krytyczne.

Cooperation (współpraca między wątkami) — komunikacja między wątkami (np. wait(), notify()).

Przykład synchronizacji w systemie rezerwacji biletów
Metoda bookTicket() synchronizuje dostęp, aby uniknąć sprzedaży więcej biletów niż dostępnych.

Podsumowanie ważnych punktów:
Synchronizacja zapobiega race condition i uszkodzeniu danych.

Synchronizować można całe metody lub fragmenty kodu (bloki).

Synchronizacja odbywa się na monitorach obiektów.

Nadmierna synchronizacja może prowadzić do deadlocków i obniżać wydajność.

Mechanizmy uzupełniające:

volatile – zapewnia widoczność zmian, ale nie wyklucza równoczesnego dostępu.

ReentrantLock – bardziej zaawansowana blokada z dodatkowymi funkcjami.
