---
unique-page-id: 18874795
description: Aggiunta [!DNL Marketo Measure] Script - [!DNL Marketo Measure] - Documentazione del prodotto
title: Aggiunta [!DNL Marketo Measure] Script
exl-id: f8773037-04d7-4308-ba04-440e9b990d92
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '1307'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] Script {#adding-marketo-measure-script}

[!DNL Marketo Measure] JavaScript di cui tenere traccia [!DNL Marketo Measure] devono essere aggiunte il prima possibile a tutte le proprietà web. Una volta implementato JavaScript, [!DNL Marketo Measure] inizierà a raccogliere i tuoi dati digitali. Questo articolo illustra i metodi per la distribuzione di [!DNL Marketo Measure] JavaScript e considerazioni aggiuntive da considerare.

>[!NOTE]
>
>Assicurati di aver [ha richiesto tutti i domini appropriati in [!DNL Adobe Admin Console]](/help/marketo-measure-and-adobe/domain-management.md){target="_blank"} oltre a distribuire il [!DNL Marketo Measure] JavaScript.

Quando si inizia con [!DNL Marketo Measure], è possibile aggiungere [!DNL Marketo Measure] JavaScript per il sito Web:

* Hard-Coding
* Sistemi Tag Management

## Hard-Coding {#hard-coding}

Come best practice, consigliamo vivamente la codifica fissa [!DNL Marketo Measure] JavaScript per le proprietà web. Per codificare lo script, devi inserire lo script prima della chiusura `</head>` su ogni pagina del sito.

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Codifica di JavaScript in `<head>` delle pagine assicura che [!DNL Marketo Measure] lo script verrà caricato per primo e le informazioni di riferimento non verranno perse. Il [!DNL Marketo Measure] JavaScript viene caricato in modo asincrono. In caso di codifica fissa, il codice JavaScript deve essere aggiunto manualmente a Marketing Automation.

>[!TIP]
>
>Scopri come assicurarti che lo script sia [Conforme ai requisiti RGPD](/help/security-and-compliance/compliance-related-resources/ensuring-consent-for-gdpr-in-marketo-measure-js.md){target="_blank"}.

## Sistemi Tag Management {#tag-management-systems}

Se si aggiunge [!DNL Marketo Measure] JavaScript tramite codifica fissa non è possibile, un’altra opzione consiste nell’aggiungere [!DNL Marketo Measure] script che utilizza un sistema Tag Management come [!DNL Google Tag Manager] GTM o Tealium.

L’utilizzo dei sistemi di gestione dei tag per la distribuzione [!DNL Marketo Measure] JS può comportare una potenziale perdita di dati del 5-10% a causa della latenza del tempo di caricamento dello script. In sostanza, se lo strumento di gestione dei tag non viene caricato abbastanza rapidamente, [!DNL Marketo Measure] Inoltre, JS non può essere caricato abbastanza rapidamente e potrebbe perdere le informazioni sul primo referente.

Una pratica comune consiste nell’implementare [!DNL Marketo Measure] JS tramite uno strumento di gestione dei tag fino a quando i tempi e le risorse sono migliori per passare all’hardcoding.

Da aggiungere [!DNL Marketo Measure] tramite una soluzione di gestione tag, dovrai creare un nuovo tag e aggiungere il nostro JavaScript al suo interno. Applica questo tag a tutte le pagine del sito web che desideri monitorare.

[!DNL Marketo Measure] consiglia di attivare il tag in qualsiasi visualizzazione di pagina. Inoltre, è meglio dare [!DNL Marketo Measure] la priorità più alta nell&#39;ordine di attivazione e assicurati che non vi siano script sincroni davanti al [!DNL Marketo Measure] per garantire la massima qualità dei dati.

Ulteriori informazioni possono essere [trovato qui](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-via-google-tag-manager.md){target="_blank"}.

## Considerazioni aggiuntive {#additional-considerations}

[!DNL Marketo Measure] JavaScript è basato su dominio ed è quindi in grado di gestire automaticamente qualsiasi sottodominio, purché il JavaScript si trovi sulle pagine e il dominio principale sia lo stesso utilizzato per creare l’account Marketo Measure.

Tuttavia, se utilizzi domini separati o internazionali, assicurati di consentire ai [!DNL Marketo Measure] Consulente sa. I domini devono essere aggiunti manualmente al tuo account nella [!DNL Marketo Measure] terminare in modo che [!DNL Marketo Measure] sa collegare i dati dei domini aggiuntivi al tuo account. Pertanto, si prega di inviare eventuali domini separati/internazionali al tuo [!DNL Marketo Measure] Consulente.

Se utilizzi pagine di terze parti, parla del tuo caso d’uso con il [!DNL Marketo Measure] Consulente. In generale, è importante sapere se è possibile aggiungere una versione personalizzata di [!DNL Marketo Measure] JavaScript per tenere traccia di tali pagine, se appropriato. Se questo non è possibile, il tracciamento tramite i punti di contatto della campagna CRM verrà esplorato con il tuo [!DNL Marketo Measure] Consulente.

Sono presenti moduli CHE NON devono essere tracciati da [!DNL Marketo Measure] dal momento che non hanno necessariamente senso per l’attribuzione (ad esempio, moduli per annullare l’abbonamento, accessi dei clienti, ecc.)? In tal caso, aggiungi il codice di esclusione [in questo articolo](/help/marketo-measure-tracking/setting-up-tracking/excluding-marketo-measure-from-specific-forms.md){target="_blank"} a ogni modulo

Hai delle pagine non sicure? In tal caso, è necessario proteggerli in quanto la navigazione tra una pagina sicura/non protetta interromperà la sessione di tracciamento.

Assicurati di avere una conversazione con il tuo team web in modo che sappiano [!DNL Marketo Measure] JavaScript deve trovarsi sempre nelle proprietà web appropriate. Se vengono introdotte nuove pagine/moduli/siti, assicurati che la distribuzione [!DNL Marketo Measure] JavaScript fa parte del protocollo.

Se un [!DNL Web Application Firewall (WAF)] L’avviso viene attivato durante la configurazione di JavaScript, gli utenti possono disabilitare la regola WAF o inserire nell’elenco Consentiti i cookie, come nell’esempio seguente:

![](assets/adding-marketo-measure-script-1.png)

## Forms a cui prestare maggiore attenzione {#forms-to-pay-extra-attention-to}

**Invio di più moduli**

* Problema: se come parte di un singolo invio di moduli collegati si dispone di più moduli, è possibile che il primo modulo generi un punto di contatto anche se il modulo completo non viene inviato.
* Soluzione: è necessario forzare una delle maschere a cui segnalare l&#39;utente [!DNL Marketo Measure] in base ai dati memorizzati nella cache e illustra le pratiche di abbandono. Generalmente, [codice utente report](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-to-different-form-providers/ajax-form-handling.md){target="_blank"} può risolvere per questo.

**Accesso all’account (non creazione)**

* Problema: [!DNL Marketo Measure] consiglia di non creare punti di contatto per i successivi accessi all’account, in quanto questi tendono a diluire la storia di attribuzione.
* Soluzione: aggiungi il codice di esclusione al modulo di accesso account/cliente/partner.

>[!NOTE]
>
>È consigliabile creare un punto di contatto per la creazione di un account o di una versione di prova.

**Download della risorsa**

* Problema: se le risorse vengono gestite, [!DNL Marketo Measure] tiene traccia dei download durante la compilazione del modulo. Se le risorse non sono gestite, ci sono limitazioni a ciò su cui possiamo generare rapporti senza personalizzazione.
* Soluzione: cancella la risorsa se desideri che venga tracciata da [!DNL Marketo Measure] JavaScript. Se questa non è un’opzione e desideri comunque un punto di contatto, puoi invece sincronizzare una campagna CRM.

**iFrame**

* Problema: iFrame funziona essenzialmente come pagine all’interno delle pagine.
* Soluzione: [!DNL Marketo Measure] Per poter essere collegato correttamente al modulo, JS deve essere distribuito direttamente all’interno dell’intestazione iFrame.

**Lightbox**

* Le Lightbox sono in genere pop-up che contengono iFrame
* Soluzione: [!DNL Marketo Measure] JS deve essere distribuito all’interno dell’intestazione dell’iFrame in hosting.

**Più moduli su una pagina**

* Problema: se in una pagina sono presenti più moduli ospitati, potresti non essere in grado di comunicare quale modulo specifico è stato compilato con [!DNL Marketo Measure] Campo URL modulo.
* Soluzione: se devi sapere quale modulo è stato compilato, prova a configurare l’hashing dinamico degli URL con il tuo team web.

**Forms organizzato in `<div>` formato**

* Problema: [!DNL Marketo Measure] JS fa fatica a riconoscere i moduli organizzati in `<div>` in modo da richiedere codice personalizzato.
* Soluzione: [modelli utente per report](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-to-different-form-providers/ajax-form-handling.md){target="_blank"} può essere utilizzato dal team di sviluppo web per aggiungere il codice necessario.

**Chat**

* Problema: se utilizzi un provider di chat, potrebbe essere necessaria una gestione speciale.
* Soluzione: [!DNL Marketo Measure] si integra con Drift, Olark, Livechat, LivePerson e SnapEngage. Tutte le altre piattaforme devono essere tracciate tramite l’iscrizione alla campagna CRM.

**Secondo dominio**

* Problema: [!DNL Marketo Measure] JavaScript è specifico per il dominio, pertanto è necessario effettuare ulteriori passaggi per qualsiasi dominio separato o internazionale. Tieni presente che [!DNL Marketo Measure] JS può gestire sottodomini sullo stesso dominio principale.
* Soluzione: se possiedi più domini radice, di cui desideri tenere traccia [!DNL Marketo Measure] assicurati di aggiungere JS ai domini E lascia che il tuo [!DNL Marketo Measure] Il consulente sa quali domini devono essere associati manualmente al tuo [!DNL Marketo Measure] account.

## Test [!DNL Marketo Measure] JavaScript {#testing-marketo-measure-javascript}

Il tuo [!DNL Marketo Measure] Il consulente ti aiuterà a testare il sito web per assicurarti che [!DNL Marketo Measure] JavaScript è presente in tutte le pagine. Parte di questo test consiste nell’invio di alcuni moduli compilati con dettagli di test chiaramente indicati per garantire la corretta restituzione del tracciamento.

Tuttavia, [!DNL Marketo Measure] È probabile che il consulente non abbia familiarità con il sito web come lo è il tuo team. Per questo motivo, è molto importante che il tuo team web o un altro team appropriato controlli accuratamente il sito web, soprattutto se ci sono moduli complessi in uso come quelli sopra menzionati. Il tuo team sarà in ultima analisi responsabile di garantire che tutte le proprietà web necessarie siano correttamente tracciate, ma se sei a conoscenza di eventuali moduli o situazioni complesse, puoi chiedere al tuo [!DNL Marketo Measure] Consulente per assistenza nei test.

Per verificare manualmente un modulo, eseguire la procedura seguente:

1. Utilizza sempre un browser in incognito o cancella la cache tra ciascun test di invio del modulo E utilizza ogni volta un indirizzo e-mail diverso.

   a. Una best practice consiste nell’utilizzare un’e-mail falsa che contiene qualcosa che indica che si tratta di un test e l’ora del giorno. Ad esempio: testing830am@test.com.

1. Registra l’URL della pagina a cui stai inviando il modulo e l’e-mail utilizzata.

1. Individua il record creato nel CRM (lead o contatto) per l’invio del modulo e verifica che sia stato creato correttamente un punto di contatto.

   a. È possibile utilizzare un [!DNL Marketo Measure] rapporti sulle scorte, ad esempio Lead con punti di contatto dell&#39;acquirente, oppure il layout della pagina Lead/Contatto, se si è scelto di aggiornare i layout di pagina con [!DNL Marketo Measure] dettagli.

   b. Tieni presente che l’elaborazione dei dati potrebbe richiedere del tempo.
