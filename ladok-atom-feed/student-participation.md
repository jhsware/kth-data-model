# Student Participation

REF: https://confluence.its.umu.se/confluence/pages/viewpage.action?pageId=730398886

## State Changes

```mermaid
sequenceDiagram
    actor Student
    participant FörväntatDeltagande
    participant Registrerad
    participant Avbrott
    participant Återbud

    Student ->> FörväntatDeltagande:Antagning
    FörväntatDeltagande ->> Student:Ta bort förväntat deltagande
    FörväntatDeltagande ->> Student:Återbud
    FörväntatDeltagande ->> Student:Tidigt avbrott (period = 1, ej för tillfällesbyte)

    FörväntatDeltagande ->> Registrerad:Registrering (period = 1)
    FörväntatDeltagande ->> Registrerad:Omregistrering (period = 1)
    Registrerad ->> FörväntatDeltagande:Ta bort omregistrering (period = 1)
    Registrerad ->> FörväntatDeltagande:Ta bort registrering (period = 1)
    Registrerad ->> FörväntatDeltagande:Tillfällesbyte

    Registrerad ->> Registrerad:Registrering (period > 1)
    Registrerad ->> Registrerad:Ta bort registrering (period > 1)
    
    Registrerad ->> Avbrott:Vanligt avbrott
    Avbrott ->> Registrerad:Ta bort avbrott

```

------------

## Ladok Events


### Antagning
```mermaid
sequenceDiagram
    actor Student
    participant FörväntatDeltagande
    participant Registrerad
    participant Avbrott

    Student ->> FörväntatDeltagande:ForvantatDeltagandeEvent
```
------------
### Återbud
```mermaid
sequenceDiagram
    actor Student
    participant FörväntatDeltagande
    participant Registrerad
    participant Avbrott

    FörväntatDeltagande ->> Student:AterbudEvent
```
------------
### Ta bort förväntat deltagande
```mermaid
sequenceDiagram
    actor Student
    participant FörväntatDeltagande
    participant Registrerad
    participant Avbrott

    FörväntatDeltagande ->> Student:ForvantatDeltagandeBorttagetEvent
```
------------
### Tidigt avbrott (period = 1, ej för tillfällesbyte)
```mermaid
sequenceDiagram
    actor Student
    participant FörväntatDeltagande
    participant Registrerad
    participant Avbrott

    Registrerad ->> Student:AterkalladRegistreringEvent
    Registrerad ->> Student:AterkalladPaborjadUtbildningEvent
    Registrerad ->> Student:AterkallatPaborjadUtbildningstillfalleEvent
```
------------
### Registrering (period = 1)
```mermaid
sequenceDiagram
    actor Student
    participant FörväntatDeltagande
    participant Registrerad
    participant Avbrott

    FörväntatDeltagande ->> Registrerad:RegistreringEvent
    FörväntatDeltagande ->> Registrerad:PaborjadUtbildningEvent
    FörväntatDeltagande ->> Registrerad:PaborjadUtbildningstillfalleEvent
```
------------
### Omregistrering (period = 1)
```mermaid
sequenceDiagram
    actor Student
    participant FörväntatDeltagande
    participant Registrerad
    participant Avbrott

    FörväntatDeltagande ->> Registrerad:OmregistreringEvent
    FörväntatDeltagande ->> Registrerad:PaborjatUtbildningstillfalleEvent
```
------------
### Tillfällesbyte
```mermaid
sequenceDiagram
    actor Student
    participant FörväntatDeltagande
    participant Registrerad
    participant Avbrott

    Registrerad ->> FörväntatDeltagande:ForvantatDeltagandeEvent
```
------------
### Ta bort omregistrering (period = 1)
```mermaid
sequenceDiagram
    actor Student
    participant FörväntatDeltagande
    participant Registrerad
    participant Avbrott

    Registrerad ->> FörväntatDeltagande:AterkalladOmregistreringEvent
    Registrerad ->> FörväntatDeltagande:AterkallatPaborjatUtbildningstillfalleEvent
```
------------
### Ta bort registrering (period = 1)
```mermaid
sequenceDiagram
    actor Student
    participant FörväntatDeltagande
    participant Registrerad
    participant Avbrott

    Registrerad ->> FörväntatDeltagande:AterkalladRegistreringEvent
    Registrerad ->> FörväntatDeltagande:AterkalladPaborjadUtbildningEvent
    Registrerad ->> FörväntatDeltagande:AterkalladPaborjatUtbildningstillfalleEvent
```
------------
### Registrering (period > 1)
```mermaid
sequenceDiagram
    actor Student
    participant FörväntatDeltagande
    participant Registrerad
    participant Avbrott

    Registrerad ->> Registrerad:RegistreringEvent
```
------------
### Ta bort registrering (period > 1)
```mermaid
sequenceDiagram
    actor Student
    participant FörväntatDeltagande
    participant Registrerad
    participant Avbrott

    Registrerad ->> Registrerad:AterkallaRegistreringEvent
```
------------
### Vanligt avbrott
```mermaid
sequenceDiagram
    actor Student
    participant FörväntatDeltagande
    participant Registrerad
    participant Avbrott

    Registrerad ->> Avbrott:AvbrottEvent
```
------------
### Ta bort avbrott
```mermaid
sequenceDiagram
    actor Student
    participant FörväntatDeltagande
    participant Registrerad
    participant Avbrott
    
    Avbrott ->> Registrerad:AvbrottBorttagetEvent
```

