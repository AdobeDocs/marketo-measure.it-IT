---
unique-page-id: 18874720
description: Effetti degli strumenti di gestione delle offerte su  [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Effetti degli strumenti di gestione delle offerte [!DNL Marketo Measure]
exl-id: 67c00ad9-8b12-4238-8a1f-2d2f5ed04423
feature: APIs, Integration, UTM Parameters
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# Effetti degli strumenti di gestione delle offerte su [!DNL Marketo Measure] {#how-bid-management-tools-affect-marketo-measure}

Scopri in che modo le piattaforme di gestione delle offerte influiscono sulla capacità di [!DNL Marketo Measure] di tenere traccia di AdWords e BingAds, nonché come impostare modelli di tracciamento con i nostri parametri per garantire che tutto venga tracciato correttamente.

Kenshoo e Marin sono ottimi strumenti che consentono agli esperti di marketing di monitorare, gestire e ottimizzare le campagne pubblicitarie con diversi motori di ricerca. Per aggiungere i parametri [!DNL Marketo Measure] a questi URL di annunci, devi impostare un modello di tracciamento con i nostri parametri [!DNL Marketo Measure]. Non è possibile collegare le piattaforme di annunci al tuo account [!DNL Marketo Measure] e abilitare l&#39;assegnazione automatica dei tag, poiché il sistema di assegnazione dei tag [!DNL Marketo Measure] è in concorrenza con il sistema di assegnazione dei tag di Kenshoo/Marin. In questo modo i nostri parametri vengono modificati e aggiunti in modo errato. Per evitare questo problema, è necessario configurare i modelli di tracciamento con [!DNL Marketo Measure] parametri all&#39;interno di Kenshoo e Marin.

## Per gli account [!DNL Adwords] {#for-adwords-accounts}

Imposta un modello di tracciamento come segue:

* Fare clic sulla scheda **[!UICONTROL Campaigns]**.
* Fare clic sul collegamento **[!UICONTROL Shared library]** nella barra di spostamento laterale.
* Fare clic su **Opzioni URL**.
* Accanto a &quot;Modello di tracciamento&quot;, fare clic su **Modifica**.
* Inserisci l’URL:

   * Se TUTTI gli URL dell’annuncio hanno un &quot;?&quot; in essi, utilizza questo URL:
      * `{lpurl}&_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`
   * Se NESSUNO degli URL dell’annuncio ha un &quot;?&quot; in essi, utilizza questo URL:
      * `{lpurl}?_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`


## Per gli account [!DNL Bing Ads] {#for-bing-ads-accounts}

Imposta un modello di tracciamento come segue:

* Fare clic sulla scheda **[!UICONTROL Campaigns]**.
* Fare clic sul collegamento **[!UICONTROL Shared library]** nella barra di spostamento laterale.
* Fare clic su **Opzioni URL**.
* Accanto a &quot;Modello di tracciamento&quot;, fare clic su **Modifica**.
* Inserisci l’URL:

   * Se TUTTI gli URL dell’annuncio hanno un &quot;?&quot; in essi, utilizza questo URL:
      * `{lpurl}&_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
   * Se NESSUNO degli URL dell’annuncio ha un &quot;?&quot; in essi, utilizza questo URL:
      * `{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
