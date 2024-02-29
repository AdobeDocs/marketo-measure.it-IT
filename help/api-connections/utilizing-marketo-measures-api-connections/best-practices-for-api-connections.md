---
description: Best practice per le connessioni API - [!DNL Marketo Measure]
title: Best practice per le connessioni API
exl-id: b8550e4e-a567-427f-b5d3-50232553a066
feature: APIs, Integration
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 0%

---

# Best practice per le connessioni API {#best-practices-for-api-connections}

## Panoramica {#overview}

[!DNL Marketo Measure] offre connessioni API con [!DNL Google AdWords], [!DNL Microsoft Bing Ads], [!DNL Facebook Ads]e LinkedIn. Queste connessioni API abilitano [!DNL Marketo Measure] per estrarre una varietà di dati dalle piattaforme pubblicitarie che possono poi essere riportati nei dati dei punti di contatto dell&#39;acquirente. Una caratteristica chiave di queste connessioni API è la capacità di richiamare automaticamente i dati di spesa, risparmiando a te e al tuo team il tempo e l’impegno necessari per caricare manualmente i dati per il reporting del ROI. La configurazione di queste connessioni API non è obbligatoria per [!DNL Marketo Measure] per tenere traccia di tali canali, ma forniscono dettagli granulari che migliorano i rapporti.

Il [!DNL Marketo Measure] Le connessioni API sono un aspetto prezioso del tuo account e le nostre raccomandazioni sulle best practice aiuteranno te e il tuo team a utilizzare al massimo le nostre connessioni.

## Best practice {#best-practice}

Indipendentemente dalla piattaforma pubblicitaria che stai connettendo, le seguenti linee guida sono importanti da tenere a mente.

* Usa un amministratore per la connessione
* Puoi collegare più account di annunci per una piattaforma
* Connetti tutti i possibili account annuncio per automatizzare il più possibile la generazione di rapporti sulla spesa
* Se disponibile, implementa sempre un modello di tracciamento. Il modello garantisce che, anche se l’account dell’annuncio viene disconnesso, [!DNL Marketo Measure] è ancora in grado di richiamare i dettagli granulari degli annunci

Per ottimizzare ogni [!DNL Marketo Measure] API, attieniti alle seguenti best practice.

**[!DNL Facebook]**: connessione con assegnazione tag automatica

Prima di abilitare l’assegnazione tag automatica, esporta la cronologia degli annunci in un file CSV. L’abilitazione dell’assegnazione tag automatica reimposterà la cronologia delle conversioni e la bozza social di tutti gli annunci taggati da [!DNL Marketo Measure].

Seguendo le nostre raccomandazioni sulle best practice, [!DNL Marketo Measure] [!DNL Facebook] L’API sarà in grado di:

* Assegna tag automatici a tutti [!DNL Facebook] Annunci con il necessario [!DNL Marketo Measure] parametro `_bf ={creative}`
* Scaricare informazioni sui costi degli annunci in tutti i siti attivi [!DNL Facebook] annunci

>[!NOTE]
>
>Non esiste un modello di tracciamento per [!DNL Facebook], l’API si basa sul parametro con tag automatici (_bf) per raccogliere i dettagli dell’annuncio.

**AdWords**: implementa un modello di tracciamento a livello di account e abilita l’assegnazione tag automatica

[!DNL Marketo Measure] consiglia di utilizzare un modello di tracciamento a livello di account, campagna o gruppo di annunci, in quanto consente di aggiungere e sottrarre parametri per tutti gli annunci senza il rischio di interruzioni o eliminazioni della cronologia degli annunci.

Seguendo le nostre raccomandazioni sulle best practice, [!DNL Marketo Measure] L’API di AdWords sarà in grado di:

* Applica tag automatici a tutti gli annunci AdWords con il [!DNL Marketo Measure] parametri di `_bk={keyword}, _bt={creative}, _bm={matchtype}, _bn={network}, _bg={adgroupID}`
* Scaricare informazioni sui costi degli annunci in tutti gli annunci AdWords attivi

