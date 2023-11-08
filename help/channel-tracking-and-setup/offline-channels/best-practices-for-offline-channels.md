---
description: Best practice per i canali offline - [!DNL Marketo Measure] - Documentazione del prodotto
title: Best practice per i canali offline
exl-id: 71c50614-8d5b-469f-bc02-3cc489464a4e
feature: Channels
source-git-commit: b8ea008c594ed114323dedd3762d1265287193c7
workflow-type: tm+mt
source-wordcount: '1050'
ht-degree: 0%

---

# Best practice per i canali offline {#best-practices-for-offline-channels}

## Panoramica {#overview}

Per ottenere [!DNL Marketo Measure] rapporti di, i canali di marketing devono essere configurati correttamente. L&#39;&#39;[!UICONTROL Marketing Channel]&quot;mostra il gruppo di più alto livello di tattiche di marketing a cui può appartenere un punto di contatto (ad esempio, Eventi, Webinar, Syndication di contenuti, ecc.).

La configurazione dei canali di marketing può essere effettuata in due modi: online e offline. Questo documento si concentrerà sulla [!DNL Marketo Measure] raccomandazioni sulle best practice per l’impostazione e la manutenzione dei canali offline e per la loro sincronizzazione con [!DNL Marketo Measure] tramite campagne CRM.

I canali offline presentano due aspetti chiave:

1. Offline Channel Mapping, framework che indica [!DNL Marketo Measure] a quale canale e sottocanale appartiene il punto di contatto offline
1. Sincronizzazione campagna offline: creazione dei punti di contatto offline

I punti di contatto offline sono creati da una campagna CRM e sono intesi per tenere traccia di eventuali interazioni di marketing che non possono essere tracciate digitalmente tramite la [!DNL Marketo Measure] JavaScript implementato nelle pagine del sito web. Quando una campagna CRM viene sincronizzata con [!DNL Marketo Measure], i punti di contatto vengono creati per i membri della campagna definiti all’interno della campagna.

Il valore &quot;Canale di marketing&quot; per questi punti di contatto si basa sul campo &quot;Tipo&quot; della campagna. La mappatura di &quot;CRM Campaign Type&quot; a &quot;Marketing Channel&quot; e &quot;Subchannel&quot; è gestita nella scheda &quot;Offline Channels&quot; della [!DNL Marketo Measure] Impostazioni account. Assicurati che la mappatura del canale offline sia accurata e aggiornata e che i dati dei punti di contatto offline vengano attribuiti ai canali di marketing e ai sottocanali corretti all’interno del tuo [!DNL Marketo Measure] Generazione rapporti.

## Best practice | Mappatura canale offline {#best-practice-offline-channel-mapping}

Se stai eseguendo la mappatura dei canali offline per la prima volta o semplicemente esaminandoli per verificarne l’accuratezza, tieni presente le seguenti best practice.

* Creare un framework intenzionale per i canali offline
   * Prenditi un po’ di tempo per pensare all’organizzazione delle campagne di marketing e a come si adattano al [!DNL Marketo Measure] infrastruttura. Determinare quali canali e sottocanali devono essere rappresentati nei canali offline e quali tipi di campagna CRM differenziano tali canali l’uno dall’altro
* Utilizzare prima i valori &#39;Tipo&#39; della campagna CRM corrente
   * I canali offline sono definiti da &quot;Tipo&quot; della campagna CRM, tuttavia, potrebbe essere necessario creare un valore &quot;Tipo&quot; della campagna CRM personalizzato per adattarlo ai valori ideali del canale offline e del sottocanale. I valori ideali della campagna CRM personalizzata &quot;Type&quot; devono avere la convenzione di denominazione riportata di seguito:
      * CANALE - SOTTOCANALE
      * Esempio: Event - Tradeshow
      * In questo modo la mappatura a livello di sottocanale è il più semplice e pulito possibile
* Un solo sottocanale può essere mappato a un &#39;Tipo&#39; della campagna CRM
   * È possibile mappare più &quot;Tipi&quot; di campagna CRM a un singolo canale, ma è possibile mappare un solo &quot;Tipo&quot; di campagna CRM a ciascun sottocanale all’interno di ciascun canale
* Solo i &#39;Tipi&#39; della campagna CRM OFFLINE devono essere mappati ai canali offline, in quanto solo le campagne offline devono essere sincronizzate con [!DNL Marketo Measure] per creare punti di contatto:
   * I &#39;Tipi&#39; della campagna CRM ONLINE devono essere mappati su un [!UICONTROL Marketing Channel] = &quot;NULL&quot;. Questo valore è consigliato in quanto funge da &#39;flag rosso&#39; che indica che i tuoi canali offline sono stati revisionati e che qualsiasi &#39;Tipo&#39; della campagna CRM mappato su &quot;NULL&quot; è un &#39;Tipo&#39; ONLINE e non deve essere sincronizzato con [!DNL Marketo Measure]. I punti di contatto relativi ai &quot;Tipi&quot; di campagne CRM online verranno già tracciati tramite [!DNL Marketo Measure] Funzionalità e canali online. La sincronizzazione di queste campagne comporta il rischio di &quot;duplicare&quot; i punti di contatto/doppio conteggio

