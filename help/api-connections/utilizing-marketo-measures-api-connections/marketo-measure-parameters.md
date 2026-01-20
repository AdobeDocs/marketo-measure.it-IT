---
unique-page-id: 18874608
description: '[!DNL Marketo Measure] Parametri - [!DNL Marketo Measure]'
title: Parametri [!DNL Marketo Measure]
exl-id: d66b9864-0d7e-455a-ae20-cca555f4d8c8
feature: APIs, Integration, UTM Parameters
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Parametri [!DNL Marketo Measure] {#marketo-measure-parameters}

## [!DNL Marketo Measure] parametri spiegati {#marketo-measure-parameters-explained}

Per ottenere ulteriori insight dall&#39;utilizzo di UTM, [!DNL Marketo Measure] aggiunge parametri personalizzati agli annunci in [!DNL Google] AdWords, Bing Ads e [!DNL Facebook] Ads. [!DNL Marketo Measure] si integra con queste piattaforme per automatizzare la maggior parte del processo di installazione. Se si sceglie di utilizzare l&#39;assegnazione tag automatica, [!DNL Marketo Measure] aggiungerà automaticamente i relativi parametri agli URL degli annunci. [!DNL Marketo Measure] scaricherà inoltre automaticamente i costi di marketing dalle piattaforme e li caricherà nell&#39;app [!DNL Marketo Measure].

Esempio di URL senza parametri:

`http://adobe.com/landing-page?myParam=foo`

Esempio di un URL con [!DNL Marketo Measure] parametri:

`http://adobe.com/landing-page?myParam=foo&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Parametri AdWords {#adwords-parameters}

* `_bk={keyword}`
   * Rappresenta la parola chiave utilizzata nel motore di ricerca.
   * È simile al parametro del termine UTM.

* `_bt={creative}`
   * Rappresenta l’ID o il nome della creatività.
   * È simile al parametro di contenuto UTM.

* `_bm={matchtype}`
   * Rappresenta la corrispondenza con la parola chiave.
   * I tipi di corrispondenza delle parole chiave aiutano a controllare quali ricerche attivano l’annuncio. Ad esempio, puoi utilizzare la corrispondenza ampia per mostrare l’annuncio a un pubblico ampio oppure puoi utilizzare la corrispondenza esatta per affinare su gruppi specifici di clienti.
   * I tre tipi di corrispondenza sono: ampia, sfocata ed esatta.

>[!TIP]
>
>Per ulteriori informazioni sui tipi di corrispondenza, [ecco un articolo AdWords pertinente](https://support.google.com/adwords/answer/2497836?hl=en){target="_blank"}.

* `_bn={network}`
   * Rappresenta il tipo di rete dell&#39;annuncio - [visualizzazione o ricerca](https://support.google.com/adwords/answer/1752334?hl=en){target="_blank"}.
   * È simile al parametro Source UTM.

* `_bg={adgroupID}`
   * Rappresenta l’ID del gruppo di annunci a cui appartiene l’annuncio

>[!NOTE]
>
>I parametri degli URL di reindirizzamento non sono supportati.

## Parametri di Bing Ads {#bing-ads-parameters}

* `_bt={adid}`
* `utm_medium=cpc`
* `utm_source=bing`
* `utm_term={keyword}`

## Parametri Facebook {#facebook-parameters}

* `_bf ={creative}`
   * Rappresenta l’ID o il nome della creatività
