---
unique-page-id: 18874554
description: Generazione e mapping dei punti di contatto - [!DNL Marketo Measure]
title: Generazione e mappatura dei punti di contatto
exl-id: bb4988f5-4fbc-43b7-9544-da541b8e1d32
feature: Touchpoints
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Generazione e mappatura dei punti di contatto {#touchpoint-generation-and-mapping}

Le storie di attribuzione [!DNL Marketo Measure] si basano su due processi:

* Generazione di punti di contatto, che crea punti di contatto che rappresentano le interazioni di una persona con le attività di marketing e vendita
* Mappatura dei punti di contatto, che attribuisce i punti di contatto al canale e al sottocanale appropriati

Affinché tu possa trarre il massimo da [!DNL Marketo Measure], devi collaborare con il tuo rappresentante [!DNL Marketo Measure] per personalizzare entrambi i processi in base alle esigenze della tua organizzazione.

Metodi di generazione dei punti di contatto

Il processo di generazione dei punti di contatto risponde alla domanda: &quot;Come farà [!DNL Marketo Measure] a sapere che si è verificato questo problema?&quot; A seconda della serie di funzioni e dei tipi di interazioni che i potenziali clienti possono avere, [!DNL Marketo Measure] può scegliere un&#39;interazione in tre modi e creare un punto di contatto per rappresentarla.

>[!IMPORTANT]
>
>[!DNL Marketo Measure] genera un solo punto di contatto per sessione. Se sono stati compilati più moduli, viene acquisito solo il primo modulo.

| **Tipo di interazione** | **Esempio** | **Metodo di generazione punto di contatto** |
|---|---|---|
| Online, sui tuoi siti | Compilazione modulo | [!DNL Marketo Measure] JavaScript |
| Non in linea; non in linea sui siti | Fiere; il partner per la diffusione dei contenuti fornisce un elenco di lead coinvolti nei contenuti | Appartenenza alla campagna CRM sincronizzata in [!DNL Marketo Measure], impostando il tipo di sincronizzazione della campagna direttamente nella campagna o impostando regole sulla pagina Campagne in [!DNL Marketo Measure] |
| Attività di vendita | Chiamata in uscita tramite SDR | Record attività CRM (attività o evento) sincronizzato in [!DNL Marketo Measure] tramite logica nella pagina [!UICONTROL Activities] in [!DNL Marketo Measure] |

Metodi di mappatura dei punti di contatto

Il processo di mappatura dei punti di contatto risponde alla domanda: &quot;Una volta creato questo punto di contatto, in che modo [!DNL Marketo Measure] saprà a quale canale e sottocanale appartiene?&quot; Ogni metodo di generazione dei punti di contatto ha un proprio metodo di mappatura dei punti di contatto.

| **Tipo di interazione** | **Metodo di generazione** | **Metodo di mappatura** |
|---|---|---|
| Online, sui tuoi siti | [!DNL Marketo Measure] JavaScript | Tramite la pagina [!DNL Online Channels] in [!DNL Marketo Measure], facendo riferimento ai valori UTM, alla pagina di destinazione e alle informazioni della pagina di riferimento |
| Offline; Online, non sui tuoi siti | Sincronizzazione appartenenza campagna CRM | Attraverso la pagina [!UICONTROL Offline Channels] in [!DNL Marketo Measure], facendo riferimento al tipo di campagna |
| Attività di vendita | Sincronizzazione attività CRM | Tramite la pagina [!UICONTROL Online Channels] in [!DNL Marketo Measure], facendo riferimento al nome della campagna assegnato nella pagina [!UICONTROL Activities] |

>[!MORELIKETHIS]
>
>* [Mappatura dei punti di contatto in linea a [!DNL Marketo Measure] Canali/Sottocanali](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
>* [Sincronizzazione delle campagne CRM da SFDC](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md)
>* [Sincronizzazione delle campagne CRM da [!DNL Marketo Measure]](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md)
>* [Mappatura delle campagne CRM su [!DNL Marketo Measure] Canali/Sottocanali](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)
>* [Creazione di punti di contatto dalle attività di vendita](/help/advanced-marketo-measure-features/activities-attribution/salesforce-activities-attribution.md)
>* [Domande frequenti sulle attività e mappatura dei punti di contatto delle attività su canali/sottocanali](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)

