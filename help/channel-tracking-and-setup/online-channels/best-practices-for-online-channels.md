---
description: Best practice per i canali online - [!DNL Marketo Measure]
title: Best practice per i canali online
exl-id: 766cb01c-98b3-492d-bb35-e0a78b76333a
feature: Channels
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 0%

---


# Best practice per i canali online {#best-practices-for-online-channels}

## Panoramica {#overview}

Per ottenere rapporti accurati su [!DNL Marketo Measure], i canali di marketing devono essere configurati correttamente. Nel campo Canale di marketing viene visualizzato il gruppo di attività di marketing di livello più alto a cui può appartenere un punto di contatto, ad esempio Ricerca a pagamento, Diretta, Social e così via.

La configurazione dei canali di marketing può essere effettuata in due modi: online e offline. Questo documento si concentra sulle [!DNL Marketo Measure] best practice consigliate per la configurazione e la manutenzione dei tuoi canali online.

Le regole del canale online sono le linee guida per la mappatura di [!DNL Marketo Measure] dei punti di contatto digitali, ovvero di tutti i punti di contatto tracciati e creati tramite [!DNL Marketo Measure] JS sul sito. Se queste regole non sono complete o non sono ordinate correttamente, i punti di contatto possono essere attribuiti al canale errato, riducendo così la precisione della generazione dei rapporti. La verifica dell&#39;accuratezza e dell&#39;aggiornamento delle regole del canale online garantisce che i dati digitali vengano attribuiti al canale e ai sottocanali corretti nel reporting di [!DNL Marketo Measure].

## Best practice {#best-practice}

Se imposti le regole per la prima volta o le esamini solo per verificarne l’accuratezza, tieni presente le seguenti best practice.

Prenditi un po&#39; di tempo per pensare all&#39;organizzazione delle campagne di marketing e a come rientrano nel framework [!DNL Marketo Measure]. Determina quali canali e sottocanali devono essere rappresentati nei tuoi canali online e quali campagne, parametri UTM o siti web di riferimento differenziano tali canali l’uno dall’altro.

Aspetti da considerare:

* Tutti i canali digitali e i sottocanali devono essere rappresentati con almeno una regola
   * Se il canale non porta le persone al sito, non è un canale online
* È possibile avere più regole per un canale/sottocanale
   * È possibile considerare più regole come &quot;lanciare una rete più ampia&quot; per garantire che ogni punto di contatto sia mappato correttamente. Spesso i parametri possono essere aggiunti o saltati completamente in modo errato, pertanto l’esistenza di più regole per acquisire un canale/sottocanale è una buona idea per garantire la precisione della mappatura.
* La logica [!DNL Marketo Measure] assegna priorità alla mappatura dei punti di contatto in ordine decrescente, a partire dalla riga superiore del foglio di calcolo fino alla fine
   * [!DNL Marketo Measure] legge ogni regola (riga), cercando il vero e il primo adattamento. Il punto di contatto viene quindi mappato su quel canale/sottocanale
   * Non ordinare il foglio in ordine alfabetico in quanto questo interferisce con le regole logiche.
* Mantieni le regole tra parentesi quadre, non modificare o aggiungere le regole tra parentesi quadre (ad esempio: [Ricerca AdWords Pagata] o [Facebook Pagata])
   * Sono regole predefinite [!DNL Marketo Measure] con logica incorporata, che sono collegate alle integrazioni [!DNL Marketo Measure]. Assegna a queste regole la massima priorità per la sezione canale/sottocanale per garantire che le integrazioni [!DNL Marketo Measure] funzionino come previsto.
* Una volta caricato il file, non puoi modificare nessuna delle regole per sette giorni
   * [!DNL Marketo Measure] utilizza questo tempo per elaborare e aggiornare i punti di contatto, quindi assicurati di controllare le regole prima di caricare.

## Procedure consigliate per la manutenzione {#best-practice-for-maintenace}

Dopo il salvataggio e l’elaborazione delle regole del canale online, queste funzionano continuamente per raccogliere i punti di contatto digitali. Tuttavia, alcune modifiche o scenari richiedono la revisione della configurazione del canale online. [!DNL Marketo Measure] consiglia di rivedere le regole del canale online ogni sei mesi. In questo modo i dati di [!DNL Marketo Measure] saranno allineati con le definizioni interne dei canali/sottocanali online e con l&#39;utilizzo di UTM.

Altri elementi che potrebbero attivare il team per la manutenzione dei canali online sono....

* Lancio del nuovo canale/sottocanale digitale
* I parametri UTM vengono aggiornati o modificati
* Modifiche all’organizzazione del canale o alle convenzioni di denominazione
* Fatturato del team marketing

Se il tuo team ha riscontrato uno degli eventi sopra descritti di recente, [!DNL Marketo Measure] ti consiglia di rivedere le regole dei canali online e apportare le modifiche appropriate.

>[!MORELIKETHIS]
> [Configurazione canale in linea](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
> [Parametri UTM](/help/channel-tracking-and-setup/online-channels/utm-parameters.md)
> [Canale di marketing e sottocanale](/help/channel-tracking-and-setup/online-channels/marketing-channels-and-subchannels.md)
> [Best practice UTM](/help/channel-tracking-and-setup/online-channels/best-practices-for-setting-up-utm-parameters.md)
