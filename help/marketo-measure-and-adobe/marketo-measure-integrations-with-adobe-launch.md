---
description: '''[!DNL Marketo Measure] Integrazioni con Adobe Launch - [!DNL Marketo Measure] - Documentazione del prodotto"'
title: '''[!DNL Marketo Measure] Integrazioni con Adobe Launch"'
exl-id: 316ee8a8-b2d3-42e9-9ee5-c9b1d91c2769
source-git-commit: 19f670505358b04fb26620574b71c2af8d0d9847
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# [!DNL Marketo Measure] Integrazioni con Adobe Launch {#marketo-measure-integrations-with-adobe-launch}

L’estensione Adobe Launch è progettata per i [!DNL Marketo Measure] utenti che utilizzano già Adobe Launch sul loro sito web. L&#39;estensione funge da soluzione di gestione dei tag da utilizzare per configurare e caricare dinamicamente gli script sulle pagine in base a determinati eventi e condizioni.

Quando installato e configurato in Adobe Launch, la funzione [!DNL Marketo Measure] L&#39;estensione caricherà lo script bizible.js sulle pagine in cui è presente lo script Adobe Launch. Questo consente agli addetti al marketing di aggiungere bizible.js tramite la configurazione di Adobe Launch, anziché modificare esplicitamente la pagina web per aggiungere il tag script bizible.js .

## Configurare l’estensione Adobe Launch {#configure-the-adobe-launch-extension}

>[!PREREQUISITES]
>
>Consulta i seguenti collegamenti per ulteriori informazioni su Adobe Launch ed sue estensioni:
>
>* [[!DNL Marketo Measure] Estensione](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email/bizible.html?lang=en#catalog){target="_blank"}
>* [Panoramica di Adobe Launch](https://experienceleague.adobe.com/docs/launch-learn/implementing-in-websites-with-launch/index.html?lang=en#prerequisites){target="_blank"}
>* [Panoramica dell’estensione Adobe Launch](https://experienceleague.adobe.com/docs/launch/using/extension-dev/overview.html?lang=en#extension-configuration){target="_blank"}


1. Crea una proprietà seguendo i passaggi [nel presente articolo](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html?lang=en#go-to-the-data-collection-interface){target="_blank"}.

1. Fai clic sulla proprietà appena creata.

   ![](assets/marketo-measure-integrations-with-adobe-launch-1.png)

1. Clic **[!UICONTROL Extensions]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-2.png)

1. Fai clic sul pulsante **[!UICONTROL Catalog]** scheda e cerca &quot;[!UICONTROL Bizible].&quot;

   ![](assets/marketo-measure-integrations-with-adobe-launch-3.png)

1. In [!UICONTROL Bizible Analytics] riquadro, fai clic su **[!UICONTROL Install]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-4.png)

1. Nel campo Bizible AccountId , digita l’URL del sito web.

   ![](assets/marketo-measure-integrations-with-adobe-launch-5.png)

   >[!NOTE]
   >
   >Questo campo non è l&#39;&quot;ID account&quot; nella tabella Business_Prod.Business. Tutte le attività web dall’URL specificato saranno mappate sul [!DNL Marketo Measure] inquilino.

1. Clic **[!UICONTROL Save]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-6.png)

1. Fai clic su **[!UICONTROL Rules]**, quindi seleziona **[!UICONTROL Create New Rule]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-7.png)

1. Fai clic sul pulsante **[!UICONTROL Add]** pulsante sotto [!UICONTROL Events].

   ![](assets/marketo-measure-integrations-with-adobe-launch-8.png)

1. Nel menu a discesa Estensione , seleziona **[!UICONTROL Core]**. Quindi, nel menu a discesa Tipo evento , seleziona **[!UICONTROL Library Loaded (Page Top)]**. Se non assegna un nome all’evento, ne verrà applicato uno predefinito. Fai clic su **[!UICONTROL Keep Changes]** al termine.

   ![](assets/marketo-measure-integrations-with-adobe-launch-9.png)

1. Fai clic sul pulsante **[!UICONTROL Add]** in Azioni.

   ![](assets/marketo-measure-integrations-with-adobe-launch-10.png)

1. Nel menu a discesa Estensione , seleziona **[!UICONTROL Bizible Analytics]**. Quindi, nel menu a discesa Tipo di azione , seleziona **[!UICONTROL Initialize]**. Se non assegna un nome all’azione, ne verrà applicato uno predefinito. Fai clic su **[!UICONTROL Keep Changes]** al termine.

   ![](assets/marketo-measure-integrations-with-adobe-launch-11.png)

1. Clic **[!UICONTROL Save]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-12.png)
