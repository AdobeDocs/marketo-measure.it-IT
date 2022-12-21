---
unique-page-id: 18874680
description: "[!DNL Facebook] API - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Facebook] API"
exl-id: d6d18545-baae-4103-b0a6-c3de681ec833
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 1%

---

# [!DNL Facebook] API {#facebook-api}

## Introduzione {#introduction}

Simile ai nostri AdWords e [!DNL Bing Ads] integrazioni, le nostre [!DNL Facebook] l&#39;integrazione esegue due azioni fondamentali:

* Etichetta automatica tutto [!DNL Facebook] Annunci con un [!DNL Marketo Measure] parametro (_bf)
* Scarica le informazioni sui costi degli annunci in tutti gli annunci Facebook attivi

## Come configurare le [!DNL Facebook] Integrazione {#how-to-configure-the-facebook-integration}

Per quanto riguarda la configurazione, ci sono sette passaggi da completare all&#39;interno del [!DNL Marketo Measure] app.

1. Passa a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target=&quot;_blank&quot;} e accedi.
1. In Account personale selezionare **[!UICONTROL Settings]**.
1. In Integrazioni seleziona **[!UICONTROL Connections]**.
1. Seleziona **[!UICONTROL Set Up New Ads Connection]** e apparirà un pop-up. Seleziona **[!UICONTROL Facebook]** e di accedere utilizzando le credenziali Facebook.

   >[!NOTE]
   >
   >La persona che collega la [!DNL Facebook Ads] l&#39;account deve essere un amministratore all&#39;interno della [!DNL Facebook Ads] conto.

1. Una volta [!DNL Marketo Measure] è connesso al tuo account Facebook, fai clic sull’icona a forma di matita accanto all’account .
1. In questa visualizzazione, sposta l’assegnazione tag automatica? passa a &quot;Sì&quot;. Quindi seleziona la casella di controllo che si trova in [!UICONTROL Learn More] per accettare i termini e le condizioni. Assicurati che [!UICONTROL Auto-tagging] l&#39;interruttore è ancora impostato su &#39;[!UICONTROL Yes]&quot;.

## Collegamento dell&#39;account {#connecting-the-account}

![](assets/1.gif)

## Abilitazione dell’assegnazione automatica dei tag {#enabling-autotagging}

>[!NOTE]
>
>Se abiliti l’assegnazione automatica dei tag, verranno reimpostati la cronologia delle conversioni e le prove social di tutti gli annunci a cui assegniamo i tag. Consigliamo vivamente [esportazione di questi dati come CSV](https://www.facebook.com/business/help/205067636197240) prima di attivare l’assegnazione tag automatica.

![](assets/2-2.png)

Dopo aver abilitato l’integrazione, [!DNL Marketo Measure] inizierà a scaricare i costi a livello di annuncio nel [!DNL Marketo Measure Marketing ROI] Dashboard.

Affinché l’integrazione funzioni correttamente, devi abilitare l’assegnazione tag automatica al tuo [!DNL Facebook] conto. Questo consentirà al nostro sistema di aggiungere un parametro _bf in tutti i collegamenti agli annunci. Questo processo aggiungerà il nuovo parametro sopra tutti gli altri parametri di tracciamento che hai già aggiunto al tuo [!DNL Facebook] annunci pubblicitari.

![](assets/3.gif)

## Mappatura dei campi {#field-mapping}

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
   <td><p>Id campagna annunci</p></td> 
   <td><p>[[!DNL Facebook] ID campagna]</p></td> 
  </tr> 
  <tr> 
   <td><p>Nome della campagna pubblicitaria </p></td> 
   <td><p>[[!DNL Facebook] Nome campagna], o [utm_campaign] se fornito</p></td> 
  </tr> 
  <tr> 
   <td><p>Id Gruppo Di Annunci</p></td> 
   <td><p>[[!DNL Facebook] ID set di annunci]</p></td> 
  </tr> 
  <tr> 
   <td><p>Nome gruppo di annunci</p></td> 
   <td><p>[[!DNL Facebook] Nome set di annunci]</p></td> 
  </tr> 
  <tr> 
   <td><p>Origine punto di contatto</p></td> 
   <td><p>"[!DNL Facebook]", o [utm_source] se fornito</p></td> 
  </tr> 
  <tr> 
   <td><p>Medium</p></td> 
   <td><p>"Social", o [utm_medium] se fornito</p></td> 
  </tr> 
  <tr> 
   <td><p>Id annuncio o ID_univoco_creativo (Data Warehouse)</p></td> 
   <td><p>[ID personalizzato generato da utm_content]</p></td> 
  </tr> 
  <tr> 
   <td><p>Contenuto annuncio o Nome_creativo (Data Warehouse)</p></td> 
   <td><p>[utm_content] se fornito</p></td> 
  </tr> 
  <tr> 
   <td><p>Testo della parola chiave o nome_parola chiave (Data Warehouse)</p></td> 
   <td><p>[utm_term] se fornito</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_Unique_Id (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] ID annuncio</p></td> 
  </tr> 
  <tr> 
   <td><p>Nome_annuncio (Data Warehouse)</p></td> 
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
   <td><p>[[!DNL Facebook] Account #]</p></td> 
  </tr> 
  <tr> 
   <td><p>Nome_account (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] Nome account]</p></td> 
  </tr> 
 </tbody> 
</table>

## Domande frequenti {#faq}

**D: Cosa [!DNL Facebook] Gli annunci sono supportati da [!DNL Marketo Measure]?**

R: Carosello, Immagine Singola. Non Video, Presentazione o Raccolta al momento.

**D: Che cosa è la prova sociale?**

R: La prova social è un coinvolgimento visibile come mi piace, clic, commenti e condivisioni.

**D: Cosa succede quando [!DNL Marketo Measure] contrassegna l&#39;annuncio?**

R: [!DNL Facebook] non consente di modificare gli annunci in modo da [!DNL Marketo Measure] deve eliminare il contenuto creativo, che contiene l’URL di destinazione, quindi ricreare l’annuncio con i nuovi parametri.

**D: Perché [!DNL Marketo Measure] aggiorna tutto [!DNL Facebook] Annunci?**

R: La [!DNL Marketo Measure] Il processo consiste nel assegnare tag a tutti gli annunci nel caso in cui vengano riattivati.

**D: Di quale autorizzazione ha bisogno l&#39;utente connesso?**

R: ads_management, e-mail

**D: Quanto tempo può essere necessario per importare i dati di spesa?**

R: 1 ora

**D: Quanto tempo può essere necessario per importare i dati degli annunci?**

R: 4 ore
