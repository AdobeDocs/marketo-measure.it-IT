---
description: Best practice per la mappatura dello staging - [!DNL Marketo Measure]
title: Best practice per la mappatura degli staging
exl-id: 1ed380a1-4a3a-4761-b70f-cdf2e290329d
feature: Tracking, Custom Models
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Best practice per la mappatura degli staging {#best-practices-for-stage-mapping}

## Panoramica {#overview}

La sezione Mappatura fasi dell&#39;account [!DNL Marketo Measure] descrive le fasi che [!DNL Marketo Measure] estrae automaticamente dal CRM e tutte le fasi personalizzate definite se si utilizza il modello di attribuzione personalizzato. La validità dei dati di [!DNL Marketo Measure] si basa sul fatto che queste fasi vengono ordinate correttamente in modo che [!DNL Marketo Measure] possa comprendere con precisione il funnel e l&#39;avanzamento dei record in tale funnel.

Nella sezione Mappatura fasi dell&#39;istanza [!DNL Marketo Measure] verranno visualizzate le fasi attive e inattive del CRM. Ordina tutte le fasi in base alle tue esigenze, in base alle esigenze attuali del tuo funnel.

Una funzione aggiuntiva gestita in questa sezione sono gli Stadi di Funnel, che consentono di aggiungere stadi a funnel senza applicare l’attribuzione. Le fasi di funnel verranno tracciate come punti di contatto e popolate nel campo Posizioni punto di contatto nel CRM. Queste fasi di Funnel saranno inoltre rappresentate in varie bacheche di percorso in [!DNL Marketo Measure] Discover.

## Best practice {#best-practices}

Sia che si stia valutando la mappatura dello staging per la prima volta o che si stia solo esaminando l&#39;ordine funnel, è importante tenere presenti le seguenti best practice.

* L&#39;ordine è tutto!
   * Considerando che [!DNL Marketo Measure] richiama sia gli stadi attivi che quelli inattivi dal CRM, confermare che tutti gli stadi che potrebbero essere utilizzati su un lead/contatto o un&#39;opportunità sono raggruppati e ordinati di conseguenza
* Quando definisci una fase personalizzata, assicurati che il tracciamento della cronologia dei campi sia abilitato per tutti i campi utilizzati per definire la fase
* Non utilizzare un campo formula per definire una fase personalizzata
   * Un campo booleano è la best practice consigliata
* La sezione Fase lead o fase contatto è divisa in Perso, Aperto e Convertito; verificare che le fasi siano nella sezione relativa alla fase appropriata
   * Se una fase si trova nella sezione di fase errata, i dati di [!DNL Marketo Measure] potrebbero risultare molto errati
   * Se sei un cliente Marketo Measure Ultimate e hai impostato l&#39;oggetto dashboard predefinito come contatto, non utilizzare i due campi seguenti specifici per lead ([ulteriori informazioni](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).
      * b2b.personStatus
      * b2b.isConverted
* La sezione relativa alla fase Opportunità è divisa in Persa, Aperta e Vinta; verificare che le fasi si trovino nella sezione corrispondente
   * Se una fase si trova nella sezione di fase errata, i dati dei ricavi [!DNL Marketo Measure] o della pipeline potrebbero essere molto errati
* Evita di usare nomi di fase duplicati (il nostro sistema li rileverà e ne rimuoverà automaticamente uno).
* Per impostare una regola che verifichi la presenza di valori NULL, lasciare vuota la casella di testo del valore.

## Best practice per la manutenzione {#best-practices-for-maintenance}

Rivedere la mappatura dello staging una volta all&#39;anno assicurerà che i dati dell&#39;opportunità in [!DNL Marketo Measure] siano accurati e aggiornati.

Altri motivi che potrebbero attivare una revisione della mappatura dello staging includono...

* Fatturato del team marketing
* Eventuali modifiche alle fasi del CRM
* Aggiornamenti al funnel della tua organizzazione
* Visualizzazione dei dati errati sui ricavi nei rapporti di [!DNL Marketo Measure]

>[!MORELIKETHIS]
>
>[Differenza tra gli stadi di Funnel e gli stadi del modello personalizzato](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md#the-difference-between-funnel-stages-and-custom-model-stages)
