---
description: Accesso Data Warehouse - Account di Reader - Documentazione del prodotto
title: Data Warehouse accesso - Account Reader
exl-id: 2aa73c41-47ab-4f11-96d8-dafb642308fc
feature: Data Warehouse
source-git-commit: e9861f8032475d3e60a3bb3ebf67dfee520bbb75
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Data Warehouse accesso - Account Reader {#data-warehouse-access-reader-account}

## Collegamento accesso Snowflake {#snowflake-access-link}

Per accedere al data warehouse di Snowflake, devi passare all’URL specifico del tuo account di Snowflake. Per trovare questo collegamento di accesso, accedere a [!DNL Marketo Measure] e seguire la procedura riportata di seguito per passare alla pagina delle informazioni di Data Warehouse.

1. In [!DNL Marketo Measure], nella parte superiore della pagina, fare clic su **[!UICONTROL My Account]** > **[!UICONTROL Settings]**.

   ![](assets/data-warehouse-access-reader-account-1.png)

1. Nel menu a sinistra, sotto Protezione, fare clic su **[!UICONTROL Data Warehouse]**.

   ![](assets/data-warehouse-access-reader-account-2.png)

1. Questa pagina contiene il collegamento al data warehouse di Snowflake e il nome utente.

   ![](assets/data-warehouse-access-reader-account-3.png)

   >[!NOTE]
   >
   >Questo è un account di sola lettura disponibile per la tua organizzazione, non solo per un singolo utente. Qualsiasi utente dell&#39;organizzazione che ha accesso a [!DNL Marketo Measure] può utilizzare questo account per accedere all&#39;account lettore di Date Warehouse di Snowflake.

1. Fare clic sul collegamento fornito nell&#39;URL del Snowflake per passare alla pagina di accesso del Snowflake in cui si immettono nome utente e password. _Se non si dispone della password, vedere la procedura seguente per reimpostarla_.

   ![](assets/data-warehouse-access-reader-account-4.png)

1. Dopo aver effettuato l&#39;accesso, fare clic su **[!UICONTROL Worksheets]** nella parte superiore della pagina.

   ![](assets/data-warehouse-access-reader-account-5.png)

1. Gli oggetti di database BIZIBLE_ROI_V3 si trovano sul lato sinistro dello schermo. Immettere Warehouse, Database e Schema dalle opzioni a discesa nella parte superiore della finestra della query. Dovrebbe essere disponibile una sola opzione per ciascuno di essi. Ora puoi eseguire le query all’interno dell’editor di query del Snowflake.

   ![](assets/data-warehouse-access-reader-account-6.png)

## Reimposta la password {#reset-your-password}

[!DNL Marketo Measure] non ha accesso alla tua password di accesso al Snowflake. Se è necessario reimpostare la password, fare clic sul pulsante [!UICONTROL Reset Password] nella pagina Data Warehouse informazioni e seguire le istruzioni. Una password temporanea viene visualizzata immediatamente nell’interfaccia utente. Ti verrà chiesto di creare la tua password al prossimo accesso al data warehouse.

>[!NOTE]
>
>* La reimpostazione della password la reimposta per tutti [!DNL Marketo Measure] utenti dell&#39;organizzazione, non solo per l&#39;utente attualmente connesso.
>* Nell’interfaccia utente viene visualizzata solo la password temporanea. Non verrà inviata un’e-mail.

![](assets/data-warehouse-access-reader-account-7.png)

![](assets/data-warehouse-access-reader-account-8.png)

## Connessione al Snowflake tramite strumenti di terze parti {#connecting-to-snowflake-via-third-party-tools}

È necessario immettere alcune informazioni per collegare il data warehouse di Snowflake a uno strumento di terze parti.

>[!NOTE]
>
>Ogni strumento ha requisiti di connessione diversi; si consiglia di consultare la documentazione dello strumento specifico che si sta tentando di connettere.

* **URI** (sempre obbligatorio)
   * Nome di dominio dell&#39;account di Snowflake. È contenuto in una parte del collegamento di accesso al Snowflake.
* **Nome utente** (sempre obbligatorio)
   * Il nome utente è elencato nella pagina delle informazioni sulla Data Warehouse in [!DNL Marketo Measure].
* **Password** (sempre richiesta)
   * Questa è la password impostata al primo accesso all&#39;account di Snowflake. Per reimpostare la password, seguire la procedura descritta in precedenza.
* **Nome database** (non sempre richiesto)
   * Il database è ciò che memorizza i dati nel Snowflake. Si tratta della risorsa di archiviazione. Il nome del database è elencato nella pagina delle informazioni sulla Data Warehouse in [!DNL Marketo Measure].
* **Nome data warehouse** (non sempre obbligatorio)
   * Il warehouse esegue le query nel Snowflake. È la risorsa calcolata. Il nome del magazzino è elencato nella pagina delle informazioni sulle Date Warehouse in [!DNL Marketo Measure].

  ![](assets/data-warehouse-access-reader-account-9.png)
