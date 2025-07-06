Zależność między Stage a Scene w JavaFX

![image](https://github.com/user-attachments/assets/6bf4fac9-d2e5-4ce3-8500-9bd1a429509d)

1. Stage
Reprezentuje główne okno aplikacji (lub okno dialogowe).

Jest kontenerem najwyższego poziomu, który wyświetla zawartość użytkownikowi.

Można mieć wiele Stage (np. główne okno + okna dialogowe).

2. Scene
Reprezentuje zawartość wyświetlaną w oknie (Stage).

To hierarchia elementów GUI (węzłów — Node), np. przyciski, layouty, kontrolki.

Scene przechowuje drzewo komponentów (root node), które jest wyświetlane w Stage.

Relacja między Stage i Scene
Stage zawiera Scene — scena jest „pokazywana” na oknie.

Do Stage przypisujemy Scene metodą:
```
stage.setScene(scene);
```
Możemy zmienić Scene na Stage w trakcie działania aplikacji (np. zmienić widok).

Bez Scene okno Stage jest puste.


Podsumowanie
Stage to okno aplikacji.

Scene to zawartość tego okna (interfejs użytkownika).

Stage posiada Scene i pokazuje ją użytkownikowi.
