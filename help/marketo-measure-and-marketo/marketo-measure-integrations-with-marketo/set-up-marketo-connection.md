---
unique-page-id: 42762762
description: Configura connessione Marketo - [!DNL Marketo Measure]
title: Configura connessione Marketo
exl-id: 11660539-1cc5-4768-8f22-d6f7cd0b94f3
feature: Integration
TQID: https://experienceleague.adobe.com/IQhZzu6iqS-5BdooPRA6-A8BoJtQ936NRFJHPGu3Xp4
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
feature_v2:
  - id: c8f57308-7e33-4e41-a385-b55041c78939
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 9ceb54139bfa9b6ce7c2c5fbb4e25e649f5708a3
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 1%

---

# Configura connessione Marketo {#set-up-marketo-connection}

Ecco come impostare la connessione a Marketo.

>[!PREREQUISITES]
>
>[Crea un ruolo utente solo API](https://experienceleague.adobe.com/docs/marketo/using/product-docs/administration/users-and-roles/create-an-api-only-user.html?lang=it){target="_blank"} per la connessione [!DNL Marketo Measure]/Marketo Engage.

1. In [!DNL Marketo Measure], fare clic sul menu a discesa **[!UICONTROL My Account]** e selezionare **[!UICONTROL Settings]**.

   ![](assets/set-up-marketo-connection-1.png)

1. In [!UICONTROL Integrations], fare clic su **[!UICONTROL Connections]**.

   ![](assets/set-up-marketo-connection-2.png)

1. Fai clic su **[!UICONTROL Set Up New CRM Connection]**.

   ![](assets/set-up-marketo-connection-3.png)

1. Fare clic sul pulsante **[!UICONTROL Connect]** accanto a Marketo.

   ![](assets/set-up-marketo-connection-4.png)

1. In una nuova scheda, accedi al tuo account Marketo Engage. Vai a **Amministratore** > **Servizi Web**. Scorri verso il basso fino a API REST. Evidenzia e salva l’URL dell’endpoint e del servizio Identity. Sono necessari nei passaggi seguenti.

   ![](assets/set-up-marketo-connection-5.png)

1. Sempre in Marketo Engage, seleziona **LaunchPoint** nella struttura a sinistra. Individuare il servizio personalizzato che si desidera connettere a Marketo Measure e fare clic su **Visualizza dettagli**.

   ![](assets/set-up-marketo-connection-6.png)

1. Evidenzia e salva l’ID client e il segreto client. Fai clic su **Chiudi**.

   ![](assets/set-up-marketo-connection-7.png)

1. Compila nuovamente i campi in [!DNL Marketo Measure] con i dati raccolti.

   ![](assets/set-up-marketo-connection-8.png)

1. Dopo aver immesso i valori, fare clic su **[!UICONTROL Authenticate]**. Il tuo account Marketo Engage è connesso a [!DNL Marketo Measure].

   ![](assets/set-up-marketo-connection-9.png)

   >[!NOTE]
   >
   >[!DNL Marketo Measure] effettua chiamate all&#39;API Marketo per tuo conto senza utilizzare i limiti dell&#39;API Marketo, quindi non è necessario preoccuparsi dei limiti e dell&#39;allocazione del credito con altre integrazioni.
