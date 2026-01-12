---
description: API [!DNL Facebook] - [!DNL Marketo Measure]
title: API [!DNL Facebook]
exl-id: d6d18545-baae-4103-b0a6-c3de681ec833
feature: APIs, Integration, UTM Parameters
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---


# API [!DNL Facebook] {#facebook-api}

## Introduzione {#introduction}

Analogamente alle integrazioni AdWords e [!DNL Bing Ads], l&#39;integrazione [!DNL Facebook] esegue due azioni fondamentali:

* Applica tag automatici a tutti gli annunci [!DNL Facebook] con un parametro [!DNL Marketo Measure] (_bf)
* Scaricare informazioni sui costi degli annunci in tutti gli annunci attivi di Facebook

## Come configurare l&#39;integrazione di [!DNL Facebook] {#how-to-configure-the-facebook-integration}

Per quanto riguarda la configurazione, è necessario completare sette passaggi nell&#39;app [!DNL Marketo Measure].

1. Passa a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} e accedi.
1. In Il mio account seleziona **[!UICONTROL Settings]**.
1. In Integrazioni, selezionare **[!UICONTROL Connections]**.
1. Selezionare **[!UICONTROL Set Up New Ads Connection]** per visualizzare un popup. Seleziona **[!UICONTROL Facebook]** e accedi utilizzando le tue credenziali Facebook.

   >[!NOTE]
   >La persona che connette l&#39;account [!DNL Facebook Ads] deve essere un amministratore nell&#39;account [!DNL Facebook Ads].

1. Una volta che [!DNL Marketo Measure] è connesso al tuo account Facebook, fai clic sull&#39;icona della matita accanto all&#39;account.
1. All’interno di questa vista, sposta l’assegnazione automatica tag? passa a &#39;Sì&#39;. Selezionare quindi la casella di controllo nella sezione [!UICONTROL Learn More] per accettare i termini e le condizioni. Verificare che l&#39;interruttore [!UICONTROL Auto-tagging] sia ancora impostato su &#39;[!UICONTROL Yes]&#39;.

## Collegamento dell’account {#connecting-the-account}

![Impostazione di una nuova connessione di annunci Facebook in Marketo Measure](assets/1.gif)

## Abilitazione del tag automatico {#enabling-autotagging}

>[!NOTE]
>Se abiliti l’assegnazione tag automatica, verranno reimpostate la cronologia delle conversioni e le bozze social di tutti gli annunci a cui vengono assegnati tag. Ti consigliamo vivamente di [esportare questi dati come CSV](https://www.facebook.com/business/help/205067636197240) prima di abilitare l&#39;assegnazione tag automatica.

![&#x200B; 2](assets/2-2.png)

Dopo aver abilitato l&#39;integrazione, [!DNL Marketo Measure] inizierà a scaricare il costo a livello di annuncio nel dashboard [!DNL Marketo Measure Marketing ROI].

Affinché l&#39;integrazione funzioni correttamente, è necessario abilitare l&#39;assegnazione tag automatica sull&#39;account [!DNL Facebook]. Questo consentirà al nostro sistema di aggiungere un parametro _bf in tutti i collegamenti degli annunci. Questo processo aggiungerà il nuovo parametro oltre a tutti gli altri parametri di tracciamento già aggiunti agli annunci di [!DNL Facebook].

![Abilitazione dell&#39;assegnazione tag automatica nelle impostazioni della connessione Facebook](assets/3.gif)

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
   <td><p>[[!DNL Facebook] ID set di annunci]</p></td>
  </tr>
  <tr>
   <td><p>Nome gruppo di annunci</p></td>
   <td><p>[[!DNL Facebook] nome set di annunci]</p></td>
  </tr>
  <tr>
   <td><p>Source punto di contatto</p></td>
   <td><p>"[!DNL Facebook]" o [utm_source] se fornito</p></td>
  </tr>
  <tr>
   <td><p>Canale</p></td>
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
   <td><p>[[!DNL Facebook] nome annuncio]</p></td>
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
   <td><p>N. account [[!DNL Facebook]]</p></td>
  </tr>
  <tr>
   <td><p>Nome_account (Data Warehouse)</p></td>
   <td><p>[[!DNL Facebook] Nome account]</p></td>
  </tr>
 </tbody>
</table>

## Domande frequenti {#faq}

**Q: quali [!DNL Facebook] annunci sono supportati da [!DNL Marketo Measure]?**

R: Carosello, Immagine Singola. Al momento non ci sono video, presentazioni o raccolte.

**D: Cos&#39;è la bozza social?**

R: per bozza social si intende il coinvolgimento visibile come Mi piace, clic, commenti e condivisioni.

**D: cosa succede quando [!DNL Marketo Measure] assegna i tag all&#39;annuncio?**

R: [!DNL Facebook] non consente la modifica degli annunci quindi [!DNL Marketo Measure] deve eliminare il contenuto creativo, che contiene l&#39;URL di destinazione, e ricreare l&#39;annuncio con i nuovi parametri.

**Q: perché [!DNL Marketo Measure] aggiorna tutti i [!DNL Facebook] annunci?**

R: Il processo [!DNL Marketo Measure] consiste nel assegnare tag a tutti gli annunci nel caso in cui vengano riattivati.

**D: di quale autorizzazione ha bisogno l&#39;utente connesso?**

A: ads_management, e-mail

**Q: quanto tempo è necessario per importare i dati di spesa?**

R: 1 ora

**D: quanto tempo ci vuole per importare i dati degli annunci?**

R: 4 ore
