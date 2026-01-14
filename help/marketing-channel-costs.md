---
description: Indicazioni sui costi del canale di marketing per gli utenti di Marketo Measure
title: Costi canale di marketing
exl-id: 36ccaff3-db55-47bd-a24e-4aa1894f13e0
feature: Channels, Spend Management
hidefromtoc: true
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '1309'
ht-degree: 0%

---

# Costi canale di marketing {#marketing-channel-costs}

Uno dei vantaggi principali dell&#39;utilizzo di [!DNL Marketo Measure] è la possibilità di collegare le attività di marketing direttamente all&#39;impatto sui ricavi, con la granularità desiderata. È possibile vedere il ritorno sull&#39;investimento a livello di punto di contatto. Per usufruire di questo vantaggio, i costi del canale devono essere caricati nell&#39;app [!DNL Marketo Measure]. I report sul ROI vengono creati automaticamente e sono disponibili nella **dashboard sul ROI marketing** in [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

[Fai clic qui per passare direttamente alle istruzioni.](/help/marketing-channel-costs.md)

La funzione [!DNL Marketo Measure] spesa di marketing consente ai clienti di caricare la spesa in tutti i canali, i sottocanali e le campagne. Più dati vengono aggiunti dai clienti, più rapporti sul ROI vengono visualizzati nel dashboard di attribuzione dei ricavi.

I costi segnalati e importati da connessioni di annunci diretti vengono automaticamente inseriti al livello più granulare e non è necessario caricarli. Questo include le nostre attuali integrazioni con Google AdWords, Bing Ads, Doubleclick e Facebook.

[Fai clic qui per passare direttamente alle domande frequenti.](/help/marketing-channel-costs.md)

## Definizioni {#definitions}

**Spesa per campagna**

Al livello più granulare, i clienti possono inserire le spese per singole campagne, raggruppate all’interno del rispettivo canale. Per le campagne CRM, [!DNL Marketo Measure] ha inserito l&#39;ID campagna in una colonna separata che consente di mappare la spesa delle campagne offline dal CRM in questa tabella. L’aggiunta di spesa a questo livello consente ai clienti di visualizzare il ROI di Campaign e di ottimizzare le prestazioni per Campaign.

Il totale di tutte le campagne non deve sommare fino a tutti i valori immessi nel canale secondario o nel canale, ma non può superare i valori immessi nel canale secondario o nel canale. Se la somma è inferiore al valore immesso nel canale secondario o nel canale, [!DNL Marketo Measure] aggiungerà automaticamente una riga per &quot;Altro&quot; per coprire la differenza e colmare eventuali spazi vuoti.

**Spesa per sottocanale**

A un livello più alto, i clienti possono inserire le spese per sottocanale, raggruppate sotto il relativo canale. L’aggiunta di spesa a questo livello consente ai clienti di visualizzare il ROI del sottocanale e di ottimizzare le prestazioni per sottocanale.

Il totale di tutti i sottocanali non deve necessariamente sommare fino a qualsiasi valore immesso nel canale, ma non può essere superiore a qualsiasi valore immesso nel canale. Se la somma è inferiore al valore immesso nel canale, [!DNL Marketo Measure] aggiungerà automaticamente una riga per &quot;Altro&quot; per coprire la differenza e colmare eventuali spazi vuoti.

**Spesa per canale**

Al livello più alto, i clienti possono inserire le spese per canale. L&#39;aggiunta di spesa a questo livello consente ai clienti di visualizzare il ROI dei canali e di ottimizzare le prestazioni in base al canale.

**Selezione data**

L&#39;intervallo di date predefinito inizia dalla data di inizio con [!DNL Marketo Measure] fino al mese corrente. Per garantire che i costi rimangano corretti, non è possibile immettere i costi per i mesi futuri, ma è possibile immettere i costi per i mesi precedenti alla partnership con [!DNL Marketo Measure].

**Filtro**

Per limitare i risultati nella tabella Spesa marketing, seleziona un canale in alto per filtrare altri canali. Questa funzione è utile quando si dispone di un team focalizzato su un singolo canale.

**Ricerca**

Utilizza la casella Cerca per trovare il testo corrispondente da canali, sottocanali o campagne.

**Scarica costi correnti**

Il file CSV scaricato estrae i risultati dalla schermata corrente, il che significa che tutte le date, i filtri o le ricerche applicati verranno scaricati così come sono.

**Carica CSV**

Indipendentemente da quale visualizzazione si trovi nel browser, se si tratta di una visualizzazione filtrata o predefinita con tutte le date e i canali, puoi caricare qualsiasi CSV.

L’errore più comune riscontrato è il formato delle colonne di data, che si verifica se il formato della data viene modificato e potrebbe verificarsi intenzionalmente in caso di spostamento tra fogli di Excel e/o Google. Tieni presente che la data deve essere MM-AA, quindi settembre-12 e non settembre-12, o maggio-12 e non 05-12.

## Prima di iniziare {#before-you-begin}

[!DNL Marketo Measure] viene fornito con 13 canali predefiniti che possono essere utilizzati o espansi. Inoltre, è possibile creare fino a 40 canali online e offline per adattarsi alla tua struttura di marketing specifica. Su questa base, è possibile creare un totale di 200 sottocanali per supportare anche questi canali online e offline.

