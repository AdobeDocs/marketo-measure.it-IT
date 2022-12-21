---
description: Tecniche consigliate per la mappatura dello stage - [!DNL Marketo Measure] - Documentazione del prodotto
title: Tecniche consigliate per la mappatura dello stage
exl-id: 1ed380a1-4a3a-4761-b70f-cdf2e290329d
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Tecniche consigliate per la mappatura dello stage {#best-practices-for-stage-mapping}

## Panoramica {#overview}

La sezione Mappatura fase del [!DNL Marketo Measure] delinea le fasi che [!DNL Marketo Measure] richiama automaticamente dal CRM e da qualsiasi fase personalizzata definita se si utilizza il modello di attribuzione personalizzato. La validità del tuo [!DNL Marketo Measure] i dati si basano sul fatto che queste fasi siano state ordinate correttamente in modo che [!DNL Marketo Measure] può capire accuratamente il tuo imbuto e la progressione dei record in tutto detto imbuto.

Nella sezione Mappatura fase della [!DNL Marketo Measure] ad esempio, vedrai sia gli stadi attivi che quelli inattivi dal tuo CRM. Ordinate tutte le fasi al meglio delle vostre capacità in allineamento con come il vostro funnel è oggi.

Un’ulteriore funzione gestita in questa sezione è Funnel Stages, che consente di aggiungere aree di visualizzazione al funnel senza applicare l’attribuzione. Gli stadi funnel verranno tracciati come punti di contatto e verranno compilati nel campo Posizioni dei punti di contatto nel CRM. Questi stadi funnel saranno rappresentati anche all&#39;interno di varie schede di percorso in [!DNL Marketo Measure] Scoprite.

## Best practice {#best-practices}

Sia che stiate valutando la Mappatura fase per la prima volta o semplicemente rivedendo l’ordine funnel, è importante tenere a mente le seguenti best practice.

* L&#39;ordine è tutto!
   * Considerazione [!DNL Marketo Measure] estrae sia le fasi attive che inattive dal CRM, conferma che qualsiasi fase che può essere utilizzata su un lead/contatto o opportunità sono raggruppate e ordinate di conseguenza
* Quando definisci un’area di visualizzazione personalizzata, assicurati che il tracciamento della cronologia dei campi sia abilitato per qualsiasi campo utilizzato per definire l’area di visualizzazione
* Non utilizzare un campo formula per definire uno stadio personalizzato
   * Un campo booleano è una raccomandazione di best practice
* Nota che la sezione della fase Lead o Contatto è divisa in Lost, Open e Convertito; verificare che le fasi si trovino nella sezione della fase appropriata
   * Avere una fase nella sezione della fase errata può causare un errore molto grave [!DNL Marketo Measure] dati
* La sezione della fase Opportunità è divisa in Perdita, Apri e Vinto; verificare che le fasi si trovino nella sezione della fase appropriata
   * Avere una fase nella sezione della fase errata può causare un errore molto grave [!DNL Marketo Measure] dati sulle entrate o sulle entrate della pipeline
* Evita di usare nomi di fase duplicati (il nostro sistema li rileverà e ne rimuoverà automaticamente uno).

## Tecniche consigliate per la manutenzione {#best-practices-for-maintenance}

Esaminare la mappatura della fase una volta all’anno garantirà che i dati relativi alle opportunità in [!DNL Marketo Measure] è accurato e aggiornato.

Altri motivi per cui potrebbe essere attivata una revisione di Stage Mapping sono...

* Fatturato del team di marketing
* Qualsiasi modifica alle tue fasi CRM
* Aggiornamenti al funnel della tua organizzazione
* Visualizzazione di dati di ricavi errati nel [!DNL Marketo Measure] reporting

>[!MORELIKETHIS]
>
>[Differenza tra le fasi funnel e le fasi del modello personalizzato](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md#the-difference-between-funnel-stages-and-custom-model-stages)
