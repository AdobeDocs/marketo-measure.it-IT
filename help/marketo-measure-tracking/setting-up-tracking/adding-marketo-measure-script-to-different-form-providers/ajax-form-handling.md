---
unique-page-id: 18874745
description: Gestione modulo AJAX - [!DNL Marketo Measure]
title: Gestione dei moduli AJAX
exl-id: 042e42ff-d8d9-4380-b878-aba4934bc4a0
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Gestione dei moduli AJAX {#ajax-form-handling}

Per segnalare manualmente le conversioni dei clienti in [!DNL Marketo Measure], è possibile utilizzare una semplice API. Entrambe queste API di JavaScript sono automaticamente disponibili sul tuo sito, se hai un codice di tracciamento su di esso. Non è necessario eseguire alcuna operazione speciale per accedervi.

## Scenario 1 - Modulo HTML con invio AJAX {#scenario-html-form-with-an-ajax-submit}

Quando si utilizzano moduli contenenti AJAX (o un altro meccanismo) per inviare le date di conversione dal client ai nostri server, [!DNL Marketo Measure] potrebbe non essere a conoscenza della conversione del cliente tramite nessuno dei percorsi standard monitorati. In questo scenario, possiamo utilizzare una semplice API (fornita di seguito).

Se gestisci i tuoi invii di moduli, puoi chiamare esplicitamente [!DNL Marketo Measure] da JavaScript. [!DNL Marketo Measure] raccoglie tutte le informazioni rilevanti dal modulo e le pubblica in modo asincrono sui nostri server.

**Di seguito è riportato un esempio di codice che utilizza JQuery (supponendo che l&#39;ID nel modulo sia &quot;formId&quot;):**

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// Give Marketo Measure the JQuery Selector for the form and we'll collect the data automatically.  
Bizible.Push('Form',$('#*formId*'));
```

**Di seguito è riportato un esempio di codice che non utilizza JQuery (supponendo che l&#39;ID nel modulo sia &quot;formId&quot;):**

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// Give Marketo Measure the Form ID and we'll collect the data automatically.
Bizible.Push('Form','MyFormID');
```

## Scenario 2 - Informazioni sui lead raccolte in un modulo non HTML {#scenario-lead-information-collected-in-a-non-html-form}

Se le informazioni di un lead convertito vengono raccolte utilizzando JavaScript o campi di testo semplici senza modulo HTML, questa soluzione funziona automaticamente. Di seguito è riportata l’API da utilizzare in questo scenario:

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// If your site is using Ajax, or you are running a secure site, it is best to send us the data directly.  
Bizible.Push('User', {
eMail: 'user@gmail.com' // required  
});  
```

In questo codice, il campo [!UICONTROL email] è obbligatorio. [!DNL Marketo Measure] pubblica questi dati in modo asincrono sui nostri server.

## Scenario 3 - Segnalare le informazioni utente dalla pagina di ringraziamento {#scenario-report-user-information-from-the-thank-you-page}

A volte è più comodo segnalare le informazioni del lead a [!DNL Marketo Measure] dalla pagina di ringraziamento, dopo l&#39;invio del modulo. Il modo più semplice per segnalare queste informazioni è aggiungere un elemento nascosto alla pagina che contiene le informazioni dell&#39;invio del modulo. [!DNL Bizible.js] leggerà queste informazioni al caricamento della pagina di ringraziamento.

**Esempio:**

```html
<div id="bizible.reportUser" style="display:none"  
data-email="user@gmail.com">  
```

Non importa se l’elemento nascosto è un div, uno script o un altro tipo di tag. [!DNL Marketo Measure] cerca id=&quot;bizible.reportUser&quot; per leggere le informazioni.
