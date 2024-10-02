## KTH Domain Model
KTH is sometimes refered to as a program oriented university. A program is a study track with a set of mandatory and optional course that eventually leads a student to acquiring a degree.



### Program

```mermaid
erDiagram
    Program ||--|{ ProgramRound : ""
    ProgramRound |o--|{ Course : ""
    ProgramRound |o--|{ CourseRound : ""
    Program ||--|{ ProgramResponsible : ""
    Course ||--|{ CourseRound : ""
```

------------

### Student
```mermaid
erDiagram
    Program |o--|{ Student : ""
    Course ||--|{ Student : ""
    CourseRound ||--|{ Student : ""
```

------------

### Course
```mermaid
erDiagram
    Course ||--|{ CourseResponsible : ""
    Course ||--|{ Teacher : ""
    CourseRound ||--|{ Teacher : ""
    CourseRound ||--|| Assistant : ""
    CourseRound ||--|| CourseResponsible : ""
    CourseRound ||--|| Examinor : ""
    Course ||--|{ CourseRound : ""
```