## Best practice | Sincronizzazione campagna offline {#best-practice-offline-campaign-sync}

* Assicurati che il campo &quot;Tipo&quot; sia accurato in ogni campagna CRM
   * &quot;Tipo&quot; determina il canale di marketing e il sottocanale per tutti i punti di contatto generati dalla campagna una volta sincronizzati
* Se si utilizza il metodo di sincronizzazione delle campagne basato su CRM (Abilita punti di contatto dell’acquirente) o [!DNL Marketo Measure] Metodo di sincronizzazione basato su app (sincronizzazione campagna personalizzata all’interno di )[!UICONTROL Campaigns]&#39; del tuo [!UICONTROL Marketo Measure] Impostazioni account), i punti di contatto offline devono essere creati solo se il membro della campagna ha un coinvolgimento offline effettivo con la campagna e il tuo marchio:
   * Per canali offline come eventi o webinar: le &quot;registrazioni&quot; vengono generalmente tracciate tramite l’invio di moduli sul sito web e [!DNL Marketo Measure] Funzionalità online. Pertanto, i membri della campagna con lo stato &quot;Registrato&quot; non devono ricevere un punto di contatto offline dalla campagna per evitare un doppio conteggio. I punti di contatto offline devono essere rappresentativi della &quot;partecipazione&quot; solo all’evento o al webinar.
   * Alcuni canali offline, come la diffusione di contenuti, sono solitamente più semplici in quanto ogni membro della campagna ha lo stesso stato di &quot;risposta&quot;, il che significa che ha effettivamente risposto alla campagna; in questo caso, scarica i contenuti su un sito di terze parti e quindi dovrebbe ricevere un punto di contatto offline
* Quando si utilizza il metodo di sincronizzazione personalizzato delle campagne in [!DNL Marketo Measure] App, assicurati che il campo &quot;Data punto di contatto&quot; sia basato sul campo data del membro della campagna o della campagna che è più indicativo del momento in cui l’interazione del punto di contatto si è effettivamente verificata
* Sfrutta il pulsante &quot;Bulk Update Touchpoint Date&quot; (Aggiorna data punto di contatto in blocco) se devi sovrascrivere &quot;Touchpoint Date&quot; (Data punto di contatto) per qualsiasi punto di contatto offline originato da una campagna CRM. La &quot;Data del punto di contatto&quot; deve essere il più accurata possibile affinché il punto di contatto contenga la &quot;Posizione del punto di contatto&quot; più accurata possibile e quindi l’importo corretto del credito di attribuzione

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

Una volta effettuata la configurazione iniziale, l’impostazione del canale offline continuerà a creare di conseguenza punti di contatto offline. Come best practice, è consigliabile rivedere la configurazione offline almeno due volte all’anno. In questo modo i dati dei punti di contatto dell&#39;acquirente saranno accurati e accurati.

Inoltre, se apporti modifiche alla gestione o ai processi di Campaign, dovrai accertarti di aggiornare i [!DNL Marketo Measure] Processo di mappatura e/o sincronizzazione del canale offline.

Modifiche che potrebbero attivare il team per apportare aggiornamenti alla configurazione del canale offline in [!DNL Marketo Measure] potrebbe includere:

* &#39;Tipi&#39; di campagna CRM creati o modificati
* Stato del membro della campagna creato o modificato
* Se utilizzi il metodo di sincronizzazione delle campagne CRM tramite il campo &quot;Abilita punti di contatto buyer&quot;, assicurati che questo campo sia rivisto e aggiornato per ogni campagna CRM creata. Se questo campo viene trascurato, non ci saranno dati di punti di contatto offline correlati
* Se rilevi punti di contatto offline da una campagna CRM che sembrano punti di contatto online (Canale marketing = NULL), assicurati che la campagna CRM correlata sia rivista e che la sincronizzazione sia disabilitata

Se il tuo team ha avuto di recente una delle esperienze precedenti, [!DNL Marketo Measure] consiglia di rivedere la mappatura dei canali offline e le campagne offline per apportare le modifiche appropriate e assicurarti che siano sincronizzate correttamente.

>[!MORELIKETHIS]
>
>* [Configurazione canale offline](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)
>* [Sincronizzazione campagna personalizzata - Sincronizzazione app](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md)
>* [Sincronizzazione delle campagne offline - Sincronizzazione CRM](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md)
>* [Membri campagna e campagna offline - Sincronizzazione CRM](/help/channel-tracking-and-setup/offline-channels/legacy-processes/campaigns-and-campaign-members.md)
>* [Date di sincronizzazione campagna - Sincronizzazione CRM](/help/channel-tracking-and-setup/offline-channels/legacy-processes/campaign-sync-dates.md)
>* [Configurazioni per più tipi di record campagna](/help/channel-tracking-and-setup/offline-channels/configurations-for-multiple-campaign-record-types.md)
>* [Creazione di una vista a elenco delle campagne](/help/channel-tracking-and-setup/offline-channels/legacy-processes/creating-a-campaign-list-view-for-salesforce-campaigns.md)
>* [Sincronizzazione dei dati cronologici](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-historical-data.md)
