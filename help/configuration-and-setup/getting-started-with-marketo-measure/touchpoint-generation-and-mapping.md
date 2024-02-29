---
unique-page-id: 18874554
description: Generazione e mappatura dei punti di contatto - [!DNL Marketo Measure]
title: Generazione e mappatura dei punti di contatto
exl-id: bb4988f5-4fbc-43b7-9544-da541b8e1d32
feature: Touchpoints
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Generazione e mappatura dei punti di contatto {#touchpoint-generation-and-mapping}

[!DNL Marketo Measure] le storie di attribuzione si basano su due processi:

* Generazione di punti di contatto, che crea punti di contatto che rappresentano le interazioni di una persona con le attività di marketing e vendita
* Mappatura dei punti di contatto, che attribuisce i punti di contatto al canale e al sottocanale appropriati

Per ottenere il massimo da [!DNL Marketo Measure], è necessario utilizzare [!DNL Marketo Measure] rep per personalizzare entrambi i processi in base alle esigenze dell&#39;organizzazione.

Metodi di generazione dei punti di contatto

Il processo di generazione dei punti di contatto risponde alla domanda: &quot;Come è [!DNL Marketo Measure] vuoi sapere che è successo?&quot; A seconda della serie di funzioni e dei tipi di interazioni che i potenziali clienti possono avere, ci sono fino a tre modi [!DNL Marketo Measure] può prendere in considerazione un’interazione e creare un punto di contatto per rappresentarla.

>[!IMPORTANT]
>
>[!DNL Marketo Measure] genera un solo punto di contatto per sessione. Se sono stati compilati più moduli, viene acquisito solo il primo modulo.

| **Tipo di interazione** | **Esempio** | **Metodo di generazione dei punti di contatto** |
|---|---|---|
| Online, sui tuoi siti | Compilazione modulo | [!DNL Marketo Measure] JavaScript |
| Non in linea; non in linea sui siti | Fiere; il partner per la diffusione dei contenuti fornisce un elenco di lead coinvolti nei contenuti | Iscrizione alla campagna CRM sincronizzata in [!DNL Marketo Measure], impostando il tipo di sincronizzazione della campagna direttamente nella campagna oppure impostando regole sulla pagina Campagne in [!DNL Marketo Measure] |
| Attività di vendita | Chiamata in uscita tramite SDR | Record attività CRM (attività o evento) sincronizzato in [!DNL Marketo Measure], tramite la logica su [!UICONTROL Activities] pagina in [!DNL Marketo Measure] |

Metodi di mappatura dei punti di contatto

Il processo di mappatura dei punti di contatto risponde alla domanda: &quot;Una volta creato questo punto di contatto, come viene [!DNL Marketo Measure] per sapere a quale canale e sottocanale appartiene?&quot; Ogni metodo di generazione dei punti di contatto ha un proprio metodo di mappatura dei punti di contatto.

| **Tipo di interazione** | **Metodo di generazione** | **Metodo di mappatura** |
|---|---|---|
| Online, sui tuoi siti | [!DNL Marketo Measure] JavaScript | Attraverso il [!DNL Online Channels] pagina in [!DNL Marketo Measure], facendo riferimento ai valori UTM, alla pagina di destinazione e alle informazioni della pagina di riferimento |
| Offline; Online, non sui tuoi siti | Sincronizzazione appartenenza campagna CRM | Attraverso il [!UICONTROL Offline Channels] pagina in [!DNL Marketo Measure], facendo riferimento al tipo di campagna |
| Attività di vendita | Sincronizzazione attività CRM | Attraverso il [!UICONTROL Online Channels] pagina in [!DNL Marketo Measure], facendo riferimento al Nome della campagna assegnato sulla [!UICONTROL Activities] pagina |

>[!MORELIKETHIS]
>
>* [Mappatura dei punti di contatto online su [!DNL Marketo Measure] Canali/Sottocanali](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
>* [Sincronizzazione delle campagne CRM da SFDC](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md)
>* [Sincronizzazione delle campagne CRM da [!DNL Marketo Measure]](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md)
>* [Mappatura delle campagne CRM su [!DNL Marketo Measure] Canali/Sottocanali](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)
>* [Creazione di punti di contatto da attività di vendita](/help/advanced-marketo-measure-features/activities-attribution/salesforce-activities-attribution.md)
>* [Domande frequenti sulle attività e mappatura dei punti di contatto delle attività su canali/sottocanali](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)

