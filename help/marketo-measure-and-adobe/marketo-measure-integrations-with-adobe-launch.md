---
description: '[!DNL Marketo Measure] integrazioni con Adobe Launch - [!DNL Marketo Measure]'
title: Integrazioni '[!DNL Marketo Measure]' con Adobe Launch
exl-id: 316ee8a8-b2d3-42e9-9ee5-c9b1d91c2769
feature: Integration
source-git-commit: 6aaf6fd26f19e9382cc559e54558e1c5d84cfd6d
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Integrazioni [!DNL Marketo Measure] con Adobe Launch {#marketo-measure-integrations-with-adobe-launch}

L&#39;estensione Adobe Launch è progettata per gli utenti [!DNL Marketo Measure] esistenti che già utilizzano Adobe Launch sul loro sito Web. L’estensione funge da soluzione di gestione tag da utilizzare per configurare e caricare dinamicamente gli script sulle pagine in base a determinati eventi e condizioni.

Quando è installata e configurata in Adobe Launch, l&#39;estensione [!DNL Marketo Measure] carica lo script bizible.js sulle pagine in cui è presente lo script Adobe Launch. Questo consente agli addetti al marketing di aggiungere bizible.js tramite la configurazione di Adobe Launch, anziché modificare esplicitamente la pagina web per aggiungere il tag di script bizible.js.

## Configurare l’estensione Adobe Launch {#configure-the-adobe-launch-extension}

>[!PREREQUISITES]
>
>Per ulteriori informazioni su Adobe Launch e le sue estensioni, consulta i seguenti collegamenti:
>
>* [[!DNL Marketo Measure] Estensione](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email/bizible.html#catalog){target="_blank"}
>* [Panoramica di Adobe Launch](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/overview.html){target="_blank"}
>* [Panoramica dell&#39;estensione Adobe Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/extension-dev/overview.html){target="_blank"}

1. Crea una proprietà seguendo i passaggi [descritti in questo articolo](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html#go-to-the-data-collection-interface){target="_blank"}.

1. Fai clic sulla proprietà creata.

   ![](assets/marketo-measure-integrations-with-adobe-launch-1.png)

1. Fare clic su **[!UICONTROL Extensions]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-2.png)

1. Fare clic sulla scheda **[!UICONTROL Catalog]** e cercare &quot;[!UICONTROL Bizible]&quot;.

   ![](assets/marketo-measure-integrations-with-adobe-launch-3.png)

1. Nel riquadro [!UICONTROL Bizible Analytics], fare clic su **[!UICONTROL Install]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-4.png)

1. Nel campo ID account Bizible digitare l&#39;URL del sito Web, ad esempio `adobe.com`.

   ![](assets/marketo-measure-integrations-with-adobe-launch-5.png)

1. Fare clic su **[!UICONTROL Save]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-6.png)

1. Fai clic su **[!UICONTROL Rules]**, quindi seleziona **[!UICONTROL Create New Rule]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-7.png)

1. Fare clic sul pulsante **[!UICONTROL Add]** in [!UICONTROL Events].

   ![](assets/marketo-measure-integrations-with-adobe-launch-8.png)

1. Nel menu a discesa Estensione, selezionare **[!UICONTROL Core]**. Quindi nel menu a discesa Tipo evento, seleziona **[!UICONTROL Library Loaded (Page Top)]**. Se non si assegna un nome all’evento, viene applicato un nome predefinito. Al termine, fai clic su **[!UICONTROL Keep Changes]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-9.png)

1. Fare clic sul pulsante **[!UICONTROL Add]** in Azioni.

   ![](assets/marketo-measure-integrations-with-adobe-launch-10.png)

1. Nel menu a discesa Estensione, selezionare **[!UICONTROL Bizible Analytics]**. Quindi nel menu a discesa Tipo di azione, seleziona **[!UICONTROL Initialize]**. Se non assegna un nome all’azione, viene applicato un nome predefinito. Al termine, fai clic su **[!UICONTROL Keep Changes]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-11.png)

1. Fare clic su **[!UICONTROL Save]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-12.png)

