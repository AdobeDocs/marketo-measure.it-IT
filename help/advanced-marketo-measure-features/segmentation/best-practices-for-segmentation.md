---
description: Best practice per la segmentazione - [!DNL Marketo Measure]
title: Best practice per la segmentazione
exl-id: 68281210-383b-4688-86e9-27fbdc1fabbb
feature: Segmentation
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Best practice per la segmentazione {#best-practices-for-segmentation}

## Panoramica {#overview}

La segmentazione di [!DNL Marketo Measure] ti consente di definire regole, che sono essenzialmente filtri, in base ai campi del tuo sistema di gestione delle relazioni con i clienti per includerli nei singoli segmenti. Questi segmenti saranno quindi disponibili per l&#39;utilizzo nelle dashboard di individuazione e nel reporting di [!DNL Salesforce].

La segmentazione è fondamentale per l&#39;utilizzo dell&#39;account [!DNL Marketo Measure], in particolare all&#39;interno delle bacheche Discover. Poiché le bacheche di individuazione di [!DNL Marketo Measure] sono limitate a un set di filtri predeterminato, la segmentazione consente di dissezionare i dati in Discover in modo analogo a quanto si farebbe nei rapporti di [!DNL Salesforce].

Quando viene inviato a [!DNL Salesforce], i valori del segmento vengono scritti nel campo &quot;Segmento&quot; e si trovano all&#39;interno di qualsiasi tipo di rapporto Punto di contatto buyer. Questo consente un reporting uniforme su entrambe le piattaforme. Il segmento si trova anche nel &quot;Dettaglio punto di contatto&quot; di qualsiasi punto di contatto.

Quando viene inviato a [!UICONTROL Discover], i segmenti verranno visualizzati come filtro disponibile all&#39;interno del menu a discesa dei filtri disponibile in tutte le bacheche.

## Best practice {#best-practice}

Se definisci la segmentazione per la prima volta o esamini solo la segmentazione stabilita in precedenza, tieni presente le seguenti best practice.

* Semplificalo!
* Allinea il nome del segmento alla nomenclatura dell’organizzazione, ovvero categoria = nome filtro, segmento = valore filtro
* Non utilizzare i campi formula nelle regole
* Quando possibile, crea la segmentazione sia sul lead/contatto che sull’opportunità in modo da poterla utilizzare in tutto il funnel
   * Se sei un cliente Marketo Measure Ultimate e hai impostato l&#39;oggetto dashboard predefinito come contatto, non utilizzare i due campi seguenti specifici per lead ([ulteriori informazioni qui](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).
      * b2b.personStatus
      * b2b.isConverted
   * Non tutte le categorie di segmenti verranno allineate in tutto funnel
      * Ad esempio, una categoria di segmenti &quot;Tipo di opportunità&quot; non è correlata ai lead, tuttavia un segmento correlato a &quot;Area&quot; è probabilmente una categoria che può essere definita in funnel
* Pensa al modo in cui attualmente desideri suddividere i tuoi dati, sia che si tratti di un CRM o di uno strumento BI, e considera la creazione di questo come un segmento in [!DNL Marketo Measure] in modo da poter avere lo stesso reporting in Discover

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

Rivedere la segmentazione almeno due volte all’anno assicurerà che la segmentazione sia aggiornata. Come best practice, ti consigliamo di rivedere le regole nella scheda &#39;[!UICONTROL Segments]&#39; delle impostazioni dell&#39;account [!DNL Marketo Measure], nonché di richiamare rapporti all&#39;interno di [!DNL Salesforce] per rivedere i tuoi segmenti in azione. Questi passaggi aiuteranno te e il tuo team a sentirsi sicuri della tua segmentazione e, di conseguenza, delle tue attività di reporting per [!DNL Marketo Measure].

Altri motivi per cui potrebbe essere attivata una revisione della segmentazione sono...

* Fatturato del team marketing
* Modifiche ai campi utilizzati per definire i segmenti
* Aggiunte o modifiche ai segmenti già stabilite

>[!MORELIKETHIS]
>
>[Come impostare la segmentazione personalizzata](/help/advanced-marketo-measure-features/segmentation/custom-segmentation.md)
