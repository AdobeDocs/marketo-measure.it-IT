---
unique-page-id: 42762600
description: Documentazione di Snapshot Dashboard - [!DNL Marketo Measure]
title: Documentazione di Snapshot Dashboard
exl-id: 4dfc92d2-ccab-4726-a869-3ae32aa89a5f
feature: Reporting
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Documentazione di Snapshot Dashboard {#snapshot-dashboard-documentation}

Il dashboard delle istantanee consente di visualizzare lo stato del CRM in un determinato momento, con la distribuzione dei record nelle fasi Lead/Contatto e Opportunità.

Questo dashboard ha due sezioni:

* **Snapshot lead/contatto:** Il numero di record Lead o Contatto in ogni fase alla data selezionata.

>[!NOTE]
>
>In tutti i dashboard di individuazione è possibile segnalare un solo oggetto persona, lead o contatto. Questo è impostato in [!UICONTROL Settings] > [!UICONTROL Reporting] > [!UICONTROL Attribution Settings] > [!UICONTROL Default Dashboard Object].

* **Snapshot opportunità:** Il numero di record Opportunità in ogni fase alla data selezionata.

Questo dashboard supporta i seguenti filtri (tutti i filtri si applicano a entrambe le tessere):

* Data snapshot: selezionare la data dell&#39;snapshot.
* ID/nome account CRM: filtra i record in base agli ID o ai nomi degli account CRM.

>[!NOTE]
>
>I suggerimenti mostrano solo i nomi.

* Canale: filtra i record in base ai canali. Un record è associato a un canale se uno qualsiasi dei suoi punti di contatto è associato al canale.
* Sottocanale: filtra i record per sottocanali. Un record è associato a un sottocanale se uno qualsiasi dei suoi punti di contatto è associato al sottocanale.
* Campagna: filtra i record per campagne. Un record è associato a una campagna se uno qualsiasi dei suoi punti di contatto è associato alla campagna.
* Origine campagna: filtra i record per origini campagna. Le origini della campagna di esempio sono [!DNL Adwords], [!DNL BingAds], [!DNL Facebook], [!DNL LinkedIn], ecc. Un record è associato a un’origine della campagna se uno qualsiasi dei suoi punti di contatto è associato all’origine della campagna.
* ID/nome account annuncio: filtra i record in base agli ID o ai nomi dell’account annuncio. Un record è associato a un account annuncio se uno qualsiasi dei suoi punti di contatto è associato a una campagna dagli account annuncio selezionati.

>[!NOTE]
>
>Suggerimento per mostrare solo i nomi.

* Filtri di segmenti: filtra i record per segmenti personalizzati. Un record è associato a un segmento se uno qualsiasi dei suoi punti di contatto è associato al segmento.

In tutti i filtri, viene utilizzata la logica &quot;AND&quot;.

>[!NOTE]
>
>Se un record cambia fase alla data selezionata, il record verrà conteggiato per le fasi da e a e per tutte le fasi di pass-through.

## Snapshot contatti/lead {#lead-contact-snapshot}

![](assets/one.png)

Gli stadi includono FT, LC e Funnel selezionati negli stadi lead/contatto aperti ([!UICONTROL Settings] > [!UICONTROL CRM] > [!UICONTROL Stage Mapping]).

È possibile eseguire un drill-down da ogni barra per visualizzare i record Lead/Contatto per ogni fase.

## Snapshot opportunità {#opportunity-snapshot}

![](assets/two.png)

Gli stadi includono FT, LC, stadi funnel selezionati in stadi lead/contatto aperti ([!UICONTROL Settings] > [!UICONTROL CRM] > [!UICONTROL Stage Mapping]). E fasi OC e Funnel selezionate in fasi opportunità aperte ([!UICONTROL Settings] > [!UICONTROL CRM] > [!UICONTROL Stage Mapping]).

È possibile eseguire un drill-down da ogni barra per visualizzare i record Opportunità per ogni fase.
