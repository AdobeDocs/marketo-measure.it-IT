---
description: Accesso a Data Warehouse - Condivisione diretta - Documentazione del prodotto
title: Accesso Data Warehouse - Condivisione diretta
exl-id: 940c3316-5f94-4aa2-a656-aec5eb7b7450
feature: Data Warehouse
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Accesso Data Warehouse - Condivisione diretta {#data-warehouse-access-direct-share}

## Requisiti {#requirements}

Affinché [!DNL Marketo Measure] possa impostare una condivisione diretta al data warehouse, è necessario soddisfare i seguenti requisiti.

* Disponi di un’istanza Snowflake personalizzata.
* L&#39;istanza di Snowflake si trova nell&#39;area Snowflake di Azure East US 2.
* Hai fornito a [!DNL Marketo Measure] l&#39;ID del tuo account Snowflake.

## Limitazioni {#limitations}

[!DNL Marketo Measure] potrà configurare solo condivisioni dirette Snowflake con account situati in Azure East US 2 (si tratta di una limitazione in Marketo Measure, non in Snowflake). Se i dati devono essere resi disponibili in altre aree geografiche di Snowflake, è consigliabile creare una copia dei dati in un account di Snowflake che si trova in Azure East US 2 e utilizzare la funzionalità [Replica database Snowflake](https://docs.snowflake.com/en/user-guide/database-replication-intro.html){target="_blank"} per copiare i dati nell&#39;area o nell&#39;account di Snowflake desiderato.

## Immetti ID account Snowflake {#enter-snowflake-account-id}

Apri la sezione **Impostazioni** nell&#39;app Marketo Measure e passa alla pagina **Data Warehouse**. Nella sezione **Condivisione diretta**, immetti il tuo [ID account Snowflake](https://docs.snowflake.com/en/user-guide/admin-account-identifier.html){target="_blank"} nella casella fornita e fai clic su **Connetti**.

![](assets/data-warehouse-access-direct-share-1.png)

## Accesso alla condivisione {#accessing-the-share}

Dopo aver creato la condivisione per l&#39;ID account fornito, devi completare i [passaggi di configurazione](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"} nell&#39;istanza Snowflake per accedere ai dati.

>[!NOTE]
>
>È possibile scegliere qualsiasi nome di database desiderato. Puoi assegnare i privilegi a qualsiasi ruolo scelto, purché esista nella tua istanza di Snowflake.

* Utilizzare il ruolo Amministratore account

```
USE ROLE ACCOUNTADMIN
```

* Visualizza le condivisioni disponibili (mostra il nome della condivisione concessa)

```
SHOW SHARES
```

* Creare un database per la condivisione

```
CREATE DATABASE <database_name> FROM SHARE <provider_account>.<share_name>
```

* Concedere i privilegi sul database condiviso

```
GRANT IMPORTED PRIVILEGES ON DATABASE <database_name> TO ROLE <role_name>
GRANT IMPORTED PRIVILEGES ON ALL SCHEMAS IN DATABASE <database_name> TO ROLE <role_name>
```

Per istruzioni e passaggi più dettagliati per eseguire questi passaggi dall&#39;interfaccia utente di Snowflake, fai riferimento direttamente alla [documentazione di Snowflake](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"}.
