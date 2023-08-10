---
description: Best practice per i canali online - [!DNL Marketo Measure] - Documentazione del prodotto
title: Best practice per i canali online
exl-id: 766cb01c-98b3-492d-bb35-e0a78b76333a
feature: Channels
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Best practice per i canali online {#best-practices-for-online-channels}

## Panoramica {#overview}

Per ottenere [!DNL Marketo Measure] reporting, i canali di marketing devono essere configurati correttamente. Nel campo Canale di marketing viene visualizzato il gruppo di attività di marketing di livello più alto a cui può appartenere un punto di contatto (ad esempio, Ricerca a pagamento, Diretta, Social, ecc.).

La configurazione dei canali di marketing può essere effettuata in due modi: online e offline. Questo documento si concentrerà sulla [!DNL Marketo Measure] consigli sulle best practice per l’impostazione e la manutenzione dei canali online.

Le regole del canale online sono le linee guida per [!DNL Marketo Measure] mappa i punti di contatto digitali, ovvero tutti i punti di contatto tracciati e creati tramite [!DNL Marketo Measure] JS sul sito. Se queste regole non sono complete o non sono ordinate correttamente, i punti di contatto possono essere attribuiti al canale errato, riducendo così la precisione della generazione dei rapporti. Assicurati che le regole del canale online siano accurate e aggiornate, assicurerai che i dati digitali vengano attribuiti al canale e ai sottocanali corretti nel tuo [!DNL Marketo Measure] Generazione rapporti.

## Best practice {#best-practice}

Se imposti le regole per la prima volta o le esamini solo per verificarne l’accuratezza, tieni presente le seguenti best practice.

Prenditi un po’ di tempo per pensare all’organizzazione delle campagne di marketing e a come si adattano al [!DNL Marketo Measure] infrastruttura. Determina quali canali e sottocanali devono essere rappresentati nei tuoi canali online, nonché quali campagne, parametri UTM o siti web di riferimento differenziano tali canali l’uno dall’altro.

Aspetti da considerare:

* Tutti i canali digitali e i sottocanali devono essere rappresentati con almeno una regola
   * Se il canale non porta le persone al sito, non è un canale online
* È possibile avere più regole per un canale/sottocanale
   * È possibile considerare più regole come &quot;lanciare una rete più ampia&quot; per garantire che ogni punto di contatto sia mappato correttamente. Spesso i parametri possono essere aggiunti o saltati completamente in modo errato, pertanto l’esistenza di più regole per acquisire un canale/sottocanale è una buona idea per garantire la precisione della mappatura.
* [!DNL Marketo Measure] la logica dà priorità alla mappatura dei punti di contatto in ordine decrescente, a partire dalla riga superiore del foglio di calcolo fino alla fine
   * [!DNL Marketo Measure] legge ogni regola (riga), cercando true e first fit. Il punto di contatto viene quindi mappato su quel canale/sottocanale
   * Non ordinare il foglio in ordine alfabetico in quanto ciò interferisce con le regole logiche.
* Gestisci le regole tra parentesi quadre, non modificarle né aggiungerle (ad esempio; [Ricerca AdWords a pagamento] o [Facebook a pagamento] )
   * Sono preconfigurati [!DNL Marketo Measure] regole che hanno una logica incorporata, a cui sono associati i [!DNL Marketo Measure] integrazioni. Assegna a queste regole la priorità principale per quella sezione canale/sottocanale per garantire che [!DNL Marketo Measure] Le integrazioni possono funzionare come previsto.
* Una volta caricato il file, non puoi modificare nessuna delle regole per sette giorni
   * [!DNL Marketo Measure] utilizza questo tempo per elaborare e aggiornare i punti di contatto; assicurati quindi di controllare due volte le regole prima di caricare.

## Procedure consigliate per la manutenzione {#best-practice-for-maintenace}

Una volta salvate ed elaborate, le regole del canale online funzionano continuamente per raccogliere i punti di contatto digitali. Tuttavia, alcune modifiche o scenari richiedono la revisione della configurazione del canale online. [!DNL Marketo Measure] consiglia di rivedere le regole del canale online una volta ogni sei mesi. In questo modo il tuo [!DNL Marketo Measure] I dati sono allineati con le definizioni interne di canali/sottocanali online e con l’utilizzo di UTM.

Altri elementi che potrebbero attivare il team per la manutenzione dei canali online sono....

* Lancio del nuovo canale/sottocanale digitale
* I parametri UTM vengono aggiornati o modificati
* Modifiche all’organizzazione del canale o alle convenzioni di denominazione
* Fatturato del team marketing

Se il tuo team ha avuto esperienza di una delle situazioni sopra descritte di recente [!DNL Marketo Measure] consiglia di rivedere le regole dei canali online e apportare le modifiche appropriate.

>[!MORELIKETHIS]
>
>* [Configurazione canale online](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
>* [Parametri UTM](/help/channel-tracking-and-setup/online-channels/utm-parameters.md)
>* [Canale di marketing e sottocanale](/help/channel-tracking-and-setup/online-channels/marketing-channels-and-subchannels.md)
>* [Best practice UTM](/help/channel-tracking-and-setup/online-channels/best-practices-for-setting-up-utm-parameters.md)
