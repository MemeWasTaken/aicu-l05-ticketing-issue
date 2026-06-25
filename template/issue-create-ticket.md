# Issue: Create ticket from support

## Request

```txt
Serve creare ticket dal supporto.
```

## Fatti (Facts)

- Siamo in una semplice applicazione di ticketing in react e node.js
- Esistono dei ticket già presenti nella nostra applicazione e visualizzabili in pagine UI dedicate
- Non avrai accesso all'applicazione, siamo in una fase precedente


## Assunzioni (Assumptions)

- Il ticket deve contenere un titolo (ticketID), un body (bodyTicketID) e le informazioni di contatto del cliente quali: nome (contactNameID) e indirizzo email (contactEmailID)
- Il ticket non richiede: autenticazione, sistemi di mentioning, allegati, notifiche
- Il ticket deve avere per forza: titolo, body, e le informazioni di contatto (nome e email del cliente). Altrimenti il ticket non è valido

## Domande Aperte (Questions)

- Dove saranno posizionate le note? Dove le potrò recuperare?
- Ci sono già modelli di dati per i ticket?

## Decisione (Decision)

Per questo slice, "creare ticket" significa:

```txt
Creare ticket dal supporto significa permettere al cliente di contattare il team di supporto che dovrà raccogliere i dati e le informazione del cliente per poi creare un ticket associato al cliente. 
```

## Fuori Scope / Non-Obiettivi (Non-Goals)

- Autenticazione
- Modifica UI
- Creazione componenti
- Allegati
- Notifiche
- Mention
- Refactoring
- Altre funzionalità aggiuntive alle note non esplicitamente dichiarate

## Criteri Di Accettazione (Acceptance Criteria)

1. Un ticket valido inserito all'interno dell'applicazione deve avere: titolo, body (testo) e le informazioni del cliente (nome e email)
2. Un ticket non valido deve essere rifiutato a seguito della validazione
3. La fruizione degli altri elementi relativi del ticket deve essere analoga allo stato precedente

## Piano Di Verifica Manuale (Manual Test Plan)

- Ticket valido: Contiene titolo, body, nome cliente e email cliente
- Ticket non valido: Il ticket non viene inserito con successo

## Note Per L06

- [quale payload andra' chiarito]
- [quale errore andra' chiarito]
- [quale campo dati andra' deciso]
