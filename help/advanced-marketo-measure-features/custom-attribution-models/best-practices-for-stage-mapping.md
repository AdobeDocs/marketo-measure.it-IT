---
description: Best practice per la mappatura degli stadi - [!DNL Marketo Measure]
title: Best practice per la mappatura degli staging
exl-id: 1ed380a1-4a3a-4761-b70f-cdf2e290329d
feature: Tracking, Custom Models
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Best practice per la mappatura degli staging {#best-practices-for-stage-mapping}

## Panoramica {#overview}

La sezione Mappatura fase del [!DNL Marketo Measure] conto delinea le fasi che [!DNL Marketo Measure] estrae automaticamente dal CRM ed eventuali stadi personalizzati definiti se utilizzi il modello di attribuzione personalizzato. La validità del tuo [!DNL Marketo Measure] i dati si basano sul fatto che queste fasi vengano ordinate correttamente in modo che [!DNL Marketo Measure] è in grado di comprendere con precisione il funnel e la progressione dei record in tutto il funnel.

Nella sezione Mappatura area di visualizzazione della [!DNL Marketo Measure] dell’istanza, visualizzerai le fasi attiva e inattiva dal tuo sistema CRM. Ordina tutte le fasi al meglio delle tue capacità in base a come è oggi il funnel.

Un’ulteriore funzione gestita in questa sezione è Stadi funnel, che consente di aggiungere stadi al funnel senza applicare l’attribuzione. Gli stadi funnel verranno tracciati come punti di contatto e popolati nel campo Posizioni punto di contatto nel CRM. Questi stadi funnel saranno anche rappresentati in varie bacheche di percorso in [!DNL Marketo Measure] Scopri.

## Best practice {#best-practices}

Sia che stiate valutando la mappatura dello staging per la prima volta o semplicemente rivedendo l&#39;ordine del funnel, è importante tenere a mente le seguenti best practice.

* L&#39;ordine è tutto!
   * Considerazione [!DNL Marketo Measure] richiama dal CRM le fasi sia attive che inattive; verifica che tutte le fasi che potrebbero essere utilizzate su un lead/contatto o un’opportunità siano raggruppate e ordinate di conseguenza
* Quando definisci una fase personalizzata, assicurati che il tracciamento della cronologia dei campi sia abilitato per tutti i campi utilizzati per definire la fase
* Non utilizzare un campo formula per definire una fase personalizzata
   * Un campo booleano è la best practice consigliata
* La sezione Fase lead o fase contatto è divisa in Perso, Aperto e Convertito; verificare che le fasi siano nella sezione relativa alla fase appropriata
   * Se una fase si trova nella sezione di fase errata, è possibile che si verifichino errori [!DNL Marketo Measure] dati
   * Se si è un cliente di Marketo Measure Ultimate e si è impostato l&#39;oggetto dashboard predefinito come contatto, non utilizzare i due campi seguenti specifici per lead ([ulteriori informazioni](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).
      * b2b.personStatus
      * b2b.isConverted
* La sezione relativa alla fase Opportunità è divisa in Persa, Aperta e Vinta; verificare che le fasi si trovino nella sezione corrispondente
   * Se una fase si trova nella sezione di fase errata, è possibile che si verifichino errori [!DNL Marketo Measure] dati sui ricavi o sulla pipeline
* Evita di usare nomi di fase duplicati (il nostro sistema li rileverà e ne rimuoverà automaticamente uno).
* Per impostare una regola che verifichi la presenza di valori NULL, lasciare vuota la casella di testo del valore.

## Best practice per la manutenzione {#best-practices-for-maintenance}

Rivedere la mappatura dello staging una volta all’anno assicurerà che i dati dell’opportunità in [!DNL Marketo Measure] è accurato e aggiornato.

Altri motivi che potrebbero attivare una revisione della mappatura dello staging includono...

* Fatturato del team marketing
* Eventuali modifiche alle fasi del CRM
* Aggiornamenti al funnel della tua organizzazione
* Visualizzazione dei dati errati dei ricavi nel tuo [!DNL Marketo Measure] reportistica

>[!MORELIKETHIS]
>
>[La differenza tra gli stadi funnel e gli stadi del modello personalizzato](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md#the-difference-between-funnel-stages-and-custom-model-stages)
