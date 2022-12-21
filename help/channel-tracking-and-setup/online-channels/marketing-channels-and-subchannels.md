---
unique-page-id: 18874682
description: Canali di marketing e sottocanali - [!DNL Marketo Measure] - Documentazione del prodotto
title: Canali di marketing e sottocanali
exl-id: fbe2a994-cf6d-439c-af96-a562216434cc
source-git-commit: 02f686645e942089df92800d8d14c76215ae558f
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Canali di marketing e sottocanali {#marketing-channels-and-subchannels}

## Finalità {#purpose}

Definizione di un canale e di un canale secondario [!DNL Marketo Measure], il modo in cui si relazionano al contenuto, la differenza tra le due classificazioni e il modo in cui vengono utilizzate all’interno del [!DNL Marketo Measure] app.

## Panoramica {#overview}

I canali di marketing vengono utilizzati per aiutare a categorizzare (o &quot;bucket&quot;) le attività di marketing per facilitarne la creazione di rapporti, sia nel [!DNL Marketo Measure] Dash del ROI e nel tuo CRM. [!DNL Marketo Measure] viene fornito con 12 canali preconfigurati (che puoi personalizzare/rinominare per adattarli alle convenzioni della tua organizzazione), nonché la possibilità di creare ulteriormente canali personalizzati per un filtro ancora più granulare.

Ogni volta che ricevi un visitatore per una delle pagine di contenuto del sito (che si tratti di una pagina web, di un download in white paper, di un URL di pagina, ecc.), tale lead verrà &quot;inserito&quot; in un canale/canale secondario in base a diversi parametri UTM presenti nell’URL:

* Medium
* Fonte
* Campaign
* Pagina di destinazione
* Sito Web di riferimento

Per personalizzare il &quot;bucket&quot; in cui rientreranno i lead in base ai relativi parametri UTM, puoi utilizzare le regole del canale. Per ulteriori informazioni sulla configurazione e la manutenzione delle regole per i canali, [fai clic qui](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md).

Scopri come configurare la [Canali online](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md) e [Canali offline](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md), così come la differenza tra loro.

**Canale di marketing**

Il canale di marketing è il più ampio livello di classificazione e può coprire un&#39;ampia varietà di sottocanali. Puoi considerarli il &quot;tipo&quot; di Subchannel da cui provengono i lead. Esempi di canali di marketing includono **Ricerca A Pagamento, Ricerca Organica, Visualizzazione,** e **Social a pagamento**. Il canale di marketing solitamente corrisponde al valore del parametro utm_medium trovato nell’URL.

**Canale secondario**

I sottocanali sono il secondo pezzo del puzzle quando si intasano i lead in arrivo. I sottocanali raccontano esattamente la storia di _che_ È stata utilizzata l’iterazione del canale di marketing. Ad esempio, all’interno del Canale di social marketing a pagamento, puoi avere dei sottocanali per **AdWords**, **BingAds**, **Facebook**, ecc. Il canale secondario di solito corrisponde al valore del parametro utm_source trovato nell&#39;URL.

## Esempio di caso d’uso {#use-case-example}

Il diagramma seguente illustra un esempio di canale di marketing, canale secondario e contenuto basato su una pagina web con il seguente URL:

* [http://info.bizible.com/intro-guide-b2b-marketing-attribution?utm_source=linkedin&amp;utm_medium=paidsocial](http://info.bizible.com/intro-guide-b2b-marketing-attribution?utm_source=linkedin&amp;utm_medium=paidsocial)*

In questo caso, il contenuto a cui l’utente sta tentando di accedere è la Guida introduttiva all’attribuzione di marketing B2B. [!DNL Marketo Measure] analizzerà l’URL che porta a questo contenuto utilizzando le regole del canale impostate in questa organizzazione e le utilizzerà per eseguire il &quot;bucket&quot; in questo lead nel canale di marketing &quot;Paid Social&quot; e nel canale secondario &quot;LinkedIn&quot;.

![](assets/1.jpg)

Altri esempi...

**Canale di marketing (medio)**

* PPC
* Social a pagamento
* Social organico
* E-mail
* Eventi e conferenze
* Ricerca organica/SEO
* PR
* Programmi di riferimento

**Canale secondario (sorgente punto di contatto)**

* Google AdWords
* BingAds
* Facebook Ads
* Adroll
* Doppio clic
* Capterra
* Campagne Drip
* linkedIn Ads

**Contenuto (white paper, URL della pagina, post di blog)**

* www.adobe.com/blog1
* www.adobe.com/whitepaper
* www.adobe.com/sign-up-now
