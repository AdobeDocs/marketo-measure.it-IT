---
unique-page-id: 18874736
description: Rimuovi [!DNL Marketo Measure] parametri di tracciamento dall'URL della pagina di destinazione in Google Analytics - [!DNL Marketo Measure]
title: Rimuovi [!DNL Marketo Measure] parametri di tracciamento dall'URL della pagina di destinazione in Google Analytics
exl-id: ec81ba4a-bb10-49fd-b62e-5a1bc9e1a023
feature: Tracking
TQID: 'https://experienceleague.adobe.com/vKhwWUT0VQ1Kr-3-dWVWt08S4848Q0Bn4HYrGgHawb8'
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: dcbeff6e-0253-5a4b-9ac2-1b67cc4a6286
    internal-label: Tracking
topic_v2:
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%
---
# Rimuovi [!DNL Marketo Measure] parametri di tracciamento dall&#39;URL della pagina di destinazione in Google Analytics {#remove-marketo-measure-tracking-parameters-from-the-landing-page-url-in-google-analytics}

Talvolta, durante la visualizzazione delle pagine di destinazione in [!DNL Google Analytics], è necessario rimuovere i parametri di tracciamento dagli URL. In caso contrario, verranno suddivise in singole righe.

Fortunatamente, questa è una correzione facile.

1. In [!DNL Google Analytics], vai a [!UICONTROL Admin] >[!UICONTROL View Settings] >[!UICONTROL Exclude URL Query Parameters].
1. Digitate &quot;_bt,_bk,_bm,_bn,_bg&quot; nella casella (meno le virgolette).
1. Scorrere verso il basso e fare clic su **[!UICONTROL Save]**.

   Tenere presente che [!DNL Google Analytics] non rielabora i dati. Pertanto questa modifica verrà applicata solo in futuro e i dati passati verranno comunque visualizzati con i parametri bt, bk e bm.
