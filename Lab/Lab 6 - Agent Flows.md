# Lab 6 - Agent Flows
## Step 0: Prerequisiti

1. Aver creato il Sito SharePoint del `Lab 3`.

2. Aver realizzato il Topic del `Lab 4.1/4.2`.

## Step 1: Inizio del Flow

1. Nel topic `Ticket card`, scorrere fino in fondo e aggiungere un nuovo nodo.

2. Selezionare `Add a tool` e, nel pannello laterale della scheda “Basic tools”, scegliere `New Agent flow`.

3. Il Designer di Agent flows si aprirà con un trigger e un’azione già presenti. Seleziona il `Trigger`

4. Aggiungere questi 3 input di tipo Text:

- `Tipologia
- `Nome+Cognome
- `Descrizione

Aggiungere anche la variabile `Email` di tipo `email`.

![[Pasted image 20251218104312.png]]

Su Descrizione premere l'icona  `( . . . )` e spuntare il `Make the field optional`.

![[Pasted image 20251218104355.png]]

## Step 2: Aggiungere il Ticket

1. Terminato lo `Step 1` nel quale vengono definite le variabili di input del flow, procedere con l'aggiunta del connettore.

2. Premere il `+` e cercare il seguente connettore di SharePoint:

```
Create item
```

3. Premere l'icona ( . . . ) e rinominare il connettore come:

```
Add Ticket
```

4. Nel `Site Address` selezionare `Help Desk CSM` e nella sezione `List Name` selezionare `Tickets`

5. Inserire i seguenti dati riprendendoli dal simbolo power Fx come dati dinamici.


| Campo             | Valore         |
| ----------------- | -------------- |
| Title             | Tipologia      |
| Issue Description | Descrizione    |
| User              | Nome + Cognome |
| Email             | Email          |

![[Pasted image 20251218104234.png]]

6. Premere su `Save Draft`.

## Step 3: Collegare il Flow

1. Dopo aver premuto su `Save Draft` pubblicare il flow selezionando `Publish`.

![[Pasted image 20251218110319.png]]

2. Successivamente andare sull' `Overview` del Flow e premere su `Edit` nella sezione `Details`.

3. Modificare il nome dell'Agent Flow con :


```
Ticket on SharePoint
```

4. Cambiare la `Description` con:

```
When an agent calls the flow add a ticket on Sharepoint.
```

5. Premere `Save`.

![[Pasted image 20251218105941.png]]

6. Tornare sull'Agente `Help Desk` e riaprire il Topic `Ticket card`.

7. Sotto l'ultimo `Message` con `Adaptive Card` premere `Add node` selezionando il +.

8. selezionare `Add a tool` e cercare il Flow appena creato.

![[Pasted image 20251218110120.png]]

9. Dopo aver aggiunto il Flow al Topic compilare gli input richiesti come in tabella sottostante:

| Field          | Type         | Value                              |
| -------------- | ------------ | ---------------------------------- |
| Descrizione    | Custom value | Global.descrizione                 |
| Email          | Custom value | Global.email                       |
| Name + Surname | Custom value | Global.nome & " " & Global.cognome |
| Tipologia      | Custom value | Global.tipologia                   |
![[Pasted image 20251218105851.png]]

10. Testare il flow compilando un ticket e controllando il sito sharepoint.

>[!success]
>Congratulazioni il laboratorio sugli Agent Flows è terminato.
>