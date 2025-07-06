| Cecha / Właściwość               | `ArrayList`                                                  | `LinkedList`                                                                                                                                   |
| -------------------------------- | ------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **Implementacja**                | Tablica dynamiczna (`dynamic array`)                         | Dwukierunkowa lista łączona (dwukierunkowa lista)                                                                                              |
| **Dostęp do elementu (get)**     | Szybki, dostęp w czasie stałym O(1)                          | Wolniejszy, wymaga przejścia listy O(n)                                                                                                        |
| **Dodawanie na koniec**          | Szybkie amortyzowane O(1) (z wyjątkiem rozszerzenia tablicy) | Szybkie O(1), dodawanie elementu na koniec listy                                                                                               |
| **Dodawanie na początek/środek** | Wolne, wymaga przesunięcia elementów O(n)                    | Szybsze, wystarczy zmiana referencji O(1)                                                                                                      |
| **Usuwanie elementu**            | Wolne, przesunięcie elementów O(n)                           | Szybsze, zmiana referencji O(1) przy usuwaniu z początku lub środka, ale wymaga przejścia do elementu O(n)                                     |
| **Zużycie pamięci**              | Mniejsze, przechowuje tylko tablicę i jej elementy           | Większe, każdy element przechowuje dodatkowo referencje do poprzedniego i następnego węzła                                                     |
| **Iterator**                     | Przesuwa się po tablicy                                      | Przesuwa się po listę łączoną                                                                                                                  |
| **Zastosowanie**                 | Gdy potrzebny jest szybki dostęp do elementów                | Gdy często modyfikujemy listę (wstawianie/usuwanie) w środku lub na początku                                                                   |
| **Metody oferowane dodatkowo**   | Brak dodatkowych, klasyczna implementacja listy              | Implementuje dodatkowo interfejs `Deque` (kolejka dwukierunkowa) — metody takie jak `addFirst()`, `addLast()`, `removeFirst()`, `removeLast()` |
| **Wydajność pamięciowa**         | Lepsza, mniej overheadu na element                           | Gorsza, każdy element zajmuje więcej pamięci                                                                                                   |

![image](https://github.com/user-attachments/assets/30b3cd29-e4e7-4875-a0a4-69bfab170ec7)


![image](https://github.com/user-attachments/assets/573994b2-6140-42d0-ad68-2554879d8aed)
