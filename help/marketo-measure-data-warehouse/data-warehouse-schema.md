---
unique-page-id: 35586140
description: Data Warehouse schema - Marketo Measure - Documentazione del prodotto
title: Data Warehouse schema
exl-id: f1895eb1-a32d-4c43-93fb-0aa838527946
source-git-commit: 6e2d438da273511c3465d02eef6813f64e7aec5d
workflow-type: tm+mt
source-wordcount: '22615'
ht-degree: 4%

---

# Data Warehouse schema {#data-warehouse-schema}

Data Warehouse ti consente di tenere traccia di quanto desideri, di eseguire rapporti sui dati di attribuzione ovunque ti trovi e di collegarli ad altri set di dati.

>[!IMPORTANT]
>
>Le righe con un valore per _DELETED_DATE verranno mantenute per 15 giorni, quindi rimosse dal Snowflake. Le unità orarie Snowflake sono in UTC.

>[!NOTE]
>
>[Fai clic qui](#sample-queries) per visualizzare query di esempio in fondo a questo articolo.

## Diagrammi di relazione entità {#entity-relationship-diagrams}

La _Data Warehouse modello dati_ ERD mostra come i dati nel data warehouse devono fluire e essere collegati tra loro. Questo diagramma non include tutte le tabelle disponibili nel data warehouse perché alcune di esse rappresentano tabelle di mappatura, visualizzazioni di altre tabelle già presenti o tabelle obsolete che non è consigliabile utilizzare. Di seguito sono riportate le descrizioni dettagliate delle tabelle e delle colonne presenti nel data warehouse. Molte di queste tabelle contengono campi denormalizzati, tuttavia, questo diagramma è il modello dati consigliato, sfruttando invece i dati provenienti da tabelle dimensionali.

L&#39;ulteriore _Modello dati dimensionale annunci_ ERD presenta una panoramica del modo in cui le tabelle per le dimensioni specifiche degli annunci possono essere collegate meglio alle tabelle nel modello dati principale. Anche se le dimensioni degli annunci vengono denormalizzate in altre tabelle, questo rappresenta il modello consigliato per l’unione di queste dimensioni.

_Fare clic su un&#39;immagine per la relativa versione a dimensione intera_

<table style="table-layout:auto"> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td><strong>Data Warehouse modello dati</strong></td> 
   <td><strong>Modello dati dimensionale annunci</strong></td> 
  </tr> 
  <tr> 
   <td> 
    <div> 
     <p><a href="assets/data-warehouse-data-model.pdf"><img src="assets/data-warehouse-data-model-thumb.png"></a></p> 
    </div></td>
   <td> 
    <div> 
     <p><a href="assets/ads-dimensional-data-model.pdf"><img src="assets/ads-dimensional-data-model-thumb.png"></a></p>
    </div></td> 
  </tr> 
 </tbody> 
</table>

## Viste {#views}

### BIZ_ACCOUNTS {#biz-accounts}

Account importati dal sistema di origine.

<table>
  <tbody>
    <tr>
      <th><strong>Colonna</strong></th>
      <th><strong>Tipo di dati</strong></th>
      <th><strong>Descrizione</strong></th>
      <th><strong>Dati di esempio</strong></th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>L'ID account dal sistema di origine.</td>
      <td>0013100001kpAZxAAM</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione dell'account dal sistema di origine.</td>
      <td>2016-08-28 00:32:55.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data ultima modifica dell'account dal sistema di origine.</td>
      <td>2018-08-01 17:38:30.000</td>
    </tr>
    <tr>
      <td>NOME</td>
      <td>varchar</td>
      <td>Nome account dal sistema di origine.</td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>WEB_SITE</td>
      <td>varchar</td>
      <td>Sito web per l'account, come registrato nel sistema di origine, utilizzato per la mappatura da lead a account.</td>
      <td>www.adobe.com</td>
    </tr>
    <tr>
      <td>ENGAGEMENT_RATING</td>
      <td>varchar</td>
      <td>Un grado di lettera (A, B, C, D, N/D) generato dal [!DNL Marketo Measure] Modello di apprendimento automatico. Se ABM è disattivato, questo valore sarà nullo.</td>
      <td>B</td>
    </tr>
    <tr>
      <td>ENGAGEMENT_SCORE</td>
      <td>numero(38,19)</td>
      <td>Punteggio numerico calcolato da [!DNL Marketo Measure] Apprendimento automatico per generare il punteggio di coinvolgimento predittivo (Engagement_Rating). Se ABM è disattivato, questo valore sarà nullo.</td>
      <td>0.1417350147058800000</td>
    </tr>
    <tr>
      <td>DOMINIO</td>
      <td>varchar</td>
      <td>La versione ridotta del sito web, che memorizza solo il dominio.</td>
      <td>adobe</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>booleano</td>
      <td>Se il record viene eliminato o meno nel sistema di origine.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Proprietà personalizzate che [!DNL Marketo Measure] è stato importato dal sistema di origine in formato JSON.</td>
      <td>{"Account_Type__c": "Sicurezza", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ACCOUNT_TO_EMAILS {#biz-account-to-emails}

Tabella di mappatura tra gli indirizzi e-mail e gli account lead/contatti noti. Questa tabella sarà vuota se ABM è disattivato.

<table>
  <tbody>
    <tr>
    <th><strong>Colonna</strong></th>
      <th><strong>Tipo di dati</strong></th>
      <th><strong>Descrizione</strong></th>
      <th><strong>Dati di esempio</strong></th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>Un ID univoco per il record.</td>
      <td>0013800001MMPPiAAP_person@adobe.com|2022-01-05 17:22:13,000</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID account del sistema di origine.</p>
      </td>
      <td>
        <p>0013100001phrBAAAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-MAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Indirizzo e-mail mappato sull'account tramite relazioni di contatto o mappatura lead su account.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data ultima modifica dell'account dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-31 23:53:39.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di creazione dell'account dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-18 22:01:32.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il record viene considerato eliminato o meno.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ACTIVITIES {#biz-activities}

Attività importate da un sistema sorgente o da un account annuncio connesso.

<table>
  <tbody>
  <tr>
    <th><strong>Colonna</strong></th>
    <th><strong>Tipo di dati</strong></th>
    <th><strong>Descrizione</strong></th>
    <th><strong>Dati di esempio</strong></th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'ID attività dal sistema di origine.</p>
      </td>
      <td>
        <p>1678625515</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Id per il lead associato all’attività.</td>
      <td>
        <p>15530482</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del contatto associato all'attività.</p>
      </td>
      <td>
        <p>13792552</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACTIVITY_TYPE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID per il tipo di attività, dal sistema di origine.</p>
      </td>
      <td>
        <p>104</p>
      </td>
    </tr>
    <tr>
      <td>ACTIVITY_TYPE_NAME</td>
      <td>varchar</td>
      <td>Nome attività dal sistema di origine.</td>
      <td>
        <p>cambia stato in avanzamento</p>
      </td>
    </tr>
    <tr>
      <td>START_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di inizio dell'attività, dal sistema di origine.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>DATA_FINE</td>
      <td>timestapm_ntz</td>
      <td>Data di fine dell’attività, dal sistema di origine.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>CAMPAIGN_ID</td>
      <td>varchar</td>
      <td>ID per la campagna di cui l’attività fa parte dal sistema di origine.</td>
      <td>
        <p>li.508038570.147643566</p>
      </td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Identifica il tipo di sistema di origine.</td>
      <td>Marketo</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione della riga nel sistema di origine.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica apportata alla riga nel sistema di origine.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>IS_DELETD</td>
      <td>booleano</td>
      <td>Se il record viene considerato eliminato o meno nel sistema di origine.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>AD_FORM_ID</td>
      <td>varchar</td>
      <td>ID per il modulo annuncio di cui l’attività fa parte dal sistema di origine.</td>
      <td>li.507063119.3757704</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ADS {#biz-ads}

Annunci importati da qualsiasi account annuncio connesso.

<table>
  <tbody>
    <tr>
      <th>
        <p><strong>Colonna</strong></p>
      </th>
      <th>
        <p><strong>Tipo di dati</strong></p>
      </th>
      <th>
        <p><strong>Descrizione</strong></p>
      </th>
      <th>
        <p><strong>Dati di esempio</strong></p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per l'annuncio.</p>
      </td>
      <td>
        <p>fb.106851586409075.6052044288804.605204429004.60534577 66804</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'ID dell'annuncio dal sistema di origine.</p>
      </td>
      <td>
        <p>6053457066804</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’account dell’annuncio da cui è stato importato l’annuncio.</p>
      </td>
      <td>
        <p>fb.106851586409075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’account dell’annuncio da cui è stato importato l’annuncio.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Account</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id dell’inserzionista per l’annuncio, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’inserzionista dell’annuncio, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del gruppo di annunci per l’annuncio.</p>
      </td>
      <td>
        <p>fb.106851586409075.6052044288804.6052044290004</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del gruppo di annunci per l’annuncio.</p>
      </td>
      <td>
        <p>Set di annunci per l’annuncio B</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della campagna per l’annuncio.</p>
      </td>
      <td>
        <p>fb.106851586409075.6052044288804</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna per l’annuncio.</p>
      </td>
      <td>
        <p>Campagna per la generazione di lead</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se l’annuncio è ancora attivo nel sistema di origine.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se l’annuncio è stato eliminato o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:59.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui il record è stato importato per la prima volta dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:59.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’annuncio dal sistema di origine.</p>
      </td>
      <td>
        <p>Annuncio 2</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se l’annuncio deve essere aggiornato o meno per [!DNL Marketo Measure] assegnazione tag.</p>
        <p>(Campo diagnostico, utilizzato dall'elaborazione interna.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Campo diagnostico, utilizzato per l’elaborazione interna.</td>
      <td>
        <p>fb.106851586409075.6052044288804.6052044290004</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'oggetto o l'entità principale per questa tabella. In questo caso, "Aggiungi".</p>
      </td>
      <td>
        <p>Annuncio</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del provider di annunci per l’annuncio.</p>
      </td>
      <td>
        <p>Facebook</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L’URL della pagina di destinazione.</p>
        <p>(campo diagnostico, per elaborazione interna.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valore precedente per URL_CURRENT.</p>
        <p>(campo diagnostico, per elaborazione interna.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Di cosa sarà decorato l’URL [!DNL Marketo Measure] Parametri.</p>
        <p>(campo diagnostico, per elaborazione interna.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_ALTENATIVES</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Importata dal sistema di origine.</p>
        <p>(campo diagnostico, per elaborazione interna.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ADVERTISERS {#biz-advertisers}

Gli inserzionisti hanno importato da qualsiasi account pubblicitario collegato.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per l'inserzionista.</p>
      </td>
      <td>
        <p>dc.6114.9143143</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>L'ID inserzionista dal sistema di origine.</td>
      <td>9143143</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’account dell’annuncio da cui è stato importato l’annuncio.</p>
      </td>
      <td>
        <p>fb.106851586409075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’account dell’annuncio da cui è stato importato l’annuncio.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Account</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id dell’inserzionista, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell'inserzionista, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un gruppo di annunci sopra l’inserzionista in alcuna gerarchia di annunci.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un gruppo di annunci sopra l’inserzionista in alcuna gerarchia di annunci.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste una campagna pubblicitaria sopra l’inserzionista in alcuna gerarchia di annunci.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste una campagna al di sopra dell’inserzionista pubblicitario in alcuna gerarchia di annunci.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se l’inserzionista è ancora attivo nel sistema di origine.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se l’inserzionista è stato eliminato o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:59.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui il record è stato importato per la prima volta dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:59.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell'inserzionista dal sistema di origine.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se l’inserzionista deve essere aggiornato o meno per [!DNL Marketo Measure] assegnazione tag.</p>
        <p>(Campo diagnostico, utilizzato dall'elaborazione interna.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Campo diagnostico, utilizzato per l’elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'oggetto o l'entità principale per questa tabella. In questo caso, "Inserzionista".</p>
      </td>
      <td>
        <p>Inserzionista</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Provider di annunci per l’inserzionista.</p>
      </td>
      <td>
        <p>Doppio</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_ACCOUNTS {#biz-ad-accounts}

Account annunci importati da qualsiasi account annuncio connesso.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un identificatore univoco per l'account dell'annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>L'ID account dell'annuncio dal sistema di origine.</td>
      <td>
        <p>6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Si prevede che sia nullo perché si tratta del record per gli Ad Accounts nella gerarchia degli annunci.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Si prevede che sia nullo perché si tratta del record per gli Ad Accounts nella gerarchia degli annunci.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un inserzionista sopra gli Ad Accounts in alcuna gerarchia di annunci.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un inserzionista sopra gli Ad Accounts in alcuna gerarchia di annunci.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Si prevede che sia nullo perché non esiste un gruppo di annunci sopra gli account annunci in alcuna gerarchia di annunci.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Si prevede che sia nullo perché non esiste un gruppo di annunci sopra gli account annunci in alcuna gerarchia di annunci.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Si prevede che sia nullo perché non vi è alcuna campagna pubblicitaria sopra gli Account annuncio in alcuna gerarchia di annunci.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Si prevede che sia nullo perché non vi è alcuna campagna pubblicitaria sopra gli Account annuncio in alcuna gerarchia di annunci.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se l'account dell'annuncio è ancora attivo nel sistema di origine.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se l’account annuncio è stato eliminato o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-09-06 12:54:37.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui il record è stato importato per la prima volta dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nome dell'account dell'annuncio dal sistema di origine.</td>
      <td>
        <p>[!DNL Marketo Measure] Account annuncio</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se l’inserzionista deve essere aggiornato o meno per [!DNL Marketo Measure] assegnazione tag.</p>
        <p>(Campo diagnostico, utilizzato dall'elaborazione interna.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Campo diagnostico, utilizzato per l’elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'oggetto o l'entità principale per questa tabella. In questo caso, "Account".</p>
      </td>
      <td>
        <p>Account</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del provider di annunci per l'account dell'annuncio.</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_CURRENCY_UNIT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il codice valuta utilizzato per l'Ad Account dal sistema di origine.</p>
      </td>
      <td>
        <p>USD</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COMPANY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per elaborazione interna.</td>
      <td>1933789</td>
    </tr>
    <tr>
      <td>
        <p>SORGENTE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Viene analizzato dall’URL da utm_source.</td>
      <td>
        <p>Social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIO</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Viene analizzato dall’URL da utm_medium.</td>
      <td>
        <p>lisu07261601</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_COST</p>
      </td>
      <td>
        <p>numero(38,19)</p>
      </td>
      <td>
        <p>La quantità di spesa importata per gli ultimi 30 giorni, applicabile solo ad AdWords.</p>
      </td>
      <td>
        <p>17260.000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_IMPRESSIONS</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Il numero di impression degli ultimi 30 giorni, applicabile solo ad AdWords.</p>
      </td>
      <td>
        <p>730060</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_CLICKS</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Il numero di clic degli ultimi 30 giorni, applicabile solo ad AdWords.</p>
      </td>
      <td>
        <p>3400</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_CONVERSIONS</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Il numero di conversioni riportate negli ultimi 30 giorni, applicabile solo ad AdWords.</p>
      </td>
      <td>
        <p>180</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il modello di tracciamento aggiunto a livello di account annuncio per AdWords o Bing per l’assegnazione di tag alle pagine di destinazione.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>-4609512587744160000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_CAMPAIGNS {#biz-ad-campaigns}

Campagne importate da account annunci, sistemi di origine, utm e rapporti automatici collegati.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id univoco per la campagna.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>L'ID campagna dal sistema di origine.</td>
      <td>
        <p>285114995</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’account dell’annuncio da cui è stata importata la campagna.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’account dell’annuncio da cui è stata importata la campagna.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id dell’inserzionista per la campagna, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’inserzionista per la campagna, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un gruppo di annunci sopra la campagna in alcuna gerarchia di annunci.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un gruppo di annunci sopra la campagna in alcuna gerarchia di annunci.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id univoco per la campagna, utilizza invece il campo ID .</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna, utilizza invece il campo Nome .</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la campagna è ancora attiva o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se la campagna è stata eliminata o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui il record è stato importato per la prima volta dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna.</p>
      </td>
      <td>
        <p>Retargeting dei partner</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se la campagna deve essere aggiornata o meno per [!DNL Marketo Measure] assegnazione tag.</p>
        <p>(Campo diagnostico, utilizzato dall'elaborazione interna.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Campo diagnostico, utilizzato per l’elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'oggetto o l'entità principale per questa tabella. In questo caso, "Campaign".</p>
      </td>
      <td>
        <p>Campaign</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del provider di annunci per la campagna.</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DAILY_BUDGET</p>
      </td>
      <td>
        <p>numero(38,19)</p>
      </td>
      <td>
        <p>Il budget giornaliero impostato nell’Ad Platform per la campagna.</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il modello di tracciamento aggiunto a livello di Campaign per AdWords o Bing per assegnare tag alle pagine di destinazione.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>-6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_FORMS {#biz-ad-forms}

Ad Forms importato da qualsiasi account annuncio collegato.

<table>
  <tr>
    <th>
      <p>Colonna</p>
    </th>
    <th>
      <p>Tipo di dati</p>
    </th>
    <th>
      <p>Descrizione</p>
    </th>
    <th>
      <p>Dati di esempio</p>
    </th>
  </tr>
  <tbody>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per il modulo annuncio.</p>
      </td>
      <td>
        <p>li.507063119.3757704</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’account dell’annuncio da cui è stato importato il modulo dell’annuncio.</p>
      </td>
      <td>
        <p>li.507063119</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’account dell’annuncio da cui è stato importato il modulo dell’annuncio.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Stato eliminato dal sistema di origine. Impostato su eliminato se lo stato è Bozza, Archiviato o Annullato.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui il record è stato importato per la prima volta dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del modulo annuncio.</p>
      </td>
      <td>
        <p>Ebook NSPA LGF (maggio 2020)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'oggetto o l'entità principale per questa tabella. In questo caso, "AdForm".</p>
      </td>
      <td>
        <p>AdForm</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del provider di annunci per il modulo di annuncio.</p>
      </td>
      <td>
        <p>LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DESCRIZIONE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Descrizione del modulo annuncio.</p>
      </td>
      <td>
        <p>Scopri come l'automazione intelligente può aumentare l'efficienza dei processi nelle applicazioni di credito per il rifinanziamento dei mutui ipotecari.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LINEA GUIDA</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Titolo del modulo annuncio.</td>
      <td>
        <p>È ora di automatizzare il processo di rifinanziamento delle applicazioni</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>URL di destinazione del modulo annuncio.</td>
      <td>
        <p>https://adobe.com/blog/refinancing-application-process/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DOMANDE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Elenco delle domande per il modulo annuncio.</td>
      <td>
        <p>Nome:Cognome:Indirizzo e-mail:Paese/Regione:Titolo del lavoro:Nome della società</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STATO</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Stato del modulo annuncio.</p>
      </td>
      <td>
        <p>presentato</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>SOURCE_ID</td>
      <td>varchar</td>
      <td>ID per l'origine da cui è stato creato il record.</td>
      <td>aw.3284209</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_GROUPS {#biz-ad-groups}

Gruppi di annunci importati da qualsiasi account di annunci collegato.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per il gruppo di annunci.</p>
      </td>
      <td>
        <p>aw.6601259029.317737955.23105326115</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>ID gruppo di annunci dal sistema di origine.</td>
      <td>
        <p>23105326115</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell'account dell'annuncio da cui è stato importato il gruppo di annunci.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’account dell’annuncio da cui è stato importato il gruppo di annunci.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un gruppo di annunci nella gerarchia degli annunci Doubleclick.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un gruppo di annunci nella gerarchia degli annunci Doubleclick.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché si tratta del record per il gruppo di annunci nella gerarchia.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché si tratta del record per il gruppo di annunci nella gerarchia.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della campagna per il gruppo di annunci.</p>
      </td>
      <td>
        <p>aw.6601259029.317737955</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna per il gruppo di annunci.</p>
      </td>
      <td>
        <p>Attribuzione ricavi</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se l'account dell'annuncio è ancora attivo nel sistema di origine.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se l’account annuncio è stato eliminato o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:14.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui il record è stato importato per la prima volta dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:14.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del gruppo di annunci.</p>
      </td>
      <td>
        <p>Attribuzione ricavi - Basato su conto</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se l’inserzionista deve essere aggiornato o meno per [!DNL Marketo Measure] assegnazione tag.</p>
        <p>(Campo diagnostico, utilizzato dall'elaborazione interna.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Campo diagnostico, utilizzato per l’elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'oggetto o l'entità principale per questa tabella. In questo caso, "AdGroup".</p>
      </td>
      <td>
        <p>AdGroup</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del provider di annunci per il gruppo di annunci.</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NETWORK_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il/i supporto/i su cui è in esecuzione il gruppo di annunci.</p>
      </td>
      <td>
        <p>Ricerca, visualizzazione, YouTube_Search, YouTube_Watch</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il modello di tracciamento aggiunto a livello di account annuncio per AdWords o Bing per l’assegnazione di tag alle pagine di destinazione.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>-5594512713562690000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_PROVIDERS

<p>Fornitori di annunci da qualsiasi account annuncio connesso, compresa una voce per se segnalata autonomamente, se applicabile.</p>

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per il provider di annunci.</p>
      </td>
      <td>
        <p>Bing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del provider di annunci.</p>
      </td>
      <td>
        <p>Bing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>4783788151269206864</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ATTRIBUTION_TOUCHPOINTS {#biz-attribution-touchpoints}

<p>Punti di contatto per l’attribuzione dell’acquirente, tutti i punti di contatto associati a un’opportunità.</p>
<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per il punto di contatto dell’attribuzione dell’acquirente (BAT).</p>
      </td>
      <td>
        <p>BAT2_0060Z0000lFHtOQAW_</p>
        <p>0030Z0003K5bpKQAR_2017-06-20:01-05-20-6193330.0b5c5678807c</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-09-01 04:53:53.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id per l’opportunità a cui viene attribuito il BAT.</p>
      </td>
      <td>
        <p>0060Z00000lFHtOQAW</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del contatto associato al BAT.</p>
      </td>
      <td>
        <p>0030Z00003K5bpKQAR</p>
      </td>
    </tr>
    <tr>
      <td>E-MAIL</td>
      <td>varchar</td>
      <td>Indirizzo e-mail associato alla BAT.</td>
      <td>person@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id per l’account a cui viene attribuito il BAT.</p>
      </td>
      <td>
        <p>0013100001otbIAAAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_TOUCHPOINT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id per il punto di contatto utente che ha generato il BAT.</p>
      </td>
      <td>
        <p>person@adobe.com_00v1B00003ZbWzHQAV</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data del punto di contatto.</p>
      </td>
      <td>
        <p>2017-06-20 01:05:20.000</p>
      </td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>ID del visitatore associato al BAT.</td>
      <td>v_277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>MARKETING_TOUCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tipo di attività, visita web, modulo web, chat web, chiamata telefonica, campagna [CRM] o attività [CRM]. In CRM è indicato come "tipo di punto di contatto".</p>
      </td>
      <td>
        <p>Modulo Web</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CANALE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il canale in cui rientra il punto di contatto, come definito nelle definizioni del canale personalizzato all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Canale di marketing - Percorso".</p>
      </td>
      <td>
        <p>Social.LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore del segmento per la prima categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</p>
      </td>
      <td>
        <p>ABC</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore del segmento per la seconda categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</p>
      </td>
      <td>
        <p>Sì</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY3</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore del segmento per la terza categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</p>
      </td>
      <td>
        <p>SMB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY4</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per la quarta categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td>
        <p>Nuove attività</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY5</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per la quinta categoria in cui rientra il punto di contatto, come definito nelle definizioni del segmento all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY6</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per la 6a categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY7</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per la settima categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY8</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per l’8a categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY9</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per la 9a categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY10</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per la decima categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY11</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per l’undicesima categoria in cui si trova il punto di contatto, come definito nelle definizioni del segmento all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY12</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per la dodicesima categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY13</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per la tredicesima categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY14</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per la quattordicesima categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY15</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per la quindicesima categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NOME_BROWSER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall'indirizzo javascript e IP, il browser rilevato che l'utente era attivo durante la sessione.</p>
      </td>
      <td>
        <p>Chrome</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall'indirizzo javascript e IP, la versione rilevata del browser su cui l'utente si trovava durante la sessione.</p>
      </td>
      <td>
        <p>58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, la piattaforma rilevata dall’utente durante la sessione.</p>
      </td>
      <td>
        <p>Mac</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, la versione rilevata della piattaforma su cui l’utente si trovava durante la sessione.</p>
      </td>
      <td>
        <p>10_12</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La prima pagina di destinazione della sessione che ha generato un punto di contatto. In CRM è indicato come "Pagina di destinazione".</p>
      </td>
      <td>
        <p>http://www.adobe.com/blog/uncover- verità dietro costo per lead</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La prima pagina di destinazione della sessione che ha generato un punto di contatto. Una pagina di destinazione non elaborata conterrà tutti i parametri di query nell’URL. In CRM è indicato come "Pagina di destinazione - Raw".</p>
      </td>
      <td>
        <p>http://www.adobe.com/blog/uncover-truth -behind-cost-per-lead?utm_content=27322869&amp;utm_ medium=social&amp;utm_source=linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>In genere la pagina di destinazione esterna immediatamente prima che l’utente acceda al sito web. In CRM è indicato come "Pagina referente".</p>
      </td>
      <td>
        <p>https://www.linkedin.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>In genere la pagina di destinazione esterna immediatamente prima che l’utente acceda al sito web. Una pagina referente non elaborata può contenere parametri di query nell’URL. In CRM è indicato come "Pagina referente - Raw".</p>
      </td>
      <td>
        <p>https://www.linkedin.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODULO_PAGINA</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il primo modulo registrato in una sessione che ha generato un punto di contatto. Gli invii dei moduli successivi non verranno visualizzati nella tabella Attribution_Touchpoints, ma nella tabella Form_Submit. In CRM è indicato come "URL del modulo".</p>
      </td>
      <td>
        <p>http://info.adobe.com/intro-guide-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il primo modulo registrato in una sessione che ha generato un punto di contatto. Gli invii dei moduli successivi non verranno visualizzati nella tabella Attribution_Touchpoints, ma nella tabella Form_Submit. Una pagina modulo non elaborata può contenere parametri di query nell’URL. In CRM è indicato come "URL modulo - Raw".</p>
      </td>
      <td>
        <p>http://info.adobe.com/intro-guide-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell’invio del modulo.</p>
      </td>
      <td>
        <p>2017-06-20 01:06:41.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITTÀ</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, la città rilevata in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>San Francisco</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGIONE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, la regione rilevata in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>California</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAESE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, il paese rilevato in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>Stati Uniti</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIO</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Utilizzato per definire il mezzo che ha portato al punto di contatto. Questo può essere analizzato dall’URL da utm_medium. Oppure, se [!DNL Marketo Measure] è in grado di risolvere un annuncio, può essere valori come "cpc" o "display".</p>
      </td>
      <td>
        <p>sociale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Utilizzato per definire la sorgente che ha generato il punto di contatto. Questo può essere analizzato dall'URL da utm_source, generalmente impostato come "Campaign CRM" se è stato sincronizzato dal CRM, o se [!DNL Marketo Measure] è in grado di risolvere un annuncio, possono essere valori come "Google AdWords" o "Facebook". In CRM è indicato come "Origine punto di contatto".</p>
      </td>
      <td>
        <p>linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore immesso dall’utente nel browser per la ricerca e finito sul sito web. A seconda delle parole chiave acquistate, potrebbe corrispondere o meno alle parole chiave acquistate dalla piattaforma di ricerca a pagamento.</p>
      </td>
      <td>
        <p>google [!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Piattaforma di annunci [!DNL Marketo Measure] è stato in grado di risolvere da, tipicamente uno dei nostri partner di integrazione.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’account dell’annuncio da cui è stata risolta l’inserzione.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’account dell’annuncio da cui è stata risolta l’inserzione.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’inserzionista dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’inserzionista dall’account dell’annuncio dal quale l’annuncio è stato risolto. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del sito dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del sito dall’account dell’annuncio dal quale è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>blocco stradale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della campagna dall’account dell’annuncio da cui è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029.317738075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna dall’account dell’annuncio dal quale è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>Attribuzione di marketing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del gruppo di annunci dall'account dell'annuncio da cui è stato risolto l'annuncio. Questo vale solo per Google Adwords.</p>
      </td>
      <td>
        <p>aw.6601259029.317738075.23105327435</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del gruppo di annunci dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale solo per Google AdWords.</p>
      </td>
      <td>
        <p>Attribuzione marketing - Generale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’annuncio dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>
        <p>dc.6114.8882972.25272734.492579576</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’annuncio dall’account dell’annuncio dal quale l’annuncio è stato risolto. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>
        <p>Webinar sul budget - barra laterale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del creativo dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>aw.6601259029.317738075.23105327435.182716179597</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del creativo dall’account dell’annuncio dal quale è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Attribuzione di marketing B2B</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La prima riga del Creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Scarica la guida CMO</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La seconda riga del creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Scopri come l’attribuzione misura il ROI collegando le attività di marketing ai ricavi</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La pagina di destinazione che fa clic dall’annuncio di ricerca, estratta dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>http://info.adobe.com/cmos-guide-to-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il nome dell’URL descrittivo mostrato nell’annuncio di ricerca, estratto dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>http://info.adobe.com/CMOs-Guide</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della parola chiave acquistata dall’acquisto di ricerca a pagamento, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>aw.6601259029.317738075.23105327435.4838421670</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della parola chiave acquistata dall’acquisto di ricerca a pagamento, estratta dall’account dell’annuncio dal quale l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca)</p>
      </td>
      <td>
        <p>"attribuzione marketing"</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il tipo di corrispondenza trovato tra la frase di ricerca e la parola chiave acquistata.</p>
      </td>
      <td>
        <p>Esatto</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FIRST_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se questo punto di contatto viene trattato o meno come il primo tocco del percorso di opportunità.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_LEAD_CREATION_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se questo punto di contatto viene trattato o meno come punto di contatto per la creazione di un lead, viene toccato dal percorso di opportunità.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_OPP_CREATION_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se questo punto di contatto viene trattato o meno come la creazione di opportunità tocca il percorso di opportunità.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CLOSED_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se questo punto di contatto viene trattato o meno come il tocco di chiusura del percorso di opportunità.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGES_TOUCHED</p>
      </td>
      <td>varchar</td>
      <td>Questo campo è stato dichiarato obsoleto. Utilizzare le tabelle Stage_Transitions per informazioni sull'area di visualizzazione.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se questo punto di contatto ha compilato un modulo durante la sessione.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IMPRESSION_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se questo punto di contatto viene trattato o meno come la prima impressione del percorso di opportunità</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>La percentuale calcolata allocata a questo punto di contatto perché si tratta di un primo contatto (consulta Is_First_Touch).</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_ANON_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>Percentuale calcolata allocata a questo punto di contatto perché si tratta di un contatto per la creazione di lead (consulta Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>U_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>La percentuale calcolata allocata a questo punto di contatto perché fa parte di un tocco a forma di u (consulta Is_First_Touch e Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>W_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>La percentuale calcolata allocata a questo punto di contatto perché fa parte di un tocco a forma di w (vedere Is_First_Touch, Is_Lead_Creation_Touch e Is_Opp_Creation_Touch).</p>
      </td>
      <td>
        <p>0.0153374234214425</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FULL_PATH_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>La percentuale calcolata allocata a questo punto di contatto perché fa parte di un modello di percorso completo (vedere Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch).</p>
      </td>
      <td>
        <p>0.0143061513081193</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CUSTOM_MODEL_PERCENTAGE</p>
      </td>
      <td>numero(22,19)</td>
      <td>La percentuale calcolata allocata a questo punto di contatto perché fa parte di un modello personalizzato (vedere Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch).</td>
      <td>0.0143061513081193</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se questo punto di contatto viene eliminato.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_ROW_KEY</p>
      </td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CAMPAIGN_MEMBERS {#biz-campaign-members}

Membri della campagna importati dal sistema di origine. Questa tabella sarà vuota se la sincronizzazione di Campaign è disabilitata.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID membro della campagna dal sistema di origine.</p>
      </td>
      <td>
        <p>00v0Z00001VVzdLQAT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell’ultima modifica del membro della campagna, dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-31 20:49:54.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di creazione del membro della campagna dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-31 20:49:54.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_TOUCH_POINT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data e ora impostate dal cliente per ignorare la data della campagna e utilizzare questo valore per Data punto di contatto.</p>
      </td>
      <td>
        <p>2018-08-30 18:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id per il lead a cui è associato il membro della campagna.</p>
      </td>
      <td>
        <p>00Q0Z000013dw4GUAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>E-mail per il lead a cui è associato il membro della campagna.</p>
      </td>
      <td>
        <p>persona@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id per il contatto al quale è associato il membro della campagna.</p>
      </td>
      <td>
        <p>00331000032hMxRAAU</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>E-mail per il contatto al quale è associato il membro della campagna.</p>
      </td>
      <td>
        <p>persona@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STATO</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Stato del membro della campagna, in genere impostato su Inviato o Rispondato o su un altro valore personalizzato. Questo stato è associato a Campaign_Sync_Type per determinare per quali membri della campagna creare i punti di contatto.</p>
      </td>
      <td>
        <p>Inviato</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_RESPONDED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se il membro della campagna è stato contrassegnato come "Risposta" dal selettore di stato.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_RESPONDED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui il membro della campagna ha risposto per la prima volta.</p>
      </td>
      <td>
        <p>2018-08-30 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna correlata di cui il membro della campagna fa parte.</p>
      </td>
      <td>
        <p>Interviste rapido CMO</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della campagna correlata di cui il membro della campagna fa parte.</p>
      </td>
      <td>
        <p>7010Z000001TcKlQAK</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tipo selezionato nella relativa campagna di cui fa parte il membro della campagna. Il tipo viene utilizzato per mappare il canale di marketing.</p>
      </td>
      <td>
        <p>Offline</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_SYNC_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Determina per quali membri della campagna creare i punti di contatto. I valori possibili sono: Include_All, Include_Responded, Exclude_All.</p>
      </td>
      <td>
        <p>Includi_tutto</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SYNC_STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Campo di audit, indica se è stato generato un punto di contatto dell’acquirente per il lead. Se non è stato creato alcun punto di contatto, viene fornito il motivo per cui non è stato qualificato.</p>
      </td>
      <td>
        <p>Nessun punto di contatto: Data fuori modello</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_SYNC_STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Campo Audit, indica se è stato generato un punto di contatto dell'acquirente per il contatto. Se non è stato creato alcun punto di contatto, viene fornito il motivo per cui non è stato qualificato.</p>
      </td>
      <td>
        <p>Punto di contatto creato</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPP_SYNC_STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Campo di audit, indica se è stato generato un punto di contatto di attribuzione dell’acquirente per l’opportunità. Se non è stato creato alcun punto di contatto, viene fornito il motivo per cui non è stato qualificato.</p>
      </td>
      <td>
        <p>Punto di contatto creato</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il record viene considerato eliminato o meno nel sistema di origine .</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Proprietà personalizzate che [!DNL Marketo Measure] è stato importato dal sistema di origine in formato JSON.</td>
      <td>{"Campaign_Type__c":"Dinners","Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CHANNELS {#biz-channels}

Canali di marketing, come creato nel [!DNL Marketo Measure] applicazione.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per il canale.</p>
      </td>
      <td>
        <p>Ricerca organica.Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del canale.</p>
      </td>
      <td>
        <p>Ricerca organica.Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>La data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CONTACTS {#biz-contacts}

Contatti importati dal sistema di origine.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID contatto dal sistema di origine.</p>
      </td>
      <td>
        <p>0030Z00003OzioeQAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record Contatto dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-09-05 05:17:53.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di creazione del record Contatto dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-09-05 05:17:51.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-MAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Indirizzo e-mail del contatto dal sistema di origine.</p>
      </td>
      <td>
        <p>persona@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNTID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell'account relativo al contatto.</p>
      </td>
      <td>
        <p>0013100001b44aGAAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Origine in cui è stato creato il lead.</p>
      </td>
      <td>
        <p>Pubblicità</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Fase corrente del contatto, riconosciuta come fase personalizzata che può essere creata nel [!DNL Marketo Measure] applicazione.</p>
      </td>
      <td>
        <p>Demo pianificata</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE_PREVIOUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tutte le fasi precedenti del contatto, riconosciute come fasi personalizzate che possono essere create nel [!DNL Marketo Measure] applicazione.</p>
      </td>
      <td>
        <p>Apri - Contatto</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ODDS_OF_CONVERSION</p>
      </td>
      <td>
        <p>numero(38,19)</p>
      </td>
      <td>
        <p>La [!DNL Marketo Measure] algoritmo per stimare se un contatto aiuterà un'opportunità a chiudersi in base all'età e allo stadio</p>
      </td>
      <td>
        <p>.290034</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La [!DNL Marketo Measure] ID cookie utilizzato per popolare da un partner di integrazione per mappare un evento offline a una sessione web. Requisito: Abilita tracciamento chiamate: True</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il record viene eliminato o meno nel sistema di origine.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>IS_DUPLICATE</td>
      <td>booleano</td>
      <td>Utilizzato per deduplicare i record se è configurata sia un’integrazione CRM che Marketo. Se sono presenti duplicati, il contatto Marketo è contrassegnato come true.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Indica se il record proviene da un’integrazione CRM o Marketo.</td>
      <td>Crm</td>
    </tr>
    <tr>
      <td>NEW_SYSTEM_ID</td>
      <td>varchar</td>
      <td>Mappa una persona da un'integrazione Marketo con un contatto da un'integrazione CRM. Se esiste sia un’integrazione CRM che Marketo, il valore è l’ID corrispondente.</td>
      <td>1234 / 00Q0Z00001OohgTUAR</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Proprietà personalizzate che [!DNL Marketo Measure] è stato importato dal sistema di origine in formato JSON.</td>
      <td>{"Contact_Type__c":"CMO", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>3263982503087870000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CONVERSION_RATES {#biz-conversion-rates}

Tassi di conversione della valuta importati dal sistema di origine.

<table>
  <tbody>
    <tr>
      <th>Colonna</th>
      <th>Tipo di dati</th>
      <th>Descrizione</th>
      <th>Dati di esempio</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>number(38,0)</td>
      <td>Un ID univoco per il record.</td>
      <td>-5942345438803054604</td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>number(38,0)</td>
      <td>Valore ID per la valuta.</td>
      <td>7493833133899044458</td>
    </tr>
    <tr>
      <td>SOURCE_ISO_CODE</td>
      <td>varchar</td>
      <td>Codice ISO valuta, dal sistema di origine.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>START_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di inizio del tasso di conversione.</td>
      <td>2018-11-01 00:00:00.000</td>
    </tr>
    <tr>
      <td>DATA_FINE</td>
      <td>timestamp_ntz</td>
      <td>Data di inizio successiva per il tasso di conversione. (La data di fine del tasso di conversione è end_date meno 1 giorno.)</td>
      <td>2018-09-01 00:00:00.000</td>
    </tr>
    <tr>
      <td>CONVERSION_RATE</td>
      <td>number(38,0)</td>
      <td>Tasso utilizzato per convertire la valuta nella valuta aziendale.</td>
      <td>0.76728300</td>
    </tr>
    <tr>
      <td>IS_CURRENT</td>
      <td>booleano</td>
      <td>La semantica di questo campo è stata danneggiata. Non usare.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel sistema di origine.</td>
      <td>2019-03-30 00:54:50.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel sistema di origine.</td>
      <td>2019-03-30 00:54:50.000</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>booleano</td>
      <td>Se il record viene considerato eliminato o meno nel sistema di origine.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_COSTS {#biz-costs}

Dati di costo importati da account annunci connessi o da spese di marketing segnalate autonomamente.

<table>
  <tbody>
    <tr>
      <th>Colonna</th>
      <th>Tipo di dati</th>
      <th>Descrizione</th>
      <th>Dati di esempio</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>Un ID univoco per il record Costo.</td>
      <td>aw.6601259029.285114995.21703163075.[Visualizzazione AdWords]_2018-09-06</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record.</td>
      <td>2018-09-06 12:22:45.000</td>
    </tr>
    <tr>
      <td>COST_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il costo è stato sostenuto (o attribuito).</td>
      <td>2018-09-06 00:00:00.000</td>
    </tr>
    <tr>
      <td>SORGENTE</td>
      <td>varchar</td>
      <td>Origine del costo segnalato.</td>
      <td>[Visualizzazione di AdWords]</td>
    </tr>
    <tr>
      <td>COST_IN_MICRO</td>
      <td>number(38,0)</td>
      <td>Costo in milioni. L’utente dovrà dividere il valore per 1000000.</td>
      <td>1410000</td>
    </tr>
    <tr>
      <td>CLIC</td>
      <td>number(38,0)</td>
      <td>Numero di clic segnalati per il gruppo del giorno.</td>
      <td>4</td>
    </tr>
    <tr>
      <td>IMPRESSIONI</td>
      <td>number(38,0)</td>
      <td>Numero di impression riportate per il gruppo del giorno.</td>
      <td>4187</td>
    </tr>
    <tr>
      <td>ESTIMATED_TOTAL_POSSIBLE_IMPRESSIONS</td>
      <td>number(38,0)</td>
      <td>Numero totale di impression stimate da DCM per il gruppo del giorno.</td>
      <td>5024</td>
    </tr>
    <tr>
      <td>AD_PROVIDER</td>
      <td>varchar</td>
      <td>Provider per il quale è stato estratto il costo.</td>
      <td>Google</td>
    </tr>
    <tr>
      <td>CHANNEL_UNIQUE_ID</td>
      <td>varchar</td>
      <td>ID per il canale di marketing, creato da [!DNL Marketo Measure].</td>
      <td>Display.Google</td>
    </tr>
    <tr>
      <td>CHANNEL_NAME</td>
      <td>varchar</td>
      <td>Nome del canale di marketing, creato dal cliente nel [!DNL Marketo Measure] app.</td>
      <td>Display.Google</td>
    </tr>
    <tr>
      <td>CHANNEL_IS_AGGREGATABLE_COST</td>
      <td>booleano</td>
      <td>Indica se la riga contiene il costo che può essere sommato dal canale. (ad esempio, per ottenere Costo canale, somma le righe in cui questa colonna è uguale a vero).</td>
      <td>false</td>
    </tr>
    <tr>
      <td>ADVERTISER_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Id dell’inserzionista estratto dalla connessione Ad, in particolare per le connessioni Doubleclick.</td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>ADVERTISER_NAME</td>
      <td>varchar</td>
      <td>Nome dell’inserzionista estratto dalla connessione Ad, in particolare per le connessioni Doubleclick.</td>
      <td>[!DNL Marketo Measure] Marketing analytics</td>
    </tr>
    <tr>
      <td>ADVERTISER_IS_AGGREGATABLE_COST</td>
      <td>booleano</td>
      <td>Indica se la riga contiene il costo che può essere sommato da Advertiser (Inserzionista). (ovvero per ottenere Costo inserzionista, somma le righe in cui questa colonna è uguale a true).</td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell'account dell'annuncio estratto dalla connessione dell'annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell'account dell'annuncio estratto dalla connessione dell'annuncio.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato da Conto. (ovvero per ottenere Costo conto, somma le righe in cui questa colonna è uguale a vero).</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id della campagna estratto dalla connessione dell’annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna estratta dalla connessione dell’annuncio.</p>
      </td>
      <td>
        <p>Retargeting dei partner</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato da Campaign. (ovvero per ottenere il costo della campagna, somma le righe in cui questa colonna è uguale a vero).</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id del gruppo di annunci estratto dalla connessione dell'annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995.21703163075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del gruppo di annunci estratto dalla connessione dell’annuncio.</p>
      </td>
      <td>
        <p>Software di gestione dell'attribuzione | Frase</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato dal gruppo di annunci. (ad esempio, per ottenere Costo gruppo di annunci, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id dell'annuncio estratto dalla connessione dell'annuncio.</p>
      </td>
      <td>
        <p>dc.6114.9131003.24149929.467969200</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell'annuncio estratto dalla connessione dell'annuncio.</p>
      </td>
      <td>
        <p>Nome annuncio: Ad3-320x50.gif; 320 x 50</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato dall’annuncio. (ovvero per ottenere Ad Cost, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id del creativo estratto dalla connessione dell'annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995.51749608028.266050115160</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del creativo estratto dalla connessione dell’annuncio.</p>
      </td>
      <td>
        <p>Gartner Magic Quadrant 2019</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato da Creative. (ovvero per ottenere Costo creativo, somma le righe in cui questa colonna è uguale a vero).</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id della parola chiave estratta dalla connessione dell'annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029.669328935.39419128772.99608705795</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della parola chiave estratta dalla connessione dell’annuncio.</p>
      </td>
      <td>
        <p>Attribuzione marketing sfdc</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato da Parola chiave. (ovvero per ottenere il costo delle parole chiave, somma le righe in cui questa colonna è uguale a vero).</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del posizionamento estratto dalla connessione Ad.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del Posizionamento estratto dalla connessione Annuncio.</p>
      </td>
      <td>
        <p>blocco stradale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato per Posizionamento. (ovvero, per ottenere il costo di posizionamento, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id del sito estratto dalla connessione dell'annuncio.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del sito estratto dalla connessione Annuncio.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato dal sito . (ovvero per ottenere il costo del sito, somma le righe in cui questa colonna è uguale a vero).</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il record viene considerato eliminato o meno nel sistema di origine .</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>ISO_CURRENCY_CODE</td>
      <td>varchar</td>
      <td>Codice ISO per la valuta, importato dal sistema di origine.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>SOURCE_ID</td>
      <td>varchar</td>
      <td>ID per l'origine da cui è stato creato il record.</td>
      <td>aw.3284209</td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>number(38,0)</td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ROW_KEY</p>
      </td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>number(38,0)</td>
      <td>Valore ID della valuta per il record.</td>
      <td>
        <p>-3253183181619994799</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CREATIVES {#biz-creatives}

Creativi importati da qualsiasi account pubblicitario collegato.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per il creativo.</p>
      </td>
      <td>
        <p>ba.3284209.132855866.4556709270.10426699711</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>L'ID creativo dal sistema di origine.</td>
      <td>
        <p>10426699711</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID per l’account dell’annuncio da cui è stata importata la creatività.</p>
      </td>
      <td>fb.106851586409075</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’account dell’annuncio da cui è stato importato il creativo.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id dell’inserzionista per il creativo, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell'inserzionista per il creativo, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del gruppo di annunci per il creativo.</p>
      </td>
      <td>fb.106851586409075.6052044288804.6052044290004</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del gruppo di annunci per il creativo.</p>
      </td>
      <td>Set di annunci per l’annuncio B</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della campagna per il creativo.</p>
      </td>
      <td>
        <p>ba.3284209.132855866</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna per il creativo.</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il Creativo è ancora attivo nel sistema di origine.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il Creativo è stato eliminato o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:25.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui il record è stato importato per la prima volta dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:25.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del creativo dal sistema di origine.</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il Creativo deve essere aggiornato o meno per [!DNL Marketo Measure] assegnazione tag.</p>
        <p>(Campo diagnostico, utilizzato dall'elaborazione interna.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Campo diagnostico per l'elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'oggetto o l'entità principale per questa tabella. In questo caso, "Creativo".</p>
      </td>
      <td>
        <p>Creativo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del provider di annunci per il creativo.</p>
      </td>
      <td>
        <p>BingAds</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La versione corrente dell’URL, compresi tutti i tag.</p>
        <p>(campo diagnostico, per elaborazione interna.)</p>
      </td>
      <td>
        <p>cdn.adobe.com/redir?lp=http%3a%2f%2fwww.pipelinemarketing.com%2f&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}&amp;utm_content={adid}&amp;utm_term={keyword}&amp;utm_campaign=PipelineMarketing.com&amp;utm_source=bing&amp;utm_medium=cpc</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_DISPLAY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L’URL abbreviato e intuitivo che viene visualizzato sul Creativo.</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valore precedente per URL_CURRENT.</p>
        <p>(campo diagnostico, per elaborazione interna.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Di cosa sarà decorato l’URL [!DNL Marketo Measure] Parametri.</p>
        <p>(campo diagnostico, per elaborazione interna.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_SHORTENED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>L’URL abbreviato e intuitivo che viene visualizzato sul Creativo. (Utilizzato solo per LinkedIn Ads.)</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tipo di creativo, che potrebbe essere Testo o Visualizzazione</p>
      </td>
      <td>
        <p>Testo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_UPGRADED_URL</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se il contenuto creativo utilizza o meno gli URL aggiornati.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LINEA GUIDA</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il titolo principale del creativo</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DESCRIPTION_LINE_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La copia dalla prima riga del creativo</p>
      </td>
      <td>
        <p>Connetti E Impara Dagli Addetti Al Marketing B2B Basati Sui Ricavi. Iscriviti alla Community.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DESCRIPTION_LINE_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La copia dalla seconda riga del creativo</p>
      </td>
      <td>
        <p>Lei Ha Usato Analytics? Lascia un commento oggi stesso!</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Campo di diagnostica per elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Campo di diagnostica per elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Campo di diagnostica per elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Campo di diagnostica per elaborazione interna.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SHARE_URN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id condivisione. (Utilizzato solo per LinkedIn Ads.)</p>
      </td>
      <td>
        <p>abbandono:li:azione:6376987561897848832</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CRM_EVENTS {#biz-crm-events}

Eventi importati dal sistema di origine. Questa tabella sarà vuota se la sincronizzazione delle attività è disabilitata.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'ID evento dal sistema di origine.</p>
      </td>
      <td>
        <p>00U3100000VLUnEEAX</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di creazione dell'evento dal sistema di origine.</p>
      </td>
      <td>
        <p>2016-12-12 19:32:53.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica dell'evento, dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-09-03 08:39:51.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del lead associato all’evento.</p>
      </td>
      <td>
        <p>00Q0Z000013eVrxUAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Email per il lead associato all’evento.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del contatto associato all'evento.</p>
      </td>
      <td>
        <p>0030Z00003OyjbOQAR</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Invia un'e-mail al contatto associato all'evento.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La [!DNL Marketo Measure] ID cookie utilizzato per popolare da un partner di integrazione per mappare un evento offline a una sessione web. Requisito: Abilita tracciamento chiamate: True</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACTIVITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome tipo di attività dal sistema di origine.</p>
      </td>
      <td>
        <p>E-mail</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_START_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di inizio dell’evento, una delle opzioni utilizzate per determinare la data del punto di contatto.</p>
      </td>
      <td>
        <p>2016-12-16 19:30:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_END_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di fine dell’evento, una delle opzioni utilizzate per determinare la data del punto di contatto.</p>
      </td>
      <td>
        <p>2016-12-16 21:30:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Se il record viene considerato eliminato o meno nel sistema di origine.</td>
      <td>
        <p>False</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Proprietà personalizzate che [!DNL Marketo Measure] è stato importato dal sistema di origine in formato JSON.</td>
      <td>{"Contact_Type__c":"CMO","Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CRM_TASKS {#biz-crm-tasks}

Attività importate dal sistema di origine. Questa tabella verrà compilata se l’opzione Activity Sync o Call Tracking è abilitata.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID attività dal sistema di origine.</p>
      </td>
      <td>
        <p>00T0Z00004Rf62rUAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di creazione dell'attività dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-27 18:30:25.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica dell'attività, dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-27 18:31:53.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del lead associato all’attività.</p>
      </td>
      <td>
        <p>00Q0Z000013eVrxUAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Email per il lead associato all’attività.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del contatto associato all'attività.</p>
      </td>
      <td>
        <p>00331000038uGfhAAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Invia un'e-mail al contatto associato all'attività.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La [!DNL Marketo Measure] ID cookie utilizzato per popolare da un partner di integrazione per mappare un evento offline a una sessione web. Requisito: Abilita tracciamento chiamate: True</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACTIVITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome tipo di attività dal sistema di origine.</p>
      </td>
      <td>
        <p>Chiamata</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACTIVITY_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui si è verificata l'attività, una delle opzioni utilizzate per determinare la data del punto di contatto.</p>
      </td>
      <td>
        <p>2018-08-27 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Se il record viene considerato eliminato o meno nel sistema di origine.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Proprietà personalizzate che [!DNL Marketo Measure] è stato importato dal sistema di origine in formato JSON.</td>
      <td>{"Contact_Type__c":"CMO", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CURRENCIES {#biz-currencies}

Tabella di tutte le valute ISO.

<table>
  <tbody>
    <tr>
      <th>Colonna</th>
      <th>Tipo di dati</th>
      <th>Descrizione</th>
      <th>Dati di esempio</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>number(38,0)</td>
      <td>Un ID univoco per il record Valuta.</td>
      <td>139474809945095870</td>
    </tr>
    <tr>
      <td>ISO_CODE</td>
      <td>varchar</td>
      <td>Codice ISO per la valuta.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>IS_CORPORATE</td>
      <td>booleano</td>
      <td>Indica se la valuta è la valuta aziendale.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>IS_ENABLED</td>
      <td>booleano</td>
      <td>Indica se la divisa è abilitata nel sistema di origine.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record in [!DNL Marketo Measure].</td>
      <td>2018-08-27 18:30:25.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE_CRM</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel sistema di origine.</td>
      <td>2018-08-27 18:30:25.000</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record in [!DNL Marketo Measure]</td>
      <td>2018-08-27 18:30:25.000</td>
    </tr>
    <tr>
      <td>CREATED_DATE_CRM</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel sistema di origine.</td>
      <td>2018-08-27 18:30:25.000</td>
    </tr>
    <tr>
      <td>ISO_NUMERIC</td>
      <td>number(38,0)</td>
      <td>Codice numerico standard ISO.</td>
      <td>048</td>
    </tr>
    <tr>
      <td>ESPONENTE</td>
      <td>number(38,0)</td>
      <td>Numero di posizioni decimali tra l'unità di valuta definita più piccola e un'unità di valuta intera.</td>
      <td>2</td>
    </tr>
    <tr>
      <td>NOME</td>
      <td>varchar</td>
      <td>Nome della valuta.</td>
      <td>Peso argentino</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CUSTOMER_AB_TESTS {#biz-customer-ab-tests}

Test AB registrati. Questa tabella sarà vuota se i test AB non sono abilitati.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>Dati di esempio</th>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il primo ID cookie dell’ID visitatore correlato.</p>
      </td>
      <td>v_36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID cookie registrato al momento della registrazione dell’evento.</p>
      </td>
      <td>36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui la chat è stata registrata.</p>
      </td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>IP_ADDRESS</td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'indirizzo IP registrato al momento del log dell'esperimento.</p>
      </td>
      <td>192.0.2.1</td>
    </tr>
    <tr>
      <td>
        <p>EXPERIMENT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell'esperimento estratto dalla piattaforma di prova AB.</p>
      </td>
      <td>123</td>
    </tr>
    <tr>
      <td>
        <p>EXPERIMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell'esperimento estratto dalla piattaforma di prova AB.</p>
      </td>
      <td>Esperimento A</td>
    </tr>
    <tr>
      <td>
        <p>VARIATION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID variante dell'esperimento estratto dalla piattaforma di prova AB.</p>
      </td>
      <td>456</td>
    </tr>
    <tr>
      <td>
        <p>VARIATION_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della variante dell'esperimento prelevato dalla piattaforma di prova AB.</p>
      </td>
      <td>Test blu</td>
    </tr>
    <tr>
      <td>
        <p>ABTEST_USER_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'id dell'utente a cui è stato servito l'esperimento è stato estratto dalla piattaforma di test AB.</p>
      </td>
      <td>584d64et</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il record è stato eliminato o meno, utilizzato per la diagnostica e il controllo.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CUSTOMER_EVENTS {#biz-customer-events}

Eventi Web registrati utilizzando eventi personalizzati in JavaScript. Questa tabella sarà vuota se [!DNL Marketo Measure] Gli eventi non sono abilitati.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>Dati di esempio</th>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il primo ID cookie dell’ID visitatore correlato.</p>
      </td>
      <td>v_36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'ID cookie registrato al momento in cui l'evento è stato attivato dal javascript personalizzato.</p>
      </td>
      <td>36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui l’evento è stato attivato dal javascript personalizzato.</p>
      </td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>L'ultima data in cui il record è stato modificato.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'indirizzo IP registrato al momento in cui l'evento è stato attivato dal javascript personalizzato.</p>
      </td>
      <td>192.0.2.1</td>
    </tr>
    <tr>
      <td>
        <p>CHIAVE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome assegnato all'evento attivato dal javascript personalizzato.</p>
      </td>
      <td>Vista video</td>
    </tr>
    <tr>
      <td>
        <p>VALORE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore dato all'evento attivato dal javascript personalizzato.</p>
      </td>
      <td>75% visualizzato</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il record è stato eliminato o meno, utilizzato per la diagnostica e il controllo.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CUSTOM_LANDING_PAGES {#biz-custom-landing-pages}

Pagine di destinazione scaricate da qualsiasi account annuncio connesso.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>Dati di esempio</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per il record.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>ID dell’account annuncio da cui è stata importata la pagina di destinazione.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nome dell’account annuncio da cui è stata importata la pagina di destinazione</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’inserzionista per la pagina di destinazione, in particolare per Doubleclick.</p>
      </td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’inserzionista per la pagina di destinazione, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>ID del gruppo di annunci per la pagina di destinazione.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del gruppo di annunci per la pagina di destinazione.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della campagna per la pagina di destinazione.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna per la pagina di destinazione.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell’ultima modifica della riga</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_EMAIL_TO_VISITOR_IDS {#biz-email-to-visitor-ids}

Tabella di mappatura per gli indirizzi e-mail e gli ID visitatore.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>Un ID univoco per il record.</td>
      <td>
        <p>0013800001MMPPiAAP_person@adobe.com|2022-01-05 17:22:13,000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-MAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un indirizzo e-mail noto associato a un determinato ID visitatore da una sessione</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il primo cookie dell’ID visitatore correlato</p>
      </td>
      <td>
        <p>v_36ec805b4db344d6e92c972c86aee34a</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell’ultima modifica della riga</p>
      </td>
      <td>
        <p>2018-08-14 23:55:03.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di creazione della riga</p>
      </td>
      <td>
        <p>2018-08-14 23:55:03.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il record viene considerato eliminato o meno, utilizzato per la diagnostica e il controllo.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>IS_IGNORE</td>
      <td>booleano</td>
      <td>Indica se l’ID e-mail o visitatore è considerato rumore o spam, utilizzato per l’elaborazione interna.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_FACTS {#biz-facts}

Unisce insieme Impression, Visualizzazioni pagina, Visite, Invii modulo, Punti di contatto utente, Punto di contatto (BT), Punti di contatto di attribuzione (BAT) e Dati di costo. Utilizzato internamente per supportare [!DNL Marketo Measure] rapporti.

<table>
  <tbody>
    <tr>
      <th>Colonna</th>
      <th>Tipo di dati</th>
      <th>Descrizione</th>
      <th>Dati di esempio</th>
    </tr>
    <tr>
      <td>COST_KEY</td>
      <td>number(38,0)</td>
      <td>Utilizzato per unire alla tabella Costi.</td>
      <td>2672629811884560039</td>
    </tr>
    <tr>
      <td>ATP_KEY</td>
      <td>number(38,0)</td>
      <td>Utilizzato per aggiungere alla tabella dei punti di contatto di attribuzione.</td>
      <td>2672629811884560039</td>
    </tr>
    <tr>
      <td>TP_KEY</td>
      <td>number(38,0)</td>
      <td>Utilizzato per unire le tabelle Punti di contatto o Punti di contatto utente.</td>
      <td>5028390208679093800</td>
    </tr>
    <tr>
      <td>PAGE_VIEW_KEY</td>
      <td>number(38,0)</td>
      <td>Utilizzato per unire alla tabella Visualizzazioni di pagina.</td>
      <td>-8044063242541720607</td>
    </tr>
    <tr>
      <td>SESSION_KEY</td>
      <td>number(38,0)</td>
      <td>Utilizzato per partecipare alla tabella Sessions.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>Il primo ID cookie dell’ID visitatore correlato.</td>
      <td>v_530d8334c455460df0d48f48270a4b23</td>
    </tr>
    <tr>
      <td>COOKIE_ID</td>
      <td>varchar</td>
      <td>ID cookie registrato al momento della registrazione dell’evento.</td>
      <td>530d8334c455460df0d48f48270a4b23</td>
    </tr>
    <tr>
      <td>FORM_SUBMIT_KEY</td>
      <td>number(38,0)</td>
      <td>Utilizzato per unire alla tabella Invio modulo.</td>
      <td>-8659572802702769670</td>
    </tr>
    <tr>
      <td>IMPRESSION_KEY</td>
      <td>number(38,0)</td>
      <td>Utilizzato per unire alla tabella Impression.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Utilizzato per unire alla tabella Url.</td>
      <td>4079876040770132443</td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Utilizzato per unire alla tabella Url.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Utilizzato per unire alla tabella Url.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>AD_PROVIDER_KEY</td>
      <td>number(38,0)</td>
      <td>Utilizzato per partecipare alla tabella Fornitori di annunci.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>
        <p>CHANNEL_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per unire alla tabella Canali.</p>
      </td>
      <td>
        <p>-1921844114032355934</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per partecipare alla tabella Campagne pubblicitarie .</p>
      </td>
      <td>
        <p>252687814634577606</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per unire alla tabella Parole chiave.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per partecipare alla tabella Ads.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per partecipare alla tabella Gruppi di annunci.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Faceva parte del tavolo dei Creativi.</p>
      </td>
      <td>
        <p>-2333871387956621113</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per unire alla tabella Sites.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per partecipare alla tabella Inserzionisti.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per partecipare alla tabella Account annuncio.</p>
      </td>
      <td>
        <p>1825012532740770032</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per unire alla tabella Posizionamenti.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>CATEGORY_01_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_02_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_03_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Segmenti.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_04_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_05_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_06_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Segmenti.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_07_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_08_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_09_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Segmenti.</td>
      <td>2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_10_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_11_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_12_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Segmenti.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_13_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_14_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_15_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>TIPO</td>
      <td>number(38,0)</td>
      <td>Indica il tipo di fatto della riga. 1 = punto di contatto dell’attribuzione dell’acquirente 2 = costo 3 = punto di contatto dell’acquirente 4 = punto di contatto dell’utente 5 = punto di contatto dell’utente 6 = sessione 7 = invio del modulo 8 = impression</td>
      <td>3</td>
    </tr>
    <tr>
      <td>DATA</td>
      <td>date</td>
      <td>Data in cui si è verificato l’evento.</td>
      <td>2018-08-28</td>
    </tr>
    <tr>
      <td>TIMESTAMP</td>
      <td>timestamp_ntz</td>
      <td>Data e ora in cui si è verificato l’evento.</td>
      <td>2018-08-28 19:39:15.000</td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell’ultima modifica apportata alla riga.</p>
      </td>
      <td>
        <p>2018-08-29 00:46:47.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COST_IN_MICRO</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Costo in milioni. L’utente dovrà dividere il valore per 1000000.</p>
      </td>
      <td>
        <p>27370000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IMPRESSIONI</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Numero di impression riportate per il gruppo del giorno.</p>
      </td>
      <td>
        <p>340</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIC</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Numero di clic segnalati per il gruppo del giorno.</p>
      </td>
      <td>4</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>Percentuale calcolata allocata a questo punto di contatto perché si tratta di un primo contatto.</p>
      </td>
      <td>0.0000000000000000000</td>
    </tr>
    <tr>
      <td>
        <p>LAST_ANON_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>Percentuale calcolata allocata a questo punto di contatto perché si tratta di un tocco per la creazione di lead.</p>
      </td>
      <td>100.0000000000000000000</td>
    </tr>
    <tr>
      <td>
        <p>U_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>Percentuale calcolata allocata a questo punto di contatto perché fa parte di un tocco a forma di u.</p>
      </td>
      <td>
        <p>100.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>W_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>Percentuale calcolata allocata a questo punto di contatto perché fa parte di un tocco a forma di w.</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FULL_PATH_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>La percentuale calcolata che viene allocata a questo punto di contatto perché fa parte di un modello di percorso completo.</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CUSTOM_MODEL_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>Percentuale calcolata che viene allocata a questo punto di contatto perché fa parte di un modello personalizzato.</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IMPORTO</p>
      </td>
      <td>
        <p>numero(38,8)</p>
      </td>
      <td>
        <p>Importo dell'opportunità dal sistema di origine.</p>
      </td>
      <td>
        <p>42000.00000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_WON</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se l'opportunità è stata spostata in un passaggio classificato come vinto.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_OPP_CLOSED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se l'opportunità è stata spostata in un'area di visualizzazione classificata come chiusa.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID opportunità dal sistema di origine.</p>
      </td>
      <td>
        <p>0060Z00000nFEfEQAW</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPP_CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di creazione dell'opportunità dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-31 15:45:47.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPP_CLOSE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Chiudi la data dell'opportunità dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-12-31 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di creazione del record Contatto dal sistema di origine.</p>
      </td>
      <td>2017-04-28 00:21:52.000</td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID contatto dal sistema di origine.</p>
      </td>
      <td>
        <p>0030Z00003ORVJmQAP</p>
      </td>
    </tr>
    <tr>
      <td>E-MAIL</td>
      <td>varchar</td>
      <td>Indirizzo e-mail del record.</td>
      <td>personb@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>LEAD_CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di creazione del record Lead dal sistema di origine.</p>
      </td>
      <td>
        <p>2017-04-28 00:21:52.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID lead dal sistema di origine.</p>
      </td>
      <td>
        <p>00Q3100001GMPIsEAP</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_AD</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato dall’annuncio. (ovvero per ottenere Ad Cost, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_ADVERTISER</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato da Advertiser (Inserzionista). (ovvero per ottenere Costo inserzionista, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_AD_ACCOUNT</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato da Conto. (ovvero per ottenere Costo conto, somma le righe in cui questa colonna è uguale a vero).</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_AD_GROUP</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato dal gruppo di annunci. (ad esempio, per ottenere Costo gruppo di annunci, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CAMPAIGN</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato da Campaign. (ovvero per ottenere il costo della campagna, somma le righe in cui questa colonna è uguale a vero).</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CHANNEL</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato dal canale. (ad esempio, per ottenere Costo canale, somma le righe in cui questa colonna è uguale a vero).</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CREATIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato da Creative. (ovvero per ottenere Costo creativo, somma le righe in cui questa colonna è uguale a vero).</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_KEYWORD</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato da Parola chiave. (ovvero per ottenere il costo delle parole chiave, somma le righe in cui questa colonna è uguale a vero).</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_PLACEMENT</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato per Posizionamento. (ovvero, per ottenere il costo di posizionamento, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_SITE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene il costo che può essere sommato dal sito . (ovvero per ottenere il costo del sito, somma le righe in cui questa colonna è uguale a vero).</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il record è stato eliminato o meno, utilizzato come traccia di audit.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>number(38,0)</td>
      <td>Valore ID della valuta per il record.</td>
      <td>-3253183181619994799</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_FORM_SUBMITS {#biz-forms-submits}

Invio Di Moduli Acquisiti.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per l’invio del modulo.</p>
      </td>
      <td>
        <p>2018-08-06:01-35-21-927280.9bc63c34482f4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID cookie registrato al momento della registrazione del modulo di invio.</p>
      </td>
      <td>
        <p>9bc63c34482f4de8c2e3b9d8d9f0df56</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il primo ID cookie dell’ID visitatore correlato. Se il record è contrassegnato come is_duplicate = true, questo campo sarà null.</p>
      </td>
      <td>
        <p>v_9bc63c34482f4de8c2e3b9d8d9f0df56</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID sessione registrata al momento della registrazione dell’invio del modulo. Se il record è contrassegnato come is_duplicate = true, questo campo sarà null.</p>
      </td>
      <td>
        <p>2018-08-06:01-35-24-1231230.9bc63c34482f</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di invio del modulo.</p>
      </td>
      <td>
        <p>2018-08-06 01:35:21.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-07 23:09:52.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL in cui è stato inviato il modulo, senza parametri di query.</p>
      </td>
      <td>
        <p>https://info.adobe.com/webinar-marketo-measure-impact</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL in cui è stato inviato il modulo, inclusi eventuali parametri di query.</p>
      </td>
      <td>
        <p>https://info.adobe.com/webinar-marketo-measure-impact?utm_source=partner&amp;mkt_tok=eyJpIjoiTnpBeE1EVml PV0UyWlRObSIsInQiOiI3MEFIek04ZVJiWm9renc1Z29RXC9kXC92YkxycFRYclE0MVhOaH Nwdml3YTZBZDd PdXh4Q0RmcnBJWXhwZTF1Z0RrbXlDVmxJNzIwNkhW</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Indirizzo IP registrato al momento dell’invio del modulo.</p>
      </td>
      <td>
        <p>174.127.184.158</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TIPO</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indica il tipo di evento.</td>
      <td>
        <p>FormSubmit</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_AGENT_STRING</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dispositivo e browser registrati al momento dell’invio del modulo.</p>
      </td>
      <td>
        <p>Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/605.1.15 (KHTML, come Gecko) versione/11.1.2 Safari/605.1.15</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_SEQUENCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indica l’ordine in cui si è verificata la visualizzazione della pagina nella sessione.</td>
      <td>
        <p>4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_RANDOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per il controllo e l'elaborazione interni.</td>
      <td>
        <p>20042b6b7af44512b43f6244d86faf4c</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATO</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Indica se il record è considerato un duplicato.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Utilizzato per elaborazione interna.</td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-MAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Indirizzo e-mail fornito nel modulo, come acquisito dal javascript.</p>
      </td>
      <td>
        <p>personc@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indica il tipo di modulo inviato.</td>
      <td>
        <p>Chat</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Indica il metodo di riconoscimento del modulo, ad esempio onSubmit o AjaxIntercept</p>
      </td>
      <td>
        <p>onSubmit</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_IDENTIFIER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Valore ID del modulo.</td>
      <td>
        <p>-956012665</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>-6255315750913680000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Chiave esterna per la tabella URL.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_IMPRESSIONS {#biz-impressions}

Impression attivate e registrate. Questa tabella richiede una connessione DoubleClick e Enable View Through è impostato su True.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per l'impression.</p>
      </td>
      <td>
        <p>6acd7b43290490fe5c53eed31281d09a|2020-05-18:22:20:59|000|0|2869369052</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID cookie registrato al momento dell'impression.</p>
      </td>
      <td>08c1063cb0a64349ad0d2d862f5cc700</td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il primo ID cookie dell’ID visitatore correlato.</p>
      </td>
      <td>v_08c1063cb0a64349ad0d2d862f5cc700</td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'ID della sessione registrata al momento della registrazione dell'impression.</p>
      </td>
      <td>2018-08-06:01-35-24-1231230.9bc63c34482f</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui è stata distribuita l’impression.</p>
      </td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL in cui è stata distribuita l’impression, senza parametri di query.</p>
      </td>
      <td>https://info.adobe.com/webinar-marketo-measure-impact</td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL in cui è stata trasmessa l’impression, inclusi eventuali parametri di query.</p>
      </td>
      <td>https://info.adobe.com/webinar-marketo-measure-impact?utm_source=partner&amp;mkt_tok=eyJpIjoiTnpBeE1EVml PV0UyWlRObSIsInQiOiI3MEFIek04ZVJiWm9renc1Z29RXC9kXC92YkxycFRYclE0MVhOaH Nwdml3YTZBZDd PdXh4Q0RmcnBJWXhwZTF1Z0RrbXlDVmxJNzIwNkhW</td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'indirizzo IP registrato al momento dell'impression.</p>
      </td>
      <td>174.127.184.158</td>
    </tr>
    <tr>
      <td>
        <p>TIPO</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indica il tipo di evento.</td>
      <td>Impression</td>
    </tr>
    <tr>
      <td>
        <p>USER_AGENT_STRING</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dispositivo e browser registrati al momento dell’invio del modulo.</p>
      </td>
      <td>
        <p>Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/605.1.15 (KHTML, come Gecko) versione/11.1.2 Safari/605.1.15</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_SEQUENCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indica l’ordine in cui si è verificata la visualizzazione della pagina nella sessione.</td>
      <td>
        <p>4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_RANDOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per il controllo e l'elaborazione interni.</td>
      <td>
        <p>20042b6b7af44512b43f6244d86faf4c</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATO</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Indica se il record è considerato un duplicato.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Utilizzato per elaborazione interna.</td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>In genere la pagina di destinazione esterna immediatamente prima che l’utente acceda al sito web. In CRM è indicato come "Pagina referente".</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE-RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>In genere la pagina di destinazione esterna immediatamente prima che l’utente acceda al sito web. Una pagina referente non elaborata può contenere parametri di query nell’URL. In CRM è indicato come "Pagina referente - Raw".</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>CITTÀ</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La città risolta dall'indirizzo IP.</p>
      </td>
      <td>
        <p>Seattle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGIONE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Area risolta dall'indirizzo IP.</p>
      </td>
      <td>
        <p>Washington</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAESE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il paese risolto dall'indirizzo IP.</p>
      </td>
      <td>
        <p>Stati Uniti</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ISP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del provider di servizi Internet utilizzato dai clienti con monitoraggio Geo IP avanzato.</p>
      </td>
      <td>
        <p>AT&amp;T verso U</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Piattaforma di annunci [!DNL Marketo Measure] è stato in grado di risolvere da, tipicamente uno dei nostri partner di integrazione.</p>
      </td>
      <td>Google</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’account dell’annuncio da cui è stata risolta l’inserzione.</p>
      </td>
      <td>aw.6601259029</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’account dell’annuncio da cui è stata risolta l’inserzione.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’inserzionista dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’inserzionista dall’account dell’annuncio dal quale l’annuncio è stato risolto. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Analisi di marketing delle misure di mercato</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del sito dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del sito dall’account dell’annuncio dal quale è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>blocco stradale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della campagna dall’account dell’annuncio da cui è stato risolto l’annuncio.</p>
      </td>
      <td>aw.6601259029.317738075</td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna dall’account dell’annuncio dal quale è stato risolto l’annuncio.</p>
      </td>
      <td>Attribuzione di marketing</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché nella gerarchia di Doubleclick non è presente alcun gruppo di annunci per le impression</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché nella gerarchia di Doubleclick non è presente alcun gruppo di annunci per le impression</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’annuncio dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>
        <p>68035923</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’annuncio dall’account dell’annuncio dal quale l’annuncio è stato risolto. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>
        <p>centurylink_banner_98121</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un creativo nella gerarchia di Doubleclick per le impressioni.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un creativo nella gerarchia di Doubleclick per le impressioni.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un creativo nella gerarchia di Doubleclick per le impressioni.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un creativo nella gerarchia di Doubleclick per le impressioni.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un creativo nella gerarchia di Doubleclick per le impressioni.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un creativo nella gerarchia di Doubleclick per le impressioni.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto valore nullo perché nella gerarchia di Doubleclick per le impressioni non è presente alcuna parola chiave.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>KYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto valore nullo perché nella gerarchia di Doubleclick per le impressioni non è presente alcuna parola chiave.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto valore nullo perché nella gerarchia di Doubleclick per le impressioni non è presente alcuna parola chiave.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>NOME_BROWSER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall'indirizzo javascript e IP, il browser rilevato che l'utente era attivo durante la sessione.</p>
      </td>
      <td>
        <p>Chrome</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall'indirizzo javascript e IP, la versione rilevata del browser su cui l'utente si trovava durante la sessione.</p>
      </td>
      <td>
        <p>58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, la piattaforma rilevata dall’utente durante la sessione.</p>
      </td>
      <td>
        <p>Mac</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, la versione rilevata della piattaforma su cui l’utente si trovava durante la sessione.</p>
      </td>
      <td>
        <p>10_12</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista BIZ_FACTS.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_KEY</p>
      </td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_KEYWORDS {#biz-keywords}

Parole chiave importate da qualsiasi account annuncio connesso.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per la parola chiave.</p>
      </td>
      <td>
        <p>ba.3284209.132630532.364689365.39464932147</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>ID parola chiave dal sistema di origine.</td>
      <td>
        <p>39464932147</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’account dell’annuncio da cui è stata importata la parola chiave.</p>
      </td>
      <td>fb.106851586409075</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’account dell’annuncio da cui è stata importata la parola chiave.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto valore nullo perché nella gerarchia di Doubleclick per le impressioni non è presente alcuna parola chiave.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto valore nullo perché nella gerarchia di Doubleclick per le impressioni non è presente alcuna parola chiave.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id del gruppo di annunci per la parola chiave.</p>
      </td>
      <td>
        <p>ba.3284209.132630532.3646889365</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del gruppo di annunci per la parola chiave.</p>
      </td>
      <td>
        <p>Attribuzione ricavi - B2B</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della campagna per la parola chiave.</p>
      </td>
      <td>
        <p>ba.3284209.132630532</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna per la parola chiave.</p>
      </td>
      <td>
        <p>Attribuzione ricavi</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la parola chiave è ancora attiva nel sistema di origine.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la parola chiave è stata eliminata o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>2018-08-02 06:37:29.000</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui il record è stato importato per la prima volta dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-02 06:37:29.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della parola chiave dal sistema di origine.</p>
      </td>
      <td>
        <p>[attribuzione ricavi b2b]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la parola chiave deve essere aggiornata o meno per [!DNL Marketo Measure] assegnazione tag.</p>
        <p>(Campo diagnostico, utilizzato per l’elaborazione interna.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Campo diagnostico, utilizzato per l’elaborazione interna.</td>
      <td>
        <p>ba.3284209.132630532.3646889365</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'oggetto o l'entità principale per questa tabella. In questo caso, "Parola chiave".</p>
      </td>
      <td>
        <p>Parola chiave</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del provider di annunci per la parola chiave.</p>
      </td>
      <td>
        <p>BingAds</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L’URL della pagina di destinazione.</p>
        <p>(campo diagnostico, per elaborazione interna.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valore precedente per URL_CURRENT.</p>
        <p>(campo diagnostico, per elaborazione interna.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>URL_REQUESTED</td>
      <td>varchar</td>
      <td>
        <p>L’URL della pagina di destinazione con [!DNL Marketo Measure] Parametri.</p>
        <p>(campo diagnostico, per elaborazione interna.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_UPGRADED_URL</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Campo diagnostico per l'elaborazione interna.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAROLA</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La fase di ricerca immessa dall'utente.</td>
      <td>
        <p>attribuzione ricavi b2b</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tipo di corrispondenza trovato tra la frase di ricerca e la parola chiave.</p>
      </td>
      <td>
        <p>Esatto</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Modello di tracciamento URL [!DNL Marketo Measure] aggiunto alla parola chiave.</td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>-2712935512233520000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_LANDING_PAGES {#biz-landing-pages}

Pagine di destinazione importate da qualsiasi account annuncio connesso.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>Dati di esempio</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per la pagina di destinazione.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>ID dell’account annuncio da cui è stata importata la pagina di destinazione.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nome dell’account annuncio da cui è stata importata la pagina di destinazione.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’inserzionista per la pagina di destinazione, in particolare per Doubleclick.</p>
      </td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’inserzionista per la pagina di destinazione, in particolare per Doubleclick.</p>
      </td>
      <td>Marketing analytics</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>ID del gruppo di annunci per la pagina di destinazione.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nome del gruppo di annunci per la pagina di destinazione.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>ID della campagna per la pagina di destinazione.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nome della campagna per la pagina di destinazione.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell’ultima modifica della riga.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_LEADS {#biz-leads}

Lead importati dal sistema di origine.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID lead dal sistema di origine.</p>
      </td>
      <td>
        <p>00Q0Z00001MZcj8UAD</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record Lead dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-27 21:52:10.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di creazione del record Lead dal sistema di origine.</p>
      </td>
      <td>2018-08-27 21:52:10.000</td>
    </tr>
    <tr>
      <td>
        <p>E-MAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Indirizzo e-mail del lead dal sistema di origine.</p>
      </td>
      <td>persona@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>WEB_SITE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Sito Web immesso per il lead, dal sistema di origine, utilizzato per la mappatura Lead2Account.</p>
      </td>
      <td>
        <p>adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AZIENDA</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome società immesso per il lead, dal sistema di origine, utilizzato per la mappatura Lead2Account.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Origine in cui è stato creato il lead.</p>
      </td>
      <td>
        <p>Pubblicità</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CONVERTED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il lead è stato convertito o meno in un contatto.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_OPPORTUNITY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’opportunità correlata dopo la conversione del lead.</p>
      </td>
      <td>
        <p>0013100001b44aGAAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui il lead è stato convertito in un contatto.</p>
      </td>
      <td>
        <p>2018-08-27 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del contatto correlato una volta convertito il lead.</p>
      </td>
      <td>
        <p>0030Z00003Oyp25QAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNTID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell'account mappato. Requisiti: Abilita ABM</p>
      </td>
      <td>
        <p>0010Z0000236F9GQAU</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Fase corrente del lead, riconosciuta come fase personalizzata che può essere creata nel [!DNL Marketo Measure] applicazione.</p>
      </td>
      <td>
        <p>Demo pianificata</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE_PREVIOUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tutti gli stadi precedenti per il lead, riconosciuti come stadi personalizzati che possono essere creati nel [!DNL Marketo Measure] applicazione.</p>
      </td>
      <td>
        <p>MQL</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ODDS_OF_CONVERSION</p>
      </td>
      <td>
        <p>numero(38,19)</p>
      </td>
      <td>
        <p>La [!DNL Marketo Measure] algoritmo di stima se un lead verrà convertito in base all’età e allo stadio.</p>
      </td>
      <td>
        <p>.290034</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SCORE_MODEL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>(obsoleto)</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SCORE_RESULTS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>(obsoleto)</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La [!DNL Marketo Measure] ID cookie utilizzato per popolare da un partner di integrazione per mappare un evento offline a una sessione web. Requisito: Abilita tracciamento chiamate: True</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il record viene eliminato o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>3263982503087870000</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Proprietà personalizzate che [!DNL Marketo Measure] è stato importato dal sistema di origine in formato JSON.</td>
      <td>{"Lead_Type__c":"Vendite create", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>IS_DUPLICATE</td>
      <td>booleano</td>
      <td>Utilizzato per deduplicare i record se è configurata sia un’integrazione CRM che Marketo. In presenza di duplicati, il lead Marketo è contrassegnato come true.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Indica se il record proviene da un’integrazione CRM o Marketo.</td>
      <td>Crm</td>
    </tr>
    <tr>
      <td>NEW_SYSTEM_ID</td>
      <td>varchar</td>
      <td>Mappa una persona da un’integrazione Marketo con un lead da un’integrazione CRM. Se esiste sia un’integrazione CRM che Marketo, il valore è l’ID corrispondente.</td>
      <td>1234</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_LEAD_STAGE_TRANSITIONS {#biz-lead-stage-transitions}

Transizioni di stage per lead o contatti.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per la transizione.</p>
      </td>
      <td>
        <p>ST_0030Z0003FhkRXQAZ__FT-1_TP2_Person_0030Z0003FhkRXQAZ_2018-08-27:17-05-45-944 74800.0d5c18c29d7b</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-MAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'indirizzo e-mail fornito per il relativo lead/contatto.</p>
      </td>
      <td>
        <p>persone@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del lead associato alla transizione.</p>
      </td>
      <td>
        <p>00Q3100001Fx6AlEAJ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del contatto associato alla transizione.</p>
      </td>
      <td>
        <p>0033100003Aq9grAAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id per il punto di contatto dell’acquirente associato alla transizione.</p>
      </td>
      <td>
        <p>TP2_Person_00Q3100001Fx6AlEAJ_2018-08-28:14-41-06-1674260.d00ceb09fbd3</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRANSITION_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui il record è passato all’area di visualizzazione.</p>
      </td>
      <td>
        <p>2018-08-27 16:05:34.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valore ID dell’area di visualizzazione per la transizione.</p>
      </td>
      <td>
        <p>_bizible_FT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FASE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’area di visualizzazione per la transizione.</p>
      </td>
      <td>
        <p>FT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLASSIFICA</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>La classificazione numerica dello stadio, come ordinato nella [!DNL Marketo Measure] Impostazioni di Mappatura della fase.</p>
      </td>
      <td>
        <p>5</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>INDICE</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Utilizzato nell'elaborazione interna per l'indicizzazione e l'ordinamento delle fasi boomerang.</p>
      </td>
      <td>
        <p>1</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_INDEX</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>Utilizzato nell'elaborazione interna per l'indicizzazione e l'ordinamento delle fasi boomerang.</td>
      <td>
        <p>1</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PENDING</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se il punto di contatto è considerato in sospeso e non ancora chiuso. Viene visualizzato solo per i clienti con modello di attribuzione percorso completo.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_NON_TRANSITIONAL</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga è associata a una transizione di fase cardine. Ad esempio, se ci sono 3 fasi/ingressi (FT, LC, MQL) e 4 punti di contatto, il 1 punto di contatto senza una fase su di esso è considerato "non transitorio" in modo che il valore sia uguale a vero.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PREVIOUS_STAGE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di transizione per la fase precedente, in base al rango dello stadio.</p>
      </td>
      <td>
        <p>2017-11-28 21:26:44.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEXT_STAGE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di transizione per la fase successiva, in base al rango dello stadio.</p>
      </td>
      <td>
        <p>2017-12-11 22:39:17.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-28 15:31:10.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il record di transizione viene considerato eliminato o meno.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_OPPORTUNITÀ {#biz-opportunities}

Opportunità importate dal sistema di origine.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'ID opportunità dal sistema di origine.</p>
      </td>
      <td>
        <p>0060Z00000o89I4QAI</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data ultima modifica dell'opportunità dal sistema di origine.</p>
      </td>
      <td>2017-11-28 21:26:44.000</td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di creazione dell'opportunità dal sistema di origine.</p>
      </td>
      <td>2017-11-28 21:26:44.000</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell'account correlato.</p>
      </td>
      <td>
        <p>001i000000qbyeoAAA</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome opportunità dal sistema di origine.</p>
      </td>
      <td>
        <p>Rinnovo della misura Mareketo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_WON</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se l'opportunità è stata spostata in uno stadio considerato vinto.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CLOSED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se l'opportunità è stata spostata in uno stadio considerato chiuso.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLOSE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di chiusura prevista o effettiva dell'opportunità dal sistema di origine.</p>
      </td>
      <td>
        <p>2019-08-28 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_CUSTOM_MODEL_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>(obsoleto)</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IMPORTO</p>
      </td>
      <td>
        <p>numero(38,8)</p>
      </td>
      <td>
        <p>Importo dell'offerta previsto o chiuso dall'opportunità dal sistema di origine.</p>
      </td>
      <td>
        <p>8988.00000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_FROM_LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del lead correlato convertito in questa opportunità.</p>
        <p>Tieni presente che questo campo non è impostato e restituisce null in Snowflake per tutti i clienti.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_FROM_LEAD_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L’e-mail del lead correlato che si era convertito in questa opportunità.</p>
        <p>Tieni presente che questo campo non è impostato e restituisce null in Snowflake per tutti i clienti.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMARY_CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Se si utilizza il ruolo di contatto principale, l'ID del contatto correlato viene elencato come ruolo di contatto principale.</p>
      </td>
      <td>
        <p>00331000038uGfhAAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMARY_CONTACT_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Se si utilizza il ruolo di contatto principale, l'e-mail del contatto correlato è elencata come ruolo di contatto principale.</p>
      </td>
      <td>
        <p>personb@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ODDS_OF_CONVERSION</p>
      </td>
      <td>
        <p>numero(38,19)</p>
      </td>
      <td>
        <p>La [!DNL Marketo Measure] algoritmo per stimare se un'opportunità verrà chiusa in base all'età e allo stadio.</p>
      </td>
      <td>
        <p>0.8225108385086060000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Fase corrente dell'opportunità, come definito nel [!DNL Marketo Measure] applicazione.</p>
      </td>
      <td>
        <p>Demo DM</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE_PREVIOUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Una stringa di tutte le fasi che l'opportunità ha attraversato in precedenza, come definito in [!DNL Marketo Measure] applicazione.</p>
      </td>
      <td>
        <p>Individuazione qualificata, demo pianificato</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il record viene eliminato o meno nel sistema di origine.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>4609512587744160000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENCY_ISO_CODE</td>
      <td>varchar</td>
      <td>Codice ISO per la valuta, importato dal sistema di origine.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>number(38,0)</td>
      <td>Valore ID della valuta per il record.</td>
      <td>4609512587744160000</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Proprietà personalizzate che [!DNL Marketo Measure] è stato importato dal sistema di origine in formato JSON.</td>
      <td>{"Opportunity_Location__c":"Seattle", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_OPP_STAGE_TRANSITIONS {#biz-opp-stage-transitions}

Transizioni stage per Opportunità.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per la transizione.</p>
      </td>
      <td>
        <p>ST_0060Z0000nEgjlQAC_0030Z0003IjojKQAR_Demo Pianificato-1_BAT2_0060Z00000nEgjlQAC_0030Z 00003IjojKQAR_2018-06-01:19-51-38-1685390.beec556e7757</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell'account associato all'opportunità.</p>
      </td>
      <td>
        <p>0013100001b44nTAAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID per l'opportunità associata alla transizione.</p>
      </td>
      <td>
        <p>0060Z00000nEgjlQAC</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del contatto associato alla transizione.</p>
      </td>
      <td>
        <p>0030Z00003IjojKQAR</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-MAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'indirizzo e-mail fornito per il contatto correlato.</p>
      </td>
      <td>
        <p>persone@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id per il punto di contatto dell’attribuzione dell’acquirente associato alla transizione.</p>
      </td>
      <td>
        <p>BAT2_0060Z0000nEgjlQAC_0030Z0003IjojKQAR_2018-06-01:19-51-38-1685390.beec 556e7757</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRANSITION_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui il record è passato all’area di visualizzazione.</p>
      </td>
      <td>
        <p>2018-05-26 07:29:43.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FASE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’area di visualizzazione per la transizione.</p>
      </td>
      <td>
        <p>Demo pianificata</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valore ID dell’area di visualizzazione per la transizione.</p>
      </td>
      <td>
        <p>_bizible_FT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLASSIFICA</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>La classificazione numerica dello stadio, come ordinato nella [!DNL Marketo Measure] Impostazioni di Mappatura della fase.</p>
      </td>
      <td>
        <p>4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>INDICE</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Utilizzato nell'elaborazione interna per l'indicizzazione e l'ordinamento delle fasi boomerang.</p>
      </td>
      <td>1</td>
    </tr>
    <tr>
      <td>
        <p>LAST_INDEX</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Utilizzato nell'elaborazione interna per l'indicizzazione e l'ordinamento delle fasi boomerang.</p>
      </td>
      <td>1</td>
    </tr>
    <tr>
      <td>
        <p>IS_PENDING</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se il punto di contatto è considerato in sospeso e non ancora chiuso. Viene visualizzato solo per i clienti con modello di attribuzione percorso completo.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_NON_TRANSITIONAL</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga è associata a una transizione di fase cardine. Ad esempio, se ci sono 3 fasi/ingressi (FT, LC, MQL) e 4 punti di contatto, il 1 punto di contatto senza una fase su di esso è considerato "non transitorio" in modo che il valore sia uguale a vero.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PREVIOUS_STAGE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di transizione per la fase precedente, in base al rango dello stadio.</p>
      </td>
      <td>
        <p>2015-07-16 17:41:49.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEXT_STAGE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data di transizione per la fase successiva, in base al rango dello stadio.</p>
      </td>
      <td>
        <p>2018-08-27 19:40:52.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-28 03:53:33.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il record di transizione viene considerato eliminato o meno.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_PAGE_VIEWS {#biz-page-views}

Visualizzazioni di pagina raccolte dalle visite web. Più visualizzazioni di pagina possono comporre una singola sessione.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per la visualizzazione pagina.</p>
      </td>
      <td>
        <p>2018-08-19:16-49-58-24340.277d79d0167849</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID cookie registrato al momento della registrazione della visualizzazione pagina.</p>
      </td>
      <td>
        <p>277d79d01678498fea067c9b631bf6df</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il primo cookie dell’ID visitatore correlato.</p>
      </td>
      <td>
        <p>v_277d79d01678498fea067c9b631bf6df</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L’ID sessione è correlato alla visualizzazione pagina.</p>
      </td>
      <td>
        <p>2018-08-19:16-49-58-24340.277d79d0167849</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui si è verificata la visualizzazione della pagina.</p>
      </td>
      <td>
        <p>2018-08-19 16:49:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-19 16:55:37.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL della visualizzazione pagina, senza parametri di query.</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL della visualizzazione pagina, inclusi eventuali parametri di query.</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo?hsCtaTracking=207219e9-87b6-4105-8f4b-0a3b62ae1af8%7C48060522-3aeb-4c72-8ce5-fd4b1017f069</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Indirizzo IP registrato al momento dell’invio del modulo.</p>
      </td>
      <td>
        <p>174.127.184.158</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TIPO</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indica il tipo di evento.</td>
      <td>
        <p>PageView</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_AGENT_STRING</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dispositivo e browser registrati al momento dell’invio del modulo.</p>
      </td>
      <td>
        <p>Mozilla/5,0 (X11; Linux x86_64; rv:52.0) Gecko/20100101 Firefox/52.0</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_SEQUENCE</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Indica l’ordine in cui si è verificata la visualizzazione della pagina nella sessione.</p>
      </td>
      <td>
        <p>1</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_RANDOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Utilizzato per il controllo e l'elaborazione interni.</td>
      <td>
        <p>103532</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATO</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Indica se il record è considerato un duplicato.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Utilizzato per elaborazione interna.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL da cui proviene la visualizzazione pagina, senza parametri di query.</p>
      </td>
      <td>
        <p>http://info.adobe.com/cmos-guide-to-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL da cui proviene la visualizzazione pagina, compresi eventuali parametri di query.</p>
      </td>
      <td>
        <p>http://info.adobe.com/cmos-guide-to-b2b-marketing-attribution?utm_source=linkedin&amp;utm_medium=Social&amp;utm_campaign=SU%20-%20CMO%20JT&amp;utm_content=CMOs%20Guide&amp;utm_term=lisu05091601</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAGE_TITLE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Titolo della pagina.</p>
      </td>
      <td>
        <p>Guida CMO al download di B2B Marketing Attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-MAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Indirizzo e-mail fornito in un modulo, come acquisito dal javascript.</p>
      </td>
      <td>personc@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>-6255315750913680000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Chiave esterna per la tabella URL.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Chiave esterna per la tabella URL.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>HAS_USER_CONSENT</td>
      <td>booleano</td>
      <td>Indica se l’utente ha acconsentito al tracciamento. False indica che la visualizzazione pagina è stata raccolta perché non è richiesto il consenso dell’utente. True indica che la visualizzazione pagina è stata raccolta e che l'utente ha dato il consenso per il tracciamento.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_PLACEMENTS {#biz-placements}

Tabella in cui vengono memorizzati tutti i posizionamenti scaricati da qualsiasi account di annunci connessi, un oggetto dell&#39;integrazione di Doubleclick.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>Dati di esempio</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per il posizionamento.</p>
      </td>
      <td>
        <p>ba.3284209.132855866.4556709270.10426699711</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>ID posizionamento dal sistema di origine.</td>
      <td>10426699711</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID per l’account dell’annuncio da cui è stato importato il posizionamento.</p>
      </td>
      <td>f ter. 106851586409075</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’account dell’annuncio da cui è stato importato il posizionamento.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id dell’inserzionista per il posizionamento, in particolare per Doubleclick.</p>
      </td>
      <td>300184624</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’inserzionista per il posizionamento, in particolare per Doubleclick.</p>
      </td>
      <td>[!DNL Marketo Measure] Analytics</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un gruppo di annunci sopra il posizionamento in una gerarchia di annunci.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un gruppo di annunci sopra il posizionamento in una gerarchia di annunci.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della campagna per il posizionamento.</p>
      </td>
      <td>ba.3284209.132855866</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna per il posizionamento.</p>
      </td>
      <td>Marketing sulle pipeline</td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il Posizionamento è ancora attivo nel sistema di origine.</p>
      </td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il Posizionamento è stato eliminato o meno nel sistema di origine.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>2018-08-02 06:36:25.000</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui il record è stato importato per la prima volta dal sistema di origine.</p>
      </td>
      <td>2018-08-02 06:36:25.000</td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del Posizionamento dal sistema di origine.</p>
      </td>
      <td>Mercato</td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se è necessario aggiornare o meno il posizionamento per [!DNL Marketo Measure] assegnazione tag.</p>
        <p>(Campo diagnostico, utilizzato dall'elaborazione interna.)</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Campo diagnostico per l'elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'oggetto o l'entità principale per questa tabella. In questo caso, "Posizionamento".</p>
      </td>
      <td>Posizionamento</td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del provider di annunci per il posizionamento.</p>
      </td>
      <td>BingAds</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del Snowflake del record</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di modifica del Snowflake del record</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di eliminazione del Snowflake del record se è stato eliminato</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SEGMENTS {#biz-segments}

Valori del segmento come definiti nella [!DNL Marketo Measure] applicazione.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per il segmento.</p>
      </td>
      <td>
        <p>Nuove attività</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del segmento.</p>
      </td>
      <td>
        <p>Nuove attività</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>1028715376434030000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SEGMENT_NAMES {#biz-segment-names}

Mappa il nome del segmento personalizzato sul valore della sua categoria. (Questo mappa i nomi delle colonne alle intestazioni di colonna Categoria1 - 15 presenti nelle tabelle dei punti di contatto).

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Indica la categoria a cui è mappato il nome del segmento.</p>
      </td>
      <td>
        <p>CategoriaUno</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2022-02-28 18:12:35.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEGMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del segmento mappato alla categoria.</p>
      </td>
      <td>
        <p>1028715376434030000</p>
      </td>
    </tr>
    <tr>
      <td>IS_ACTIVE</td>
      <td>booleano</td>
      <td>Indica se la categoria è in uso.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>booleano</td>
      <td>Indica se il record viene eliminato.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SESSIONS {#biz-sessions}

Sessioni elaborate dalle visualizzazioni di pagina. Più visualizzazioni di pagina possono costituire una sessione e un singolo ID visitatore può essere associato a più sessioni.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per la sessione.</p>
      </td>
      <td>
        <p>2016-08-01:14-24-21-9079480.33163948f0a3</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il primo cookie dell’ID visitatore correlato.</p>
      </td>
      <td>v_277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID cookie registrato della sessione.</p>
      </td>
      <td>277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data della sessione.</p>
      </td>
      <td>
        <p>2016-08-01 14:24:21.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DATA DI MODIFICA</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-09-01 03:49:10.000</p>
      </td>
    </tr>
    <tr>
      <td>IS_FIRST_SESSION</td>
      <td>booleano</td>
      <td>Indica se si tratta della prima sessione per l’ID visitatore.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>CANALE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Canale assegnato alla sessione, come definito dalle definizioni dei canali impostate nella [!DNL Marketo Measure] applicazione.</p>
      </td>
      <td>
        <p>Ricerca.AdWords a pagamento</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAGE_TITLE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della pagina web.</p>
      </td>
      <td>
        <p>Google Analytics Salesforce | [!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL della prima visualizzazione di pagina della sessione, senza parametri di query.</p>
      </td>
      <td>
        <p>http://www.adobe.com/salesforce-google-analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL della prima visualizzazione di pagina della sessione, inclusi eventuali parametri di query.</p>
      </td>
      <td>
        <p>http://www.adobe.com/salesforce-google-analytics?_bt=83558988035&amp;_bk=google%20analytics%20salesforce&amp;_bm= p&amp;gclid=CMvd5YTLo84CFUI9gQodd-kLEQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL da cui è nata la sessione, senza parametri di query.</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL da cui è nata la sessione, inclusi eventuali parametri di query.</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della pagina di riferimento.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore immesso dall’utente nel browser per la ricerca e finito sul sito web.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] google salesforce</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Utilizzato per definire l'origine risultante nella sessione. Questo può essere analizzato dall'URL da utm_source o impostato su un Ad Provider se [!DNL Marketo Measure] è in grado di risolvere un annuncio.</p>
      </td>
      <td>
        <p>Google AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_FORM</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se la sessione conteneva o meno una compilazione del modulo,</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_CHAT</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se la sessione conteneva o meno una chat web.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_EMAIL</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se la sessione aveva o meno un indirizzo e-mail.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_CRM_ACTIVITY</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la sessione proviene o meno da un record di attività CRM.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPOSITIVO</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il browser e il sistema operativo dell'utente durante la sessione.</p>
      </td>
      <td>
        <p>Chrome (65.0), Windows (6.1)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Piattaforma Ad [!DNL Marketo Measure] Risolto da, tipicamente uno dei nostri partner di integrazione.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’account dell’annuncio da cui è stata risolta l’inserzione.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’account dell’annuncio dal quale l’annuncio è stato risolto.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id dell’inserzionista da cui è stato risolto l’annuncio, in particolare dalla connessione Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’inserzionista da cui è stato risolto l’annuncio, in particolare dalla connessione Doubleclick.</p>
      </td>
      <td>
        <p>Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del sito da cui è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del sito da cui è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del pacchetto da cui è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del posizionamento da cui è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>blocco stradale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della campagna da cui è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029.321586235</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna da cui è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>Pianificazione del webinar sul budget</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del gruppo di annunci da cui è stato risolto l’annuncio. Questo vale solo per Google Adwords.</p>
      </td>
      <td>
        <p>aw.6601259029.321586235.23182235435</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del gruppo di annunci da cui è stato risolto l’annuncio. Questo vale solo per Google Adwords.</p>
      </td>
      <td>
        <p>Salesforce - Google Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’annuncio risolto da. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>aw.6601259029.321586235.23182235435</td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’annuncio risolto da. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>Promo invernale - Verde</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id del creativo da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>aw.6601259029.321586235.23182235435.83558988035</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del creativo da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Integrare GA e Salesforce</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La prima riga del Creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Integrare Salesforce &amp; Analytics In</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La seconda riga del creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Ottimizza i ricavi. Impara Come.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La pagina di destinazione che fa clic dall’annuncio di ricerca, estratta dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>http://www.adobe.com/salesforce-google-analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il nome dell’URL descrittivo mostrato nell’annuncio di ricerca, estratto dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>adobe.com/Salesforce-for-GA</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della parola chiave da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>aw.6601259029.321586235.23182235435.35934468937</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della parola chiave da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>salesforce di google analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il tipo di corrispondenza trovato tra la frase di ricerca e la parola chiave acquistata.</p>
      </td>
      <td>
        <p>Frase</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAGNA</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Viene analizzato dall’URL da utm_campaign.</p>
      </td>
      <td>
        <p>SU - Account ABC - Abilità media a pagamento</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SORGENTE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Viene analizzato dall’URL da utm_source.</p>
      </td>
      <td>
        <p>linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIO</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Viene analizzato dall’URL da utm_medium.</p>
      </td>
      <td>
        <p>Social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TERMINE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Viene analizzato dall’URL da utm_term.</p>
      </td>
      <td>
        <p>lisu07261601</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTENUTO</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Viene analizzato dall’URL da utm_content.</p>
      </td>
      <td>
        <p>Rapporto Benchmark AdWords 2016</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITTÀ</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La città risolta dall'indirizzo IP.</p>
      </td>
      <td>Vancouver</td>
    </tr>
    <tr>
      <td>
        <p>REGIONE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Area risolta dall'indirizzo IP.</p>
      </td>
      <td>Columbia Britannica</td>
    </tr>
    <tr>
      <td>
        <p>PAESE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il paese risolto dall'indirizzo IP.</p>
      </td>
      <td>Canada</td>
    </tr>
    <tr>
      <td>
        <p>ISP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Provider di servizi Internet dell'utente</p>
      </td>
      <td>
        <p>AT&amp;T verso U</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'indirizzo IP registrato al momento della sessione.</p>
      </td>
      <td>
        <p>174.127.184.158</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Determina se questa sessione è stata unita a un'altra e deve essere eliminata.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SITES {#biz-sites}

Siti importati da qualsiasi account annuncio connesso.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per il sito.</p>
      </td>
      <td>aw.3284209</td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>L'ID del sito dal sistema di origine.</td>
      <td>39464932147</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell'account dell'annuncio da cui è stato importato il sito.</p>
      </td>
      <td>aw.3284209</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell'account dell'annuncio da cui è stato importato il sito.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell'inserzionista per il sito, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell'inserzionista del sito, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un gruppo di annunci sopra Site in alcuna gerarchia di annunci.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Previsto null perché non esiste un gruppo di annunci sopra Site in alcuna gerarchia di annunci.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della campagna per il sito.</p>
      </td>
      <td>
        <p>ba.3284209.132630532</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna per il sito.</p>
      </td>
      <td>Attribuzione ricavi</td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se il sito è ancora attivo nel sistema di origine.</p>
      </td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il Sito è stato eliminato o meno nel sistema di origine.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>2018-08-02 06:37:29.000</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui il record è stato importato per la prima volta dal sistema di origine.</p>
      </td>
      <td>2018-08-02 06:37:29.000</td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del sito dal sistema di origine.</p>
      </td>
      <td>Entrate</td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il sito deve essere aggiornato o meno per [!DNL Marketo Measure] assegnazione tag.</p>
        <p>(Campo diagnostico, utilizzato per l’elaborazione interna.)</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Campo diagnostico, utilizzato per l’elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'oggetto o l'entità principale per questa tabella. In questo caso, "Sito".</p>
      </td>
      <td>Sito</td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del provider di annunci per il sito.</p>
      </td>
      <td>AdWords</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SITE_LINKS {#biz-site-links}

Collegamenti a siti da qualsiasi account Ads connesso.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per il collegamento al sito</p>
      </td>
      <td>
        <p>aw.6601259029.285077795.1654234342</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td>
        <p>1654234342</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell'account degli annunci connessi per il collegamento al sito</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell'account degli annunci connessi per il collegamento al sito</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’inserzionista per il collegamento al sito, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il nome dell'inserzionista per il link del sito, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del gruppo di annunci per il collegamento al sito</p>
      </td>
      <td>aw.6601259029.208548635.1675016675</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del gruppo di annunci per il collegamento al sito</p>
      </td>
      <td>Brand - Core</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della campagna per il collegamento al sito</p>
      </td>
      <td>
        <p>aw.6601259029.285077795</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna per il collegamento al sito</p>
      </td>
      <td>
        <p>Brand</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il collegamento al sito è ancora attivo o meno nell'account degli annunci</p>
      </td>
      <td>
        <p>TRUE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il collegamento al sito è stato eliminato o meno nell’account degli annunci</p>
      </td>
      <td>
        <p>FALSE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell’ultima modifica della riga</p>
      </td>
      <td>
        <p>2018-08-02 06:36:50.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>La data in cui il collegamento al sito è stato scaricato per la prima volta da [!DNL Marketo Measure]</p>
      </td>
      <td>
        <p>2018-08-02 06:36:50.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del collegamento al sito</p>
      </td>
      <td>Collegamento A</td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il collegamento al sito deve essere aggiornato o meno per ottenere l’assegnazione tag di Marekto Measure</p>
      </td>
      <td>
        <p>FALSE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td>
        <p>aw.6601259029.285077795</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'oggetto o l'entità principale per questa tabella. In questo caso, "SiteLink"</p>
      </td>
      <td>
        <p>CollegamentoSito</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del provider di annunci per il collegamento al sito</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L’URL della pagina di destinazione.</p>
        <p>(campo diagnostico, per elaborazione interna.)</p>
      </td>
      <td>
        <p>http://adobe.com/b2b-marketing-attribution?_bt =</p>
        <p>{creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valore precedente per URL_CURRENT.</p>
        <p>(campo diagnostico, per elaborazione interna.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Di cosa sarà decorato l’URL [!DNL Marketo Measure] Parametri.</p>
        <p>(campo diagnostico, per elaborazione interna.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del Snowflake del record</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di modifica del Snowflake del record</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di eliminazione del Snowflake del record se è stato eliminato</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_STAGE_DEFINITIONS {#biz-stage-definitions}

Elenco delle fasi importate o definite nella [!DNL Marketo Measure] applicazione.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per lo stage.</p>
      </td>
      <td>
        <p>01J3100000QE753EAD</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-22 17:27:27.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dello stage.</p>
      </td>
      <td>
        <p>Verbale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_INACTIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Indica se lo stage è considerato inattivo.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IN_CUSTOM_MODEL</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se lo stage è selezionato per il tracciamento nel modello personalizzato.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_BOOMERANG</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se lo stage è selezionato per il tracciamento come stadio boomerang.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_TRANSITION_TRACKING</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Indica se l’opzione Stage è selezionata per il tracciamento delle transizioni.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Stato della fase, come definito nella [!DNL Marketo Measure] Mappatura della fase dell'applicazione.</p>
      </td>
      <td>
        <p>Apri</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FROM_SALESFORCE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se lo stage viene importato da un sistema di origine esterno.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DEFAULT</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Indica se lo stage è impostato come predefinito.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLASSIFICA</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>La classificazione numerica dello stage, utilizzata per ordinare le fasi in ordine transitorio.</p>
      </td>
      <td>
        <p>53</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se lo stage è stato eliminato o meno.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_TOUCHPOINTS {#biz-touchpoints}

Punti di contatto per gli acquirenti, tutti i punti di contatto associati a un lead o a un contatto. Questa tabella sarà vuota se i punti di contatto lead o i punti di contatto contatti sono disattivati.

<table>
  <tbody>
    <tr>
      <th>Colonna</th>
      <th>Tipo di dati</th>
      <th>Descrizione</th>
      <th>Dati di esempio</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per il punto di contatto dell’acquirente (BT).</p>
      </td>
      <td>
        <p>TP2_Person_00Q0Z00013e2PYUAY_2018-08-27:20-04-40-565690.1ee8567c175a</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-29 22:29:30.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-MAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indirizzo e-mail associato al BT.</td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del contatto associato al BT.</p>
      </td>
      <td>0030Z00003K5bpKQAR</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID per l'account associato al BT.</p>
      </td>
      <td>
        <p>0013100001lSLScAAO</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id per il lead associato al BT.</p>
      </td>
      <td>
        <p>00Q0Z000013e2PYUAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>UNIQUE_ID_PERSON</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Record della persona padre relativo a un lead o a un contatto.</p>
      </td>
      <td>
        <p>Person_00Q0Z00013e2PYUAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_TOUCHPOINT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID per il punto di contatto utente che ha generato il BT.</p>
      </td>
      <td>
        <p>person@adobe.com_2018-08-29:18-14-53-8102030.10df92cbb414</p>
      </td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>ID per il visitatore associato al BT.</td>
      <td>v_277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data del punto di contatto.</p>
      </td>
      <td>
        <p>2018-08-27 20:04:40.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MARKETING_TOUCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tipo di attività, visita web, modulo web, chat web, chiamata telefonica, campagna [CRM] o attività [CRM]. In CRM è indicato come "tipo di punto di contatto".</p>
      </td>
      <td>
        <p>Modulo Web</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CANALE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il canale in cui rientra il punto di contatto, come definito nelle definizioni del canale personalizzato all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Canale di marketing - Percorso".</p>
      </td>
      <td>Social.LinkedIn</td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore del segmento per la prima categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</p>
      </td>
      <td>ABC</td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore del segmento per la seconda categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</p>
      </td>
      <td>
        <p>Sì</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY3</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore del segmento per la terza categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</p>
      </td>
      <td>
        <p>Altro</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY4</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore del segmento per la quarta categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</p>
      </td>
      <td>
        <p>Partner</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY5</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore del segmento per la quinta categoria in cui rientra il punto di contatto, come definito nelle definizioni del segmento all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY6</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore del segmento per la 6a categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY7</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per la settima categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY8</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per l’8a categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY9</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per la 9a categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY10</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per la decima categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY11</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per l’undicesima categoria in cui si trova il punto di contatto, come definito nelle definizioni del segmento all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY12</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per la dodicesima categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY13</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il valore del segmento per la tredicesima categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY14</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore del segmento per la quattordicesima categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY15</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore del segmento per la quindicesima categoria in cui si trova il punto di contatto, come definito nelle definizioni dei segmenti all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Segmenti".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NOME_BROWSER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall'indirizzo javascript e IP, il browser rilevato che l'utente era attivo durante la sessione.</p>
      </td>
      <td>Chrome</td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall'indirizzo javascript e IP, la versione rilevata del browser su cui l'utente si trovava durante la sessione.</p>
      </td>
      <td>
        <p>68</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, la piattaforma rilevata dall’utente durante la sessione.</p>
      </td>
      <td>
        <p>Windows</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, la versione rilevata della piattaforma su cui l’utente si trovava durante la sessione.</p>
      </td>
      <td>10_12</td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La prima pagina di destinazione della sessione che ha generato un punto di contatto. In CRM è indicato come "Pagina di destinazione".</p>
      </td>
      <td>
        <p>https://info.adobe.com/definitive-guide-to-pipeline-marketing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La prima pagina di destinazione della sessione che ha generato un punto di contatto. Una pagina di destinazione non elaborata conterrà tutti i parametri di query nell’URL. In CRM è indicato come "Pagina di destinazione - Raw".</p>
      </td>
      <td>
        <p>https://info.adpbe.com/definitive-guide-to-pipeline-marketing?utm_source=linkedin&amp;utm_medium=Social&amp;utm_campaign=SU_COM_Demand_ Skills&amp;utm_content=DGPM&amp;utm_term=lisu03151846&amp;_bl=66452504</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>In genere la pagina di destinazione esterna immediatamente prima che l’utente acceda al sito web. In CRM è indicato come "Pagina referente".</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>In genere la pagina di destinazione esterna immediatamente prima che l’utente acceda al sito web. Una pagina referente non elaborata può contenere parametri di query nell’URL. In CRM è indicato come "Pagina referente - Raw".</p>
      </td>
      <td>
        <p>https://www.linkedin.com/feed</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODULO_PAGINA</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il primo modulo registrato in una sessione che ha generato un punto di contatto. Gli invii dei moduli successivi non verranno visualizzati nella tabella Punti di contatto, ma nella tabella Form_Submit. In CRM è indicato come "URL del modulo".</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>FORM_PAGE_RAW</td>
      <td>varchar</td>
      <td>Il primo modulo registrato in una sessione che ha generato un punto di contatto. Gli invii dei moduli successivi non verranno visualizzati nella tabella Punti di contatto, ma nella tabella Form_Submit. Una pagina modulo non elaborata può contenere parametri di query nell’URL. In CRM è indicato come "URL modulo - Raw".</td>
      <td>https://info.adobe.com/demo?hsCtaTracking=98adcc2f-afe2-40c4-9d79-40dcc41663ee%7C3cfaa909-39cb-4f5d-93eb-be05de6b0180</td>
    </tr>
    <tr>
      <td>
        <p>FORM_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell’invio del modulo.</p>
      </td>
      <td>
        <p>2017-06-20 01:06:41.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITTÀ</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, la città rilevata in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>New York</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGIONE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, la regione rilevata in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>New York</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAESE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, il paese rilevato in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>Stati Uniti</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIO</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Utilizzato per definire il mezzo che ha portato al punto di contatto. Questo può essere analizzato dall’URL da utm_medium. Oppure, se [!DNL Marketo Measure] è in grado di risolvere un annuncio, può essere valori come "cpc" o "display".</p>
      </td>
      <td>
        <p>Social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Utilizzato per definire la sorgente che ha generato il punto di contatto. Questo può essere analizzato dall'URL da utm_source, generalmente impostato come "Campaign CRM" se è stato sincronizzato dal CRM, o se [!DNL Marketo Measure] è in grado di risolvere un annuncio, possono essere valori come "Google AdWords" o "Facebook". In CRM è indicato come "Origine punto di contatto".</p>
      </td>
      <td>
        <p>LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore immesso dall’utente nel browser per la ricerca e finito sul sito web. A seconda delle parole chiave acquistate, potrebbe corrispondere o meno alle parole chiave acquistate dalla piattaforma di ricerca a pagamento.</p>
      </td>
      <td>
        <p>misurazione markeot attribuzione</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Piattaforma di annunci [!DNL Marketo Measure] è stato in grado di risolvere da, tipicamente uno dei nostri partner di integrazione.</p>
      </td>
      <td>
        <p>LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’account dell’annuncio da cui è stata risolta l’inserzione.</p>
      </td>
      <td>
        <p>li.502664737</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’account dell’annuncio da cui è stata risolta l’inserzione.</p>
      </td>
      <td>
        <p>MM SC 2016_14605342_3/7-3/3/16</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’inserzionista dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’inserzionista dall’account dell’annuncio dal quale l’annuncio è stato risolto. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Marketo Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del sito dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del sito dall’account dell’annuncio dal quale è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>blocco stradale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della campagna dall’account dell’annuncio da cui è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>li.502664737.138949954</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna dall’account dell’annuncio dal quale è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>SU - Account COM - Competenze della domanda</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del gruppo di annunci dall'account dell'annuncio da cui è stato risolto l'annuncio. Questo vale solo per Google Adwords.</p>
      </td>
      <td>aw.6601259029.317738075.23105327435</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del gruppo di annunci dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale solo per Google AdWords.</p>
      </td>
      <td>Attribuzione marketing - Generale</td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’annuncio dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>dc.6114.8882972.25272734.492579576</td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’annuncio dall’account dell’annuncio dal quale l’annuncio è stato risolto. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>Webinar sul budget - barra laterale</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del creativo dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>li.502664737.138949954.66452504</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del creativo dall’account dell’annuncio dal quale è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>lisu03151846</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La prima riga del Creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>La generazione di piombo è fatta</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La seconda riga del creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Scarica la guida definitiva al marketing della pipeline: https://lnkd.in/e9xYj5M</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La pagina di destinazione che fa clic dall’annuncio di ricerca, estratta dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>https://image-store.slidesharecdn.com/d29165c0-1e0b-4ffc-a494-d2c77e7cd4a6-large.jpeg</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il nome dell’URL descrittivo mostrato nell’annuncio di ricerca, estratto dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>marektomeasure.com/guide</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della parola chiave acquistata dall’acquisto di ricerca a pagamento, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>__GAId__lisu03151846</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della parola chiave acquistata dall’acquisto di ricerca a pagamento, estratta dall’account dell’annuncio dal quale l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca)</p>
      </td>
      <td>
        <p>lisu03151846</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il tipo di corrispondenza trovato tra la frase di ricerca e la parola chiave acquistata.</p>
      </td>
      <td>
        <p>Ampio</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FIRST_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se questo punto di contatto viene trattato o meno come il primo tocco del percorso di opportunità.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_LEAD_CREATION_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se questo punto di contatto viene trattato o meno come punto di contatto per la creazione di un lead, viene toccato dal percorso di opportunità.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_OPP_CREATION_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se questo punto di contatto viene trattato o meno come la creazione di opportunità tocca il percorso di opportunità.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CLOSED_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se questo punto di contatto viene trattato o meno come il tocco di chiusura del percorso di opportunità.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>STAGES_TOUCHED</td>
      <td>varchar</td>
      <td>Questo campo è stato dichiarato obsoleto. Utilizzare le tabelle Stage_Transitions per informazioni sull'area di visualizzazione.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se questo punto di contatto ha compilato un modulo durante la sessione.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IMPRESSION_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se questo punto di contatto viene trattato o meno come la prima impressione del percorso di opportunità</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>La percentuale calcolata allocata a questo punto di contatto perché si tratta di un primo contatto (consulta Is_First_Touch).</p>
      </td>
      <td>
        <p>100</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_ANON_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>Percentuale calcolata allocata a questo punto di contatto perché si tratta di un contatto per la creazione di lead (consulta Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>100</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>U_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>La percentuale calcolata allocata a questo punto di contatto perché fa parte di un tocco a forma di u (consulta Is_First_Touch e Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>100</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>W_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>La percentuale calcolata allocata a questo punto di contatto perché fa parte di un tocco a forma di w (vedere Is_First_Touch, Is_Lead_Creation_Touch e Is_Opp_Creation_Touch). Previsto 0 poiché si tratta di un BT.</p>
      </td>
      <td>
        <p>0</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FULL_PATH_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>La percentuale calcolata allocata a questo punto di contatto perché fa parte di un modello di percorso completo (vedere Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch). Previsto 0 poiché si tratta di un BT.</p>
      </td>
      <td>
        <p>0</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_MODEL_PERCENTAGE</td>
      <td>numero(22,19)</td>
      <td>La percentuale calcolata allocata a questo punto di contatto perché fa parte di un modello personalizzato (vedere Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch). Previsto 0 poiché si tratta di un BT.</p>
      </td>
      <td>0</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se questo punto di contatto viene eliminato.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>-9004910726709710000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_URLS {#biz-urls}

Aggregazione di URL da pagine di destinazione, pagine di riferimento e visualizzazioni di pagina.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>L'URL completo.</p>
      </td>
      <td>
        <p>https://www.adobe.com/blog/strategic-marketing-plangoals</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SCHEMA</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La comunicazione sicura della pagina web attraverso la rete.</p>
      </td>
      <td>
        <p>https</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HOST</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dominio dell’URL, con tutti i sottodomini.</p>
      </td>
      <td>
        <p>www.adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PORTA</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La porta da un host Internet, opzionale in un URL.</p>
      </td>
      <td>
        <p>584</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PERCORSO</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La parte dell'URL che punta a una posizione specifica sull'host.</p>
      </td>
      <td>
        <p>/blog/strategico-marketing-plangos</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la visualizzazione Biz_Facts.</p>
      </td>
      <td>
        <p>5686109553536636820</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_USER_TOUCHPOINTS {#biz-user-touchpoints}

Tutti i punti di contatto creati da qualsiasi evento associato a un’e-mail.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Un ID univoco per il punto di contatto utente.</p>
      </td>
      <td>
        <p>person@adobe.com_2018-01-05:16-47-02-8803320.ddf67c101f58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-09-05 23:30:53.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-MAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Indirizzo e-mail associato al punto di contatto utente.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID per la sessione che ha creato il punto di contatto utente.</p>
      </td>
      <td>
        <p>2018-01-05:16-47-02-8803320.ddf67c101f58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_MEM_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID per il membro della campagna che ha creato il punto di contatto utente.</p>
      </td>
      <td>
        <p>00v0Z00001VTgv1QAD</p>
      </td>
    </tr>
    <tr>
      <td>CRM_ACTIVITY_ID</td>
      <td>varchar</td>
      <td>ID per l’attività che ha creato il punto di contatto utente.</td>
      <td>1678625515</td>
    </tr>
    <tr>
      <td>
        <p>CRM_EVENT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID per l’evento che ha creato il punto di contatto utente.</p>
      </td>
      <td>
        <p>00U0Z00000pCZmyUAG</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CRM_TASK_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>TI per l’attività che ha creato il punto di contatto utente.</p>
      </td>
      <td>
        <p>00T0Z00004Qbd1jUAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IMPRESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id per l’impression che ha creato il punto di contatto utente.</p>
      </td>
      <td>00T0Z00004Qbd1jUAB</td>
    </tr>
    <tr>
      <td>IS_FIRST_KNOWN_TOUCH</td>
      <td>booleano</td>
      <td>Se questo punto di contatto viene trattato o meno come il primo tocco del percorso di opportunità.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>Il primo ID cookie dell’ID visitatore correlato.</td>
      <td>v_36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data in cui si è verificato il punto di contatto utente.</p>
      </td>
      <td>
        <p>2018-01-05 16:47:02.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MARKETING_TOUCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tipo di attività, visita web, modulo web, chat web, chiamata telefonica, campagna [CRM] o attività [CRM]. In CRM è indicato come "tipo di punto di contatto".</p>
      </td>
      <td>
        <p>Modulo Web</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CANALE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il canale in cui rientra il punto di contatto, come definito nelle definizioni del canale personalizzato all’interno della [!DNL Marketo Measure] App. In CRM è indicato come "Canale di marketing - Percorso".</p>
      </td>
      <td>
        <p>Social.LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_BROWSER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall'indirizzo javascript e IP, il browser rilevato che l'utente era attivo durante la sessione.</p>
      </td>
      <td>
        <p>Firefox</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall'indirizzo javascript e IP, la versione rilevata del browser su cui l'utente si trovava durante la sessione.</p>
      </td>
      <td>
        <p>33</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, la piattaforma rilevata dall’utente durante la sessione.</p>
      </td>
      <td>
        <p>Mac</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, la versione rilevata della piattaforma su cui l’utente si trovava durante la sessione.</p>
      </td>
      <td>
        <p>10_12</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La prima pagina di destinazione della sessione che ha generato un punto di contatto. In CRM è indicato come "Pagina di destinazione".</p>
      </td>
      <td>
        <p>https://www.adobe.com/blog/budget-and-planning-maturity-model-b2b-marketing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La prima pagina di destinazione della sessione che ha generato un punto di contatto. Una pagina di destinazione non elaborata conterrà tutti i parametri di query nell’URL. In CRM è indicato come "Pagina di destinazione - Raw".</p>
      </td>
      <td>
        <p>https://www.adobe.com/blog/budget-and-planning-maturity-model-b2b-marketing?utm_source=feedburner&amp;utm_medium=feed&amp;utm_campaign=Feed%3A+ marketo+%maeasure%27s+Pipeline+Marketing+Blog%29</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>In genere la pagina di destinazione esterna immediatamente prima che l’utente acceda al sito web. In CRM è indicato come "Pagina referente".</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>In genere la pagina di destinazione esterna immediatamente prima che l’utente acceda al sito web. Una pagina referente non elaborata può contenere parametri di query nell’URL. In CRM è indicato come "Pagina referente - Raw".</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODULO_PAGINA</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il primo modulo registrato in una sessione che ha generato un punto di contatto. Gli invii dei moduli successivi non verranno visualizzati nella tabella Attribution_Touchpoints, ma nella tabella Form_Submit. In CRM è indicato come "URL del modulo".</p>
      </td>
      <td>
        <p>http://info.adobe.com/adwords-for-lead-generation</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il primo modulo registrato in una sessione che ha generato un punto di contatto. Gli invii dei moduli successivi non verranno visualizzati nella tabella Attribution_Touchpoints, ma nella tabella Form_Submit. Una pagina modulo non elaborata può contenere parametri di query nell’URL. In CRM è indicato come "URL modulo - Raw".</p>
      </td>
      <td>
        <p>http://info.adobe.com/adwords-for-lead-generation?utm_source=linkedin&amp;utm_medium=paid&amp;utm_content=sfskill&amp;utm Guida a _campaign=Content%20-%20AdWords%20</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Data dell’invio del modulo.</p>
      </td>
      <td>
        <p>2015-06-03 17:49:10.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITTÀ</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, la città rilevata in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>Oakland</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGIONE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, la regione rilevata in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>California</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAESE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Dall’indirizzo javascript e IP, il paese rilevato in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>Stati Uniti</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIO</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Utilizzato per definire il mezzo che ha portato al punto di contatto. Questo può essere analizzato dall’URL da utm_medium. Oppure, se [!DNL Marketo Measure] è in grado di risolvere un annuncio, può essere valori come "cpc" o "display".</p>
      </td>
      <td>
        <p>pagato</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Utilizzato per definire la sorgente che ha generato il punto di contatto. Questo può essere analizzato dall'URL da utm_source, generalmente impostato come "Campaign CRM" se è stato sincronizzato dal CRM, o se [!DNL Marketo Measure] è in grado di risolvere un annuncio, possono essere valori come "Google AdWords" o "Facebook". In CRM è indicato come "Origine punto di contatto".</p>
      </td>
      <td>
        <p>linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il valore immesso dall’utente nel browser per la ricerca e finito sul sito web. A seconda delle parole chiave acquistate, potrebbe corrispondere o meno alle parole chiave acquistate dalla piattaforma di ricerca a pagamento.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Piattaforma di annunci [!DNL Marketo Measure] è stato in grado di risolvere da, tipicamente uno dei nostri partner di integrazione.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’account dell’annuncio da cui è stata risolta l’inserzione.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’account dell’annuncio da cui è stata risolta l’inserzione.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Account</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’inserzionista dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’inserzionista dall’account dell’annuncio dal quale l’annuncio è stato risolto. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del sito dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del sito dall’account dell’annuncio dal quale è stato risolto l’annuncio. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale solo per Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>blocco stradale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della campagna dall’account dell’annuncio da cui è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029.208548635</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della campagna dall’account dell’annuncio dal quale è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>Brand</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del gruppo di annunci dall'account dell'annuncio da cui è stato risolto l'annuncio. Questo vale solo per Google Adwords.</p>
      </td>
      <td>
        <p>aw.6601259029.208548635.1675016675</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del gruppo di annunci dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale solo per Google AdWords.</p>
      </td>
      <td>
        <p>Brand - Core</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID dell’annuncio dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>dc.6114.8882972.25272734.492579576</td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome dell’annuncio dall’account dell’annuncio dal quale l’annuncio è stato risolto. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>Webinar sul budget - barra laterale</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID del creativo dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>aw.6601259029.208548635.1675016675.195329631298</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome del creativo dall’account dell’annuncio dal quale è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Sito ufficiale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La prima riga del Creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Pianificazione e attribuzione dei ricavi</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La seconda riga del creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Scopri perché più di 250 aziende scelgono [!DNL Marketo Measure] per l’attribuzione marketing. Prendi una demo!</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>La pagina di destinazione che fa clic dall’annuncio di ricerca, estratta dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>http://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il nome dell’URL descrittivo mostrato nell’annuncio di ricerca, estratto dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID della parola chiave acquistata dall’acquisto di ricerca a pagamento, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>aw.6601259029.208548635.1675016675.46267805426</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Nome della parola chiave acquistata dall’acquisto di ricerca a pagamento, estratta dall’account dell’annuncio dal quale l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca)</p>
      </td>
      <td>
        <p>[marketo]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Il tipo di corrispondenza trovato tra la frase di ricerca e la parola chiave acquistata.</p>
      </td>
      <td>
        <p>Esatto</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se questo punto di contatto ha compilato un modulo durante la sessione.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IMPRESSION_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se questo punto di contatto viene trattato o meno come la prima impressione del percorso di opportunità.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il punto di contatto viene eliminato o meno.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>number(38,0)</td>
      <td>Chiave esterna per la visualizzazione Biz_Facts.</td>
      <td>-5269090762570690000</td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_WEB_HOST_MAPPINGS {#biz-web-host-mappings}

Mappatura di una tabella da mappare [!DNL Marketo Measure] ID sessione per Adobe ECID e Munckin Id.

<table>
  <tbody>
    <tr>
      <th>
        <p>Colonna</p>
      </th>
      <th>
        <p>Tipo di dati</p>
      </th>
      <th>
        <p>Descrizione</p>
      </th>
      <th>
        <p>Dati di esempio</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Un ID univoco per il record di mappatura.</td>
      <td>
        <p>0d643578c0c74753eff91abe668ed328|2020-06-17:19:03:36|0002|0|568668</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La [!DNL Marketo Measure] id cookie registrato.</td>
      <td>0d643578c0c74753eff91abe668ed328</td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Il primo ID cookie dell’ID visitatore correlato.</td>
      <td>v_0d643578c0c74753eff91abe668ed328</td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>La [!DNL Marketo Measure] ID sessione.</td>
      <td>2018-08-06:01-35-24-1231230.9bc63c34482f</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>Data in cui è stata registrata la mappatura.</td>
      <td>
        <p>2020-06-17 19:03:36.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell'ultima modifica del record.</p>
      </td>
      <td>
        <p>2020-06-17 19:03:36.000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE</td>
      <td>
        <p>varchar</p>
      </td>
      <td>URL della visualizzazione pagina, senza parametri di query.</td>
      <td>
        <p>https://learn.atest.com/simplify-retention-starter-kit.html</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_RAW</td>
      <td>
        <p>varchar</p>
      </td>
      <td>URL della visualizzazione pagina, inclusi eventuali parametri di query.</td>
      <td>
        <p>https://learn.atest.com/simplify-retention-starter-kit.html?x=nGfrBF&amp;utm_medium=cpc&amp;utm_source=intensify</p>
      </td>
    </tr>
    <tr>
      <td>IP_ADDRESS</td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indirizzo IP registrato.</td>
      <td>
        <p>159.203.142.127</p>
      </td>
    </tr>
    <tr>
      <td>TIPO</td>
      <td>
        <p>varchar</p>
      </td>
      <td>Indica il tipo di evento.</td>
      <td>
        <p>HostMapping</p>
      </td>
    </tr>
    <tr>
      <td>USER_AGENT_STRING</td>
      <td>
        <p>varchar</p>
      </td>
      <td>Dispositivo e browser registrati al momento della visualizzazione della pagina.</td>
      <td>
        <p>Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, come Gecko) Chrome/79.0.3945.130 Safari/537.36</p>
      </td>
    </tr>
    <tr>
      <td>CLIENT_SEQUENCE</td>
      <td>varchar</td>
      <td>Indica l’ordine in cui si è verificata la visualizzazione della pagina nella sessione.</td>
      <td>2</td>
    </tr>
    <tr>
      <td>CLIENT_RANDOM</td>
      <td>varchar</td>
      <td>Utilizzato per il controllo e l'elaborazione interni.</td>
      <td>566868</td>
    </tr>
    <tr>
      <td>IS_DUPLICATO</td>
      <td>booleano</td>
      <td>Indica se il record è considerato un duplicato.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>IS_PROCESSED</td>
      <td>booleano</td>
      <td>Utilizzato per elaborazione interna.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>MAPPING_TYPE</td>
      <td>varchar</td>
      <td>Il tipo di ID mappato al [!DNL Marketo Measure] ID cookie.</td>
      <td>Adobe_OrgId_Ecid</td>
    </tr>
    <tr>
      <td>MAPPING_ORD_ID</td>
      <td>varchar</td>
      <td>ID organizzazione Adobe IMS.</td>
      <td>8CC867C25245ADC30A490D4C</td>
    </tr>
    <tr>
      <td>MAPPING_COOKIE_ID</td>
      <td>varchar</td>
      <td>Adobe ECID per l'ID organizzazione specificato.</td>
      <td>09860926390077352923264316157493772857</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

## Query di esempio {#sample-queries}

**Quanti punti di contatto dell’acquirente (BT) ci sono stati per ogni canale/canale del mese scorso?**

```
--Note: This query can quickly be modified to show Buyer Attribution Touchpoint (BAT) counts by switching the biz_touchpoints table to the biz_attribution_touchpoints table.
 
select trim(split(ch.name,'.')[0])  as channel
      ,trim(split(ch.name,'.')[1])  as subchannel
      ,count(bt.id)                 as buyer_touchpoint_count
  from biz_user_touchpoints     ut
       left outer join
       biz_touchpoints          bt
        on bt.user_touchpoint_id    = ut.id
       and bt._deleted_date         is null
       left outer join
       biz_channels             ch
        on ut.channel               = ch.id
       and ch._deleted_date         is null
 where ut._deleted_date is null
   and ut.touchpoint_date between add_months(date_trunc(month,current_date),-1) and last_day(dateadd(month,-1,current_date))
group by 1,2
```

**Quanti ricavi attribuiti per ogni canale sono stati chiusi nell’ultimo mese, per il modello di attribuzione del percorso completo?**

```
--Note: This query does not perform any currency conversion.  If your data contains multiple currencies, you will need to add in logic to perform the conversion to the desired currency using the biz_conversion_rates table.
 
select trim(split(ch.name,'.')[0])  as channel
      ,sum(opp.amount*(bat.full_path_percentage/100))   as attributed_revenue
  from biz_user_touchpoints         ut
       inner join
       biz_attribution_touchpoints  bat
        on bat.user_touchpoint_id   = ut.id
       and bat._deleted_date        is null
       inner join
       biz_opportunities            opp
        on bat.opportunity_id       = opp.id
       and opp._deleted_date        is null
       and opp.is_closed            = true
       and opp.is_won               = true
       and opp.close_date between add_months(date_trunc(month,current_date),-1) and last_day(dateadd(month,-1,current_date))
       left outer join
       biz_channels                 ch
        on ut.channel               = ch.id
       and ch._deleted_date         is null
 where ut._deleted_date is null
group by 1
```

**Qual è l&#39;intero percorso per una persona?  Mostra tutti i punti di contatto per un singolo indirizzo e-mail.**

```
select ut.touchpoint_date
      ,ut.marketing_touch_type
      ,listagg(distinct ifnull(sdl.stage_name,sdo.stage_name),',')           as touchpoint_position
  from biz_user_touchpoints         ut
       left outer join
       biz_touchpoints              bt
        on bt.user_touchpoint_id    = ut.id
       and bt._deleted_date         is null
       left outer join
       biz_attribution_touchpoints  bat
        on bat.user_touchpoint_id   = ut.id
       and bat._deleted_date        is null
       left outer join
       biz_lead_stage_transitions   lst
        on lst.touchpoint_id        = bt.id
       and lst._deleted_date        is null
       and lst.is_pending           = false
       and lst.is_non_transitional  = false
       left outer join
       biz_stage_definitions        sdl
        on lst.stage_id             = sdl.id
       and sdl._deleted_date        is null
       left outer join
       biz_opp_stage_transitions    ost
        on ost.touchpoint_id        = bat.id
       and ost._deleted_date        is null
       and ost.is_pending           = false
       and ost.is_non_transitional  = false
       left outer join
       biz_stage_definitions        sdo
        on ost.stage_id             = sdo.id
       and sdo._deleted_date        is null
 where ut._deleted_date     is null
   and ut.email             = [email address]
group by 1,2
order by 1
```

**Mostra tutti i punti di contatto di attribuzione dell’acquirente (BAT) e i relativi ricavi attribuiti per un’unica opportunità.**

>[!NOTE]
>
>Questa query restituisce i ricavi attribuiti per il modello a forma w. Modificare il modello aggiornando il campo nel calcolo dei ricavi attribuiti.

```
select bat.id
      ,bat.touchpoint_date
      ,bat.email
      ,opp.amount*(bat.w_shape_percentage/100)             as attributed_revenue
      ,listagg(osd.stage_name,', ')                        as touchpoint_position
  from biz_opportunities               opp
       inner join
       biz_attribution_touchpoints     bat
        on bat.opportunity_id      = opp.id
       and bat._deleted_date       is null
       left outer join
       biz_opp_stage_transitions       ost
        on ost.touchpoint_id       = bat.id
       and ost._deleted_date       is null
       and ost.is_pending          = false
       and ost.is_non_transitional = false
       left outer join
       biz_stage_definitions            osd
        on ost.stage_id             = osd.id
       and osd._deleted_date        is null
 where opp._deleted_date    is null
   and opp.id               = [opportunity id]
group by 1,2,3,4
order by touchpoint_date
```

[Torna all&#39;inizio](#data-warehouse-schema)
