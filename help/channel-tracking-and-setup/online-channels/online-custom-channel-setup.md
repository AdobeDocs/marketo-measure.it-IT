---
description: Linee guida per l’installazione di canali personalizzati online per gli utenti di Marketo Measure
title: Impostazione canale personalizzato online
exl-id: 170ac564-6cdd-4036-abf0-b9b230bed4f7
feature: Channels
hidefromtoc: true
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 0%

---

# Impostazione canale personalizzato online {#online-custom-channel-setup}

Per ottenere una reportistica accurata, i canali di marketing devono essere impostati in modo da riflettere la strategia UTM della tua organizzazione. Questa guida illustra il modo migliore per configurare le regole di canale personalizzate.

## Prima di iniziare {#before-you-begin}

Prima di iniziare a creare le regole di canale per [!DNL Marketo Measure], è necessario riflettere sull&#39;organizzazione delle campagne di marketing e su come si adattano al framework [!DNL Marketo Measure]. Determina quali canali, sottocanali, campagne e siti web di riferimento desideri monitorare.

Aspetti da considerare:

* La tua organizzazione può creare un massimo di 40 canali di marketing personalizzati. Ciò include sia i canali offline che online.
* La tua organizzazione può creare fino a 200 sottocanali.
* Ogni raccolta, o bucket, di dati necessita di una propria regola (riga nel foglio di calcolo) per specificare la modalità di organizzazione dei dati. Sii il più specifico possibile.
* La logica [!DNL Marketo Measure] assegna priorità ai dati in ordine decrescente a partire dalla riga superiore del foglio di calcolo fino alla fine. Legge ogni bucket, o cella, riga per riga alla ricerca del primo adattamento. I dati vengono quindi ordinati in base ai valori in questi bucket. Ulteriori informazioni su questo.
* Non ordinare il foglio in ordine alfabetico in quanto questo interferisce con le regole logiche.
* Una volta caricato il file, non puoi modificare nessuna delle regole per sette giorni. [!DNL Marketo Measure] utilizza questo tempo per elaborare e aggiornare i punti di contatto.

## Logica e priorità [!DNL Marketo Measure] {#marketo-measure-logic-and-priorities}

Il primo passaggio consiste nel scaricare il foglio di calcolo del canale personalizzato dall&#39;app [!DNL Marketo Measure]. Passa a **Impostazioni** nella scheda **Account personale** e seleziona **Online**. È possibile selezionare **Scarica modello originale** o **Scarica regole correnti**.

![](assets/online-channels-1.png)

Il foglio di calcolo è composto da sette colonne:

![](assets/online-channels-2.png)

* **Canale:** aggiungi qui i tuoi vari canali di marketing
* **Sottocanale:** aggiungi qui i sottocanali corrispondenti
* **Campagna:** aggiungi qui i nomi delle campagne, sia che il valore provenga da UTM o da Salesforce Campaign per la funzionalità [!DNL Marketo Measure] attività
* **Medium:** la colonna medium rappresenta il valore del parametro utm_medium
* **Source:** la colonna di origine rappresenta il valore del parametro utm_source
* **Pagina di destinazione:** aggiungi qui la pagina di destinazione
* **Sito Web di riferimento:** gli URL dei siti Web che fanno riferimento al traffico delle pagine o la logica integrata di [!DNL Marketo Measure] (indicata tra parentesi)

L’ottava colonna indica quali regole non è possibile eliminare dal foglio di calcolo con &quot;Non rimuovere&quot;. Nella parte superiore del foglio di calcolo sono presenti regole di canale predefinite che [!DNL Marketo Measure] consiglia di non modificare o rimuovere anche se non si utilizzano questi canali. [!DNL Marketo Measure] ha integrazioni profonde con queste piattaforme, pertanto sono incluse per impostazione predefinita.

Le righe rappresentano le regole e l&#39;ordine in cui [!DNL Marketo Measure] assegna la priorità ai dati. La prima riga ha priorità rispetto alla seconda riga, la seconda riga ha priorità rispetto alla terza e così via. Quando determina in quale canale di marketing e sottocanale inserire i punti di contatto, [!DNL Marketo Measure] legge dall&#39;alto verso il basso, da sinistra a destra, finché non trova una riga che soddisfa i criteri del punto di contatto. (Se un punto di contatto ha un `utm_source=Facebook`, viene inserito nel bucket del canale Social.Facebook a causa della regola 15 nella schermata).

![](assets/online-channels-3.png)

[!DNL Marketo Measure] viene fornito con 12 canali predefiniti per il tuo utilizzo. Questi canali sono correlati alle piattaforme con cui [!DNL Marketo Measure] è completamente integrato. Che li utilizzi o meno, non rimuoverli. Se ad esempio utilizzi una di queste piattaforme, Bing Ads, ma preferisci utilizzare una convenzione di denominazione diversa per il canale o il sottocanale, potrai aggiornare il nome. Un esempio è mostrato nell&#39;immagine seguente.

![](assets/online-channels-4.png)

