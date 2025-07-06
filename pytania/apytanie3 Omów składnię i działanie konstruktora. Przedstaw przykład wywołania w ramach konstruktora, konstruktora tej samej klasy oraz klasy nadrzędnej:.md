Konstruktor – składnia i działanie
Co to jest konstruktor?
Konstruktor to specjalna metoda, która jest wywoływana automatycznie podczas tworzenia obiektu (operator new).

Nazwa konstruktora zawsze jest taka sama jak nazwa klasy.

Konstruktor nie ma typu zwracanego (nawet void).

Jego głównym zadaniem jest inicjalizacja pól obiektu w momencie tworzenia.

Przykład konstruktora z parametrami i bezparametrowego

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

    // Konstruktor bezparametrowy (domyślny)
    public Bicycle() {
        gear = 1;
        cadence = 10;
        speed = 0;
    }
}
```
Wywołanie konstruktora
Konstruktor jest wywoływany przez operator new, np.:
```
Bicycle bike = new Bicycle(30, 0, 8);
```
Wywołanie innego konstruktora tej samej klasy – this()
Konstruktor może wywołać inny konstruktor w tej samej klasie przez this(...).

Pozwala to uniknąć powtarzania kodu (tzw. constructor chaining).

Wywołanie this() musi być pierwszą linią w konstruktorze.

Przykład:
```
public class Rectangle {
    private int x, y, width, height;

    public Rectangle() {
        this(0, 0, 1, 1); // wywołuje konstruktor z parametrami
    }

    public Rectangle(int width, int height) {
        this(0, 0, width, height); // wywołuje konstruktor z parametrami
    }

    public Rectangle(int x, int y, int width, int height) {
        this.x = x;
        this.y = y;
        this.width = width;
        this.height = height;
    }
}
```
Wywołanie konstruktora klasy nadrzędnej – super()
W klasach dziedziczących konstruktor może wywołać konstruktor klasy bazowej za pomocą super(...).

Pozwala to na inicjalizację części obiektu zdefiniowanej w klasie nadrzędnej.

super() musi być również pierwszą linią konstruktora.

Przykład:
```
public class Bicycle {
    public Bicycle(int startCadence, int startSpeed, int startGear) {
        // inicjalizacja pól
    }
}

public class MountainBike extends Bicycle {
    private int seatHeight;

    public MountainBike(int startHeight, int startCadence, int startSpeed, int startGear) {
        super(startCadence, startSpeed, startGear); // wywołanie konstruktora nadrzędnej klasy
        seatHeight = startHeight;
    }
}
```
| Element                                     | Opis                                                                    |
| ------------------------------------------- | ----------------------------------------------------------------------- |
| **Definicja**                               | Specjalna metoda inicjalizująca obiekt, bez typu zwracanego             |
| **Nazwa**                                   | Taka sama jak nazwa klasy                                               |
| **Wywołanie**                               | Przez `new` np. `new Bicycle(30, 0, 8);`                                |
| **Przeciążanie**                            | Możliwe, jeśli różnią się parametrami                                   |
| **Wywołanie konstruktora tej samej klasy**  | `this(...)` – musi być pierwszą instrukcją w konstruktorze              |
| **Wywołanie konstruktora klasy nadrzędnej** | `super(...)` – musi być pierwszą instrukcją w konstruktorze             |
| **Konstruktor domyślny**                    | Tworzony automatycznie tylko, gdy nie zdefiniowano żadnego konstruktora |
| **Parametry konstruktora**                  | Dowolne typy: prymitywne, referencyjne, tablice, varargs                |



# notatki

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
