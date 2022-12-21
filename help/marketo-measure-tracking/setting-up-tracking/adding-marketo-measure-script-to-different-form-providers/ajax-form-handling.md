---
unique-page-id: 18874745
description: Gestione dei moduli AJAX - [!DNL Marketo Measure] - Documentazione del prodotto
title: Gestione dei moduli AJAX
exl-id: 042e42ff-d8d9-4380-b878-aba4934bc4a0
source-git-commit: ae5b77744d523606ce6cfcf48d7e8d5049d5ccb7
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Gestione dei moduli AJAX {#ajax-form-handling}

Per segnalare manualmente le conversioni dei clienti in [!DNL Marketo Measure], abbiamo fornito un’API molto semplice da utilizzare. Entrambe queste API Javascript sono automaticamente disponibili sul tuo sito, se hai il nostro codice di tracciamento su di esso. Non è necessario fare nulla di speciale per accedervi.

## Scenario 1 - Modulo HTML con un AJAX inviato {#scenario-html-form-with-an-ajax-submit}

Quando si utilizzano moduli contenenti AJAX (o un altro meccanismo) per inviare le date di conversione dal client ai nostri server, [!DNL Marketo Measure] potrebbero non essere a conoscenza della conversione del cliente attraverso uno dei percorsi standard monitorati. In questo scenario, possiamo sfruttare una semplice API (fornita di seguito).

Se gestisci gli invii del modulo, puoi chiamare esplicitamente [!DNL Marketo Measure] da Javascript. [!DNL Marketo Measure] raccoglie tutte le informazioni pertinenti dal modulo e le pubblica in modo asincrono sui nostri server.

**Di seguito è riportato un esempio di codice che utilizza JQuery (partendo dal presupposto che l’ID sul modulo sia &quot;formId&quot;):**

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// Give Marketo Measure the JQuery Selector for the form and we'll collect the data automatically.  
Bizible.Push('Form',$('#*formId*'));
```

**Di seguito è riportato un esempio di codice che non utilizza JQuery (partendo dal presupposto che l’ID sul modulo sia &quot;formId&quot;):**

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// Give Marketo Measure the Form ID and we'll collect the data automatically.
Bizible.Push('Form','MyFormID');
```

## Scenario 2 - Informazioni lead raccolte in un modulo non HTML {#scenario-lead-information-collected-in-a-non-html-form}

Se le informazioni provenienti da un lead convertito vengono raccolte utilizzando campi di testo Javascript o semplici senza modulo HTML, questa soluzione funzionerà per te. Di seguito è riportata l’API da utilizzare in questo scenario:

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// If your site is using Ajax, or you are running a secure site, it is best to send us the data directly.  
Bizible.Push('User', {
eMail: 'user@gmail.com' // required  
});  
```

In questo codice, la [!UICONTROL email] campo obbligatorio. [!DNL Marketo Measure] pubblicherà questi dati in modo asincrono sui nostri server.

## Scenario 3 - Segnalare le informazioni utente dalla pagina di ringraziamento {#scenario-report-user-information-from-the-thank-you-page}

In alcuni casi, è più comodo segnalare le informazioni del lead a [!DNL Marketo Measure] dalla pagina di ringraziamento, dopo l’invio del modulo. Il modo più semplice per segnalare queste informazioni consiste nell’aggiungere alla pagina un elemento nascosto che contenga informazioni provenienti dall’invio del modulo, e [!DNL Bizible.js] leggerà queste informazioni una volta caricata la pagina di ringraziamento.

**Ad esempio:**

```html
<div id="bizible.reportUser" style="display:none"  
data-email="user@gmail.com">  
```

Non importa se l’elemento nascosto è un elemento div, uno script o qualsiasi altro tipo di tag. [!DNL Marketo Measure] cerca l&#39;id=&quot;bizible.reportUser&quot; per leggere le informazioni.
