---
unique-page-id: 18874747
description: Aggiunta [!DNL Marketo Measure] Script per pagine Sitecore - [!DNL Marketo Measure]
title: Aggiunta [!DNL Marketo Measure] Script per pagine Sitecore
exl-id: 87ce1857-7532-45a7-8c39-255c6118b50a
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] Script per pagine Sitecore {#adding-marketo-measure-script-to-sitecore-pages}

I sistemi di gestione dei contenuti possono richiedere ulteriori passaggi oltre l&#39;implementazione di script standard per [!DNL Marketo Measure] per riconoscere gli invii di moduli. Il processo seguente illustra come aggiungere [!DNL Marketo Measure] javascript nel tuo [!DNL Sitecore] pagine.

Per i siti con pagine Sitecore:

1. Accedi a Sitecore e naviga sul tuo sito web. Individua il [!UICONTROL Configuration] cartella che si trova sullo stesso livello della cartella [!UICONTROL Home] elemento e [!UICONTROL Metadata] cartella.
1. Fai clic su **[!UICONTROL +]** accanto al [!UICONTROL Configuration] cartella.
1. Fai clic su **[!UICONTROL +]** accanto al [!UICONTROL Tools] cartella.
1. Seleziona la [!UICONTROL Javascript] elemento.
1. In [!UICONTROL Content] , fare clic sulla scheda **[!UICONTROL Lock and Edit]** collegamento per sbloccare l&#39;elemento per la modifica.
1. Trova il [!UICONTROL 'JavaScript'] sezione. Se non è già espanso, fare clic su **[!UICONTROL +]**.
1. Inserisci il nostro script: `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js"async=""></script>`
1. Clic **[!UICONTROL Save]** nell’angolo superiore sinistro.
