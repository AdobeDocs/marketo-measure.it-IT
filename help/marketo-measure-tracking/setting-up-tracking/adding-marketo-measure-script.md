---
unique-page-id: 18874795
description: Aggiunta di  [!DNL Marketo Measure] script - [!DNL Marketo Measure]
title: Aggiunta dello script  [!DNL Marketo Measure]  in corso
exl-id: f8773037-04d7-4308-ba04-440e9b990d92
feature: Tracking
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 0%

---

# Aggiunta dello script [!DNL Marketo Measure] {#adding-marketo-measure-script}

[!DNL Marketo Measure] JavaScript che desideri monitorare da [!DNL Marketo Measure] deve essere aggiunto il prima possibile a tutte le proprietà web. Una volta distribuito JavaScript, [!DNL Marketo Measure] inizia a raccogliere i tuoi dati digitali. In questo articolo vengono illustrati i metodi per la distribuzione di JavaScript [!DNL Marketo Measure] e ulteriori considerazioni.

>[!NOTE]
>
>Assicurati di aver [reclamato tutti i domini appropriati in  [!DNL Adobe Admin Console]](/help/marketo-measure-and-adobe/domain-management.md){target="_blank"} oltre a distribuire il JavaScript [!DNL Marketo Measure].

Quando si inizia a utilizzare [!DNL Marketo Measure], è possibile aggiungere il JavaScript [!DNL Marketo Measure] al sito Web in due modi:

* Hard-Coding
* Sistemi Tag Management

## Hard-Coding {#hard-coding}

Come best practice, consigliamo vivamente di utilizzare il codice rigido [!DNL Marketo Measure] JavaScript per le proprietà Web. Per codificare lo script, devi inserire lo script prima di `</head>` di chiusura in ogni pagina del sito.

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

L&#39;hardcoding del JavaScript in `<head>` delle pagine assicura che lo script [!DNL Marketo Measure] venga caricato per primo e che le informazioni di riferimento non vengano perse. Il JavaScript [!DNL Marketo Measure] viene caricato in modo asincrono. In caso di codifica fissa, il JavaScript deve essere aggiunto manualmente a Marketing Automation.

>[!TIP]
>
>Scopri come verificare che lo script sia [conforme ai requisiti RGPD](/help/security-and-compliance/compliance-related-resources/ensuring-consent-for-gdpr-in-marketo-measure-js.md){target="_blank"}.

## Sistemi Tag Management {#tag-management-systems}

Se non è possibile aggiungere [!DNL Marketo Measure] JavaScript tramite codifica fissa, un&#39;altra opzione consiste nell&#39;aggiungere lo script [!DNL Marketo Measure] utilizzando un Tag Management System come [!DNL Google Tag Manager] (GTM) o Tealium.

L&#39;utilizzo dei sistemi di gestione dei tag per distribuire [!DNL Marketo Measure] JS può comportare una potenziale perdita di dati del 5-10% a causa della latenza del tempo di caricamento dello script. In sostanza, se lo strumento di gestione dei tag non viene caricato abbastanza rapidamente, anche [!DNL Marketo Measure] JS non può essere caricato abbastanza rapidamente e potrebbe perdere le informazioni sul primo referente.

In genere, si distribuisce JS [!DNL Marketo Measure] tramite uno strumento di gestione dei tag fino a quando non è più opportuno passare alla codifica fissa per tempi e risorse.

Per aggiungere lo script [!DNL Marketo Measure] tramite una soluzione di gestione tag, è necessario creare un tag e aggiungere il JavaScript al suo interno. Applica questo tag a tutte le pagine del sito web che desideri monitorare.

[!DNL Marketo Measure] consiglia che qualsiasi visualizzazione di pagina provochi l&#39;attivazione del tag. È inoltre consigliabile assegnare a [!DNL Marketo Measure] la priorità più alta nell&#39;ordine di attivazione e assicurarsi che non vi siano script sincroni davanti al tag [!DNL Marketo Measure] per garantire la massima qualità dei dati.

Ulteriori informazioni sono disponibili [qui](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-via-google-tag-manager.md){target="_blank"}.

