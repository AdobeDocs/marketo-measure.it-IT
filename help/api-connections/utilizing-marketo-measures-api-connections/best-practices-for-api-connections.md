---
description: Tecniche consigliate per le connessioni API - [!DNL Marketo Measure] - Documentazione del prodotto
title: Tecniche consigliate per le connessioni API
exl-id: b8550e4e-a567-427f-b5d3-50232553a066
source-git-commit: 65e7f8bc198ceba2f873ded23c94601080ad0546
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Tecniche consigliate per le connessioni API {#best-practices-for-api-connections}

## Panoramica {#overview}

[!DNL Marketo Measure] offre connessioni API con [!DNL Google AdWords], [!DNL Microsoft Bing Ads], [!DNL Facebook Ads]e LinkedIn. Queste connessioni API attivano [!DNL Marketo Measure] per estrarre una varietà di dati dalle piattaforme di annunci che possono essere successivamente segnalati nei dati del punto di contatto dell’acquirente. Una caratteristica chiave di queste connessioni API è la loro capacità di estrarre i dati automaticamente, risparmiando a te e al tuo team il tempo e lo sforzo necessari per caricare manualmente i dati per il reporting sul ROI. L’impostazione di queste connessioni API non è obbligatoria per [!DNL Marketo Measure] per tenere traccia di tali canali, ma forniscono dettagli granulari utili che migliorano il reporting.

La [!DNL Marketo Measure] Le connessioni API sono un aspetto prezioso del tuo account e i nostri consigli sulle best practice ti aiuteranno a utilizzare al meglio le nostre connessioni con il tuo team.

## Best practice {#best-practice}

Indipendentemente dalla piattaforma di annunci che stai connettendo, le seguenti linee guida sono importanti da tenere a mente!

* Utilizzare un amministratore per connettersi
* Puoi collegare più account di annunci per una piattaforma
* Connetti tutti gli account di annunci possibili per automatizzare il più possibile il reporting delle spese
* Se disponibile, implementa sempre un modello di tracciamento. Il modello assicura che anche se l’account dell’annuncio viene disconnesso, [!DNL Marketo Measure] è ancora in grado di estrarre dettagli di annunci granulari

Per ottimizzare [!DNL Marketo Measure] API, segui le seguenti best practice.

**[!DNL Facebook]**: Connetti con assegnazione tag automatica

Prima di abilitare l’assegnazione tag automatica, esporta la cronologia degli annunci in un CSV. L’abilitazione dell’assegnazione tag automatica reimposta la cronologia delle conversioni e la prova social di tutti gli annunci con tag [!DNL Marketo Measure].

Seguendo la raccomandazione sulle best practice, la [!DNL Marketo Measure] [!DNL Facebook] L’API sarà in grado di:

* Etichetta automatica tutto [!DNL Facebook] Annunci con il necessario [!DNL Marketo Measure] parameter `_bf ={creative}`
* Scarica le informazioni sui costi degli annunci in tutte le aree attive [!DNL Facebook] annunci

>[!NOTE]
>
>Non esiste un modello di tracciamento per [!DNL Facebook], l’API si basa sul parametro con tag automatico (_bf) per raccogliere i dettagli dell’annuncio.

**AdWords**: Implementa un modello di tracciamento a livello di account e abilita l’assegnazione automatica dei tag

[!DNL Marketo Measure] consiglia di utilizzare un modello di tracciamento a livello di account, di campagna o di gruppo di annunci, in quanto consente l’aggiunta e la sottrazione di parametri per tutti gli annunci senza il rischio di interruzioni o cancellazione della cronologia annunci.

Seguendo la raccomandazione sulle best practice, la [!DNL Marketo Measure] L’API di AdWords sarà in grado di:

* Assegnare automaticamente tag a tutti gli annunci AdWords con il tag [!DNL Marketo Measure] parametri di `_bk={keyword}, _bt={creative}, _bm={matchtype}, _bn={network}, _bg={adgroupID}`
* Scarica informazioni sui costi degli annunci in tutti gli annunci AdWords attivi

**Bing**: Implementa un modello di tracciamento a livello di account e abilita l’assegnazione automatica dei tag

Non c&#39;è alcun rischio di perdere la cronologia degli annunci durante la configurazione del tuo [!DNL Bing] Connessione API, a differenza di altre connessioni API.

Seguendo la raccomandazione sulle best practice, la [!DNL Marketo Measure] L’API Bing sarà in grado di:
* Assegnare automaticamente tag a tutti gli annunci Bing con i seguenti parametri di `_bt={adid}, utm_medium=cpc, utm_source=bing, utm_term={keyword}`
* Scarica le informazioni sui costi degli annunci in tutti gli annunci Bing attivi

**linkedIn**: Connetti con assegnazione tag automatica

Se abiliti l’assegnazione automatica dei tag, viene ricreato una condivisione e la inserisce in un nuovo creativo, il vecchio creativo viene archiviato.

Seguendo la raccomandazione sulle best practice, la [!DNL Marketo Measure] L’API linkedIn sarà in grado di:

* Assegnare automaticamente tag a tutti gli annunci LinkedIn che sono di tipo annuncio Contenuto sponsorizzato con il necessario [!DNL Marketo Measure] parametro _bl={creativeId}. Questo parametro effettua il pull in ID creativo consentendo [!DNL Marketo Measure] per risolvere la campagna e le informazioni creative.
* Scaricare informazioni sui costi degli annunci in tutte le aree attive e supportate [!DNL LinkedIn] annunci

>[!NOTE]
>
>Non esiste un modello di tracciamento per [!DNL LinkedIn], l’API si basa sul parametro con tag automatico (_bl) per raccogliere tutti i dettagli di annunci possibili.

## Best practice per la manutenzione {#best-practice-for-maintenance}

Seguendo le nostre best practice potrai evitare la perdita di dati se disconnesso, ti consigliamo comunque di rivedere la connessione regolarmente, mensilmente se possibile. Questo è un semplice controllo visivo del [!UICONTROL Connections] nella sezione [!DNL Marketo Measure] app per assicurarti che non siano presenti icone di chiave rossa, segnalando un account disconnesso.

Quando un account connesso API viene disconnesso, [!DNL Marketo Measure] non è in grado di estrarre i dati di spesa in o di assegnare tag a nuovi annunci. Per questo motivo, se possibile, consigliamo sempre di implementare un modello di tracciamento. Il modello assicura che anche se l’account dell’annuncio viene disconnesso, [!DNL Marketo Measure] è ancora in grado di assegnare tag agli annunci e inserire dettagli di annunci granulari. Una volta riconnessa, i dati di spesa verranno nuovamente compilati e l&#39;interruzione del reporting del canale a pagamento è minima.

I motivi della disconnessione e della riautorizzazione includono...

* Modifica della password dell&#39;account utente connesso
* Quella persona non è più nell&#39;azienda
* Aggiornamenti alle API

Se il tuo team ha sperimentato uno degli scenari di cui sopra, controlla le tue connessioni API nella [!DNL Marketo Measure] per assicurarti che non debbano essere nuovamente autorizzati.

>[!MORELIKETHIS]
>
>* [Piattaforme di annunci integrate (API)](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md)
>* [Effetti degli strumenti di gestione delle offerte [!DNL Marketo Measure]](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md)
>* [[!DNL Marketo Measure] Spiegazione dei parametri API](/help/api-connections/utilizing-marketo-measures-api-connections/marketo-measure-parameters.md)
>* [Panoramica API di facebook](/help/api-connections/utilizing-marketo-measures-api-connections/facebook-api.md)
>* [[!DNL LinkedIn] Panoramica dell’integrazione](/help/api-connections/utilizing-marketo-measures-api-connections/linkedin-integration.md)
>* [Panoramica dell’integrazione di AdWords](/help/api-connections/utilizing-marketo-measures-api-connections/understanding-marketo-measure-adwords-tagging.md)
>* [Riautorizzazione degli account API collegati](/help/api-connections/utilizing-marketo-measures-api-connections/reauthorizing-connected-accounts.md)

