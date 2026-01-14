---
description: Linee guida per canali di marketing e sottocanali per gli utenti Marketo Measure
title: Canali marketing e sottocanali
exl-id: fbe2a994-cf6d-439c-af96-a562216434cc
feature: Channels
hidefromtoc: true
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 2%

---

# Canali marketing e sottocanali {#marketing-channels-and-subchannels}

## Finalità {#purpose}

Per definire cosa sono un canale e un sottocanale in [!DNL Marketo Measure], come si relazionano al contenuto, la differenza tra le due classificazioni e come vengono utilizzati nell&#39;app [!DNL Marketo Measure].

## Panoramica {#overview}

I canali di marketing vengono utilizzati per aiutare a categorizzare (o &quot;bucket&quot;) le attività di marketing per semplificare la generazione di rapporti, sia nel Dash ROI di [!DNL Marketo Measure] che nel CRM. [!DNL Marketo Measure] include 12 canali predefiniti (che puoi personalizzare o rinominare in base alle convenzioni della tua organizzazione) e la possibilità di creare ulteriori canali personalizzati per un filtro ancora più granulare.

Ogni volta che ricevi un visitatore di una delle pagine di contenuto sul tuo sito (che si tratti di una pagina web, di un download di white paper, di un URL della pagina, ecc.), tale lead viene &quot;inserito&quot; in un canale/sottocanale in base a diversi parametri UTM trovati nell’URL:

* Canale
* Origine
* Campaign
* Pagina di destinazione
* Sito Web di riferimento

Per personalizzare in quale &quot;bucket&quot; rientreranno i lead in base ai loro parametri UTM, puoi utilizzare le regole del canale. Per ulteriori informazioni sulla configurazione e la manutenzione delle regole del canale, [fai clic qui](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md).

Scopri come configurare i [canali online](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md) e [canali offline](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md) e la differenza tra di essi.

**Canale di marketing**

Il canale di marketing è il livello di classificazione più ampio e può coprire un’ampia varietà di sottocanali. Puoi considerarli il &quot;tipo&quot; di Sottocanale da cui provengono i lead. Esempi di canali di marketing includono **Ricerca a pagamento, Ricerca organica, Visualizzazione,** e **Social a pagamento**. Il canale di marketing in genere corrisponde al valore del parametro utm_medium presente nell’URL.

**Sottocanale**

I sottocanali sono il secondo elemento del puzzle quando si inseriscono i lead in arrivo. I sottocanali raccontano esattamente la storia di _quale_ iterazione del tuo canale di marketing è stata utilizzata. Ad esempio, all&#39;interno del canale di social marketing a pagamento, potresti avere dei sottocanali per **AdWords**, **BingAds**, **Facebook**, ecc. Il sottocanale in genere corrisponde al valore del parametro utm_source presente nell’URL.

## Esempio di caso d’uso {#use-case-example}

Il diagramma seguente illustra un esempio di canale di marketing, sottocanale e contenuto basato su una pagina web con il seguente URL:

* [http://info.bizible.com/intro-guide-b2b-marketing-attribution?utm_source=linkedin&amp;utm_medium=paidsocial](http://info.bizible.com/intro-guide-b2b-marketing-attribution?utm_source=linkedin&utm_medium=paidsocial)*

In questo caso, il contenuto a cui l’utente sta tentando di accedere è la Guida introduttiva all’attribuzione B2B di marketing. [!DNL Marketo Measure] analizzerà l&#39;URL che porta a questo contenuto utilizzando le regole di canale impostate in questa organizzazione e le utilizzerà per &quot;bucket&quot; di questo lead nel canale di marketing &quot;Paid Social&quot; e nel sottocanale &quot;LinkedIn&quot;.

![](assets/online-channels-1.png)

Altri esempi...

**Canale di marketing (Medium)**

* PPC
* Social a pagamento
* Organic Social
* E-mail
* Eventi e conferenze
* Ricerca organica/SEO
* PR
* Programmi di riferimento

**Sottocanale (punto di contatto Source)**

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
