---
description: Tecniche consigliate per i canali offline - [!DNL Marketo Measure] - Documentazione del prodotto
title: Tecniche consigliate per i canali offline
exl-id: 71c50614-8d5b-469f-bc02-3cc489464a4e
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '1050'
ht-degree: 0%

---

# Tecniche consigliate per i canali offline {#best-practices-for-offline-channels}

## Panoramica {#overview}

Per avere precisione [!DNL Marketo Measure] reporting, i canali di marketing devono essere configurati correttamente. Il[!UICONTROL Marketing Channel]Il campo &quot; visualizza il gruppo di massimo livello di tattiche di marketing a cui un punto di contatto può appartenere (ad esempio, Eventi, Webinar, Sincronizzazione dei contenuti, ecc.).

Esistono due aspetti per configurare i canali di marketing: online e offline. Questo documento sarà incentrato sul [!DNL Marketo Measure] consigli sulle best practice per la configurazione e la manutenzione dei canali offline e su come sincronizzarli con [!DNL Marketo Measure] tramite campagne CRM.

I canali offline hanno due aspetti chiave:

1. Mappatura del canale offline, framework che indica [!DNL Marketo Measure] a quale punto di contatto Canale e Sottocanale appartiene il punto di contatto Offline
1. Sincronizzazione campagna offline: la creazione dei punti di contatto offline

I punti di contatto offline vengono creati da una campagna CRM e sono destinati a monitorare qualsiasi interazione di marketing che non può essere tracciata digitalmente tramite il [!DNL Marketo Measure] JavaScript implementato sulle pagine del sito web. Quando una campagna di gestione delle relazioni con i clienti viene sincronizzata con [!DNL Marketo Measure], i punti di contatto vengono creati per i membri della campagna definiti all’interno della campagna.

Il valore &quot;Canale di marketing&quot; per questi punti di contatto si basa sul campo &quot;Tipo&quot; della campagna. La mappatura di &quot;Tipo campagna CRM&quot; su &quot;Canale marketing&quot; e &quot;Canale secondario&quot; viene gestita all’interno della scheda &quot;Canali offline&quot; del tuo [!DNL Marketo Measure] Impostazioni account. Garantire che la mappatura del canale offline sia accurata e aggiornata garantirà che i dati dei punti di contatto offline siano attribuiti ai canali di marketing e ai sottocanali corretti all’interno dei tuoi [!DNL Marketo Measure] Generazione rapporti.

## Best practice | Mappatura del canale offline {#best-practice-offline-channel-mapping}

Sia che mappi i canali offline per la prima volta o che li riveda per verificarne l&#39;accuratezza, tieni a mente le seguenti best practice.

* Crea un framework deliberato per i canali offline
   * Prenditi del tempo per pensare all’organizzazione delle campagne di marketing e a come si adattano alle [!DNL Marketo Measure] struttura. Determinare quali canali e sottocanali devono essere rappresentati nei canali offline e quali tipi di campagna CRM differenziano tali canali l’uno dall’altro
* Lavora per utilizzare prima i valori &#39;Type&#39; della campagna CRM corrente
   * I canali offline sono definiti dal &#39;Tipo&#39; della campagna CRM, tuttavia potrebbe essere necessario creare il valore &#39;Tipo&#39; della campagna CRM personalizzata per contenere i valori del canale offline e del canale secondario ideali. I valori &quot;Type&quot; della campagna CRM personalizzata ideali devono includere la convenzione di denominazione mostrata di seguito:
      * CANALE - SOTTOCANALE
      * Esempio: Evento - Tradeshow
      * In questo modo la mappatura a livello di canale secondario è il più semplice e pulito possibile
* Un solo sottocanale può essere mappato a un solo &quot;Tipo&quot; campagna CRM
   * Puoi mappare più tipi di campagna CRM su un singolo canale, ma solo un &quot;tipo&quot; di campagna CRM può essere mappato su ciascun sottocanale all’interno di ciascun canale
* Solo i &quot;tipi&quot; della campagna CRM OFFLINE devono essere mappati su canali offline in quanto solo le campagne offline devono essere sincronizzate con [!DNL Marketo Measure] per creare punti di contatto:
   * I &#39;tipi&#39; della campagna CRM ONLINE devono essere mappati su un [!UICONTROL Marketing Channel] = &quot;NULL&quot;. Questo valore è consigliato in quanto agisce come un &quot;flag rosso&quot; che denota i tuoi canali offline sono stati rivisti e qualsiasi campagna CRM &#39;Type&#39; mappato a &quot;NULL&quot; è un &#39;Type&#39; ONLINE e non deve essere sincronizzato con [!DNL Marketo Measure]. I punti di contatto relativi ai &quot;tipi&quot; della campagna CRM online sarebbero già tracciati tramite [!DNL Marketo Measure] Funzionalità e canali online. La sincronizzazione di queste campagne comporta il rischio di punti di contatto/doppio conteggio

## Best practice | Sincronizzazione campagna offline {#best-practice-offline-campaign-sync}

