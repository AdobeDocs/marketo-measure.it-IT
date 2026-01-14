---
description: Integrazione di [!DNL Marketo Engage] persone - [!DNL Marketo Measure]
title: Integrazione di [!DNL Marketo Engage] persone
exl-id: 51930e84-4ff8-4e35-9d44-ea017c24b051
feature: Integration
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 0%

---

# Integrazione di [!DNL Marketo Engage] persone {#marketo-engage-people-integration}

L&#39;integrazione Marketo People consente a [!DNL Marketo Measure] di iniziare a scaricare persone da Marketo e di collegare le sessioni tracciate all&#39;utente e mappare i punti di contatto ai suoi impegni. Storicamente, [!DNL Marketo Measure] era in grado di mappare punti di contatto solo per una persona del CRM, quindi questo aiuta gli addetti al marketing a misurare le loro attività di marketing prima di aspettare una fase o un trigger per sincronizzarlo con il CRM.

## Requisiti {#requirements}

* Istanza Marketo di produzione
* Istanza [!DNL Salesforce] o [!DNL Microsoft Dynamics] di produzione
* Qualsiasi abbonamento a [!DNL Marketo Measure] a pagamento
* Solr abilitato (contattare il [supporto Marketo](https://nation.marketo.com/t5/Support/ct-p/Support) per attivare questa funzione)

## Come funziona {#how-it-works}

In qualità di cliente corrente, [!DNL Marketo Measure] sta già scaricando persone dal tuo CRM. Il processo standard prevede che [!DNL Marketo Measure] scarichi le persone e mappi l&#39;indirizzo e-mail a una sessione Web tracciata tramite bizible.js.

Con l&#39;introduzione del download delle persone di Marketo, [!DNL Marketo Measure] è ora in grado di mappare le sessioni Web su un pool più ampio di persone, quelle che non sono state sincronizzate con il sistema CRM. Di solito questo accade a causa di processi interni che attendono che le persone raggiungano un determinato stato prima di essere inviate al sistema CRM.

Quando [!DNL Marketo Measure] esegue correttamente il mapping della persona Marketo a una sessione Web, l&#39;elaborazione genererà eventuali punti di contatto rilevanti per la persona, che verranno infine segnalati in [!DNL Marketo Measure Discover]. Se la persona Marketo viene inviata al CRM, [!DNL Marketo Measure] gestirà lo scenario duplicato e ricreerà il punto di contatto per la persona CRM e contrassegnerà il set iniziale come &quot;duplicato&quot;.

Per rilevare questi duplicati, assicurati che la sincronizzazione di [!DNL Marketo-Salesforce] o [!DNL Marketo-Dynamics] stia popolando gli ID lead e contatto nella persona Marketo. Se l’ID viene sincronizzato correttamente, dovresti essere in grado di visualizzare l’ID del sistema di gestione delle relazioni con i clienti nel record Persona, come segue:

![Per rilevare questi duplicati, assicurati che il tuo](assets/marketo-engage-programs-06.png)

![Per rilevare questi duplicati, assicurati che il tuo](assets/marketo-engage-programs-07.png)

I clienti hanno la possibilità di segnalare l&#39;intero set di persone Marketo e CRM all&#39;interno di [!DNL Marketo Measure] Discover. Se sei interessato a generare rapporti solo sulle persone CRM, ti consigliamo di creare un segmento per filtrarle.

## [!DNL Marketo Measure Discover] {#marketo-measure-discover}

Quando esegui il reporting sui lead (persone) in [!DNL Marketo Measure Discover], visualizzerai il totale dei lead Marketo e CRM. Per creare rapporti solo sulle persone Marketo o solo sui lead CRM, dovrai creare una categoria di segmenti per la tua origine, quindi creare regole di segmenti per Marketo e CRM utilizzando il campo &quot;Sistema Source&quot; per definire la regola. Una volta creati i segmenti, sarà disponibile la categoria Source per filtrare le dashboard di [!DNL Marketo Measure Discover].

![La generazione di rapporti sui lead (persone) in Marketo Measure Discover](assets/bizible-discover-1.png)

![La generazione di rapporti sui lead (persone) in Marketo Measure Discover](assets/bizible-discover-2.png)

## Mappature campi {#field-mappings}

<table>
 <colgroup>
  <col>
  <col>
 </colgroup>
 <tbody>
  <tr>
   <th><p><strong>biz_lead</strong></p></th>
   <th><p><strong>Marketo</strong></p></th>
  </tr>
  <tr>
   <td><p>ID</p></td>
   <td><p>id</p></td>
  </tr>
  <tr>
   <td><p>MODIFIED_DATE</p></td>
   <td><p>updatedAt<strong>*</strong></p></td>
  </tr>
  <tr>
   <td><p>DATA_CREAZIONE</p></td>
   <td><p>createdAt</p></td>
  </tr>
  <tr>
   <td><p>EMAIL</p></td>
   <td><p>e-mail</p></td>
  </tr>
  <tr>
   <td><p>SITO_WEB</p></td>
   <td><p>sito web</p></td>
  </tr>
  <tr>
   <td><p>AZIENDA</p></td>
   <td><p>azienda</p></td>
  </tr>
  <tr>
   <td><p>IS_CONVERTED</p></td>
   <td><p>n/d</p></td>
  </tr>
  <tr>
   <td><p>ACCOUNT_ID</p></td>
   <td><p>ID account (L2A)</p></td>
  </tr>
  <tr>
   <td><p>BIZIBLE_STAGE</p></td>
   <td><p>Stato</p></td>
  </tr>
  <tr>
   <td><p>IS_DELETED</p></td>
   <td><p>true/false</p></td>
  </tr>
 </tbody>
</table>

*Esiste un problema di comportamento noto in cui i campi dell&#39;entità Marketo Company non influiscono sul valore updateAt della persona, pertanto se vengono aggiornati campi rilevanti come Sito Web o Azienda, [!DNL Marketo Measure] non saprà che tali valori sono stati modificati perché il valore updateAt data/ora non è aggiornato. Questo influisce sulla funzione ABM, in cui non avremmo dati aggiornati per risolvere l’account per il lead. Al momento non esiste una soluzione alternativa, ma si prevede di affrontarla in futuro.

## Domande frequenti {#faq}

**Perché i conteggi dei lead differiscono tra il sistema di gestione delle relazioni con i clienti e [!DNL Marketo Measure Discover]?**

Poiché questa integrazione ci consente di creare punti di contatto per i lead importati direttamente da Marketo, potrebbero esserci lead che non sono stati sincronizzati con il sistema di gestione delle relazioni con i clienti, pertanto il conteggio all’interno di Discover potrebbe essere più alto di quello del sistema di gestione delle relazioni con i clienti, in quanto i punti di contatto vengono inviati solo per i lead di gestione delle relazioni con i clienti.

**In che modo vengono sostituiti i dati?**

Questa integrazione unisce effettivamente i set di dati all&#39;interno dell&#39;istanza [!DNL Marketo Measure] corrente, quindi non viene sostituito nulla. Quello che ci aspetteremmo dai tuoi lead CRM correnti è che quando scaricassimo il valore di 2 anni di lead Marketo, semplicemente aggiorneremmo quel record di lead per mostrare che c&#39;è stata anche una corrispondenza con un lead Marketo. Che tutto accada nel backend e che i punti di contatto rimangano gli stessi. Ci aspetteremmo inoltre di vedere più punti di contatto a causa dei lead Marketo idonei. Se riusciamo a trovare sessioni Web corrispondenti a quelle di Marketo, inizieremo a visualizzare i punti di contatto conteggiati in [!DNL Marketo Measure].

**È possibile scaricare solo persone personali da Marketo e interrompere la connessione CRM?**

In questo momento, no. Questa opzione sarà disponibile in futuro, ma è necessario creare altre fasi dell&#39;integrazione di Marketo in modo da collegare i programmi, le opportunità e le offerte da Marketo a [!DNL Marketo Measure].

**Importi TUTTI i miei utenti di Marketo?**

Al momento, la prima persona che importeremo è dal 1/1/2018 in modo che abbiamo un minimo di 2 anni di dati, che è lo stesso comportamento che applichiamo dai download CRM. Implementeremo un comportamento migliorato per scaricare una finestra continua di 2 anni una volta stabilita la connessione Marketo.

Inoltre, non filtra per nessun tipo di persone, quindi tutte le persone nella finestra di due anni verranno importate e saranno idonee per i punti di contatto.

**Cos&#39;è SOLR e perché devo abilitarlo per usare questa funzione?**

L&#39;abilitazione di SOLR per l&#39;istanza Marketo è un passaggio insignificante che apre spazio hardware in Marketo in modo che la sottoscrizione possa utilizzare l&#39;integrazione di [!DNL Marketo Measure]. Se la funzione SOLR non è abilitata, non abbiamo accesso a determinate chiamate che altrimenti ci consentirebbero di scaricare le persone appropriate dalla tua istanza di Marketo.
