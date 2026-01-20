---
unique-page-id: 18874592
description: Integrazione tracciamento chiamate - [!DNL Marketo Measure]
title: Integrazione tracciamento chiamate
exl-id: bc35a789-e056-4456-9038-306ed34c2a8e
feature: Tracking, Integration
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# Integrazione tracciamento chiamate {#call-tracking-integration}

L&#39;integrazione con [!DNL CallTrackingMetrics] ha lo scopo di unire una sessione Web con una telefonata. Una telefonata viene trattata come un invio di un modulo a [!DNL Marketo Measure]. Dà credito a una sessione web che altrimenti sarebbe stata considerata solo una visita web perché non c&#39;era un invio effettivo del modulo.

## Informazioni sul tracciamento delle chiamate {#call-tracking-explained}

Il &quot;tracciamento delle chiamate&quot; in senso generale è un prodotto di aziende come [!DNL CallTrackingMetrics], [!DNL DiaglogTech], [!DNL Invoca] o [!DNL CallRail], per citarne alcune. I numeri di telefono univoci vengono visualizzati agli utenti in base ai diversi canali o campagne di marketing da cui provengono. In questo modo gli addetti al marketing possono vedere le prestazioni di tali canali o campagne.

![](assets/1.png)

## Prima e dopo {#before-and-after}

Osservare il diagramma di flusso seguente per vedere come [!DNL Marketo Measure] gestiva le telefonate senza un&#39;integrazione con CallTrackingMetrics. La telefonata che ha avuto luogo è stata detracciata, quindi è stata vista come una sessione web e non è stato creato alcun punto di contatto per essa. Solo durante la visita successiva, quando l’utente completava un modulo, veniva finalmente popolato un punto di contatto.

Con l&#39;integrazione, potete vedere che la sessione web era in realtà legata a una telefonata. Il successivo riempimento del modulo diventa un tocco PostLC e viene ancora tracciato come parte del percorso.

![](assets/2.png)

## Come funziona {#how-it-works}

CallTrackingMetrics deve completare un lavoro di sviluppo affinché questo funzioni. Con il JavaScript inserito sul sito, CallTrackingMetrics può acquisire _biz_uid dal cookie [!DNL Marketo Measure]. Questo &quot;[!DNL BizibleId]&quot; viene quindi archiviato da CallTrackingMetrics.

Quando un visitatore accede al tuo sito e effettua una telefonata, è compito di CallTrackingMetrics inviare tali dati a [!DNL Salesforce].  In genere, viene creato un [!DNL Salesforce Task] che popola dati quali numero di telefono, oggetto, tipo e ora, il [!DNL BizibleId]

[!DNL BizibleId] è un campo installato con la versione 6.7+ del pacchetto di attribuzione marketing [!DNL Marketo Measure].

Di seguito è riportato un esempio di record Attività con [!DNL BizibleId] popolato.

![](assets/3.png)

Quando [!DNL Marketo Measure] trova un record Attività con un valore [!DNL BizibleId] noto compilato, [!DNL Marketo Measure] può mappare l&#39;utente a una sessione Web con lo stesso [!DNL BizibleId] e attribuire tale sessione a una telefonata invece che a una visita Web.

## Punto di contatto {#the-touchpoint}

Quando [!DNL Marketo Measure] può importare/scaricare l&#39;attività, i dettagli vengono elaborati insieme alla sessione Web. Di solito, può essere unita a un referrer o a un annuncio. Nell’esempio seguente, un visitatore ha trovato l’attività tramite un annuncio a pagamento di Google ed ha effettuato una telefonata.

Il tipo [!UICONTROL Touchpoint] &quot;Call&quot; viene estratto dall&#39;attività, dalla schermata precedente, che viene popolata anche da CallTrackingMetrics al momento della creazione dell&#39;attività.

![](assets/4.png)

## Generazione dei rapporti {#reporting}

I valori del tipo di punto di contatto che [!DNL Marketo Measure] invia in genere sono Visita Web, Modulo Web o Chat Web, ma nel caso dei punti di contatto di CallTrackingMetrics il tipo di punto di contatto è Chiamata telefonica. In questo modo gli addetti al marketing possono vedere quali canali assorbono il maggior numero di telefonate e generare ricavi per la loro organizzazione.

![](assets/5.png)

## Domande frequenti {#faq}

**Perché la mia visita Web è di tipo punto di contatto?**

Il campo Tipo punto di contatto viene compilato dal campo Task.Type. Se il campo Task.Type è vuoto, [!DNL Marketo Measure] imposterà automaticamente il tipo di punto di contatto come visita Web. Una volta compilato il campo Task.Type, [!DNL Marketo Measure] leggerà tale valore e compilerà di conseguenza il tipo di punto di contatto.

**Quali altri campi viene popolato dal punto di contatto dalla chiamata telefonica?**

Sia il tipo di punto di contatto che Medium contengono i dati estratti dal tipo Task.Type. Tutti gli altri punti dati vengono estratti dai dati di tracciamento web e JavaScript.

**Perché questa telefonata non è associata a una sessione Web?**

Innanzitutto, controlla l&#39;Attività per assicurarti che sia popolato [!DNL BizibleId]. Se non è presente alcun valore, non è possibile creare un punto di contatto. Questa situazione deve essere aggravata con CallTrackingMetrics.

Se è presente un valore, tieni presente che consideriamo tutte le sessioni web solo 30 minuti. Se è stato fatto clic su un annuncio Google alle 12:17pm (inizio della sessione sul sito Web), ma la telefonata è stata effettuata solo all&#39;1:05pm, la sessione Web e la telefonata non verranno unite. Piuttosto, [!DNL Marketo Measure] crea un punto di contatto [!DNL Salesforce Task] separato per tenere traccia della telefonata, ma non avrà dati di sessione web.

![](assets/6.png)

## Partnership {#partnerships}

[!DNL Marketo Measure] dispone attualmente di un partner ufficiale per il tracciamento delle chiamate che ha superato il processo di integrazione &quot;ufficiale&quot; con noi, che include il co-marketing e la formazione sul prodotto. Questo partner è CallTrackingMetrics.
