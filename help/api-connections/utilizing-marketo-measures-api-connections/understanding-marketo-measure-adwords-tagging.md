---
unique-page-id: 18874678
description: Comprensione [!DNL Marketo Measure] Assegnazione tag AdWords - [!DNL Marketo Measure] - Documentazione del prodotto
title: Comprensione [!DNL Marketo Measure] Assegnazione tag adWords
exl-id: c6658766-d3a8-46ed-b2d2-826eb61ce269
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# Comprensione [!DNL Marketo Measure] Assegnazione tag adWords {#understanding-marketo-measure-adwords-tagging}

Per tenere traccia degli annunci a un livello molto granulare, gli URL di destinazione dell’annuncio devono essere univoci. Per ottenere questo risultato, [!DNL Marketo Measure] l’assegnazione automatica dei tag aggiunge automaticamente parametri di tracciamento agli URL di destinazione dell’annuncio [!DNL AdWords] annunci pubblicitari. Diamo un&#39;occhiata ad un esempio qui sotto.

Il seguente URL non fornirà dati granulari:

* `http://example.com/landing-page?myParam=foo`

Tuttavia, lo stesso URL fornirà dati granulari a causa del [!DNL Marketo Measure] parametri:

* `http://example.com/landing-page?myParam=foo&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Come [!DNL Marketo Measure] L’assegnazione tag automatica funziona {#how-marketo-measure-auto-tagging-works}

**Se [!DNL Marketo Measure] trova un modello di tracciamento:**

* [!DNL Marketo Measure] aggiungerà i relativi parametri al modello di tracciamento.
* Se un reindirizzamento di terze parti si trova in un modello di tracciamento come Kenshoo o Marin, [!DNL Marketo Measure] non intraprenderà alcuna azione. Invece, devi [add [!DNL Marketo Measure] parametri per lo strumento di terze parti nel tuo account](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md){target=&quot;_blank&quot;}.

Tuttavia, se non viene trovato alcun modello di tracciamento, [!DNL Marketo Measure] :

* Analizza tutti gli URL di destinazione dell’annuncio per il nostro [!DNL Marketo Measure] Parametri.
* Se trovato, sei bravo ad andare.
* In caso contrario, [!DNL Marketo Measure] aggiungerà i suoi parametri alla fine degli URL di destinazione dell’annuncio. Per nuovi annunci, [!DNL Marketo Measure] aggiungerà i suoi parametri all’URL di destinazione dell’annuncio entro due ore dalla creazione.
* È importante disporre di un modello di tracciamento prima di abilitare l’assegnazione automatica dei tag in modo che [!DNL Marketo Measure] può allegarlo ed impedire la reimpostazione della cronologia degli annunci.

[!DNL Marketo Measure] consiglia di utilizzare un modello di tracciamento a livello di account, di campagna o di gruppo di annunci, in quanto consente l’aggiunta e la sottrazione di parametri per tutti gli annunci senza il rischio di interruzioni o cancellazione della cronologia annunci.

## Modelli di tracciamento {#tracking-templates}

Come spiegato da [!DNL Google AdWords], un modello di tracciamento è l’URL utilizzato per raggiungere una pagina di destinazione. Le informazioni di tracciamento raccolte vengono utilizzate per comprendere il traffico degli annunci. [Fai clic qui](https://support.google.com/adwords/answer/7197008?hl=en){target=&quot;_blank&quot;} per ulteriori informazioni da Google.

[!DNL Marketo Measure] consiglia di utilizzare un modello di tracciamento a livello di account, di campagna o di gruppo di annunci, in quanto consente l’aggiunta e la sottrazione di parametri per tutti gli annunci senza il rischio di interruzioni o eliminazioni della cronologia annunci.

Esistono due modelli di tracciamento [!DNL Marketo Measure] consiglia di utilizzare. Utilizza quanto segue per determinare quale versione è appropriata:

* Se tutti gli URL degli annunci hanno un &quot;?&quot; in essi, utilizza questo URL:

`{lpurl}&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

* Se nessuno dei tuoi URL di annunci ha un &quot;?&quot; in essi, utilizza questo URL:

`{lpurl}?_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Impostazione di un modello di tracciamento a livello di account {#setting-up-a-tracking-template-at-the-account-level}

1. Accedi al tuo [!DNL Google AdWords] Conto.

1. Fai clic su **[!UICONTROL All campaigns]** e poi **[!UICONTROL Settings]** nella finestra in espansione.

   ![](assets/1.png)

1. Fai clic su **[!UICONTROL Account Settings]** in alto e poi **[!UICONTROL Tracking Template]**. Inserisci il [!DNL Marketo Measure] Modello di tracciamento.

   ![](assets/2-1.png)

1. Clic **[!UICONTROL Save]**.

## Impostazione di un modello di tracciamento a livello di campagna {#setting-up-a-tracking-template-at-the-campaign-level}

1. Fai clic su **[!UICONTROL All campaigns]** e poi **[!UICONTROL Campaigns]** nella finestra in espansione.

   ![](assets/3.png)

1. Seleziona tutte le campagne applicabili o **[!UICONTROL Select All]**, fai clic su **[!UICONTROL Edit]**, quindi fai clic su **[!UICONTROL Change Tracking Templates]**.

   ![](assets/4-1.png)

1. Inserisci il [!DNL Marketo Measure] Modello di tracciamento e fai clic su **[!UICONTROL Apply]**.

## Impostazione di un modello di tracciamento a livello di gruppo di annunci: {#setting-up-a-tracking-template-at-the-ad-group-level}

1. Fai clic su **[!UICONTROL All campaigns]** e poi **[!UICONTROL Ad Groups]** nella finestra in espansione.

   ![](assets/5-1.png)

1. Seleziona tutti i gruppi di annunci applicabili o seleziona tutto, fai clic su **[!UICONTROL Edit]** quindi fai clic su **[!UICONTROL Change Tracking Templates]**.

1. Inserisci il [!DNL Marketo Measure] Modello di tracciamento e fai clic su **[!UICONTROL Apply]**.

   ![](assets/6-1.png)

## Domande frequenti {#faq}

**D: Di quali autorizzazioni ha bisogno l&#39;utente connesso?**

R: userinfo.email

**D: Quanto tempo può essere necessario per importare i dati di spesa?**

R: 6 ore

**D: Quanto tempo può essere necessario per importare i dati degli annunci?**

R: 4 ore

>[!NOTE]
>
>Dopo aver apportato le modifiche, effettua l’operazione. Sentiti libero di contattare [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target=&quot;_blank&quot;} in caso di domande durante l&#39;installazione.

[Fai clic qui](https://support.google.com/adwords/answer/6076199?hl=en#tracking){target=&quot;_blank&quot;} per istruzioni da Google sulla creazione di modelli di tracciamento a livello di account.
