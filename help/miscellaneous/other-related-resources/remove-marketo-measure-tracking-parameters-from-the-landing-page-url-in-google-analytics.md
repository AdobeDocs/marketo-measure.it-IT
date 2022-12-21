---
unique-page-id: 18874736
description: Rimuovi [!DNL Marketo Measure] Tracciamento dei parametri dall’URL della pagina di destinazione in Google Analytics - [!DNL Marketo Measure] - Documentazione del prodotto
title: Rimuovi [!DNL Marketo Measure] Tracciamento dei parametri dall’URL della pagina di destinazione nelle Google Analytics
exl-id: ec81ba4a-bb10-49fd-b62e-5a1bc9e1a023
source-git-commit: 09ffdbb0b1baeed870a3145268997e63a3707c97
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 0%

---

# Rimuovi [!DNL Marketo Measure] Tracciamento dei parametri dall’URL della pagina di destinazione nelle Google Analytics {#remove-marketo-measure-tracking-parameters-from-the-landing-page-url-in-google-analytics}

A volte durante la visualizzazione delle pagine di destinazione in [!DNL Google Analytics], rimuovi i parametri di tracciamento dagli URL. In caso contrario, verranno suddivisi in singole righe.

Fortunatamente, questa è una soluzione facile.

1. In [!DNL Google Analytics], vai a [!UICONTROL Admin] >[!UICONTROL View Settings] >[!UICONTROL Exclude URL Query Parameters].
1. Digitare &quot;_bt,_bk,_bm,_bn,_bg&quot; nella casella (meno le virgolette).
1. Scorri verso il basso e fai clic su **[!UICONTROL Save]**.

   Nota bene [!DNL Google Analytics] non rielabora i dati. Pertanto questa modifica verrà solo riflessa in avanti e i dati passati verranno comunque visualizzati con i parametri bt, bk e bm.
