---
description: Accesso Data Warehouse - Account di Reader - Documentazione del prodotto
title: Data Warehouse accesso - Account Reader
exl-id: 2aa73c41-47ab-4f11-96d8-dafb642308fc
feature: Data Warehouse
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Data Warehouse accesso - Account Reader {#data-warehouse-access-reader-account}

## Collegamento accesso Snowflake {#snowflake-access-link}

Per accedere al data warehouse di Snowflake, devi passare all’URL specifico del tuo account di Snowflake. Per trovare questo collegamento di accesso, accedi a [!DNL Marketo Measure] e seguire i passaggi riportati di seguito per passare alla pagina delle informazioni di Data Warehouse.

1. In entrata [!DNL Marketo Measure], nella parte superiore della pagina, fai clic su **[!UICONTROL My Account]** > **[!UICONTROL Settings]**.

   ![](assets/data-warehouse-access-reader-account-1.png)

1. Nel menu a sinistra, nella sezione Protezione, fare clic su **[!UICONTROL Data Warehouse]**.

   ![](assets/data-warehouse-access-reader-account-2.png)

1. In questa pagina è disponibile il collegamento al data warehouse di Snowflake e al nome utente.

   ![](assets/data-warehouse-access-reader-account-3.png)

   >[!NOTE]
   >
   >Questo è un account di sola lettura disponibile per la tua organizzazione, non solo per un singolo utente. Qualsiasi utente all’interno dell’organizzazione che ha accesso a [!DNL Marketo Measure] può utilizzare questo account per accedere all&#39;account lettore di Date Warehouse di Snowflake.

1. Fai clic sul collegamento fornito nell’URL del Snowflake per passare alla pagina di accesso del Snowflake in cui immetti il nome utente e la password. _Se la password non è disponibile, vedere i passaggi seguenti per reimpostarla_.

   ![](assets/data-warehouse-access-reader-account-4.png)

1. Una volta effettuato l’accesso, fai clic su **[!UICONTROL Worksheets]** nella parte superiore della pagina.

   ![](assets/data-warehouse-access-reader-account-5.png)

1. Gli oggetti di database BIZIBLE_ROI_V3 si trovano sul lato sinistro dello schermo. Immettere Warehouse, Database e Schema dalle opzioni a discesa nella parte superiore della finestra della query. Dovrebbe essere disponibile una sola opzione per ciascuno di essi. Ora puoi eseguire le query all’interno dell’editor di query del Snowflake.

   ![](assets/data-warehouse-access-reader-account-6.png)

## Reimposta la password {#reset-your-password}

[!DNL Marketo Measure] non ha accesso alla password di accesso del Snowflake. Se è necessario reimpostare la password, fare clic su [!UICONTROL Reset Password] nella pagina delle informazioni della Data Warehouse e seguire le istruzioni. Una password temporanea viene visualizzata immediatamente nell’interfaccia utente. Ti verrà chiesto di creare una password al prossimo accesso a Data Warehouse.

>[!NOTE]
>
>* Reimpostando la password si reimposta per tutti [!DNL Marketo Measure] utenti dell’organizzazione, non solo l’utente attualmente connesso.
>* Nell’interfaccia utente viene visualizzata solo la password temporanea. Non verrà inviata un’e-mail.

![](assets/data-warehouse-access-reader-account-7.png)

![](assets/data-warehouse-access-reader-account-8.png)

## Connessione al Snowflake tramite strumenti di terze parti {#connecting-to-snowflake-via-third-party-tools}

È necessario immettere alcune informazioni per collegare il data warehouse di Snowflake a uno strumento di terze parti.

>[!NOTE]
>
>Ogni strumento ha requisiti di connessione diversi; si consiglia di consultare la documentazione dello strumento specifico che si sta tentando di connettere.

* **URI** (sempre obbligatorio)
   * Nome di dominio dell&#39;account di Snowflake.  È contenuto in una parte del collegamento di accesso al Snowflake.
* **Nome utente** (sempre obbligatorio)
   * Il nome utente è elencato nella pagina delle informazioni della Data Warehouse in [!DNL Marketo Measure].
* **Password** (sempre obbligatorio)
   * Questa è la password impostata al primo accesso all&#39;account di Snowflake.  Per reimpostare la password, vedere i passaggi descritti in precedenza.
* **Nome database** (non sempre richiesto)
   * Il database è ciò che memorizza i dati nel Snowflake. Si tratta della risorsa di archiviazione. Il nome del database è elencato nella pagina Data Warehouse informazioni di [!DNL Marketo Measure].
* **Nome data warehouse** (non sempre richiesto)
   * Il warehouse esegue le query nel Snowflake. È la risorsa di calcolo.  Il nome del magazzino è elencato nella pagina delle informazioni sulla Data Warehouse in [!DNL Marketo Measure].

  ![](assets/data-warehouse-access-reader-account-9.png)
