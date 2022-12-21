---
unique-page-id: 37356395
description: "[!DNL Marketo Engage] Integrazione delle persone - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Engage] Integrazione delle persone"
exl-id: 51930e84-4ff8-4e35-9d44-ea017c24b051
source-git-commit: 54337a0a65b79d80ebeae6531f5e92f4f48721a7
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 0%

---

# [!DNL Marketo Engage] Integrazione delle persone {#marketo-engage-people-integration}

L&#39;integrazione Marketo People consente [!DNL Marketo Measure] per iniziare a scaricare persone da Marketo e iniziare a collegare le loro sessioni tracciate al singolo utente e mappare i punti di contatto ai loro impegni. Storicamente, [!DNL Marketo Measure] è stato in grado di mappare solo i punti di contatto a una persona dal CRM, pertanto questo aiuta gli esperti di marketing a misurare le proprie attività di marketing prima che aspettare uno stadio o un trigger per sincronizzarlo con il CRM.

## Requisiti {#requirements}

* Istanza Marketo di produzione
* Produzione [!DNL Salesforce] o [!DNL Microsoft Dynamics] istanza
* Qualsiasi pagamento [!DNL Marketo Measure] abbonamento
* SOLR abilitato (contattare [Supporto Marketo](https://nation.marketo.com/t5/Support/ct-p/Support) per abilitare questa opzione)

## Come funziona {#how-it-works}

Come cliente attuale, [!DNL Marketo Measure] sta già scaricando persone dal tuo CRM. Il processo standard è che [!DNL Marketo Measure] scarica le persone e mappa l’indirizzo e-mail a una sessione web che abbiamo monitorato tramite bizible.js.

Con l&#39;introduzione di scaricare persone Marketo, [!DNL Marketo Measure] è ora in grado di mappare le sessioni web a un pool più ampio di utenti, quelli che non sono stati sincronizzati con il CRM. Questo accade solitamente a causa di processi interni che attendono che le persone raggiungano un certo stato prima di essere inviate al CRM.

Quando [!DNL Marketo Measure] mappa con successo la persona Marketo a una sessione web, la nostra elaborazione genererà qualsiasi punto di contatto pertinente per essa, che sono in ultima analisi segnalabili in [!DNL Marketo Measure Discover]. Se la persona Marketo viene spinta al CRM, [!DNL Marketo Measure] gestisce lo scenario duplicato e ricreerà il punto di contatto per la persona CRM e contrassegnerà il set iniziale come &quot;duplicato&quot;.

Per poter rilevare questi duplicati, assicurati che [!DNL Marketo-Salesforce] o [!DNL Marketo-Dynamics] La sincronizzazione sta popolando gli ID lead e contatti sulla persona Marketo. Se l&#39;ID si sincronizza correttamente, dovresti essere in grado di visualizzare l&#39;ID CRM nel record Persona, come riportato di seguito:

![](assets/5a.png)

![](assets/5b.png)

I clienti possono scegliere di segnalare l&#39;intero set di persone Marketo e di persone CRM all&#39;interno di [!DNL Marketo Measure] Scoprite. Se sei interessato a generare rapporti solo sulle persone CRM, ti consigliamo di creare un segmento per filtrarli.

## [!DNL Marketo Measure Discover] {#marketo-measure-discover}

Quando si riferiscono a lead (persone) in [!DNL Marketo Measure Discover], vedrai il totale dei lead Marketo e CRM. Per creare rapporti solo sulle persone Marketo o solo sui lead CRM, vuoi creare una categoria di segmenti per la tua origine, quindi creare regole di segmento per Marketo e CRM utilizzando il campo &quot;Sistema sorgente&quot; per definire la regola. Una volta creati i segmenti, visualizzerai la categoria Origine disponibile per filtrare tra i tuoi [!DNL Marketo Measure Discover] dashboard.

![](assets/bizible-discover-1.png)

![](assets/bizible-discover-2.png)

## Mappature dei campi {#field-mappings}

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
   <td><p>updateAt<strong>*</strong></p></td> 
  </tr> 
  <tr> 
   <td><p>CREATED_DATE</p></td> 
   <td><p>createdAt</p></td> 
  </tr> 
  <tr> 
   <td><p>E-MAIL</p></td> 
   <td><p>e-mail</p></td> 
  </tr> 
  <tr> 
   <td><p>WEB_SITE</p></td> 
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

*Esiste un problema comportamentale noto in cui i campi dell&#39;entità Società Marketo non influiscono sul valore aggiornato della PersonaAt, quindi se i campi rilevanti come Sito Web o Società vengono aggiornati, [!DNL Marketo Measure] non saprà che tali valori vengono modificati perché il valore data/ora aggiornato non viene aggiornato. Questo influisce sulla funzione ABM, che non dispone di nuovi dati per risolvere l’Account per il lead. Non c&#39;è soluzione al momento, ma ci sono piani per affrontare questo problema in futuro.

## Domande frequenti {#faq}

**Perché i conteggi dei lead differiscono tra CRM e [!DNL Marketo Measure Discover]?**

Poiché questa integrazione ci consente di creare punti di contatto per i lead che abbiamo importato direttamente da Marketo, potrebbero esserci lead che non sono stati sincronizzati con il CRM, pertanto il conteggio all’interno di Discover potrebbe essere superiore al CRM, in quanto i punti di contatto vengono inviati solo per i lead CRM.

**In che modo questi sostituiscono i miei dati?**

Questa integrazione unisce effettivamente i set di dati all’interno dell’attuale [!DNL Marketo Measure] istanza in modo che non venga sostituito nulla. Ciò che ci aspetteremmo dai vostri attuali lead CRM è che quando scarichiamo il valore di 2 anni di Marketo Leads, aggiorneremmo semplicemente quel record Lead per dimostrare che c&#39;era anche una corrispondenza con un lead Marketo. Tutto questo avviene nel backend e i punti di contatto dovrebbero rimanere gli stessi. Ci aspetteremmo anche di vedere più punti di contatto a causa dei Marketo Leads idonei. Se riusciamo a trovare sessioni web abbinate a quelle persone di Marketo, inizieremo a vedere i punti di contatto conteggiati in [!DNL Marketo Measure].

**Posso scaricare solo le mie persone da Marketo e interrompere la connessione CRM?**

Al momento, no. Avremo questa opzione in futuro, ma dobbiamo sviluppare altre fasi di questa integrazione Marketo in modo da collegare i programmi, le opportunità e le offerte da Marketo a [!DNL Marketo Measure].

**Importa TUTTI i miei Marketo?**

Al momento, il più presto importeremo persone a partire dall’1/1/2018 in modo da avere un minimo di 2 anni di dati, che è lo stesso comportamento che applichiamo dai download CRM. Implementeremo un comportamento migliorato per scaricare una finestra continua di 2 anni dopo che la connessione Marketo è stata stabilita.

Inoltre, non viene applicato alcun filtro per i tipi di persone, pertanto tutte le persone all’interno della finestra di due anni verranno importate e possono essere utilizzate per i punti di contatto.

**Cos&#39;è SOLR e perché ho bisogno che sia abilitato per utilizzare questa funzione?**

Abilitare SOLR per la tua istanza Marketo è un passaggio banale che apre spazio hardware in Marketo in modo che l&#39;abbonamento possa utilizzare il [!DNL Marketo Measure] integrazione. Senza SOLR abilitato, non abbiamo accesso a determinate chiamate che altrimenti ci permetterebbero di scaricare le persone appropriate dalla tua istanza Marketo.
