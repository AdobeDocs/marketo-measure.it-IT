---
unique-page-id: 18874747
description: Aggiunta [!DNL Marketo Measure] Script per le pagine del sito - [!DNL Marketo Measure] - Documentazione del prodotto
title: Aggiunta [!DNL Marketo Measure] Script per memorizzare le pagine
exl-id: 87ce1857-7532-45a7-8c39-255c6118b50a
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] Script per memorizzare le pagine {#adding-marketo-measure-script-to-sitecore-pages}

I sistemi di gestione dei contenuti possono richiedere passaggi aggiuntivi oltre all’implementazione standard degli script per [!DNL Marketo Measure] per riconoscere gli invii dei moduli. Il processo seguente illustra come aggiungere il [!DNL Marketo Measure] javascript al tuo [!DNL Sitecore] pagine.

Per siti con pagine di Sitecore:

1. Accedi al tuo sito web e naviga al tuo sito web. Individua il [!UICONTROL Configuration] cartella che si trova sullo stesso livello della [!UICONTROL Home] articolo e [!UICONTROL Metadata] cartella.
1. Fai clic sul pulsante **[!UICONTROL +]** accanto al [!UICONTROL Configuration] cartella.
1. Fai clic sul pulsante **[!UICONTROL +]** accanto al [!UICONTROL Tools] cartella.
1. Seleziona la [!UICONTROL Javascript] oggetto.
1. In [!UICONTROL Content] fai clic sulla scheda **[!UICONTROL Lock and Edit]** collegamento per sbloccare l’elemento per la modifica.
1. Trova il [!UICONTROL 'JavaScript'] sezione . Se non è già espanso, fai clic sul pulsante **[!UICONTROL +]**.
1. Inserisci il nostro script: `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js"async=""></script>`
1. Fai clic su **[!UICONTROL Save]** nell&#39;angolo in alto a sinistra.
