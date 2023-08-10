---
unique-page-id: 27656737
description: Segnala spesa di marketing - [!DNL Marketo Measure] - Documentazione del prodotto
title: Segnala spesa di marketing
exl-id: 46b0f81c-acd1-47a5-bf75-6a943edb9009
feature: Reporting, Spend Management
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Segnala spesa di marketing {#report-marketing-spend}

## Tabella delle spese di marketing {#marketing-spend-table}

La tabella Spese di marketing contiene ora una nuova colonna per visualizzare la valuta per ogni riga Canale, Sottocanale e Campagna. Questa nuova colonna verrà visualizzata per tutti i clienti, anche se non hanno più divise abilitate.

La tabella conterrà ora una combinazione di valute diverse. Consulta la dashboard Spesa marketing se devi ottenere una somma di tutti i canali, i sottocanali o le campagne in una singola valuta.

## Costi di caricamento {#upload-costs}

Quando un utente scarica il file dei costi, il file contiene anche una nuova colonna con la valuta per ogni riga. Le uniche valute accettabili sono quelle che sono state impostate e memorizzate nel CRM. Dovrai conoscere il codice abbreviato di 3 lettere per la tua valuta (ad esempio USD, CAD, JPY, EUR) e se un file viene caricato con una valuta non riconosciuta, il caricamento del file non riuscirà.

## Costi da integrazioni annuncio {#costs-from-ad-integrations}

Quando [!DNL Marketo Measure] importa il costo da piattaforme collegate come AdWords, Bing, Facebook o Doubleclick; utilizziamo anche la valuta riportata. La valuta viene visualizzata insieme al canale, al sottocanale e alla campagna quando compaiono nella tabella Spesa marketing.

Se la valuta del provider di annunci non corrisponde a una valuta estratta dal sistema di gestione delle relazioni con i clienti, potresti visualizzare un errore &quot;Valute miste&quot; in [!DNL Marketo Measure Discover] perché non siamo stati in grado di effettuare una conversione su quella valuta. Per risolvere questo problema, l’amministratore del sistema di gestione delle relazioni con i clienti deve aggiungere una conversione per la valuta sconosciuta.

## Migrare alle spese di marketing convertite {#migrate-to-converted-marketing-spend}

Poiché storicamente la spesa di marketing è stata investita in un&#39;unica valuta (USD), è necessario un piccolo impegno per convertire tutte le spese riportate nella nuova valuta. Anche se nel tuo account non sono abilitate più divise, se hai una singola divisa aziendale diversa da USD, dovrai effettuare questa migrazione.

1. Scarica il file Spesa corrente in un file CSV
1. Verrà visualizzata la colonna Valuta &quot;[!UICONTROL USD]&quot; come valuta presunta. Puoi sostituire manualmente tutte le occorrenze di &quot;[!UICONTROL USD]&quot; oppure utilizzare Trova+Sostituisci per modificare tutte le &quot;[!UICONTROL USD]&quot; istanze nella tua valuta aziendale, ad esempio &quot;[!UICONTROL EUR]&quot; o &quot;[!UICONTROL GBP]&quot; ad esempio.
1. Salva il file e caricalo di nuovo in [!DNL Marketo Measure].
1. Tutti i costi riportati verranno ora visualizzati come nuova valuta.
