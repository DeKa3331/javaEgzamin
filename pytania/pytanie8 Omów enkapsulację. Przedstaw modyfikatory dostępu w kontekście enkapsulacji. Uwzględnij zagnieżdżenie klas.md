# Enkapsulacja w Javie

Enkapsulacja (ang. *encapsulation*) to jedna z podstawowych zasad programowania obiektowego.  
Polega na ukrywaniu wewnętrznych szczegółów implementacji klasy (np. pól i metod pomocniczych) i udostępnianiu tylko niezbędnego interfejsu, za pomocą którego inne klasy mogą się komunikować z obiektem.  
Dzięki enkapsulacji zapewniamy kontrolę nad dostępem do danych i chronimy je przed nieuprawnioną modyfikacją.

Enkapsulacja realizowana jest głównie poprzez:
- modyfikatory dostępu,
- stosowanie metod dostępnych publicznie (gettery i settery),
- ukrywanie pól klasy przez zadeklarowanie ich jako prywatne (`private`).

---

## Modyfikatory dostępu w kontekście enkapsulacji

W Javie dostęp do klas, metod, pól i konstruktorów kontrolowany jest przez modyfikatory dostępu:

### `public`

- Element oznaczony jako `public` jest dostępny z każdego miejsca w programie, niezależnie od pakietu.  
- Publiczne pola i metody są częścią interfejsu klasy, czyli tego, co klienci klasy mogą używać.

### `protected`

- Dostępny w obrębie tego samego pakietu oraz w klasach dziedziczących (potomnych), nawet jeśli znajdują się poza pakietem.  
- Przydatny, gdy chcemy udostępnić elementy klasom potomnym, ale ograniczyć dostęp z innych klas.

### Package-private (domyślny, brak modyfikatora)

- Dostępny tylko w obrębie tego samego pakietu.  
- Pozwala ukryć elementy przed klasami spoza pakietu, ale pozwala na współpracę klas w pakiecie.

### `private`

- Najbardziej restrykcyjny dostęp — element jest widoczny i dostępny tylko w obrębie tej samej klasy.  
- Pola i metody prywatne są niedostępne z zewnątrz, nawet dla klas potomnych i innych klas w pakiecie.  
- Idealny do ukrywania implementacji i wymuszania korzystania z getterów/setterów.

---

## Zagnieżdżenie klas a modyfikatory dostępu

Java pozwala definiować klasy zagnieżdżone (*inner classes*) — klasy zdefiniowane wewnątrz innych klas. Enkapsulacja i modyfikatory dostępu działają również w tym kontekście:

- Klasa zagnieżdżona może mieć własne modyfikatory dostępu (`public`, `protected`, `private`, package-private).  
- Klasa zagnieżdżona oznaczona jako `private` jest dostępna tylko w obrębie klasy zewnętrznej i stanowi bardzo silne ukrycie implementacji.  
- Dzięki temu można ukryć klasy pomocnicze lub implementacyjne przed resztą programu.  
- Modyfikatory dostępu dla zagnieżdżonych klas pomagają w kontrolowaniu, kto i skąd może tworzyć obiekty tych klas.

---

## Podsumowanie

- Enkapsulacja polega na ukrywaniu szczegółów implementacji i kontrolowaniu dostępu do danych oraz metod klasy.  
- Modyfikatory dostępu w Javie pozwalają na precyzyjne określenie, które elementy klasy są widoczne i dostępne z różnych części programu.  
- Stosowanie `private` do pól i pomocniczych metod oraz `public` do interfejsu klasy (getterów/setterów i metod) jest podstawową praktyką enkapsulacji.  
- Klasy zagnieżdżone można ukrywać za pomocą modyfikatorów dostępu, co pozwala tworzyć bardziej hermetyczne i bezpieczne struktury kodu.



| **Temat**                      | **Opis**                                                                                                                                                                                            |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Enkapsulacja**               | Ukrywanie szczegółów implementacji klasy, kontrolowanie dostępu do danych i metod poprzez modyfikatory dostępu oraz udostępnianie wyłącznie niezbędnego interfejsu.                                 |
| **Public**                     | - Elementy dostępne z każdego miejsca w programie (dowolny pakiet)<br>- Używane do udostępniania funkcjonalności klasy na zewnątrz                                                                  |
| **Protected**                  | - Dostępne w tym samym pakiecie oraz w klasach dziedziczących spoza pakietu<br>- Pozwala na dostęp klasom potomnym i klasom w pakiecie                                                              |
| **Package-private (domyślny)** | - Dostęp tylko w obrębie tego samego pakietu<br>- Ukrywa elementy przed klasami spoza pakietu, ale pozwala współpracować klasom w pakiecie                                                          |
| **Private**                    | - Dostępny tylko w obrębie klasy, w której element jest zadeklarowany<br>- Najsilniejsza forma ukrycia implementacji<br>- Wymusza korzystanie z getterów/setterów                                   |
| **Zagnieżdżenie klas**         | - Klasy zagnieżdżone mogą mieć własne modyfikatory dostępu<br>- Klasa zagnieżdżona `private` jest dostępna tylko w klasie zewnętrznej<br>- Umożliwia silną hermetyzację i ukrycie klas pomocniczych |
