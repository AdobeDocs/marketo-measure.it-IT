---
description: Scopri il processo di migrazione durante il passaggio dalla sottoscrizione a più livelli  [!DNL Marketo Measure] ad Ultimate [!DNL Marketo Measure] .
title: Migrazione dal livello a  [!DNL Marketo Measure] Ultimate
feature: Integration, Tracking, Attribution
exl-id: 828c9bba-3835-484a-bd80-84b5a6b67e22
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 1%

---

# Migrazione da Ultimate livello 1-2 a [!DNL Marketo Measure] {#migration-from-tier-to-marketo-measure-ultimate}

Questo articolo illustra il processo di migrazione per gli utenti che passano dalla sottoscrizione di livello 1 o 2 ad Ultimate [!DNL Marketo Measure].

>[!IMPORTANT]
>
>Ricorda di mantenere l’istanza di livello esistente fino al completamento della migrazione.

## Raccolta dati {#data-collection}

### Dati traffico web {#web-traffic-data}

* Non sono richieste modifiche per l’implementazione di JavaScript.

* Abilita i domini nella nuova istanza di Ultimate.

* Se necessario, invia un ticket per migrare ed elaborare nuovamente i dati web storici.

* Le integrazioni degli annunci rimangono invariate, ma ricorda di ricollegarle in Ultimate. Prima di procedere, accertati di disconnettere gli account annuncio nel tenant di livello.

>[!NOTE]
>
>I dati storici sui costi degli annunci non verranno importati. I dati sui costi degli annunci verranno importati solo dopo la riconnessione degli account degli annunci.

### Connessione dati organizzazione {#enterprise-data-connection}

Reimplementa tutte le connessioni dati di origine in AEP, incluse le connessioni CRM e Marketo Engage.

## Trasformazione dei dati {#data-transformation}

* Le funzioni di Account-Based Marketing, tra cui la corrispondenza lead-account e i punteggi di coinvolgimento predittivi, non sono disponibili in Ultimate.

   * Tuttavia, puoi importare i risultati di corrispondenza lead-account tramite AEP e utilizzarli all’interno della piattaforma.

* In Ultimate, le transizioni di fase storiche del CRM sono dedotte anziché lette direttamente, in quanto non esiste una connessione CRM diretta.

   * Leggiamo i record di opportunità e le marche temporali e vediamo la fase corrente, quindi deduciamo le fasi storiche.

## Generazione dei rapporti {#reporting}

* Ultimate non invia i dati ai CRM.

   * Per inviare nuovamente i dati al CRM, è necessaria una pipeline ETL personalizzata per estrarre i dati da Marketo Measure Snowflake al CRM. Devi impostare un modello dati personalizzato nel CRM.

* Tutte le dashboard di Discover rimangono invariate rispetto alla soluzione su più livelli, con l’aggiunta delle dashboard di IA per l’attribuzione.
