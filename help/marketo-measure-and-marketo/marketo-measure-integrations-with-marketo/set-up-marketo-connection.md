---
unique-page-id: 42762762
description: Configura connessione Marketo - [!DNL Marketo Measure] - Documentazione del prodotto
title: Configura connessione Marketo
exl-id: 11660539-1cc5-4768-8f22-d6f7cd0b94f3
feature: Integration
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 1%

---

# Configura connessione Marketo {#set-up-marketo-connection}

Ecco come impostare la connessione a Marketo.

>[!PREREQUISITES]
>
>[Creare un ruolo utente solo API](https://experienceleague.adobe.com/docs/marketo/using/product-docs/administration/users-and-roles/create-an-api-only-user.html) per [!DNL Marketo Measure]/Marketi Engage.

1. In entrata [!DNL Marketo Measure], fare clic su **[!UICONTROL My Account]** a discesa e selezionare **[!UICONTROL Settings]**.

   ![](assets/set-up-marketo-connection-1.png)

1. Sotto [!UICONTROL Integrations], fai clic su **[!UICONTROL Connections]**.

   ![](assets/set-up-marketo-connection-2.png)

1. Clic **[!UICONTROL Set Up New CRM Connection]**.

   ![](assets/set-up-marketo-connection-3.png)

1. Fai clic su **[!UICONTROL Connect]** accanto a Marketo.

   ![](assets/set-up-marketo-connection-4.png)

1. In una nuova scheda, accedi al tuo account di Marketo Engage. Vai a **Amministratore** > **Servizi Web**. Scorri verso il basso fino a API REST. Evidenzia e salva l’URL dell’endpoint e del servizio Identity. Ne avrai bisogno tra un po&#39;.

   ![](assets/set-up-marketo-connection-5.png)

1. Sempre nel Marketo Engage, seleziona **LaunchPoint** nell&#39;albero a sinistra. Trova il servizio personalizzato da connettere a Marketo Measure e fai clic su **Visualizza dettagli**.

   ![](assets/set-up-marketo-connection-6.png)

1. Evidenzia e salva l’ID client e il segreto client. Fai clic su **Chiudi**.

   ![](assets/set-up-marketo-connection-7.png)

1. Torna in [!DNL Marketo Measure], popola i campi con i dati appena raccolti.

   ![](assets/set-up-marketo-connection-8.png)

1. Dopo aver immesso i valori, fare clic su **[!UICONTROL Authenticate]**. L&#39;account di Marketo Engage sarà quindi connesso a [!DNL Marketo Measure].

   ![](assets/set-up-marketo-connection-9.png)

   >[!NOTE]
   >
   >[!DNL Marketo Measure] effettuerà chiamate all’API Marketo per tuo conto senza consumare nessuno dei limiti dell’API Marketo, quindi non preoccuparti di massimali e allocazione di credito con altre integrazioni.