* Assicurati che il campo &quot;Tipo&quot; sia accurato su ogni campagna CRM
   * &quot;Type&quot; determina il canale di marketing e il sottocanale per tutti i punti di contatto provenienti dalla campagna una volta sincronizzati
* Se si utilizza il metodo di sincronizzazione delle campagne basato su CRM (abilitare i punti di contatto dell’acquirente) o [!DNL Marketo Measure] Metodo di sincronizzazione basato su app (sincronizzazione di campagna personalizzata all’interno di &#39;[!UICONTROL Campaigns]scheda del [!UICONTROL Marketo Measure] Impostazioni account), i punti di contatto offline devono essere creati solo se il membro della campagna ha avuto un effettivo coinvolgimento offline con la campagna e il tuo marchio:
   * Per canali offline come Eventi o Webinar: le &quot;registrazioni&quot; sono tipicamente monitorate tramite l&#39;invio di moduli sul sito web e [!DNL Marketo Measure] Funzionalità online. Pertanto, i membri della campagna con uno stato di &quot;Registrato&quot; non devono ricevere un punto di contatto offline dalla campagna per evitare il doppio conteggio. I punti di contatto offline devono essere rappresentativi della &quot;presenza&quot; solo all’evento o al webinar.
   * Alcuni canali offline come la sindacazione dei contenuti sono solitamente più semplici in quanto ogni membro della campagna ha lo stesso stato di &quot;risposta&quot; che rappresenta che ha effettivamente risposto alla campagna, in questo caso scarica contenuto su un sito di terze parti e quindi dovrebbe ricevere un punto di contatto offline
* Quando utilizzi il metodo di sincronizzazione della campagna personalizzata in [!DNL Marketo Measure] App, assicurati che il campo &quot;Data punto di contatto&quot; sia basato sul campo data del membro della campagna o della campagna che è più indicativo di quando si è verificata l’interazione con il punto di contatto
* Utilizza il pulsante &quot;Aggiorna in blocco data punto di contatto&quot; se devi sovrascrivere la &quot;data punto di contatto&quot; per uno qualsiasi dei punti di contatto offline provenienti da una campagna CRM. La &quot;Data punto di contatto&quot; deve essere il più accurata possibile per garantire che il punto di contatto contenga la più accurata possibile &quot;Posizione punto di contatto&quot; e, quindi, la corretta quantità di credito di attribuzione

## Best practice per la manutenzione {#best-practice-for-maintenance}

Una volta effettuata la configurazione iniziale, la configurazione del canale offline continuerà a creare punti di contatto offline di conseguenza. Come best practice, ti consigliamo di rivedere la configurazione offline almeno due volte all&#39;anno. In questo modo è possibile garantire dati precisi e precisi sui punti di contatto dell’acquirente.

Inoltre, se apporti modifiche alla gestione o ai processi di Campaign, dovrai accertarti di effettuare l’aggiornamento [!DNL Marketo Measure] Processo di mappatura e/o sincronizzazione dei canali offline

Modifiche che potrebbero attivare il team per apportare aggiornamenti alla configurazione del canale offline in [!DNL Marketo Measure] possono includere:

* Creazione o modifica della campagna di gestione delle relazioni con i clienti
* Stato membro campagna creato o modificato
* Se utilizzi il metodo di sincronizzazione della campagna di gestione delle relazioni con i clienti tramite il campo &quot;Abilita punti di contatto per gli acquirenti&quot;, assicurati che questo campo sia rivisto e aggiornato per ogni campagna di gestione delle relazioni con i clienti creata. Se questo campo viene ignorato, non saranno presenti dati relativi ai punti di contatto offline
* Se ti imbatti in qualsiasi punto di contatto offline di una campagna CRM che sembri essere punti di contatto online (canale di marketing = NULL), assicurati che la relativa campagna CRM sia rivista e che la sincronizzazione sia disabilitata

Se il tuo team ha recentemente sperimentato uno di questi, [!DNL Marketo Measure] consiglia di rivedere la mappatura dei canali offline e le campagne offline per apportare le modifiche appropriate e assicurarsi che siano sincronizzate correttamente.

>[!MORELIKETHIS]
>
>* [Configurazione del canale offline](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)
>* [Sincronizzazione campagna personalizzata - Sincronizzazione app](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md)
>* [Sincronizzazione delle campagne offline - Sincronizzazione CRM](/help/channel-tracking-and-setup/offline-channels/syncing-offline-campaigns.md)
>* [Membri di campagne e campagne offline - Sincronizzazione CRM](/help/channel-tracking-and-setup/offline-channels/campaigns-and-campaign-members.md)
>* [Date di sincronizzazione della campagna - Sincronizzazione CRM](/help/channel-tracking-and-setup/offline-channels/campaign-sync-dates.md)
>* [Configurazioni per più tipi di record di campagne](/help/channel-tracking-and-setup/offline-channels/configurations-for-multiple-campaign-record-types.md)
>* [Creazione di una visualizzazione elenco di campagne](/help/channel-tracking-and-setup/offline-channels/creating-a-campaign-list-view-for-salesforce-campaigns.md)
>* [Sincronizzazione dei dati storici](/help/channel-tracking-and-setup/offline-channels/syncing-historical-data.md)

