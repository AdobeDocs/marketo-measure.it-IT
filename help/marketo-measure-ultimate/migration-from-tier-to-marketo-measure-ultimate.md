---
description: Informazioni sul processo di migrazione durante lo spostamento dall'abbonamento a più livelli [!DNL Marketo Measure] ad Ultimate [!DNL Marketo Measure].
title: Migrazione dal livello a [!DNL Marketo Measure] Ultimate
feature: Integration, Tracking, Attribution
exl-id: 828c9bba-3835-484a-bd80-84b5a6b67e22
TQID: 'https://experienceleague.adobe.com/Q-VV8-RWaGb-lk-vr3y9KK9SjTlsugPJ-N4HrSH5uxA'
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: c8f57308-7e33-4e41-a385-b55041c78939
    internal-label: Integrations
  - id: 7da342c5-06ee-5869-b3e8-b73d5bf75a9d
    internal-label: Integration
  - id: dcbeff6e-0253-5a4b-9ac2-1b67cc4a6286
    internal-label: Tracking
  - id: d7322935-5b46-52a3-b6ea-21e6aec748b5
    internal-label: Attribution
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '286'
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
