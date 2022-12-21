---
unique-page-id: 18874554
description: Generazione e mappatura di punti di contatto - [!DNL Marketo Measure] - Documentazione del prodotto
title: Generazione e mappatura di punti di contatto
exl-id: bb4988f5-4fbc-43b7-9544-da541b8e1d32
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# Generazione e mappatura di punti di contatto {#touchpoint-generation-and-mapping}

[!DNL Marketo Measure] le storie di attribuzione si basano su due processi:

* Generazione di punti di contatto, che crea punti di contatto che rappresentano le interazioni di una persona con le attività di marketing e di vendita
* Mappatura dei punti di contatto, che attribuisce i punti di contatto al canale e al canale secondario appropriati

Per ottenere il massimo da [!DNL Marketo Measure], dovresti lavorare con [!DNL Marketo Measure] per personalizzare entrambi i processi in base alle esigenze della tua organizzazione.

Metodi di generazione dei punti di contatto

Il processo di generazione dei punti di contatto risponde alla domanda, &quot;Com&#39;è [!DNL Marketo Measure] per sapere che è successo?&quot; A seconda del set di funzioni e dei tipi di interazioni che i potenziali clienti possono avere, sono disponibili fino a tre modi [!DNL Marketo Measure] è in grado di rilevare un’interazione e creare un punto di contatto per rappresentarla.

| **Tipo di interazione** | **Esempio** | **Metodo di generazione punto di contatto** |
|---|---|---|
| Online, sul sito | Compilazione modulo | [!DNL Marketo Measure] JavaScript |
| Non in linea; Non online sul sito o sui siti | fiere commerciali; Il partner di sindacazione dei contenuti fornisce un elenco di lead che si occupano dei contenuti | Iscrizione alla campagna CRM sincronizzata con [!DNL Marketo Measure], impostando il Tipo di sincronizzazione campagna direttamente nella campagna o impostando le regole nella pagina Campagne in [!DNL Marketo Measure] |
| Attività di vendita | Chiamata in uscita da SDR | Record dell’attività CRM (attività o evento) sincronizzato in [!DNL Marketo Measure], attraverso la logica [!UICONTROL Activities] in [!DNL Marketo Measure] |

Metodi di mappatura dei punti di contatto

Il processo di mappatura dei punti di contatto risponde alla domanda: &quot;Una volta creato questo punto di contatto, come sta [!DNL Marketo Measure] per sapere a quale canale e canale appartiene?&quot; Ogni metodo di generazione dei punti di contatto ha un proprio metodo di mappatura dei punti di contatto.

| **Tipo di interazione** | **Metodo di generazione** | **Metodo di mappatura** |
|---|---|---|
| Online, sul sito | [!DNL Marketo Measure] JavaScript | Attraverso il [!DNL Online Channels] in [!DNL Marketo Measure], facendo riferimento a valori UTM, pagina di destinazione e informazioni sulla pagina di riferimento |
| Non in linea; Online, non sul sito | Sincronizzazione dell&#39;appartenenza alla campagna di gestione delle relazioni con i clienti | Attraverso il [!UICONTROL Offline Channels] in [!DNL Marketo Measure], facendo riferimento al tipo di campagna |
| Attività di vendita | Sincronizzazione attività CRM | Attraverso il [!UICONTROL Online Channels] in [!DNL Marketo Measure], facendo riferimento al nome della campagna assegnato nel [!UICONTROL Activities] page |

>[!MORELIKETHIS]
>
>* [Mappatura di punti di contatto online su [!DNL Marketo Measure] Canali/Sottocanali](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
>* [Sincronizzazione delle campagne CRM dall&#39;interno di SFDC](/help/channel-tracking-and-setup/offline-channels/syncing-offline-campaigns.md)
>* [Sincronizzazione delle campagne CRM da [!DNL Marketo Measure]](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md)
>* [Mappatura di campagne CRM su [!DNL Marketo Measure] Canali/Sottocanali](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)
>* [Creazione di punti di contatto dalle attività di vendita](/help/advanced-marketo-measure-features/activities-attribution/salesforce-activities-attribution.md)
>* [Domande frequenti sulle attività e mappatura di attività Punti di contatto su Canali/Sottocanali](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)


