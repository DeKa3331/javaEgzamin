1. Wprowadzenie
Abstrakcja jest jedną z kluczowych cech programowania obiektowego. Pozwala ukryć złożoność implementacji, oferując funkcjonalności poprzez prostsze interfejsy. W Javie abstrakcję osiągamy, używając albo interfejsu, albo klasy abstrakcyjnej.

W tym artykule omówimy, kiedy stosować interfejs, a kiedy klasę abstrakcyjną podczas projektowania aplikacji. Przedstawimy też główne różnice między nimi oraz podpowiemy, którą z tych dwóch konstrukcji wybrać w zależności od celu, jaki chcemy osiągnąć.

2. Klasa a interfejs
Najpierw spójrzmy na różnice między zwykłą (konkretną) klasą a interfejsem.

Klasa to zdefiniowany przez użytkownika typ, który działa jak szablon do tworzenia obiektów. Może mieć właściwości i metody, które reprezentują stan i zachowania obiektu.

Interfejs jest również typem zdefiniowanym przez użytkownika, syntaktycznie podobnym do klasy. Może zawierać zbiór stałych pól oraz podpisy metod, które muszą zostać nadpisane przez klasy implementujące dany interfejs.

Od Javy 8 w interfejsach można też definiować metody statyczne oraz domyślne (default) w celu zapewnienia kompatybilności wstecznej. Metody w interfejsie, które nie są statyczne ani domyślne, są domyślnie abstrakcyjne i publiczne.

Od Javy 9 możliwe jest również dodawanie metod prywatnych w interfejsach.

3. Interfejs a klasa abstrakcyjna
Klasa abstrakcyjna to klasa zadeklarowana ze słowem kluczowym abstract. Pozwala zadeklarować metody abstrakcyjne (bez implementacji), które wymuszają na klasach dziedziczących ich implementację. Jeśli klasa ma choć jedną metodę abstrakcyjną, sama musi być abstrakcyjna.

Klasy abstrakcyjne nie mają ograniczeń co do modyfikatorów pól i metod, podczas gdy w interfejsie wszystko jest domyślnie publiczne. W klasie abstrakcyjnej można mieć bloki inicjalizacyjne (statyczne i instancyjne), czego nie można robić w interfejsach. Klasy abstrakcyjne mogą mieć też konstruktory, które są wywoływane przy tworzeniu obiektu potomnego.

Java 8 wprowadziła pojęcie interfejsów funkcyjnych — interfejsów z maksymalnie jedną metodą abstrakcyjną (poza metodami statycznymi i domyślnymi). Dzięki temu można ograniczyć liczbę abstrakcyjnych metod w interfejsie. W klasach abstrakcyjnych nie ma takiego ograniczenia.

Podobieństwa między klasami abstrakcyjnymi i interfejsami:

Nie można ich bezpośrednio instancjonować (czyli nie można stworzyć obiektu przy pomocy new Typ() bez nadpisania metod, np. w anonimowej klasie).

Mogą zawierać metody zadeklarowane lub zaimplementowane (np. metody statyczne i domyślne w interfejsach, metody instancyjne i abstrakcyjne w klasach abstrakcyjnych).

4. Kiedy używać interfejsu
Przykładowe sytuacje, gdy warto wybrać interfejs:

Gdy problem wymaga wielodziedziczenia i jest związany z różnymi hierarchiami klas.

Gdy niepowiązane klasy implementują ten sam interfejs, np. Comparable z metodą compareTo().

Gdy funkcjonalności mają być zdefiniowane jako kontrakt, a implementacja może należeć do różnych, nieznanych z góry klas (np. zewnętrzni dostawcy).

Gdy chcemy wyrazić, że „A potrafi coś robić” — np. „Clonable potrafi klonować”, „Drawable potrafi rysować”.

Przykład:
```
public interface Sender {
    void send(File fileToBeSent);
}

public class ImageSender implements Sender {
    @Override
    public void send(File fileToBeSent) {
        // implementacja wysyłania obrazu
    }
}
```

Kiedy używać klasy abstrakcyjnej
Przykładowe sytuacje, gdy warto użyć klasy abstrakcyjnej:

