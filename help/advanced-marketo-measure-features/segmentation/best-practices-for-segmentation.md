---
description: Best practice per la segmentazione - [!DNL Marketo Measure]
title: Best practice per la segmentazione
exl-id: 68281210-383b-4688-86e9-27fbdc1fabbb
feature: Segmentation
source-git-commit: 518a984b0d8d640290bd9b637221fcdc0948e5b9
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# Best practice per la segmentazione {#best-practices-for-segmentation}

## Panoramica {#overview}

[!DNL Marketo Measure] La segmentazione ti consente di definire regole, che sono essenzialmente filtri, in base ai campi del sistema di gestione delle relazioni con i clienti per includerli in segmenti singoli. Questi segmenti saranno quindi disponibili per l’utilizzo nelle tue dashboard di Discover e nel tuo [!DNL Salesforce] reportistica.

La segmentazione è fondamentale per l’utilizzo dei [!DNL Marketo Measure] account, in particolare all’interno di Discover boards. Perché il [!DNL Marketo Measure] Le bacheche Discover sono limitate a un set predeterminato di filtri, la segmentazione consente di dissezionare i dati in Discover in modo analogo a come si farebbe nelle [!DNL Salesforce] reportistica.

Quando viene inviato a [!DNL Salesforce], I valori del segmento vengono scritti nel campo &quot;Segmento&quot; e si trovano all’interno di qualsiasi tipo di rapporto Punto di contatto buyer. Questo consente un reporting uniforme su entrambe le piattaforme. Il segmento si trova anche nel &quot;Dettaglio punto di contatto&quot; di qualsiasi punto di contatto.

Quando viene inviato a [!UICONTROL Discover], I segmenti verranno visualizzati come filtro disponibile all’interno del menu a discesa del filtro che si trova su tutte le bacheche.

## Best practice {#best-practice}

Per definire la segmentazione per la prima volta o rivedere solo la segmentazione stabilita in precedenza, tieni presenti le seguenti best practice.

* Semplificalo!
* Allinea il nome del segmento alla nomenclatura dell’organizzazione, ovvero categoria = nome filtro, segmento = valore filtro
* Non utilizzare i campi formula nelle regole
* Quando possibile, crea la segmentazione sia sul lead/contatto che sull’opportunità in modo da poterla utilizzare nell’intero funnel
   * Se si è un cliente di Marketo Measure Ultimate e si è impostato l&#39;oggetto dashboard predefinito come contatto, non utilizzare i due campi seguenti specifici per lead ([fai clic qui per saperne di più](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).
      * b2b.personStatus
      * b2b.isConverted
   * Non tutte le categorie di segmenti saranno allineate in tutto il funnel
      * Ad esempio, una categoria di segmenti di &quot;Tipo di opportunità&quot; non è correlata ai lead, tuttavia un segmento correlato a &quot;Area&quot; è probabilmente una categoria che può essere definita in tutto il funnel
* Pensa al modo in cui attualmente desideri suddividere i dati, sia che si tratti di un elemento di gestione delle relazioni con i clienti o di uno strumento di business intelligence. Considera la possibilità di creare questo elemento come un segmento in [!DNL Marketo Measure] in modo da poter avere lo stesso reporting in Discover

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

Rivedere la segmentazione almeno due volte all’anno assicurerà che la segmentazione sia aggiornata. Come best practice, consigliamo di rivedere le regole all’interno di &quot;[!UICONTROL Segments]&#39; del tuo [!DNL Marketo Measure] Impostazioni account, nonché il richiamo di rapporti in [!DNL Salesforce] per rivedere i segmenti in azione. Questi passaggi aiuteranno te e il tuo team a sentirsi sicuri nella tua segmentazione e, di conseguenza, nella tua [!DNL Marketo Measure] reportistica.

Altri motivi per cui potrebbe essere attivata una revisione della segmentazione sono...

* Fatturato del team marketing
* Modifiche ai campi utilizzati per definire i segmenti
* Aggiunte o modifiche ai segmenti già stabilite

>[!MORELIKETHIS]
>
>[Impostare la segmentazione personalizzata](/help/advanced-marketo-measure-features/segmentation/custom-segmentation.md)
