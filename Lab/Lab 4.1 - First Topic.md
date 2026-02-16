# Lab 4.1 - Topic
## Step 1: Creazione del Primo Topic

1. Andare su [Copilot Studio](https://copilotstudio.microsoft.com/) nella sezione `Agents` selezionare l'Agente `Help Desk ` .

2. Nel menù dell'Agente premere su `Topics`.

![[Pasted image 20251212161531.png]]

3. Premere `Add a topic` e successivamente `From blank`.

![[Pasted image 20251212161616.png]]

4. Per prima cosa cambiare il nome del `Topic`, selezionando `Untitled` in alto a sinistra e inserendo il seguente nome:

```
Ticket 1
```

![[Pasted image 20251212161743.png]]

5. Ora aggiugere il `trigger` con la seguente descrizione:

```
When a user has a issue or a problem start this topic.
```

![[Pasted image 20251212161713.png]]
## Step 2: Question and Conditions

1. Sotto al `Trigger` premere su `+Add Node`

![[Pasted image 20251212161825.png]]

2. Selezionare `Ask a question` e inserire nel corpo il seguente messaggio:

```
Hello, could you indicate the type of issue?
```

3. Aggiungere *User.DisplayName* premendo il `{x}` dopo la virgola .

4. Su Identify selezionare `Multiple choice options` 

5. Inserire nuove opzioni di risposta:

- `Hardware Issues`
- `Software Issues`
- `Network Issues`

![[Pasted image 20251212161918.png]]

3. Notare come Copilot Studio crea in automatico le `Conditions` per ogni caso tranne `All other conditions`.

![[Pasted image 20251212162034.png]]

4. Sotto ogni opzione premere `Add a node` e selezionare `Ask a question`.

```
Describe the issue
```

5. Impostare Identify come `User's entire response`

6. Andare su `Save user response as` selezionare la variabile e rinominarla `Issue`.

![[Pasted image 20251212162106.png]]

7. Ripetere il processo per le varie opzioni o fare Copy and Paste del nodo.

## Step 3: Topic management

1. Premere `Add node` sotto `All other conditions` 

2. Selezionare `Topic Management`,  `Go to another topic` e infine `Escalate`.

![[Pasted image 20251212162244.png]]

![[Pasted image 20251212162258.png]]

![[Pasted image 20251212162149.png]]

3. Sotto tutte le `conditions` premere `Add node`

4. Selezionare `Topic Management` e `End current topic`

![[Pasted image 20251212162340.png]]

5. Salvare il `Topic`.
## Step 4: Testing

1. Dopo aver salvato il `Topic` premere il tasto Test

> [!tip] 
> Ricordarsi di premere su `start a new session`, perché facendolo la chat di Test si aggiornerà con le ultime modifiche fatte all'Agente.

2. Inserire la seguente richiesta:

```
I have a technical issue
```

3. Continuare il dialogo con l'agente e vederne il funzionamento.

>[!success]
>Con questo ultimo passaggio, il laboratorio sulla creazione di un primo Topic è terminato.
>