---
unique-page-id: 37356395
description: "[!DNL Marketo Engage] Integrazione delle persone - [!DNL Marketo Measure]"
title: "[!DNL Marketo Engage] Integrazione delle persone"
exl-id: 51930e84-4ff8-4e35-9d44-ea017c24b051
feature: Integration
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 1%

---

# [!DNL Marketo Engage] Integrazione delle persone {#marketo-engage-people-integration}

L&#39;integrazione Marketo People consente [!DNL Marketo Measure] per iniziare a scaricare persone da Marketo e iniziare a collegare le loro sessioni tracciate all&#39;individuo e mappare i punti di contatto ai loro impegni. Storicamente, [!DNL Marketo Measure] È stato in grado di mappare i punti di contatto solo per una persona dal sistema CRM, in modo da aiutare gli addetti al marketing a misurare le loro attività di marketing prima di aspettare una fase o un trigger per sincronizzarla con il sistema CRM.

## Requisiti {#requirements}

* Istanza Marketo di produzione
* Produzione [!DNL Salesforce] o [!DNL Microsoft Dynamics] istanza
* Qualsiasi pagamento effettuato [!DNL Marketo Measure] abbonamento
* SOLR abilitato (raggiungere [Supporto Marketo](https://nation.marketo.com/t5/Support/ct-p/Support) per abilitare questa funzione)

## Come funziona {#how-it-works}

In qualità di cliente attuale, [!DNL Marketo Measure] sta già scaricando persone dal tuo CRM. Il processo standard è quello [!DNL Marketo Measure] scarica le persone e mappa l’indirizzo e-mail su una sessione web tracciata tramite bizible.js.

Con l&#39;introduzione del download di persone Marketo, [!DNL Marketo Measure] è ora in grado di mappare le sessioni web su un pool più ampio di singoli utenti, quelli che non sono stati sincronizzati con il sistema CRM. Di solito questo accade a causa di processi interni che attendono che le persone raggiungano un determinato stato prima di essere inviate al sistema CRM.

Quando [!DNL Marketo Measure] mappa con successo la persona Marketo su una sessione web; la nostra elaborazione genererà eventuali punti di contatto pertinenti per essa, che sono infine segnalabili in [!DNL Marketo Measure Discover]. Se la persona Marketo viene inviata al CRM, [!DNL Marketo Measure] Gestirà lo scenario duplicato e ricreeremo il punto di contatto per la persona del sistema di gestione delle relazioni con i clienti e contrassegneremo il set iniziale come &quot;duplicato&quot;.

Per rilevare questi duplicati, assicurati che il tuo [!DNL Marketo-Salesforce] o [!DNL Marketo-Dynamics] La sincronizzazione sta popolando gli ID lead e contatto nella persona Marketo. Se l’ID viene sincronizzato correttamente, dovresti essere in grado di visualizzare l’ID del sistema di gestione delle relazioni con i clienti nel record Persona, come segue:

![](assets/5a.png)

![](assets/5b.png)

I clienti hanno la possibilità di segnalare l’intero set di persone Marketo e CRM all’interno di [!DNL Marketo Measure] Scopri. Se sei interessato a generare rapporti solo sulle persone CRM, ti consigliamo di creare un segmento per filtrarle.

## [!DNL Marketo Measure Discover] {#marketo-measure-discover}

Quando si generano rapporti sui lead (persone) in [!DNL Marketo Measure Discover], visualizzerai il totale dei lead Marketo e CRM. Per creare rapporti solo sulle persone Marketo o solo sui lead CRM, dovrai creare una categoria di segmenti per la tua origine, quindi creare regole di segmenti per Marketo e CRM utilizzando il campo &quot;Sistema di origine&quot; per definire la regola. Una volta creati i segmenti, vedrai la categoria Origine disponibile per filtrare in base al [!DNL Marketo Measure Discover] dashboard.

![](assets/bizible-discover-1.png)

![](assets/bizible-discover-2.png)

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

*È noto un problema comportamentale in cui i campi dell’entità Marketo Company non influiscono sul valore updateAt della persona, quindi se vengono aggiornati campi rilevanti come Sito web o Azienda, [!DNL Marketo Measure] non è a conoscenza del fatto che tali valori vengono modificati perché il valore di data/ora updateAt non è aggiornato. Questo influisce sulla funzione ABM, in cui non avremmo dati aggiornati per risolvere l’account per il lead. Al momento non esiste una soluzione alternativa, ma si prevede di affrontarla in futuro.

## Domande frequenti {#faq}

**Perché i conteggi dei lead differiscono tra il sistema CRM e [!DNL Marketo Measure Discover]?**

Poiché questa integrazione ci consente di creare punti di contatto per i lead importati direttamente da Marketo, potrebbero esserci lead che non sono stati sincronizzati con il sistema di gestione delle relazioni con i clienti, pertanto il conteggio all’interno di Discover potrebbe essere più alto di quello del sistema di gestione delle relazioni con i clienti, in quanto i punti di contatto vengono inviati solo per i lead di gestione delle relazioni con i clienti.

**In che modo questo sostituirà i miei dati?**

Questa integrazione unisce effettivamente i set di dati all’interno del [!DNL Marketo Measure] così nulla viene sostituito. Quello che ci aspetteremmo dai tuoi lead CRM correnti è che quando scaricassimo il valore di 2 anni di lead Marketo, semplicemente aggiorneremmo quel record di lead per mostrare che c&#39;è stata anche una corrispondenza con un lead Marketo. Che tutto accada nel backend e che i punti di contatto rimangano gli stessi. Ci aspetteremmo inoltre di vedere più punti di contatto a causa dei lead Marketo idonei. Se riusciamo a trovare sessioni web che corrispondano a quelle di Marketo, inizieremo a vedere i punti di contatto conteggiati in [!DNL Marketo Measure].

**È possibile scaricare da Marketo solo persone personali e interrompere la connessione CRM?**

In questo momento, no. Avremo questa opzione in futuro, ma dobbiamo sviluppare altre fasi di questa integrazione Marketo in modo da collegare i programmi, le opportunità e gli accordi di Marketo a [!DNL Marketo Measure].

**Importa TUTTI i miei Marketo?**

Al momento, la prima persona che importeremo è dal 1/1/2018 in modo che abbiamo un minimo di 2 anni di dati, che è lo stesso comportamento che applichiamo dai download CRM. Implementeremo un comportamento migliorato per scaricare una finestra continua di 2 anni una volta stabilita la connessione Marketo.

Inoltre, non filtra per nessun tipo di persone, quindi tutte le persone nella finestra di due anni verranno importate e saranno idonee per i punti di contatto.

**Cos&#39;è la funzione SOLR e perché è necessario che sia abilitata per l&#39;utilizzo di questa funzione?**

L&#39;abilitazione di SOLR per l&#39;istanza Marketo è un passaggio insignificante che apre spazio hardware in Marketo in modo che l&#39;abbonamento possa utilizzare [!DNL Marketo Measure] integrazione. Se la funzione SOLR non è abilitata, non abbiamo accesso a determinate chiamate che altrimenti ci consentirebbero di scaricare le persone appropriate dalla tua istanza di Marketo.
