---
unique-page-id: 18874743
description: Collegamento [!DNL Marketo Measure] per annullare l'esecuzione di Script Manager - [!DNL Marketo Measure] - Documentazione del prodotto
title: Collegamento [!DNL Marketo Measure] a Unbounce Script Manager
exl-id: c3212bc3-1d8f-4da5-bb2d-11ffd2fb4e98
source-git-commit: ae5b77744d523606ce6cfcf48d7e8d5049d5ccb7
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 1%

---

# Collegamento [!DNL Marketo Measure] a Unbounce Script Manager {#connecting-marketo-measure-to-unbounce-script-manager}

[!DNL Marketo Measure] si integra direttamente con Unbounce, consentendoti di monitorare l’origine di marketing digitale delle conversioni di pagine di destinazione direttamente in [!DNL Salesforce]. Per effettuare la connessione, è sufficiente aggiungere la [!DNL Marketo Measure] script nel gestore script Unbounce. Ecco come.

1. Accedi al tuo [!DNL Unbounce] conto.
1. Fai clic su **[!UICONTROL Settings]** > **[!UICONTROL Script Manager]** > **[!UICONTROL Add Script]**.
1. Nella finestra a comparsa, seleziona [!UICONTROL Custom Script] e denominalo &quot;[!DNL Marketo Measure Marketing Analytics].&quot; Clic **[!UICONTROL Add Script Details]**.
1. Selezionare il posizionamento nella testa. Includere lo script nella pagina di destinazione principale e nella finestra di dialogo di conferma del modulo. Incolla [!DNL Marketo Measure] script sottostante nella casella.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Clic **[!UICONTROL Save]**.

La [!DNL Marketo Measure] L’integrazione funziona sulle pagine di destinazione Unbounce purché siano ospitate sul tuo dominio (ad esempio, landing.mysite.com) e non su quelle che utilizzano il dominio unbounce.com .
