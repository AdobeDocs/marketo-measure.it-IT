---
description: Connessione in corso  [!DNL Marketo Measure]  a Gestione script per l'annullamento del mancato recapito - [!DNL Marketo Measure]
title: Connessione in corso  [!DNL Marketo Measure]  a Gestione script per l'annullamento della remissione
exl-id: c3212bc3-1d8f-4da5-bb2d-11ffd2fb4e98
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 3%

---


# Connessione di [!DNL Marketo Measure] a Gestione script per l&#39;annullamento della remissione {#connecting-marketo-measure-to-unbounce-script-manager}

[!DNL Marketo Measure] si integra direttamente con Unbounce, consentendo di tenere traccia dell&#39;origine di marketing digitale delle conversioni della pagina di destinazione direttamente in [!DNL Salesforce]. Per stabilire la connessione, è sufficiente aggiungere lo script [!DNL Marketo Measure] al gestore degli script non recapitati. Ecco come.

1. Accedi al tuo account [!DNL Unbounce].
1. Fare clic su **[!UICONTROL Settings]** > **[!UICONTROL Script Manager]** > **[!UICONTROL Add Script]**.
1. Nel popup, selezionare [!UICONTROL Custom Script] e denominarlo &quot;[!DNL Marketo Measure Marketing Analytics]&quot;. Fai clic su **[!UICONTROL Add Script Details]**.
1. Selezionate il posizionamento nella testina. Includi lo script nella pagina di destinazione principale e nella finestra di dialogo di conferma del modulo. Incolla nella casella lo script [!DNL Marketo Measure] sottostante.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Fai clic su **[!UICONTROL Save]**.

L&#39;integrazione di [!DNL Marketo Measure] funziona sulle pagine di destinazione Unbounce purché siano ospitate nel dominio (ad esempio, landing.mysite.com) e non in quelle che utilizzano il dominio unbounce.com.
