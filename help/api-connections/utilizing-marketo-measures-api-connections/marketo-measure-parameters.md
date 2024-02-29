---
unique-page-id: 18874608
description: "[!DNL Marketo Measure] Parametri - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Parameters"
exl-id: d66b9864-0d7e-455a-ae20-cca555f4d8c8
feature: APIs, Integration, UTM Parameters
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# [!DNL Marketo Measure] Parametri {#marketo-measure-parameters}

## [!DNL Marketo Measure] Spiegazione dei parametri {#marketo-measure-parameters-explained}

Per ottenere ulteriori informazioni dall&#39;uso di UTM, [!DNL Marketo Measure] aggiunge parametri personalizzati agli annunci in [!DNL Google] AdWords, Bing Ads e [!DNL Facebook] Annunci. [!DNL Marketo Measure] si integra con queste piattaforme per automatizzare la maggior parte del processo di configurazione. Se selezioni di utilizzare l’assegnazione tag automatica, [!DNL Marketo Measure] aggiungerà automaticamente i parametri agli URL degli annunci. [!DNL Marketo Measure] scarica automaticamente i costi di marketing dalle piattaforme e li carica nel [!DNL Marketo Measure] app.

Esempio di URL senza parametri:

`http://adobe.com/landing-page?myParam=foo`

Esempio di URL con [!DNL Marketo Measure] parametri:

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
>Per ulteriori informazioni sui tipi di corrispondenza, [ecco un articolo AdWords rilevante](https://support.google.com/adwords/answer/2497836?hl=en){target="_blank"}.

* `_bn={network}`
   * Rappresenta il tipo di rete dell’annuncio - [visualizzare o cercare](https://support.google.com/adwords/answer/1752334?hl=en){target="_blank"}.
   * È simile al parametro Origine UTM.

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

## Parametri facebook {#facebook-parameters}

* `_bf ={creative}`
   * Rappresenta l’ID o il nome della creatività
