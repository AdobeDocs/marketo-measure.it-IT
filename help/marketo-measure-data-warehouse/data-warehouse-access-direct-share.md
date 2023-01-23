---
description: Accesso a Data Warehouse - Condivisione diretta - Documentazione del prodotto
title: Accesso Data Warehouse - Condivisione diretta
exl-id: 940c3316-5f94-4aa2-a656-aec5eb7b7450
source-git-commit: 36ee02b2dfc2651987f72fc7f02fe629717f02a0
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Accesso Data Warehouse - Condivisione diretta {#data-warehouse-access-direct-share}

## Requisiti {#requirements}

Per [!DNL Marketo Measure] per impostare una condivisione diretta nel data warehouse è necessario soddisfare i seguenti requisiti.

* Hai la tua istanza di Snowflake.
* L&#39;istanza del Snowflake si trova nell&#39;area del Snowflake Azure East US 2.
* Fornisci [!DNL Marketo Measure] con il tuo ID account Snowflake.

## Limitazioni {#limitations}

[!DNL Marketo Measure] potrà impostare azioni dirette di Snowflake solo con account situati in Azure East US 2 a causa delle limitazioni correnti del Snowflake. Se devi rendere disponibili i tuoi dati in altre aree del Snowflake, ti consigliamo di creare una copia dei dati in un account di Snowflake situato in Azure East US 2 e di sfruttare il [Replica del database di Snowflake](https://docs.snowflake.com/en/user-guide/database-replication-intro.html){target="_blank"} per copiare i dati nell’area geografica o nell’account di Snowflake desiderato.

## Immettere l&#39;ID account Snowflake {#enter-snowflake-account-id}

Apri **Impostazioni** nell’app Marketo Measure e passa alla sezione **Data Warehouse** pagina. In **Condivisione diretta** nella sezione [ID account Snowflake](https://docs.snowflake.com/en/user-guide/admin-account-identifier.html){target="_blank"} nella casella fornita e fai clic su **Connetti**.

![](assets/data-warehouse-access-direct-share-1.png)

## Accesso alla condivisione {#accessing-the-share}

Una volta creata la condivisione per l&#39;ID account fornito, devi completare la [fasi di configurazione](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"} all’interno dell’istanza del Snowflake per accedere ai dati.

>[!NOTE]
>
>È possibile scegliere qualsiasi nome di database desiderato. Puoi assegnare i privilegi a qualsiasi ruolo scelto, purché siano presenti nell’istanza di Snowflake.

* Utilizzare il ruolo Amministratore account

```
USE ROLE ACCOUNTADMIN
```

* Visualizza le azioni disponibili (verrà visualizzato il nome della quota concessa)

```
SHOW SHARES
```

* Crea un database per la condivisione

```
CREATE DATABASE <database_name> FROM SHARE <provider_account>.<share_name>
```

* Privilegi di sovvenzione nel database condiviso

```
GRANT IMPORTED PRIVILEGES ON DATABASE <database_name> TO ROLE <role_name>
GRANT IMPORTED PRIVILEGES ON ALL SCHEMAS IN DATABASE <database_name> TO ROLE <role_name>
```

Per istruzioni e passaggi più dettagliati per eseguire questi passaggi dall’interfaccia utente del Snowflake, fai riferimento a [Documentazione del Snowflake direttamente](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"}.
