---
description: '''[!DNL Marketo Measure] Panoramica finale - [!DNL Marketo Measure] - Documentazione del prodotto"'
title: '''[!DNL Marketo Measure] Panoramica finale"'
hide: true
hidefromtoc: true
exl-id: fada9479-0671-4698-8043-c67d7977577b
source-git-commit: 604db0227cc48e09743db317cc72488755586a48
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# [!DNL Marketo Measure] Panoramica finale {#marketo-measure-ultimate-overview}

[!DNL Marketo Measure] (precedentemente Bizible) offre agli esperti di marketing informazioni sulle attività di marketing più efficaci per incrementare le entrate e massimizzare il ritorno sull’investimento per la loro azienda. [!DNL Marketo Measure] è una soluzione di attribuzione marketing che tiene traccia e crea rapporti automatici sulle prestazioni dei canali, fornendo la visibilità in cui i canali determinano il coinvolgimento del cliente più elevato e consentendo di ottimizzare di conseguenza le spese di marketing.

[!DNL Marketo Measure Ultimate] contiene le funzionalità aggiuntive:

* Acquisisci da quasi tutte le origini dati e da più origini dati dello stesso tipo per inserire tutti i dati per l’attribuzione.
   * Utilizza con quasi qualsiasi CRM, non solo Salesforce e Dynamics.
   * Connettere più istanze CRM e/o istanze MAP a una [!DNL Marketo Measure] istanza.
   * Inserire dati di registrazione e partecipazione dei webinar di terze parti.

* Trasforma i tuoi dati con grande flessibilità attraverso le funzionalità di mappatura dei campi e trasformazione per garantire la giusta forma dei dati.

* Rendi disponibili le informazioni di attribuzione alle applicazioni esterne tramite il data warehouse incluso per integrare le informazioni nel flusso di lavoro. Dati di risultati più granulari e rapporti basati su BI, inclusa la Data Warehouse di Snowflake, che fornisce l’accesso ai dati dei risultati granulari e la possibilità di utilizzare qualsiasi strumento BI per l’analisi e il reporting.

* Integrazione con RTCDP (B2B o B2P Edition), fornendo una soluzione di attribuzione B2B integrata per i clienti RTCDP come RTCDP e [!DNL Marketo Measure] entrambi funzionano a partire da dati Adobe Experience Platform centralizzati (AEP).

**Livelli Marketo Measure 1-3**

![](assets/marketo-measure-ultimate-overview-1.png)

**Marketo Measure Ultimate**

![](assets/marketo-measure-ultimate-overview-2.png)

## Novità di [!DNL Marketo Measure Ultimate] {#whats-new-in-marketo-measure-ultimate}

**TITOLO INTESTAZIONE - Importare dati B2B tramite AEP**

Gli addetti al marketing devono portare i loro dati B2B (ad esempio account, opportunità, contatto, lead, campagna, membro della campagna, attività) tramite AEP. Le connessioni dirette CRM e al Marketo Engage non sono più disponibili per Ultimate. Gli addetti al marketing continueranno a fornire dati ad Platform tramite connessioni dirette e tracciando attività web tramite [!DNL Marketo Measure] javascript.

![](assets/marketo-measure-ultimate-overview-3.png)

**TITOLO INTESTAZIONE - Impostazione valuta predefinita**

BREVE INTRO???

![](assets/marketo-measure-ultimate-overview-4.png)

**TITOLO HEADER - Sandbox Marketo Measure Ultimate**

[!DNL Marketo Measure Ultimate] L&#39;istanza deve essere mappata su una sandbox AEP prima di creare la [!DNL Marketo Measure] flussi di dati di destinazione in AEP.

>[!NOTE]
>
>A [!DNL Marketo Measure Ultimate] l&#39;istanza di produzione deve essere mappata su una sandbox di produzione AEP, una [!DNL Marketo Measure Ultimate] l’istanza di sviluppatori deve essere mappata su una sandbox per sviluppatori AEP.

Una volta salvata la selezione della mappatura sandbox, non è possibile modificarla nell’applicazione in questo momento. Per modificarlo, contatta [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

I dati di una determinata entità (ad esempio, Account) provenienti da una determinata origine dati possono essere inseriti in un solo set di dati. Ogni set di dati può essere incluso in un solo flusso di dati. Le violazioni interromperanno il flusso di dati in fase di esecuzione.

![](assets/marketo-measure-ultimate-overview-5.png)

**TITOLO INTESTAZIONE - Mappatura fase**

Tutto [!DNL Marketo Measure Ultimate] le regole sono specifiche per i set di dati. È necessario creare regole di mappatura stage per tutti i set di dati e per tutte le fasi selezionate.

Sono disponibili sei fasi integrate:

* Piombo perso
* Lead aperti
* Piombo convertito
* Opportunità perduta
* Apertura opportunità
* Opportunità conquistata

Le sezioni Perduto, Vinto e Convertito non consentono stadi personalizzati. I dati di origine possono tuttavia essere mappati alle fasi incorporate Lost/Won/Converted aggiornando la regola di mappatura.

Gli stadi personalizzati possono essere definiti solo per le sezioni aperte.
Non includiamo più automaticamente le fasi CRM nella mappatura dello stadio.

È necessario mappare quattro fasi integrate con le regole (le regole di mappatura per gli altri due, Lead Lost e Lead Convertito, sono facoltative):

* Lead aperti
* Opportunità perduta
* Apertura opportunità
* Opportunità conquistata

Le condizioni delle regole sono specifiche per i set di dati. Le regole di mappatura della fase devono essere create per tutti i set di dati e tutte le fasi, ad eccezione dei lead persi e lead convertiti.

Nessuna selezione per funnel vs boomerang vs modello personalizzato. Tutti gli stadi sono selezionati per imbuto, boomerang e modello personalizzato. C&#39;è un limite del numero di fasi supportate: 15 fasi personalizzate più 6 fasi integrate.

![](assets/marketo-measure-ultimate-overview-6.png)

Le regole dei punti di contatto per i membri della campagna e i punti di contatto per le attività sono specifiche per i set di dati.

![](assets/marketo-measure-ultimate-overview-7.png)

![](assets/marketo-measure-ultimate-overview-8.png)

I punti di contatto di attribuzione non sono scritti in CRM perché Ultimate non dispone di una connessione CRM diretta.

[!DNL Marketo Measure] I servizi ABM ML (Lead-to-Account Matching and Predictive Engagement Score) non sono disponibili per [!DNL Marketo Measure Ultimate]. Puoi trovare tali servizi gratuitamente nell’edizione RT-CDP B2B.

## Limitazioni {#limitations}

* Al momento sono disponibili campi limitati per le regole di trasformazione dei dati.
* Non esiste un percorso di migrazione per gli utenti di livello 1/2/3 esistenti. Richiede una nuova implementazione, ma aiuteremo a migrare i dati dell’attività web tracciati dall’istanza esistente.

>[!MORELIKETHIS]
>
>[Connessione destinazione](/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/set-up-marketo-connection.md){target="_blank"}
