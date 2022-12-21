---
description: Best practice per l’attribuzione delle attività - [!DNL Marketo Measure] - Documentazione del prodotto
title: Best practice per l’attribuzione delle attività
exl-id: 66fb9f47-3912-40a6-b112-3efca789f321
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Best practice per l’attribuzione delle attività {#best-practices-for-activities-attribution}

## Panoramica {#overview}

La [!DNL Marketo Measure] La funzione Attribuzione attività consente ai clienti di creare punti di contatto dai record di attività nel CRM. Questo metodo di creazione dei punti di contatto è flessibile e consente di creare regole basate sui campi Attività o Evento per informare [!DNL Marketo Measure] quale attività registra deve produrre punti di contatto da e successivamente ricevere il credito di attribuzione.

Il caso d’uso più comune per questa funzione è quello di creare regole che incorporano le interazioni di vendita nei dati dei punti di contatto dell’acquirente. Attribuzione attività consente di allineare i dati di vendita e marketing in un unico percorso.

Per molti [!DNL Salesforce] Le istanze, l&#39;oggetto Attività può contenere diversi tipi di record, pertanto è importante che le regole dell&#39;attività siano specifiche e personalizzate in base ai record che si sta tentando di tradurre in punti di contatto. Le seguenti best practice sono utili per creare punti di contatto significativi e importanti tramite l’attribuzione Attività .

## Best practice {#best-practice}

Sia che tu stia definendo le regole di attività per la prima volta o che stia solo rivedendo le regole di attività precedentemente configurate, ricorda le seguenti best practice.

* Inizia semplice
   * Identifica alcuni tipi chiave di attività che desideri incorporare nel tuo [!DNL Marketo Measure] dati, quindi aggiungi altri tipi man mano che ti senti a tuo agio con come vengono attribuiti questi punti di contatto
   * Come accennato, il caso d’uso principale di questa funzione è quello di creare punti di contatto che monitorino l’efficacia del team di sviluppo delle vendite, in particolare le chiamate telefoniche in uscita e le e-mail in uscita

>[!NOTE]
>
>È **NOT** Si consiglia di tenere traccia delle attività di vendita che si verificano dopo la creazione dell&#39;opportunità, in quanto il tracciamento di un processo dei responsabili vendite non offrirà molte informazioni. L&#39;obiettivo è tracciare l&#39;influenza delle vendite insieme all&#39;influenza del marketing, principalmente nello sviluppo di una nuova generazione di opportunità/pipeline

* Non utilizzare i campi formula per definire le regole
* Creare regole specifiche e precise
   * Desideri che la soglia per la creazione di un punto di contatto attività sia la stessa (o simile) di un modulo di compilazione o di un&#39;iscrizione a una campagna, ovvero (Risposte a un&#39;e-mail in uscita o conversazioni telefoniche completate)
* Convalida sempre nuove regole in [!DNL Salesforce] prima del salvataggio e dell&#39;elaborazione
   * La replica delle regole di attività in un tipo di rapporto &quot;Attività ed eventi&quot; ti fornirà una chiara comprensione di quanti punti di contatto verranno creati da tale regola
* Collabora con il tuo team di Sales Opp
   * Il coinvolgimento del team che lavora più vicino ai record di attività o allo strumento di abilitazione delle vendite garantirà l&#39;utilizzo dei campi corretti per definire le regole

## Best practice per la manutenzione {#best-practice-for-maintenance}

Rivedere le regole di attribuzione attività almeno due volte all’anno garantirà che i punti di contatto attività siano precisi e aggiornati. Assicurati che queste regole non creino punti di contatto indesiderati che diluiscono i dati di Attribuzione dell’acquirente. Una revisione della definizione delle regole aiuterà te e il tuo team a sentirti sicuro nella tua Attribuzione attività e nel suo ruolo nel tuo [!DNL Marketo Measure] dati.

Altri motivi per cui potrebbe innescare una revisione delle regole di attività includono..

* Fatturato del team di marketing
* Modifiche ai campi utilizzati per definire i record dell’attività
* Modifiche o aggiornamenti ai tuoi strumenti di abilitazione alle vendite

>[!MORELIKETHIS]
>
>* [Attribuzione attività](/help/advanced-marketo-measure-features/activities-attribution/salesforce-activities-attribution.md)
>* [Domande frequenti sull’attribuzione delle attività di vendita](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)


