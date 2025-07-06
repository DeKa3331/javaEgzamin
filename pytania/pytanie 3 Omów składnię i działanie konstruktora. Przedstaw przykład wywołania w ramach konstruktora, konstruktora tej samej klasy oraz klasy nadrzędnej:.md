Co to jest konstruktor?
Specjalna metoda wywoływana przy tworzeniu obiektu (new).

Nazywa się tak samo jak klasa i nie ma typu zwracanego (nawet void).

Służy do inicjalizacji pól obiektu w momencie jego tworzenia.

```
public class Bicycle {
    int gear;
    int cadence;
    int speed;

    // Konstruktor z parametrami
    public Bicycle(int startCadence, int startSpeed, int startGear) {
        gear = startGear;
        cadence = startCadence;
        speed = startSpeed;
    }

    // Konstruktor bezparametrowy (no-arg)
    public Bicycle() {
        gear = 1;
        cadence = 10;
        speed = 0;
    }
}
```
Wywołanie konstruktora innego konstruktora tej samej klasy (this())
Stosujemy do konstruktor chaining w ramach jednej klasy:
```
public class Rectangle {
    private int x, y;
    private int width, height;

    public Rectangle() {
        this(0, 0, 1, 1); // wywołuje konstruktor z 4 parametrami
    }

    public Rectangle(int width, int height) {
        this(0, 0, width, height); // wywołuje konstruktor z 4 parametrami
    }

    public Rectangle(int x, int y, int width, int height) {
        this.x = x;
        this.y = y;
        this.width = width;
        this.height = height;
    }
}
```
Wywołanie konstruktora klasy nadrzędnej (super())
Stosujemy do konstruktor chaining między klasami dziedziczącymi:
```
public class Bicycle {
    public Bicycle(int startCadence, int startSpeed, int startGear) { ... }
}

public class MountainBike extends Bicycle {
    private int seatHeight;

    public MountainBike(int startHeight, int startCadence, int startSpeed, int startGear) {
        super(startCadence, startSpeed, startGear); // wywołanie konstruktora nadklasy
        seatHeight = startHeight;
    }
}
```
| Element                                     | Opis                                                             |
| ------------------------------------------- | ---------------------------------------------------------------- |
| **Definicja**                               | Konstruktor to metoda inicjalizująca obiekt, bez typu zwracanego |
| **Nazwa**                                   | Zawsze taka sama jak klasa                                       |
| **Wywołanie**                               | Przez `new`, np. `new Bicycle(30, 0, 8);`                        |
| **Przeciążanie**                            | Możliwe, jeśli różnią się parametrami                            |
| **Wywołanie konstruktora tej samej klasy**  | `this(...)`                                                      |
| **Wywołanie konstruktora klasy nadrzędnej** | `super(...)`                                                     |
| **Pozycja wywołania `this()` i `super()`**  | Zawsze jako pierwsza linia w konstruktorze                       |

Kluczowe punkty do zapamiętania:
✅ Konstruktor pozwala inicjalizować pola obiektu w chwili jego tworzenia.
✅ Konstruktor domyślny jest dodawany tylko, jeśli nie ma żadnego konstruktora.
✅ this(...) służy do wywoływania innego konstruktora tej samej klasy.
✅ super(...) służy do wywoływania konstruktora klasy nadrzędnej.
✅ Konstruktor może przyjmować parametry dowolnego typu (prymitywne, referencyjne, tablice, varargs).
