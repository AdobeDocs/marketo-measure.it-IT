---
unique-page-id: 27656737
description: Spese di marketing per report - [!DNL Marketo Measure] - Documentazione del prodotto
title: Spese di marketing per i rapporti
exl-id: 46b0f81c-acd1-47a5-bf75-6a943edb9009
source-git-commit: 54337a0a65b79d80ebeae6531f5e92f4f48721a7
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Spese di marketing per i rapporti {#report-marketing-spend}

## Tabella delle spese di marketing {#marketing-spend-table}

La tabella delle spese di marketing contiene ora una nuova colonna per visualizzare la valuta per ciascuna riga Canale, Canale secondario e Campagna. Questa nuova colonna verrà visualizzata per tutti i clienti, anche se non dispongono dell’opzione Valute multiple abilitata.

La tabella conterrà ora una combinazione di valute diverse. Per ottenere una somma di tutti i canali, i sottocanali o le campagne in una sola valuta, consultate la dashboard Marketing Spend (Spese di marketing) .

## Caricare i costi {#upload-costs}

Quando un utente scarica il file dei costi, il file conterrà anche una nuova colonna con la valuta per ogni riga. Le uniche valute accettabili sono quelle che sono state impostate e memorizzate nel CRM. Sarà necessario conoscere il codice abbreviato di 3 lettere per la valuta (cioè USD, CAD, JPY, EUR) e se un file viene caricato con una valuta non riconosciuta, il caricamento del file non riuscirà.

## Costi delle integrazioni pubblicitarie {#costs-from-ad-integrations}

Quando [!DNL Marketo Measure] importa il costo da piattaforme collegate come AdWords, Bing, Facebook o Doubleclick, utilizziamo anche la valuta segnalata. La valuta viene visualizzata accanto al canale, al canale secondario e alla campagna quando viene visualizzata nella tabella Marketing Spend (Spesa di marketing).

Se la valuta del provider di annunci non corrisponde a una valuta prelevata dal CRM, potresti visualizzare un errore &quot;Valute miste&quot; in [!DNL Marketo Measure Discover] perché non è stato possibile effettuare una conversione su quella valuta. Per risolvere questo problema, l’amministratore del sistema di gestione delle relazioni con i clienti deve aggiungere una conversione per la valuta sconosciuta.

## Migrazione a spese di marketing convertite {#migrate-to-converted-marketing-spend}

Dal momento che la nostra spesa di marketing è stata storicamente solo in una singola valuta (USD), c&#39;è una piccola quantità di lavoro necessario per cambiare tutte le spese riportate nella nuova valuta. Anche se il tuo account non ha l&#39;opzione Valute multiple abilitata, se disponi di una singola valuta aziendale diversa da USD, dovrai effettuare questa migrazione.

1. Scarica il file di spesa corrente in un CSV
1. Viene visualizzata la colonna relativa alla valuta &quot;[!UICONTROL USD]&quot; come valuta presunta. Puoi sostituire manualmente tutte le occorrenze di &quot;[!UICONTROL USD]&quot; o utilizzare Trova+Sostituisci per cambiare tutti i &quot;[!UICONTROL USD]&quot; istanze nella propria valuta aziendale, ad esempio &quot;[!UICONTROL EUR]&quot; o &quot;[!UICONTROL GBP]&quot;, ad esempio.
1. Salva il file e caricalo nuovamente in [!DNL Marketo Measure].
1. Tutti i costi segnalati verranno ora visualizzati come nuova valuta.
