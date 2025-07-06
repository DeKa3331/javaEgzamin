Cykl życia wątku w Javie

![image](https://github.com/user-attachments/assets/6a022065-cd97-48c5-b9d0-48d5ec8e29b9)

Wątek w Javie przechodzi przez kilka stanów podczas swojego działania:

1. Nowy (New)
Wątek jest utworzony przy pomocy new Thread().

W tym stanie wątek istnieje, ale jeszcze nie został uruchomiony.

Nie jest aktywny i nie wykonuje żadnego kodu.

2. Gotowy (Runnable)
Po wywołaniu metody start() wątek przechodzi do stanu gotowego.

Wątek jest gotowy do wykonania, ale nie musi od razu działać – czeka na przydział czasu procesora przez scheduler systemu.

W tym stanie może być wiele wątków gotowych do uruchomienia, system zarządza ich kolejnością.

Jest gotowy do wykonania, ale może czekać na przydział czasu procesora.

3. Wykonywany (Running)
Wątek otrzymał czas procesora i wykonuje kod zawarty w metodzie run().

Jest to aktywny stan, w którym wątek robi faktyczną pracę.

4. Zablokowany (Blocked)
Wątek próbuje uzyskać dostęp do zasobu, który jest aktualnie zajęty przez inny wątek (np. sekcja synchronized).

Czeka, aż zasób zostanie zwolniony.

Nie wykonuje żadnej pracy, dopóki nie uzyska blokady.


5. Uśpiony (Timed Waiting)
Wątek czeka przez określony, zdefiniowany czas.

Przykładowe metody, które powodują taki stan to: sleep(time), wait(time), join(time).

Po upływie czasu wątek przechodzi ponownie do stanu gotowego (Runnable).
6. Oczekujący (Waiting)
Wątek czeka w nieskończoność na sygnał lub powiadomienie od innego wątku.

Przykładowe metody wywołujące ten stan: wait() bez timeoutu, join() bez timeoutu.

Wątek pozostaje zawieszony aż do momentu, gdy inny wątek go obudzi (notify(), notifyAll(), zakończenie wątku).
7. Zakończony (Terminated)
Wątek zakończył wykonanie metody run() naturalnie lub został przerwany (np. wyjątek lub wywołanie stop() – choć ta metoda jest przestarzała).

W tym stanie wątek jest martwy, nie może być ponownie uruchomiony.

Zasoby zajmowane przez wątek mogą zostać zwolnione.

Najważniejsze metody:

start() — rozpoczyna wykonanie wątku (przejście New → Runnable).

run() — zawiera kod wątku (wykonuje się w stanie Running).

sleep(time) — wątek przechodzi do Timed Waiting na określony czas.

wait() — wątek przechodzi do Waiting, czeka na notify.

join() — wątek czeka na zakończenie innego wątku.
