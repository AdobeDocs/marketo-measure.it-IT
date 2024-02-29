---
unique-page-id: 18874743
description: Connessione [!DNL Marketo Measure] per annullare la remissione di Script Manager - [!DNL Marketo Measure]
title: Connessione [!DNL Marketo Measure] per annullare la remissione di Script Manager
exl-id: c3212bc3-1d8f-4da5-bb2d-11ffd2fb4e98
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Connessione [!DNL Marketo Measure] per annullare la remissione di Script Manager {#connecting-marketo-measure-to-unbounce-script-manager}

[!DNL Marketo Measure] si integra direttamente con Unbounce, consentendoti di tenere traccia dell’origine di marketing digitale delle conversioni della pagina di destinazione direttamente in [!DNL Salesforce]. Per effettuare la connessione, aggiungi semplicemente [!DNL Marketo Measure] script per Unbounce Script Manager. Ecco come.

1. Accedi al tuo [!DNL Unbounce] account.
1. Clic **[!UICONTROL Settings]** > **[!UICONTROL Script Manager]** > **[!UICONTROL Add Script]**.
1. Nel popup, seleziona [!UICONTROL Custom Script] e denominalo &quot;[!DNL Marketo Measure Marketing Analytics].&quot; Clic **[!UICONTROL Add Script Details]**.
1. Selezionate il posizionamento nella testina. Includi lo script nella pagina di destinazione principale e nella finestra di dialogo di conferma del modulo. Incolla il [!DNL Marketo Measure] nella casella.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Clic **[!UICONTROL Save]**.

Il [!DNL Marketo Measure] L’integrazione funziona sulle pagine di destinazione Unbounce purché siano ospitate nel dominio (ad esempio, landing.mysite.com) e non in quelle che utilizzano il dominio unbounce.com.
