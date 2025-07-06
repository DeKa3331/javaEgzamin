Tworzenie wątku w Javie
Sposoby tworzenia wątku:
Dziedziczenie po klasie Thread
```
class MyThread extends Thread {
    public void run() {
        // kod wątku
    }
}
MyThread t = new MyThread();
t.start();
```
Implementacja interfejsu Runnable
```
class MyRunnable implements Runnable {
    public void run() {
        // kod wątku
    }
}
Thread t = new Thread(new MyRunnable());
t.start();
```
| Cecha                     | `Thread`                                                   | `Runnable`                                                          |
| ------------------------- | ---------------------------------------------------------- | ------------------------------------------------------------------- |
| Dziedziczenie             | Trzeba dziedziczyć klasę `Thread`                          | Można implementować interfejs `Runnable` (elastyczniejsze)          |
| Wielodziedziczenie        | Brak możliwości (Java nie wspiera wielodziedziczenia klas) | Pozwala dziedziczyć inną klasę i implementować `Runnable`           |
| Reużywalność              | Mniej elastyczne, każdy wątek to osobna klasa              | Można używać tego samego `Runnable` w wielu wątkach                 |
| Przekazywanie do `Thread` | Niepotrzebne, klasa jest wątkiem                           | Wymaga utworzenia obiektu `Thread`, któremu przekazujemy `Runnable` |
| Kod uruchamiany           | Metoda `run()` klasy `Thread`                              | Metoda `run()` interfejsu `Runnable`                                |

Podsumowanie
Runnable jest zalecany do implementacji kodu wątku, bo pozwala na lepszą separację logiki od samego wątku i umożliwia wielodziedziczenie.

Thread to klasa reprezentująca wątek, której można użyć bezpośrednio, ale jest mniej elastyczna.
