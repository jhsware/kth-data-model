# Result on Module

NOTE: WORK IN PROGRESS

The transitions are named by required actions in the LADOK GUI.

## State Changes

```mermaid
sequenceDiagram
    actor ResultatModul
    participant Utkast
    participant Klarmarkerad
    participant Attesterad
    participant Borttagen

    Utkast ->> Klarmarkerad:Klarmarkerat
    Klarmarkerad ->> Attesterad:Attesterat
    Attesterad ->> Borttagen:Ta bort resultat
```
------------

## Ladok Events

### Klarmarkerat
```mermaid
sequenceDiagram
    actor ResultatModul
    participant Utkast
    participant Klarmarkerad
    participant Attesterad
    participant Borttagen

    Note over Utkast,Klarmarkerad: Inget meddelande skickas
```
------------

### Attesterat
```mermaid
sequenceDiagram
    actor ResultatModul
    participant Utkast
    participant Klarmarkerad
    participant Attesterad
    participant Borttagen

    Klarmarkerad ->> Attesterad:ResultatPaModulAttesteratEvent
    opt Om resultat på modul = resultat på kurs
        Klarmarkerad ->> Attesterad:ResultatPaHelKursAttesteratEvent
    end
```
------------

### Ta bort resultat
```mermaid
sequenceDiagram
    actor ResultatModul
    participant Utkast
    participant Klarmarkerad
    participant Attesterad
    participant Borttagen

    Attesterad ->> Borttagen:ResulAttesteratResultatMakuleratEvent
    
```
------------