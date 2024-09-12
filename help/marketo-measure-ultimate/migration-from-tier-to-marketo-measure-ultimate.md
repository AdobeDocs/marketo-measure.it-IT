---
description: Scopri il processo di migrazione durante il passaggio dalla sottoscrizione a più livelli  [!DNL Marketo Measure] a Ultimate [!DNL Marketo Measure] .
title: Migrazione dal livello a  [!DNL Marketo Measure] Ultimate
feature: Integration, Tracking, Attribution
source-git-commit: 9c3c3c75a9a505bb078da18e13f210add8699c24
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 1%

---

# Migrazione dal livello 1-2 a [!DNL Marketo Measure] Ultimate {#migration-from-tier-to-marketo-measure-ultimate}

Questo articolo illustra il processo di migrazione per gli utenti che passano dalla sottoscrizione di livello 1 o 2 a [!DNL Marketo Measure] Ultimate.

>[!IMPORTANT]
>
>Ricorda di mantenere l’istanza di livello esistente fino al completamento della migrazione.

## Raccolta dati {#data-collection}

### Dati traffico web {#web-traffic-data}

* Non sono richieste modifiche per l’implementazione di JavaScript.

* Abilita i domini nella nuova istanza Ultimate.

* Se necessario, invia un ticket per migrare ed elaborare nuovamente i dati web storici.

* Le integrazioni degli annunci rimangono invariate, ma ricorda di ricollegarle in Ultimate. Prima di procedere, accertati di disconnettere gli account annuncio nel tenant di livello.

>[!NOTE]
>
>I dati storici sui costi degli annunci non verranno importati. I dati sui costi degli annunci verranno importati solo dopo la riconnessione degli account degli annunci.

### Connessione dati organizzazione {#enterprise-data-connection}

Reimplementa tutte le connessioni dati di origine in AEP, incluse le connessioni CRM e di Marketo Engage.

## Trasformazione dei dati {#data-transformation}

* Le funzioni di Account-Based Marketing, tra cui la corrispondenza lead-account e i punteggi di coinvolgimento predittivi, non sono disponibili in Ultimate.

   * Tuttavia, puoi importare i risultati di corrispondenza lead-account tramite AEP e utilizzarli all’interno della piattaforma.

* In Ultimate, le transizioni di fase storiche del CRM sono dedotte piuttosto che lette direttamente, in quanto non esiste una connessione CRM diretta.

   * Leggiamo i record di opportunità e le marche temporali e vediamo la fase corrente, quindi deduciamo le fasi storiche.

## Generazione rapporti {#reporting}

* Ultimate non invia i dati ai CRM.

   * Per inviare nuovamente i dati al sistema di gestione delle relazioni con i clienti, è necessaria una pipeline ETL personalizzata per estrarre i dati dal Snowflake Marketo Measure al sistema di gestione delle relazioni con i clienti. Devi impostare un modello dati personalizzato nel CRM.

* Tutte le dashboard di Discover rimangono invariate rispetto alla soluzione su più livelli, con l&#39;aggiunta delle dashboard di Attribution AI.
