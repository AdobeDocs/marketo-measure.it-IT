---
unique-page-id: 27656737
description: Segnala spesa marketing - [!DNL Marketo Measure]
title: Segnala spesa di marketing
exl-id: 46b0f81c-acd1-47a5-bf75-6a943edb9009
feature: Reporting, Spend Management
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '341'
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

Poiché la spesa di marketing è stata storicamente solo in una singola valuta (USD), è necessaria una piccola quantità di lavoro per modificare tutte le spese riportate nella nuova valuta. Anche se nel tuo account non sono abilitate più divise, se hai una singola divisa aziendale diversa da USD, devi effettuare questa migrazione.

1. Scarica il file Spesa corrente in un file CSV
1. Nella colonna Valuta viene visualizzato &quot;[!UICONTROL USD]&quot; come valuta assunta. È possibile sostituire manualmente tutte le occorrenze di &quot;[!UICONTROL USD]&quot; oppure utilizzare Trova+Sostituisci per modificare tutte le istanze &quot;[!UICONTROL USD]&quot; nella propria valuta aziendale, ad esempio &quot;[!UICONTROL EUR]&quot; o &quot;[!UICONTROL GBP]&quot;.
1. Salva il file e caricalo di nuovo in [!DNL Marketo Measure].
1. Tutti i costi riportati verranno ora visualizzati come nuova valuta.
