# Lab 1 - Copilot Studio Setup
## Step 0: Prerequisiti

1. `Mail aziendale o scolastica` ( @outlook.com, @gmail.com, etc., email personali non sono supportate).
2. Accesso a `internet`e un motore di ricerca (Edge, Chrome, or Firefox recommended).
3. Essere familiari con `Microsoft 365`.
4. (Opzionale) Avere una carta di credito o un metodo di pagamento in caso di acquisto di licenze a pagamento.

## Step 1: Ottenere un Microsoft 365 Account

E' possibile usare un account esistente o seguire questi step per procurarsi la licenza appropriata:

1. Acquistare una `Microsoft 365 Business Subscription`
2. Andare su [Microsoft 365 Business Plans and Pricing Page](https://www.microsoft.com/microsoft-365/business/microsoft-365-plans-and-pricing)
3. Selezionare `Try for free` e compilare il form guidato con le informazioni per l'account e metodo di pagamento.

![[Pasted image 20251201104606.png]]

4. Una volta ottenuto l'account eseguire il `login`.

## Step 2: Iniziare la Copilot Studio Trial

Una volta ottenuto un `Microsoft 365 Tenant`, è necessario l'accesso a `Copilot Studio`. E' possibile riscattare gratuitamente una Trial di 30 giorni seguendo questi step:

1. Navigare su [aka.ms/TryCopilotStudio](https://aka.ms/TryCopilotStudio).

![[Pasted image 20251201104705.png]]

2. Inserire le informazioni dell'account creato negli step precedenti e premere`Next`.

3. Una volta riconosciuto l'account. Selezionare `Sign In`.

4. Premere su `Start Free Trial`.

> [!tip] Trial Notes
> 1. La versione di prova gratuita offre tutte le funzionalità di Copilot Studio.
> 2. Verranno inviate notifiche via email relative alla scadenza della prova. È possibile estendere la prova a incrementi di 30 giorni (fino a un massimo di 90 giorni di runtime dell'agente).
> 3. Se l'amministratore del tenant ha disattivato la registrazione self-service, verrà visualizzato un errore: in tal caso, contattare l'amministratore Microsoft 365 per riattivarla.

## Step 3: Creare un nuovo Developer Environment

Per proseguire con il lab conviene creare un nuovo Enviroment dove gestire i nostri Agenti, per far ciò basta seguire questi step:

1. Andare su [Power Apps Developer Plan website](https://aka.ms/PowerAppsDevPlan).

![[Pasted image 20251201104901.png]]

2. Inserire l'`email address` -> Spuntare la `checkbox` -> Selezionare `Start free`.

3. Dopo aver eseguito il login per il Developer Plan, verrà aperto [Power Apps](https://make.powerapps.com/). 

4. Utilizzare questo nuovo `Enviroment` per il Lab su `Copilot Studio`.

> [!Note] Note:
Se si utilizza un account Microsoft 365 esistente e non ne è stato creato uno nello Step 1, ad esempio utilizzando il proprio account nell'organizzazione di lavoro, è possibile che l'amministratore IT (o il team equivalente) che gestisce il tenant/ambiente abbia disattivato il processo di registrazione. In tal caso, contattare l'amministratore oppure creare un tenant di test come indicato nello Step 1.

## Step 4: Creare una nuova Solution

- Una volta aperto [Copilot Studio](https://copilotstudio.microsoft.com/), essere sicuri di aver selezionato il nuovo `developer environment`, creato nello Step 3.

- Per cambiare `Enviroment` in alto a destra selezionare il box `Enviroment` e cambiare il `default Enviroment` con quello nuovo.

## Step 4.1: Creare un Solution publisher

 1. Dopo aver selezionato il giusto`Copilot Studio environment`, premere sull'`ellipsis icon (. . .)`nel menù a sinistra su Copilot Studio. Premere su `Solutions` sotto`Explore`.

![[Pasted image 20251201105403.png]]

2. Verrà aperto il`Solution Explorer`in Copilot Studio. Premere `+ New solution`.

![[Pasted image 20251201105522.png]]

3. Il pannello`New solution` apparirà e sarà possibile definire i dettagli della`Solution`.Ma prima è necessario creare un nuovo`Publisher`. Selezionare `+ New publisher`.

![[Pasted image 20251201105616.png]]

4. La Tab `Properties`del nuovo `Publisher`apparirà con campi obbligatori e non obbligatori da compilare nella scheda `Properties`.

![[Pasted image 20251201105643.png]]

- Qui è possibile delineare i dettagli del `Publisher`che verranno utilizzati come etichetta o marchio per identificare chi ha creato o possiede la `Solution`.

|Property|Description|Required|
|---|---|---|
|Display name|Display name for the publisher|Yes|
|Name|The unique name and schema name for the publisher|Yes|
|Description|Outlines the purpose of the solution|No|
|Prefix|Publisher prefix which will be applied to newly created components|Yes|
|Choice value prefix|Generates a number based on the publisher prefix. This number is used when you add options to choices and provides an indicator of which solution was used to add the option.|Yes|
5. Copia e incolla il seguente`Display name`:

```
My Publisher
```

6. Copia e incolla il seguente`Name`:

```
MyPublisher
```

7. Copia e incolla la`Description`:

```
Corso Copilot Studio
```

8. Copia e incolla il`Prefix`:

```
myp
```

9. Per impostazione predefinita, il prefisso del valore `Choice` mostrerà un valore intero. Aggiornare questo a `77000` (nota: solo per facilità di lettura, non ha alcun effetto pratico).

10. Selezionare la `Properties` tab e premere `Save` per creare il `Publisher`.

11. La pagina `New publisher` verrà chiusa e il riquadro `New solution` si aprirà con il Publisher appena creato selezionato.

## Step 4.2: Creare la New Solution

Una volta creato il `publisher`, è possibile completare il resto del modulo nel riquadro `New solution`.

1. Copia e incolla il`Display name`:

```
Corso Copilot Studio
```

2. Copia e incolla il seguente`Name`:

```
CorsoCopilotStudio
```

3. Visto che è stata creata una nuova `Solution` il  [**Version** number](https://learn.microsoft.com/power-apps/maker/data-platform/update-solutions#understanding-version-numbers-for-updates/?WT.mc_id=power-172615-ebenitez) di default sarà`1.0.0.0`.

4. Selezionare il`Set as your preferred solution` checkbox.

5. Espandere `More Options` per vedere dettagli aggiuntivi della `Solution`,lasciare i campi bianchi per questo lab.

6. Premere `Create`.

7. La soluzione `Corso Copilot Studio` è stata creata. Non saranno presenti `components` finché non verrà creato un agente in Copilot Studio. Selezionare l’icona della `Back Arrow` per tornare al Solution Explorer.

8. La `Current preferred Solution` risulta essere `Corso Copilot Studio`, in quanto in precedenza è stata selezionata la casella di controllo `Set as your preferred solution`.

## Step 5: Creare un Custom Agent da Conversazione

Una volta creata la`Solution` e il`Publisher`è possibile iniziare il lab di creazione del primo `Custom Agent`.

1. Accedere alla pagina `Agent` di [Copilot Studio](https://copilotstudio.microsoft.com/) e verificare la `Solution` nel menu delle impostazioni tramite l’icona a forma di ingranaggio.

![[Pasted image 20251201110746.png]]

![[Pasted image 20251201110815.png]]

2. Successivamente nel `Chat field` inserire la seguente descrizione dell'`Agent`.

![[Pasted image 20251201110847.png]]

```
You are the first-level virtual assistant for Zava Spa called "Help Desk". Your task is to provide immediate support for standard technical requests: password reset, credential recovery, access issues, basic configurations, and guided procedures. Maintain a professional and courteous tone.
```

3. In Copilot Studio verrà avviato il provisioning dell'`Agent`.

4. Al termine del provisioning, la configurazione dell'agente verrà generata da Copilot sulla base della descrizione fornita. Scorrere verso il basso per visualizzare la sezione `Overview` dell'agente, che include `Name`, `Description`, `Instructions`, `Agent's Model`, `Knowledge sources` e `Suggested prompts`.

> [!success] 
> 
>Con questo ultimo passaggio, il laboratorio per la creazione del primo agente in Copilot Studio è completato.
