---
unique-page-id: 18874592
description: Integrazione tracciamento chiamate - [!DNL Marketo Measure]
title: Integrazione tracciamento chiamate
exl-id: bc35a789-e056-4456-9038-306ed34c2a8e
feature: Tracking, Integration
source-git-commit: 4787f765348da71bc149c997470ce678ba498772
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 0%

---

# Integrazione tracciamento chiamate {#call-tracking-integration}

La nostra integrazione con [!DNL CallTrackingMetrics] ha lo scopo di unire una sessione web a una telefonata. Una telefonata viene trattata come un invio tramite modulo a [!DNL Marketo Measure]. Dà credito a una sessione web che altrimenti sarebbe stata considerata solo una visita web perché non c&#39;era un invio effettivo del modulo.

## Informazioni sul tracciamento delle chiamate {#call-tracking-explained}

Il &quot;tracciamento delle chiamate&quot; in senso generale è un prodotto di aziende come [!DNL CallTrackingMetrics], [!DNL DiaglogTech], [!DNL Invoca], o [!DNL CallRail], per citarne alcuni. I numeri di telefono univoci vengono visualizzati agli utenti in base ai diversi canali o campagne di marketing da cui provengono. In questo modo gli addetti al marketing possono vedere le prestazioni di tali canali o campagne.

![](assets/1.png)

## Prima e dopo {#before-and-after}

Osservare il diagramma di flusso seguente per vedere come [!DNL Marketo Measure] utilizzato per gestire le chiamate telefoniche senza un’integrazione con CallTrackingMetrics. La telefonata che ha avuto luogo è stata detracciata, quindi è stata vista come una sessione web e non è stato creato alcun punto di contatto per essa. Solo durante la visita successiva, quando l’utente completava un modulo, veniva finalmente popolato un punto di contatto.

Con l&#39;integrazione, potete vedere che la sessione web era in realtà legata a una telefonata. Il successivo riempimento del modulo diventa un tocco PostLC e viene ancora tracciato come parte del percorso.

![](assets/2.png)

## Come funziona {#how-it-works}

CallTrackingMetrics deve completare un lavoro di sviluppo affinché questo funzioni. Con il JavaScript inserito sul sito, CallTrackingMetrics può acquisire _biz_uid da [!DNL Marketo Measure] cookie. Questo&quot;[!DNL BizibleId]&quot; viene quindi memorizzato da CallTrackingMetrics.

Quando un visitatore accede al tuo sito ed effettua una chiamata, è compito di CallTrackingMetrics inviare tali dati in [!DNL Salesforce].  In genere, un [!DNL Salesforce Task] viene creato per compilare dati quali numero di telefono, oggetto, tipo e ora, il [!DNL BizibleId]

Il [!DNL BizibleId] è un campo installato con la versione 6.7+ di [!DNL Marketo Measure] Pacchetto di attribuzione marketing.

Di seguito è riportato un esempio di record Attività con [!DNL BizibleId] popolato.

![](assets/3.png)

Quando [!DNL Marketo Measure] trova un record Attività con un record noto [!DNL BizibleId] valore inserito, [!DNL Marketo Measure] può mappare tale utente a una sessione web con lo stesso [!DNL BizibleId] e attribuisci quella sessione a una telefonata invece che a una visita web.

## Punto di contatto {#the-touchpoint}

Quando [!DNL Marketo Measure] può importare/scaricare l’attività, elaboriamo quei dettagli insieme alla sessione web. Di solito, può essere unita a un referrer o a un annuncio. Nell’esempio seguente, un visitatore ha trovato l’attività tramite un annuncio a pagamento di Google ed ha effettuato una telefonata.

Il [!UICONTROL Touchpoint] Il tipo &quot;Chiamata&quot; viene estratto dall’Attività, dalla schermata precedente, che viene anche compilata da CallTrackingMetrics al momento della creazione dell’Attività.

![](assets/4.png)

## Reporting {#reporting}

Valori tipo punto di contatto che [!DNL Marketo Measure] in genere i push sono Visita web, Modulo web o Chat web, ma nel caso dei punti di contatto CallTrackingMetrics, il tipo di punto di contatto è Chiamata telefonica. In questo modo gli addetti al marketing possono vedere quali canali assorbono il maggior numero di telefonate e generare ricavi per la loro organizzazione.

![](assets/5.png)

## Domande frequenti {#faq}

**Perché la mia visita web di tipo punto di contatto?**

Il campo Tipo punto di contatto viene compilato dal campo Task.Type. Se il campo Task.Type è vuoto, [!DNL Marketo Measure] imposta automaticamente il tipo di punto di contatto come visita web. Dopo aver popolato il campo Task.Type [!DNL Marketo Measure] leggerà tale valore e compilerà di conseguenza il tipo di punto di contatto.

**Quali altri campi vengono compilati dal punto di contatto dalla chiamata telefonica?**

Sia il tipo di punto di contatto che il tipo medio contengono i dati estratti dal tipo Task.Type. Tutti gli altri punti dati vengono estratti dai dati di tracciamento web e JavaScript.

**Perché questa telefonata non è associata a una sessione Web?**

Innanzitutto, controlla l’Attività per assicurarti che sia presente [!DNL BizibleId] popolato. Se non è presente alcun valore, non è possibile creare un punto di contatto. Questa situazione deve essere aggravata con CallTrackingMetrics.

Se è presente un valore, tieni presente che consideriamo tutte le sessioni web solo 30 minuti. Se un annuncio Google è stato fatto clic alle 12:17 (inizio della sessione sul sito web), ma la telefonata è avvenuta solo alle 13:05, la sessione web e la chiamata non verranno unite. Piuttosto, [!DNL Marketo Measure] crea un [!DNL Salesforce Task] punto di contatto per tenere traccia della chiamata telefonica, ma non avrà dati di sessione web.

![](assets/6.png)

## Partnership {#partnerships}

[!DNL Marketo Measure] attualmente dispone di un partner ufficiale per il tracciamento delle chiamate che ha superato il processo di integrazione &quot;ufficiale&quot; con noi, che include il co-marketing e la formazione sul prodotto. Questo partner è CallTrackingMetrics.
