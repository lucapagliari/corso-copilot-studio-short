# Lab 3 - Knowledge Base
## Step 0: Prerequisiti

Per questo lab è necessario creare un sito SharePoint, seguire i seguenti step:

1. Andare su [Microsoft 365](https://m365.cloud.microsoft/), accedere con il proprio account aziendale/scolastico,  premere su `Apps` e selezionare `All Apps`.

![[Pasted image 20251210165858.png]]

2. Selezionare `SharePoint`, successivamente premere su `Create Site` -> `Team Site` -> `From Microsoft` -> `Standard Team`-> `Use Template`.

![[Pasted image 20251210170004.png]]

![[Pasted image 20251210170043.png]]

![[Pasted image 20251017143821.png]]

![[Pasted image 20251017144036.png]]

3. Ora aggiungere i dettagli del sito SharePoint elencati qui sotto e premere su `Next`.

| Field            | Value                |
| ---------------- | -------------------- |
| Site name        | Help Desk Copilot    |
| Site description | Corso Copilot Studio |
| Site address     | HelpDeskCS           |

4. Andare avanti premendo su `Create site` e `Finish`, senza aggiungere altro.

5. Andare in `Documents`, premere + Upload, e successivamente selezionare i seguenti file:

![[Contoso_Help_Desk_SLA.docx]]

![[Contoso_Incident_Report_Template_Example.docx]]

![[Contoso_Help_Desk_Playbook.docx]]

7. Una volta caricati i file tornare su [Copilot Studio](https://copilotstudio.microsoft.com/).

8. Sistemare le istruzioni del agente del `Lab 1`:

```
# Purpose
Agire come assistente virtuale di primo livello per Zava S.p.a, fornendo supporto immediato per richieste tecniche standard.

# General Guidelines
- Mantieni un tono professionale, cortese e chiaro.
- Fornisci risposte concise e accurate.
- Non fornire informazioni sensibili o non autorizzate.
- Se il problema non può essere risolto, indirizza l'utente al supporto di secondo livello.


# Step-by-Step Instructions
1. Identifica la richiesta: Chiedi all'utente di descrivere il problema.
2. Verifica le informazioni: Assicurati di avere i dati necessari (es. username, email aziendale).
3. Fornisci la soluzione con la KB
4. Escalation: Se il problema non è risolvibile, crea un ticket per il supporto di secondo livello.
```

9. Disattivare la `Web Search` e procedere con l'aggiunta della `Knowledge Base`.

## Step 1: Caricare documenti come knowledge base

1. Dalla schermata `Home` di Copilot Studio selezionare `Agents`.

![[Pasted image 20251210165207.png]]

2. Cercare l'Agente creato nel `Lab 1` e aprire la pagina di configurazione.

3. Selezionare `Knowledge` nel menu in alto adiacente al Nome dell'Agente.

![[Pasted image 20251210165310.png]]

4. Premere su `+Add knowledge`.

![[Pasted image 20251210165334.png]]

5. Una volta premuto apparirà un popup per aggiungere all'agente fonti di conoscenza.

![[Pasted image 20251210165401.png]]

6. Premere su `Upload`, verrà aperta una finestra del File Explorer, nella quale selezionare i seguenti Documenti: 

![[Contoso_KB_Reset_M365_Password.docx]]

>[!Info]
>Gli agenti di Copilot Studio richiedono la [Dataverse search](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-file-upload) per utilizzare questa fonte di conoscenza. Se non puoi aggiungere file Dataverse a un agente, chiedi all’amministratore di attivare la `Dataverse search` nel tuo `Enviroment`.

7. Modificare la `Description` con il seguente testo:

```
Use this Knowledge source when a user need to reset password.
```

6. Testare l'aggiunta della knowledge dalla chat di `test`, premere su `start a new session` e incollare la seguente domanda:

```
How can i reset my Password?
```

>[!Info] Info
>La dimensione massima dei file da uploadare è 512MB e il numero massimo di URL per siti pubblici è 4. Per controllare altre specifiche tecniche andare su [Quotas and limits - Microsoft Copilot Studio | Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-quotas)

## Step 2: Aggiungere il sito SharePoint alla Knowledge

1. Selezionare `Knowledge` nel menu in alto adiacente al Nome dell'Agente.

2. Premere su `+Add knowledge`.

3. Una volta premuto apparirà un popup per aggiungere all'agente fonti di conoscenza.

>[!abstract] Nota:
>Alcune Knowledge Base, come SharePoint e Dataverse, richiedono l'autenticazione dell'utente. Questo significa che l'agente farà riferimento, nelle sue risposte, solo ai dati che l'utente è autorizzato a visualizzare.
>


4. Selezionare `SharePoint`.

![[Pasted image 20251210165550.png]]

5. Premere su `Browse Item`.

![[Pasted image 20251210165625.png]]

6. Cercare il sito SharePoint creato nello `Step 0`.
   
7. Selezionare `Documents`, e premere `Confirm Selection`.
   
8. Aggiornare la Descrizione della Knowledge con la seguente:

```
Essential documentation and resources to support IT service management and end-user assistance.
```

> [!tip] Tip
> L'aggiunta di una descrizione aiuta l'Agente a identificare meglio quale fonte utilizzare in base alla richiesta posta dall'utente.
> 

11. Testare l'aggiunta della knowledge dalla chat di `test`, premere su `start a new session` e incollare la seguente domanda:

```
What are the standard hours vs emergency support availability?
```

> [!tip] 
> Ricordarsi di premere su `start a new session`, perché facendolo la chat di Test si aggiornerà con le ultime modifiche fatte all'Agente.

## Step 3: Aggiungere Files Group (BONUS)

1. Selezionare `Knowledge` nel menu in alto adiacente al Nome dell'Agente.

2. Premere su `+Add knowledge`.

3. Una volta premuto apparirà un popup per aggiungere all'agente fonti di conoscenza.

4. Premere `Upload` e selezionare questi file :

![[Zava_Guida_VPN_v2.docx]]

![[Zava_Guida_VPN_v3.docx]]

![[Zava_Guida_VPN_v1.docx]]

5. Abilitare il `Group these files`.

![[Pasted image 20260213150325.png]]

>[!Info] 
>Per sapere i limiti o eventuali informazioni aggiuntive sui Files Group visitare la [Documentazione](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-file-group)

6. Successivamente modificare il `Name` e la `Description` con :

```
VPN Guide
```

```
Include the installation and usage guides for the ZavaSecure VPN. Use the most update version (v3), unless a different version is required.
```

6. Aggiungere le `Instructions`:

```
The documents are named `Zava_Guida_"topic"_vX`, where X indicates the version (lower = older). **Always use the most recent available version** to provide instructions. Do not use older versions **unless the user explicitly requests it**. Check the version number and the topic before responding, and specify to the user whether you are using the most up-to-date guide.

```

7. Testare l'aggiunta della knowledge dalla chat di `test`, premere su `start a new session` e incollare la seguente domanda:

```
How do I configure Zava VPN?
```


>[!success]
>Con questo ultimo passaggio, il laboratorio per l'aggiunta di Knowledge al nostro Agente è completato.
>

