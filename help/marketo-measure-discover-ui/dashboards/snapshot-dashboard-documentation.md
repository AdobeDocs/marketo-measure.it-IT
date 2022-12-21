---
unique-page-id: 42762600
description: Documentazione del dashboard di snapshot - [!DNL Marketo Measure] - Documentazione del prodotto
title: Documentazione del dashboard di snapshot
exl-id: 4dfc92d2-ccab-4726-a869-3ae32aa89a5f
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Documentazione del dashboard di snapshot {#snapshot-dashboard-documentation}

Il dashboard snapshot ti consente di visualizzare lo stato del CRM in un determinato momento, con la distribuzione dei record tra le fasi Lead/Contatto e Opportunità.

Questo dashboard ha due riquadri:

* **Istantanea lead/contatto:** Numero di record Lead o Contatto in ogni fase della data selezionata.

>[!NOTE]
>
>In tutte le dashboard di Discover, è possibile segnalare un solo oggetto persona, Lead o Contatto. È impostato in [!UICONTROL Settings] > [!UICONTROL Reporting] > [!UICONTROL Attribution Settings] > [!UICONTROL Default Dashboard Object].

* **Snapshot opportunità:** Il numero di record Opportunità in ogni fase della data selezionata.

Questo dashboard supporta i seguenti filtri (tutti i filtri si applicano a entrambi i riquadri):

* Data snapshot: selezionare la data dello snapshot.
* ID/nome account CRM: filtrare i record in base agli ID o ai nomi dell&#39;account CRM.

>[!NOTE]
>
>I suggerimenti mostrano solo nomi.

* Canale: filtrare i record in base ai canali. Un record è associato a un canale se uno dei suoi punti di contatto è associato al canale.
* Canale secondario: filtrare i record per sottocanali. Un record è associato a un canale secondario se uno dei suoi punti di contatto è associato al canale secondario.
* Campagna: filtrare i record in base alle campagne. Un record è associato a una campagna se uno dei relativi punti di contatto è associato alla campagna.
* Origine campagna: filtrare i record in base alle origini della campagna. Esempio di origini di campagne [!DNL Adwords], [!DNL BingAds], [!DNL Facebook], [!DNL LinkedIn], ecc. Un record è associato a un’origine della campagna se uno dei relativi punti di contatto è associato all’origine della campagna.
* Nome/ID account dell’annuncio: Filtrare i record in base agli ID o ai nomi dell’account annuncio. Un record è associato a un account annuncio se uno dei suoi punti di contatto è associato a una campagna dagli account annuncio selezionati.

>[!NOTE]
>
>I suggerimenti mostrano solo i nomi.

* Filtri del segmento: filtrare i record in base ai segmenti personalizzati. Un record è associato a un segmento se uno dei suoi punti di contatto è associato al segmento.

In tutti i filtri viene utilizzata la logica &quot;AND&quot; (E).

>[!NOTE]
>
>Se un record cambia fase nella data selezionata, il record verrà conteggiato per le fasi da e a e per tutte le fasi di passaggio.

## Istantanea lead/contatto {#lead-contact-snapshot}

![](assets/one.png)

Le fasi includono le fasi FT, LC e funnel selezionati in fasi di lead/contatti aperti ([!UICONTROL Settings] > [!UICONTROL CRM] > [!UICONTROL Stage Mapping]).

È possibile approfondire da ogni barra i record Lead/Contatto per ogni fase.

## Snapshot opportunità {#opportunity-snapshot}

![](assets/two.png)

Le fasi includono FT, LC, le fasi funnel selezionate in fase di lead/contatti aperti ([!UICONTROL Settings] > [!UICONTROL CRM] > [!UICONTROL Stage Mapping]). E OC e le fasi funnel selezionate nelle fasi di apertura opportunità ([!UICONTROL Settings] > [!UICONTROL CRM] > [!UICONTROL Stage Mapping]).

È possibile espandere da ogni barra per visualizzare i record Opportunità per ogni fase.
