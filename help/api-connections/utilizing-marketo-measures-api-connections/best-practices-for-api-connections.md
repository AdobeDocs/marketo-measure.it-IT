---
description: Best practice per le connessioni API - [!DNL Marketo Measure]
title: Best practice per le connessioni API
exl-id: b8550e4e-a567-427f-b5d3-50232553a066
feature: APIs, Integration
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 0%

---

# Best practice per le connessioni API {#best-practices-for-api-connections}

## Panoramica {#overview}

[!DNL Marketo Measure] offre connessioni API con [!DNL Google AdWords], [!DNL Microsoft Bing Ads], [!DNL Facebook Ads] e LinkedIn. Queste connessioni API consentono a [!DNL Marketo Measure] di estrarre una serie di dati dalle piattaforme pubblicitarie su cui è possibile generare rapporti nei dati di Buyer Touchpoint. Una caratteristica chiave di queste connessioni API è la capacità di richiamare automaticamente i dati di spesa, risparmiando a te e al tuo team il tempo e l’impegno necessari per caricare manualmente i dati per il reporting del ROI. La configurazione di queste connessioni API non è obbligatoria per [!DNL Marketo Measure] per tenere traccia di tali canali, ma fornisce dettagli granulari utili per migliorare il reporting.

Le connessioni API [!DNL Marketo Measure] sono un aspetto fondamentale del tuo account e le nostre raccomandazioni sulle best practice consentiranno a te e al tuo team di utilizzare al massimo le nostre connessioni.

## Best practice {#best-practice}

Indipendentemente dalla piattaforma pubblicitaria che stai connettendo, le seguenti linee guida sono importanti da tenere a mente.

* Usa un amministratore per la connessione
* Puoi collegare più account di annunci per una piattaforma
* Connetti tutti i possibili account annuncio per automatizzare il più possibile la generazione di rapporti sulla spesa
* Se disponibile, implementa sempre un modello di tracciamento. Il modello garantisce che, anche se l&#39;account dell&#39;annuncio viene disconnesso, [!DNL Marketo Measure] sia ancora in grado di richiamare dettagli granulari sull&#39;annuncio

Per ottimizzare ogni API [!DNL Marketo Measure], attieniti alle seguenti best practice.

**[!DNL Facebook]**: connessione con assegnazione tag automatica

Prima di abilitare l’assegnazione tag automatica, esporta la cronologia degli annunci in un file CSV. L&#39;abilitazione dell&#39;assegnazione tag automatica reimposterà la cronologia delle conversioni e la verifica tramite social di tutti gli annunci con tag di [!DNL Marketo Measure].

Seguendo le nostre raccomandazioni sulle best practice, l&#39;API [!DNL Marketo Measure] [!DNL Facebook] sarà in grado di:

* Applica tag automatici a tutti gli annunci [!DNL Facebook] con il parametro [!DNL Marketo Measure] di `_bf ={creative}` necessario
* Scarica informazioni sui costi degli annunci in tutti gli annunci [!DNL Facebook] attivi

>[!NOTE]
>
>Nessun modello di tracciamento per [!DNL Facebook]. L&#39;API si basa sul parametro con tag automatici (_bf) per raccogliere i dettagli dell&#39;annuncio.

**AdWords**: implementa un modello di tracciamento a livello di account e abilita l&#39;assegnazione tag automatica

[!DNL Marketo Measure] consiglia di utilizzare un modello di tracciamento a livello di account, campagna o gruppo di annunci, in quanto consente di aggiungere e sottrarre parametri per tutti gli annunci senza il rischio di interruzioni o eliminazioni della cronologia degli annunci.

Seguendo le nostre raccomandazioni sulle best practice, l&#39;API AdWords di [!DNL Marketo Measure] sarà in grado di:

* Applica tag automatici a tutti gli annunci AdWords con i parametri [!DNL Marketo Measure] di `_bk={keyword}, _bt={creative}, _bm={matchtype}, _bn={network}, _bg={adgroupID}`
* Scaricare informazioni sui costi degli annunci in tutti gli annunci AdWords attivi

