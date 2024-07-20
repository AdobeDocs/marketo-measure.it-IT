---
unique-page-id: 18874736
description: Rimuovi [!DNL Marketo Measure] Parametri di tracciamento dall'URL della pagina di destinazione nelle Google Analytics - [!DNL Marketo Measure]
title: Rimuovi [!DNL Marketo Measure] Parametri di tracciamento dall'URL della pagina di destinazione nelle Google Analytics
exl-id: ec81ba4a-bb10-49fd-b62e-5a1bc9e1a023
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# Rimuovi [!DNL Marketo Measure] parametri di tracciamento dall&#39;URL della pagina di destinazione nelle Google Analytics {#remove-marketo-measure-tracking-parameters-from-the-landing-page-url-in-google-analytics}

Talvolta, durante la visualizzazione delle pagine di destinazione in [!DNL Google Analytics], è necessario rimuovere i parametri di tracciamento dagli URL. In caso contrario, verranno suddivise in singole righe.

Fortunatamente, questa è una correzione facile.

1. In [!DNL Google Analytics], vai a [!UICONTROL Admin] >[!UICONTROL View Settings] >[!UICONTROL Exclude URL Query Parameters].
1. Digitate &quot;_bt,_bk,_bm,_bn,_bg&quot; nella casella (meno le virgolette).
1. Scorrere verso il basso e fare clic su **[!UICONTROL Save]**.

   Tenere presente che [!DNL Google Analytics] non rielabora i dati. Pertanto questa modifica verrà applicata solo in futuro e i dati passati verranno comunque visualizzati con i parametri bt, bk e bm.
