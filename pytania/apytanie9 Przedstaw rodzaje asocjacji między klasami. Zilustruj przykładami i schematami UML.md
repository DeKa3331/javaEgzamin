[Relacje między klasami](https://bkotyra.github.io/uml/2021/04/11/relacje-miedzy-klasami.html)



2. Kompozycja
Kompozycja to rodzaj relacji „należy do” (ang. belongs-to). Oznacza to, że jeden z obiektów jest logicznie większą strukturą, która zawiera w sobie inny obiekt. Innymi słowy, jest to część lub członek tego większego obiektu.

Często nazywamy to też relacją „ma” (ang. has-a), w przeciwieństwie do relacji „jest” (ang. is-a), która opisuje dziedziczenie.

Na przykład, pokój należy do budynku, czyli inaczej — budynek ma pokój. W zasadzie to, czy nazwemy to „należy do” czy „ma”, zależy tylko od punktu widzenia.

Kompozycja jest silnym typem relacji „ma”, ponieważ obiekt zawierający jest właścicielem obiektu zawartego. W związku z tym cykle życia tych obiektów są powiązane — jeśli zniszczymy obiekt właścicielski, to jego części również zostaną zniszczone. Na przykład, pokój zostaje zniszczony razem z budynkiem, jak w podanym przykładzie.

Warto jednak zauważyć, że to nie oznacza, iż obiekt zawierający nie może istnieć bez żadnej ze swoich części. Na przykład możemy rozebrać wszystkie ściany w budynku, a więc zniszczyć pokoje, ale sam budynek nadal będzie istniał.

Jeśli chodzi o krotności (kardynalność), obiekt zawierający może mieć dowolną liczbę części. Jednak każda z tych części musi mieć dokładnie jeden obiekt właścicielski.
![image](https://github.com/user-attachments/assets/2512a92b-03d7-435c-8afe-81f9a8b15452)

Agregacja
Agregacja to również relacja „ma” (ang. has-a). To, co ją odróżnia od kompozycji, to fakt, że nie wiąże się z własnością. W efekcie cykle życia obiektów nie są powiązane — każdy z nich może istnieć niezależnie od pozostałych.

Na przykład samochód i jego koła. Możemy zdjąć koła, a one nadal będą istnieć. Możemy założyć inne (już istniejące) koła albo zainstalować te koła do innego samochodu i wszystko będzie działać poprawnie.

Oczywiście, samochód bez kół albo odłączone koło nie będzie tak użyteczny jak samochód z założonymi kołami. Ale właśnie dlatego ta relacja istnieje — aby łączyć części w większą całość, która jest zdolna do więcej niż jej pojedyncze elementy.

Ponieważ agregacja nie wiąże się z własnością, element (członek) nie musi być przypisany tylko do jednego kontenera. Na przykład trójkąt składa się z odcinków, ale różne trójkąty mogą współdzielić te same odcinki jako swoje boki.

![image](https://github.com/user-attachments/assets/d5656042-5253-458e-86c1-532faf3955a9)

Asocjacja
Asocjacja jest najsłabszą relacją spośród tych trzech. Nie jest to relacja „ma” (ang. has-a), żaden z obiektów nie jest częścią ani członkiem drugiego.

Asocjacja oznacza jedynie, że obiekty „znają się nawzajem”. Na przykład matka i jej dziecko.

![image](https://github.com/user-attachments/assets/3482de51-62c0-4975-a751-869f37ecbe13)