<!-- # Alternative Notation

NOTE: This isn't very readable unless we can do something about the styling.

```mermaid
sequenceDiagram
    actor Student
    participant FörväntatDeltagande
    participant Registrerad
    participant Avbrott

    par Antagning
      Student ->> FörväntatDeltagande:ForvatatDeltagandeEvent
    end

    par Återbud
      FörväntatDeltagande ->> Student:AterbudEvent
    end

    par Ta bort förväntat deltagande
      FörväntatDeltagande ->> Student:ForvantatDeltagandeBorttagetEvent
    end
    
    par Tidigt avbrott (period = 1, ej för tillfällesbyte)
      Registrerad ->> Student:AterkalladrRegistreringEvent
      Registrerad ->> Student:AterkalladrPaborjadUtbildningEvent
      Registrerad ->> Student:AterkalladrPaborjadUtbildningstillfalleEvent
    end

    par Registrering (period = 1)
      FörväntatDeltagande ->> Registrerad:RegistreringEvent
      FörväntatDeltagande ->> Registrerad:PaborjadUtbildningEvent
      FörväntatDeltagande ->> Registrerad:PaborjadUtbildningstillfalleEvent
    end
    
    par Omregistrering (period = 1)
      FörväntatDeltagande ->> Registrerad:OmregistreringEvent
      FörväntatDeltagande ->> Registrerad:PaborjatUtbildningstillfalleEvent
    end

    par Tillfällesbyte
      Registrerad ->> FörväntatDeltagande:ForvantatDeltagandeEvent
    end

    par Ta bort omregistrering (period = 1)
      Registrerad ->> FörväntatDeltagande:AterkalladOmregistreringEvent
      Registrerad ->> FörväntatDeltagande:AterkalladPaborjatUtbildningstillfalleEvent
    end
    
    par Ta bort registrering (period = 1)
      Registrerad ->> FörväntatDeltagande:AterkalladRegistreringEvent
      Registrerad ->> FörväntatDeltagande:AterkalladPaborjadUtbildningEvent
      Registrerad ->> FörväntatDeltagande:AterkalladPaborjatUtbildningstillfalleEvent
    end

    par Registrering (period > 1)
      Registrerad ->> Registrerad:RegistreringEvent
    end
    
    par Registrering (period > 1)
      Registrerad ->> Registrerad:AterkallaRegistreringEvent
    end

    par Vanligt avbrott
      Registrerad ->> Avbrott:AvbrottEvent
    end
    
    par Vanligt avbrott
      Avbrott ->> Registrerad:AvbrottBorttagetEvent
    end
``` -->
