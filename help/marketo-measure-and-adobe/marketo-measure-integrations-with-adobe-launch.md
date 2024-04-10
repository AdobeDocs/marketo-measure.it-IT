---
description: '[!DNL Marketo Measure] Integrazioni con Adobe Launch - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] Integrazioni con Adobe Launch'
exl-id: 316ee8a8-b2d3-42e9-9ee5-c9b1d91c2769
feature: Integration
source-git-commit: 6aaf6fd26f19e9382cc559e54558e1c5d84cfd6d
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# [!DNL Marketo Measure] Integrazioni con Adobe Launch {#marketo-measure-integrations-with-adobe-launch}

L’estensione Adobe Launch è progettata per [!DNL Marketo Measure] utenti che già utilizzano Adobe Launch sul proprio sito web. L’estensione funge da soluzione di gestione tag da utilizzare per configurare e caricare dinamicamente gli script sulle pagine in base a determinati eventi e condizioni.

Quando è installato e configurato in Adobe Launch, il [!DNL Marketo Measure] L&#39;estensione carica lo script bizible.js sulle pagine in cui è presente lo script Adobe Launch. Questo consente agli addetti al marketing di aggiungere bizible.js tramite la configurazione di Adobe Launch, anziché modificare esplicitamente la pagina web per aggiungere il tag di script bizible.js.

## Configurare l’estensione Adobe Launch {#configure-the-adobe-launch-extension}

>[!PREREQUISITES]
>
>Per ulteriori informazioni su Adobe Launch e le sue estensioni, consulta i seguenti collegamenti:
>
>* [[!DNL Marketo Measure] Estensione](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email/bizible.html#catalog){target="_blank"}
>* [Panoramica di Adobe Launch](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/overview.html){target="_blank"}
>* [Panoramica dell’estensione Adobe Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/extension-dev/overview.html){target="_blank"}

1. Crea una proprietà seguendo la procedura riportata di seguito [in questo articolo](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html#go-to-the-data-collection-interface){target="_blank"}.

1. Fai clic sulla proprietà creata.

   ![](assets/marketo-measure-integrations-with-adobe-launch-1.png)

1. Clic **[!UICONTROL Extensions]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-2.png)

1. Fai clic su **[!UICONTROL Catalog]** e cerca &quot;[!UICONTROL Bizible].&quot;

   ![](assets/marketo-measure-integrations-with-adobe-launch-3.png)

1. In [!UICONTROL Bizible Analytics] riquadro, fai clic su **[!UICONTROL Install]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-4.png)

1. Nel campo ID account Bizible, digita l’URL del tuo sito web (ad esempio, `adobe.com`).

   ![](assets/marketo-measure-integrations-with-adobe-launch-5.png)

1. Clic **[!UICONTROL Save]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-6.png)

1. Clic **[!UICONTROL Rules]**, quindi seleziona **[!UICONTROL Create New Rule]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-7.png)

1. Fai clic su **[!UICONTROL Add]** pulsante sotto [!UICONTROL Events].

   ![](assets/marketo-measure-integrations-with-adobe-launch-8.png)

1. Nel menu a discesa Estensione, seleziona **[!UICONTROL Core]**. Quindi nel menu a discesa Tipo evento, seleziona **[!UICONTROL Library Loaded (Page Top)]**. Se non si assegna un nome all’evento, viene applicato un nome predefinito. Clic **[!UICONTROL Keep Changes]** al termine.

   ![](assets/marketo-measure-integrations-with-adobe-launch-9.png)

1. Fai clic su **[!UICONTROL Add]** in Azioni.

   ![](assets/marketo-measure-integrations-with-adobe-launch-10.png)

1. Nel menu a discesa Estensione, seleziona **[!UICONTROL Bizible Analytics]**. Quindi, nel menu a discesa Tipo di azione, seleziona **[!UICONTROL Initialize]**. Se non assegna un nome all’azione, viene applicato un nome predefinito. Clic **[!UICONTROL Keep Changes]** al termine.

   ![](assets/marketo-measure-integrations-with-adobe-launch-11.png)

1. Clic **[!UICONTROL Save]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-12.png)