## Considerazioni aggiuntive {#additional-considerations}

[!DNL Marketo Measure] JavaScript è basato su dominio e quindi è in grado di gestire automaticamente tutti i sottodomini, purché JavaScript sia presente nelle pagine e il dominio radice sia lo stesso utilizzato per creare l&#39;account Marketo Measure.

Tuttavia, se utilizzi domini separati o internazionali, assicurati di informare il tuo consulente [!DNL Marketo Measure]. I domini devono essere aggiunti manualmente al tuo account all&#39;estremità [!DNL Marketo Measure] in modo che [!DNL Marketo Measure] sappia collegare i dati dei domini aggiuntivi al tuo account. Inviare domini separati/internazionali al proprio consulente [!DNL Marketo Measure].

Se utilizzi pagine di terze parti, parla del tuo caso d&#39;uso con il tuo consulente [!DNL Marketo Measure]. In generale, è possibile aggiungere una versione personalizzata di [!DNL Marketo Measure] JavaScript per tenere traccia delle pagine, se necessario. Se non è possibile, il tracciamento tramite i punti di contatto della campagna CRM verrà esplorato con il tuo consulente [!DNL Marketo Measure].

Sono presenti moduli che NON devono essere tracciati da [!DNL Marketo Measure] in quanto non hanno necessariamente senso per l&#39;attribuzione (ad esempio moduli per annullare l&#39;abbonamento, accessi dei clienti e così via)? In tal caso, aggiungere il codice di esclusione [in questo articolo](/help/marketo-measure-tracking/setting-up-tracking/excluding-marketo-measure-from-specific-forms.md){target="_blank"} a ogni modulo

Hai delle pagine non sicure? È necessario proteggerli in quanto la navigazione tra una pagina sicura e non protetta interrompe la sessione di tracciamento.

Assicurati di parlare con il tuo team Web in modo che sappia che [!DNL Marketo Measure] JavaScript deve trovarsi sempre nelle proprietà Web appropriate. Se vengono introdotte nuove pagine/moduli/siti, assicurarsi che la distribuzione di [!DNL Marketo Measure] JavaScript faccia parte del protocollo.

Se durante la configurazione di JavaScript viene attivato un avviso [!DNL Web Application Firewall (WAF)], gli utenti possono disabilitare la regola di WAF o inserire nell&#39;elenco Consentiti i cookie, come nell&#39;esempio seguente:

![](assets/adding-marketo-measure-script-1.png)

## Forms a cui prestare maggiore attenzione {#forms-to-pay-extra-attention-to}

**Invio con più moduli**

* Problema: se hai più moduli collegati come parte di un singolo invio di moduli, è possibile che il primo modulo generi un punto di contatto anche se il modulo completo non viene inviato.
* Soluzione: è necessario forzare uno dei moduli per segnalare l&#39;utente a [!DNL Marketo Measure] in base ai dati memorizzati nella cache e discutere le procedure di abbandono. In genere, [codice utente report](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-to-different-form-providers/ajax-form-handling.md){target="_blank"} può risolvere questo problema.

**Accesso account (non creazione)**

* Problema: [!DNL Marketo Measure] consiglia di non creare punti di contatto per i successivi accessi all&#39;account, poiché questi tendono a diluire la storia di attribuzione.
* Soluzione: aggiungi il codice di esclusione al modulo di accesso account/cliente/partner.

>[!NOTE]
>
>È consigliabile creare un punto di contatto per la creazione di un account o di una versione di prova.

**Download della risorsa**

* Problema: se le risorse vengono cancellate, [!DNL Marketo Measure] tiene traccia dei download come riempimenti di moduli. Se le risorse non sono gestite, ci sono limitazioni a ciò su cui possiamo generare rapporti senza personalizzazione.
* Soluzione: cancella la risorsa se desideri che venga tracciata da [!DNL Marketo Measure] JavaScript. Se questa non è un’opzione e desideri comunque un punto di contatto, puoi invece sincronizzare una campagna CRM.

**iFrame**

* Problema: iFrame funziona essenzialmente come pagine all’interno delle pagine.
* Soluzione: per poter essere collegato correttamente al modulo, il file JS [!DNL Marketo Measure] deve essere distribuito direttamente nell&#39;intestazione iFrame.

