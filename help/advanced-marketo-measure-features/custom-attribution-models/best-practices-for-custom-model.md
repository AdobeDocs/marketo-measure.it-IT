---
description: Best practice per modelli personalizzati - [!DNL Marketo Measure] - Documentazione del prodotto
title: Best practice per modelli personalizzati
exl-id: 7c19bb6a-30fc-4cbd-a58e-f20751102afe
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 0%

---

# Best practice per modelli personalizzati {#best-practices-for-custom-model}

## Panoramica {#overview}

Oltre al [!DNL Marketo Measure] i modelli di attribuzione predefiniti, i clienti di livello 2 e versioni successive hanno accesso a un modello di attribuzione personalizzato.

La [!DNL Marketo Measure] Il modello Attribution personalizzato consente agli utenti di scegliere le posizioni dei punti di contatto cardine e/o le fasi personalizzate da includere nel modello. Inoltre, gli utenti possono controllare la percentuale di credito attribuita a ogni fase all’interno del modello (gli utenti possono definire fino a 6 fasi personalizzate aggiuntive), oppure possono utilizzare i valori percentuali di attribuzione suggeriti dal [!DNL Marketo Measure] Modello di apprendimento automatico.

Esistono due aspetti chiave del modello di attribuzione personalizzato:

**Stadi personalizzati** consentire agli utenti di definire il proprio funnel in relazione alla propria attività e ai propri processi. Le fasi personalizzate dovrebbero rappresentare &quot;pietre miliari&quot; in tutto il percorso dell&#39;acquirente molto simile al [!DNL Marketo Measure] Le tappe (Primo contatto, Contatto per la creazione di lead, Contatto per la creazione di opportunità e Touch chiuso) vengono eseguite all’interno dei modelli di attribuzione delle azioni. È fondamentale che le fasi personalizzate siano definite e mappate correttamente all’interno dell’account per garantire che [!DNL Marketo Measure] è in grado di monitorare correttamente le transizioni di fase. In questo modo si identificano i punti di contatto da associare a ciascuna fase e si attribuisce il credito in modo appropriato. La mappatura della fase personalizzata è essenzialmente un&#39;estensione della &quot;Mappatura della fase&quot; standard e deve seguire le stesse procedure.

>[!NOTE]
>
>Per ulteriori informazioni, consulta la risorsa Best practice per la mappatura della fase .

**Modellazione dell’attribuzione personalizzata** viene definito una volta selezionato il funnel Stages personalizzati . Gli utenti possono quindi controllare la quantità di credito di attribuzione da assegnare a ogni fase personalizzata e alla [!DNL Marketo Measure] tappe fondamentali. Gli utenti possono assegnare credito a ogni fase come ritengono opportuno, oppure fare riferimento al [!DNL Marketo Measure] Modello di apprendimento automatico che agisce come un &quot;modello suggestivo&quot; basato su dati storici.

È fondamentale che questi due aspetti del modello personalizzato siano definiti correttamente e precisamente per garantire che [!DNL Marketo Measure] sta producendo un modello di attribuzione personalizzato accurato.

## Best practice {#best-practice}

Sia che si stia configurando il modello personalizzato per la prima volta, sia che si riveda ciò che è stato precedentemente stabilito, è importante tenere a mente le seguenti best practice.

* Inizia semplice
   * Identificare le fasi chiave che si desidera aggiungere al modello personalizzato che sono cruciali per il [!DNL Marketo Measure] rapporti. In genere si tratta di fasi alle quali si è comunemente misurati o che si intende ottenere informazioni
   * È sempre possibile aggiungere al modello personalizzato nel tempo
* Utilizzare [!DNL Marketo Measure] Modello di apprendimento automatico
   * Se ti stai impegnando a decidere l’abbandono della percentuale di attribuzione, l’ [!DNL Marketo Measure] Il modello di apprendimento automatico può aiutarti a prendere decisioni informate quando imposti un modello di attribuzione personalizzato.
   * Quando visualizzi il modello di apprendimento automatico, le percentuali di attribuzione di ogni fase riflettono il potenziale impatto delle attività di marketing
      * Una percentuale più elevata significa che il marketing può influenzare direttamente lo spostamento dell&#39;imbuto in quel momento
      * Una percentuale di attribuzione inferiore indica che le aree di visualizzazione sono meno importanti per il monitoraggio da parte del team
* È necessario definire le fasi principali dell&#39;imbuto in base agli stadi Lead o Contatto, non in entrambi
   * Questo significa che è necessario assicurarsi che tutte le persone passino attraverso quel passaggio sull&#39;oggetto relativo
      * Ad esempio: Se si definisce lo stadio MQL dall’oggetto Lead, tutte le persone devono accedere al sistema come lead e essere contrassegnate come MQL nel record Lead per [!DNL Marketo Measure] per riflettere con precisione quale contatto era correlato alla transizione del lead a MQL. In caso contrario, e alcune persone passano a Contatto prima di diventare MQL come lead, [!DNL Marketo Measure] non sarà in grado di tenere conto con precisione di questo nei tuoi dati di Touchpoint e dovremo presumere che la persona abbia già MQL&#39;d. [!DNL Marketo Measure] non può rendere conto della salita di palcoscenico, quindi dedurremo che le fasi sono state passate anche se non lo hanno fatto.
* Assicurati che il tracciamento della cronologia dei campi sia abilitato per tutti i campi utilizzati per definire le fasi personalizzate incorporate
* Non utilizzare campi formula per definire uno stadio personalizzato
   * Un campo booleano è una raccomandazione sulle best practice
* Non incorporare gli stadi personalizzati nel modello personalizzato che coincidono con un [!DNL Marketo Measure] Posizione punto di contatto Milestone (FT, LC, OC, Won/Lost chiuso)
   * In tal caso, queste posizioni si verificheranno sempre simultaneamente e possono causare un credito di attribuzione gonfiato a parti del funnel.
* Collabora con il tuo team di Sales Opp
   * L&#39;inserimento nel team che lavora più vicino alle aree di visualizzazione e al loro significato garantirà l&#39;utilizzo delle aree di visualizzazione corrette e la corretta definizione delle aree di visualizzazione

## Best practice per la manutenzione {#best-practice-for-maintenance}

La revisione del modello personalizzato almeno due volte all’anno garantirà che il rapporto di attribuzione personalizzato sia accurato e affidabile.

Se il modello personalizzato utilizza il modello di apprendimento automatico, è necessario esaminarne l’applicazione all’interno del modello personalizzato trimestralmente per verificare che il modello personalizzato sia il più aggiornato possibile.

Altri motivi per cui potrebbe innescare una revisione del modello personalizzato includono..

* Fatturato del team di marketing
* Qualsiasi modifica alle tue fasi CRM
* Aggiornamenti al funnel delle organizzazioni
* Visualizzazione di dati di ricavo inesatti nel [!DNL Marketo Measure] reporting durante l&#39;applicazione del modello personalizzato
* Visualizzazione di posizioni di punti di contatto popolate che non sono più rilevanti per il funnel delle organizzazioni

>[!MORELIKETHIS]
>
>* [Modello di attribuzione e configurazione personalizzati](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md)
>* [Abilita tracciamento cronologia campi per modello personalizzato](/help/advanced-marketo-measure-features/custom-attribution-models/custom-model-setup-enable-field-history-tracking.md)
>* [Modello di apprendimento automatico](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md)

