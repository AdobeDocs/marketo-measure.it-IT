---
description: Indicazioni sulle spese di marketing per gli utenti di Marketo Measure
title: Segnala spesa di marketing
exl-id: 46b0f81c-acd1-47a5-bf75-6a943edb9009
feature: Reporting, Spend Management
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: d24e0b99-7796-5c7d-831d-d71a1d725f01
    internal-label: Reporting
  - id: e3b4b95f-0bb9-5cb3-a479-9dcb943dca3f
    internal-label: Spend Management
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%
---
# Segnala spesa di marketing {#report-marketing-spend}

## Tabella delle spese di marketing {#marketing-spend-table}

La tabella Spese marketing contiene una nuova colonna per visualizzare la valuta per ogni riga Canale, Sottocanale e Campagna. Questa nuova colonna viene visualizzata per tutti i clienti, anche se non hanno più divise abilitate.

La tabella contiene una combinazione di valute diverse. Per ottenere una somma di tutti i canali, i sottocanali o le campagne in un’unica valuta, fai riferimento al dashboard Spesa marketing.

## Costi di caricamento {#upload-costs}

Quando un utente scarica il file dei costi, il file contiene anche una nuova colonna con la valuta per ogni riga. Le uniche valute accettabili sono quelle che sono state impostate e memorizzate nel CRM. Devi conoscere il codice abbreviato di 3 lettere per la tua valuta (USD, CAD, JPY, EUR) e se un file viene caricato con una valuta non riconosciuta, il caricamento del file non riesce.

## Costi da integrazioni annuncio {#costs-from-ad-integrations}

Quando [!DNL Marketo Measure] importa il costo da piattaforme collegate come AdWords, Bing, Facebook o Doubleclick, viene utilizzata anche la valuta riportata. La valuta viene visualizzata accanto a Canale, Sottocanale e Campagna quando viene visualizzata nella tabella Spesa marketing.

Se la valuta del provider di annunci non corrisponde a una valuta estratta dal CRM, è possibile che venga visualizzato un errore &quot;Valute miste&quot; in [!DNL Marketo Measure Discover]. Per risolvere questo problema, l’amministratore del sistema di gestione delle relazioni con i clienti deve aggiungere una conversione per la valuta sconosciuta.

## Migrare alle spese di marketing convertite {#migrate-to-converted-marketing-spend}

Poiché storicamente le spese di marketing sono state in un’unica valuta (USD), è necessario un po’ di lavoro per convertire tutte le spese riportate nella nuova valuta. Anche se per il tuo account non sono abilitate più valute, se disponi di una singola valuta aziendale diversa da USD devi effettuare questa migrazione.

1. Scarica il file Spesa corrente in un file CSV
1. Nella colonna Valuta viene visualizzato &quot;[!UICONTROL USD]&quot; come valuta assunta. È possibile sostituire manualmente tutte le occorrenze di &quot;[!UICONTROL USD]&quot; oppure utilizzare Trova+Sostituisci per modificare tutte le istanze &quot;[!UICONTROL USD]&quot; nella propria valuta aziendale, ad esempio &quot;[!UICONTROL EUR]&quot; o &quot;[!UICONTROL GBP]&quot;.
1. Salva il file e caricalo di nuovo in [!DNL Marketo Measure].
1. Tutti i costi riportati verranno ora visualizzati come nuova valuta.