**Lightbox**

* Le Lightbox sono in genere pop-up che contengono iFrame
* Soluzione: il file JS [!DNL Marketo Measure] deve essere distribuito all&#39;interno dell&#39;intestazione dell&#39;iFrame ospitato.

**Più moduli in una pagina**

* Problema: se in una pagina sono presenti più moduli ospitati, è possibile che non si sia in grado di indicare quale modulo specifico è stato compilato con il campo URL modulo [!DNL Marketo Measure].
* Soluzione: se devi sapere quale modulo è stato compilato, prova a configurare l’hashing dinamico degli URL con il tuo team web.

**Forms organizzato in formato `<div>`**

* Problema: a [!DNL Marketo Measure] JS non è possibile riconoscere i moduli organizzati in formato `<div>`, pertanto può essere necessario un codice personalizzato.
* Soluzione: questi [modelli utente per report](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-to-different-form-providers/ajax-form-handling.md){target="_blank"} possono essere utilizzati dal team di sviluppo Web per aggiungere il codice necessario.

**Chat**

* Problema: se utilizzi un provider di chat, potrebbe essere necessaria una gestione speciale.
* Soluzione: [!DNL Marketo Measure] si integra con Drift, Olark, Livechat, LivePerson e SnapEngage. Tutte le altre piattaforme devono essere tracciate tramite l’iscrizione alla campagna CRM.

**Secondo dominio**

* Problema: [!DNL Marketo Measure] JavaScript è specifico per il dominio, pertanto è necessario eseguire ulteriori passaggi per qualsiasi dominio separato o internazionale. [!DNL Marketo Measure] JS può gestire sottodomini sullo stesso dominio radice.
* Soluzione: se possiedi più domini principali, che desideri che vengano tracciati da [!DNL Marketo Measure], assicurati di aggiungere JS ai domini E informa il tuo consulente [!DNL Marketo Measure] sui domini da associare manualmente al tuo account [!DNL Marketo Measure].

## Verifica di [!DNL Marketo Measure] JavaScript {#testing-marketo-measure-javascript}

Il tuo consulente [!DNL Marketo Measure] ti aiuterà a testare il sito Web per assicurarti che [!DNL Marketo Measure] JavaScript sia presente in tutte le pagine. Parte di questo test consiste nell’invio di alcuni moduli compilati con dettagli di test chiaramente indicati per garantire la corretta restituzione del tracciamento.

Tuttavia, è probabile che il tuo consulente [!DNL Marketo Measure] non abbia familiarità con il tuo sito Web come lo è il tuo team. Per questo motivo, è molto importante che il tuo team web o un altro team appropriato controlli accuratamente il sito web, soprattutto se ci sono moduli complessi in uso come quelli sopra menzionati. Il tuo team sarà in ultima analisi responsabile di garantire che tutte le proprietà Web necessarie siano correttamente monitorate, ma se sei a conoscenza di eventuali moduli o situazioni complesse, puoi chiedere al tuo consulente [!DNL Marketo Measure] assistenza per il test.

Per verificare manualmente un modulo, eseguire la procedura seguente:

1. Utilizza sempre un browser in incognito o cancella la cache tra ciascun test di invio del modulo E utilizza ogni volta un indirizzo e-mail diverso.

   a. Una best practice consiste nell’utilizzare un’e-mail falsa che contiene qualcosa che indica che si tratta di un test e l’ora del giorno. Ad esempio: testing830am@test.com.

1. Registra l’URL della pagina a cui stai inviando il modulo e l’e-mail utilizzata.

1. Individua il record creato nel CRM (lead o contatto) per l’invio del modulo e verifica che sia stato creato correttamente un punto di contatto.

   a. È possibile utilizzare un report azionario [!DNL Marketo Measure] come Lead con punti di contatto dell&#39;acquirente oppure esaminare il layout della pagina Lead/Contatto se si è scelto di aggiornare i layout di pagina con i dettagli [!DNL Marketo Measure].

   b. L’elaborazione dei dati potrebbe richiedere del tempo.
