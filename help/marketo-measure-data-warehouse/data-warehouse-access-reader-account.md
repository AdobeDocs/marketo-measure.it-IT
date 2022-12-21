---
description: Accesso a Data Warehouse - Account Reader - Documentazione del prodotto
title: Accesso Data Warehouse - Account Reader
exl-id: 2aa73c41-47ab-4f11-96d8-dafb642308fc
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Accesso Data Warehouse - Account Reader {#data-warehouse-access-reader-account}

## Collegamento di accesso al Snowflake {#snowflake-access-link}

Per accedere al data warehouse di Snowflake, dovrai passare all&#39;URL specifico per l&#39;account di Snowflake. Puoi trovare questo collegamento di accesso accedendo a [!DNL Marketo Measure] e segui i passaggi seguenti per passare alla pagina delle informazioni sulla Data Warehouse .

1. In [!DNL Marketo Measure], nella parte superiore della pagina, fai clic su **[!UICONTROL My Account]** > **[!UICONTROL Settings]**.

   ![](assets/data-warehouse-access-reader-account-1.png)

1. Scegliere Protezione dal menu a sinistra. **[!UICONTROL Data Warehouse]**.

   ![](assets/data-warehouse-access-reader-account-2.png)

1. In questa pagina troverai il collegamento al data warehouse di Snowflake e il tuo nome utente.

   ![](assets/data-warehouse-access-reader-account-3.png)

   >[!NOTE]
   >
   >Questo è un account di sola lettura disponibile per la tua organizzazione, non solo per un singolo utente. Qualsiasi utente della tua organizzazione che ha accesso a [!DNL Marketo Measure] può utilizzare questo account per accedere all&#39;account lettore Data Warehouse Snowflake.

1. Fai clic sul collegamento fornito nell’URL del Snowflake per passare alla pagina di accesso del Snowflake in cui inserirai il tuo nome utente e password. _Se non disponi di una password, consulta i passaggi seguenti per reimpostarla_.

   ![](assets/data-warehouse-access-reader-account-4.png)

1. Una volta effettuato l’accesso, fai clic su **[!UICONTROL Worksheets]** nella parte superiore della pagina.

   ![](assets/data-warehouse-access-reader-account-5.png)

1. Gli oggetti del database BIZIBLE_ROI_V3 si trovano sul lato sinistro dello schermo. Immettere il warehouse, il database e lo schema dal menu a discesa nella parte superiore della finestra della query. Ci dovrebbe essere una sola opzione per ogni. Ora è possibile eseguire query all’interno dell’editor delle query di Snowflake.

   ![](assets/data-warehouse-access-reader-account-6.png)

## Ripristino della password {#reset-your-password}

[!DNL Marketo Measure] non ha accesso alla password di accesso del Snowflake. Se devi reimpostare la password, fai clic sul pulsante [!UICONTROL Reset Password] nella pagina Data Warehouse informazioni e seguire le istruzioni. Nell’interfaccia utente viene immediatamente visualizzata una password temporanea. Verrà richiesto di creare la propria password sul tuo successivo accesso al data warehouse.

>[!NOTE]
>
>* Reimpostando la password, la reimposta per tutti [!DNL Marketo Measure] utenti della tua organizzazione, non solo l&#39;utente che ha effettuato l&#39;accesso.
>* Mostriamo solo la password temporanea nell’interfaccia utente. Un’e-mail non verrà inviata.


![](assets/data-warehouse-access-reader-account-7.png)

![](assets/data-warehouse-access-reader-account-8.png)

## Connessione al Snowflake tramite strumenti di terze parti {#connecting-to-snowflake-via-third-party-tools}

Per collegare il data warehouse di Snowflake a uno strumento di terze parti, è necessario immettere alcune informazioni.

>[!NOTE]
>
>Ogni strumento ha requisiti di connessione diversi; è consigliabile consultare la documentazione relativa allo strumento specifico che si sta tentando di collegare.

* **URI** (obbligatorio sempre)
   * Nome di dominio dell&#39;account di Snowflake.  È contenuto in una parte del collegamento di accesso del Snowflake.
* **Nome utente** (obbligatorio sempre)
   * Il nome utente è elencato nella pagina delle informazioni sulla Data Warehouse in [!DNL Marketo Measure].
* **Password** (obbligatorio sempre)
   * Questa è la password impostata al primo accesso al tuo account di Snowflake.  Per reimpostare la password, consulta i passaggi descritti in precedenza.
* **Nome database** (non sempre richiesto)
   * Il database è ciò che memorizza i dati in Snowflake. È la risorsa di archiviazione. Il nome del database viene elencato nella pagina Data Warehouse informazioni in [!DNL Marketo Measure].
* **Nome magazzino** (non sempre richiesto)
   * Il magazzino è ciò che esegue le query nel Snowflake. È la risorsa di calcolo.  Il nome del warehouse viene elencato nella pagina Data Warehouse informazioni in [!DNL Marketo Measure].
   ![](assets/data-warehouse-access-reader-account-9.png)