Gdy chcemy korzystać z dziedziczenia, dzieląc wspólny kod między klasy powiązane.

Gdy mamy określone wymagania i częściową implementację, którą chcemy wymusić na podklasach.

Gdy klasy potomne mają wspólne pola lub metody, które wymagają modyfikatorów innych niż publiczne.

Gdy potrzebujemy metod niestatycznych i niefinalnych, które zmieniają stan obiektu.

Warto używać klas abstrakcyjnych, gdy zachodzi relacja typu „A jest B”, np. „Pies jest Zwierzęciem”, „Lamborghini jest Samochodem”.

| Cecha / Właściwość          | Klasa abstrakcyjna                                               | Interfejs                                                                                    |
| --------------------------- | ---------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| Deklaracja                  | `abstract class Nazwa`                                           | `interface Nazwa`                                                                            |
| Dziedziczenie               | Klasa może rozszerzać tylko jedną klasę abstrakcyjną (`extends`) | Interfejs może rozszerzać wiele innych interfejsów (`extends`)                               |
| Implementacja               | Klasa dziedzicząca musi zaimplementować metody abstrakcyjne      | Klasa implementująca interfejs musi zaimplementować wszystkie metody abstrakcyjne interfejsu |
| Metody domyślne / statyczne | Może mieć metody z implementacją, również statyczne              | Od Javy 8: może mieć metody domyślne (default) i statyczne                                   |
| Modyfikatory metod          | Mogą mieć różne modyfikatory (private, protected, public)        | Metody są domyślnie publiczne, od Javy 9 mogą być też prywatne                               |
| Pola / zmienne              | Mogą mieć pola instancyjne i statyczne                           | Mogą mieć tylko stałe pola (public static final)                                             |
| Konstruktory                | Mogą mieć konstruktory                                           | Nie mogą mieć konstruktorów                                                                  |
| Bloki inicjalizacyjne       | Mogą mieć bloki inicjalizacyjne (statyczne i instancyjne)        | Nie mogą mieć bloków inicjalizacyjnych                                                       |
| Instancjonowanie            | Nie można tworzyć instancji klasy abstrakcyjnej bezpośrednio     | Nie można tworzyć instancji interfejsu bez implementacji                                     |
| Cel użycia                  | Wspólna baza kodu i implementacji dla powiązanych klas           | Definicja kontraktu dla klas niezależnych, możliwość wielodziedziczenia                      |
| Wielodziedziczenie          | Brak (klasa może rozszerzać tylko jedną klasę)                   | Tak (interfejs może rozszerzać wiele interfejsów)                                            |
| Przykład relacji            | „A jest B” (np. Samochód jest Pojazdem)                          | „A potrafi coś zrobić” (np. Obiekt jest Klonowalny)                                          |

Oto tabela przedstawiająca główne różnice między klasami abstrakcyjnymi a interfejsami w Javie:

| Główna różnica                       | Klasa abstrakcyjna                                                              | Interfejs                                                                                  |
| ------------------------------------ | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| Dziedziczenie                        | Klasa może rozszerzać tylko jedną klasę                                         | Interfejs może rozszerzać wiele interfejsów                                                |
| Implementacja metod abstrakcyjnych   | Klasa dziedzicząca musi implementować metody abstrakcyjne                       | Klasa implementująca interfejs musi implementować wszystkie abstrakcyjne metody            |
| Modyfikatory metod i pól             | Mogą mieć różne modyfikatory (private, protected, public) oraz pola instancyjne | Metody i pola są domyślnie publiczne, pola są stałe (public static final)                  |
| Konstruktory i bloki inicjalizacyjne | Mogą mieć konstruktory i bloki inicjalizujące                                   | Nie mogą mieć konstruktorów ani bloków inicjalizujących                                    |
| Wielodziedziczenie                   | Nie jest dozwolone (może być tylko jedno rozszerzenie)                          | Dozwolone (może rozszerzać wiele interfejsów)                                              |
| Przeznaczenie                        | Do wspólnego dzielenia kodu i implementacji między powiązanymi klasami          | Do definiowania kontraktu dla klas niezależnych i umożliwienia wielodziedziczenia zachowań |
