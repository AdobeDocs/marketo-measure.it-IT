---
description: Best practice per i canali offline - [!DNL Marketo Measure]
title: Best practice per i canali offline
exl-id: 71c50614-8d5b-469f-bc02-3cc489464a4e
feature: Channels
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 0%

---


# Best practice per i canali offline {#best-practices-for-offline-channels}

## Panoramica {#overview}

Per ottenere rapporti accurati su [!DNL Marketo Measure], i canali di marketing devono essere configurati correttamente. Nel campo &#39;[!UICONTROL Marketing Channel]&#39; viene visualizzato il gruppo di più alto livello di tattiche di marketing a cui può appartenere un punto di contatto, ad esempio Eventi, Webinar, Syndication di contenuti e così via.

La configurazione dei canali di marketing può essere effettuata in due modi: online e offline. Questo documento si concentra sui consigli sulle best practice [!DNL Marketo Measure] per la configurazione e la manutenzione dei canali offline e per la modalità di sincronizzazione con [!DNL Marketo Measure] tramite le campagne CRM.

I canali offline presentano due aspetti chiave:

1. Mappatura canali offline: framework che indica a [!DNL Marketo Measure] a quale canale e sottocanale appartiene il punto di contatto offline
1. Sincronizzazione campagna offline: creazione dei punti di contatto offline

I punti di contatto offline vengono creati da una campagna CRM e sono intesi per tenere traccia di eventuali interazioni di marketing che non possono essere tracciate digitalmente tramite il JavaScript [!DNL Marketo Measure] implementato nelle pagine del sito Web. Quando una campagna CRM viene sincronizzata con [!DNL Marketo Measure], vengono creati punti di contatto per i membri della campagna definiti all&#39;interno della campagna.

Il valore &quot;Canale di marketing&quot; per questi punti di contatto si basa sul campo &quot;Tipo&quot; della campagna. La mappatura di &#39;CRM Campaign Type&#39; a &#39;Marketing Channel&#39; e &#39;Subchannel&#39; è gestita nella scheda &#39;Offline Channels&#39; delle impostazioni account [!DNL Marketo Measure]. La verifica che la mappatura dei canali offline sia accurata e aggiornata garantirà che i dati dei punti di contatto offline vengano attribuiti ai canali marketing e ai sottocanali corretti nel reporting di [!DNL Marketo Measure].

## Best practice | Mappatura canale offline {#best-practice-offline-channel-mapping}

Per la mappatura dei canali offline per la prima volta o per una semplice revisione al fine di verificarne l’accuratezza, considera le seguenti best practice.

* Creare un framework intenzionale per i canali offline
   * Prenditi un po&#39; di tempo per pensare all&#39;organizzazione delle campagne di marketing e a come rientrano nel framework [!DNL Marketo Measure]. Determinare quali canali e sottocanali devono essere rappresentati nei canali offline e quali tipi di campagna CRM differenziano tali canali l’uno dall’altro
* Utilizzare prima i valori &#39;Tipo&#39; della campagna CRM corrente
   * I canali offline sono definiti da &quot;Tipo&quot; della campagna CRM, tuttavia, potrebbe essere necessario creare un valore &quot;Tipo&quot; della campagna CRM personalizzato per adattarlo ai valori ideali del canale offline e del sottocanale. I valori ideali della campagna CRM personalizzata &quot;Type&quot; devono avere la convenzione di denominazione riportata di seguito:
      * CANALE - SOTTOCANALE
      * Esempio: Event - Tradeshow
      * In questo modo la mappatura a livello di sottocanale è il più semplice e pulito possibile
* Un solo sottocanale può essere mappato a un solo &quot;tipo&quot; della campagna CRM
   * È possibile mappare più &quot;Tipi&quot; di campagna CRM a un singolo canale, ma è possibile mappare un solo &quot;Tipo&quot; di campagna CRM a ciascun sottocanale all’interno di ciascun canale
* Solo i &#39;Tipi&#39; della campagna CRM OFFLINE devono essere mappati ai canali offline, in quanto solo le campagne offline devono essere sincronizzate con [!DNL Marketo Measure] per creare punti di contatto:
   * I &#39;Tipi&#39; della campagna CRM online devono essere mappati su un [!UICONTROL Marketing Channel] = &quot;NULL&quot;. Questo valore è consigliato in quanto funge da &#39;flag rosso&#39; che indica che i canali offline sono stati esaminati e qualsiasi &#39;Tipo&#39; della campagna CRM mappato su &quot;NULL&quot; è un &#39;Tipo&#39; ONLINE e non deve essere sincronizzato con [!DNL Marketo Measure]. I punti di contatto relativi ai &#39;Tipi&#39; della campagna CRM online verranno già tracciati tramite la funzionalità e i canali online [!DNL Marketo Measure]. La sincronizzazione di queste campagne comporta il rischio di &quot;duplicare&quot; i punti di contatto/doppio conteggio

## Best practice | Sincronizzazione campagna offline {#best-practice-offline-campaign-sync}

