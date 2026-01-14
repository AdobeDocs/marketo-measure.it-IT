---
description: Descrive come impostare e utilizzare un account di lettura per accedere al data warehouse di Marketo Measure
title: Accesso a Data Warehouse - Account Reader
exl-id: 2aa73c41-47ab-4f11-96d8-dafb642308fc
feature: Data Warehouse
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 1%

---

# Accesso a Data Warehouse - Account Reader {#data-warehouse-access-reader-account}

## Collegamento di accesso a Snowflake {#snowflake-access-link}

Per accedere al data warehouse di Snowflake, devi passare all’URL specifico del tuo account Snowflake. Per trovare questo collegamento di accesso, accedere a [!DNL Marketo Measure] e seguire la procedura riportata di seguito per accedere alla pagina delle informazioni di Data Warehouse.

1. In [!DNL Marketo Measure], nella parte superiore della pagina, fare clic su **[!UICONTROL My Account]** > **[!UICONTROL Settings]**.

   ![1. In Marketo Measure, nella parte superiore della pagina, fare clic su](assets/data-account-7.png)

1. Nel menu a sinistra, sotto Protezione, fare clic su **[!UICONTROL Data Warehouse]**.

   ![1. Nel menu a sinistra, in Protezione, fare clic su Data Warehouse.](assets/data-account-8.png)

1. Questa pagina contiene il collegamento al data warehouse di Snowflake e il nome utente.

   ![1. Questa pagina contiene il collegamento al data warehouse Snowflake e &#x200B;](assets/data-account-9.png)

   >[!NOTE]
   >
   >Questo è un account di sola lettura disponibile per la tua organizzazione, non solo per un singolo utente. Qualsiasi utente dell&#39;organizzazione che ha accesso a [!DNL Marketo Measure] può utilizzare questo account per accedere all&#39;account lettore di Snowflake Data Warehouse.

1. Fai clic sul collegamento fornito nell’URL di Snowflake per passare alla pagina di accesso di Snowflake in cui inserisci nome utente e password. _Se non si dispone della password, vedere la procedura seguente per reimpostarla_.

   ![1. Fai clic sul collegamento fornito nell&#39;URL di Snowflake, per visualizzare](assets/data-account-5.png)

1. Dopo aver effettuato l&#39;accesso, fare clic su **[!UICONTROL Worksheets]** nella parte superiore della pagina.

   ![1. Una volta effettuato l&#39;accesso, fare clic su Fogli di lavoro nella parte superiore di &#x200B;](assets/data-account-6.png)

1. Gli oggetti di database BIZIBLE_ROI_V3 si trovano sul lato sinistro dello schermo. Immettere Warehouse, Database e Schema dalle opzioni a discesa nella parte superiore della finestra della query. Dovrebbe essere disponibile una sola opzione per ciascuno di essi. Ora puoi eseguire le query all’interno dell’editor di query di Snowflake.

   ![1. Gli oggetti di database BIZIBLEROIV3 si trovano sul lato sinistro di &#x200B;](assets/data-account-4.png)

## Reimposta la password {#reset-your-password}

[!DNL Marketo Measure] non ha accesso alla tua password di accesso a Snowflake. Se è necessario reimpostare la password, fare clic sul pulsante [!UICONTROL Reset Password] nella pagina delle informazioni di Data Warehouse e seguire le istruzioni. Una password temporanea viene visualizzata immediatamente nell’interfaccia utente. Ti verrà chiesto di creare la tua password al prossimo accesso al data warehouse.

>[!NOTE]
>
>* La reimpostazione della password la reimposta per tutti [!DNL Marketo Measure] utenti dell&#39;organizzazione, non solo per l&#39;utente attualmente connesso.
>* Nell’interfaccia utente viene visualizzata solo la password temporanea. Non verrà inviata un’e-mail.

![Nell&#39;interfaccia utente viene visualizzata solo la password temporanea. Un&#39;e-mail](assets/data-account-3.png)

![Nell&#39;interfaccia utente viene visualizzata solo la password temporanea. Un&#39;e-mail](assets/data-account-1.png)

## Connessione a Snowflake tramite strumenti di terze parti {#connecting-to-snowflake-via-third-party-tools}

È necessario immettere alcune informazioni per collegare il data warehouse di Snowflake a uno strumento di terze parti.

>[!NOTE]
>
>Ogni strumento ha requisiti di connessione diversi; si consiglia di consultare la documentazione relativa allo strumento specifico che si sta tentando di connettere.

* **URI** (sempre obbligatorio)
   * Questo è il nome di dominio dell’account Snowflake. È contenuto all’interno di una parte del collegamento di accesso a Snowflake.
* **Nome utente** (sempre obbligatorio)
   * Il nome utente è elencato nella pagina delle informazioni di Data Warehouse in [!DNL Marketo Measure].
* **Password** (sempre richiesta)
   * Questa è la password che hai impostato al primo accesso al tuo account Snowflake. Per reimpostare la password, seguire la procedura descritta in precedenza.
* **Nome database** (non sempre richiesto)
   * Il database è ciò che memorizza i dati in Snowflake. Si tratta della risorsa di archiviazione. Il nome del database è elencato nella pagina delle informazioni di Data Warehouse in [!DNL Marketo Measure].
* **Nome data warehouse** (non sempre obbligatorio)
   * Il warehouse esegue le query in Snowflake. È la risorsa calcolata. Il nome del magazzino è elencato nella pagina delle informazioni di Data Warehouse in [!DNL Marketo Measure].

  ![Il warehouse esegue le query in Snowflake. È il &#x200B;](assets/data-account-2.png) calcolato