**Bing**: implementa un modello di tracciamento a livello di account e abilita l’assegnazione tag automatica

Non c’è rischio di perdere la cronologia degli annunci durante la configurazione [!DNL Bing] connessione API, a differenza di alcune delle altre connessioni API.

Seguendo le nostre raccomandazioni sulle best practice, [!DNL Marketo Measure] L’API Bing sarà in grado di:
* Applica tag automatici a tutti gli annunci Bing con i seguenti parametri di `_bt={adid}, utm_medium=cpc, utm_source=bing, utm_term={keyword}`
* Scaricare informazioni sui costi degli annunci in tutti gli annunci Bing attivi

**LinkedIn**: connessione con assegnazione tag automatica

L’attivazione dell’assegnazione tag automatica ricrea una Condivisione e la inserisce in una nuova Creativa, la vecchia Creativa viene archiviata.

Seguendo le nostre raccomandazioni sulle best practice, [!DNL Marketo Measure] L’API di linkedIn sarà in grado di:

* Applica tag automatici a tutti gli annunci LinkedIn che sono contenuti sponsorizzati di tipo annuncio con il necessario [!DNL Marketo Measure] parametro _bl={creativeId}. Questo parametro richiama l’ID creativo consentendo [!DNL Marketo Measure] per risolvere la campagna e le informazioni creative.
* Scaricare informazioni sui costi in tutti i sistemi attivi e supportati [!DNL LinkedIn] annunci

>[!NOTE]
>
>Non esiste un modello di tracciamento per [!DNL LinkedIn], l’API si basa sul parametro con tag automatici (_bl) per raccogliere tutti i possibili dettagli dell’annuncio.

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

Anche se seguire le nostre best practice ti proteggerà dalla perdita di dati se non sei connesso, ti consigliamo comunque di rivedere la connessione regolarmente, se possibile mensilmente. Questo è un semplice controllo visivo del [!UICONTROL Connections] sezione nel tuo [!DNL Marketo Measure] app per verificare che non siano presenti icone a forma di chiave rossa, che segnalano un account disconnesso.

Quando un account API connesso viene disconnesso, [!DNL Marketo Measure] non è in grado di estrarre i dati di spesa in o di assegnare tag ai nuovi annunci. Per questo consigliamo sempre di implementare un modello di tracciamento, se possibile. Il modello garantisce che, anche se l’account dell’annuncio viene disconnesso, [!DNL Marketo Measure] è ancora in grado di assegnare tag agli annunci e richiamare dettagli granulari. Una volta riconnessa, i dati sulla spesa torneranno a essere disponibili e l’interruzione del reporting sui canali a pagamento sarà minima.

I motivi per la disconnessione e la riautorizzazione includono...

* Modifica della password dell&#39;account utente connesso
* Quella persona non è più in azienda
* Aggiornamenti alle API di

Se il tuo team ha sperimentato uno degli scenari sopra riportati, controlla le connessioni API in [!DNL Marketo Measure] per assicurarsi che non debbano essere nuovamente autorizzate.

>[!MORELIKETHIS]
>
>* [Piattaforme di annunci integrate (API)](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md)
>* [Effetti degli strumenti di gestione delle offerte [!DNL Marketo Measure]](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md)
>* [[!DNL Marketo Measure] Spiegazione dei parametri API](/help/api-connections/utilizing-marketo-measures-api-connections/marketo-measure-parameters.md)
>* [Panoramica API di facebook](/help/api-connections/utilizing-marketo-measures-api-connections/facebook-api.md)
>* [[!DNL LinkedIn] Panoramica dell’integrazione](/help/api-connections/utilizing-marketo-measures-api-connections/linkedin-integration.md)
>* [Panoramica dell’integrazione di AdWords](/help/api-connections/utilizing-marketo-measures-api-connections/understanding-marketo-measure-adwords-tagging.md)
>* [Autorizzazione di nuovo account API connessi](/help/api-connections/utilizing-marketo-measures-api-connections/reauthorizing-connected-accounts.md)
