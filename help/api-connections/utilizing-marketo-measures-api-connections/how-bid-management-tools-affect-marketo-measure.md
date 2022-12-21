---
unique-page-id: 18874720
description: Effetti degli strumenti di gestione delle offerte [!DNL Marketo Measure] - [!DNL Marketo Measure] - Documentazione del prodotto
title: Effetti degli strumenti di gestione delle offerte [!DNL Marketo Measure]
exl-id: 67c00ad9-8b12-4238-8a1f-2d2f5ed04423
source-git-commit: 65e7f8bc198ceba2f873ded23c94601080ad0546
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Effetti degli strumenti di gestione delle offerte [!DNL Marketo Measure] {#how-bid-management-tools-affect-marketo-measure}

Scopri in che modo le piattaforme di gestione delle offerte influiscono su [!DNL Marketo Measure] possibilità di tenere traccia di AdWords e BingAds, insieme a come impostare modelli di tracciamento con i nostri parametri per garantire che tutto venga tracciato correttamente.

Kenshoo e Marin sono ottimi strumenti che consentono agli esperti di marketing di tracciare, gestire e ottimizzare le campagne pubblicitarie con diversi motori di ricerca. Per [!DNL Marketo Measure] parametri da aggiungere a questi URL di annunci, dovrai impostare un modello di tracciamento con il nostro [!DNL Marketo Measure] Parametri. Non è possibile collegare le piattaforme di annunci al tuo [!DNL Marketo Measure] l&#39;account e l&#39;abilitazione dell&#39;assegnazione automatica dei tag in quanto causa la [!DNL Marketo Measure] sistema di marcatura per competere con il sistema di marcatura di Kenshoo/Marin. In questo modo i nostri parametri vengono modificati e aggiunti in modo errato. Per aggirare questo problema, tracciare i modelli con [!DNL Marketo Measure] è necessario stabilire parametri all&#39;interno di Kenshoo e Marin.

## Per [!DNL Adwords] Account {#for-adwords-accounts}

Imposta un modello di tracciamento come segue:

* Fai clic sul pulsante **[!UICONTROL Campaigns]** scheda .
* Fai clic sul pulsante **[!UICONTROL Shared library]** nella barra di navigazione laterale.
* Fai clic su **Opzioni URL**.
* Accanto a &quot;Modello di tracciamento&quot;, fai clic su **Modifica**.
* Compila l’URL:

   * Se TUTTI gli URL degli annunci hanno un &quot;?&quot; in essi, utilizza questo URL:
      * `{lpurl}&_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`
   * Se NESSUNO dei tuoi URL di annunci ha un &quot;?&quot; in essi, utilizza questo URL:
      * `{lpurl}?_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`


## Per [!DNL Bing Ads] Account {#for-bing-ads-accounts}

Imposta un modello di tracciamento come segue:

* Fai clic sul pulsante **[!UICONTROL Campaigns]** scheda .
* Fai clic sul pulsante **[!UICONTROL Shared library]** nella barra di navigazione laterale.
* Fai clic su **Opzioni URL**.
* Accanto a &quot;Modello di tracciamento&quot;, fai clic su **Modifica**.
* Compila l’URL:

   * Se TUTTI gli URL degli annunci hanno un &quot;?&quot; in essi, utilizza questo URL:
      * `{lpurl}&_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
   * Se NESSUNO dei tuoi URL di annunci ha un &quot;?&quot; in essi, utilizza questo URL:
      * `{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
