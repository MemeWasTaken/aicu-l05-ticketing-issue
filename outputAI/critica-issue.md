# Critica Issue — `issue-create-ticket.md`

## 1. Confusione "ticket" vs "note" (residuo copy-paste)
- **Problema**: "Domande Aperte" e "Note Per L06" parlano ripetutamente di *note* (es. "Dove saranno posizionate le note?", "[quale campo dati andra' deciso]"), ma l'oggetto della issue è la creazione di *ticket*.
- **Perché blocca**: ambiguità sostanziale sulla funzionalità da implementare; un reviewer non sa se lo slice riguarda ticket, note o entrambi.
- **Correzione**: sostituire ogni ricorrenza di "note" con "ticket" e riallineare le domande/nota all'oggetto della issue.

## 2. Decisione ambigua su CHI compila il form
- **Problema**: La decisione dice "il team di supporto raccogliere i dati del cliente per poi creare un ticket", mentre le assunzioni implicano campi di contatto del cliente (nome/email) come parte del ticket. Non è chiaro se il form lo compili il *cliente* o l'*agente di supporto*.
- **Perché blocca**: senza questo chiarimento, scope UI e attori sono indefiniti; cambia radicalmente chi è l'utente dello slice.
- **Correzione**: dichiarare esplicitamente l'attore (es. "il cliente finale compila autonomamente un form pubblico" oppure "l'operatore di supporto inserisce i dati riferiti dal cliente") e uniformare Request, Decision e Assunzioni.

## 3. Criteri di accettazione non osservabili
- **Problema**: AC2 "Un ticket non valido deve essere rifiutato" non specifica l'osservabile (messaggio? mancata creazione? risposta vuota?). AC3 "La fruizione degli altri elementi… analoga allo stato precedente" non è misurabile.
- **Perché blocca**: la review non può stabilire quando il criterio è soddisfatto; il test plan non sa cosa verificare.
- **Correzione**: esplicitare l'osservabile per AC2 (es. "il ticket non viene persistito e l'utente vede un feedback di validazione") e rimuovere/riscrivere AC3 in termini di non-regressione misurabile (es. "i ticket preesistenti restano visibili nelle pagine UI dedicate").

## 4. Test plan manuale debole
- **Problema**: Il piano elenca solo "ticket valido contiene…" e "ticket non valido non viene inserito" — riformula il requisito, non descrive la procedura. Manca: schermata/entry point, casi di invalidità specifici (titolo vuoto, email malformata, solo spazi, campi mancanti uno alla volta).
- **Perché blocca**: l'esecutore non sa come condurre il test né quali input minimi coprono il rifiuto.
- **Correzione**: aggiungere al test plan (a) il punto di accesso (es. "vai alla schermata X, compila il form Y"), (b) elenco esaustivo dei casi invalidi (campo mancante, tipo errato, formato email non valido) con atteso per ciascuno.

## 5. Non-Goals contraddittori / incompleti
- **Problema**: "Creazione componenti" come non-goal è incoerente in un'app React: implementare un form richiede componenti. Mancano inoltre non-goals ovvi (modifica ticket, cancellazione ticket, listaggio/visualizzazione del nuovo ticket, scelta del layer di persistenza, paginazione/ricerca).
- **Perché blocca**: il vincolo su "no componenti" rende letteralmente impossibile consegnare lo slice in React; le omissioni aprono la porta a scope creep su edit/delete/list.
- **Correzione**: rimuovere "Creazione componenti" dai non-goals (o riformularlo come "nessun refactor di componenti esistenti") e aggiungere esplicitamente *modifica*, *cancellazione*, *listaggio del nuovo ticket* e *scelta tecnologia di persistenza* tra i non-goals.
