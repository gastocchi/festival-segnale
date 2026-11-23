# Scheda dati — Programma Segnale

## Entità: Evento

| Campo | Tipo | Esempio |
|---|---|---|
| id | numero | 1 |
| titolo | testo | Lettere in movimento |
| data | data in formato AAAA-MM-GG | 2026-06-12 |
| orario | testo, formato HH:MM | 10:00 |
| categoria | testo | Incontro |
| descrizione | testo | Un incontro su tipografia e comunicazione visiva. |
| immagine | percorso testuale | assets/lettere-in-movimento.svg |
| immagine_alt | testo | Lettere geometriche disposte su una griglia |
| sede_id | numero | 1 |

Chiave primaria: `id`, numerico, univoco nell’entità e stabile.

## Entità: Sede

| Campo | Tipo | Esempio |
|---|---|---|
| id | numero | 1 |
| nome | testo | Officina Nord |
| indirizzo | testo | Corso Duca degli Abruzzi 24, Torino |

Chiave primaria: `id`, numerico, univoco nell’entità e stabile.

## Relazione

Una sede può ospitare più eventi; ogni evento si svolge in una sede.
`Evento.sede_id` fa riferimento a `Sede.id`.

```mermaid
erDiagram
    SEDE ||--o{ EVENTO : ospita
    SEDE {
        number id PK
        string nome
        string indirizzo
    }
    EVENTO {
        number id PK
        string titolo
        string data
        string orario
        string categoria
        string descrizione
        string immagine
        string immagine\_alt
        number sede\_id FK
    }
