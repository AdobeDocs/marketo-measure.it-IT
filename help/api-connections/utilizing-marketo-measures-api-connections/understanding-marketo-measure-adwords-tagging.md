---
unique-page-id: 18874678
description: Informazioni [!DNL Marketo Measure] Assegnazione tag AdWords - [!DNL Marketo Measure] - Documentazione del prodotto
title: Informazioni [!DNL Marketo Measure] Assegnazione tag AdWords
exl-id: c6658766-d3a8-46ed-b2d2-826eb61ce269
feature: APIs, Integration, UTM Parameters
source-git-commit: 3bad77a72c0dea6caf0daadbb594f10f791af715
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Informazioni [!DNL Marketo Measure] Assegnazione tag AdWords {#understanding-marketo-measure-adwords-tagging}

Per tenere traccia degli annunci a un livello molto granulare, gli URL di destinazione dell’annuncio devono essere univoci. A questo scopo, [!DNL Marketo Measure] L’assegnazione automatica dei tag aggiunge automaticamente i parametri di tracciamento agli URL di destinazione dell’annuncio del [!DNL AdWords] annunci. Vediamo un esempio qui sotto.

Il seguente URL non fornirà dati granulari:

* `http://example.com/landing-page?myParam=foo`

Tuttavia, lo stesso URL fornirà dati granulari a causa del [!DNL Marketo Measure] parametri:

* `http://example.com/landing-page?myParam=foo&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Come [!DNL Marketo Measure] Applicazione di tag automatici {#how-marketo-measure-auto-tagging-works}

**Se [!DNL Marketo Measure] trova un modello di tracciamento:**

* [!DNL Marketo Measure] aggiungerà i relativi parametri al modello di tracciamento.
* Se un reindirizzamento di terze parti si trova in un modello di tracciamento come Kenshoo o Marin, [!DNL Marketo Measure] non intraprenderà alcuna azione. Invece, devi [aggiungi [!DNL Marketo Measure] parametri dello strumento di terze parti nel tuo account](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md){target="_blank"}.

Tuttavia, se non viene trovato alcun modello di tracciamento, [!DNL Marketo Measure] consente di:

* Analizza tutti gli URL di destinazione dell’annuncio per [!DNL Marketo Measure] Parametri.
* Se ti trovo, sei a posto.
* Se non viene trovato, [!DNL Marketo Measure] aggiungerà i relativi parametri alla fine degli URL di destinazione dell’annuncio. Per i nuovi annunci, [!DNL Marketo Measure] aggiungerà i relativi parametri all’URL di destinazione dell’annuncio entro due ore dalla creazione.
* È importante disporre di un modello di tracciamento prima di abilitare l’assegnazione tag automatica, in modo che [!DNL Marketo Measure] può collegarsi ad essa e impedire la reimpostazione della cronologia degli annunci.

[!DNL Marketo Measure] consiglia di utilizzare un modello di tracciamento a livello di account, campagna o gruppo di annunci, in quanto consente di aggiungere e sottrarre parametri per tutti gli annunci senza il rischio di interruzioni o eliminazioni della cronologia degli annunci.

## Modelli di tracciamento {#tracking-templates}

Come spiegato da [!DNL Google AdWords], un modello di tracciamento è l’URL utilizzato per raggiungere una pagina di destinazione. Le informazioni di tracciamento raccolte vengono utilizzate per comprendere il traffico dell’annuncio. [Fai clic qui](https://support.google.com/adwords/answer/7197008?hl=en){target="_blank"} per ulteriori informazioni da Google.

[!DNL Marketo Measure] consiglia di utilizzare un modello di tracciamento a livello di account, campagna o gruppo di annunci, in quanto consente di aggiungere e sottrarre parametri per tutti gli annunci senza il rischio di interruzioni o eliminazioni della cronologia degli annunci.

Esistono due modelli di tracciamento [!DNL Marketo Measure] consiglia di utilizzare. Utilizza quanto segue per determinare quale versione è appropriata per te:

* Se tutti gli URL dell’annuncio hanno un &quot;?&quot; in essi, utilizza questo URL:

`{lpurl}&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

* Se nessuno degli URL dell’annuncio ha un &quot;?&quot; in essi, utilizza questo URL:

`{lpurl}?_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Impostazione di un modello di verifica a livello di conto {#setting-up-a-tracking-template-at-the-account-level}

1. Accedi al tuo [!DNL Google AdWords] Account.

1. Clic **[!UICONTROL All campaigns]** e poi **[!UICONTROL Settings]** nella finestra di espansione.

   ![](assets/1.png)

1. Clic **[!UICONTROL Account Settings]** in alto e poi **[!UICONTROL Tracking Template]**. Inserisci il [!DNL Marketo Measure] Modello di tracciamento.

   ![](assets/2-1.png)

1. Clic **[!UICONTROL Save]**.

## Impostazione di un modello di tracciamento a livello di campagna {#setting-up-a-tracking-template-at-the-campaign-level}

1. Clic **[!UICONTROL All campaigns]** e poi **[!UICONTROL Campaigns]** nella finestra di espansione.

   ![](assets/3.png)

1. Seleziona tutte le campagne applicabili oppure **[!UICONTROL Select All]**, fai clic su **[!UICONTROL Edit]** e quindi fare clic su **[!UICONTROL Change Tracking Templates]**.

   ![](assets/4-1.png)

1. Inserisci il [!DNL Marketo Measure] Modello di tracciamento e clic **[!UICONTROL Apply]**.

## Impostazione di un modello di tracciamento a livello di gruppo di annunci: {#setting-up-a-tracking-template-at-the-ad-group-level}

1. Clic **[!UICONTROL All campaigns]** e poi **[!UICONTROL Ad Groups]** nella finestra di espansione.

   ![](assets/5-1.png)

1. Seleziona tutti i gruppi di annunci applicabili o Seleziona tutto, fai clic su **[!UICONTROL Edit]** e quindi fare clic su **[!UICONTROL Change Tracking Templates]**.

1. Inserisci il [!DNL Marketo Measure] Modello di tracciamento e clic **[!UICONTROL Apply]**.

   ![](assets/6-1.png)

## Domande frequenti {#faq}

**D: Di quali autorizzazioni ha bisogno l’utente connesso?**

R: userinfo.email

**D: Quanto tempo ci vuole per importare i dati di spesa?**

R: 6 ore

**D: Quanto tempo ci vuole per importare i dati degli annunci?**

R: 4 ore

**D: per gli annunci di Dynamic Search Ads, è possibile tenere traccia della combinazione di titolo, descrizione e così via nella creatività distribuita?**

R: Non è possibile recuperare singoli dettagli creativi per gli annunci di ricerca dinamica, ma se è abilitato il tag automatico possiamo comunque ottenere l’ID creativo e i ricavi degli attributi.

>[!NOTE]
>
>Dopo aver apportato le modifiche, l’operazione è completata. Sentiti libero di raggiungere [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} in caso di domande durante la configurazione.

[Fai clic qui](https://support.google.com/adwords/answer/6076199?hl=en#tracking){target="_blank"} per istruzioni da Google sulla creazione di modelli di tracciamento a livello di account.
