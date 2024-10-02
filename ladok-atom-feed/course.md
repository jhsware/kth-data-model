# Course

NOTE: WORK IN PROGRESS

The transitions are named by required actions in the LADOK GUI.

## State Changes

```mermaid
sequenceDiagram
    actor Course
    participant Utkast
    participant Påbörjad
    participant Komplett

    Utkast ->> Påbörjad:Utkast till påbörjad
    Note over Påbörjad: Moduler kan läggas till
    Påbörjad ->> Komplett:Påbörjad till komplett
```
------------

## Ladok Events

### Till påbörjad
```mermaid
sequenceDiagram
    actor Course
    participant Utkast
    participant Påbörjad
    participant Komplett

    Utkast ->> Påbörjad:KursTillStatusEvent
```
------------

### Till komplett
```mermaid
sequenceDiagram
    actor Course
    participant Utkast
    participant Påbörjad
    participant Komplett

    Påbörjad ->> Komplett:KursTillStatusEvent
    Påbörjad ->> Komplett:StrukturEvent
```
------------