**Bing**: implementa un modello di tracciamento a livello di account e abilita l&#39;assegnazione tag automatica

Non vi è alcun rischio di perdere la cronologia degli annunci durante la configurazione della connessione API [!DNL Bing], a differenza di alcune altre connessioni API.

Seguendo le nostre raccomandazioni sulle best practice, l&#39;API Bing [!DNL Marketo Measure] sarà in grado di:
* Applica tag automatici a tutti gli annunci Bing con i seguenti parametri di `_bt={adid}, utm_medium=cpc, utm_source=bing, utm_term={keyword}`
* Scaricare informazioni sui costi degli annunci in tutti gli annunci Bing attivi

**LinkedIn**: connessione con assegnazione tag automatica

L’abilitazione dell’assegnazione tag automatica ricrea una condivisione e la inserisce in un nuovo Creative, il vecchio Creative viene archiviato.

Seguendo le nostre raccomandazioni sulle best practice, l&#39;API LinkedIn [!DNL Marketo Measure] sarà in grado di:

* Applica tag automatici a tutti gli annunci LinkedIn che sono contenuti sponsorizzati di tipo di annuncio con il parametro [!DNL Marketo Measure] _bl={creativeId} necessario. Questo parametro richiama l&#39;ID creativo consentendo a [!DNL Marketo Measure] di risolvere la campagna e le informazioni creative.
* Scarica informazioni sui costi degli annunci in tutti gli annunci [!DNL LinkedIn] attivi e supportati

>[!NOTE]
>
>Nessun modello di tracciamento per [!DNL LinkedIn]. L&#39;API si basa sul parametro con tag automatici (_bl) per raccogliere tutti i possibili dettagli degli annunci.

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

Anche se seguire le nostre best practice ti proteggerà dalla perdita di dati se non sei connesso, ti consigliamo comunque di rivedere la connessione regolarmente, se possibile mensilmente. Si tratta di un semplice controllo visivo della sezione [!UICONTROL Connections] nell&#39;app [!DNL Marketo Measure] per verificare che non siano presenti icone con chiave rossa, segnalando un account disconnesso.

Quando un account connesso all&#39;API viene disconnesso, [!DNL Marketo Measure] non è in grado di estrarre i dati di spesa o di assegnare tag ai nuovi annunci. Per questo consigliamo sempre di implementare un modello di tracciamento, se possibile. Il modello assicura che, anche se l&#39;account dell&#39;annuncio viene disconnesso, [!DNL Marketo Measure] sia ancora in grado di assegnare tag agli annunci e richiamare dettagli granulari. Una volta riconnessa, i dati sulla spesa torneranno a essere disponibili e l’interruzione del reporting sui canali a pagamento sarà minima.

I motivi per la disconnessione e la riautorizzazione includono...

* Modifica della password dell&#39;account utente connesso
* Quella persona non è più in azienda
* Aggiornamenti alle API di

Se il tuo team ha sperimentato uno degli scenari di cui sopra, controlla le connessioni API nell&#39;app [!DNL Marketo Measure] per assicurarti che non debbano essere nuovamente autorizzate.

>[!MORELIKETHIS]
>
>* [Piattaforme di annunci integrate (API)](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md)
>* [Effetti degli strumenti di gestione delle offerte [!DNL Marketo Measure]](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md)
>* [[!DNL Marketo Measure] Spiegazione parametri API](/help/api-connections/utilizing-marketo-measures-api-connections/marketo-measure-parameters.md)
>* [Panoramica API Facebook](/help/api-connections/utilizing-marketo-measures-api-connections/facebook-api.md)
>* [[!DNL LinkedIn] Panoramica dell&#39;integrazione](/help/api-connections/utilizing-marketo-measures-api-connections/linkedin-integration.md)
>* [Panoramica dell&#39;integrazione AdWords](/help/api-connections/utilizing-marketo-measures-api-connections/understanding-marketo-measure-adwords-tagging.md)
>* [Autorizzazione degli account API connessi in corso](/help/api-connections/utilizing-marketo-measures-api-connections/reauthorizing-connected-accounts.md)
