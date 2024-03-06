---
description: Attribuzione delle best practice per le attività - [!DNL Marketo Measure]
title: Attribuzione delle best practice per le attività
exl-id: 66fb9f47-3912-40a6-b112-3efca789f321
feature: Attribution
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Attribuzione delle best practice per le attività {#best-practices-for-activities-attribution}

## Panoramica {#overview}

Il [!DNL Marketo Measure] La funzione Attribuzione attività consente ai clienti di creare punti di contatto dai record Attività nel CRM. Questo metodo di creazione dei punti di contatto è flessibile. Ti consente di creare regole basate sui campi &quot;Attività&quot; o &quot;Evento&quot; per informare [!DNL Marketo Measure] da quali attività deve produrre punti di contatto e quindi ricevere il credito di attribuzione.

Il caso d’uso più comune per questa funzione è quello di creare regole che incorporano le interazioni di vendita nei dati dei punti di contatto dell’acquirente. Attribuzione attività consente di allineare i dati di vendita e marketing in un unico percorso.

Per molti [!DNL Salesforce] istanze, l’oggetto Attività può ospitare vari tipi di record, pertanto è importante che le regole di attività siano specifiche e personalizzate in base ai record che stai tentando di tradurre in punti di contatto. Le seguenti best practice consentono di creare punti di contatto significativi e preziosi tramite l’attribuzione Attività.

## Best practice {#best-practice}

Se definisci le regole di attività per la prima volta o esamini solo le regole di attività impostate in precedenza, tieni presente le seguenti best practice.

* Inizia semplice
   * Identifica alcuni tipi chiave di attività da incorporare nel tuo [!DNL Marketo Measure] , quindi aggiungi altri tipi man mano che acquisisci familiarità con l’attribuzione di questi punti di contatto
   * Come accennato, il caso d’uso principale di questa funzione consiste nel creare punti di contatto che tracciano l’efficacia del team di sviluppo delle vendite, in particolare chiamate telefoniche in uscita e e-mail in uscita.

>[!NOTE]
>
>È **NOT** si consiglia di tenere traccia delle attività di vendita che si verificano dopo la creazione dell’opportunità, in quanto il processo di tracciamento di un responsabile vendite non offre molte informazioni. L’obiettivo è monitorare l’influenza delle vendite insieme all’influenza del marketing, principalmente nello sviluppo di una nuova generazione di opportunità/pipeline

* Non utilizzare i campi formula per definire le regole
* Creare regole specifiche e precise
   * La soglia per la creazione di un punto di contatto Attività deve essere la stessa (o simile) di una compilazione di moduli o di un’iscrizione alla campagna: Risposte a un’e-mail in uscita o Conversazioni telefoniche completate
* Convalida sempre nuove regole in [!DNL Salesforce] prima del salvataggio e dell’elaborazione
   * La replica delle regole di attività in un tipo di rapporto &quot;Attività ed eventi&quot; consente di comprendere chiaramente quanti punti di contatto provengono dalla regola
* Lavora con il tuo team Sales Opp
   * L’intervento del team più vicino ai tuoi record di attività o allo strumento di abilitazione delle vendite ti garantirà l’utilizzo dei campi corretti per definire le tue regole

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

Rivedere le regole di attribuzione dell’attività almeno due volte all’anno assicura che i punti di contatto dell’attività siano precisi e aggiornati. Desideri accertarti che queste regole non creino punti di contatto indesiderati che stanno diluendo i dati di Attribution dell’acquirente. Una rassegna della definizione delle regole ti aiuterà e il tuo team avrà fiducia nell’Attribuzione delle attività e nel suo ruolo nel tuo [!DNL Marketo Measure] dati.

Altri motivi per cui potrebbe attivare una revisione delle regole di attività sono...

* Fatturato del team marketing
* Modifiche ai campi utilizzati per definire i record di attività
* Modifiche o aggiornamenti agli strumenti di supporto alle vendite

>[!MORELIKETHIS]
>
>* [Attribuzione attività](/help/advanced-marketo-measure-features/activities-attribution/salesforce-activities-attribution.md)
>* [Domande frequenti sull’attribuzione delle attività di vendita](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)
