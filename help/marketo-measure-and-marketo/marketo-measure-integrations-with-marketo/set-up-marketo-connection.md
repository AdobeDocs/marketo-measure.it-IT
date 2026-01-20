---
unique-page-id: 42762762
description: Configura connessione Marketo - [!DNL Marketo Measure]
title: Configura connessione Marketo
exl-id: 11660539-1cc5-4768-8f22-d6f7cd0b94f3
feature: Integration
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 1%

---

# Configura connessione Marketo {#set-up-marketo-connection}

Ecco come impostare la connessione a Marketo.

>[!PREREQUISITES]
>
>[Crea un ruolo utente solo API](https://experienceleague.adobe.com/docs/marketo/using/product-docs/administration/users-and-roles/create-an-api-only-user.html){target="_blank"} per la connessione [!DNL Marketo Measure]/Marketo Engage.

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
