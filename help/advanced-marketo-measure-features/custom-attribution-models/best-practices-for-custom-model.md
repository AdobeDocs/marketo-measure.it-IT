---
description: Best practice per il modello personalizzato - [!DNL Marketo Measure]
title: Best practice per il modello personalizzato
exl-id: 7c19bb6a-30fc-4cbd-a58e-f20751102afe
feature: Custom Models
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 0%

---

# Best practice per il modello personalizzato {#best-practices-for-custom-model}

## Panoramica {#overview}

Oltre a [!DNL Marketo Measure] modelli di attribuzione predefiniti, i clienti di livello 2 e versioni successive hanno accesso a un modello di attribuzione personalizzato.

Il modello di attribuzione personalizzata [!DNL Marketo Measure] consente agli utenti di scegliere quali posizioni dei punti di contatto di milestone e/o fasi personalizzate includere nel modello. Inoltre, gli utenti possono controllare la percentuale di credito attribuita a ogni fase all&#39;interno del modello (gli utenti possono definire fino a 6 fasi personalizzate aggiuntive), oppure possono utilizzare i valori percentuali di attribuzione suggeriti dal modello di apprendimento automatico [!DNL Marketo Measure].

Esistono due aspetti chiave del modello di attribuzione personalizzato:

**Le fasi personalizzate** consentono agli utenti di definire il proprio funnel in relazione alla propria attività e ai propri processi. Le fasi personalizzate devono rappresentare le &quot;milestone&quot; in tutto il percorso dell&#39;acquirente, in modo analogo alle [!DNL Marketo Measure] attività cardine (Primo contatto, Tocco per la creazione di lead, Tocco per la creazione di opportunità e Tocco vinto chiuso) eseguite all&#39;interno dei modelli di attribuzione delle azioni. È fondamentale che le fasi personalizzate siano definite e mappate correttamente nel tuo account per garantire che [!DNL Marketo Measure] tenga traccia correttamente delle transizioni delle fasi. Questo consente di identificare quali punti di contatto devono essere associati a ciascuna fase e attribuire il credito in modo appropriato. La mappatura personalizzata dello staging è essenzialmente un’estensione della mappatura standard dello staging e deve seguire le stesse procedure.

>[!NOTE]
>
>Fai riferimento alla risorsa Best practice per la mappatura degli stadi per ulteriori dettagli

**La modellazione di attribuzione personalizzata** viene definita dopo aver selezionato il funnel Stadi personalizzati. Gli utenti possono quindi controllare la quantità di credito di attribuzione da assegnare a ogni fase personalizzata e alle fasi cardine [!DNL Marketo Measure]. Gli utenti possono assegnare il credito a ogni fase in base alle proprie esigenze oppure fare riferimento al modello di apprendimento automatico [!DNL Marketo Measure] che funge da &quot;modello suggestivo&quot; in base ai dati storici.

È fondamentale che questi due aspetti del modello personalizzato siano definiti in modo corretto e preciso per garantire che [!DNL Marketo Measure] produca un modello di attribuzione personalizzato accurato.

## Best practice {#best-practice}

Sia che si configuri il modello personalizzato per la prima volta, sia che si riveda ciò che è stato stabilito in precedenza, è importante tenere a mente le seguenti best practice.

* Inizia semplice
   * Identifica le fasi chiave da aggiungere al modello personalizzato che sono fondamentali per il reporting di [!DNL Marketo Measure]. In genere si tratta di fasi rispetto alle quali si effettua una misurazione comune o sulle quali si intende ottenere insight
   * Puoi sempre aggiungere al modello personalizzato nel tempo
* Utilizza il modello di apprendimento automatico [!DNL Marketo Measure]
   * Se hai difficoltà a decidere la percentuale di suddivisione dell&#39;attribuzione, il modello di apprendimento automatico [!DNL Marketo Measure] può aiutarti a prendere decisioni informate durante l&#39;impostazione del modello di attribuzione personalizzato.
   * Quando si visualizza il modello di apprendimento automatico, le percentuali di attribuzione di ogni fase riflettono il potenziale impatto delle attività di marketing
      * Una percentuale più elevata indica che il marketing può influenzare direttamente lo spostamento del funnel a quel punto
      * Una percentuale di attribuzione più bassa indica che le fasi sono meno importanti per il monitoraggio del team
* È necessario definire la parte superiore delle fasi di funnel in base alle fasi Lead o Contatto, non in entrambe
   * Ciò significa che è necessario assicurarsi che tutte le persone passino attraverso quella fase sull&#39;oggetto relativo
      * Ad esempio: se definisci la fase MQL dall&#39;oggetto Lead, tutte le persone devono entrare nel sistema come Lead ed essere contrassegnate come MQL nel proprio record Lead affinché [!DNL Marketo Measure] rifletta con precisione quale contatto è stato correlato alla transizione del Lead a MQL. In caso contrario, e alcuni utenti passano al contatto prima di diventare MQL come lead, [!DNL Marketo Measure] non sarà in grado di tenere conto accuratamente di questo nei tuoi dati del punto di contatto e dovremo presumere che la persona abbia già MQL&#39;d. [!DNL Marketo Measure] non può tenere conto dell&#39;hopping di fase. Si dedurrà quindi che le fasi sono state passate anche se non lo sono state.
* Assicurati che il tracciamento della cronologia dei campi sia abilitato per tutti i campi utilizzati per definire le fasi personalizzate che incorpori
* Non utilizzare campi formula per definire una fase personalizzata
   * Un campo booleano è una best practice consigliata
* Non incorporare gli stadi personalizzati nel modello personalizzato che coincidono con una posizione del punto di contatto di Milestone [!DNL Marketo Measure] (FT, LC, OC, Closed Won/Lost)
   * In caso contrario, queste posizioni si verificano sempre simultaneamente e possono causare un credito di attribuzione gonfiato a parti del funnel.
* Lavora con il tuo team Sales Opp
   * L’intervento del team che lavora più da vicino con gli stadi e il loro significato garantiscono l’utilizzo degli stadi corretti e la loro corretta definizione

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

La revisione del modello personalizzato almeno due volte all’anno garantirà che i rapporti di attribuzione personalizzati siano precisi e affidabili.

Se il modello personalizzato utilizza il modello di apprendimento automatico, è necessario esaminarne l’applicazione trimestralmente all’interno del modello personalizzato per assicurarsi che il modello personalizzato sia il più aggiornato possibile.

Altri motivi per cui potrebbe essere attivata una revisione del modello personalizzato sono...

* Fatturato del team marketing
* Eventuali modifiche alle fasi del CRM
* Aggiornamenti a funnel delle organizzazioni
* Visualizzazione dei dati imprecisi sui ricavi nei rapporti di [!DNL Marketo Measure] durante l&#39;applicazione del modello personalizzato
* Visualizzazione di posizioni dei punti di contatto popolate che non sono più rilevanti per la funnel delle organizzazioni

>[!MORELIKETHIS]
>
>* [Modello di attribuzione personalizzato e installazione](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md)
>* [Abilita Tracciamento Cronologia Campi Per Modello Personalizzato](/help/advanced-marketo-measure-features/custom-attribution-models/custom-model-setup-enable-field-history-tracking.md)
>* [Modello di apprendimento automatico](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md)
