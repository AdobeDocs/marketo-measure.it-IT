---
description: Accesso a Data Warehouse - Condivisione diretta - Documentazione del prodotto
title: Accesso Data Warehouse - Condivisione diretta
exl-id: 940c3316-5f94-4aa2-a656-aec5eb7b7450
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Accesso Data Warehouse - Condivisione diretta {#data-warehouse-access-direct-share}

**Requisiti**

Per [!DNL Marketo Measure] per impostare una condivisione diretta nel data warehouse è necessario soddisfare i seguenti requisiti.

* Hai la tua istanza di Snowflake.
* L&#39;istanza del Snowflake si trova nell&#39;area del Snowflake Azure East US 2.
* Fornisci [!DNL Marketo Measure] con il tuo ID account Snowflake.

**Limitazioni**

[!DNL Marketo Measure] potrà impostare azioni dirette di Snowflake solo con account situati in Azure East US 2 a causa delle limitazioni correnti del Snowflake. Se devi rendere disponibili i tuoi dati in altre aree del Snowflake, ti consigliamo di creare una copia dei dati in un account di Snowflake situato in Azure East US 2 e di sfruttare il [Replica del database di Snowflake](https://docs.snowflake.com/en/user-guide/database-replication-intro.html)funzionalità {target=&quot;_blank&quot;} per copiare i dati nell&#39;area/account di Snowflake di tua scelta.

**Accesso alla condivisione**

Una volta creata la condivisione per l&#39;ID account fornito, devi completare la [fasi di configurazione](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target=&quot;_blank&quot;} all&#39;interno dell&#39;istanza del Snowflake per accedere ai dati.

>[!NOTE]
>
>È possibile scegliere qualsiasi nome di database desiderato. Puoi assegnare i privilegi a qualsiasi regola scelta, purché sia presente nell’istanza di Snowflake.

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

Per istruzioni e passaggi più dettagliati per eseguire questi passaggi dall’interfaccia utente del Snowflake, fai riferimento a [Documentazione del Snowflake direttamente](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target=&quot;_blank&quot;}.