[!DNL Marketo Measure] scaricherà automaticamente i costi dei canali di marketing dalle piattaforme con cui ha un&#39;integrazione API, come Bing Ads e Google AdWords. I costi per le piattaforme non integrate con [!DNL Marketo Measure] devono essere caricati manualmente. I canali di marketing devono essere impostati prima del caricamento dei dati sui costi.

## Caricamento dei costi di marketing {#uploading-marketing-costs}

Una volta che i canali e le regole di marketing sono stati impostati o aggiornati, i relativi costi possono essere caricati. Per farlo, segui la procedura indicata di seguito:

**Passaggio 1: passare alla pagina Spesa marketing nell&#39;app [!DNL Marketo Measure].**

Vai al menu **[!UICONTROL My Account]**, fai clic su **[!UICONTROL Settings]**, quindi passa all&#39;opzione **[!UICONTROL Marketing Spend]** nella barra laterale a sinistra sotto la sezione **[!UICONTROL Reporting]**.

![Vai al menu Account personale, fai clic su Impostazioni, quindi](assets/spend-management-4.png)

**Passaggio 2: scarica il CSV dei costi correnti**

Passare alla destra della schermata e fare clic su **[!UICONTROL Download Current Costs].** Questa opzione consente di scaricare un foglio di calcolo in formato CSV.

![Spostarsi a destra della schermata e fare clic su Scarica corrente](assets/spend-management-1.png)

**Passaggio 3: aprire il file CSV e apportare le modifiche**

Puoi importare il file e aprirlo utilizzando i fogli di Google, i numeri di Apple, Microsoft Excel o un software a tua scelta. [!DNL Marketo Measure] consiglia di utilizzare i fogli di Google.

Dopo aver importato il foglio, apportare le modifiche desiderate, ad esempio aggiungere costi ai canali e ai sottocanali o aggiornare le informazioni esistenti.

Controlla le regole logiche nel foglio. Ogni riga deve contenere un canale e uno dei relativi sottocanali separati da un punto (.) alla fine. È importante utilizzare questo formato in modo coerente.

Ad esempio, per indicare Facebook come sottocanale e Social come canale, la regola deve essere scritta come segue: &quot;Social.Facebook&quot;. Allo stesso modo, per tenere traccia di un evento offline, la sintassi del canale dovrebbe essere: &quot;Events.Big Conference&quot;. L’immagine seguente mostra alcuni esempi:

![Ad esempio, per indicare Facebook come sottocanale e Social come ](assets/spend-management-2.png)

_Note aggiuntive_:

Non modificare le date nel foglio di calcolo perché ciò può causare problemi durante il caricamento del documento.

Non lasciare alcun campo vuoto. Anche se non è presente alcun valore in dollari da aggiungere, immettere 0 come valore in dollari.

Non è necessario immettere o aggiornare i costi di Bing Ads e Google AdWords perché [!DNL Marketo Measure] estrae automaticamente questi dati dalla connessione API con queste piattaforme.

**Passaggio 4: salva il file in formato CSV**

Se utilizzi Google Sheets, assicurati di scaricare prima il file. Non escludere o eliminare dati mensili, in quanto potrebbero causare problemi durante il caricamento del file CSV in [!DNL Marketo Measure] in un secondo momento.

**Passaggio 5: carica il file CSV**

Andare alla sezione **[!UICONTROL Cost]** dell&#39;app [!DNL Marketo Measure] e fare clic su **[!UICONTROL Upload.CSV]**. Il sistema aggiorna e riflette le nuove informazioni.

## Domande frequenti {#faq}

**Perché i numeri sono visualizzati nel file CSV**

Se non viene immesso alcun valore a un livello superiore come Canale o Sottocanale, [!DNL Marketo Measure] sommerà automaticamente i livelli figlio, che verranno presentati dopo il caricamento del file. Inoltre, se la somma dei figli è inferiore a un valore immesso per il padre, [!DNL Marketo Measure] aggiunge una riga &quot;Altro&quot; per mostrare la differenza nel totale.

**Come vengono determinate le campagne nell&#39;elenco visualizzato?**

Al momento, i nostri risultati elencano le campagne che abbiamo visto essere accreditate con un punto di contatto. Se è stata rilevata un’attività da una campagna, viene mostrato che la campagna si è verificata in base alla data del punto di contatto.

**Troppe righe e colonne da esaminare. È possibile consolidare la visualizzazione?**

Grazie alla possibilità di modificare l’intervallo di date, filtrare il canale o cercare valori, puoi consolidare i risultati della tabella in base alle tue esigenze.

**Perché non posso caricare un file?**

Nell&#39;app [!DNL Marketo Measure] sono presenti set di autorizzazioni diversi. Per caricare un file, devi essere un AccountAdmin. Per ovviare a questo problema, richiedi l’accesso all’amministratore del tuo account o fai in modo che l’amministratore del tuo account carichi il file per tuo conto. Un elenco di utenti e dei loro ruoli si trova in **[!UICONTROL My Account]** > **[!UICONTROL Settings]** > **[!UICONTROL View/Add Account Users]**.
