---
description: Best practice per la segmentazione - [!DNL Marketo Measure] - Documentazione del prodotto
title: Best practice per la segmentazione
exl-id: 68281210-383b-4688-86e9-27fbdc1fabbb
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Best practice per la segmentazione {#best-practices-for-segmentation}

## Panoramica {#overview}

[!DNL Marketo Measure] La segmentazione ti consente di definire regole, che sono essenzialmente filtri, in base ai campi CRM per raggrupparli in segmenti singoli. Questi segmenti saranno quindi disponibili per l’utilizzo nelle dashboard di Discover e nei [!DNL Salesforce] rapporti.

La segmentazione è fondamentale per l’utilizzo del [!DNL Marketo Measure] account, specialmente all&#39;interno di voi Scopri bacheche. Perché [!DNL Marketo Measure] Le bacheche sono limitate a un set predeterminato di filtri, la segmentazione ti dà la possibilità di dissezionare i tuoi dati in Discover come faresti nel tuo [!DNL Salesforce] rapporti.

Quando viene inviato a [!DNL Salesforce], i valori del segmento vengono scritti nel campo &quot;Segmento&quot; e si trovano in qualsiasi tipo di rapporto relativo ai punti di contatto dell’acquirente. Ciò consente di ottenere rapporti uniformi tra entrambe le piattaforme. Il segmento si trova anche nel campo &quot;Dettaglio punto di contatto&quot; di qualsiasi punto di contatto.

Quando viene inviato a Discover, i segmenti vengono visualizzati come filtro disponibile nel menu a discesa del filtro presente su tutte le bacheche.

## Best practice {#best-practice}

Che tu stia definendo la segmentazione per la prima volta o semplicemente rivedendo la segmentazione stabilita in precedenza, tieni a mente le seguenti best practice.

* La tenga semplice!
* Allinea il nome del segmento alla nomenclatura dell’organizzazione, ovvero la categoria = nome del filtro, segmento = valore del filtro
* Non utilizzare i campi formula nelle regole
* Quando possibile, crea la segmentazione sia su Lead/Contatto che su Opportunità in modo da poterla utilizzare nell’intero funnel
   * Non tutte le categorie di segmenti vengono allineate nell’intero funnel
      * Una categoria di segmento di &quot;Tipo opportunità&quot; non si riferisce ad esempio ai lead, tuttavia un segmento correlato a &quot;Regione&quot; è probabilmente una categoria che può essere definita in tutto il funnel
* Pensa ai modi in cui attualmente ti piace suddividere i dati, sia che si tratti di uno strumento CRM o BI, considera la creazione di questo come segmento in [!DNL Marketo Measure] in modo da poter avere lo stesso reporting in Discover

## Best practice per la manutenzione {#best-practice-for-maintenance}

Rivedere la segmentazione almeno due volte all’anno assicurerà che la segmentazione sia aggiornata. Come best practice, ti consigliamo di rivedere le tue regole all’interno di[!UICONTROL Segments]scheda del [!DNL Marketo Measure] Impostazioni account, nonché richiamare rapporti in [!DNL Salesforce] per rivedere i segmenti in azione. Questi passaggi aiuteranno te e il tuo team a sentirsi sicuri della tua segmentazione e successivamente del tuo [!DNL Marketo Measure] rapporti.

Altri motivi per cui potrebbe innescare una revisione della segmentazione includono..

* Fatturato del team di marketing
* Modifiche ai campi utilizzati per definire i segmenti
* Aggiunte o modifiche ai segmenti già stabiliti

>[!MORELIKETHIS]
>
>[Come impostare la segmentazione personalizzata](/help/advanced-marketo-measure-features/segmentation/custom-segmentation.md)
