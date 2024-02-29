---
unique-page-id: 42762628
description: Documentazione di Passport Dashboard - [!DNL Marketo Measure]
title: Documentazione di Passport Dashboard
exl-id: 43cb01a8-d02e-4086-af57-d7ec9275f87a
feature: Reporting
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# Documentazione di Passport Dashboard {#passport-dashboard-documentation}

Il dashboard Passport consente agli addetti al marketing di visualizzare lead/contatti e opportunità che hanno attraversato ogni fase della pipeline durante un determinato intervallo di tempo.

Questo dashboard ha due sezioni:

* Opportunità: il numero di record Opportunità passati attraverso ogni fase durante il periodo di tempo specificato.
* Lead/Contatti: il numero di record Lead o Contatto passati in ogni fase durante il periodo di tempo specificato.

>[!NOTE]
>
>In tutti i dashboard di individuazione è possibile segnalare un solo oggetto persona, lead o contatto. Questo è impostato in [!UICONTROL Settings] > [!UICONTROL Reporting] > [!UICONTROL Attribution Settings] > [!UICONTROL Default Dashboard Object].

Questo dashboard supporta i seguenti filtri (tutti i filtri si applicano a entrambe le tessere):

* Data: seleziona l’intervallo di tempo.
* Canale: filtra i record in base ai canali. Un record è associato a un canale se uno qualsiasi dei suoi punti di contatto è associato al canale.
* Sottocanale: filtra i record per sottocanali. Un record è associato a un sottocanale se uno qualsiasi dei suoi punti di contatto è associato al sottocanale.
* Campagna: filtra i record per campagne. Un record è associato a una campagna se uno qualsiasi dei suoi punti di contatto è associato alla campagna.
* Origine campagna: filtra i record per origini campagna. Le origini della campagna di esempio sono AdWords, BingAds, Facebook, LinkedIn ecc. Un record è associato a un’origine della campagna se uno qualsiasi dei suoi punti di contatto è associato all’origine della campagna.
* Nome account CRM: filtra i record in base ai nomi account CRM.
* Filtri di segmenti: filtra i record per segmenti personalizzati. Un record è associato a un segmento se uno qualsiasi dei suoi punti di contatto è associato al segmento.

In tutti i filtri, viene utilizzata la logica &quot;AND&quot;.

>[!NOTE]
>
>Se un record cambia fase alla data selezionata, il record verrà conteggiato per le fasi da e a e per tutte le fasi di pass-through.

## Opportunità {#opportunities}

![](assets/one-1.png)

Gli stadi includono OC, gli stadi funnel selezionati negli stadi dell&#39;opportunità aperta ([!UICONTROL Settings] > [!UICONTROL CRM] > [!UICONTROL Stage Mapping]) e le fasi dell’opportunità acquisita ([!UICONTROL Settings] > [!UICONTROL CRM] > [!UICONTROL Stage Mapping]).

>[!NOTE]
>
>Per gli stadi Won, i conteggi dei record sono solo per i record sottoposti a transizione nello stadio durante l’intervallo di tempo selezionato.

È possibile eseguire un drill-down da ogni barra per visualizzare i record Opportunità per ogni fase.

## Lead/Contatti {#leads-contacts}

![](assets/two-1.png)

Gli stadi includono FT, LC, stadi funnel selezionati in stadi lead/contatto aperti in Impostazioni - CRM - Mappatura stadio e stadi lead/contatto convertiti in Impostazioni - CRM - Mappatura stadio.

>[!NOTE]
>
>Per gli stadi convertiti, i conteggi dei record sono solo per i record sottoposti a transizione nello stadio durante l’intervallo di tempo selezionato.

È possibile eseguire un drill-down da ogni barra per visualizzare i record Lead/Contatto per ogni fase.
