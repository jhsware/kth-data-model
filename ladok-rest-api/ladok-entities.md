# LADOK Entities
WIP: Just a sketch

### Studiedeltagande
```mermaid
erDiagram
    KurspaketeringsDeltagandeForTheWin
    KurstillfallesDeltagande
    AktivitetstillfallesDeltagande
```
------

### Utbildningsinformation
```mermaid
erDiagram
    Kurspaketering |o--|{ Kurs : ""
    Kurs ||--|{ Kurstillfalle : ""
    Kurs }|--|{ Modul : ""
```
------

### Personer
Are these roles or actual entities?

```mermaid
erDiagram
    Student
    Larare
    Examinator
    Kursansvarig
```