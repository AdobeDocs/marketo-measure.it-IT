---
description: Linee guida sulle best practice per l’attribuzione delle attività per gli utenti di Marketo Measure
title: Attribuzione delle best practice per le attività
exl-id: 66fb9f47-3912-40a6-b112-3efca789f321
feature: Attribution
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# Attribuzione delle best practice per le attività {#best-practices-for-activities-attribution}

## Panoramica {#overview}

La funzione Attribuzione attività di [!DNL Marketo Measure] consente ai clienti di creare punti di contatto dai record Attività nel CRM. Questo metodo di creazione dei punti di contatto è flessibile. Ti consente di creare regole basate sui campi &quot;Attività&quot; o &quot;Evento&quot; per informare [!DNL Marketo Measure] da quali record di attività deve produrre punti di contatto e quindi ricevere il merito di attribuzione.

Il caso d’uso più comune per questa funzione è quello di creare regole che incorporano le interazioni di vendita nei dati dei punti di contatto dell’acquirente. Attribuzione attività consente di allineare i dati di vendita e marketing in un unico percorso.

Per molte istanze di [!DNL Salesforce], l&#39;oggetto Attività può ospitare vari tipi di record, pertanto è importante che le regole di attività siano specifiche e personalizzate in base ai record che si sta tentando di tradurre in punti di contatto. Le seguenti best practice consentono di creare punti di contatto significativi e preziosi tramite l’attribuzione Attività.

## Best practice {#best-practice}

Se definisci le regole di attività per la prima volta o esamini solo le regole di attività impostate in precedenza, tieni presente le seguenti best practice.

* Inizia semplice
   * Identifica alcuni tipi chiave di attività da incorporare nei dati di [!DNL Marketo Measure], quindi aggiungi altri tipi man mano che ti senti a tuo agio con l&#39;attribuzione di questi punti di contatto
   * Come accennato, il caso d’uso principale di questa funzione consiste nel creare punti di contatto che tracciano l’efficacia del team di sviluppo delle vendite, in particolare chiamate telefoniche in uscita e e-mail in uscita.

>[!NOTE]
>
>Si consiglia di **NON** tenere traccia delle attività di vendita che si verificano dopo la creazione dell&#39;opportunità, in quanto il monitoraggio di un processo dei responsabili vendite non offre molto insight. L’obiettivo è monitorare l’influenza delle vendite insieme all’influenza del marketing, principalmente nello sviluppo di una nuova generazione di opportunità/pipeline

* Non utilizzare i campi formula per definire le regole
* Creare regole specifiche e precise
   * La soglia per la creazione di un punto di contatto Attività deve essere la stessa (o simile) di una compilazione di moduli o di un’iscrizione alla campagna: Risposte a un’e-mail in uscita o Conversazioni telefoniche completate
* Convalida sempre nuove regole in [!DNL Salesforce] prima di salvare ed elaborare
   * La replica delle regole di attività in un tipo di rapporto &quot;Attività ed eventi&quot; consente di comprendere chiaramente quanti punti di contatto provengono dalla regola
* Lavora con il tuo team Sales Opp
   * L’intervento del team più vicino ai tuoi record di attività o allo strumento di abilitazione delle vendite ti garantirà l’utilizzo dei campi corretti per definire le tue regole

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

Rivedere le regole di attribuzione dell’attività almeno due volte all’anno assicura che i punti di contatto dell’attività siano precisi e aggiornati. Desideri accertarti che queste regole non creino punti di contatto indesiderati che stanno diluendo i dati di Attribution dell’acquirente. La revisione della definizione delle regole aiuterà te e il tuo team a sentirsi sicuri dell&#39;attribuzione delle attività e del suo ruolo nei dati di [!DNL Marketo Measure].

Altri motivi per cui potrebbe attivare una revisione delle regole di attività sono...

* Fatturato del team marketing
* Modifiche ai campi utilizzati per definire i record di attività
* Modifiche o aggiornamenti agli strumenti di supporto alle vendite

>[!MORELIKETHIS]
>
>* Attribuzione [Attività](/help/channel-tracking-and-setup/salesforce-activities-attribution.md)
>* [Domande frequenti sull&#39;attribuzione delle attività di vendita](/help/channel-tracking-and-setup/activities-attribution-faq.md)
