---
unique-page-id: 18874682
description: Canali marketing e sottocanali - [!DNL Marketo Measure]
title: Canali marketing e sottocanali
exl-id: fbe2a994-cf6d-439c-af96-a562216434cc
feature: Channels
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 1%

---

# Canali marketing e sottocanali {#marketing-channels-and-subchannels}

## Finalità {#purpose}

Per definire cosa sono un canale e un sottocanale [!DNL Marketo Measure], il modo in cui si relazionano al contenuto, la differenza tra le due classificazioni e il modo in cui vengono utilizzate all&#39;interno del [!DNL Marketo Measure] app.

## Panoramica {#overview}

I canali di marketing vengono utilizzati per aiutare a categorizzare (o &quot;bucket&quot;) le attività di marketing per facilitarne la generazione di rapporti, sia nel [!DNL Marketo Measure] ROI Dash e nel tuo CRM. [!DNL Marketo Measure] viene fornito con 12 canali predefiniti (che puoi personalizzare o rinominare in base alle convenzioni della tua organizzazione), nonché la possibilità di creare ulteriormente canali personalizzati per un filtro ancora più granulare.

Ogni volta che ricevi un visitatore di una delle pagine di contenuto sul tuo sito (che si tratti di una pagina web, di un download di white paper, di un URL della pagina, ecc.), tale lead viene &quot;inserito&quot; in un canale/sottocanale in base a diversi parametri UTM trovati nell’URL:

* Medium
* Origine
* Campaign
* Pagina di destinazione
* Sito Web di riferimento

Per personalizzare in quale &quot;bucket&quot; rientreranno i lead in base ai loro parametri UTM, puoi utilizzare le regole del canale. Per ulteriori informazioni sulla configurazione e la manutenzione delle regole del canale, [fai clic qui](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md).

Scopri come configurare il [Canali online](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md) e [Canali offline](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)e la differenza tra di essi.

**Canale di marketing**

Il canale di marketing è il livello di classificazione più ampio e può coprire un’ampia varietà di sottocanali. Puoi considerarli il &quot;tipo&quot; di Sottocanale da cui provengono i lead. Esempi di canali di marketing includono **Ricerca a pagamento, Ricerca organica, Visualizzazione,** e **Social a pagamento**. Il canale di marketing in genere corrisponde al valore del parametro utm_medium presente nell’URL.

**Sottocanale**

I sottocanali sono il secondo elemento del puzzle quando si inseriscono i lead in arrivo. I sottocanali raccontano esattamente la storia di _che_ è stata utilizzata l’iterazione del canale di marketing. Ad esempio, all’interno del canale di social marketing a pagamento, potresti disporre di sottocanali per **AdWords**, **BingAds**, **Facebook**, ecc. Il sottocanale in genere corrisponde al valore del parametro utm_source presente nell’URL.

## Esempio di caso d’uso {#use-case-example}

Il diagramma seguente illustra un esempio di canale di marketing, sottocanale e contenuto basato su una pagina web con il seguente URL:

* [http://info.bizible.com/intro-guide-b2b-marketing-attribution?utm_source=linkedin&amp;utm_medium=paidsocial](http://info.bizible.com/intro-guide-b2b-marketing-attribution?utm_source=linkedin&amp;utm_medium=paidsocial)*

In questo caso, il contenuto a cui l’utente sta tentando di accedere è la Guida introduttiva all’attribuzione B2B di marketing. [!DNL Marketo Measure] analizzerà l’URL che porta a questo contenuto utilizzando le Regole di canale impostate in questa organizzazione e le utilizzerà per &quot;bucket&quot; di questo lead nel canale di marketing &quot;Paid Social&quot; e nel sottocanale &quot;LinkedIn&quot;.

![](assets/1.jpg)

Altri esempi...

**Canale di marketing (medio)**

* PPC
* Social a pagamento
* Organic Social
* E-mail
* Eventi e conferenze
* Ricerca organica/SEO
* PR
* Programmi di riferimento

**Sottocanale (origine punto di contatto)**

* Google AdWords
* BingAds
* Facebook Ads
* Adroll
* Doppio clic
* Capterra
* Eliminare le campagne
* LinkedIn Ads

**Contenuto (white paper, URL pagina, post di blog)**

* www.adobe.com/blog1
* www.adobe.com/whitepaper
* www.adobe.com/sign-up-now
