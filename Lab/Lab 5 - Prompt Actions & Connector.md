# Lab 5 - Prompt Actions & Power Platform Connectors
## Step 1: Creazione della Prompt Action

1. Andare su [Copilot Studio](https://copilotstudio.microsoft.com/) nella sezione `Agents` selezionare l'Agente `Help Desk ` .
   
2. Selezionare `Topics`  e successivamente `Ticket card`.
   
3. Sotto l'ultimo punto premere `Add node` andare su `New Prompt`

4. Verrà aperta una schermata per la creazione del Prompt.

5. Rinominare il `Prompt` seguendo l'esempio:
   
```
Adaptive Card to Html
```

5. Inserire il seguente `Prompt`:
   
```
You are an expert in creating professional HTML emails.

Your task is to take the text from the [Descrizione] and transform it into clean, responsive HTML that can be used directly in an email body.

  

Requirements:

- At the very top, insert a greeting like this :

Hello, [Nome+Cognome] opened a ticket

Here is the information:

Type of Issue: [Tipologia]

Descrizione:

  

- Preserve all formatting such as tables, bullet points, numbered lists, and hyperlinks.

- Use semantic HTML (<table>, <tr>, <td>, <ul>, <li>, <a>).

- Make the output mobile-friendly and compatible with common email clients (Outlook, Gmail, Apple Mail).

- Apply the following default style template consistently:

  

<style>

body {

margin: 0;

padding: 0;

background-color: #f4f6f8;

font-family: Arial, Helvetica, sans-serif;

}

.container {

max-width: 600px;

margin: 30px auto;

background-color: #ffffff;

border-radius: 6px;

overflow: hidden;

box-shadow: 0 2px 6px rgba(0, 0, 0, 0.08);

}

.header {

background-color: #2f80ed;

color: #ffffff;

padding: 20px;

text-align: center;

font-size: 20px;

font-weight: bold;

}

.content {

padding: 25px;

color: #333333;

font-size: 14px;

line-height: 1.6;

}

.field {

margin-bottom: 15px;

}

.label {

font-weight: bold;

color: #555555;

}

.value {

margin-top: 4px;

}

.footer {

padding: 15px;

text-align: center;

font-size: 12px;

color: #888888;

background-color: #f4f6f8;

}

</style>

  

Here a guideline for the mail:

</head>

<body>

<div class="container">

<div class="header">

New Support Request

</div>

<div class="content">

<div class="field">

<div class="label">User Name</div>

<div class="value">[Nome+Cognome]</div>

</div>

<div class="field">

<div class="label">Email</div>

<div class="value">[Email]</div>

</div>

<div class="field">

<div class="label">Type of Issue</div>

<div class="value">[Tipologia]</div>

</div>

<div class="field">

<div class="label">Description</div>

<div class="value">[Descrizione]</div>

</div>

</div>

<div class="footer">

This email was automatically generated. Please do not reply.

</div>

</div>

</body>

Output: Provide only the final HTML code block, nothing else.
```

6. Sostituire tutti i dati tra parentesi quadre con il `Add content` in formato `Text` come in esempio:

 ![[Pasted image 20251215151106.png]]
## Step 2: Configurazione nel Topic

1. Impostare come nome dell'action:

```
Adaptive card to Html
```

3. In `Inputs` configurare i seguenti dati:

| Descrizione    | Topic.descrizione                |
| -------------- | -------------------------------- |
| Email          | Topic.email                      |
| Name + Surname | Topic.nome & " " & Topic.cognome |
| Tipologia      | Topic.tipologia                  |

![[Pasted image 20251219095619.png]]

>[!danger] Nota sull'immagine
>Le variabili inserite nell'immagine sono `Global` perchè varranno usate per una versione alternativa del lab.

4. Cambiare il nome della variabile di output in `HTML` e salvare il topic.

## Step 3: PowerPlatform Connector

1. Andare su [Copilot Studio](https://copilotstudio.microsoft.com/) nella sezione `Agents` selezionare l'Agente `Help Desk ` .
   
2. Selezionare `Topics`  e successivamente `Ticket card` e premere `Add node` sotto il Prompt `Adaptive card to Html`.

3. Premere `Add Tool`, andare su `New Tool`e selezionare `Office 365 Outlook`
   
4. Cercare e selezionare il connettore chiamato `Send an email (V2)`.
   
5. Configurare `Name` con:

```
Send Ticket Email
```

7. In `Initiation` nella sezione `End user Authentication`  impostare `Maker-provided credentials`.

![[Pasted image 20251219100736.png]]

8. Nella sezione Input inserire i seguenti dati:

| To:      | User.Email      |
| -------- | --------------- |
| Subject: | New Ticket      |
| Body:    | Topic.HTML.text |

![[Pasted image 20251219100821.png]]

9. Terminati gli Input salvare il tool.

10. Testare l'agente chiedendo un ticket e controllando la propria mail.

## Step 4: Come usare tool fuori dal Topic (BONUS) 

1. Cancellare i `node` creati nello step 2 e 3 nel Topic `Ticket card`

2. Modificare le variabili di output dell'`adaptive card` in `Global`.

![[Pasted image 20251215161950.png]]
   
3. Andare sui `Tools` dell'Agente e successivamente `Add a tool`.
   
4. Sulla finestra `Add Tool` selezionare `Adaptive Card to Html` creato nello `step 1`.
## Step 5: Configurazione del Tool (BONUS) 

1. Impostare come `Name` :

```
Adaptive card to Html
```

2. Impostare come `Description`:

```
Convert the input content into a professional HTML email fragment, preserving structure and links, without altering content.
```

3. In `Additional details` in `Credential to use` impostare `Maker-provided credentials`.

4. In `Input` configurare i seguenti dati:

| Field          | Type         | Value                              |
| -------------- | ------------ | ---------------------------------- |
| Descrizione    | Custom value | Global.descrizione                 |
| Email          | Custom value | Global.email                       |
| Name + Surname | Custom value | Global.nome & " " & Global.cognome |
| Tipologia      | Custom value | Global.tipologia                   |
![[Pasted image 20251215152613.png]]

5. Terminati gli Input salvare il tool.

## Step 6: Tool per la Mail (BONUS) 
   
2. Tornare su `Tools`  e successivamente `Add a tool`.

3. Sulla finestra `Add Tool` andare su `New Tool`e selezionare `Office 365 Outlook`
   
4. Cercare e selezionare il connettore chiamato `Send an email (V2)`.

5. Configurare `Name` con:

```
Send Ticket Email
```

6. Come `Description` inserire:

```
This tool delivers the Ticket email to the It Staff.
It requires three inputs: 
- TO → the recipient’s email address (handled statically, do not modify). 
- SUBJECT → a very short sentence summarizing the content of the recap (max ~8 words, no mention of formatting or HTML). 
- BODY → the complete HTML email fragment generated from the Text to HTML Tool, including the greeting and style block. 
```

7. In `Additional details` in `Credential to use` impostare `Maker-provided credentials`.

![[Pasted image 20251215155729.png]]

8. Nella sezione Input inserire i seguenti dati:

- To | Custom value | User.Email

![[Pasted image 20251215155632.png]]

- Subject | Dynamically fill with AI | (Modificare la Description in Customize)
  
```
The SUBJECT should be a very short sentence (max ~8 words) summarizing the content of the recap, without any reference to formatting or HTML.
```

![[Pasted image 20251215155654.png]]

- Body | Dynamically fill with AI | (Modificare la Description in Customize)

```
The BODY must contain the full HTML email fragment generated from the "Adaptive card to HTML" tool, including the style block and greeting, without any extra text.
```

![[Pasted image 20251215155709.png]]

9. Terminati gli Input salvare il tool.

## Step 4: Modificare le Istruzioni (BONUS) 

1. Aggiungere allo scopo le seguenti istruzioni :

```
Help user with ticket, enter the topic [Ticket card] and after that use
[Adaptive card to Html] and after [Send Ticket Email].
```

2. Modificare le parti fra parentesi quadre `[]` attraverso lo `/` e selezionare il giusto `topic` e i giusti `tools`.

3. Aggiungere alle istruzioni anche una guida su come usare il tool:

```
## Tools Usage
1.[Adaptive card to Html] → Extract your most final and authoritative answer from the conversation and transform it into a professional HTML fragment. Do not modify or summarize beyond what this tool produces. This step ensures that nothing is lost in translation.
2.[Send Ticket Email] → Send the final recap email to the fixed recipient. 
- TO: a known static email (already handled). 
- SUBJECT: a very short summary of the content (≤8 words, no references to formatting/HTML). 
- BODY: the exact HTML produced by the Text to HTML tool.
```

4. Modificare le parti fra parentesi quadre `[]` attraverso lo `/` e selezionare i giusti `tools`.

![[Pasted image 20251215153247.png]]

5. Salvare le `Instructions`.

6. Testare il funzionamento dei tool.

>[!success]
>Con questo ultimo passaggio, il laboratorio sull'utilizzo delle Prompt Actions e dei PowerPlatform Connectors è terminato.
>

