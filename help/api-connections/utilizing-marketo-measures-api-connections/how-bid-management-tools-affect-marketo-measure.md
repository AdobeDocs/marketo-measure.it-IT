---
unique-page-id: 18874720
description: Effetti degli strumenti di gestione delle offerte [!DNL Marketo Measure] - [!DNL Marketo Measure] - Documentazione del prodotto
title: Effetti degli strumenti di gestione delle offerte [!DNL Marketo Measure]
exl-id: 67c00ad9-8b12-4238-8a1f-2d2f5ed04423
feature: APIs, Integration, UTM Parameters
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Effetti degli strumenti di gestione delle offerte [!DNL Marketo Measure] {#how-bid-management-tools-affect-marketo-measure}

Scopri in che modo le piattaforme di gestione delle offerte influiscono sul [!DNL Marketo Measure] possibilità di tenere traccia di AdWords e BingAds, oltre a come impostare modelli di tracciamento con i nostri parametri per garantire che tutto venga tracciato correttamente.

Kenshoo e Marin sono ottimi strumenti che consentono agli esperti di marketing di monitorare, gestire e ottimizzare le campagne pubblicitarie con diversi motori di ricerca. Per ottenere [!DNL Marketo Measure] parametri da aggiungere a questi URL di annunci, dovrai impostare un modello di tracciamento con [!DNL Marketo Measure] parametri. Non è possibile collegare le piattaforme di annunci al tuo [!DNL Marketo Measure] e abilitare l&#39;assegnazione automatica dei tag in quanto causa [!DNL Marketo Measure] sistema di tagging per competere con il sistema di tagging di Kenshoo/Marin. In questo modo i nostri parametri vengono modificati e aggiunti in modo errato. Per evitare questo problema, i modelli di tracciamento con [!DNL Marketo Measure] I parametri devono essere impostati all’interno di Kenshoo e Marin.

## Per [!DNL Adwords] Account {#for-adwords-accounts}

Imposta un modello di tracciamento come segue:

* Fai clic su **[!UICONTROL Campaigns]** scheda.
* Fai clic su **[!UICONTROL Shared library]** nella barra di navigazione laterale.
* Clic **Opzioni URL**.
* Accanto a &quot;Modello di tracciamento&quot;, fai clic su **Modifica**.
* Inserisci l’URL:

   * Se TUTTI gli URL dell’annuncio hanno un &quot;?&quot; in essi, utilizza questo URL:
      * `{lpurl}&_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`
   * Se NESSUNO degli URL dell’annuncio ha un &quot;?&quot; in essi, utilizza questo URL:
      * `{lpurl}?_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`


## Per [!DNL Bing Ads] Account {#for-bing-ads-accounts}

Imposta un modello di tracciamento come segue:

* Fai clic su **[!UICONTROL Campaigns]** scheda.
* Fai clic su **[!UICONTROL Shared library]** nella barra di navigazione laterale.
* Clic **Opzioni URL**.
* Accanto a &quot;Modello di tracciamento&quot;, fai clic su **Modifica**.
* Inserisci l’URL:

   * Se TUTTI gli URL dell’annuncio hanno un &quot;?&quot; in essi, utilizza questo URL:
      * `{lpurl}&_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
   * Se NESSUNO degli URL dell’annuncio ha un &quot;?&quot; in essi, utilizza questo URL:
      * `{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
