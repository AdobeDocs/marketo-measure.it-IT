---
unique-page-id: 18874795
description: Aggiunta [!DNL Marketo Measure] Script - [!DNL Marketo Measure] - Documentazione del prodotto
title: Aggiunta [!DNL Marketo Measure] Script
exl-id: f8773037-04d7-4308-ba04-440e9b990d92
source-git-commit: 82cc8269bfdb26b6acf039d0ce0e06564f5e2612
workflow-type: tm+mt
source-wordcount: '1307'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] Script {#adding-marketo-measure-script}

[!DNL Marketo Measure] JavaScript da tracciare [!DNL Marketo Measure] deve essere aggiunto a tutte le proprietà web il prima possibile. Una volta distribuito JavaScript, [!DNL Marketo Measure] inizierà a raccogliere i tuoi dati digitali. Questo articolo illustra i metodi di distribuzione [!DNL Marketo Measure] JavaScript e considerazioni aggiuntive da tenere in considerazione.

>[!NOTE]
>
>Assicurati di [ha richiesto tutti i domini appropriati nel [!DNL Adobe Admin Console]](/help/marketo-measure-and-adobe/domain-management.md){target="_blank"} oltre a distribuire il [!DNL Marketo Measure] JavaScript.

Quando iniziare con [!DNL Marketo Measure], sono disponibili due modi per aggiungere il [!DNL Marketo Measure] JavaScript sul tuo sito web:

* Codifica rigida
* Sistemi Tag Management

## Codifica rigida {#hard-coding}

Come best practice, consigliamo vivamente di utilizzare la codifica fissa [!DNL Marketo Measure] JavaScript per le proprietà web. Per codificare lo script, è necessario inserire lo script prima della chiusura `</head>` in ogni pagina del sito.

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Codifica di JavaScript nel `<head>` delle pagine assicura [!DNL Marketo Measure] lo script verrà caricato per primo e le informazioni di riferimento non verranno perse. La [!DNL Marketo Measure] JavaScript viene caricato in modo asincrono. Se si utilizza la codifica fissa, è necessario aggiungere manualmente JavaScript a Marketing Automation.

>[!TIP]
>
>Scopri come verificare che lo script sia [Conformità al RGPD](/help/security-and-compliance/compliance-related-resources/ensuring-consent-for-gdpr-in-marketo-measure-js.md){target="_blank"}.

## Sistemi Tag Management {#tag-management-systems}

Se si aggiunge [!DNL Marketo Measure] JavaScript tramite hardcoding non è possibile, un&#39;altra opzione è quella di aggiungere il [!DNL Marketo Measure] script che utilizza un sistema Tag Management, ad esempio [!DNL Google Tag Manager] (GTM) o Tealium.

Tieni presente che l’utilizzo dei sistemi di gestione tag per la distribuzione [!DNL Marketo Measure] JS può causare una potenziale perdita di dati del 5-10% a causa della latenza del tempo di caricamento dello script. In sostanza, se lo strumento di gestione dei tag non viene caricato abbastanza rapidamente, [!DNL Marketo Measure] JS non può inoltre essere caricato abbastanza rapidamente e potrebbe perdere le informazioni del primo referente.

Una pratica comune consiste nell’implementare [!DNL Marketo Measure] JS tramite uno strumento di gestione dei tag fino a quando è meglio passare alla codifica fissa.

Per aggiungere [!DNL Marketo Measure] esegui lo script attraverso una soluzione di gestione tag, dovrai creare un nuovo tag e aggiungere il nostro JavaScript al suo interno. Applica questo tag a tutte le pagine del sito web che desideri monitorare.

[!DNL Marketo Measure] consiglia di attivare il tag in qualsiasi visualizzazione di pagina. Inoltre, è meglio dare [!DNL Marketo Measure] la priorità più alta nell&#39;ordine di attivazione e assicurati che non ci siano script sincroni davanti al [!DNL Marketo Measure] per garantire la qualità dei dati più elevata.

Ulteriori informazioni possono essere [qui](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-via-google-tag-manager.md){target="_blank"}.

## Considerazioni aggiuntive {#additional-considerations}

[!DNL Marketo Measure] JavaScript è basato su dominio ed è quindi in grado di gestire automaticamente qualsiasi sottodominio purché JavaScript si trovi sulle pagine e il dominio principale sia lo stesso del dominio utilizzato per creare l’account Marketo Measure.

Tuttavia, se utilizzi domini separati o internazionali, assicurati di lasciare [!DNL Marketo Measure] Consulente lo sa. I domini devono essere aggiunti manualmente al tuo account sul [!DNL Marketo Measure] concludi in modo che [!DNL Marketo Measure] sa collegare i dati dei domini aggiuntivi al tuo account. Quindi, invia tutti i domini separati/internazionali al tuo [!DNL Marketo Measure] Consulente.

Se utilizzi pagine di terze parti, assicurati di parlare del tuo caso d’uso con il tuo [!DNL Marketo Measure] Consulente. In generale, è necessario sapere se è possibile aggiungere una versione personalizzata di [!DNL Marketo Measure] JavaScript per tenere traccia di quelle pagine, se appropriato. Se questo non è possibile, il tracciamento tramite i punti di contatto di Campaign CRM verrà esplorato con il tuo [!DNL Marketo Measure] Consulente.

Sono presenti moduli che NON devono essere tracciati da [!DNL Marketo Measure] poiché non hanno necessariamente senso per l’attribuzione (ad esempio, moduli di annullamento dell’abbonamento, accessi cliente, ecc.)? In tal caso, aggiungi il codice di esclusione [nel presente articolo](/help/marketo-measure-tracking/setting-up-tracking/excluding-marketo-measure-from-specific-forms.md){target="_blank"} a ciascun modulo

Hai delle pagine non sicure? In tal caso, è consigliabile proteggerli perché la navigazione tra una pagina protetta e non protetta interromperà la sessione di tracciamento.

Assicurati di avere una conversazione con il tuo team web in modo che sappiano [!DNL Marketo Measure] JavaScript deve sempre trovarsi sulle proprietà web appropriate. Se vengono introdotte nuove pagine, moduli o siti, assicurati di distribuire [!DNL Marketo Measure] JavaScript fa parte del protocollo .

Se [!DNL Web Application Firewall (WAF)] l’avviso viene attivato durante la configurazione di JavaScript, gli utenti possono disattivare tale regola WAF o inserire nell’elenco Consentiti i cookie, come nell’esempio seguente:

![](assets/adding-marketo-measure-script-1.png)

## Forms per prestare maggiore attenzione a {#forms-to-pay-extra-attention-to}

**Invio a più moduli**

* Problema: Se si dispone di più moduli collegati come parte di un singolo modulo, è possibile che il primo modulo generi un punto di contatto anche se il modulo completo non viene inviato.
* Soluzione: È necessario forzare uno dei moduli a cui inviare i rapporti per l’utente [!DNL Marketo Measure] in base ai dati memorizzati nella cache e discutere le pratiche di abbandono. In generale, [codice utente del report](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-to-different-form-providers/ajax-form-handling.md){target="_blank"} può risolvere questo.

**Accesso all’account (non creazione)**

* Problema: [!DNL Marketo Measure] consiglia di non creare punti di contatto per gli accessi successivi all’account, in quanto tendono a diluire il brano di attribuzione.
* Soluzione: Aggiungi Codice di esclusione al modulo di accesso account/cliente/partner.

>[!NOTE]
>
>È consigliabile creare un punto di contatto per la creazione di un account o una versione di prova.

**Download della risorsa**

* Problema: Se le risorse sono trasferite, [!DNL Marketo Measure] tiene traccia dei download durante la compilazione del modulo. Se le tue risorse non sono collegate, ci sono limitazioni a ciò che possiamo segnalare senza personalizzazione.
* Soluzione: Accedi alla risorsa se desideri che sia tracciata da [!DNL Marketo Measure] JavaScript. Se questa non è un’opzione e desideri comunque un punto di contatto per essa, considera la sincronizzazione di una campagna CRM.

**iFrame**

* Problema: IFrames funzionano essenzialmente come pagine all’interno di pagine.
* Soluzione: La [!DNL Marketo Measure] JS deve essere distribuito direttamente all’interno dell’intestazione iFrame per consentirci di allegare correttamente al modulo.

**Lightbox**

* Le Lightbox sono in genere pop-up che contengono iFrame
* Soluzione: la [!DNL Marketo Measure] JS deve essere distribuito all’interno dell’intestazione dell’iFrame ospitato.

**Più moduli su una pagina**

* Problema: Se in una pagina sono presenti più moduli ospitati, potrebbe non essere possibile individuare il modulo specifico che è stato compilato con [!DNL Marketo Measure] Campo URL modulo.
* Soluzione: Per sapere quale modulo è stato compilato, è consigliabile configurare l’hashing dinamico degli URL con il team web.

**Forms organizzato in `<div>` format**

* Problema: [!DNL Marketo Measure] JS ha difficoltà a riconoscere i moduli organizzati in `<div>` in modo che il codice personalizzato possa essere necessario.
* Soluzione: Tali [modelli utente di report](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-to-different-form-providers/ajax-form-handling.md){target="_blank"} può essere utilizzato dal team di sviluppo web per aggiungere il codice necessario.

**Chat**

* Problema: Se utilizzi un provider di chat, potrebbe essere necessaria una gestione speciale.
* Soluzione: [!DNL Marketo Measure] si integra con Drift, Olark, Livechat, LivePerson e SnapEngage. Tutte le altre piattaforme devono essere monitorate tramite l&#39;iscrizione alla campagna CRM.

**Secondo dominio**

* Problema: [!DNL Marketo Measure] JavaScript è specifico per il dominio, pertanto è necessario eseguire ulteriori passaggi per qualsiasi dominio separato o internazionale. Tieni presente che [!DNL Marketo Measure] JS può gestire i sottodomini nello stesso dominio principale.
* Soluzione: Se possiedi più domini root, vorresti essere monitorato da [!DNL Marketo Measure] assicurati di aggiungere JS ai domini E lasciare che il tuo [!DNL Marketo Measure] Il consulente sa quali domini devono essere associati manualmente al tuo [!DNL Marketo Measure] conto.

## Test [!DNL Marketo Measure] JavaScript {#testing-marketo-measure-javascript}

Le [!DNL Marketo Measure] Il consulente ti aiuterà a individuare il test del sito web per assicurarsi che [!DNL Marketo Measure] JavaScript è presente in tutte le pagine. Parte di questo test sarà l’invio di alcuni moduli con dettagli di test chiaramente indicati per garantire che il tracciamento ritorni correttamente.

Tuttavia, il tuo [!DNL Marketo Measure] Il consulente probabilmente non ha la stessa familiarità con il tuo sito web quanto il tuo team web. Per questo motivo, è molto importante che il tuo team web o altro team appropriato controlli accuratamente il sito web, specialmente se ci sono moduli complessi in uso come quelli sopra menzionati. In ultima analisi, il tuo team sarà responsabile di garantire che tutte le proprietà web necessarie siano correttamente monitorate, ma se sei a conoscenza di moduli o situazioni complesse, puoi chiedere al tuo team [!DNL Marketo Measure] Consulente per l&#39;assistenza nelle prove.

Per verificare personalmente un modulo, segui questi passaggi:

1. Utilizza sempre un browser in incognito o cancella la cache tra ogni test di invio del modulo E utilizza ogni volta un indirizzo e-mail diverso.

   a) Una best practice consigliata è l’utilizzo di un’e-mail falsa che contiene elementi che indicano che si tratta di un test e dell’ora del giorno. Ad esempio: testing830am@test.com.

1. Registrare l’URL della pagina che si sta inviando al modulo e l’e-mail utilizzata.

1. Individua il record creato nel CRM (Lead o Contact) per l’invio del modulo e verifica che un punto di contatto sia stato creato in modo appropriato.

   a) Puoi utilizzare un [!DNL Marketo Measure] rapporti sulle azioni, ad esempio Lead con punti di contatto per l’acquirente, oppure guarda il layout della pagina Lead/Contatto se hai scelto di aggiornare i layout di pagina con [!DNL Marketo Measure] dettagli.

   b) Tieni presente che l’elaborazione dei dati potrebbe richiedere del tempo.
