---
unique-page-id: 18874602
description: Costi del canale di marketing - [!DNL Marketo Measure] - Documentazione del prodotto
title: Costi del canale di marketing
exl-id: 36ccaff3-db55-47bd-a24e-4aa1894f13e0
source-git-commit: 54337a0a65b79d80ebeae6531f5e92f4f48721a7
workflow-type: tm+mt
source-wordcount: '1279'
ht-degree: 0%

---

# Costi del canale di marketing {#marketing-channel-costs}

Uno dei vantaggi più importanti dell&#39;utilizzo [!DNL Marketo Measure] è la capacità di collegare le attività di marketing direttamente all’impatto sui ricavi, con la granularità che desideri. È possibile vedere il ritorno sull&#39;investimento a livello di punto di contatto. Per sfruttare questo vantaggio, è sufficiente caricare i costi del canale sul [!DNL Marketo Measure] app. I rapporti sul ROI vengono creati automaticamente e disponibili nella **Dashboard di Marketing ROI** in [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

[Fai clic qui per accedere direttamente alle istruzioni.](/help/marketing-spend/spend-management/marketing-channel-costs.md#uploading-marketing-costs)

La [!DNL Marketo Measure] La funzione di spesa marketing consente ai clienti di caricare le proprie spese su tutti i canali, i sottocanali e le campagne. Più dati vengono aggiunti dai clienti, più rapporti sul ROI emergono nella dashboard di attribuzione dei ricavi.

I costi segnalati e importati dalle connessioni degli annunci diretti vengono automaticamente inseriti al livello più granulare e non devono essere caricati. Sono incluse le nostre integrazioni correnti con Google AdWords, Bing Ads, Doubleclick e Facebook.

[Fai clic qui per accedere direttamente alle domande frequenti.](/help/marketing-spend/spend-management/marketing-channel-costs.md#faq)

## Definizioni {#definitions}

**Spesa per campagna**

Al livello più granulare, i clienti possono immettere le spese per singole campagne, raggruppate all’interno del rispettivo canale. Per le campagne CRM, [!DNL Marketo Measure] ha estratto l’ID campagna in una colonna separata che ti aiuterà a mappare la spesa della campagna offline dal tuo CRM in questa tabella. L’aggiunta di una spesa a questo livello consentirà ai clienti di visualizzare il ROI di Campaign e ottimizzare le prestazioni in base a Campaign.

Il totale di tutte le campagne non deve sommare alcun valore immesso nel canale secondario o nel canale, ma non può essere maggiore di qualsiasi valore immesso nel canale secondario o nel canale. Se la somma è inferiore al valore immesso nel canale secondario o nel canale, [!DNL Marketo Measure] aggiungerà automaticamente una riga per &quot;Altro&quot; per coprire la differenza e riempire eventuali lacune.

**Spesa per canale secondario**

A un livello più alto, i clienti possono inserire la spesa per canale secondario, raggruppati sotto il canale corrispondente. L’aggiunta di una spesa a questo livello consentirà ai clienti di visualizzare il ROI dei sottocanali e di ottimizzare le prestazioni in base al canale secondario.

Il totale di tutti i sottocanali non deve sommare fino a qualsiasi valore immesso nel canale, ma non può essere più di qualsiasi valore immesso nel canale. Se la somma è inferiore al valore inserito nel canale, [!DNL Marketo Measure] aggiungerà automaticamente una riga per &quot;Altro&quot; per coprire la differenza e riempire eventuali lacune.

**Spesa per canale**

Al livello più alto, i clienti possono inserire le spese per canale. L&#39;aggiunta di una spesa a questo livello consentirà ai clienti di visualizzare il ROI del canale e ottimizzare le prestazioni in base al canale.

**Selettore data**

L’intervallo di date predefinito inizia dalla data di inizio con [!DNL Marketo Measure] fino al mese corrente. Per garantire che i costi rimangano corretti, non è possibile inserire i costi per i mesi futuri, ma è possibile inserire i costi per i mesi precedenti la partnership con [!DNL Marketo Measure].

**Filtro**

Per limitare i risultati nella tabella Marketing Spend (Spese di marketing), seleziona un canale in alto per filtrare gli altri canali. Questo è utile quando un team si concentra su un singolo canale.

**Ricerca**

Utilizzare la casella Ricerca per trovare il testo corrispondente da Canali, Sottocanali o Campagne.

**Scarica i costi correnti**

Il CSV scaricato estrarrà i risultati dalla schermata corrente, il che significa che tutte le date, i filtri o la ricerca applicati verranno scaricati così come sono.

**Carica CSV**

Indipendentemente dalla visualizzazione presente nel browser, se si tratta di una visualizzazione filtrata o quella predefinita con tutte le date e i canali, puoi caricare qualsiasi CSV.

L’errore più comune che si verifica è il formato delle colonne di data, che si verifica se il formato della data viene modificato e potrebbe verificarsi intenzionalmente se si passa da Excel a/o Google Sheets. Tieni presente che la data deve essere MM-AA, quindi set-12 e non il 12 settembre o il 12 maggio e non il 05-12.

## Prima di iniziare {#before-you-begin}

[!DNL Marketo Measure] viene fornito con 13 canali predefiniti che possono essere utilizzati o espansi. Inoltre, è possibile creare fino a 40 canali online e offline per adattarsi alla tua struttura di marketing unica. Su questa base, è possibile creare un totale di 200 sottocanali per supportare anche questi canali online e offline.

[!DNL Marketo Measure] scaricherà automaticamente i costi dei canali di marketing dalle piattaforme con cui dispone di un’integrazione API, come Bing Ads e Google AdWords. Costi per piattaforme non integrate con [!DNL Marketo Measure] dovrà essere caricato manualmente. I canali di marketing devono essere impostati prima di caricare i dati dei costi.

## Caricamento dei costi di marketing {#uploading-marketing-costs}

Una volta configurati o aggiornati i canali e le regole di marketing, è possibile caricare i costi associati. A questo scopo, segui i passaggi seguenti:

**Passaggio 1: Passa alla pagina Marketing Spend (Spesa di marketing) nel [!DNL Marketo Measure] App.**

Vai a **[!UICONTROL My Account]** menu, fai clic su **[!UICONTROL Settings]** e quindi passare alla **[!UICONTROL Marketing Spend]** nella barra laterale sinistra sotto **[!UICONTROL Reporting]** sezione .

![](assets/1.png)

**Passaggio 2: Scarica CSV dei costi correnti**

Passa a destra dello schermo e fai clic su **[!UICONTROL Download Current Costs].** Questa opzione consente di scaricare un foglio di calcolo in formato CSV.

![](assets/2.png)

**Passaggio 3: Apri il file CSV e apporta modifiche**

È possibile importare il file e aprirlo utilizzando Google Sheets, Apple Numbers, Microsoft Excel o la scelta del software. [!DNL Marketo Measure] consiglia di utilizzare Google Sheets.

Dopo aver importato il foglio, apporta le modifiche desiderate, ad esempio aggiungendo costi ai canali e ai sottocanali o aggiornando le informazioni esistenti.

Controlla le regole di logica nel tuo foglio. Ciascuna riga deve contenere un canale e uno dei relativi sottocanali separati da un (.) punto alla fine. L&#39;utilizzo coerente di questo formato è importante.

Ad esempio, per indicare Facebook come canale secondario e social come canale, la regola deve essere scritta come segue: &quot;Social.Facebook.&quot; Analogamente, per tenere traccia di un evento offline, la sintassi del canale deve essere: &quot;Events.Big Conference.&quot; Di seguito sono riportati alcuni esempi:

![](assets/3.png)

_Note aggiuntive_:

Non modificare le date nel foglio di calcolo perché questo può causare problemi durante il caricamento del documento.

Non lasciare vuoto alcun campo. Anche se non è presente un valore in dollari da aggiungere, immettere $0 come valore in dollari.

I costi di Bing Ads e Google AdWords non devono essere inseriti o aggiornati perché [!DNL Marketo Measure] richiama automaticamente questi dati dalla relativa connessione API con queste piattaforme.

**Passaggio 4: Salva file in formato CSV**

Se lavori in Google Sheets, assicurati di scaricare prima il file. Non escludere o eliminare dati mensili in quanto causerà difficoltà quando si tenta di caricare il file CSV in [!DNL Marketo Measure] più tardi.

**Passaggio 5: Caricare il file CSV**

Vai a **[!UICONTROL Cost]** della sezione [!DNL Marketo Measure] app e fai clic su **[!UICONTROL Upload.CSV]**. Il sistema si aggiorna e riflette le nuove informazioni.

## Domande frequenti {#faq}

**Perché i numeri compaiono nel CSV**

Se non viene immesso alcun valore a un livello superiore come Canale o Canale secondario, [!DNL Marketo Measure] somma automaticamente i livelli secondari per te, che verranno presentati dopo il caricamento del tuo file. Inoltre, se la somma dei figli è inferiore a un valore inserito per il padre, [!DNL Marketo Measure] aggiungerà una riga &quot;Altro&quot; per mostrare la differenza nel totale.

**Come vengono determinate le campagne nell’elenco visualizzato?**

Al momento, i nostri risultati elencano le campagne che abbiamo visto essere accreditate con un punto di contatto. Se c’è stata un’attività da una campagna, la mostreremo in base alla data del punto di contatto in cui si è verificata.

**Ci sono troppe righe e colonne da scorrere - posso consolidare la visualizzazione?**

Grazie alla possibilità di modificare l’intervallo di date, filtrare il canale o cercare i valori, è possibile consolidare i risultati della tabella per adattarli meglio alle proprie esigenze.

**Perché non posso caricare un file?**

Sono disponibili diversi set di autorizzazioni all&#39;interno di [!DNL Marketo Measure] App. Per caricare un file, devi essere un &quot;AccountAdmin&quot;. Per aggirare questo problema, richiedi l&#39;accesso al tuo AccountAdmin o chiedi al tuo AccountAdmin di caricare il file per tuo conto. Un elenco degli utenti e dei loro ruoli si trova in **[!UICONTROL My Account]** > **[!UICONTROL Settings]** > **[!UICONTROL View/Add Account Users]**.
