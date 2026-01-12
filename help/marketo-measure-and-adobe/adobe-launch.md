---
description: Integrazioni [!DNL Marketo Measure] con Adobe Launch - [!DNL Marketo Measure]
title: Integrazioni [!DNL Marketo Measure] con Adobe Launch
exl-id: 316ee8a8-b2d3-42e9-9ee5-c9b1d91c2769
feature: Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# Integrazioni [!DNL Marketo Measure] con Adobe Launch {#marketo-measure-integrations}

L&#39;estensione Adobe Launch è progettata per gli utenti [!DNL Marketo Measure] esistenti che già utilizzano Adobe Launch sul loro sito Web. L’estensione funge da soluzione di gestione tag da utilizzare per configurare e caricare dinamicamente gli script sulle pagine in base a determinati eventi e condizioni.

Quando è installata e configurata in Adobe Launch, l&#39;estensione [!DNL Marketo Measure] carica lo script bizible.js sulle pagine in cui è presente lo script di Adobe Launch. Questo consente agli addetti al marketing di aggiungere bizible.js tramite la configurazione di Adobe Launch, anziché modificare esplicitamente la pagina web per aggiungere il tag di script bizible.js.

## Configurare l’estensione Adobe Launch {#configure-the-adobe-launch-extension}

>[!PREREQUISITES]
>Consulta i seguenti collegamenti per ulteriori informazioni su Adobe Launch e le sue estensioni:
> [[!DNL Marketo Measure] Estensione](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email/bizible.html?lang=it#catalog){target="_blank"}
> [Panoramica di Adobe Launch](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/overview.html?lang=it){target="_blank"}
> [Panoramica dell&#39;estensione Adobe Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/extension-dev/overview.html?lang=it){target="_blank"}

1. Crea una proprietà seguendo i passaggi [descritti in questo articolo](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html?lang=it#go-to-the-data-collection-interface){target="_blank"}.

1. Fai clic sulla proprietà creata.

   ![La schermata di selezione delle proprietà di Adobe Launch mostra le proprietà disponibili](assets/marketo-measure-integrations-1.png)

1. Fai clic su **[!UICONTROL Extensions]**.

   ![Scheda Estensioni nelle impostazioni delle proprietà di Adobe Launch](assets/marketo-measure-integrations-2.png)

1. Fare clic sulla scheda **[!UICONTROL Catalog]** e cercare &quot;[!UICONTROL Bizible]&quot;.

   ![Ricerca nel catalogo estensioni con estensione Bizible](assets/marketo-measure-integrations-3.png)

1. Nel riquadro [!UICONTROL Bizible Analytics], fare clic su **[!UICONTROL Install]**.

   ![Riquadro dell&#39;estensione Bizible Analytics con pulsante Installa](assets/marketo-measure-integrations-4.png)

1. Nel campo ID account Bizible digitare l&#39;URL del sito Web, ad esempio `adobe.com`.

   ![Configurazione dell&#39;estensione Bizible con campo AccountId](assets/marketo-measure-integrations-5.png)

1. Fai clic su **[!UICONTROL Save]**.

   ![Pulsante Salva per la configurazione estensione Bizible](assets/marketo-measure-integrations-6.png)

1. Fai clic su **[!UICONTROL Rules]**, quindi seleziona **[!UICONTROL Create New Rule]**.

   ![Scheda Regole con pulsante Crea nuova regola](assets/marketo-measure-integrations-7.png)

1. Fare clic sul pulsante **[!UICONTROL Add]** in [!UICONTROL Events].

   ![Pulsante Aggiungi nella sezione Eventi della configurazione regola](assets/marketo-measure-integrations-8.png)

1. Nel menu a discesa Estensione, selezionare **[!UICONTROL Core]**. Quindi nel menu a discesa Tipo evento, seleziona **[!UICONTROL Library Loaded (Page Top)]**. Se non si assegna un nome all’evento, viene applicato un nome predefinito. Al termine, fai clic su **[!UICONTROL Keep Changes]**.

   ![Finestra di dialogo per la configurazione dell&#39;evento con estensione core e tipo di evento Library Loaded](assets/marketo-measure-integrations-9.png)

1. Fare clic sul pulsante **[!UICONTROL Add]** in Azioni.

   ![Pulsante Aggiungi nella sezione Azioni della configurazione regola](assets/marketo-measure-integrations-10.png)

1. Nel menu a discesa Estensione, selezionare **[!UICONTROL Bizible Analytics]**. Quindi nel menu a discesa Tipo di azione, seleziona **[!UICONTROL Initialize]**. Se non assegna un nome all’azione, viene applicato un nome predefinito. Al termine, fai clic su **[!UICONTROL Keep Changes]**.

   ![Finestra di dialogo per la configurazione delle azioni con estensione Bizible Analytics e tipo di azione Inizializza](assets/marketo-measure-integrations-11.png)

1. Fai clic su **[!UICONTROL Save]**.

   ![Pulsante Salva per la configurazione della regola](assets/marketo-measure-integrations-12.png)

