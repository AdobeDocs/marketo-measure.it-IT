---
unique-page-id: 18874680
description: "[!DNL Facebook] API - [!DNL Marketo Measure]"
title: "[!DNL Facebook] API"
exl-id: d6d18545-baae-4103-b0a6-c3de681ec833
feature: APIs, Integration, UTM Parameters
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# [!DNL Facebook] API {#facebook-api}

## Introduzione {#introduction}

Simile a AdWords e [!DNL Bing Ads] integrazioni, il nostro [!DNL Facebook] L&#39;integrazione svolge due azioni fondamentali:

* Assegna tag automatici a tutti [!DNL Facebook] Annunci con una [!DNL Marketo Measure] parametro (_bf)
* Scaricare informazioni sui costi degli annunci in tutti gli annunci Facebook attivi

## Come configurare [!DNL Facebook] Integrazione {#how-to-configure-the-facebook-integration}

Per quanto riguarda la configurazione, è necessario completare sette passaggi entro [!DNL Marketo Measure] app.

1. Accedi a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} e accedi.
1. Sotto Il mio account seleziona **[!UICONTROL Settings]**.
1. In Integrazioni seleziona **[!UICONTROL Connections]**.
1. Seleziona **[!UICONTROL Set Up New Ads Connection]** e viene visualizzato un pop-up. Seleziona **[!UICONTROL Facebook]** e accedi utilizzando le credenziali Facebook.

   >[!NOTE]
   >
   >La persona che collega [!DNL Facebook Ads] deve essere un amministratore all&#39;interno di [!DNL Facebook Ads] account.

1. Una volta [!DNL Marketo Measure] è connesso all’account Facebook, fai clic sull’icona a forma di matita accanto all’account.
1. All’interno di questa vista, sposta l’assegnazione automatica tag? passa a &#39;Sì&#39;. Quindi seleziona la casella di controllo che si trova in [!UICONTROL Learn More] sezione per accettare i termini e le condizioni. Assicurati che le [!UICONTROL Auto-tagging] toggle è ancora impostato su &#39;[!UICONTROL Yes]&quot;.

## Collegamento dell’account {#connecting-the-account}

![](assets/1.gif)

## Abilitazione del tag automatico {#enabling-autotagging}

>[!NOTE]
>
>Se abiliti l’assegnazione tag automatica, verranno reimpostate la cronologia delle conversioni e le bozze social di tutti gli annunci a cui vengono assegnati tag. Consigliamo vivamente [esportazione di questi dati come file CSV](https://www.facebook.com/business/help/205067636197240) prima di attivare l’assegnazione tag automatica.

![](assets/2-2.png)

Dopo aver abilitato l’integrazione, [!DNL Marketo Measure] inizierà a scaricare il costo dell’annuncio nel [!DNL Marketo Measure Marketing ROI] Dashboard.

Affinché l’integrazione funzioni correttamente, devi abilitare l’assegnazione tag automatica sulle [!DNL Facebook] account. Questo consentirà al nostro sistema di aggiungere un parametro _bf in tutti i collegamenti degli annunci. Questo processo aggiunge il nuovo parametro a tutti gli altri parametri di tracciamento già aggiunti al tuo [!DNL Facebook] annunci.

![](assets/3.gif)

## Mappatura campi {#field-mapping}

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th><p><strong>Campo punto di contatto</strong></p></th> 
   <th><p><strong>Valore</strong></p></th> 
  </tr> 
  <tr> 
   <td><p>ID campagna pubblicitaria</p></td> 
   <td><p>[[!DNL Facebook] ID campagna]</p></td> 
  </tr> 
  <tr> 
   <td><p>Nome campagna pubblicitaria </p></td> 
   <td><p>[[!DNL Facebook] Nome campagna], o [utm_campaign] se fornito</p></td> 
  </tr> 
  <tr> 
   <td><p>ID gruppo di annunci</p></td> 
   <td><p>[[!DNL Facebook] ID del set di annunci]</p></td> 
  </tr> 
  <tr> 
   <td><p>Nome gruppo di annunci</p></td> 
   <td><p>[[!DNL Facebook] Nome set di annunci]</p></td> 
  </tr> 
  <tr> 
   <td><p>Sorgente punto di contatto</p></td> 
   <td><p>"[!DNL Facebook]", o [utm_source] se fornito</p></td> 
  </tr> 
  <tr> 
   <td><p>Medium</p></td> 
   <td><p>"Social" o [utm_medium] se fornito</p></td> 
  </tr> 
  <tr> 
   <td><p>ID annuncio o Creative_Unique_Id (Data Warehouse)</p></td> 
   <td><p>[ID personalizzato generato da utm_content]</p></td> 
  </tr> 
  <tr> 
   <td><p>Contenuto annuncio o Creative_Name (Data Warehouse)</p></td> 
   <td><p>[utm_content] se fornito</p></td> 
  </tr> 
  <tr> 
   <td><p>Testo parola chiave o Nome_parola chiave (Data Warehouse)</p></td> 
   <td><p>[utm_term] se fornito</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_Unique_Id (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] ID annuncio]</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_Name (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] Nome annuncio]</p></td> 
  </tr> 
  <tr> 
   <td><p>Keyword_Unique_Id (Data Warehouse)</p></td> 
   <td><p>[ID personalizzato generato da utm_term]</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_Provider (Data Warehouse)</p></td> 
   <td><p>"[!DNL Facebook]"</p></td> 
  </tr> 
  <tr> 
   <td><p>Account_Unique_ID (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] N. account]</p></td> 
  </tr> 
  <tr> 
   <td><p>Nome_account (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] Nome account]</p></td> 
  </tr> 
 </tbody> 
</table>

## Domande frequenti {#faq}

**D: Cosa [!DNL Facebook] Gli annunci sono supportati da [!DNL Marketo Measure]?**

R: Carosello, Immagine Singola. Al momento non ci sono video, presentazioni o raccolte.

**D: Cos’è la bozza social?**

R: per bozza social si intende il coinvolgimento visibile come Mi piace, clic, commenti e condivisioni.

**D: Cosa succede quando [!DNL Marketo Measure] assegna tag all’annuncio?**

R: [!DNL Facebook] non consente la modifica degli annunci in modo [!DNL Marketo Measure] deve eliminare il contenuto creativo, che contiene l’URL di destinazione, e quindi ricreare l’annuncio con i nuovi parametri.

**D: Perché [!DNL Marketo Measure] aggiorna tutto [!DNL Facebook] Annunci?**

R: Il [!DNL Marketo Measure] Il processo consiste nell’assegnare tag a tutti gli annunci nel caso in cui vengano riattivati.

**D: Di quale autorizzazione ha bisogno l’utente connesso?**

A: ads_management, e-mail

**D: Quanto tempo ci vuole per importare i dati di spesa?**

R: 1 ora

**D: Quanto tempo ci vuole per importare i dati degli annunci?**

R: 4 ore
