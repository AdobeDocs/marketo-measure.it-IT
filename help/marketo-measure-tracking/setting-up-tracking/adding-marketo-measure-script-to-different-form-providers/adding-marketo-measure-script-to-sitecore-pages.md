---
unique-page-id: 18874747
description: Aggiunta di  [!DNL Marketo Measure] script alle pagine Sitecore in corso - [!DNL Marketo Measure]
title: Aggiunta di  [!DNL Marketo Measure] script alle pagine Sitecore
exl-id: 87ce1857-7532-45a7-8c39-255c6118b50a
feature: Tracking
TQID: https://experienceleague.adobe.com/sXO-rCY3NbxX0AztYt-o3f-tpJFlrncLIb7-NvEjZO0
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 9ceb54139bfa9b6ce7c2c5fbb4e25e649f5708a3
workflow-type: tm+mt
source-wordcount: 114
ht-degree: 0%

---

# Aggiunta dello script [!DNL Marketo Measure] alle pagine Sitecore {#adding-marketo-measure-script-to-sitecore-pages}

I sistemi di gestione dei contenuti possono richiedere ulteriori passaggi oltre l&#39;implementazione dello script standard per il riconoscimento degli invii di moduli da parte di [!DNL Marketo Measure]. Il processo seguente illustra come aggiungere JavaScript [!DNL Marketo Measure] alle pagine [!DNL Sitecore].

Per i siti con pagine Sitecore:

1. Accedi a Sitecore e naviga sul tuo sito web. Individuare la cartella [!UICONTROL Configuration] che si trova sullo stesso livello dell&#39;elemento [!UICONTROL Home] e della cartella [!UICONTROL Metadata].
1. Fare clic su **[!UICONTROL +]** accanto alla cartella [!UICONTROL Configuration].
1. Fare clic su **[!UICONTROL +]** accanto alla cartella [!UICONTROL Tools].
1. Selezionare l&#39;elemento [!UICONTROL Javascript].
1. Nella scheda [!UICONTROL Content], fare clic sul collegamento **[!UICONTROL Lock and Edit]** per sbloccare l&#39;elemento per la modifica.
1. Trovare la sezione [!UICONTROL 'JavaScript']. Se non è già espanso, fare clic su **[!UICONTROL +]**.
1. Immetti lo script: `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js"async=""></script>`
1. Fare clic su **[!UICONTROL Save]** nell&#39;angolo superiore sinistro.
