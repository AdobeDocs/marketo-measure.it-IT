---
description: Best practice per il modello personalizzato - [!DNL Marketo Measure]
title: Best practice per il modello personalizzato
exl-id: 7c19bb6a-30fc-4cbd-a58e-f20751102afe
feature: Custom Models
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 0%

---

# Best practice per il modello personalizzato {#best-practices-for-custom-model}

## Panoramica {#overview}

Oltre al [!DNL Marketo Measure] I modelli di attribuzione predefiniti, i clienti di livello 2 e superiore hanno accesso a un modello di attribuzione personalizzato.

Il [!DNL Marketo Measure] Il modello di attribuzione personalizzato consente agli utenti di scegliere quali posizioni dei punti di contatto di milestone e/o stadi personalizzati includere nel modello. Inoltre, gli utenti possono controllare la percentuale di credito attribuita a ogni fase all’interno del modello (gli utenti possono definire fino a 6 fasi personalizzate aggiuntive), oppure possono utilizzare i valori percentuali di attribuzione suggeriti da [!DNL Marketo Measure] Modello di apprendimento automatico.

Esistono due aspetti chiave del modello di attribuzione personalizzato:

**Fasi personalizzate** consente agli utenti di definire il funnel in relazione alla propria attività e ai propri processi. Le fasi personalizzate devono rappresentare &quot;milestone&quot; in tutto il percorso dell&#39;acquirente, proprio come [!DNL Marketo Measure] Le attività cardine (Primo contatto, Tocco creazione lead, Tocco creazione opportunità e Tocco vincente chiuso) rientrano nei modelli di attribuzione Stock. È fondamentale che le fasi personalizzate siano definite e mappate correttamente all’interno del tuo account per garantire che [!DNL Marketo Measure] tiene traccia in modo corretto delle transizioni di fase. Questo consente di identificare quali punti di contatto devono essere associati a ciascuna fase e attribuire il credito in modo appropriato. La mappatura personalizzata dello staging è essenzialmente un’estensione della mappatura standard dello staging e deve seguire le stesse procedure.

>[!NOTE]
>
>Fai riferimento alla risorsa Best practice per la mappatura degli stadi per ulteriori dettagli

**Modellazione di attribuzione personalizzata** è definito dopo aver selezionato il funnel Stadi personalizzati. Gli utenti possono quindi controllare la quantità di credito di attribuzione da assegnare a ogni fase personalizzata e al [!DNL Marketo Measure] fasi cardine. Gli utenti possono assegnare il credito a ogni fase come ritengono opportuno o fare riferimento al [!DNL Marketo Measure] Modello di apprendimento automatico che funge da &quot;modello suggestivo&quot; basato su dati storici.

È fondamentale che questi due aspetti del modello personalizzato siano definiti in modo corretto e preciso per garantire che [!DNL Marketo Measure] sta producendo un accurato modello di attribuzione personalizzato.

## Best practice {#best-practice}

Sia che si configuri il modello personalizzato per la prima volta, sia che si riveda ciò che è stato stabilito in precedenza, è importante tenere a mente le seguenti best practice.

* Inizia semplice
   * Identifica le fasi chiave da aggiungere al modello personalizzato che sono fondamentali per [!DNL Marketo Measure] reportistica. In genere si tratta di stadi rispetto ai quali si effettuano misurazioni frequenti o sui quali si intende ottenere informazioni approfondite
   * Puoi sempre aggiungere al modello personalizzato nel tempo
* Utilizzare [!DNL Marketo Measure] Modello di apprendimento automatico
   * Se hai difficoltà a decidere la percentuale di attribuzione breakout, il [!DNL Marketo Measure] Il modello di apprendimento automatico può aiutarti a prendere decisioni informate quando imposti il modello di attribuzione personalizzato.
   * Quando si visualizza il modello di apprendimento automatico, le percentuali di attribuzione di ogni fase riflettono il potenziale impatto delle attività di marketing
      * Una percentuale più alta significa che il marketing può influenzare direttamente il movimento dell’imbuto in quel momento
      * Una percentuale di attribuzione più bassa indica che le fasi sono meno importanti per il monitoraggio del team
* È necessario definire la parte superiore delle fasi funnel in base alle fasi lead o contatto, non in entrambe
   * Ciò significa che è necessario assicurarsi che tutte le persone passino attraverso quella fase sull&#39;oggetto relativo
      * Ad esempio: se definisci la fase MQL dall’oggetto Lead, tutte le persone devono entrare nel sistema come Lead ed essere contrassegnate come MQL sul proprio record Lead per [!DNL Marketo Measure] per riflettere con precisione quale contatto era correlato alla transizione del lead a MQL. In caso contrario, e alcuni utenti passeranno al contatto prima di diventare MQL come lead, [!DNL Marketo Measure] non sarà in grado di tenere conto accuratamente di questo nei tuoi dati dei punti di contatto e dovremo presumere che la persona abbia già MQL’d. [!DNL Marketo Measure] non può tenere conto del salto di fase, quindi dedurremo che le fasi sono state passate anche se non lo sono state.
* Assicurati che il tracciamento della cronologia dei campi sia abilitato per tutti i campi utilizzati per definire le fasi personalizzate che incorpori
* Non utilizzare campi formula per definire una fase personalizzata
   * Un campo booleano è una best practice consigliata
* Non incorporare gli stadi personalizzati nel modello personalizzato che coincidono con un [!DNL Marketo Measure] Posizione punto di contatto milestone (FT, LC, OC, Closed Won/Lost)
   * In tal caso, queste posizioni si verificano sempre simultaneamente e possono causare un aumento del credito di attribuzione a parti del funnel.
* Lavora con il tuo team Sales Opp
   * L’intervento del team che lavora più da vicino con gli stadi e il loro significato garantiscono l’utilizzo degli stadi corretti e la loro corretta definizione

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

La revisione del modello personalizzato almeno due volte all’anno garantirà che i rapporti di attribuzione personalizzati siano precisi e affidabili.

Se il modello personalizzato utilizza il modello di apprendimento automatico, è necessario esaminarne l’applicazione trimestralmente all’interno del modello personalizzato per assicurarsi che il modello personalizzato sia il più aggiornato possibile.

Altri motivi per cui potrebbe essere attivata una revisione del modello personalizzato sono...

* Fatturato del team marketing
* Eventuali modifiche alle fasi del CRM
* Aggiornamenti al funnel delle organizzazioni
* Visualizzazione di dati imprecisi sui ricavi nelle tue [!DNL Marketo Measure] generazione di rapporti durante l’applicazione del modello personalizzato
* Visualizzazione di posizioni dei punti di contatto popolate che non sono più rilevanti per il funnel delle organizzazioni

>[!MORELIKETHIS]
>
>* [Modello di attribuzione e configurazione personalizzati](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md)
>* [Abilita Tracciamento Cronologia Campi Per Modello Personalizzato](/help/advanced-marketo-measure-features/custom-attribution-models/custom-model-setup-enable-field-history-tracking.md)
>* [Modello di apprendimento automatico](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md)
