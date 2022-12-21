---
description: Best practice per i canali online - [!DNL Marketo Measure] - Documentazione del prodotto
title: Best practice per i canali online
exl-id: 766cb01c-98b3-492d-bb35-e0a78b76333a
source-git-commit: 02f686645e942089df92800d8d14c76215ae558f
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Best practice per i canali online {#best-practices-for-online-channels}

## Panoramica {#overview}

Per avere precisione [!DNL Marketo Measure] reporting, i canali di marketing devono essere configurati correttamente. Il campo canale di marketing mostra il gruppo di livello più alto di attività di marketing a cui un punto di contatto può appartenere (ad esempio, Ricerca a pagamento, Diretta, Social, ecc.).

Esistono due aspetti per configurare i canali di marketing: online e offline. Questo documento sarà incentrato sul [!DNL Marketo Measure] consigli sulle best practice per la configurazione e la manutenzione dei canali online.

Le regole del canale online sono le linee guida di come [!DNL Marketo Measure] mappa i tuoi punti di contatto digitali, ovvero tutti i punti di contatto tracciati e creati tramite il [!DNL Marketo Measure] JS sul tuo sito. Se queste regole non sono complete o non sono ordinate correttamente, i punti di contatto possono essere attribuiti al canale errato, riducendo quindi la precisione del reporting. Assicurare che le regole del Canale Online siano accurate e aggiornate garantirà che i tuoi dati digitali siano attribuiti al canale e ai sottocanali corretti nel tuo [!DNL Marketo Measure] Generazione rapporti.

## Best practice {#best-practice}

Sia che tu stia impostando le regole per la prima volta o che le riveda per verificarne l&#39;accuratezza, tieni a mente le seguenti best practice.

Prenditi del tempo per pensare all’organizzazione delle campagne di marketing e a come si adattano alle [!DNL Marketo Measure] struttura. Determina quali canali e sottocanali devono essere rappresentati nei canali online, nonché quali campagne, parametri UTM o siti web di riferimento differenziano tali canali gli uni dagli altri.

Aspetti da tenere a mente:

* Tutti i canali digitali e i sottocanali devono essere rappresentati con almeno una regola
   * Se il canale non porta le persone al tuo sito, non è un canale online
* È lecito avere più regole per un canale/canale secondario
   * È possibile considerare più regole come &quot;casting a più wide net&quot; (colata una rete più ampia) per garantire che ogni punto di contatto sia mappato correttamente. Spesso i parametri possono essere aggiunti o mancati completamente in modo errato, quindi avere più regole per acquisire un canale/canale secondario è una buona idea per garantire la precisione della mappatura.
* [!DNL Marketo Measure] la logica dà priorità alla mappatura dei punti di contatto in ordine decrescente a partire dalla riga superiore del foglio di calcolo e per scendere
   * [!DNL Marketo Measure] legge ogni regola (riga), cercando il vero e il primo adattamento. Il punto di contatto viene quindi mappato su tale canale/canale secondario
   * Non ordinare il foglio in ordine alfabetico, in quanto interferirà con le regole logiche.
* Mantenere le regole tra parentesi graffe, non modificare o aggiungere alle regole tra parentesi (esempio; [Ricerca adWords a pagamento] o [Facebook a pagamento] )
   * Queste sono pronte all&#39;uso [!DNL Marketo Measure] regole che hanno generato una logica, che sono legate al [!DNL Marketo Measure] integrazioni. Attribuisci a queste regole la massima priorità per la sezione canale/sottocanale per garantire [!DNL Marketo Measure] le integrazioni possono funzionare come da progetto.
* Una volta caricato il file, non puoi modificare nessuna delle regole per sette giorni
   * [!DNL Marketo Measure] utilizza questo tempo per elaborare e aggiornare i punti di contatto, quindi assicurati di controllare due volte le regole prima di caricarle.

## Best practice per la manutenzione {#best-practice-for-maintenace}

Una volta salvate ed elaborate, le regole del Canale Online funzionano continuamente per impennare i punti di contatto digitali. Tuttavia, alcune modifiche o scenari richiedono la revisione della configurazione del canale online. [!DNL Marketo Measure] consiglia di rivedere le regole del canale online una volta ogni sei mesi. Questo assicurerà che il [!DNL Marketo Measure] i dati sono allineati con le definizioni interne di canali/sottocanali online e con l’utilizzo di UTM.

Altri elementi che potrebbero indurre il team a eseguire la manutenzione dei canali online includono...

* Nuovo canale/canale digitale
* I parametri UTM vengono aggiornati o modificati
* Modifiche all&#39;organizzazione dei canali o alle convenzioni di denominazione
* Fatturato del team di marketing

Se il tuo team ha sperimentato uno dei precedenti di recente [!DNL Marketo Measure] consiglia di rivedere le regole dei canali online e di apportare le modifiche appropriate.

>[!MORELIKETHIS]
>
>* [Configurazione del canale online](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
>* [Parametri UTM](/help/channel-tracking-and-setup/online-channels/utm-parameters.md)
>* [Canale di marketing e canale secondario](/help/channel-tracking-and-setup/online-channels/marketing-channels-and-subchannels.md)
>* [Best practice per l’UTM](/help/channel-tracking-and-setup/online-channels/best-practices-for-setting-up-utm-parameters.md)

