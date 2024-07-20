---
unique-page-id: 35586140
description: Schema Data Warehouse - Marketo Measure - Documentazione del prodotto
title: Data Warehouse schema
exl-id: f1895eb1-a32d-4c43-93fb-0aa838527946
feature: Data Warehouse
source-git-commit: 9f374537dd3690b5c904e2ac1933ff460dc66282
workflow-type: tm+mt
source-wordcount: '21110'
ht-degree: 3%

---

# Data Warehouse schema {#data-warehouse-schema}

Data Warehouse consente di tenere traccia di quanto desideri, creare rapporti sui dati di attribuzione ovunque desideri e collegarli ad altri set di dati.

>[!IMPORTANT]
>
>* Le righe con un valore per _DELETED_DATE verranno mantenute per 7 Snowflake e quindi rimosse.
>* I fusi orari utilizzati nel Snowflake sono conformi al tempo coordinato universale (UTC).

>[!NOTE]
>
>[Fai clic qui](#sample-queries) per visualizzare le query di esempio in fondo a questo articolo.

## Diagrammi di relazione entità {#entity-relationship-diagrams}

L&#39;ERD _Data Warehouse Data Model_ mostra il modo in cui i dati nel data warehouse devono scorrere e essere collegati tra loro. Questo diagramma non include tutte le tabelle disponibili nel data warehouse perché alcune di esse rappresentano tabelle di mappatura, viste di altre tabelle già presenti o tabelle obsolete che non si consiglia di utilizzare più. Vedi le descrizioni dettagliate delle tabelle e delle colonne presenti nel data warehouse di seguito. Molte di queste tabelle contengono campi denormalizzati, tuttavia questo diagramma è il modello dati consigliato, che sfrutta i dati provenienti da tabelle dimensionali.

L&#39;ulteriore modello dati dimensionale _Ads_ ERD presenta una visualizzazione del modo migliore per collegare le tabelle per le dimensioni specifiche degli annunci alle tabelle nel modello dati principale. Anche se le dimensioni degli annunci vengono denormalizzate in altre tabelle, questo rappresenta il modello consigliato per unire queste dimensioni.

_Fare clic su un&#39;immagine per la versione a schermo intero_

<table style="table-layout:auto"> 
 <tbody> 
  <tr> 
   <th>Data Warehouse modello dati</th> 
   <th>Aggiunge il modello dati dimensionale</th> 
  </tr> 
  <tr> 
   <td><a href="assets/data-warehouse-data-model.pdf"><img src="assets/data-warehouse-data-model-thumb.png"></a></td>
   <td><a href="assets/ads-dimensional-data-model.pdf"><img src="assets/ads-dimensional-data-model-thumb.png"></a></td> 
  </tr> 
 </tbody> 
</table>

## Visualizzazioni {#views}

### BIZ_ACCOUNT {#biz-accounts}

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
      <td>L’ID account dal sistema di origine.</td>
      <td>0013100001kpAZxAAM</td>
    </tr>
    <tr>
      <td>DATA_CREAZIONE</td>
      <td>timestamp_ntz</td>
      <td>La data di creazione dell’account, dal sistema di origine.</td>
      <td>2016-08-28 00:32:55.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica dell’account, dal sistema di origine.</td>
      <td>01/08/2018 17:38:30.000</td>
    </tr>
    <tr>
      <td>NOME</td>
      <td>varchar</td>
      <td>Nome account, dal sistema di origine.</td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>SITO_WEB</td>
      <td>varchar</td>
      <td>Sito web dell’account, come registrato nel sistema di origine, utilizzato per la mappatura lead in account.</td>
      <td>www.adobe.com</td>
    </tr>
    <tr>
      <td>ENGAGEMENT_RATING</td>
      <td>varchar</td>
      <td>Un livello lettera (A, B, C, D, N/A) generato dal modello di apprendimento automatico [!DNL Marketo Measure]. Il valore sarà nullo se ABM è disabilitato.</td>
      <td>B</td>
    </tr>
    <tr>
      <td>ENGAGEMENT_SCORE</td>
      <td>numero(38,19)</td>
      <td>Un punteggio numerico calcolato da [!DNL Marketo Measure] Machine Learning per generare il punteggio di coinvolgimento predittivo (Engagement_Rating). Il valore sarà nullo se ABM è disabilitato.</td>
      <td>0,1417350147058800000</td>
    </tr>
    <tr>
      <td>DOMINIO</td>
      <td>varchar</td>
      <td>Versione analizzata del sito web, in cui è memorizzato solo il dominio.</td>
      <td>adobe</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>booleano</td>
      <td>Indica se il record viene eliminato o meno nel sistema di origine.</td>
      <td>falso</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Proprietà personalizzate importate da [!DNL Marketo Measure] dal sistema di origine in formato JSON.</td>
      <td>{"Account_Type__c": "Security", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td><b>∗</b> SETTORE</td>
      <td>varchar</td>
      <td>Attività principale dell’account.</td>
      <td>Retail, telecomunicazioni</td>
    </tr>
    <tr>
      <td>PAESE <b>∗</b></td>
      <td>varchar</td>
      <td>Parte del paese dell’indirizzo dell’account.</td>
      <td>USA, Canada</td>
    </tr>
  </tbody>
</table>
<p>
<b>∗</b> <i>Disponibile solo in Marketo Measure Ultimate</i>
<p>

### BIZ_ACCOUNT_TO_EMAIL {#biz-account-to-emails}

Mappatura della tabella tra gli indirizzi e-mail di lead/contatti noti e gli account. Questa tabella sarà vuota se ABM è disabilitato.

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
      <td>ID univoco del record.</td>
      <td>0013800001MMPPiAAP_person@adobe.com|2022-01-05 17:22:13.000</td>
    </tr>
    <tr>
      <td>ACCOUNT_ID</td>
      <td>varchar</td>
      <td>ID account di sistema Source.</td>
      <td>0013100001phrBAAAY</td>
    </tr>
    <tr>
      <td>EMAIL</td>
      <td>varchar</td>
      <td>Indirizzo e-mail mappato sull’account, tramite le relazioni di contatto o la mappatura lead-account.</td>
      <td>person@adobe.com</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica dell’account, dal sistema di origine.</td>
      <td>2018-08-31 23:53:39.000</td>
    </tr>
    <tr>
      <td>DATA_CREAZIONE</td>
      <td>timestamp_ntz</td>
      <td>La data di creazione dell’account, dal sistema di origine.</td>
      <td>2018-08-18 22:01:32.000</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>booleano</td>
      <td>Indica se il record viene considerato eliminato o meno.</td>
      <td>falso</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ACTIVITIES {#biz-activities}

Attività importate da un sistema di origine o da un account annuncio connesso.

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
      <td>L'ID attività dal sistema di origine.</td>
      <td>1678625515</td>
    </tr>
    <tr>
      <td>LEAD_ID</td>
      <td>varchar</td>
      <td>ID del lead associato all’attività.</td>
      <td>15530482</td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>ID del contatto associato all’attività.
      </td>
      <td>13792552</td>
    </tr>
    <tr>
      <td>ACTIVITY_TYPE_ID</td>
      <td>varchar</td>
      <td>ID per il tipo di attività, dal sistema di origine.</td>
      <td>104</td>
    </tr>
    <tr>
      <td>NOME_TIPO_ATTIVITÀ</td>
      <td>varchar</td>
      <td>Nome dell’attività, dal sistema di origine.</td>
      <td>
        <p>modifica stato in progressione</p>
      </td>
    </tr>
    <tr>
      <td>DATA_INIZIALE</td>
      <td>timestamp_ntz</td>
      <td>Data di inizio dell’attività, dal sistema di origine.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>END_DATE</td>
      <td>timestapm_ntz</td>
      <td>Data di fine dell'attività, dal sistema di origine.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>ID_CAMPAGNA</td>
      <td>varchar</td>
      <td>ID della campagna di cui fa parte l’attività, dal sistema di origine.</td>
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
      <td>DATA_CREAZIONE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione della riga nel sistema di origine.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata alla riga nel sistema di origine.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>booleano</td>
      <td>Indica se il record viene considerato eliminato o meno nel sistema di origine.</td>
      <td>falso</td>
    </tr>
    <tr>
      <td>AD_FORM_ID</td>
      <td>varchar</td>
      <td>ID del modulo annuncio di cui fa parte l’attività, dal sistema di origine.</td>
      <td>li.507063119.3757704</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ADS {#biz-ads}

Annunci importati da qualsiasi account annuncio collegato.

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
      <td>Un ID univoco per l’annuncio.</td>
      <td>fb.106851586409075.6052044288804.6052044290004.6053457066804</td>
    </tr>
    <tr>
      <td>DISPLAY_ID</td>
      <td>varchar</td>
      <td>L’ID dell’annuncio dal sistema di origine.</td>
      <td>6053457066804</td>
    </tr>
    <tr>
      <td>AD_ACCOUNT_UNIQUE_ID</td>
      <td>varchar</td>
      <td>ID dell’account annuncio da cui è stato importato l’annuncio.</td>
      <td>fb.106851586409075</td>
    </tr>
    <tr>
      <td>AD_ACCOUNT_NAME</td>
      <td>varchar</td>
      <td>Nome dell’account dell’annuncio da cui è stato importato l’annuncio.</td>
      <td>[!DNL Marketo Measure] Account</td>
    </tr>
    <tr>
      <td>ADVERTISER_UNIQUE_ID</td>
      <td>varchar</td>
      <td>ID dell’inserzionista per l’annuncio, in particolare per Doubleclick.</td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>NOME_INSERZIONISTA</td>
      <td>varchar</td>
      <td>Nome dell’inserzionista dell’annuncio, in particolare per Doubleclick.</td>
      <td>Marketing analytics</td>
    </tr>
    <tr>
      <td>AD_GROUP_UNIQUE_ID</td>
      <td>varchar</td>
      <td>ID del gruppo di annunci dell’annuncio.</td>
      <td>fb.106851586409075.6052044288804.6052044290004</td>
    </tr>
    <tr>
      <td>AD_GROUP_NAME</td>
      <td>varchar</td>
      <td>Nome del gruppo di annunci per l’annuncio.</td>
      <td>Set di annunci per l’annuncio B</td>
    </tr>
    <tr>
      <td>AD_CAMPAIGN_UNIQUE_ID</td>
      <td>varchar</td>
      <td>ID della campagna per l’annuncio.</td>
      <td>fb.106851586409075.6052044288804</td>
    </tr>
    <tr>
      <td>AD_CAMPAIGN_NAME</td>
      <td>varchar</td>
      <td>Nome della campagna per l’annuncio.</td>
      <td>Campagna di generazione di lead</td>
    </tr>
    <tr>
      <td>IS_ACTIVE</td>
      <td>booleano</td>
      <td>Se l’annuncio è ancora attivo o meno nel sistema di origine.</td>
      <td>falso</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>booleano</td>
      <td>Se l’annuncio è stato eliminato o meno nel sistema di origine.</td>
      <td>falso</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica del record.</td>
      <td>2018-08-02 06:35:59.000</td>
    </tr>
    <tr>
      <td>PRIMO_IMPORTATO</td>
      <td>timestamp_ntz</td>
      <td>Data della prima importazione del record dal sistema di origine.</td>
      <td>2018-08-02 06:35:59.000</td>
    </tr>
    <tr>
      <td>NOME</td>
      <td>varchar</td>
      <td>Nome dell’annuncio, dal sistema di origine.</td>
      <td>Annuncio 2</td>
    </tr>
    <tr>
      <td>NEED_UPDATE</td>
      <td>booleano</td>
      <td>Indica se l'annuncio deve essere aggiornato per l'assegnazione tag [!DNL Marketo Measure].
      <p>(Campo diagnostico utilizzato dall'elaborazione interna).
      </td>
      <td>falso</td>
    </tr>
    <tr>
      <td>CHIAVE_RAGGRUPPAMENTO</td>
      <td>varchar</td>
      <td>Campo diagnostico, utilizzato per l’elaborazione interna.</td>
      <td>fb.106851586409075.6052044288804.6052044290004</td>
    </tr>
    <tr>
      <td>ENTITY_TYPE</td>
      <td>varchar</td>
      <td>Oggetto o entità principale per questa tabella. In questo caso, "Ad".</td>
      <td>Annuncio</td>
    </tr>
    <tr>
      <td>TIPO_PROVIDER</td>
      <td>varchar</td>
      <td>Nome del provider dell’annuncio per l’annuncio.</td>
      <td>Facebook</td>
    </tr>
    <tr>
      <td>URL_CURRENT</td>
      <td>varchar</td>
      <td>L’URL della pagina di destinazione.
        <p>(Campo diagnostico, per elaborazione interna).
      </td>
      <td></td>
    </tr>
    <tr>
      <td>URL_OLD</td>
      <td>varchar</td>
      <td>Valore precedente per URL_CURRENT.
      <p>(Campo diagnostico, per elaborazione interna).
      </td>
      <td></td>
    </tr>
    <tr>
      <td>URL_RICHIESTO</td>
      <td>varchar</td>
      <td>Specifica l'URL con i parametri [!DNL Marketo Measure].
      <p>(Campo diagnostico, per elaborazione interna).
      </td>
      <td></td>
    </tr>
    <tr>
      <td>URL_ALTENATIVES</td>
      <td>varchar</td>
      <td>Importato dal sistema di origine.
      <p>(Campo diagnostico, per elaborazione interna).
      </td>
      <td></td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>numero(38,0)</td>
      <td>Chiave esterna per la vista Biz_Facts.</td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_INSERZIONISTI {#biz-advertisers}

Inserzionisti importati da qualsiasi account annuncio collegato.

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
      <td>Un ID univoco per l’inserzionista.</td>
      <td>dc.6114.9143143</td>
    </tr>
    <tr>
      <td>DISPLAY_ID</td>
      <td>varchar</td>
      <td>L'ID dell'inserzionista dal sistema di origine.</td>
      <td>9143143</td>
    </tr>
    <tr>
      <td>AD_ACCOUNT_UNIQUE_ID</td>
      <td>varchar</td>
      <td>ID dell’account annuncio da cui è stato importato l’annuncio.</td>
      <td>fb.106851586409075</td>
    </tr>
    <tr>
      <td>AD_ACCOUNT_NAME</td>
      <td>varchar</td>
      <td>Nome dell’account dell’annuncio da cui è stato importato l’annuncio.</td>
      <td>[!DNL Marketo Measure] Account</td>
    </tr>
    <tr>
      <td>ADVERTISER_UNIQUE_ID</td>
      <td>varchar</td>
      <td>ID dell’inserzionista, specifico per Doubleclick.</td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>NOME_INSERZIONISTA</td>
      <td>varchar</td>
      <td>Nome dell’inserzionista, specificamente per Doubleclick.</td>
      <td>[!DNL Marketo Measure] Marketing analytics</td>
    </tr>
    <tr>
      <td>AD_GROUP_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Previsto null poiché non vi è alcun gruppo di annunci sopra l’inserzionista in alcuna gerarchia di annunci.</td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>AD_GROUP_NAME</td>
      <td>varchar</td>
      <td>Previsto null poiché non vi è alcun gruppo di annunci sopra l’inserzionista in alcuna gerarchia di annunci.</td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>AD_CAMPAIGN_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Previsto null poiché nessuna campagna pubblicitaria si trova al di sopra dell’inserzionista in alcuna gerarchia di annunci.</td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>AD_CAMPAIGN_NAME</td>
      <td>varchar</td>
      <td>Previsto null poiché nessuna campagna si trova al di sopra dell’inserzionista in alcuna gerarchia di annunci.</td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>IS_ACTIVE</td>
      <td>booleano</td>
      <td>Indica se l'inserzionista è ancora attivo nel sistema di origine.</td>
      <td>vero</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>booleano</td>
      <td>Indica se l'inserzionista è stato eliminato o meno nel sistema di origine.</td>
      <td>falso</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica del record.</td>
      <td>2018-08-02 06:35:59.000</td>
    </tr>
    <tr>
      <td>PRIMO_IMPORTATO</td>
      <td>timestamp_ntz</td>
      <td>Data della prima importazione del record dal sistema di origine.</td>
      <td>2018-08-02 06:35:59.000</td>
    </tr>
    <tr>
      <td>NOME</td>
      <td>varchar</td>
      <td>Nome dell'inserzionista, dal sistema di origine.</td>
      <td>[!DNL Marketo Measure] Marketing analytics</td>
    </tr>
    <tr>
      <td>NEED_UPDATE</td>
      <td>booleano</td>
      <td>Indica se l'inserzionista deve essere aggiornato per l'assegnazione tag [!DNL Marketo Measure].
      <p>(Campo diagnostico utilizzato dall'elaborazione interna).
      </td>
      <td>falso</td>
    </tr>
    <tr>
      <td>CHIAVE_RAGGRUPPAMENTO</td>
      <td>varchar</td>
      <td>Campo diagnostico, utilizzato per l’elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>ENTITY_TYPE</td>
      <td>varchar</td>
      <td>Oggetto o entità principale per questa tabella. In questo caso, "Inserzionista".</td>
      <td>Inserzionista</td>
    </tr>
    <tr>
      <td>TIPO_PROVIDER</td>
      <td>varchar</td>
      <td>Il provider dell’annuncio per l’inserzionista.</td>
      <td>Doubleclick</td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>numero(38,0)</td>
      <td>Chiave esterna per la vista Biz_Facts.</td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_ACCOUNTS {#biz-ad-accounts}

Account annuncio importati da qualsiasi account annuncio collegato.

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
      <td>
        <p>Un identificatore univoco per l’account dell’annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td>L’ID dell’account dell’annuncio dal sistema di origine.</td>
      <td>
        <p>6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>Previsto null poiché questo è il record per gli account annuncio nella gerarchia annunci.</td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>Previsto null poiché questo è il record per gli account annuncio nella gerarchia annunci.</td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non vi è alcun inserzionista al di sopra degli Account annuncio in alcuna gerarchia di annunci.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>NOME_INSERZIONISTA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non vi è alcun inserzionista al di sopra degli Account annuncio in alcuna gerarchia di annunci.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non vi è alcun gruppo di annunci al di sopra della gerarchia degli account di annunci.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non vi è alcun gruppo di annunci al di sopra della gerarchia degli account di annunci.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore atteso è nullo poiché nessuna campagna pubblicitaria si trova al di sopra della gerarchia degli account pubblicitari in qualsiasi gerarchia di annunci.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore atteso è nullo poiché nessuna campagna pubblicitaria si trova al di sopra della gerarchia degli account pubblicitari in qualsiasi gerarchia di annunci.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se l'account dell'annuncio è ancora attivo nel sistema di origine.</p>
      </td>
      <td>
        <p>vero</p>
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
        <p>Indica se l'account dell'annuncio è stato eliminato o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-09-06 12:54:37.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMO_IMPORTATO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data della prima importazione del record dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>varchar</td>
      <td>Nome dell’account dell’annuncio, dal sistema di origine.</td>
      <td>
        <p>[!DNL Marketo Measure] Account annuncio</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEED_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se l'inserzionista deve essere aggiornato per l'assegnazione tag [!DNL Marketo Measure].</p>
        <p>(Campo diagnostico utilizzato dall'elaborazione interna).</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CHIAVE_RAGGRUPPAMENTO</p>
      </td>
      <td>varchar</td>
      <td>Campo diagnostico, utilizzato per l’elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Oggetto o entità principale per questa tabella. In questo caso, "Account".</p>
      </td>
      <td>
        <p>Account</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TIPO_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il nome del provider dell’annuncio per l’account dell’annuncio.</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_CURRENCY_UNIT</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il codice valuta utilizzato per l’account annuncio dal sistema di origine.</p>
      </td>
      <td>
        <p>USD</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COMPANY_ID</p>
      </td>
      <td>varchar</td>
      <td>Utilizzato per l’elaborazione interna.</td>
      <td>1933789</td>
    </tr>
    <tr>
      <td>
        <p>SORGENTE</p>
      </td>
      <td>varchar</td>
      <td>Analizzato dall’URL da utm_source.</td>
      <td>
        <p>Social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIUM</p>
      </td>
      <td>varchar</td>
      <td>Analizzato dall’URL da utm_medium.</td>
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
        <p>17260,000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_IMPRESSIONS</p>
      </td>
      <td>
        <p>numero(38,0)</p>
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
        <p>numero(38,0)</p>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Il numero di conversioni segnalate dagli ultimi 30 giorni, applicabile solo ad AdWords.</p>
      </td>
      <td>
        <p>180</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>varchar</td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>varchar</td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUIRED</p>
      </td>
      <td>varchar</td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>varchar</td>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
      </td>
      <td>
        <p>-4609512587744160000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_CAMPAIGNS {#biz-ad-campaigns}

Campagne importate da account di annunci, sistemi di origine, utm e auto-segnalati collegati.

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
      <td>
        <p>ID univoco della campagna.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td>L’ID della campagna dal sistema di origine.</td>
      <td>
        <p>285114995</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account annuncio da cui è stata importata la campagna.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’account annuncio da cui è stata importata la campagna.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’inserzionista per la campagna, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_INSERZIONISTA</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non vi è alcun gruppo di annunci sopra la campagna in alcuna gerarchia di annunci.</p>
      </td>
      <td>
        <p>nulle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non vi è alcun gruppo di annunci sopra la campagna in alcuna gerarchia di annunci.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID univoco per la campagna, utilizza il campo ID.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della campagna, utilizza invece il campo Nome.</p>
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
        <p>Indica se la campagna è ancora attiva nel sistema di origine.</p>
      </td>
      <td>
        <p>vero</p>
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
        <p>Indica se la campagna è stata eliminata o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMO_IMPORTATO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data della prima importazione del record dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della campagna.</p>
      </td>
      <td>
        <p>Retargeting dei partner</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEED_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la campagna deve essere aggiornata per l'assegnazione tag [!DNL Marketo Measure].</p>
        <p>(Campo diagnostico utilizzato dall'elaborazione interna).</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CHIAVE_RAGGRUPPAMENTO</p>
      </td>
      <td>varchar</td>
      <td>Campo diagnostico, utilizzato per l’elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Oggetto o entità principale per questa tabella. In questo caso, "Campaign".</p>
      </td>
      <td>
        <p>Campaign</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TIPO_PROVIDER</p>
      </td>
      <td>varchar</td>
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
        <p>Il budget giornaliero impostato nella piattaforma di annunci per la campagna.</p>
      </td>
      <td>
        <p>0,0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>varchar</td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>varchar</td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUIRED</p>
      </td>
      <td>varchar</td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Modello di tracciamento aggiunto a livello di campagna per AdWords o Bing per l’assegnazione di tag alle pagine di destinazione.</p>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
      </td>
      <td>
        <p>-6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_FORMS {#biz-ad-forms}

Ad Forms importato da qualsiasi account Ad connesso.

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
       <td>ID</td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>ID dell’account annuncio da cui è stato importato il modulo annuncio.</p>
      </td>
      <td>
        <p>li.507063119</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’account annuncio da cui è stato importato il modulo annuncio.</p>
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
        <p>Stato eliminato dal sistema di origine. Impostate questa opzione su Eliminato se lo stato è Bozza, Archiviato o Annullato.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMO_IMPORTATO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data della prima importazione del record dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del modulo annuncio.</p>
      </td>
      <td>
        <p>NSPA Ebook LGF (maggio 2020)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Oggetto o entità principale per questa tabella. In questo caso, "AdForm".</p>
      </td>
      <td>
        <p>AdForm</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TIPO_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del provider dell’annuncio per il modulo dell’annuncio.</p>
      </td>
      <td>
        <p>LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DESCRIZIONE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Descrizione del modulo annuncio.</p>
      </td>
      <td>
        <p>Scopri come l’automazione intelligente può aumentare l’efficienza dei processi nelle applicazioni di rifinanziamento dei mutui ipotecari.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TITOLO</p>
      </td>
      <td>varchar</td>
      <td>Titolo del modulo annuncio.</td>
      <td>
        <p>È ora di automatizzare il processo di richiesta di rifinanziamento</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_URL</p>
      </td>
      <td>varchar</td>
      <td>URL di destinazione del modulo annuncio.</td>
      <td>
        <p>https://adobe.com/blog/refinancing-application-process/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DOMANDE</p>
      </td>
      <td>varchar</td>
      <td>Elenco di domande per il modulo annuncio.</td>
      <td>
        <p>Nome:Cognome:Indirizzo e-mail:Paese/Regione:Qualifica:Nome società</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STATO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Stato del modulo annuncio.</p>
      </td>
      <td>
        <p>inviato</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>SOURCE_ID</td>
      <td>varchar</td>
      <td>ID del Source da cui proviene il record.</td>
      <td>aw.3284209</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_GROUPS {#biz-ad-groups}

Gruppi di annunci importati da qualsiasi account di annunci connesso.

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
      <td>varchar</td>
      <td>L’ID del gruppo di annunci dal sistema di origine.</td>
      <td>
        <p>23105326115</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account annuncio da cui è stato importato il gruppo di annunci.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’account annuncio da cui è stato importato il gruppo di annunci.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non è presente alcun gruppo di annunci nella gerarchia degli annunci Doubleclick.</p>
      </td>
      <td>
        <p>nulle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_INSERZIONISTA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non è presente alcun gruppo di annunci nella gerarchia degli annunci Doubleclick.</p>
      </td>
      <td>
        <p>nulle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché questo è il record per il gruppo di annunci nella gerarchia.</p>
      </td>
      <td>
        <p>nulle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché questo è il record per il gruppo di annunci nella gerarchia.</p>
      </td>
      <td>
        <p>nulle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
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
        <p>Indica se l'account dell'annuncio è ancora attivo nel sistema di origine.</p>
      </td>
      <td>
        <p>vero</p>
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
        <p>Indica se l'account dell'annuncio è stato eliminato o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:14.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMO_IMPORTATO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data della prima importazione del record dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:14.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del gruppo di annunci.</p>
      </td>
      <td>
        <p>Attribuzione ricavi - Basata su conto</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEED_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se l'inserzionista deve essere aggiornato per l'assegnazione tag [!DNL Marketo Measure].</p>
        <p>(Campo diagnostico utilizzato dall'elaborazione interna).</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CHIAVE_RAGGRUPPAMENTO</p>
      </td>
      <td>varchar</td>
      <td>Campo diagnostico, utilizzato per l’elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Oggetto o entità principale per questa tabella. In questo caso, "AdGroup".</p>
      </td>
      <td>
        <p>AdGroup</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TIPO_PROVIDER</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>Il supporto su cui è in esecuzione il gruppo di annunci.</p>
      </td>
      <td>
        <p>Ricerca, Visualizzazione, YouTube_Search, YouTube_Watch</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>varchar</td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>varchar</td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUIRED</p>
      </td>
      <td>varchar</td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>varchar</td>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
      </td>
      <td>
        <p>-5594512713562690000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_PROVIDERS

<p>Fornitori di annunci da qualsiasi account annuncio collegato, inclusa una voce per i rapporti personali, se applicabile.</p>

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
      <td>varchar</td>
      <td>
        <p>Nome del provider dell’annuncio.</p>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
      </td>
      <td>
        <p>4783788151269206864</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ATTRIBUTION_TOUCHPOINTS {#biz-attribution-touchpoints}

<p>Punti di contatto di attribuzione acquirente, tutti i punti di contatto associati a un’opportunità.</p>
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
      <td>
        <p>Un ID univoco per il Buyer Attribution Touchpoint (BAT).</p>
      </td>
      <td>
        <p>BAT2_0060Z00000lFHtOQAW_</p>
        <p>0030Z00003K5bpKQAR_2017-06-20:01-05-20-6193330.0b5c5678807c</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>
        <p>04.0}53.000 09/01 2018:53:</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ID_OPPORTUNITÀ</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’opportunità a cui è attribuito l’BAT.</p>
      </td>
      <td>
        <p>0060Z00000lFHtOQAW</p>
      </td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>
        <p>ID del contatto associato all’BAT.</p>
      </td>
      <td>
        <p>0030Z00003K5bpKQAR</p>
      </td>
    </tr>
    <tr>
      <td>EMAIL</td>
      <td>varchar</td>
      <td>Indirizzo e-mail associato all’BAT.</td>
      <td>person@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account a cui viene attribuito l’BAT.</p>
      </td>
      <td>
        <p>0013100001otbIAAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_TOUCHPOINT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del punto di contatto utente che ha generato l’BAT.</p>
      </td>
      <td>
        <p>person@adobe.com_00v1B00003ZbWzHQAV</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DATA_PUNTO DI CONTATTO</p>
      </td>
      <td>timestamp_ntz</td>
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
      <td>ID del visitatore associato all’BAT.</td>
      <td>v_277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>MARKETING_TOUCH_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Tipo di attività, visita Web, modulo Web, chat Web, telefonata, campagna [CRM] o attività [CRM]. Nel sistema di gestione delle relazioni con i clienti è indicato come "Tipo di punto di contatto".</p>
      </td>
      <td>
        <p>Modulo web</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CANALE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il canale in cui rientra il punto di contatto, come definito nelle definizioni di canale personalizzate all'interno dell'app [!DNL Marketo Measure]. Nel sistema di gestione delle relazioni con i clienti, denominato "Canale di marketing - Percorso".</p>
      </td>
      <td>
        <p>Social.LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA 1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore del segmento per la prima categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</p>
      </td>
      <td>
        <p>ABC</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA 2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore del segmento per la seconda categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</p>
      </td>
      <td>
        <p>Sì</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA 3</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore del segmento per la terza categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</p>
      </td>
      <td>
        <p>PMI</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA4</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per la quarta categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td>
        <p>Nuove attività</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA5</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per la quinta categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA6</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per la sesta categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA7</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per la settima categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA8</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per l'ottava categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA9</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per la nona categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA10</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per la decima categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA11</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per l'11a categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA12</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per la dodicesima categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA13</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per la tredicesima categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA14</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per la quattordicesima categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA15</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per la quindicesima categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NOME_BROWSER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, il browser rilevato su cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>Chrome</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, la versione del browser rilevato su cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_PIATTAFORMA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, la piattaforma rilevata su cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>Mac</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, la versione rilevata della piattaforma su cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>10_12</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La prima pagina di destinazione della sessione che ha generato un punto di contatto. Nel sistema di gestione delle relazioni con i clienti è indicato come "Pagina di destinazione".</p>
      </td>
      <td>
        <p>http://www.adobe.com/blog/uncover- true-behind-cost-per-lead</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La prima pagina di destinazione della sessione che ha generato un punto di contatto. Una pagina di destinazione non elaborata conterrà tutti i parametri di query nell’URL. Nel sistema di gestione delle relazioni con i clienti è fatto riferimento a "Landing Page - Raw" (Pagina di destinazione - Non elaborato).</p>
      </td>
      <td>
        <p>http://www.adobe.com/blog/uncover-truth -behind-cost-per-lead?utm_content=27322869&amp;utm_ medium=social&amp;utm_source=linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>In genere, la pagina di destinazione esterna immediatamente prima che l’utente entri sul sito web. Nel sistema di gestione delle relazioni con i clienti è indicato come "Pagina di riferimento".</p>
      </td>
      <td>
        <p>https://www.linkedin.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>In genere, la pagina di destinazione esterna immediatamente prima che l’utente entri sul sito web. Una pagina di riferimento non elaborata può contenere parametri di query nell’URL. Nel sistema di gestione delle relazioni con i clienti, denominato "Pagina di provenienza - Raw".</p>
      </td>
      <td>
        <p>https://www.linkedin.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il primo modulo registrato in una sessione che ha generato un punto di contatto. Gli invii di moduli successivi non verranno visualizzati nella tabella Attribution_Touchpoints, ma nella tabella Form_Submits. Nel sistema di gestione delle relazioni con i clienti viene fatto riferimento a "URL modulo".</p>
      </td>
      <td>
        <p>http://info.adobe.com/intro-guide-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il primo modulo registrato in una sessione che ha generato un punto di contatto. Gli invii di moduli successivi non verranno visualizzati nella tabella Attribution_Touchpoints, ma nella tabella Form_Submits. Una pagina modulo non elaborata può contenere parametri di query nell’URL. Nel sistema di gestione delle relazioni con i clienti viene fatto riferimento a "URL modulo - Non elaborato".</p>
      </td>
      <td>
        <p>http://info.adobe.com/intro-guide-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di invio del modulo.</p>
      </td>
      <td>
        <p>2017-06-20 01:06:41.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITTÀ</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, la città rilevata in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>San Francisco</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGIONE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, l’area geografica rilevata in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>California</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAESE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, il paese rilevato in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>Stati Uniti</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIUM</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Utilizzato per definire il mezzo che ha determinato il punto di contatto. Questo può essere analizzato dall’URL da utm_medium. Oppure, se [!DNL Marketo Measure] è in grado di risolvere un annuncio, può trattarsi di valori quali "cpc" o "display".</p>
      </td>
      <td>
        <p>social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Utilizzato per definire l’origine che ha generato il punto di contatto. Questo può essere analizzato dall'URL da utm_source, in genere impostato come "Campagna CRM" se è stato sincronizzato dal sistema di gestione delle relazioni con i clienti oppure se [!DNL Marketo Measure] è in grado di risolvere un annuncio, potrebbe trattarsi di valori quali "Google AdWords" o "Facebook". Nel sistema di gestione delle relazioni con i clienti è indicato come "Touchpoint Source".</p>
      </td>
      <td>
        <p>linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore che l’utente ha immesso nel browser per cercare e che è finito sul sito web. A seconda delle parole chiave acquistate, questo potrebbe corrispondere o meno alle parole chiave acquistate dalla piattaforma di ricerca a pagamento.</p>
      </td>
      <td>
        <p>google [!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La piattaforma di annunci [!DNL Marketo Measure] è stata risolta da, in genere uno dei nostri partner di integrazione.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account dell’annuncio da cui l’annuncio è stato risolto.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_ACCOUNT</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’account dell’annuncio da cui l’annuncio è stato risolto.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell'inserzionista dall'account dell'annuncio da cui è stato risolto l'annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_INSERZIONISTA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell'inserzionista dall'account annuncio da cui è stato risolto l'annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del sito dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_SITO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del sito dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>blocco stradale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della campagna dall’account annuncio da cui è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029.317738075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_CAMPAGNA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della campagna dall’account annuncio da cui è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>Marketing Attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del gruppo di annunci dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale solo per Google Adwords.</p>
      </td>
      <td>
        <p>aw.6601259029.317738075.23105327435</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>Nome dell’annuncio dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>
        <p>Webinar Budget - barra laterale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del contenuto creativo dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>aw.6601259029.317738075.23105327435.182716179597</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_CREATIVO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’elemento creativo dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Attribuzione marketing B2B</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La prima riga del contenuto creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Scarica la Guida CMO</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La seconda riga del contenuto creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Scopri come l’attribuzione misura il ROI collegando le attività di marketing ai ricavi</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La pagina di destinazione in cui viene fatto clic dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>http://info.adobe.com/cmos-guide-to-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il nome URL descrittivo visualizzato nell’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>http://info.adobe.com/CMOs-Guide</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della parola chiave acquistata dall’acquisto di Paid Search, estratto dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>aw.6601259029.317738075.23105327435.4838421670</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della parola chiave acquistata dall’acquisto di Ricerca a pagamento, estratto dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca)</p>
      </td>
      <td>
        <p>"attribuzione marketing"</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Tipo di corrispondenza trovata tra la frase di ricerca e la parola chiave acquistata.</p>
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
        <p>Se questo punto di contatto viene considerato o meno come il primo contatto del percorso di opportunità.</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Se questo punto di contatto viene considerato o meno come il contatto di creazione del lead del percorso di opportunità.</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Se questo punto di contatto viene considerato o meno come il punto di contatto per la creazione di opportunità del percorso di opportunità.</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Se questo punto di contatto viene considerato o meno come il contatto chiuso del percorso di opportunità.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGES_TOUCHED</p>
      </td>
      <td>varchar</td>
      <td>Questo campo è stato dichiarato obsoleto. Utilizzare le tabelle Stage_Transitions per informazioni sull'area di visualizzazione.</td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se il punto di contatto ha o meno compilato un modulo durante la sessione.</p>
      </td>
      <td>
        <p>vero</p>
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
        <p>Se questo punto di contatto viene considerato o meno come il primo contatto di impression del percorso di opportunità</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMO_CLIC_PERCENTUALE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>La percentuale calcolata allocata a questo punto di contatto perché è un primo contatto (vedi Is_First_Touch).</p>
      </td>
      <td>
        <p>0,0000000000000000000</p>
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
        <p>La percentuale calcolata allocata a questo punto di contatto perché è un contatto per la creazione di lead (vedi Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>0,0000000000000000000</p>
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
        <p>Percentuale calcolata allocata a questo punto di contatto perché fa parte di un contatto a forma di U (consultate Is_First_Touch e Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>0,0000000000000000000</p>
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
        <p>Percentuale calcolata allocata a questo punto di contatto perché fa parte di un contatto a forma di w (consultate Is_First_Touch, Is_Lead_Creation_Touch e Is_Opp_Creation_Touch).</p>
      </td>
      <td>
        <p>0,0153374234214425</p>
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
        <p>Percentuale calcolata allocata a questo punto di contatto perché fa parte di un modello di percorso completo (consultate Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch).</p>
      </td>
      <td>
        <p>0,0143061513081193</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PERCENTUALE_MODELLO_PERSONALIZZATO</p>
      </td>
      <td>numero(22,19)</td>
      <td>La percentuale calcolata allocata a questo punto di contatto perché fa parte di un modello personalizzato (consultate Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch).</td>
      <td>0,0143061513081193</td>
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
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITÀ_CHIAVE_RIGA</p>
      </td>
      <td>
        <p>numero(38,0)</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CHIAVE_RIGA_SITO</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_ROW_KEY</p>
      </td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ATTRIBUTION_AI_TOUCHPOINTS {#biz-attribution-ai-touchpoints}

Dati generati dall’integrazione Attribution AI. Questi campi sono compilati solo per i clienti Marketo Measure Ultimate.

<table>
<thead>
  <tr>
    <th>Colonna</th>
    <th>Tipo di dati</th>
    <th>Descrizione</th>
    <th>Dati di esempio</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>CONVERSION_DATE</td>
    <td>Timestamp_ntz</td>
    <td>data della conversione</td>
    <td>01/01/2020 01 :01:00.000</td>
  </tr>
  <tr>
    <td>CONVERSION_NAME</td>
    <td>varchar</td>
    <td>nome dell’evento di conversione (come specificato dal cliente nell’impostazione dell’interfaccia utente)</td>
    <td> </td>
  </tr>
  <tr>
    <td>CONVERSION_ID</td>
    <td>varchar</td>
    <td>id per l’evento di conversione (si tratta del valore id univoco originale inviato con il record di dati dell’evento nel set di dati sorgente)</td>
    <td>0013100001b44aGAAQ</td>
  </tr>
  <tr>
    <td>CONVERSION_EVENT_ID</td>
    <td>varchar</td>
    <td>ID evento MM originale per l’evento di conversione 
    <br>corrisponde a un punto di contatto utente o a una transizione di fase</td>
    <td>00U0Z00000pCZmyUAG</td>
  </tr>
  <tr>
    <td>CONVERSION_ACCOUNT_ID</td>
    <td>varchar</td>
    <td>ID account MM originale per l’evento di conversione</td>
    <td>0013100001kpAZxAAM</td>
  </tr>
  <tr>
    <td>CONVERSION_OPPORTUNITY_ID</td>
    <td>varchar</td>
    <td>ID opportunità MM originale per l’evento di conversione</td>
    <td>0060Z00000lFHtOQAW</td>
  </tr>
  <tr>
    <td>CONVERSION_LEAD_ID</td>
    <td>varchar</td>
    <td>ID lead MM originale per l'evento di conversione <br> probabilmente nullo nella maggior parte dei casi</td>
    <td>00Q0Z000013dw4GUAQ</td>
  </tr>
  <tr>
    <td>CONVERSION_CONTACT_ID</td>
    <td>varchar</td>
    <td>ID contatto MM originale per l’evento di conversione
    <br> potrebbe essere nullo la maggior parte delle volte</td>
    <td>00331000032hMxRAAU</td>
  </tr>
  <tr>
    <td>CONVERSION_EVENT_TYPE</td>
    <td>varchar</td>
    <td>tipo di evento di conversione (b2b = conversione lead, b2c = conversione opportunità)</td>
    <td>b2b</td>
  </tr>
  <tr>
    <td>SCORE_DATE</td>
    <td>Timestamp_ntz</td>
    <td>data dell’ultimo punteggio dei punti di contatto</td>
    <td>01/01/2020 01 :01:00.000</td>
  </tr>
  <tr>
    <td>INFLUENZA_PERCENTUALE</td>
    <td>numero(38,35)</td>
    <td>la frazione della conversione di cui è responsabile ogni punto di contatto</td>
    <td>0,10</td>
  </tr>
  <tr>
    <td>INCREMENTAL_PERCENT</td>
    <td>numero(38,35)</td>
    <td>l’entità dell’impatto marginale causato direttamente da un punto di contatto</td>
    <td>0,25</td>
  </tr>
  <tr>
    <td>DATA_PUNTO DI CONTATTO</td>
    <td>Timestamp_ntz</td>
    <td>il punto di contatto o la data di transizione dell’area di visualizzazione</td>
    <td>01/01/2020 01 :01:00.000</td>
  </tr>
  <tr>
    <td>TOUCHPOINT_EVENT_ID</td>
    <td>varchar</td>
    <td>id dell’evento che ha generato il punto di contatto</td>
    <td>00U3100000VLUnEEAX</td>
  </tr>
  <tr>
    <td>TOUCHPOINT_OPPORTUNITY_ID</td>
    <td>varchar</td>
    <td>id dell’opportunità associata al punto di contatto</td>
    <td>0060Z00000lFHtOQAW</td>
  </tr>
  <tr>
    <td>TOUCHPOINT_ACCOUNT_ID</td>
    <td>varchar</td>
    <td>id dell’account associato al punto di contatto</td>
    <td>0013100001kpAZxAAM</td>
  </tr>
  <tr>
    <td>TOUCHPOINT_LEAD_ID</td>
    <td>varchar</td>
    <td>id del lead associato al punto di contatto</td>
    <td>00Q0Z000013dw4GUAQ</td>
  </tr>
  <tr>
    <td>TOUCHPOINT_CONTACT_ID</td>
    <td>varchar</td>
    <td>id del contatto associato al punto di contatto</td>
    <td>00331000032hMxRAAU</td>
  </tr>
  <tr>
    <td>COUNT_TO_CONVERSION</td>
    <td>numero(38,0)</td>
    <td>il rango o valore ordinale del punto di contatto nella catena che porta all’evento di conversione</td>
    <td>10000</td>
  </tr>
  <tr>
    <td>AAI_SOURCE_ID</td>
    <td>varchar</td>
    <td>chiave esterna per la tabella delle origini di ia per l’attribuzione</td>
    <td> </td>
  </tr>
  <tr>
    <td>_CREATED_DATE</td>
    <td>Timestamp_ntz</td>
    <td>data di creazione del record nel Snowflake</td>
    <td>01/01/2020 01 :01:00.000</td>
  </tr>
  <tr>
    <td>_MODIFIED_DATE</td>
    <td>Timestamp_ntz</td>
    <td>data dell'ultima modifica del record nel Snowflake</td>
    <td>01/01/2020 01 :01:00.000</td>
  </tr>
  <tr>
    <td>_DELETED_DATE</td>
    <td>Timestamp_ntz</td>
    <td>data in cui il record è stato eliminato nel Snowflake</td>
    <td>01/01/2020 01 :01:00.000</td>
  </tr>
</tbody>
</table>

### BIZ_CAMPAIGN_MEMBERS {#biz-campaign-members}

Membri della campagna importati dal sistema di origine. Questa tabella sarà vuota se la sincronizzazione di Campaign è disabilitata.

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
      <td>L’ID del membro della campagna dal sistema di origine.</td>
      <td>00v0Z00001VzdLQAT</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del membro della campagna, dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-31 20:49:54.000</p>
      </td>
    </tr>
    <tr>
      <td>DATA_CREAZIONE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>La data di creazione del membro della campagna, dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-31 20:49:54.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_TOUCH_POINT_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data e ora impostate dal cliente per sostituire la data della campagna e utilizzare questo valore per la data del punto di contatto.</p>
      </td>
      <td>
        <p>2018-08-30 18:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del lead a cui è associato il membro della campagna.</p>
      </td>
      <td>
        <p>00Q0Z000013dw4GUAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>E-mail del lead a cui è associato il membro della campagna.</p>
      </td>
      <td>persona@adobe.com</td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>
        <p>ID del contatto a cui è associato il membro della campagna.</p>
      </td>
      <td>
        <p>00331000032hMxRAAU</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Indirizzo e-mail del contatto a cui è associato il membro della campagna.</p>
      </td>
      <td>persona@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>STATO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Stato del membro della campagna, in genere impostato su Inviato o Risposto o su un altro valore personalizzato. Questo stato è associato a Campaign_Sync_Type per determinare per quali membri della campagna creare punti di contatto.</p>
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
        <p>Indica se il membro della campagna è stato contrassegnato come "Risposto" dal selettore di stato.</p>
      </td>
      <td>
        <p>vero</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DATA_PRIMA_RISPOSTA</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data della prima risposta del membro della campagna.</p>
      </td>
      <td>
        <p>2018-08-30 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_CAMPAGNA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della campagna correlata di cui fa parte il membro della campagna.</p>
      </td>
      <td>
        <p>Interviste CMO rapide</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ID_CAMPAGNA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della campagna correlata di cui fa parte il membro della campagna.</p>
      </td>
      <td>
        <p>7010Z000001TcKlQAK</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Tipo selezionato nella campagna correlata di cui fa parte il membro della campagna. Il Tipo viene utilizzato per mappare il Canale di marketing.</p>
      </td>
      <td>
        <p>Offline</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_SYNC_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Determina per quali membri della campagna creare punti di contatto. I valori possibili sono: Include_All, Include_Responded, Exclude_All.</p>
      </td>
      <td>
        <p>Includi_tutto</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SYNC_STATUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Campo di controllo, indica se per il lead è stato generato o meno un Buyer Touchpoint. Se non è stato creato alcun punto di contatto, viene indicato il motivo per cui non è stato qualificato.</p>
      </td>
      <td>
        <p>Nessun punto di contatto: data esterna al modello</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_SYNC_STATUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il campo Audit indica se per il contatto è stato generato o meno un Buyer Touchpoint. Se non è stato creato alcun punto di contatto, viene indicato il motivo per cui non è stato qualificato.</p>
      </td>
      <td>
        <p>Punto di contatto creato</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPP_SYNC_STATUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il campo Audit indica se per l’opportunità è stato generato o meno un Buyer Attribution Touchpoint. Se non è stato creato alcun punto di contatto, viene indicato il motivo per cui non è stato qualificato.</p>
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
        <p>Indica se il record viene considerato eliminato o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Proprietà personalizzate importate da [!DNL Marketo Measure] dal sistema di origine in formato JSON.</td>
      <td>{"Campaign_Type__c":"Cene","Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CHANNELS {#biz-channels}

Canali di marketing creati nell&#39;applicazione [!DNL Marketo Measure].

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
      <td>varchar</td>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
      </td>
      <td>
        <p>6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CONTACTS {#biz-contacts}

Contatti importati dal sistema di origine.

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
      <td>
        <p>ID del contatto dal sistema di origine.</p>
      </td>
      <td>
        <p>0030Z00003OzioeQAB</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell'ultima modifica del record Contatto dal sistema di origine.</p>
      </td>
      <td>
        <p>05/09/05/2018 :17:53.000</p>
      </td>
    </tr>
    <tr>
      <td>DATA_CREAZIONE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di creazione del record Contatto dal sistema di origine.</p>
      </td>
      <td>
        <p>05/09/2018 :17:51,000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Indirizzo e-mail del contatto, dal sistema di origine.</p>
      </td>
      <td>persona@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNTID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account correlato al contatto.</p>
      </td>
      <td>
        <p>0013100001b44aGAAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SOURCE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Source in cui è stato creato il lead.</p>
      </td>
      <td>
        <p>Pubblicità</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Fase corrente del contatto, riconosciuta come fase personalizzata che può essere creata nell'applicazione [!DNL Marketo Measure].</p>
      </td>
      <td>
        <p>Demo pianificata</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE_PREVIOUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Tutte le fasi precedenti per il contatto, riconosciute come fasi personalizzate che possono essere create nell'applicazione [!DNL Marketo Measure].</p>
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
        <p>Questa funzione è stata rimossa. Non utilizzare questa colonna.</p>
      </td>
      <td>
        <p>N/D</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L'ID cookie [!DNL Marketo Measure] utilizzato per compilare da un partner di integrazione per mappare un evento offline a una sessione Web. Requisito: Abilita tracciamento chiamate: True</p>
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
        <p>Indica se il record viene eliminato o meno nel sistema di origine.</p>
      </td>
      <td>falso</td>
    </tr>
    <tr>
      <td>IS_DUPLICATE</td>
      <td>booleano</td>
      <td>Utilizzato per deduplicare i record se è impostata un’integrazione CRM e Marketo. Se sono presenti duplicati, il contatto Marketo viene contrassegnato come true.</td>
      <td>falso</td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Indica se il record proviene da un’integrazione CRM o Marketo.</td>
      <td>Crm</td>
    </tr>
    <tr>
      <td>OTHER_SYSTEM_ID</td>
      <td>varchar</td>
      <td>Mappa una persona da un’integrazione Marketo con un contatto da un’integrazione CRM. Se esiste sia un’integrazione CRM che Marketo, il valore è l’ID corrispondente.</td>
      <td>1234/00Q0Z00001OohgTUAR</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Proprietà personalizzate importate da [!DNL Marketo Measure] dal sistema di origine in formato JSON.</td>
      <td>{"Contact_Type__c":"CMO", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>numero(38,0)</td>
      <td>Chiave esterna per la vista Biz_Facts.</td>
      <td>3263982503087870000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td><b>∗</b> JOB_TITLE</td>
      <td>varchar</td>
      <td>Qualifica del contatto.</td>
      <td>Amministratore delegato, Vicepresidente</td>
    </tr>
  </tbody>
</table>
<p>
<b>∗</b> <i>Disponibile solo in Marketo Measure Ultimate</i>
<p>

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
      <td>numero(38,0)</td>
      <td>ID univoco del record.</td>
      <td>-5942345438803054604</td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>numero(38,0)</td>
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
      <td>DATA_INIZIALE</td>
      <td>timestamp_ntz</td>
      <td>Data di inizio del tasso di conversione.</td>
      <td>00:00:00.000 01 11/01/2018</td>
    </tr>
    <tr>
      <td>END_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di inizio successiva per il tasso di conversione. La data di fine del tasso di conversione è data_finale meno 1 giorno.</td>
      <td>00:00:00.000 00 09/01/2018</td>
    </tr>
    <tr>
      <td>CONVERSION_RATE</td>
      <td>numero(38,0)</td>
      <td>Tasso utilizzato per convertire la valuta nella valuta aziendale.</td>
      <td>0,76728300</td>
    </tr>
    <tr>
      <td>IS_CURRENT</td>
      <td>booleano</td>
      <td>La semantica di questo campo è stata danneggiata. Non utilizzare.</td>
      <td>vero</td>
    </tr>
    <tr>
      <td>DATA_CREAZIONE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel sistema di origine.</td>
      <td>2019-03-30 00:54:50,000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell'ultima modifica del record nel sistema di origine.</td>
      <td>2019-03-30 00:54:50,000</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>booleano</td>
      <td>Indica se il record viene considerato eliminato o meno nel sistema di origine.</td>
      <td>falso</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_COST {#biz-costs}

Dati sui costi importati da account annuncio collegati o da spese di marketing dichiarate autonomamente.

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
      <td>ID univoco del record Costo.</td>
      <td>aw.6601259029.285114995.21703163075.[Visualizzazione AdWords]_2018-09-06</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica del record.</td>
      <td>2018-09-06 12:22:45.000</td>
    </tr>
    <tr>
      <td>COST_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il costo è stato sostenuto (o attribuito a).</td>
      <td>00:00:00.000 00 09/06/2018</td>
    </tr>
    <tr>
      <td>SORGENTE</td>
      <td>varchar</td>
      <td>Source del costo riportato.</td>
      <td>[Visualizzazione AdWords]</td>
    </tr>
    <tr>
      <td>COST_IN_MICRO</td>
      <td>numero(38,0)</td>
      <td>Costo in milioni. L’utente dovrà dividere il valore per 1000000.</td>
      <td>1410000</td>
    </tr>
    <tr>
      <td>CLIC</td>
      <td>numero(38,0)</td>
      <td>Numero di clic segnalati per il gruppo per il giorno.</td>
      <td>4</td>
    </tr>
    <tr>
      <td>IMPRESSION</td>
      <td>numero(38,0)</td>
      <td>Numero di impression segnalate per il gruppo per la giornata.</td>
      <td>4187</td>
    </tr>
    <tr>
      <td>ESTIMATED_TOTAL_POSSIBLE_IMPRESSIONS</td>
      <td>numero(38,0)</td>
      <td>Numero totale di impression stimato da DCM per il gruppo per il giorno.</td>
      <td>5024</td>
    </tr>
    <tr>
      <td>AD_PROVIDER</td>
      <td>varchar</td>
      <td>Provider per cui è stato estratto il costo.</td>
      <td>Google</td>
    </tr>
    <tr>
      <td>CHANNEL_UNIQUE_ID</td>
      <td>varchar</td>
      <td>ID del canale di marketing, creato da [!DNL Marketo Measure].</td>
      <td>Display.Google</td>
    </tr>
    <tr>
      <td>NOME_CANALE</td>
      <td>varchar</td>
      <td>Nome del canale di marketing, creato dal cliente nell'app [!DNL Marketo Measure].</td>
      <td>Display.Google</td>
    </tr>
    <tr>
      <td>CHANNEL_IS_AGGREGATABLE_COST</td>
      <td>booleano</td>
      <td>Indica se la riga contiene un costo che può essere sommato per canale. (ovvero, per ottenere il Costo canale, sommare le righe in cui questa colonna è uguale a true).</td>
      <td>falso</td>
    </tr>
    <tr>
      <td>ADVERTISER_UNIQUE_ID</td>
      <td>varchar</td>
      <td>ID dell’inserzionista estratto dalla connessione dell’annuncio, in particolare per le connessioni Doubleclick.</td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>NOME_INSERZIONISTA</td>
      <td>varchar</td>
      <td>Nome dell’inserzionista estratto dalla connessione dell’annuncio, in particolare per le connessioni Doubleclick.</td>
      <td>[!DNL Marketo Measure] Marketing analytics</td>
    </tr>
    <tr>
      <td>ADVERTISER_IS_AGGREGATABLE_COST</td>
      <td>booleano</td>
      <td>Indica se la riga contiene un costo che può essere riassunto dall'inserzionista. (ovvero, per ottenere il costo dell’inserzionista, somma le righe in cui questa colonna è uguale a true).</td>
      <td>falso</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account annuncio estratto dalla connessione dell’annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_ACCOUNT</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’account annuncio estratto dalla connessione dell’annuncio.</p>
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
        <p>Indica se la riga contiene un costo che può essere sommato per conto. (ovvero, per ottenere il costo del conto, sommare le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della campagna estratto dalla connessione dell’annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_CAMPAGNA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della campagna estratto dalla connessione dell’annuncio.</p>
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
        <p>Indica se la riga contiene un costo che può essere riepilogato da Campaign. (ovvero, per ottenere il costo di Campaign, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>vero</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del gruppo di annunci estratto dalla connessione dell’annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995.21703163075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del gruppo di annunci estratto dalla connessione dell’annuncio.</p>
      </td>
      <td>
        <p>Software di gestione attribuzione | Frase</p>
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
        <p>Indica se la riga contiene un costo che può essere sommato dal gruppo di annunci. (ovvero, per ottenere Ad Group Cost, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’annuncio estratto dalla connessione dell’annuncio.</p>
      </td>
      <td>
        <p>dc.6114.9131003.24149929.467969200</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’annuncio estratto dalla connessione dell’annuncio.</p>
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
        <p>Indica se la riga contiene un costo che può essere sommato dall’annuncio. (ovvero, per ottenere Ad Cost, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del contenuto creativo estratto dalla connessione dell’annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995.51749608028.266050115160</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_CREATIVO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del contenuto creativo estratto dalla connessione dell’annuncio.</p>
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
        <p>Indica se la riga contiene un costo che può essere riassunto da Creative. (ovvero, per ottenere il costo creativo, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della parola chiave prelevata dalla connessione dell’annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029.669328935.39419128772.99608705795</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della parola chiave estratta dalla connessione dell’annuncio.</p>
      </td>
      <td>
        <p>attribuzione marketing sfdc</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAROLA CHIAVE IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene un costo che può essere sommato per parola chiave. (ovvero, per ottenere il costo delle parole chiave, sommare le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del posizionamento estratto dalla connessione dell’annuncio.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del posizionamento estratto dalla connessione dell’annuncio.</p>
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
        <p>Indica se la riga contiene un costo che può essere riepilogato in base al posizionamento. (ovvero, per ottenere il costo di posizionamento, sommare le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del sito estratto dalla connessione dell’annuncio.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_SITO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del sito estratto dalla connessione dell’annuncio.</p>
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
        <p>Indica se la riga contiene un costo che può essere riepilogato in base al sito. (ovvero per ottenere il costo del sito, sommare le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Indica se il record viene considerato eliminato o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>falso</p>
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
      <td>ID del Source da cui proviene il record.</td>
      <td>aw.3284209</td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>numero(38,0)</td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
      </td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ROW_KEY</p>
      </td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CHIAVE_RIGA_SITO</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>numero(38,0)</td>
      <td>Valore ID della valuta per il record.</td>
      <td>
        <p>-3253183181619994799</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CREATIVES {#biz-creatives}

Creative importate da qualsiasi account annuncio collegato.

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
      <td>
        <p>Un ID univoco per la creatività.</p>
      </td>
      <td>
        <p>ba.3284209.132855866.4556709270.10426699711</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td>ID creativo dal sistema di origine.</td>
      <td>
        <p>10426699711</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account annuncio da cui è stata importata la creatività.</p>
      </td>
      <td>fb.106851586409075</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’account annuncio da cui è stata importata la creatività.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’inserzionista per il settore creativo, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_INSERZIONISTA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell'inserzionista per la creatività, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del gruppo di annunci per la creatività.</p>
      </td>
      <td>fb.106851586409075.6052044288804.6052044290004</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del gruppo di annunci per la creatività.</p>
      </td>
      <td>Set di annunci per l’annuncio B</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della campagna per la creatività.</p>
      </td>
      <td>
        <p>ba.3284209.132855866</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della campagna per la creatività.</p>
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
        <p>Indica se Creative è ancora attivo nel sistema di origine.</p>
      </td>
      <td>
        <p>vero</p>
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
        <p>Indica se la creatività è stata eliminata o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:25.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMO_IMPORTATO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data della prima importazione del record dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:25.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della creatività, dal sistema di origine.</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEED_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se il componente Creative deve essere aggiornato per l'assegnazione tag [!DNL Marketo Measure].</p>
        <p>(Campo diagnostico utilizzato dall'elaborazione interna).</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CHIAVE_RAGGRUPPAMENTO</p>
      </td>
      <td>varchar</td>
      <td>Campo diagnostico, per elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Oggetto o entità principale per questa tabella. In questo caso, "Creative".</p>
      </td>
      <td>
        <p>Creativo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TIPO_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del provider di annunci per il contenuto creativo.</p>
      </td>
      <td>
        <p>BingAds</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La versione corrente dell’URL, inclusi tutti i tag.</p>
        <p>(Campo diagnostico, per elaborazione interna).</p>
      </td>
      <td>
        <p>cdn.adobe.com/redir?lp=http%3a%2f%2fwww.pipelinemarketing.com%2f&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}&amp;utm_content={adid}&amp;utm_term={keyword}&amp;utm_campaign=PipelineMarketing.com&amp;utm_source=bing&amp;utm_medium=cpc</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_DISPLAY</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L’URL abbreviato e intuitivo visualizzato sul contenuto creativo.</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Valore precedente per URL_CURRENT.</p>
        <p>(Campo diagnostico, per elaborazione interna).</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_RICHIESTO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Specifica l'URL con i parametri [!DNL Marketo Measure].</p>
        <p>(Campo diagnostico, per elaborazione interna).</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_ABBREVIATO</p>
      </td>
      <td>varchar</td>
      <td>L’URL abbreviato e intuitivo visualizzato sul contenuto creativo. (Utilizzato solo per LinkedIn Ads).</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Tipo di elemento creativo, che può essere Testo o Visualizzazione</p>
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
        <p>Indica se la creatività utilizza o meno URL aggiornati.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TITOLO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La linea superiore (titolo) della creatività</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DESCRIPTION_LINE_1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La copia dalla prima riga del contenuto</p>
      </td>
      <td>
        <p>Connettiti Ed Impara Dai Professionisti Di Marketing B2B Basati Sui Ricavi. Iscriviti alla community.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DESCRIPTION_LINE_2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La copia dalla seconda riga del contenuto creativo</p>
      </td>
      <td>
        <p>Hai Utilizzato Analytics? Lasciate una recensione oggi!</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>varchar</td>
      <td>Campo di diagnostica, per elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>varchar</td>
      <td>Campo di diagnostica, per elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUIRED</p>
      </td>
      <td>varchar</td>
      <td>Campo di diagnostica, per elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Campo di diagnostica, per elaborazione interna.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SHARE_URN</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID condivisione. (Utilizzato solo per LinkedIn Ads).</p>
      </td>
      <td>
        <p>urn:li:condivisione:6376987561897848832</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>numero(38,0)</p>
      </td>
      <td>Chiave esterna per la vista Biz_Facts.</td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CRM_EVENTS {#biz-crm-events}

Eventi importati dal sistema di origine. Questa tabella sarà vuota se la sincronizzazione attività è disabilitata.

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
      <td>
        <p>L’ID evento dal sistema di origine.</p>
      </td>
      <td>
        <p>00U3100000VLUnEEAX</p>
      </td>
    </tr>
    <tr>
      <td>DATA_CREAZIONE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di creazione dell'evento dal sistema di origine.</p>
      </td>
      <td>
        <p>2016-12-12 19:32:53.000</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell'ultima modifica apportata all'evento dal sistema di origine.</p>
      </td>
      <td>
        <p>08.0}51.000 09/09/2018:39:</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>E-mail per il lead associato all’evento.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>
        <p>ID del contatto associato all’evento.</p>
      </td>
      <td>
        <p>0030Z00003OyjbOQAR</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>E-mail per il contatto associato all’evento.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L'ID cookie [!DNL Marketo Measure] utilizzato per compilare da un partner di integrazione per mappare un evento offline a una sessione Web. Requisito: Abilita tracciamento chiamate: True</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TIPO_ATTIVITÀ</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del tipo di attività, dal sistema di origine.</p>
      </td>
      <td>
        <p>E-mail</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DATA_INIZIO_EVENTO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di inizio dell’evento, una delle opzioni utilizzate per determinare la data del punto di contatto.</p>
      </td>
      <td>
        <p>2016-12-16 19:30:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DATA_FINE_EVENTO</p>
      </td>
      <td>timestamp_ntz</td>
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
      <td>Indica se il record viene considerato eliminato o meno nel sistema di origine.</td>
      <td>
        <p>Falso</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Proprietà personalizzate importate da [!DNL Marketo Measure] dal sistema di origine in formato JSON.</td>
      <td>{"Contact_Type__c":"CMO","Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CRM_TASKS {#biz-crm-tasks}

Attività importate dal sistema di origine. Questa tabella viene compilata se è abilitato il tracciamento delle chiamate o la sincronizzazione delle attività.

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
      <td>
        <p>ID attività dal sistema di origine.</p>
      </td>
      <td>
        <p>00T0Z00004Rf62rUAB</p>
      </td>
    </tr>
    <tr>
      <td>DATA_CREAZIONE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di creazione dell'attività, dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-27 18:30:25.000</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell'ultima modifica apportata all'attività dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-27 18:31:53.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>E-mail per il lead associato all’attività.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>
        <p>ID del contatto associato all’attività.</p>
      </td>
      <td>
        <p>00331000038uGfhAAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>E-mail per il contatto associato all’attività.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L'ID cookie [!DNL Marketo Measure] utilizzato per compilare da un partner di integrazione per mappare un evento offline a una sessione Web. Requisito: Abilita tracciamento chiamate: True</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TIPO_ATTIVITÀ</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del tipo di attività, dal sistema di origine.</p>
      </td>
      <td>
        <p>Chiamata</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DATA_ATTIVITÀ</p>
      </td>
      <td>timestamp_ntz</td>
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
      <td>Indica se il record viene considerato eliminato o meno nel sistema di origine.</td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Proprietà personalizzate importate da [!DNL Marketo Measure] dal sistema di origine in formato JSON.</td>
      <td>{"Contact_Type__c":"CMO", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_VALUTE {#biz-currencies}

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
       <td>ID</td>
      <td>numero(38,0)</td>
      <td>Un ID univoco per il record Valuta.</td>
      <td>139474809945095870</td>
    </tr>
    <tr>
      <td>CODICE_ISO</td>
      <td>varchar</td>
      <td>Codice ISO per la valuta.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>IS_CORPORATE</td>
      <td>booleano</td>
      <td>Indica se la valuta è la valuta aziendale.</td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>IS_ENABLED</td>
      <td>booleano</td>
      <td>Indica se la valuta è abilitata nel sistema di origine.</td>
      <td>falso</td>
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
      <td>DATA_CREAZIONE</td>
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
      <td>numero(38,0)</td>
      <td>Codice numerico standard ISO.</td>
      <td>048</td>
    </tr>
    <tr>
      <td>ESPONENTE</td>
      <td>numero(38,0)</td>
      <td>Il numero di cifre decimali tra l'unità di valuta definita più piccola e un'intera unità di valuta.</td>
      <td>2</td>
    </tr>
    <tr>
      <td>NOME</td>
      <td>varchar</td>
      <td>Nome della valuta.</td>
      <td>Pesos (Argentina)</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CUSTOMER_AB_TESTS {#biz-customer-ab-tests}

Test AB registrati. Questa tabella sarà vuota se i test AB non sono abilitati.

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
        <p>VISITOR_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il primo ID cookie dell’ID visitatore correlato.</p>
      </td>
      <td>v_36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID cookie registrato al momento della registrazione dell’evento.</p>
      </td>
      <td>36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>DATA_EVENTO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di registrazione della chat.</p>
      </td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica del record.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>INDIRIZZO_IP</td>
      <td>varchar</td>
      <td>
        <p>L’indirizzo IP registrato al momento della registrazione dell’esperimento.</p>
      </td>
      <td>192.0.2.1</td>
    </tr>
    <tr>
      <td>
        <p>ID_ESPERIMENTO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’esperimento estratto dalla piattaforma di test AB.</p>
      </td>
      <td>123</td>
    </tr>
    <tr>
      <td>
        <p>NOME_ESPERIMENTO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’esperimento estratto dalla piattaforma di test AB.</p>
      </td>
      <td>Esperimento A</td>
    </tr>
    <tr>
      <td>
        <p>VARIATION_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della variante dell’esperimento estratto dalla piattaforma di test AB.</p>
      </td>
      <td>456</td>
    </tr>
    <tr>
      <td>
        <p>NOME_VARIANTE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il nome della variante dell’esperimento estratto dalla piattaforma di test AB.</p>
      </td>
      <td>Prova blu</td>
    </tr>
    <tr>
      <td>
        <p>ABTEST_USER_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’utente a cui è stato distribuito l’esperimento estratto dalla piattaforma di test AB.</p>
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
        <p>Indica se il record è stato eliminato o meno, utilizzato per la diagnostica e il controllo.</p>
      </td>
      <td>falso</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CUSTOMER_EVENTS {#biz-customer-events}

Eventi web registrati tramite eventi personalizzati in JavaScript. Questa tabella sarà vuota se [!DNL Marketo Measure] eventi non sono abilitati.

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
        <p>VISITOR_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il primo ID cookie dell’ID visitatore correlato.</p>
      </td>
      <td>v_36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L’ID cookie registrato al momento dell’attivazione dell’evento da JavaScript personalizzato.</p>
      </td>
      <td>36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>DATA_EVENTO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data in cui l'evento è stato attivato dal codice JavaScript personalizzato.</p>
      </td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Ultima data di modifica del record.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>
        <p>INDIRIZZO_IP</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L'indirizzo IP registrato al momento dell'attivazione dell'evento da JavaScript personalizzato.</p>
      </td>
      <td>192.0.2.1</td>
    </tr>
    <tr>
      <td>
        <p>CHIAVE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome assegnato all'evento attivato dal codice JavaScript personalizzato.</p>
      </td>
      <td>Visualizzazione video</td>
    </tr>
    <tr>
      <td>
        <p>VALORE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore dato all'evento che è stato attivato dal codice JavaScript personalizzato.</p>
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
        <p>Indica se il record è stato eliminato o meno, utilizzato per la diagnostica e il controllo.</p>
      </td>
      <td>falso</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CUSTOM_LANDING_PAGES {#biz-custom-landing-pages}

Pagine di destinazione scaricate da qualsiasi account annuncio collegato.

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
      <td>
        <p>ID univoco del record.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>ID dell’account annuncio da cui è stata importata la pagina di destinazione.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>Nome dell’account annuncio da cui è stata importata la pagina di destinazione</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’inserzionista per la pagina di destinazione, in particolare per Doubleclick.</p>
      </td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>
        <p>NOME_INSERZIONISTA</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>ID del gruppo di annunci per la pagina di destinazione.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del gruppo di annunci per la pagina di destinazione.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della campagna per la pagina di destinazione.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
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
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica della riga</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>PRIMO_IMPORTATO</p>
      </td>
      <td>timestamp_ntz</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NEED_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CHIAVE_RAGGRUPPAMENTO</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TIPO_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_EMAIL_TO_VISITOR_IDS {#biz-email-to-visitor-ids}

Tabella di mappatura per indirizzi e-mail e ID visitatore.

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
      <td>ID univoco del record.</td>
      <td>
        <p>0013800001MMPPiAAP_person@adobe.com|2022-01-05 17:22:13.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>Il primo cookie del relativo ID visitatore</p>
      </td>
      <td>
        <p>v_36ec805b4db344d6e92c972c86aee34a</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica della riga</p>
      </td>
      <td>
        <p>2018-08-14 23:55:03.000</p>
      </td>
    </tr>
    <tr>
      <td>DATA_CREAZIONE</td>
      <td>timestamp_ntz</td>
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
        <p>Indica se il record viene considerato eliminato o meno, utilizzato per la diagnostica e il controllo.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>IS_IGNORA</td>
      <td>booleano</td>
      <td>Indica se l’e-mail o l’ID visitatore sono considerati rumori o spam, utilizzati per l’elaborazione interna.</td>
      <td>falso</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_FACTS {#biz-facts}

Unisce impressioni, visualizzazioni di pagina, visite, invii di moduli, punti di contatto degli utenti, punti di contatto (BT), punti di contatto di attribuzione (BAT) e dati sui costi. Utilizzato internamente per supportare il reporting [!DNL Marketo Measure].

>[!IMPORTANT]
>
>Marketo Measure renderà obsoleta questa tabella a metà del 2024. Se desideri crearlo, esegui [questa query SQL](/help/marketo-measure-data-warehouse/assets/BIZ_FACTS.sql).

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
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Costi.</td>
      <td>2672629811884560039</td>
    </tr>
    <tr>
      <td>TASTO_ATP</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Punti di contatto di attribuzione.</td>
      <td>2672629811884560039</td>
    </tr>
    <tr>
      <td>TP_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join delle tabelle Punti di contatto o Punti di contatto utente.</td>
      <td>5028390208679093800</td>
    </tr>
    <tr>
      <td>PAGE_VIEW_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Visualizzazioni pagina.</td>
      <td>-8044063242541720607</td>
    </tr>
    <tr>
      <td>SESSION_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Sessioni.</td>
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
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Invii modulo.</td>
      <td>-8659572802702769670</td>
    </tr>
    <tr>
      <td>IMPRESSION_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per unire alla tabella Impression.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Url.</td>
      <td>4079876040770132443</td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Url.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Url.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>AD_PROVIDER_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Provider di annunci.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>
        <p>CHIAVE_CANALE</p>
      </td>
      <td>
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per l'unione alla tabella Canali.</p>
      </td>
      <td>
        <p>-1921844114032355934</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CHIAVE_CAMPAGNA</p>
      </td>
      <td>
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per partecipare alla tabella Campagne pubblicitarie.</p>
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
        <p>numero(38,0)</p>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per eseguire il join alla tabella Ads.</p>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per eseguire il join alla tabella Gruppi di annunci.</p>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per l’unione alla tabella Creatives.</p>
      </td>
      <td>
        <p>-2333871387956621113</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CHIAVE_SITO</p>
      </td>
      <td>
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per eseguire il join alla tabella Sites.</p>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per l’unione alla tabella Advertisers.</p>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per eseguire il join alla tabella Account annuncio.</p>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Utilizzato per eseguire il join alla tabella Posizionamenti.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>CATEGORY_01_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_02_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_03_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Segmenti.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_04_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_05_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_06_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Segmenti.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_07_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_08_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_09_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Segmenti.</td>
      <td>2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_10_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_11_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_12_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Segmenti.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_13_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_14_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_15_KEY</td>
      <td>numero(38,0)</td>
      <td>Utilizzato per eseguire il join alla tabella Segmenti.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>TIPO</td>
      <td>numero(38,0)</td>
      <td>Indica il tipo di fatto della riga. 1 = Buyer Attribution Touchpoint 2 = Costo 3 = Buyer Touchpoint 4 = Punto Di Contatto Utente 5 = Visualizzazione Pagina 6 = Sessione 7 = Invio Modulo 8 = Impression</td>
      <td>3</td>
    </tr>
    <tr>
      <td>DATA</td>
      <td>data</td>
      <td>Data in cui si è verificato l’evento.</td>
      <td>28/08/2018</td>
    </tr>
    <tr>
      <td>TIMESTAMP</td>
      <td>timestamp_ntz</td>
      <td>Data e ora in cui si è verificato l’evento.</td>
      <td>2018-08-28 19:39:15.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
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
        <p>numero(38,0)</p>
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
        <p>IMPRESSION</p>
      </td>
      <td>
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Numero di impression segnalate per il gruppo per la giornata.</p>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Numero di clic segnalati per il gruppo per il giorno.</p>
      </td>
      <td>4</td>
    </tr>
    <tr>
      <td>
        <p>PRIMO_CLIC_PERCENTUALE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>La percentuale calcolata allocata a questo punto di contatto perché è un primo contatto.</p>
      </td>
      <td>0,0000000000000000000</td>
    </tr>
    <tr>
      <td>
        <p>LAST_ANON_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>La percentuale calcolata allocata a questo punto di contatto perché è un contatto per la creazione di lead.</p>
      </td>
      <td>100,0000000000000000000</td>
    </tr>
    <tr>
      <td>
        <p>U_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>La percentuale calcolata che viene allocata a questo punto di contatto perché fa parte di un contatto a forma di U.</p>
      </td>
      <td>
        <p>100,0000000000000000000</p>
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
        <p>La percentuale calcolata che viene allocata a questo punto di contatto perché fa parte di un contatto a forma di w.</p>
      </td>
      <td>
        <p>0,0000000000000000000</p>
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
        <p>La percentuale calcolata che viene allocata a questo punto di contatto perché fa parte di un modello a percorso completo.</p>
      </td>
      <td>
        <p>0,0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PERCENTUALE_MODELLO_PERSONALIZZATO</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>La percentuale calcolata che viene allocata a questo punto di contatto perché fa parte di un modello personalizzato.</p>
      </td>
      <td>
        <p>0,0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>QUANTITÀ</p>
      </td>
      <td>
        <p>numero(38,8)</p>
      </td>
      <td>
        <p>Quantità dell’opportunità dal sistema di origine.</p>
      </td>
      <td>
        <p>42000,00000000</p>
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
        <p>Indica se l’opportunità è stata spostata in una fase classificata come vinta.</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Indica se l’opportunità è stata spostata in una fase classificata come chiusa.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ID_OPPORTUNITÀ</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’opportunità dal sistema di origine.</p>
      </td>
      <td>
        <p>0060Z00000nFEfEQAW</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPP_CREATED_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di creazione dell’opportunità dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-31 15:45:47.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPP_CLOSE_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di chiusura dell’opportunità dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-12-31 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_CREATED_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di creazione del record Contatto dal sistema di origine.</p>
      </td>
      <td>2017-04-28 00:21:52.000</td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>
        <p>ID contatto dal sistema di origine.</p>
      </td>
      <td>
        <p>0030Z00003ORVJmQAP</p>
      </td>
    </tr>
    <tr>
      <td>EMAIL</td>
      <td>varchar</td>
      <td>Indirizzo e-mail del record.</td>
      <td>personb@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>LEAD_CREATED_DATE</p>
      </td>
      <td>timestamp_ntz</td>
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
      <td>varchar</td>
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
        <p>Indica se la riga contiene un costo che può essere sommato dall’annuncio. (ovvero, per ottenere Ad Cost, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>falso</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_ADVERTISER</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene un costo che può essere riassunto dall'inserzionista. (ovvero, per ottenere il costo dell’inserzionista, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>vero</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_AD_ACCOUNT</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene un costo che può essere sommato per conto. (ovvero, per ottenere il costo del conto, sommare le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Indica se la riga contiene un costo che può essere sommato dal gruppo di annunci. (ovvero, per ottenere Ad Group Cost, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Indica se la riga contiene un costo che può essere riepilogato da Campaign. (ovvero, per ottenere il costo di Campaign, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>vero</p>
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
        <p>Indica se la riga contiene un costo che può essere sommato per canale. (ovvero, per ottenere il Costo canale, sommare le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>falso</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CREATIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene un costo che può essere riassunto da Creative. (ovvero, per ottenere il costo creativo, somma le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAROLA_CHIAVE_COSTO_AGGREGABILE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la riga contiene un costo che può essere sommato per parola chiave. (ovvero, per ottenere il costo delle parole chiave, sommare le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Indica se la riga contiene un costo che può essere riepilogato in base al posizionamento. (ovvero, per ottenere il costo di posizionamento, sommare le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Indica se la riga contiene un costo che può essere riepilogato in base al sito. (ovvero per ottenere il costo del sito, sommare le righe in cui questa colonna è uguale a true).</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Indica se il record è stato eliminato o meno, utilizzato come audit trail.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>numero(38,0)</td>
      <td>Valore ID della valuta per il record.</td>
      <td>-3253183181619994799</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_FORM_SUBMITS {#biz-forms-submits}

Invii di moduli acquisiti.

<table>
  <tbody>
    <tr>
      <th>
        Colonna
      </th>
      <th>Tipo di dati</th>
      <th>Descrizione</th>
      <th>Dati di esempio</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>L’ID cookie registrato al momento dell’invio del modulo.</p>
      </td>
      <td>
        <p>9bc63c34482f4de8c2e3b9d8d9f0df56</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il primo ID cookie dell’ID visitatore correlato. Se il record è contrassegnato come is_duplicated = true, questo campo sarà null.</p>
      </td>
      <td>
        <p>v_9bc63c34482f4de8c2e3b9d8d9f0df56</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L’ID sessione registrato al momento dell’invio del modulo. Se il record è contrassegnato come is_duplicated = true, questo campo sarà null.</p>
      </td>
      <td>
        <p>2018-08-06:01-35-24-1231230.9bc63c34482f</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DATA_EVENTO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di invio del modulo.</p>
      </td>
      <td>
        <p>2018-08-06 01:35:21.000</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-07 23:09:52.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>URL in cui è stato inviato il modulo, inclusi eventuali parametri di query.</p>
      </td>
      <td>
        <p>https://info.adobe.com/webinar-marketo-measure-impact?utm_source=partner&amp;mkt_tok=eyJpIjoiTnpBeE1EVml PV0UyWlRObSIsInQiOiI3MEFIek04ZVJiWm9renc1Z29RXC9kXC92YkxycFRYclE0MVhOaH Nwdml3YTZBZDdPdXh4Q0RmcnBJWXhwZTF1Z0RbXlDVmxJNzIwNkh L</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>INDIRIZZO_IP</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L'indirizzo IP registrato al momento dell'invio del modulo.</p>
      </td>
      <td>
        <p>174 127 184 158</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TIPO</p>
      </td>
      <td>varchar</td>
      <td>Indica il tipo di evento.</td>
      <td>
        <p>FormSubmit</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_AGENT_STRING</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>Indica l'ordine in cui si è verificata la visualizzazione pagina nella sessione.</td>
      <td>
        <p>4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_RANDOM</p>
      </td>
      <td>varchar</td>
      <td>Utilizzato per l’audit e l’elaborazione interna.</td>
      <td>
        <p>20042b6b7af44512b43f6244d86faf4c</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Indica se il record è considerato un duplicato.</td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Utilizzato per l’elaborazione interna.</td>
      <td>
        <p>vero</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Indirizzo e-mail fornito nel modulo, acquisito da JavaScript.</p>
      </td>
      <td>
        <p>personc@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TIPO_MODULO</p>
      </td>
      <td>varchar</td>
      <td>Indica il tipo di modulo inviato.</td>
      <td>
        <p>Chat</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_SOURCE</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
      </td>
      <td>
        <p>-6255315750913680000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td>Chiave esterna della tabella URL.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_IMPRESSION {#biz-impressions}

Impression sparate e registrate. Questa tabella richiede una connessione DoubleClick e l&#39;opzione Attiva visualizzazione mediante è impostata su True.

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
      <td>
        <p>Un ID univoco per l’impression.</p>
      </td>
      <td>
        <p>6acd7b43290490fe5c53eed31281d09a|2020-05-18:22:20:59|0000|0|2869369052</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del cookie registrato al momento dell’impression.</p>
      </td>
      <td>08c1063cb0a64349ad0d2d862f5cc700</td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il primo ID cookie dell’ID visitatore correlato.</p>
      </td>
      <td>v_08c1063cb0a64349ad0d2d862f5cc700</td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L’ID sessione registrato al momento della registrazione dell’impression.</p>
      </td>
      <td>2018-08-06:01-35-24-1231230.9bc63c34482f</td>
    </tr>
    <tr>
      <td>
        <p>DATA_EVENTO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data in cui l’impression è stata trasmessa.</p>
      </td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL in cui è stata distribuita l’impression, senza parametri di query.</p>
      </td>
      <td>https://info.adobe.com/webinar-marketo-measure-impact</td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL in cui è stata distribuita l’impression, inclusi eventuali parametri di query.</p>
      </td>
      <td>https://info.adobe.com/webinar-marketo-measure-impact?utm_source=partner&amp;mkt_tok=eyJpIjoiTnpBeE1EVml PV0UyWlRObSIsInQiOiI3MEFIek04ZVJiWm9renc1Z29RXC9kXC92YkxycFRYclE0MVhOaH Nwdml3YTZBZDdPdXh4Q0RmcnBJWXhwZTF1Z0RbXlDVmxJNzIwNkh L</td>
    </tr>
    <tr>
      <td>
        <p>INDIRIZZO_IP</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L’indirizzo IP registrato al momento dell’impression.</p>
      </td>
      <td>174 127 184 158</td>
    </tr>
    <tr>
      <td>
        <p>TIPO</p>
      </td>
      <td>varchar</td>
      <td>Indica il tipo di evento.</td>
      <td>Impression</td>
    </tr>
    <tr>
      <td>
        <p>USER_AGENT_STRING</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>Indica l'ordine in cui si è verificata la visualizzazione pagina nella sessione.</td>
      <td>
        <p>4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_RANDOM</p>
      </td>
      <td>varchar</td>
      <td>Utilizzato per l’audit e l’elaborazione interna.</td>
      <td>
        <p>20042b6b7af44512b43f6244d86faf4c</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Indica se il record è considerato un duplicato.</td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Utilizzato per l’elaborazione interna.</td>
      <td>
        <p>vero</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>In genere, la pagina di destinazione esterna immediatamente prima che l’utente entri sul sito web. Nel sistema di gestione delle relazioni con i clienti è indicato come "Pagina di riferimento".</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE-RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>In genere, la pagina di destinazione esterna immediatamente prima che l’utente entri sul sito web. Una pagina di riferimento non elaborata può contenere parametri di query nell’URL. Nel sistema di gestione delle relazioni con i clienti, denominato "Pagina di provenienza - Raw".</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>CITTÀ</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La città risolta dall’indirizzo IP.</p>
      </td>
      <td>
        <p>Seattle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGIONE</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>Il paese risolto dall’indirizzo IP.</p>
      </td>
      <td>
        <p>Stati Uniti</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_ISP</p>
      </td>
      <td>varchar</td>
      <td>Previsto null poiché il campo è obsoleto.</td>
      <td>NULL</td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La piattaforma di annunci [!DNL Marketo Measure] è stata risolta da, in genere uno dei nostri partner di integrazione.</p>
      </td>
      <td>Google</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account dell’annuncio da cui l’annuncio è stato risolto.</p>
      </td>
      <td>aw.6601259029</td>
    </tr>
    <tr>
      <td>
        <p>NOME_ACCOUNT</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’account dell’annuncio da cui l’annuncio è stato risolto.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell'inserzionista dall'account dell'annuncio da cui è stato risolto l'annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_INSERZIONISTA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell'inserzionista dall'account annuncio da cui è stato risolto l'annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Analisi di marketing per misurazione di mercato</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del sito dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_SITO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del sito dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>blocco stradale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della campagna dall’account annuncio da cui è stato risolto l’annuncio.</p>
      </td>
      <td>aw.6601259029.317738075</td>
    </tr>
    <tr>
      <td>
        <p>NOME_CAMPAGNA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della campagna dall’account annuncio da cui è stato risolto l’annuncio.</p>
      </td>
      <td>Marketing Attribution</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non è presente alcun gruppo di annunci nella gerarchia a doppio clic per le impression</p>
      </td>
      <td>
        <p>nulle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non è presente alcun gruppo di annunci nella gerarchia a doppio clic per le impression</p>
      </td>
      <td>
        <p>nulle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>Nome dell’annuncio dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>
        <p>centurylink_banner_98121</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non è presente alcun elemento creativo nella gerarchia di Doubleclick per le impression.</p>
      </td>
      <td>
        <p>nulle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_CREATIVO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non è presente alcun elemento creativo nella gerarchia di Doubleclick per le impression.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non è presente alcun elemento creativo nella gerarchia di Doubleclick per le impression.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non è presente alcun elemento creativo nella gerarchia di Doubleclick per le impression.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non è presente alcun elemento creativo nella gerarchia di Doubleclick per le impression.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non è presente alcun elemento creativo nella gerarchia di Doubleclick per le impression.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non è presente alcuna parola chiave nella gerarchia di Doubleclick per Impression.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non è presente alcuna parola chiave nella gerarchia di Doubleclick per Impression.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non è presente alcuna parola chiave nella gerarchia di Doubleclick per Impression.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>NOME_BROWSER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, il browser rilevato su cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>Chrome</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, la versione del browser rilevato su cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_PIATTAFORMA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, la piattaforma rilevata su cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>Mac</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, la versione rilevata della piattaforma su cui si trovava l’utente durante la sessione.</p>
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
        <p>numero(38,0)</p>
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
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CHIAVE_RIGA_SITO</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_KEYWORDS {#biz-keywords}

Parole chiave importate da qualsiasi account annuncio collegato.

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
      <td>
        <p>ID univoco della parola chiave.</p>
      </td>
      <td>
        <p>ba.3284209.132630532.3646889365.39464932147</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td>L’ID della parola chiave dal sistema di origine.</td>
      <td>
        <p>39464932147</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account annuncio da cui è stata importata la parola chiave.</p>
      </td>
      <td>fb.106851586409075</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’account annuncio da cui è stata importata la parola chiave.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non è presente alcuna parola chiave nella gerarchia di Doubleclick per Impression.</p>
      </td>
      <td>
        <p>nulle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_INSERZIONISTA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non è presente alcuna parola chiave nella gerarchia di Doubleclick per Impression.</p>
      </td>
      <td>
        <p>nulle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del gruppo di annunci per la parola chiave.</p>
      </td>
      <td>
        <p>ba.3284209.132630532.3646889365</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
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
      <td>varchar</td>
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
        <p>vero</p>
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
        <p>Indica se la parola chiave è stata eliminata nel sistema di origine.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>2018-08-02 06:37:29.000</td>
    </tr>
    <tr>
      <td>
        <p>PRIMO_IMPORTATO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data della prima importazione del record dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-02 06:37:29.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della parola chiave, dal sistema di origine.</p>
      </td>
      <td>
        <p>[attribuzione ricavi b2b]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEED_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se la parola chiave deve essere aggiornata per l'assegnazione tag [!DNL Marketo Measure].</p>
        <p>(Campo diagnostico, utilizzato per l'elaborazione interna).</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CHIAVE_RAGGRUPPAMENTO</p>
      </td>
      <td>varchar</td>
      <td>Campo diagnostico, utilizzato per l’elaborazione interna.</td>
      <td>
        <p>ba.3284209.132630532.3646889365</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Oggetto o entità principale per questa tabella. In questo caso, "Parola chiave".</p>
      </td>
      <td>
        <p>Parola chiave</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TIPO_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del provider dell’annuncio per la parola chiave.</p>
      </td>
      <td>
        <p>BingAds</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L’URL della pagina di destinazione.</p>
        <p>(Campo diagnostico, per elaborazione interna).</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Valore precedente per URL_CURRENT.</p>
        <p>(Campo diagnostico, per elaborazione interna).</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>URL_RICHIESTO</td>
      <td>varchar</td>
      <td>
        <p>URL della pagina di destinazione con [!DNL Marketo Measure] parametri.</p>
        <p>(Campo diagnostico, per elaborazione interna).</p>
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
      <td>Campo diagnostico, per elaborazione interna.</td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WORD</p>
      </td>
      <td>varchar</td>
      <td>La fase di ricerca immessa dall’utente.</td>
      <td>
        <p>attribuzione ricavi b2b</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MATCH_TYPE</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>varchar</td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUIRED</p>
      </td>
      <td>varchar</td>
      <td>Utilizzato per la diagnostica interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>varchar</td>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
      </td>
      <td>-2712935512233520000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_LANDING_PAGES {#biz-landing-pages}

Pagine di destinazione importate da qualsiasi account annuncio collegato.

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
      <td>
        <p>ID univoco della pagina di destinazione.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>ID dell’account annuncio da cui è stata importata la pagina di destinazione.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>Nome dell’account dell’annuncio da cui è stata importata la pagina di destinazione.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’inserzionista per la pagina di destinazione, in particolare per Doubleclick.</p>
      </td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>
        <p>NOME_INSERZIONISTA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’inserzionista per la pagina di destinazione, in particolare per Doubleclick.</p>
      </td>
      <td>Marketing analytics</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>ID del gruppo di annunci per la pagina di destinazione.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>Nome del gruppo di annunci per la pagina di destinazione.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>ID della campagna per la pagina di destinazione.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
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
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica della riga.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>PRIMO_IMPORTATO</p>
      </td>
      <td>timestamp_ntz</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NEED_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CHIAVE_RAGGRUPPAMENTO</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TIPO_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_RICHIESTO</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_LEAD {#biz-leads}

Lead importati dal sistema di origine.

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
      <td>
        <p>L'ID lead dal sistema di origine.</p>
      </td>
      <td>
        <p>00Q0Z00001MZcj8UAD</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell'ultima modifica del record Lead dal sistema di origine.</p>
      </td>
      <td>
        <p>2018-08-27 21:52:10.000</p>
      </td>
    </tr>
    <tr>
      <td>DATA_CREAZIONE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di creazione del record Lead dal sistema di origine.</p>
      </td>
      <td>2018-08-27 21:52:10.000</td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Indirizzo e-mail del lead, dal sistema di origine.</p>
      </td>
      <td>persona@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>SITO_WEB</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>Source in cui è stato creato il lead.</p>
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
        <p>Indica se il lead è stato convertito in un contatto.</p>
      </td>
      <td>
        <p>vero</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_OPPORTUNITY_ID</p>
      </td>
      <td>varchar</td>
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
      <td>timestamp_ntz</td>
      <td>
        <p>Data in cui il lead è stato convertito in contatto.</p>
      </td>
      <td>
        <p>2018-08-27 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_CONTACT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del contatto correlato dopo la conversione del lead.</p>
      </td>
      <td>
        <p>0030Z00003Oyp25QAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNTID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account mappato. Requisiti: abilitare ABM</p>
      </td>
      <td>
        <p>0010Z0000236F9GQAU</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Fase corrente del lead, riconosciuta come fase personalizzata che può essere creata nell'applicazione [!DNL Marketo Measure].</p>
      </td>
      <td>
        <p>Demo pianificata</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE_PREVIOUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Tutte le fasi precedenti per il lead, riconosciute come fasi personalizzate che possono essere create nell'applicazione [!DNL Marketo Measure].</p>
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
        <p>Questa funzione è stata rimossa. Non utilizzare questa colonna.</p>
      </td>
      <td>
        <p>N/D</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SCORE_MODEL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>(obsoleto)</p>
      </td>
      <td>
        <p>nulle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SCORE_RESULTS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>(obsoleto)</p>
      </td>
      <td>
        <p>nulle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L'ID cookie [!DNL Marketo Measure] utilizzato per compilare da un partner di integrazione per mappare un evento offline a una sessione Web. Requisito: Abilita tracciamento chiamate: True</p>
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
        <p>Indica se il record viene eliminato o meno nel sistema di origine.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
      </td>
      <td>3263982503087870000</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Proprietà personalizzate importate da [!DNL Marketo Measure] dal sistema di origine in formato JSON.</td>
      <td>{"Lead_Type__c":"Vendite create", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>IS_DUPLICATE</td>
      <td>booleano</td>
      <td>Utilizzato per deduplicare i record se è impostata un’integrazione CRM e Marketo. In presenza di duplicati, il lead Marketo viene contrassegnato come true.</td>
      <td>vero</td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Indica se il record proviene da un’integrazione CRM o Marketo.</td>
      <td>Crm</td>
    </tr>
    <tr>
      <td>OTHER_SYSTEM_ID</td>
      <td>varchar</td>
      <td>Mappa una persona da un’integrazione Marketo con un lead da un’integrazione CRM. Se esiste sia un’integrazione CRM che Marketo, il valore è l’ID corrispondente.</td>
      <td>1234</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_LEAD_STAGE_TRANSITIONS {#biz-lead-stage-transitions}

Transizioni nell&#39;area intermedia per lead o contatti.

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
      <td>
        <p>Un ID univoco per la transizione.</p>
      </td>
      <td>
        <p>ST_0030Z00003FhkRXQAZ__FT-1_TP2_Person_0030Z00003FhkRXQAZ_2018-08-27:17-05-45-9474800.0d5c18c29d7b</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L’indirizzo e-mail fornito per il lead/contatto correlato.</p>
      </td>
      <td>
        <p>persone@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del lead associato alla transizione.</p>
      </td>
      <td>
        <p>00Q3100001Fx6AlEAJ</p>
      </td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>ID del Buyer Touchpoint associato alla transizione.</p>
      </td>
      <td>
        <p>TP2_Person_00Q3100001Fx6AlEAJ_2018-08-28:14-41-06-1674260.d00ceb09fbd3</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRANSITION_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di transizione del record nell’area di visualizzazione.</p>
      </td>
      <td>
        <p>2018-08-27 16:05:34.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Valore ID della fase per la transizione.</p>
      </td>
      <td>
        <p>_bizible_FT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FASE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della fase per la transizione.</p>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>La classificazione numerica dello stage, come ordinato nelle impostazioni di mappatura dello stage [!DNL Marketo Measure].</p>
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
        <p>Utilizzato nell’elaborazione interna per l’indicizzazione e l’ordinamento di fasi di boomerang.</p>
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
      <td>Utilizzato nell’elaborazione interna per l’indicizzazione e l’ordinamento di fasi di boomerang.</td>
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
        <p>Indica se il punto di contatto è considerato in sospeso e non ancora chiuso. Questo viene visualizzato solo per i clienti con modello di attribuzione percorso completo.</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Indica se la riga è associata a una transizione di fase milestone. Ad esempio, se ci sono 3 stadi/ingressi (FT, LC, MQL) e 4 punti di contatto, il 1 punto di contatto senza una fase su di esso è considerato "non transitorio" in modo che il valore sia uguale a vero.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PREVIOUS_STAGE_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di transizione per la fase precedente, in base alla classificazione della fase.</p>
      </td>
      <td>
        <p>2017-11-28 21:26:44.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEXT_STAGE_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di transizione per la fase successiva, in base alla classificazione della fase.</p>
      </td>
      <td>
        <p>2017-12-11 22:39:17.000</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
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
        <p>Indica se il record di transizione viene considerato eliminato o meno.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_OPPORTUNITÀ {#biz-opportunities}

Opportunità importate dal sistema di origine.

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
      <td>
        <p>L’ID dell’opportunità dal sistema di origine.</p>
      </td>
      <td>
        <p>0060Z00000o89I4QAI</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica dell’opportunità, dal sistema di origine.</p>
      </td>
      <td>2017-11-28 21:26:44.000</td>
    </tr>
    <tr>
      <td>DATA_CREAZIONE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>La data di creazione dell’opportunità, dal sistema di origine.</p>
      </td>
      <td>2017-11-28 21:26:44.000</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account correlato.</p>
      </td>
      <td>
        <p>001i000000qbyeoAAA</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il nome dell’opportunità, dal sistema di origine.</p>
      </td>
      <td>
        <p>Rinnovo Mareketo Measure</p>
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
        <p>Indica se l’opportunità è stata spostata in una fase considerata vinta.</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Indica se l’opportunità è stata spostata in una fase considerata chiusa.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLOSE_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di chiusura prevista o effettiva dell’opportunità, dal sistema di origine.</p>
      </td>
      <td>
        <p>2019-08-28 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_CUSTOM_MODEL_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>(obsoleto)</p>
      </td>
      <td>
        <p>nulle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>QUANTITÀ</p>
      </td>
      <td>
        <p>numero(38,8)</p>
      </td>
      <td>
        <p>Importo dell’offerta previsto o chiuso dall’opportunità, dal sistema di origine.</p>
      </td>
      <td>
        <p>8988,00000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_FROM_LEAD_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L’ID del lead correlato che è stato convertito in questa opportunità.</p>
        <p>Questo campo non è impostato e restituisce null nel Snowflake per tutti i clienti.</p>
      </td>
      <td>
        <p>nulle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_FROM_LEAD_EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L’e-mail del lead correlato che è stato convertito in questa opportunità.</p>
        <p>Questo campo non è impostato e restituisce null nel Snowflake per tutti i clienti.</p>
      </td>
      <td>
        <p>nulle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMARY_CONTACT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Se si utilizza il ruolo di contatto principale, l’ID del contatto correlato viene elencato come ruolo di contatto principale.</p>
      </td>
      <td>
        <p>00331000038uGfhAAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL_CONTATTO_PRINCIPALE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Se viene utilizzato il ruolo di contatto principale, l’e-mail del contatto correlato elencato come ruolo di contatto principale.</p>
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
        <p>Questa funzione è stata rimossa. Non utilizzare questa colonna.</p>
      </td>
      <td>
        <p>N/D</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Fase corrente dell'opportunità, come definita nell'applicazione [!DNL Marketo Measure].</p>
      </td>
      <td>
        <p>Demo DM</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE_PREVIOUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Stringa di tutte le fasi che l'opportunità ha attraversato in precedenza, come definito nell'applicazione [!DNL Marketo Measure].</p>
      </td>
      <td>
        <p>Discovery qualificato, demo pianificata</p>
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
        <p>Indica se il record viene eliminato o meno nel sistema di origine.</p>
      </td>
      <td>falso</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
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
      <td>numero(38,0)</td>
      <td>Valore ID della valuta per il record.</td>
      <td>4609512587744160000</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Proprietà personalizzate importate da [!DNL Marketo Measure] dal sistema di origine in formato JSON.</td>
      <td>{"Opportunity_Location__c":"Seattle", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>TIPO_OPPORTUNITÀ <b>∗</b></td>
      <td>varchar</td>
      <td>Tipo di opportunità, ad esempio Nuova azienda, Rinnovo e così via.</td>
      <td>Rinnovo, potenziale cliente</td>
    </tr>
  </tbody>
</table>
<p>
<b>∗</b> <i>Disponibile solo in Marketo Measure Ultimate</i>
<p>

### BIZ_OPP_STAGE_TRANSITIONS {#biz-opp-stage-transitions}

Transizioni nell&#39;area intermedia per le opportunità.

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
      <td>
        <p>Un ID univoco per la transizione.</p>
      </td>
      <td>
        <p>ST_0060Z00000nEgjlQAC_0030Z00003IjojKQAR_Demo Pianificata-1_BAT2_0060Z00000nEgjlQAC_0030Z00003IjojKQAR_2018-06-01:19-51-38-1685390.beec556e7757</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account associato all’opportunità.</p>
      </td>
      <td>
        <p>0013100001b44nTAAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ID_OPPORTUNITÀ</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’opportunità associata alla transizione.</p>
      </td>
      <td>
        <p>0060Z00000nEgjlQAC</p>
      </td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>
        <p>ID del contatto associato alla transizione.</p>
      </td>
      <td>
        <p>0030Z00003IjojKQAR</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L’indirizzo e-mail fornito per il contatto correlato.</p>
      </td>
      <td>
        <p>persone@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del Buyer Attribution Touchpoint associato alla transizione.</p>
      </td>
      <td>
        <p>BAT2_0060Z00000nEgjlQAC_0030Z00003IjojKQAR_2018-06-01:19-51-38-1685390.beec556e7757</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRANSITION_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di transizione del record nell’area di visualizzazione.</p>
      </td>
      <td>
        <p>2018-05-26 07:29:43.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FASE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della fase per la transizione.</p>
      </td>
      <td>
        <p>Demo pianificata</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Valore ID della fase per la transizione.</p>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>La classificazione numerica dello stage, come ordinato nelle impostazioni di mappatura dello stage [!DNL Marketo Measure].</p>
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
        <p>Utilizzato nell’elaborazione interna per l’indicizzazione e l’ordinamento di fasi di boomerang.</p>
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
        <p>Utilizzato nell’elaborazione interna per l’indicizzazione e l’ordinamento di fasi di boomerang.</p>
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
        <p>Indica se il punto di contatto è considerato in sospeso e non ancora chiuso. Questo viene visualizzato solo per i clienti con modello di attribuzione percorso completo.</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Indica se la riga è associata a una transizione di fase milestone. Ad esempio, se ci sono 3 stadi/ingressi (FT, LC, MQL) e 4 punti di contatto, il 1 punto di contatto senza una fase su di esso è considerato "non transitorio" in modo che il valore sia uguale a vero.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PREVIOUS_STAGE_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di transizione per la fase precedente, in base alla classificazione della fase.</p>
      </td>
      <td>
        <p>2015-07-16 17:41:49.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEXT_STAGE_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di transizione per la fase successiva, in base alla classificazione della fase.</p>
      </td>
      <td>
        <p>2018-08-27 19:40:52.000</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
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
        <p>Indica se il record di transizione viene considerato eliminato o meno.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_PAGE_VIEWS {#biz-page-views}

Visualizzazioni di pagina raccolte dalle visite web. Più visualizzazioni di pagina possono comporre una singola sessione.

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
      <td>
        <p>Un ID univoco per la Visualizzazione pagina.</p>
      </td>
      <td>
        <p>2018-08-19:16-49-58-24340,277 d79d0167849</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L’ID cookie registrato al momento della registrazione di Visualizzazione pagina.</p>
      </td>
      <td>
        <p>277d79d01678498fea067c9b631bf6df</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>L’ID sessione è correlato alla Visualizzazione pagina.</p>
      </td>
      <td>
        <p>2018-08-19:16-49-58-24340,277 d79d0167849</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DATA_EVENTO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data in cui si è verificata la visualizzazione della pagina.</p>
      </td>
      <td>
        <p>2018-08-19 16:49:58.000</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>
        <p>16:55:37.000 18-08-19</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL della visualizzazione Pagina, senza parametri di query.</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL della visualizzazione pagina, inclusi eventuali parametri di query.</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo?hsCtaTracking=207219e9-87b6-4105-8f4b-0a3b62ae1af8%7C48060522-3aeb-4c72-8ce5-fd4b1017f069</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>INDIRIZZO_IP</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L'indirizzo IP registrato al momento dell'invio del modulo.</p>
      </td>
      <td>
        <p>174 127 184 158</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TIPO</p>
      </td>
      <td>varchar</td>
      <td>Indica il tipo di evento.</td>
      <td>
        <p>PageView</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_AGENT_STRING</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dispositivo e browser registrati al momento dell’invio del modulo.</p>
      </td>
      <td>
        <p>Mozilla/5.0 (X11; Linux x86_64; rv:52.0) Gecko/20100101 Firefox/52.0</p>
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
        <p>Indica l'ordine in cui si è verificata la visualizzazione pagina nella sessione.</p>
      </td>
      <td>
        <p>1</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_RANDOM</p>
      </td>
      <td>varchar</td>
      <td>Utilizzato per l’audit e l’elaborazione interna.</td>
      <td>
        <p>103532</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Indica se il record è considerato un duplicato.</td>
      <td>falso</td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Utilizzato per l’elaborazione interna.</td>
      <td>vero</td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL da cui ha avuto origine la visualizzazione pagina, senza parametri di query.</p>
      </td>
      <td>
        <p>http://info.adobe.com/cmos-guide-to-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL da cui ha avuto origine la visualizzazione pagina, inclusi eventuali parametri di query.</p>
      </td>
      <td>
        <p>http://info.adobe.com/cmos-guide-to-b2b-marketing-attribution?utm_source=linkedin&amp;utm_medium=Social&amp;utm_campaign=SU%20-%20CMO%20JT&amp;utm_content=CMOs%20Guide&amp;utm_term=lisu05091601</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAGE_TITLE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Titolo della pagina.</p>
      </td>
      <td>
        <p>Guida CMO al download dell’attribuzione marketing B2B</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Indirizzo e-mail fornito in un modulo, acquisito da JavaScript.</p>
      </td>
      <td>personc@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
      </td>
      <td>
        <p>-6255315750913680000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td>Chiave esterna della tabella URL.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td>Chiave esterna della tabella URL.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>HAS_USER_CONSENT</td>
      <td>booleano</td>
      <td>Indica se l'utente ha acconsentito al tracciamento. False indica che la visualizzazione pagina è stata raccolta perché il consenso dell’utente non è richiesto. True significa che la visualizzazione pagina è stata raccolta e che l'utente ha dato il consenso per la registrazione.</td>
      <td>vero</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_PLACEMENTS {#biz-placements}

Tabella in cui sono memorizzati tutti i posizionamenti scaricati da qualsiasi account di annunci connesso, un oggetto dall’integrazione Doubleclick.

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
      <td>varchar</td>
      <td>L’ID di posizionamento dal sistema di origine.</td>
      <td>10426699711</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account dell’annuncio da cui è stato importato il posizionamento.</p>
      </td>
      <td>f ter. 106851586409075</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’account dell’annuncio da cui è stato importato il posizionamento.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’inserzionista per il posizionamento, in particolare per Doubleclick.</p>
      </td>
      <td>300184624</td>
    </tr>
    <tr>
      <td>
        <p>NOME_INSERZIONISTA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’inserzionista per il posizionamento, in particolare per Doubleclick.</p>
      </td>
      <td>[!DNL Marketo Measure] Analytics</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore atteso è nullo poiché non è presente alcun gruppo di annunci al di sopra del posizionamento in alcuna gerarchia di annunci.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore atteso è nullo poiché non è presente alcun gruppo di annunci al di sopra del posizionamento in alcuna gerarchia di annunci.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della campagna per il posizionamento.</p>
      </td>
      <td>ba.3284209.132855866</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della campagna per il posizionamento.</p>
      </td>
      <td>Marketing delle pipeline</td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se il posizionamento è ancora attivo nel sistema di origine.</p>
      </td>
      <td>vero</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se il posizionamento è stato eliminato nel sistema di origine.</p>
      </td>
      <td>falso</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>2018-08-02 06:36:25.000</td>
    </tr>
    <tr>
      <td>
        <p>PRIMO_IMPORTATO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data della prima importazione del record dal sistema di origine.</p>
      </td>
      <td>2018-08-02 06:36:25.000</td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del posizionamento, dal sistema di origine.</p>
      </td>
      <td>Mercato</td>
    </tr>
    <tr>
      <td>
        <p>NEED_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se il posizionamento deve essere aggiornato o meno per l'assegnazione tag [!DNL Marketo Measure].</p>
        <p>(Campo diagnostico utilizzato dall'elaborazione interna).</p>
      </td>
      <td>falso</td>
    </tr>
    <tr>
      <td>
        <p>CHIAVE_RAGGRUPPAMENTO</p>
      </td>
      <td>varchar</td>
      <td>Campo diagnostico, per elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Oggetto o entità principale per questa tabella. In questo caso, "Posizionamento".</p>
      </td>
      <td>Posizionamento</td>
    </tr>
    <tr>
      <td>
        <p>TIPO_PROVIDER</p>
      </td>
      <td>varchar</td>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
      </td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record del Snowflake</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di modifica del Snowflake del record</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di eliminazione del record da parte del Snowflake, se è stato eliminato</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SEGMENTS {#biz-segments}

Valori del segmento come definiti nell&#39;applicazione [!DNL Marketo Measure].

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
      <td>varchar</td>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
      </td>
      <td>
        <p>1028715376434030000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SEGMENT_NAMES {#biz-segment-names}

Mappa il nome del segmento personalizzato sul relativo valore di categoria. I nomi delle colonne vengono mappati sulle intestazioni di colonna Category1 - 15 presenti nelle tabelle dei punti di contatto.

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
        <p>CATEGORIA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Indica la categoria a cui è mappato il nome del segmento.</p>
      </td>
      <td>
        <p>CategoryOne</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>
        <p>2022-02-28 18:12:35.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_SEGMENTO</p>
      </td>
      <td>varchar</td>
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
      <td>vero</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>booleano</td>
      <td>Indica se il record è stato eliminato.</td>
      <td>falso</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SESSIONI {#biz-sessions}

Sessioni elaborate dalle visualizzazioni di pagina. Più visualizzazioni di pagina possono costituire una sessione e un singolo ID visitatore può essere associato a più sessioni.

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
      <td>
        <p>Un ID univoco per la sessione.</p>
      </td>
      <td>
        <p>2016-08-01:14-21-9079480.33163948f0a3</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il primo cookie dell’ID visitatore correlato.</p>
      </td>
      <td>v_277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID cookie registrato della sessione.</p>
      </td>
      <td>277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>DATA_EVENTO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data della sessione.</p>
      </td>
      <td>
        <p>01/08/2016 14:24:21.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DATA DI MODIFICA</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>
        <p>03:49:10.000 09-01 2018</p>
      </td>
    </tr>
    <tr>
      <td>IS_FIRST_SESSION</td>
      <td>booleano</td>
      <td>Indica se si tratta della prima sessione per l’ID visitatore.</td>
      <td>vero</td>
    </tr>
    <tr>
      <td>
        <p>CANALE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Canale attribuito alla sessione, come definito dalle definizioni dei canali impostate nell'applicazione [!DNL Marketo Measure].</p>
      </td>
      <td>
        <p>Ricerca a pagamento.AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAGE_TITLE</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>URL della prima visualizzazione pagina della sessione, senza parametri di query.</p>
      </td>
      <td>
        <p>http://www.adobe.com/salesforce-google-analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL della prima visualizzazione pagina della sessione, inclusi eventuali parametri di query.</p>
      </td>
      <td>
        <p>http://www.adobe.com/salesforce-google-analytics?_bt=83558988035&amp;_bk=google%20analytics%20salesforce&amp;_bm= p&amp;gclid=CMvd5YTLo84CFUI9gQodd-kLEQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL da cui ha avuto origine la sessione, senza parametri di query.</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL da cui ha avuto origine la sessione, inclusi eventuali parametri di query.</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della pagina del referente.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore che l’utente ha immesso nel browser per cercare e che è finito sul sito web.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] google salesforce</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Utilizzato per definire l’origine che ha generato la sessione. Questo può essere analizzato dall'URL da utm_source o impostato su un provider di annunci se [!DNL Marketo Measure] è in grado di risolvere un annuncio.</p>
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
        <p>Indica se la sessione contiene o meno un riempimento del modulo</p>
      </td>
      <td>
        <p>vero</p>
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
        <p>Indica se la sessione contiene o meno una chat Web.</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Indica se la sessione aveva o meno un indirizzo e-mail.</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPOSITIVO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il browser e il sistema operativo dell’utente durante la sessione.</p>
      </td>
      <td>
        <p>Chrome (65.0), Windows (6.1)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Piattaforma annuncio [!DNL Marketo Measure] risolta da, in genere uno dei nostri partner di integrazione.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account dell’annuncio da cui l’annuncio è stato risolto.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_ACCOUNT</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’account dell’annuncio da cui l’annuncio è stato risolto.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’inserzionista da cui è stato risolto l’annuncio, in particolare dalla connessione Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_INSERZIONISTA</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>ID del sito da cui è stato risolto l’annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_SITO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del sito da cui è stato risolto l’annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del posizionamento da cui è stato risolto l’annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del posizionamento da cui è stato risolto l’annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>blocco stradale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della campagna da cui è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029.321586235</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_CAMPAGNA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della campagna da cui è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>Pianificazione del webinar Budget</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>ID dell’annuncio risolto da. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>aw.6601259029.321586235.23182235435</td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’annuncio risolto da. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>Promozione invernale - Verde</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della creatività da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>aw.6601259029.321586235.23182235435.83558988035</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_CREATIVO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della creatività da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Integrare GA e Salesforce</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La prima riga del contenuto creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Integrare Salesforce &amp; Analytics In</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La seconda riga del contenuto creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Ottimizza per i ricavi. Scopri come.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La pagina di destinazione in cui viene fatto clic dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>http://www.adobe.com/salesforce-google-analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il nome URL descrittivo visualizzato nell’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>adobe.com/Salesforce-for-GA</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della parola chiave da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>aw.6601259029.321586235.23182235435.35934468937</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>Tipo di corrispondenza trovata tra la frase di ricerca e la parola chiave acquistata.</p>
      </td>
      <td>
        <p>Frase</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAGNA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Analizzato dall’URL da utm_campaign.</p>
      </td>
      <td>
        <p>SU - Account ABC - Competenze media a pagamento</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SORGENTE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Analizzato dall’URL da utm_source.</p>
      </td>
      <td>
        <p>linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIUM</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Analizzato dall’URL da utm_medium.</p>
      </td>
      <td>
        <p>Social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TERMINE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Analizzato dall’URL da utm_term.</p>
      </td>
      <td>
        <p>lisu07261601</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTENUTO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Analizzato dall’URL da utm_content.</p>
      </td>
      <td>
        <p>Rapporto benchmark AdWords 2016</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITTÀ</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La città risolta dall’indirizzo IP.</p>
      </td>
      <td>Vancouver</td>
    </tr>
    <tr>
      <td>
        <p>REGIONE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Area risolta dall'indirizzo IP.</p>
      </td>
      <td>Columbia Britannica</td>
    </tr>
    <tr>
      <td>
        <p>PAESE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il paese risolto dall’indirizzo IP.</p>
      </td>
      <td>Canada</td>
    </tr>
    <tr>
      <td>
        <p>NOME_ISP</p>
      </td>
      <td>varchar</td>
      <td>Previsto null poiché il campo è obsoleto.</td>
      <td>
        <p>NULL</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>INDIRIZZO_IP</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L'indirizzo IP registrato al momento della sessione.</p>
      </td>
      <td>
        <p>174 127 184 158</p>
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
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CHIAVE_RIGA_SITO</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SITES {#biz-sites}

Siti importati da qualsiasi account annuncio collegato.

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
      <td>
        <p>Un ID univoco per il sito.</p>
      </td>
      <td>aw.3284209</td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td>ID del sito dal sistema di origine.</td>
      <td>39464932147</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell'account dell'annuncio da cui è stato importato il sito.</p>
      </td>
      <td>aw.3284209</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell'account dell'annuncio da cui è stato importato il sito.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>L’ID dell’inserzionista per il sito, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_INSERZIONISTA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il nome dell’inserzionista del sito, in particolare di Doubleclick.</p>
      </td>
      <td>
        <p>Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non vi è alcun gruppo di annunci sopra il sito in alcuna gerarchia di annunci.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previsto null poiché non vi è alcun gruppo di annunci sopra il sito in alcuna gerarchia di annunci.</p>
      </td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
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
      <td>vero</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se il sito è stato eliminato nel sistema di origine.</p>
      </td>
      <td>falso</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>2018-08-02 06:37:29.000</td>
    </tr>
    <tr>
      <td>
        <p>PRIMO_IMPORTATO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data della prima importazione del record dal sistema di origine.</p>
      </td>
      <td>2018-08-02 06:37:29.000</td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del sito, dal sistema di origine.</p>
      </td>
      <td>Ricavi</td>
    </tr>
    <tr>
      <td>
        <p>NEED_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se il sito deve essere aggiornato per l'assegnazione tag [!DNL Marketo Measure].</p>
        <p>(Campo diagnostico, utilizzato per l'elaborazione interna).</p>
      </td>
      <td>falso</td>
    </tr>
    <tr>
      <td>
        <p>CHIAVE_RAGGRUPPAMENTO</p>
      </td>
      <td>varchar</td>
      <td>Campo diagnostico, utilizzato per l’elaborazione interna.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Oggetto o entità principale per questa tabella. In questo caso, "Sito".</p>
      </td>
      <td>Sito</td>
    </tr>
    <tr>
      <td>
        <p>TIPO_PROVIDER</p>
      </td>
      <td>varchar</td>
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
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SITE_LINKS {#biz-site-links}

Collegamenti ai siti da qualsiasi account Ads connesso.

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
      <td>varchar</td>
      <td></td>
      <td>
        <p>1654234342</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account degli annunci collegati per il collegamento al sito</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>L’ID dell’inserzionista del collegamento al sito, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_INSERZIONISTA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il nome dell’inserzionista del collegamento al sito, in particolare per Doubleclick.</p>
      </td>
      <td>
        <p>Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del gruppo di annunci per il collegamento al sito</p>
      </td>
      <td>aw.6601259029.208548635.16750166675</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del gruppo di annunci per il collegamento al sito</p>
      </td>
      <td>Brand - Core</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>Nome della campagna per il collegamento del sito</p>
      </td>
      <td>
        <p>Marchio</p>
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
        <p>Indica se il collegamento al sito è ancora attivo nell'account annunci</p>
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
        <p>Se il collegamento del sito è stato eliminato o meno nell’account degli annunci</p>
      </td>
      <td>
        <p>FALSE</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica della riga</p>
      </td>
      <td>
        <p>2018-08-02 06:36:50.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMO_IMPORTATO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data del primo download del collegamento al sito da parte di [!DNL Marketo Measure]</p>
      </td>
      <td>
        <p>2018-08-02 06:36:50.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del collegamento di sito</p>
      </td>
      <td>Collegamento A</td>
    </tr>
    <tr>
      <td>
        <p>NEED_UPDATE</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Se il collegamento di sito deve essere aggiornato o meno per ottenere i tag Marekto Measure</p>
      </td>
      <td>
        <p>FALSE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CHIAVE_RAGGRUPPAMENTO</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td>
        <p>aw.6601259029.285077795</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Oggetto o entità principale per questa tabella. In questo caso, "SiteLink"</p>
      </td>
      <td>
        <p>CollegamentoSito</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TIPO_PROVIDER</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>L’URL della pagina di destinazione.</p>
        <p>(Campo diagnostico, per elaborazione interna).</p>
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
      <td>varchar</td>
      <td>
        <p>Valore precedente per URL_CURRENT.</p>
        <p>(Campo diagnostico, per elaborazione interna).</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_RICHIESTO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Specifica l'URL con i parametri [!DNL Marketo Measure].</p>
        <p>(Campo diagnostico, per elaborazione interna).</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record del Snowflake</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di modifica del Snowflake del record</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di eliminazione del record da parte del Snowflake, se è stato eliminato</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_STAGE_DEFINITIONS {#biz-stage-definitions}

Elenco delle fasi importate o definite nell&#39;applicazione [!DNL Marketo Measure].

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
      <td>
        <p>Un ID univoco per lo stage.</p>
      </td>
      <td>
        <p>01J3100000QE753EAD</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-22 17:27:27.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_FASE</p>
      </td>
      <td>varchar</td>
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
        <p>falso</p>
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
        <p>falso</p>
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
        <p>Indica se lo stage è selezionato per il tracciamento come stadio di boomerang.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_TRANSITION_TRACKING</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>Indica se lo stage è selezionato per tenere traccia delle transizioni.</td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_STATUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Stato dello stage, come definito nel mapping dello stage dell'applicazione [!DNL Marketo Measure].</p>
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
        <p>vero</p>
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
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLASSIFICA</p>
      </td>
      <td>
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>La classificazione numerica dello stage, utilizzata per ordinare gli stadi in ordine transitorio.</p>
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
        <p>Indica se lo stage è stato eliminato o meno.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_PUNTI DI CONTATTO {#biz-touchpoints}

Punti di contatto dell’acquirente, tutti i punti di contatto associati a un lead o a un contatto. Questa tabella sarà vuota se i punti di contatto lead o contatti sono disattivati.

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
      <td>
        <p>Un ID univoco per il Buyer Touchpoint (BT).</p>
      </td>
      <td>
        <p>TP2_Person_00Q0Z000013e2PYUAY_2018-08-27:20-04-40-5655690.1ee8567c175a</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-08-29 22:29:30.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>Indirizzo e-mail associato all’BT.</td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>
        <p>ID del contatto associato all’BT.</p>
      </td>
      <td>0030Z00003K5bpKQAR</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account associato all’BT.</p>
      </td>
      <td>
        <p>0013100001lSLScAAO</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del lead associato all’BT.</p>
      </td>
      <td>
        <p>00Q0Z000013e2PYUAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>UNIQUE_ID_PERSON</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Record della persona padre relativo a un lead o a un contatto.</p>
      </td>
      <td>
        <p>Person_00Q0Z000013e2PYUAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_TOUCHPOINT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del punto di contatto utente che ha generato l’BT.</p>
      </td>
      <td>
        <p>person@adobe.com_2018-08-29:18-14-53-8102030.10df92cbb414</p>
      </td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>ID del visitatore associato all’BT.</td>
      <td>v_277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>DATA_PUNTO DI CONTATTO</p>
      </td>
      <td>timestamp_ntz</td>
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
      <td>varchar</td>
      <td>
        <p>Tipo di attività, visita Web, modulo Web, chat Web, telefonata, campagna [CRM] o attività [CRM]. Nel sistema di gestione delle relazioni con i clienti è indicato come "Tipo di punto di contatto".</p>
      </td>
      <td>
        <p>Modulo web</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CANALE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il canale in cui rientra il punto di contatto, come definito nelle definizioni di canale personalizzate all'interno dell'app [!DNL Marketo Measure]. Nel sistema di gestione delle relazioni con i clienti, denominato "Canale di marketing - Percorso".</p>
      </td>
      <td>Social.LinkedIn</td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA 1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore del segmento per la prima categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</p>
      </td>
      <td>ABC</td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA 2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore del segmento per la seconda categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</p>
      </td>
      <td>
        <p>Sì</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA 3</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore del segmento per la terza categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</p>
      </td>
      <td>
        <p>Altro</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA4</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore del segmento per la quarta categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</p>
      </td>
      <td>
        <p>Partner</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA5</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore del segmento per la quinta categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA6</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore del segmento per la sesta categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA7</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per la settima categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA8</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per l'ottava categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA9</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per la nona categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA10</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per la decima categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA11</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per l'11a categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA12</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per la dodicesima categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA13</p>
      </td>
      <td>varchar</td>
      <td>Il valore del segmento per la tredicesima categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA14</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore del segmento per la quattordicesima categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORIA15</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore del segmento per la quindicesima categoria in cui rientra il punto di contatto, come definito nelle definizioni dei segmenti nell'app [!DNL Marketo Measure]. Nella gestione delle relazioni con i clienti, denominati "Segmenti".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NOME_BROWSER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, il browser rilevato su cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>Chrome</td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, la versione del browser rilevato su cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>68</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_PIATTAFORMA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, la piattaforma rilevata su cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>Windows</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, la versione rilevata della piattaforma su cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>10_12</td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La prima pagina di destinazione della sessione che ha generato un punto di contatto. Nel sistema di gestione delle relazioni con i clienti è indicato come "Pagina di destinazione".</p>
      </td>
      <td>
        <p>https://info.adobe.com/definitive-guide-to-pipeline-marketing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La prima pagina di destinazione della sessione che ha generato un punto di contatto. Una pagina di destinazione non elaborata conterrà tutti i parametri di query nell’URL. Nel sistema di gestione delle relazioni con i clienti è fatto riferimento a "Landing Page - Raw" (Pagina di destinazione - Non elaborato).</p>
      </td>
      <td>
        <p>https://info.adpbe.com/definitive-guide-to-pipeline-marketing?utm_source=linkedin&amp;utm_medium=Social&amp;utm_campaign=SU_COM_Demand_ Skills&amp;utm_content=DGPM&amp;utm_term=lisu03151846&amp;_bl=66452504</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>In genere, la pagina di destinazione esterna immediatamente prima che l’utente entri sul sito web. Nel sistema di gestione delle relazioni con i clienti è indicato come "Pagina di riferimento".</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>In genere, la pagina di destinazione esterna immediatamente prima che l’utente entri sul sito web. Una pagina di riferimento non elaborata può contenere parametri di query nell’URL. Nel sistema di gestione delle relazioni con i clienti, denominato "Pagina di provenienza - Raw".</p>
      </td>
      <td>
        <p>https://www.linkedin.com/feed</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il primo modulo registrato in una sessione che ha generato un punto di contatto. I successivi invii di moduli non verranno visualizzati nella tabella Punti di contatto, ma nella tabella Form_Submits. Nel sistema di gestione delle relazioni con i clienti viene fatto riferimento a "URL modulo".</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>FORM_PAGE_RAW</td>
      <td>varchar</td>
      <td>Il primo modulo registrato in una sessione che ha generato un punto di contatto. I successivi invii di moduli non verranno visualizzati nella tabella Punti di contatto, ma nella tabella Form_Submits. Una pagina modulo non elaborata può contenere parametri di query nell’URL. Nel sistema di gestione delle relazioni con i clienti viene fatto riferimento a "URL modulo - Non elaborato".</td>
      <td>https://info.adobe.com/demo?hsCtaTracking=98adcc2f-afe2-40c4-9d79-40dcc41663ee%7C3cfaa909-39cb-4f5d-93eb-be05de6b0180</td>
    </tr>
    <tr>
      <td>
        <p>FORM_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di invio del modulo.</p>
      </td>
      <td>
        <p>2017-06-20 01:06:41.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITTÀ</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, la città rilevata in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>New York</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGIONE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, l’area geografica rilevata in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>New York</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAESE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, il paese rilevato in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>Stati Uniti</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIUM</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Utilizzato per definire il mezzo che ha determinato il punto di contatto. Questo può essere analizzato dall’URL da utm_medium. Oppure, se [!DNL Marketo Measure] è in grado di risolvere un annuncio, può trattarsi di valori quali "cpc" o "display".</p>
      </td>
      <td>
        <p>Social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Utilizzato per definire l’origine che ha generato il punto di contatto. Questo può essere analizzato dall'URL da utm_source, in genere impostato come "Campagna CRM" se è stato sincronizzato dal sistema di gestione delle relazioni con i clienti oppure se [!DNL Marketo Measure] è in grado di risolvere un annuncio, potrebbe trattarsi di valori quali "Google AdWords" o "Facebook". Nel sistema di gestione delle relazioni con i clienti è indicato come "Touchpoint Source".</p>
      </td>
      <td>
        <p>LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore che l’utente ha immesso nel browser per cercare e che è finito sul sito web. A seconda delle parole chiave acquistate, questo potrebbe corrispondere o meno alle parole chiave acquistate dalla piattaforma di ricerca a pagamento.</p>
      </td>
      <td>
        <p>attribuzione misura markeot</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La piattaforma di annunci [!DNL Marketo Measure] è stata risolta da, in genere uno dei nostri partner di integrazione.</p>
      </td>
      <td>
        <p>LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account dell’annuncio da cui l’annuncio è stato risolto.</p>
      </td>
      <td>
        <p>li.502664737</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_ACCOUNT</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’account dell’annuncio da cui l’annuncio è stato risolto.</p>
      </td>
      <td>
        <p>MM SC 2016_14605342_3/7-3/31/16</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell'inserzionista dall'account dell'annuncio da cui è stato risolto l'annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_INSERZIONISTA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell'inserzionista dall'account annuncio da cui è stato risolto l'annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Marketo Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del sito dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_SITO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del sito dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>blocco stradale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della campagna dall’account annuncio da cui è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>li.502664737.138949954</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_CAMPAGNA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della campagna dall’account annuncio da cui è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>Account SU - COM - Abilità della domanda</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del gruppo di annunci dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale solo per Google Adwords.</p>
      </td>
      <td>aw.6601259029.317738075.23105327435</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del gruppo di annunci dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale solo per Google AdWords.</p>
      </td>
      <td>Attribuzione marketing - Generale</td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’annuncio dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>dc.6114.8882972.25272734.492579576</td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’annuncio dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>Webinar Budget - barra laterale</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del contenuto creativo dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>li.502664737.138949954.66452504</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_CREATIVO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’elemento creativo dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>lisu03151846</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La prima riga del contenuto creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Generazione lead completata</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La seconda riga del contenuto creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Scarica la guida definitiva al marketing della pipeline: https://lnkd.in/e9xYj5M</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La pagina di destinazione in cui viene fatto clic dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>https://image-store.slidesharecdn.com/d29165c0-1e0b-4ffc-a494-d2c77e7cd4a6-large.jpeg</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il nome URL descrittivo visualizzato nell’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>marektomeasure.com/guide</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della parola chiave acquistata dall’acquisto di Paid Search, estratto dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>__GAId__lisu03151846</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della parola chiave acquistata dall’acquisto di Ricerca a pagamento, estratto dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca)</p>
      </td>
      <td>
        <p>lisu03151846</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Tipo di corrispondenza trovata tra la frase di ricerca e la parola chiave acquistata.</p>
      </td>
      <td>
        <p>Ampia</p>
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
        <p>Se questo punto di contatto viene considerato o meno come il primo contatto del percorso di opportunità.</p>
      </td>
      <td>
        <p>vero</p>
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
        <p>Se questo punto di contatto viene considerato o meno come il contatto di creazione del lead del percorso di opportunità.</p>
      </td>
      <td>
        <p>vero</p>
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
        <p>Se questo punto di contatto viene considerato o meno come il punto di contatto per la creazione di opportunità del percorso di opportunità.</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Se questo punto di contatto viene considerato o meno come il contatto chiuso del percorso di opportunità.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>STAGES_TOUCHED</td>
      <td>varchar</td>
      <td>Questo campo è stato dichiarato obsoleto. Utilizzare le tabelle Stage_Transitions per informazioni sull'area di visualizzazione.</td>
      <td>nulle</td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>booleano</p>
      </td>
      <td>
        <p>Indica se il punto di contatto ha o meno compilato un modulo durante la sessione.</p>
      </td>
      <td>
        <p>vero</p>
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
        <p>Se questo punto di contatto viene considerato o meno come il primo contatto di impression del percorso di opportunità</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMO_CLIC_PERCENTUALE</p>
      </td>
      <td>
        <p>numero(22,19)</p>
      </td>
      <td>
        <p>La percentuale calcolata allocata a questo punto di contatto perché è un primo contatto (vedi Is_First_Touch).</p>
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
        <p>La percentuale calcolata allocata a questo punto di contatto perché è un contatto per la creazione di lead (vedi Is_Lead_Creation_Touch).</p>
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
        <p>Percentuale calcolata allocata a questo punto di contatto perché fa parte di un contatto a forma di U (consultate Is_First_Touch e Is_Lead_Creation_Touch).</p>
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
        <p>Percentuale calcolata allocata a questo punto di contatto perché fa parte di un contatto a forma di w (consultate Is_First_Touch, Is_Lead_Creation_Touch e Is_Opp_Creation_Touch). È previsto 0 poiché si tratta di un BT.</p>
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
        <p>Percentuale calcolata allocata a questo punto di contatto perché fa parte di un modello di percorso completo (consultate Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch). È previsto 0 poiché si tratta di un BT.</p>
      </td>
      <td>
        <p>0</p>
      </td>
    </tr>
    <tr>
      <td>PERCENTUALE_MODELLO_PERSONALIZZATO</td>
      <td>numero(22,19)</td>
      <td>La percentuale calcolata allocata a questo punto di contatto perché fa parte di un modello personalizzato (consultate Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch). È previsto 0 poiché si tratta di un BT.</p>
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
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>numero(38,0)</p>
      </td>
      <td>
        <p>Chiave esterna per la vista Biz_Facts.</p>
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
        <p>numero(38,0)</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ROW_KEY</p>
      </td>
      <td>
        <p>numero(38,0)</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERISER_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CHIAVE_RIGA_SITO</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_URLS {#biz-urls}

Aggregazione di URL da pagine di destinazione, pagine di provenienza e viste pagina.

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
      <td>URL completo,.</td>
      <td>https://www.adobe.com/blog/strategic-marketing-plangoals</td>
    </tr>
    <tr>
      <td>SCHEMA</td>
      <td>varchar</td>
      <td>La comunicazione protetta della pagina web sulla rete.</td>
      <td>https</td>
    </tr>
    <tr>
      <td>HOST</td>
      <td>varchar</td>
      <td>Dominio dell’URL, con eventuali sottodomini.</td>
      <td>www.adobe.com</td>
    </tr>
    <tr>
      <td>PAGE_TITLE</td>
      <td>varchar</td>
      <td>Titolo della pagina.</td>
      <td>Guida CMO al download dell’attribuzione marketing B2B</td>
    </tr>
    <tr>
      <td>PERCORSO</td>
      <td>varchar</td>
      <td>La parte dell’URL che punta a una posizione specifica sull’host.</td>
      <td>/blog/strategic-marketing-plangoals</td>
    </tr>
    <tr>
      <td>PORTA</td>
      <td>varchar</td>
      <td>La porta da un host Internet, facoltativa in un URL.</td>
      <td>584</td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>numero(38,0)</td>
      <td>Chiave esterna per la vista Biz_Facts.</td>
      <td>5686109553536636820</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_USER_TOUCHPOINTS {#biz-user-touchpoints}

Tutti i punti di contatto creati da qualsiasi evento associato a un’e-mail.

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
      <td>
        <p>Un ID univoco per il punto di contatto utente.</p>
      </td>
      <td>
        <p>person@adobe.com_2018-01-05:16-47-02-8803320.ddf67c101f58</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>
        <p>2018-09-05 23:30:53.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>ID della sessione che ha creato il punto di contatto utente.</p>
      </td>
      <td>
        <p>2018-01-05:16-47-02-8803320.ddf67c101f58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_MEMBER_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del membro della campagna che ha creato il punto di contatto utente.</p>
      </td>
      <td>
        <p>00v0Z00001VTgv1QAD</p>
      </td>
    </tr>
    <tr>
      <td>CRM_ACTIVITY_ID</td>
      <td>varchar</td>
      <td>ID dell’attività che ha creato il punto di contatto utente.</td>
      <td>1678625515</td>
    </tr>
    <tr>
      <td>
        <p>CRM_EVENT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’evento che ha creato il punto di contatto utente.</p>
      </td>
      <td>
        <p>00U0Z00000pCZmyUAG</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CRM_TASK_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID per l’attività che ha creato il punto di contatto utente.</p>
      </td>
      <td>
        <p>00T0Z00004Qbd1jUAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IMPRESSION_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’impression che ha creato il punto di contatto utente.</p>
      </td>
      <td>00T0Z00004Qbd1jUAB</td>
    </tr>
    <tr>
      <td>IS_FIRST_KNOWN_TOUCH</td>
      <td>booleano</td>
      <td>Se questo punto di contatto viene considerato o meno come il primo contatto del percorso di opportunità.</td>
      <td>falso</td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>Il primo ID cookie dell’ID visitatore correlato.</td>
      <td>v_36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>DATA_PUNTO DI CONTATTO</p>
      </td>
      <td>timestamp_ntz</td>
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
      <td>varchar</td>
      <td>
        <p>Tipo di attività, visita Web, modulo Web, chat Web, telefonata, campagna [CRM] o attività [CRM]. Nel sistema di gestione delle relazioni con i clienti è indicato come "Tipo di punto di contatto".</p>
      </td>
      <td>
        <p>Modulo web</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CANALE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il canale in cui rientra il punto di contatto, come definito nelle definizioni di canale personalizzate all'interno dell'app [!DNL Marketo Measure]. Nel sistema di gestione delle relazioni con i clienti, denominato "Canale di marketing - Percorso".</p>
      </td>
      <td>
        <p>Social.LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_BROWSER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, il browser rilevato su cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>Firefox</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, la versione del browser rilevato su cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>33</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_PIATTAFORMA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, la piattaforma rilevata su cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>Mac</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, la versione rilevata della piattaforma su cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>10_12</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La prima pagina di destinazione della sessione che ha generato un punto di contatto. Nel sistema di gestione delle relazioni con i clienti è indicato come "Pagina di destinazione".</p>
      </td>
      <td>
        <p>https://www.adobe.com/blog/budget-and-planning-maturity-model-b2b-marketing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La prima pagina di destinazione della sessione che ha generato un punto di contatto. Una pagina di destinazione non elaborata conterrà tutti i parametri di query nell’URL. Nel sistema di gestione delle relazioni con i clienti è fatto riferimento a "Landing Page - Raw" (Pagina di destinazione - Non elaborato).</p>
      </td>
      <td>
        <p>https://www.adobe.com/blog/budget-and-planning-maturity-model-b2b-marketing?utm_source=feedburner&amp;utm_medium=feed&amp;utm_campaign=Feed%3A+ marketo+%measure%27s+Pipeline+Marketing+Blog%29</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>In genere, la pagina di destinazione esterna immediatamente prima che l’utente entri sul sito web. Nel sistema di gestione delle relazioni con i clienti è indicato come "Pagina di riferimento".</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>In genere, la pagina di destinazione esterna immediatamente prima che l’utente entri sul sito web. Una pagina di riferimento non elaborata può contenere parametri di query nell’URL. Nel sistema di gestione delle relazioni con i clienti, denominato "Pagina di provenienza - Raw".</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il primo modulo registrato in una sessione che ha generato un punto di contatto. Gli invii di moduli successivi non verranno visualizzati nella tabella Attribution_Touchpoints, ma nella tabella Form_Submits. Nel sistema di gestione delle relazioni con i clienti viene fatto riferimento a "URL modulo".</p>
      </td>
      <td>
        <p>http://info.adobe.com/adwords-for-lead-generation</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il primo modulo registrato in una sessione che ha generato un punto di contatto. Gli invii di moduli successivi non verranno visualizzati nella tabella Attribution_Touchpoints, ma nella tabella Form_Submits. Una pagina modulo non elaborata può contenere parametri di query nell’URL. Nel sistema di gestione delle relazioni con i clienti viene fatto riferimento a "URL modulo - Non elaborato".</p>
      </td>
      <td>
        <p>http://info.adobe.com/adwords-for-lead-generation?utm_source=linkedin&amp;utm_medium=paid&amp;utm_content=sfskill&amp;utm _campaign=Content%20-%20AdWords%20Guida</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data di invio del modulo.</p>
      </td>
      <td>
        <p>03/06/2015 17:49:10.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITTÀ</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, la città rilevata in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>Oakland</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGIONE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, l’area geografica rilevata in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>California</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAESE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Dall’indirizzo JavaScript e IP, il paese rilevato in cui si trovava l’utente durante la sessione.</p>
      </td>
      <td>
        <p>Stati Uniti</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIUM</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Utilizzato per definire il mezzo che ha determinato il punto di contatto. Questo può essere analizzato dall’URL da utm_medium. Oppure, se [!DNL Marketo Measure] è in grado di risolvere un annuncio, può trattarsi di valori quali "cpc" o "display".</p>
      </td>
      <td>
        <p>pagato</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Utilizzato per definire l’origine che ha generato il punto di contatto. Questo può essere analizzato dall'URL da utm_source, in genere impostato come "Campagna CRM" se è stato sincronizzato dal sistema di gestione delle relazioni con i clienti oppure se [!DNL Marketo Measure] è in grado di risolvere un annuncio, potrebbe trattarsi di valori quali "Google AdWords" o "Facebook". Nel sistema di gestione delle relazioni con i clienti è indicato come "Touchpoint Source".</p>
      </td>
      <td>
        <p>linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il valore che l’utente ha immesso nel browser per cercare e che è finito sul sito web. A seconda delle parole chiave acquistate, questo potrebbe corrispondere o meno alle parole chiave acquistate dalla piattaforma di ricerca a pagamento.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La piattaforma di annunci [!DNL Marketo Measure] è stata risolta da, in genere uno dei nostri partner di integrazione.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell’account dell’annuncio da cui l’annuncio è stato risolto.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_ACCOUNT</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’account dell’annuncio da cui l’annuncio è stato risolto.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Account</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID dell'inserzionista dall'account dell'annuncio da cui è stato risolto l'annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_INSERZIONISTA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell'inserzionista dall'account annuncio da cui è stato risolto l'annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Marketing analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del sito dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_SITO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del sito dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome del posizionamento dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo si applica solo a Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>blocco stradale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della campagna dall’account annuncio da cui è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>aw.6601259029.208548635</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_CAMPAGNA</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della campagna dall’account annuncio da cui è stato risolto l’annuncio.</p>
      </td>
      <td>
        <p>Marchio</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del gruppo di annunci dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale solo per Google Adwords.</p>
      </td>
      <td>
        <p>aw.6601259029.208548635.16750166675</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
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
      <td>varchar</td>
      <td>
        <p>ID dell’annuncio dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>dc.6114.8882972.25272734.492579576</td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’annuncio dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Doubleclick Campaign Manager e Facebook (visualizzazione).</p>
      </td>
      <td>Webinar Budget - barra laterale</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID del contenuto creativo dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>aw.6601259029.208548635.16750166675.195329631298</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NOME_CREATIVO</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome dell’elemento creativo dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Sito ufficiale</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La prima riga del contenuto creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Pianificazione ricavi e attribuzione</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La seconda riga del contenuto creativo dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>Scopri perché più di 250 aziende scelgono [!DNL Marketo Measure] per l’attribuzione marketing. Prendi una demo!</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>La pagina di destinazione in cui viene fatto clic dall’annuncio di ricerca, estratto dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>http://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Il nome URL descrittivo visualizzato nell’annuncio di ricerca, estratto dall’account dell’annuncio da cui l’annuncio è stato risolto. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>ID della parola chiave acquistata dall’acquisto di Paid Search, estratto dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca).</p>
      </td>
      <td>
        <p>aw.6601259029.208548635.16750166675.46267805426</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Nome della parola chiave acquistata dall’acquisto di Ricerca a pagamento, estratto dall’account dell’annuncio da cui è stato risolto l’annuncio. Questo vale per Google AdWords e Bing Ads (ricerca)</p>
      </td>
      <td>
        <p>[marketo]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Tipo di corrispondenza trovata tra la frase di ricerca e la parola chiave acquistata.</p>
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
        <p>Indica se il punto di contatto ha o meno compilato un modulo durante la sessione.</p>
      </td>
      <td>
        <p>vero</p>
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
        <p>Se questo punto di contatto viene considerato o meno come il primo contatto di impression del percorso di opportunità.</p>
      </td>
      <td>
        <p>falso</p>
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
        <p>Indica se il punto di contatto viene eliminato o meno.</p>
      </td>
      <td>
        <p>falso</p>
      </td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>numero(38,0)</td>
      <td>Chiave esterna per la vista Biz_Facts.</td>
      <td>-5269090762570690000</td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERISER_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CHIAVE_RIGA_SITO</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>numero(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_WEB_HOST_MAPPINGS {#biz-web-host-mappings}

Mappatura della tabella per mappare l&#39;ID sessione [!DNL Marketo Measure] all&#39;ID Adobe ECID e Munckin.

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
      <td>Un ID univoco per il record di mappatura.</td>
      <td>
        <p>0d643578c0c74753eff91abe668ed328|2020-06-17:19:03:36|0002|0|568668</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>ID cookie registrato da [!DNL Marketo Measure].</td>
      <td>0d643578c0c74753eff91abe668ed328</td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>varchar</td>
      <td>Il primo ID cookie dell’ID visitatore correlato.</td>
      <td>v_0d643578c0c74753eff91abe668ed328</td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>varchar</td>
      <td>ID sessione [!DNL Marketo Measure].</td>
      <td>2018-08-06:01-35-24-1231230.9bc63c34482f</td>
    </tr>
    <tr>
      <td>
        <p>DATA_EVENTO</p>
      </td>
      <td>timestamp_ntz</td>
      <td>Data di registrazione della mappatura.</td>
      <td>
        <p>2020-06-17 19:03:36.000</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Data dell’ultima modifica del record.</p>
      </td>
      <td>
        <p>2020-06-17 19:03:36.000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE</td>
      <td>varchar</td>
      <td>URL della visualizzazione Pagina, senza parametri di query.</td>
      <td>
        <p>https://learn.atest.com/simplify-retention-starter-kit.html</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_RAW</td>
      <td>varchar</td>
      <td>URL della visualizzazione pagina, inclusi eventuali parametri di query.</td>
      <td>
        <p>https://learn.atest.com/simplify-retention-starter-kit.html?x=nGfrBF&amp;utm_medium=cpc&amp;utm_source=intensify</p>
      </td>
    </tr>
    <tr>
      <td>INDIRIZZO_IP</td>
      <td>varchar</td>
      <td>Indirizzo IP registrato.</td>
      <td>
        <p>159 203 142 127</p>
      </td>
    </tr>
    <tr>
      <td>TIPO</td>
      <td>varchar</td>
      <td>Indica il tipo di evento.</td>
      <td>
        <p>MappaturaHost</p>
      </td>
    </tr>
    <tr>
      <td>USER_AGENT_STRING</td>
      <td>varchar</td>
      <td>Periferica e browser registrati al momento della visualizzazione della pagina.</td>
      <td>
        <p>Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, come Gecko) Chrome/79.0.3945.130 Safari/537.36</p>
      </td>
    </tr>
    <tr>
      <td>CLIENT_SEQUENCE</td>
      <td>varchar</td>
      <td>Indica l'ordine in cui si è verificata la visualizzazione pagina nella sessione.</td>
      <td>2</td>
    </tr>
    <tr>
      <td>CLIENT_RANDOM</td>
      <td>varchar</td>
      <td>Utilizzato per l’audit e l’elaborazione interna.</td>
      <td>566868</td>
    </tr>
    <tr>
      <td>IS_DUPLICATED</td>
      <td>booleano</td>
      <td>Indica se il record è considerato un duplicato.</td>
      <td>falso</td>
    </tr>
    <tr>
      <td>IS_PROCESSED</td>
      <td>booleano</td>
      <td>Utilizzato per l’elaborazione interna.</td>
      <td>vero</td>
    </tr>
    <tr>
      <td>MAPPING_TYPE</td>
      <td>varchar</td>
      <td>Tipo di ID mappato all'ID cookie [!DNL Marketo Measure].</td>
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
      <td>Adobe di ECID per l’ID organizzazione specificato.</td>
      <td>09860926390077352923264316157493772857</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data di creazione del record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data dell’ultima modifica apportata al record nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Data in cui il record è stato contrassegnato come eliminato nel Snowflake.</td>
      <td>01/01/2020 01 :01:00.000</td>
    </tr>
  </tbody>
</table>

## Query di esempio {#sample-queries}

**Quanti punti di contatto dell&#39;acquirente (BT) erano presenti il mese scorso per ogni canale/sottocanale?**

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

**Quanto Reddito Attribuito per ogni canale è stato chiuso nell&#39;ultimo mese, per il modello di attribuzione del percorso completo?**

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

**Qual è l&#39;intero percorso per una persona?  (Mostra tutti i punti di contatto per un singolo indirizzo e-mail.)**

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

**Mostra tutti i punti di contatto di attribuzione dell&#39;acquirente (BAT) e i relativi ricavi attribuiti per una singola opportunità.**

>[!NOTE]
>
>Questa query restituisce ricavi attribuiti per il modello di forma w. Modifica il modello aggiornando il campo nel calcolo dei ricavi attribuiti.

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
