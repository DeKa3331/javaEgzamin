Budowniczy (Builder) – konstrukcja i zastosowanie

Konstrukcja:
Wzorzec Budowniczy służy do tworzenia złożonych obiektów krok po kroku. Oddziela proces konstruowania obiektu od jego reprezentacji, dzięki czemu ten sam proces może tworzyć różne reprezentacje.

Budowniczy składa się z:

Klasy Budowniczy (Builder) – definiuje interfejs do budowy poszczególnych części obiektu,

Konkretnych budowniczych (Concrete Builders) – implementują interfejs budowniczego i tworzą poszczególne części obiektu,

Dyrektora (Director) – zarządza procesem budowy, wywołując kolejne kroki budowniczego (opcjonalny),

Produktu (Product) – końcowy złożony obiekt, który jest wynikiem procesu budowy.

Zastosowanie:

Gdy obiekt jest złożony i jego konstrukcja wymaga wielu etapów, które mogą się różnić (np. tworzenie różnych wariantów produktu),

Gdy chcemy oddzielić konstrukcję obiektu od jego reprezentacji,

Gdy potrzebujemy uniknąć konstruktorów z wieloma parametrami (np. "telescoping constructors"),

W przypadku budowy obiektów niemodyfikowalnych (immutable), gdzie potrzebna jest kontrola nad etapami tworzenia.