* Assicurati che il campo &quot;Tipo&quot; sia accurato in ogni campagna CRM
   * &quot;Tipo&quot; determina il canale di marketing e il sottocanale per tutti i punti di contatto generati dalla campagna una volta sincronizzati
* Sia che si utilizzi il metodo di sincronizzazione delle campagne basato su CRM (Abilita punti di contatto dell&#39;acquirente) o il metodo di sincronizzazione basato su app [!DNL Marketo Measure] (Sincronizzazione campagna personalizzata nella scheda &#39;[!UICONTROL Campaigns]&#39; delle impostazioni account [!UICONTROL Marketo Measure]), i punti di contatto offline devono essere creati solo se il membro della campagna ha un coinvolgimento offline effettivo con la campagna e il brand:
   * Per i canali offline come eventi o webinar: le &quot;registrazioni&quot; vengono in genere tracciate tramite l&#39;invio di moduli sul sito Web e la funzionalità online di [!DNL Marketo Measure]. Pertanto, i membri della campagna con lo stato &quot;Registrato&quot; non devono ricevere un punto di contatto offline dalla campagna per evitare un doppio conteggio. I punti di contatto offline devono essere rappresentativi della &quot;partecipazione&quot; solo all’evento o al webinar.
   * Alcuni canali offline come Syndication dei contenuti sono più semplici in quanto ogni membro della campagna ha lo stesso stato di &quot;risposta&quot;, il che significa che ha effettivamente risposto alla campagna. In questo caso, scarica i contenuti su un sito di terze parti e quindi dovrebbe ricevere un punto di contatto offline.
* Quando si utilizza il metodo di sincronizzazione delle campagne personalizzate nell&#39;app [!DNL Marketo Measure], accertarsi che il campo &quot;Data punto di contatto&quot; sia basato sul campo data del membro della campagna o della campagna indicativo del momento in cui l&#39;interazione del punto di contatto si è effettivamente verificata
* Utilizza il pulsante &quot;Bulk Update Touchpoint Date&quot; (Aggiorna data punto di contatto in blocco) se devi sovrascrivere &quot;Touchpoint Date&quot; (Data punto di contatto) per uno qualsiasi dei punti di contatto offline originati da una campagna CRM. La &quot;Data del punto di contatto&quot; deve essere il più accurata possibile per garantire che il punto di contatto contenga la &quot;Posizione del punto di contatto&quot; più accurata possibile e quindi l’importo corretto del credito di attribuzione

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

Una volta effettuata la configurazione iniziale, la configurazione del canale offline continua a creare di conseguenza punti di contatto offline. Come best practice, è consigliabile rivedere la configurazione offline almeno due volte all’anno. Questo garantisce dati di contatto dell&#39;acquirente puliti e accurati.

Inoltre, se apporti modifiche alla gestione o ai processi di Campaign, devi accertarti di aggiornare la mappatura e/o il processo di sincronizzazione del canale offline [!DNL Marketo Measure].

Le modifiche che potrebbero attivare il team per apportare aggiornamenti alla configurazione del canale offline in [!DNL Marketo Measure] possono includere:

* &quot;Tipi&quot; di campagna CRM creati o modificati
* Stato del membro della campagna creato o modificato
* Se utilizzi il metodo di sincronizzazione delle campagne CRM tramite il campo &quot;Abilita punti di contatto buyer&quot;, assicurati che questo campo sia rivisto e aggiornato per ogni campagna CRM creata. Se questo campo viene trascurato, non ci saranno dati di punti di contatto offline correlati
* Se rilevi punti di contatto offline da una campagna CRM che sembrano punti di contatto online (Canale marketing = NULL), assicurati che la campagna CRM correlata sia rivista e che la sincronizzazione sia disabilitata

Se il tuo team ha recentemente riscontrato uno di questi problemi, [!DNL Marketo Measure] consiglia di rivedere la mappatura del canale offline e le campagne offline per apportare le modifiche appropriate e assicurarti che siano sincronizzate correttamente.

>[!MORELIKETHIS]
> [Configurazione canale offline](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)
> [Sincronizzazione campagna personalizzata - Sincronizzazione app](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md)
> [Sincronizzazione delle campagne offline - Sincronizzazione CRM](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md)
> [Membri campagna e campagna offline - Sincronizzazione CRM](/help/channel-tracking-and-setup/offline-channels/legacy-processes/campaigns-and-campaign-members.md)
> [Date di sincronizzazione campagna - Sincronizzazione CRM](/help/channel-tracking-and-setup/offline-channels/legacy-processes/campaign-sync-dates.md)
> [Configurazioni per più tipi di record campagna](/help/channel-tracking-and-setup/offline-channels/configurations-record-types.md)
> [Creazione di una visualizzazione elenco campagne](/help/channel-tracking-and-setup/offline-channels/legacy-processes/creating-a-campaign-list-view-for-salesforce-campaigns.md)
> [Sincronizzazione dei dati cronologici](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-historical-data.md)
