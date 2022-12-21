---
unique-page-id: 42762628
description: Documentazione del dashboard di Passport - [!DNL Marketo Measure] - Documentazione del prodotto
title: Documentazione di Passport Dashboard
exl-id: 43cb01a8-d02e-4086-af57-d7ec9275f87a
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# Documentazione di Passport Dashboard {#passport-dashboard-documentation}

Il dashboard Passport consente agli addetti al marketing di visualizzare lead/contatti e opportunità che hanno attraversato ogni fase della pipeline in un determinato intervallo di tempo.

Questo dashboard ha due riquadri:

* Opportunità: Il numero di record Opportunità passati attraverso ogni fase durante l&#39;intervallo di tempo specificato.
* Lead/contatti: Il numero di record Lead o Contatto trasmessi attraverso ogni fase durante l&#39;intervallo di tempo specificato.

>[!NOTE]
>
>In tutte le dashboard di Discover, è possibile segnalare un solo oggetto persona, Lead o Contatto. È impostato in [!UICONTROL Settings] > [!UICONTROL Reporting] > [!UICONTROL Attribution Settings] > [!UICONTROL Default Dashboard Object].

Questo dashboard supporta i seguenti filtri (tutti i filtri si applicano a entrambi i riquadri):

* Data: selezionare l&#39;intervallo di tempo.
* Canale: filtrare i record in base ai canali. Un record è associato a un canale se uno dei suoi punti di contatto è associato al canale.
* Canale secondario: filtrare i record per sottocanali. Un record è associato a un canale secondario se uno dei suoi punti di contatto è associato al canale secondario.
* Campagna: filtrare i record in base alle campagne. Un record è associato a una campagna se uno dei relativi punti di contatto è associato alla campagna.
* Origine campagna: filtrare i record in base alle origini della campagna. Le fonti di esempio per le campagne sono Adwords, BingAds, Facebook, LinkedIn, ecc. Un record è associato a un’origine della campagna se uno dei relativi punti di contatto è associato all’origine della campagna.
* Nome account CRM: filtrare i record in base ai nomi dell&#39;account CRM.
* Filtri del segmento: filtrare i record in base ai segmenti personalizzati. Un record è associato a un segmento se uno dei suoi punti di contatto è associato al segmento.

In tutti i filtri viene utilizzata la logica &quot;AND&quot; (E).

>[!NOTE]
>
>Se un record cambia fase nella data selezionata, il record verrà conteggiato per le fasi da e a e per tutte le fasi di passaggio.

## Opportunità {#opportunities}

![](assets/one-1.png)

Gli stadi includono OC, gli stadi funnel selezionati in Stadi opportunità aperte ([!UICONTROL Settings] > [!UICONTROL CRM] > [!UICONTROL Stage Mapping]) e fasi opportunità vinte ([!UICONTROL Settings] > [!UICONTROL CRM] > [!UICONTROL Stage Mapping]).

>[!NOTE]
>
>Per gli stadi Won, i conteggi dei record sono solo per i record trasferiti nell&#39;area di visualizzazione durante l&#39;intervallo di tempo selezionato.

È possibile espandere da ogni barra per visualizzare i record Opportunità per ogni fase.

## Lead/contatti {#leads-contacts}

![](assets/two-1.png)

Le fasi includono FT, LC, le fasi funnel selezionate in fasi lead/contatti aperti sulle impostazioni - CRM - Stage Mapping, e le fasi lead/contatto convertite sulle impostazioni - CRM - Stage Mapping.

>[!NOTE]
>
>Per le aree di visualizzazione convertite, i conteggi dei record vengono utilizzati solo per i record trasferiti nell&#39;area di visualizzazione durante l&#39;intervallo di tempo selezionato.

È possibile approfondire da ogni barra i record Lead/Contatto per ogni fase.
