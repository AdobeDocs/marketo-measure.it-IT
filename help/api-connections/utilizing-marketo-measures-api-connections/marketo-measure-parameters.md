---
unique-page-id: 18874608
description: "[!DNL Marketo Measure] Parametri - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] Parametri"
exl-id: d66b9864-0d7e-455a-ae20-cca555f4d8c8
source-git-commit: 65e7f8bc198ceba2f873ded23c94601080ad0546
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# [!DNL Marketo Measure] Parametri {#marketo-measure-parameters}

## [!DNL Marketo Measure] Parametri spiegati {#marketo-measure-parameters-explained}

Per ottenere ulteriori informazioni dall&#39;uso degli UPM, [!DNL Marketo Measure] aggiunge parametri personalizzati ai tuoi annunci in [!DNL Google] AdWords, Bing Ads e [!DNL Facebook] Annunci. [!DNL Marketo Measure] si integra con queste piattaforme per automatizzare la maggior parte del processo di configurazione. Se scegli di utilizzare l’assegnazione tag automatica, [!DNL Marketo Measure] aggiungerà automaticamente i relativi parametri agli URL degli annunci. [!DNL Marketo Measure] scarica automaticamente i costi di marketing dalle piattaforme e li carica nel [!DNL Marketo Measure] app.

Esempio di URL senza parametri:

`http://adobe.com/landing-page?myParam=foo`

Esempio di URL con [!DNL Marketo Measure] parametri:

`http://adobe.com/landing-page?myParam=foo&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Parametri AdWords {#adwords-parameters}

* `_bk={keyword}`
   * Rappresenta la parola chiave utilizzata nel motore di ricerca.
   * È simile al parametro del termine UTM.

* `_bt={creative}`
   * Rappresenta l&#39;ID o il nome creativo.
   * È simile al parametro di contenuto UTM.

* `_bm={matchtype}`
   * Rappresenta la corrispondenza tra la parola chiave e la parola chiave.
   * I tipi di corrispondenza delle parole chiave consentono di controllare quali ricerche attivano l’annuncio. Ad esempio, puoi utilizzare un’ampia corrispondenza per mostrare il tuo annuncio a un pubblico ampio o puoi utilizzare una corrispondenza esatta per interagire con specifici gruppi di clienti.
   * I tre tipi di corrispondenza sono: largo, sfocato e esatto.

>[!NOTE]
>
>Per ulteriori informazioni sui tipi di corrispondenza, [ecco un articolo AdWords pertinente](https://support.google.com/adwords/answer/2497836?hl=en){target=&quot;_blank&quot;}.

* `_bn={network}`
   * Rappresenta il tipo di rete pubblicitaria - [visualizzazione o ricerca](https://support.google.com/adwords/answer/1752334?hl=en){target=&quot;_blank&quot;}.
   * È simile al parametro UTM Source.

* `_bg={adgroupID}`
   * Rappresenta l’ID del gruppo di annunci a cui appartiene l’annuncio

## Parametri Bing Ads {#bing-ads-parameters}

* `_bt={adid}`
* `utm_medium=cpc`
* `utm_source=bing`
* `utm_term={keyword}`

## Parametri facebook {#facebook-parameters}

* `_bf ={creative}`
   * Rappresenta l&#39;ID o il nome creativo