Anche la struttura delle norme è importante. Le regole possono sembrare informazioni ripetute e dati mancanti, ma questa struttura è intenzionale. Per un ordinamento accurato dei dati, è necessario mappare separatamente ogni singola origine sul canale appropriato, anche le origini che condividono sottocanali e canali. Più sono dettagliate e dettagliate le regole, più sono approfonditi i risultati. In pratica, è consigliabile scrivere una regola dettagliata per ogni attività di marketing che desideri monitorare.

Considera la seguente situazione: hai altri annunci che non desideri monitorare per qualche motivo, o ricevi visite al tuo sito web da un canale familiare, ma non da una fonte familiare. Questa situazione potrebbe causare la perdita di dati se [!DNL Marketo Measure] non riesce a trovare la regola appropriata da utilizzare per ordinare i dati. Per evitare che ciò si verifichi, [!DNL Marketo Measure] consiglia di interrompere la regola su più righe.

Ogni parametro o componente della regola viene mappato separatamente al canale. Ad esempio, quando [!DNL Marketo Measure] ha [!DNL Facebook] dati da ordinare, cerca le regole relative a [!DNL Facebook]. Esegue la scansione dall&#39;alto verso il basso. Nell&#39;esempio illustrato di seguito, [!DNL Marketo Measure] comprenderebbe che per il primo sottocanale [!DNL Facebook], tutto ciò che deve leggere è il parametro di origine per rilasciare i dati nel bucket di quella regola.

![](assets/online-channels-5.png)

La regola successiva richiede solo il parametro medium, quindi tutti i dati con quel parametro vengono inseriti in questo canale. Infine per [!DNL Facebook], tutti i dati provenienti dall&#39;URL di Facebook vengono inseriti nell&#39;ultimo bucket di Facebook.

Il canale predefinito &quot;Altro&quot; esiste per acquisire dati che non soddisfano i criteri di alcuna regola. Alcuni bucket nell&#39;altro canale contengono asterischi (&#42;). Questi asterischi rappresentano caratteri jolly che fungono da modello.

![](assets/online-channels-6.jpg)

Poiché la logica [!DNL Marketo Measure] funziona dall&#39;alto verso il basso, la regola con caratteri jolly, indicata con un asterisco (&#42;), deve trovarsi alla fine del foglio regole. Tutti i dati che non vengono rilevati o ordinati dalle altre regole vengono aggiunti a questo bucket di caratteri jolly.

Di seguito sono riportati altri esempi di logica dei caratteri jolly:

* &#42;email&#42; = contiene &quot;email&quot;
* &#42;email = termina con &quot;email&quot;
* e-mail&#42; = [!UICONTROL starts with email]

Inoltre, tieni presente che se crei un sottocanale per uno dei tuoi canali, devi creare un sottocanale per tutte le regole sotto tale canale. In altre parole, se si crea un canale secondario, non è possibile lasciare vuote le altre colonne.

## Configurazione delle regole dei canali personalizzate {#setting-up-your-custom-channels-rules}

Dopo aver deciso come organizzare e assegnare la priorità ai dati, puoi aggiungere le regole al foglio di calcolo. Di seguito sono riportate alcune best practice:

* Mantieni le regole il più semplice possibile dall’inizio. Puoi sempre basarti sulle regole man mano che procedi.
* Non aggiungere caratteri speciali nei nomi dei canali (ad esempio, $%#&amp;&#42;@)
* Non modificare le regole associate a BingAds e AdWords. Queste regole sono fondamentali per il bucket dei dati provenienti automaticamente dall&#39;integrazione API [!DNL Marketo Measure] con queste piattaforme. Cambiare il nome del sottocanale e del canale in base alle tue esigenze non è un problema.
* Non rimuovere le regole che contengono una nota &quot;Non rimuovere&quot;.
* Le regole di ricerca organica vengono sempre inserite dopo [!UICONTROL Paid Search rules]
* Non puoi creare regole basate su sottodomini diversi.
* Se in una cella del foglio di calcolo sono presenti più valori da aggiungere, separarli con un punto e virgola `;`. Senza virgole o spazi.
* Non è necessario aggiungere dot-com (.com) alla fine dell’URL di riferimento.
* Quando aggiungi un URL di riferimento, non metterlo tra parentesi come nelle altre regole relative all’API.

## Caricamento Delle Regole Dei Canali Personalizzati {#uploading-your-custom-channels-rules}

Accertati che tutti i nuovi valori di canale e sottocanale che stai aggiungendo nel file CSV siano già stati aggiunti nell’area delle impostazioni del canale del tuo account Bizible. Controlla che tutti i nomi di canale e sottocanale corrispondano nel file CSV con l&#39;area delle impostazioni del canale del tuo account [!DNL Marketo Measure]. Verifica la presenza di virgole e spazi.

Se ricevi un messaggio di errore durante il caricamento, correggi il problema e ricarica. Se non viene ricevuto alcun messaggio di errore, fare clic su **Salva e elabora** nella parte inferiore della pagina.
