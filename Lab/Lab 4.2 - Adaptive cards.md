# Lab 4.2 - Adaptive cards
## Step 0: Prerequsiti

1. Aver completato i `Lab` precendeti

2. Disattivare il `topic` creato nel `Lab 4.1`

![[Pasted image 20251212162555.png]]
## Step 1: Creazione del Secondo Topic

1. Andare su [Copilot Studio](https://copilotstudio.microsoft.com/) nella sezione `Agents` selezionare l'Agente `Help Desk ` .

2. Nel menù dell'Agente premere su `Topics`.

![[Pasted image 20251212161531.png]]

3. Premere `Add a topic` e successivamente `From blank`.

![[Pasted image 20251212161616.png]]

4. Per prima cosa cambiare il nome del `Topic`, selezionando `Untitled` in alto a sinistra e inserendo il seguente nome:

```
Ticket Card
```

![[Pasted image 20251212162740.png]]

5. Ora aggiungere il `trigger` con la seguente descrizione:

```
When the user need to create an issue ticket open this topic
```

![[Pasted image 20251212162754.png]]

6. Premere su `Add Node` (l'icona + sotto a trigger) e selezionare `Ask with adaptive card`.

![[Pasted image 20251212162930.png]]

>[!summary] Tips
> Puoi personalizzare le adaptive card direttamente da Copilot Studio o tramite siti esterni come [Designer Adaptive Cards](https://adaptivecards.io/designer/)

7. Aprire i dettagli dell'Adaptive card, inserire il seguente Json:

```
{
    "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.5",
    "body": [
        {
            "type": "TextBlock",
            "text": "Richiesta Ticket IT",
            "weight": "Bolder",
            "size": "Large"
        },
        {
            "type": "TextBlock",
            "text": "Compila i campi sottostanti per aprire un ticket di assistenza.",
            "wrap": true,
            "spacing": "Small"
        },
        {
            "type": "Input.Text",
            "id": "nome",
            "label": "Nome",
            "placeholder": "Inserisci il tuo nome",
            "isRequired": true,
            "errorMessage": "Il nome è obbligatorio."
        },
        {
            "type": "Input.Text",
            "id": "cognome",
            "label": "Cognome",
            "placeholder": "Inserisci il tuo cognome",
            "isRequired": true,
            "errorMessage": "Il cognome è obbligatorio."
        },
        {
            "type": "Input.Text",
            "id": "email",
            "label": "Email",
            "placeholder": "esempio@azienda.com",
            "style": "Email",
            "isRequired": true,
            "errorMessage": "Inserisci un indirizzo email valido.",
            "regex": "^[\\w.+-]+@([\\w-]+\\.)+[\\w-]{2,}$"
        },
        {
            "type": "Input.ChoiceSet",
            "id": "tipologia",
            "label": "Tipologia di problema",
            "placeholder": "Seleziona una tipologia",
            "isRequired": true,
            "errorMessage": "Seleziona una tipologia di problema.",
            "choices": [
                {
                    "title": "Hardware",
                    "value": "Hardware"
                },
                {
                    "title": "Software",
                    "value": "Software"
                },
                {
                    "title": "Rete",
                    "value": "Rete"
                },
                {
                    "title": "Altro",
                    "value": "Altro"
                }
            ]
        },
        {
            "type": "Input.Text",
            "id": "descrizione",
            "label": "Descrivi il problema",
            "isMultiline": true,
            "placeholder": "Fornisci una descrizione dettagliata del problema (sintomi, quando si verifica, eventuali messaggi di errore, ecc.)",
            "maxLength": 2000,
            "isRequired": true,
            "errorMessage": "La descrizione del problema è obbligatoria."
        },
        {
            "type": "TextBlock",
            "text": "I campi contrassegnati sono obbligatori.",
            "size": "Small",
            "isSubtle": true,
            "wrap": true,
            "spacing": "Small"
        }
    ],
    "actions": [
        {
            "type": "Action.Submit",
            "title": "Invia ticket",
            "data": {
                "action": "submitTicket"
            }
        },
        {
            "type": "Action.Submit",
            "title": "Annulla",
            "data": {
                "action": "cancel"
            }
        }
    ]
}
```

![[Pasted image 20251212162858.png]]

![[Pasted image 20251212163004.png]]

8. Sotto l'adaptive card premere `Add node`

9. Selezionare `send a message`

![[Pasted image 20251212163055.png]]


10. Nel corpo del messaggio inserire le variabili create dall'adaptive card.

11. Premere `Save` e chiudere la card.

12. Aprire la chat di test e provare a chiedere un ticket.

> [!tip] 
> Ricordarsi di premere su `start a new session`, perché facendolo la chat di Test si aggiornerà con le ultime modifiche fatte all'Agente.

## Step 2: Adaptive card in a message

1. Eliminare il contenuto del `send a message`

2. Dentro il messaggio scrivere il seguente testo:

```
The following ticket has been sent to the IT department
```

4. Sempre all'interno del messaggio premere `+ Add `

5. Selezionare `Adaptive card` e nella schermata di edit cambiare da Json a formula card.

![[Pasted image 20251212163129.png]]

> [!info]
> Nell'Adaptive card in Json non è possibile inserire variabili, quindi è necessario usare la  Formula Card scritta in [Power Fx](https://learn.microsoft.com/it-it/power-platform/power-fx/overview) 

6. Incollare la seguente card:

```
{ type: "AdaptiveCard", body: [ { type: "TextBlock", size: "Medium", weight: "Bolder", text: "Riepilogo dati inseriti" }, { type: "FactSet", facts: [ { title: "Nome", value: Text(Topic.nome) }, { title: "Cognome", value: Text(Topic.cognome) }, { title: "Email", value: Text(Topic.email) }, { title: "Tipologia di problema", value: Text(Topic.tipologia) }, { title: "Descrizione", value: Text(Topic.descrizione) } ] } ], '$schema': "http://adaptivecards.io/schemas/adaptive-card.json", version: "1.5" }
```

![[Pasted image 20251212163025.png]]

7. Premere `Save` e chiudere la card e salvare il Topic

8. Dopo aver salvato il Topic premere il tasto Test

> [!tip] 
> Ricordarsi di premere su `start a new session`, perché facendolo la chat di Test si aggiornerà con le ultime modifiche fatte all'Agente.

9. Inserire la seguente richiesta:

```
I want to open a ticket
```

10. Continuare il dialogo con l'agente e vederne il funzionamento.

>[!success]
>Con questo ultimo passaggio, il laboratorio sull'utilizzo delle Adaptive Cards è terminato.
>