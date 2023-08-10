---
unique-page-id: 18874594
description: Piattaforme di annunci integrate - [!DNL Marketo Measure] - Documentazione del prodotto
title: Piattaforme di annunci integrate
exl-id: df30ee8a-8b07-4f14-94e8-cc482fca8b18
feature: APIs, Integration
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '1696'
ht-degree: 0%

---

# Piattaforme di annunci integrate {#integrated-ad-platforms}

[!DNL Marketo Measure] dispone di connessioni API con Google AdWords, Microsoft BingAds, [!DNL Facebook] Annunci e DoubleClick Campaign Manager. Attraverso queste connessioni API, [!DNL Marketo Measure] è in grado di estrarre facilmente i dati e inviarli al CRM insieme all’app esterna dell’acquirente. Non è richiesto alcun caricamento manuale di costi o dati. Piuttosto, i tuoi account devono semplicemente essere collegati e autorizzati al [!DNL Marketo Measure] app. [!DNL Marketo Measure] scaricherà quindi automaticamente i costi di marketing dalle piattaforme e li caricherà nel [!DNL Marketo Measure] app. Se selezioni di abilitare l’assegnazione tag automatica per AdWords, BingAds o [!DNL Facebook] Annunci, [!DNL Marketo Measure] aggiungerà automaticamente i parametri agli URL degli annunci.

## Come collegare le piattaforme di annunci {#how-to-connect-ad-platforms}

Prima di entrare nelle specifiche di ogni piattaforma, esamineremo come collegare uno qualsiasi di questi account a [!DNL Marketo Measure]. Accedi prima a [!DNL Marketo Measure] e passare alla **[!UICONTROL Settings]** opzione sotto **[!UICONTROL My Account]** in alto a sinistra nella schermata. Quindi, seleziona **[!UICONTROL Connections]** sotto **[!UICONTROL Integrations]** sezione a sinistra.

Come mostrato nell’immagine seguente, verrà visualizzato un pulsante per impostare nuove connessioni di annunci.

![](assets/2.png)

Dopo aver fatto clic su [!UICONTROL Set up New Ads Connection] , una finestra (mostrata di seguito) apparirà con quattro annunci [!UICONTROL connect]tipi di ioni. Facendo clic su Connetti verrà visualizzata un&#39;altra finestra in cui viene richiesto di immettere le credenziali. Immetti le credenziali e fai clic su [!UICONTROL authorize] per collegare l&#39;account a [!DNL Marketo Measure].

![](assets/select-account-type.png)

## Google AdWords {#google-adwords}

Quando crei i tuoi annunci in [!DNL Google AdWords]In questo caso, ti consigliamo di assegnare i tag alle campagne in uno dei tre modi seguenti: tag manuali, tag automatici o creazione di un modello di tracciamento. L’assegnazione manuale di tag all’URL di AdWords si basa sulla definizione e sull’aggiunta dei parametri alla fine degli URL degli annunci. L’assegnazione manuale dei tag consente a qualsiasi piattaforma non Google di leggere facilmente i dati raccolti dai parametri.

Il modello di tracciamento è uno strumento fornito da Google per aggiungere quelli che chiama parametri ValueTrack. Funzionano allo stesso modo degli UTM e di altri parametri di assegnazione tag.

## Che cosa accade quando è abilitata l’assegnazione tag automatica {#what-happens-when-auto-tagging-is-enabled}

[!DNL Marketo Measure] Cerca modelli di tracciamento nel tuo [!DNL AdWords] account:

* *Opzione A*: modello di tracciamento trovato. [!DNL Marketo Measure] aggiunge i relativi parametri al modello.
* *Opzione B*: trovato reindirizzamento di terze parti. Se nel modello di tracciamento viene trovato un reindirizzamento di terze parti, [!DNL Marketo Measure] non può eseguire alcuna azione. Sarà necessario aggiungere manualmente il [!DNL Marketo Measure] al sistema di terze parti. Un esempio di reindirizzamento di terze parti potrebbe essere uno strumento di gestione delle offerte come Kenshoo o Marin. Ulteriori informazioni su come [gli strumenti di gestione delle offerte interessano [!DNL Marketo Measure]](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md){target="_blank"}.

* *Opzione C*: non è stato trovato alcun modello di tracciamento. [!DNL Marketo Measure] eseguirà la scansione di tutti gli URL di destinazione dell’annuncio per [!DNL Marketo Measure] parametri. In base alla scansione, se:
   * Sono stati trovati dei parametri: la configurazione è stata completata.
   * Parametri non trovati: [!DNL Marketo Measure] aggiungerà i relativi parametri alla fine degli URL di destinazione dell’annuncio. [!DNL Marketo Measure] aggiunge nuovi annunci entro due ore dalla loro creazione. I parametri non verranno aggiunti a un modello.

Ulteriori informazioni sulla [[!DNL AdWords] funzionalità di assegnazione tag automatica](/help/api-connections/utilizing-marketo-measures-api-connections/understanding-marketo-measure-adwords-tagging.md){target="_blank"}.

## Come abilitare [!DNL Marketo Measure] Assegnazione automatica tag per AdWords {#how-to-enable-marketo-measure-auto-tagging-for-adwords}

Prima dell’abilitazione [!DNL Marketo Measure] assegnazione automatica tag, **accertati di avere un modello di tracciamento abilitato a livello di account, campagna o gruppo di annunci all’interno dell’account Adwords. Questo è richiesto per qualsiasi account Adwords che avrà [!DNL Marketo Measure] assegnazione automatica tag abilitata.** L’abilitazione di un modello di tracciamento impedisce qualsiasi perdita di dati nella cronologia delle prestazioni degli annunci. Tieni presente che l’abilitazione dei modelli di tracciamento a livello di parola chiave, collegamento Sitelink o annuncio determinerà il completamento del processo di revisione e approvazione dell’annuncio e potrebbe potenzialmente riavviare la cronologia delle prestazioni degli annunci. Se non è abilitato alcun modello di tracciamento, [!DNL Marketo Measure] aggiungerà [!DNL Marketo Measure] parametri di tracciamento direttamente nell’&quot;URL finale&quot; dell’annuncio che può anche causare la perdita di dati della cronologia dell’annuncio.

Dopo aver impostato un modello di tracciamento, segui le istruzioni riportate di seguito per abilitare [!DNL Marketo Measure] Assegnazione automatica tag. Nota: [!DNL Marketo Measure] Inoltre, assegnerà automaticamente un tag agli annunci in pausa nel tuo account.

1. Accedi al tuo [!DNL Marketo Measure] account in [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

1. Vai a [!UICONTROL My Account] > [!UICONTROL Settings] > [!UICONTROL Integrations] > [!UICONTROL Connections].

   ![](assets/4.png)

1. Fai clic sull’icona a forma di matita accanto all’account Adwords che sarà [!DNL Marketo Measure] assegnazione automatica tag abilitata.

   ![](assets/5.png)

1. Nell’angolo in alto a destra, attiva **[!UICONTROL Autotagging]** passa a **[!UICONTROL Yes]**. Nella parte inferiore della pagina, fai clic su **[!UICONTROL Learn More]** per espandere la casella di testo e fare clic su **[!UICONTROL Save]**. Impostazione assegnazione automatica tag completata.

   ![](assets/6.png)

## Impostare un modello di tracciamento in AdWords con [!DNL Marketo Measure] Parametri {#how-to-set-up-a-tracking-template-in-adwords-with-marketo-measure-parameters}

Tieni presente che devi aggiungere modelli di tracciamento in corrispondenza di [!UICONTROL Account], [!UICONTROL Campaign] o a livello di gruppo di annunci in AdWords. Se aggiungi modelli di tracciamento al livello Parola chiave, Sitelink o Annuncio, il tuo annuncio dovrà seguire il processo di revisione e approvazione e rischi di riavviare la cronologia delle prestazioni degli annunci. Ulteriori informazioni su [creazione di modelli di tracciamento](https://support.google.com/adwords/answer/6076199?hl=en#tracking){target="_blank"}.

1. Accedi al tuo [!DNL Google AdWords] Account.
1. Vai al tuo [!UICONTROL Campaigns] visualizzazione dalla barra di navigazione a sinistra
1. Passa a &quot;[!UICONTROL Settings]&quot;, anche nella barra di navigazione a sinistra
1. Passa a &quot;[!UICONTROL Account Settings]&quot; vista dall&#39;alto
1. Espandi la sezione &quot;[!UICONTROL Tracking]sezione &quot;
1. Incolla una delle seguenti stringhe di testo nel modello di tracciamento per impostare il valore del modello:

   * Se hai dei punti interrogativi in TUTTI gli URL, utilizza il seguente testo URL:

   `{lpurl}&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

   * Se non hai punti interrogativi su nessuno degli URL, aggiungi il seguente testo URL:

   `{lpurl}?_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}*`

   Per evitare errori quando si applicano tag manuali agli URL, in genere si consiglia di generare automaticamente i parametri UTM. Questo non deve significare l’assegnazione automatica di tag con AdWords o [!DNL Marketo Measure] , esistono diversi strumenti che semplificano il processo generando automaticamente i parametri per l’URL in base alle informazioni fornite.

   >[!TIP]
   >
   >Se ricevi un errore che indica che il modello di tracciamento non è valido, prova a cancellare la cache del browser e riprova, spesso per risolvere il problema.

## Come generare automaticamente i tag UTM per [!DNL Google AdWords] {#how-to-automatically-generate-utm-tags-for-google-adwords}

All’inizio i tag UTM possono sembrare difficili da creare, ma sono disponibili molti strumenti per creare facilmente URL con parametri UTM. Puoi utilizzare una qualsiasi delle seguenti risorse o cercare sul web altri strumenti. Nota bene [!DNL Marketo Measure] non approva né garantisce nulla con queste piattaforme e strumenti.

**[!DNL Google URL]Builder**

Google URL Builder è uno strumento standard per la creazione di URL formattati correttamente con tag UTM. Inserisci l’URL e il valore desiderato per ciascun parametro, quindi fai clic su &quot;[!UICONTROL Generate URL]&quot;. Questo è uno strumento ideale da utilizzare se disponi solo di una manciata di URL da assegnare ai tag. Accedere allo strumento [qui](https://support.google.com/analytics/answer/1033867?hl=en){target="_blank"}.

**Foglio di calcolo Google generato da EpikOne**

Questo foglio di calcolo contiene una formula che genererà automaticamente gli URL di destinazione con tag. Questo è un ottimo strumento da utilizzare se è necessario assegnare tag a un numero elevato di collegamenti. Accedere al foglio di calcolo [qui](https://spreadsheets.google.com/ccc?key=p7c_HKcmspSUfEYSO0gskKw&amp;hl=en){target="_blank"}.

**Strumento di assegnazione tag collegamento Rafflecopter**

Il foglio di calcolo creato da Rafflecopter è una versione modificata di [!DNL EpikOne's] foglio di calcolo. Contiene inoltre una formula che genera automaticamente i collegamenti di destinazione con tag da utilizzare.

Ognuno di questi strumenti contiene istruzioni dettagliate su come utilizzarlo e modificarlo in base alle tue esigenze. Lo strumento è disponibile [qui](https://docs.google.com/spreadsheets/d/1QCIr1WUJQHE68cA4VTks2XE7nxuryaUymCEy_23-Oew/edit#gid=0){target="_blank"}.

**Generatore UTM straordinario di Effin**

Questo strumento è un’estensione di Chrome che consente di generare rapidamente tag UTM. Trova [qui](https://chrome.google.com/webstore/detail/effin-amazing-utm-builder/eoaapiimcaimddnfhfnifgkinmpcbccp?hl=en){target="_blank"}.

## Bing Ads {#bing-ads}

Bing Ads è una piattaforma integrata che consente di abilitare l’assegnazione tag automatica per gli URL o di utilizzare uno strumento di terze parti, ad esempio [!DNL Marketo Measure], per assegnare tag agli annunci. [!DNL Bing Ads] si basa anche sui parametri UTM.

La funzione di assegnazione automatica tag di Bing Ads aggiunge i seguenti parametri UTM:

* Utm_source
* Utm_medium
* Utm_term

L’assegnazione automatica tag di Bing Ads aggiunge anche il seguente parametro personalizzato:

`_bt={adid}`

La stringa sarà simile alla seguente:

`{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`

È importante notare che [!DNL Bing Ads] consente di aggiungere ancora più parametri utilizzando i tag personalizzati negli URL finali per ottenere maggiore granularità, se lo desideri.

Puoi utilizzare un modello di tracciamento, se necessario, ma non è necessario per [!DNL Bing Ads] e [!DNL Marketo Measure] da integrare. Questo perché [!DNL Bing] consente di modificare gli annunci senza modificare la cronologia, in modo [!DNL Marketo Measure] è in grado di aggiornare l’URL di destinazione.

L’assegnazione tag automatica deve essere abilitata tramite [!DNL Marketo Measure] in modo che il personalizzato [!DNL Marketo Measure] I parametri possono essere aggiunti automaticamente. Con Bing Ads non si corre il rischio di perdere la cronologia delle prestazioni degli annunci passati.

Visita il [[!DNL Bing Ads]](https://advertise.bingads.microsoft.com/en-us/blog/post/august-2016/upgraded-urls-now-available-in-bing-ads-an-easier-way-to-manage-your-tracking-urls){target="_blank"} per ulteriori informazioni sull’aggiunta di tag sulla propria piattaforma.

## Facebook Ads {#facebook-ads}

Il [!DNL Marketo Measure] integrazione con [!DNL Facebook] consente di scaricare automaticamente le informazioni sull’annuncio e di assegnare all’URL i tag con i relativi parametri. [!DNL Marketo Measure] richiamerà le informazioni sulla campagna e sul set di annunci tramite l’assegnazione automatica di tag. Il set di annunci compilerà il campo Nome gruppo di annunci. Per ulteriori informazioni sulla configurazione dei tag URL in [!DNL Facebook] piattaforma, visita il [!DNL Facebook] [business](https://www.facebook.com/business/help/1016122818401732/?ref=u2u){target="_blank"} pagina.

Prima di abilitare l’assegnazione tag automatica con [!DNL Facebook Ads], è importante esportare la cronologia delle prestazioni precedente come file CSV. A questo punto, quando [!DNL Marketo Measure] tag [!DNL Facebook Ads] con il parametro _bf, [!DNL Facebook] legge gli annunci come nuovi di zecca e cancella la cronologia delle prestazioni. Pertanto, è importante esportare un record delle prestazioni precedenti se questo è qualcosa di valore per te e la tua organizzazione.

Tieni presente che puoi collegare [!DNL Facebook] account in qualsiasi momento a [!DNL Marketo Measure] e nessun dato andrà perso; solo quando è abilitata l’assegnazione tag automatica, la cronologia delle prestazioni viene cancellata.

[Consulta questo articolo](https://www.facebook.com/business/help/393890194130036){target="_blank"} da Facebook per ulteriori informazioni sull&#39;esportazione [!DNL Facebook] Rapporti sugli annunci.

## Contenuti sponsorizzati da linkedIn {#linkedin-sponsored-content}

L’integrazione di LinkedIn consente [!DNL Marketo Measure] per assegnare tag agli URL di destinazione su [!DNL LinkedIn] Contenuto sponsorizzato, che alla fine consente [!DNL Marketo Measure] per seguire un utente attraverso l’intero percorso di punti di contatto e mappare di nuovo l’attività su [!DNL LinkedIn] Campagna e creatività. Questo fornisce informazioni ai clienti sul ROI del [!DNL LinkedIn] attività. [!DNL Marketo Measure] cercherà creativi con un unico [!DNL LinkedIn] Condividi e aggiungi un `?_bl={creativeId}` alla fine di esso.

Perché [!DNL LinkedIn] Le condivisioni possono essere utilizzate in più campagne e creatività. Chiediamo ai clienti di non copiare/clonare/duplicare i contenuti creativi esistenti in modo che possano mantenerne l’unicità. Se vengono trovate condivisioni che vengono rilevate per essere utilizzate solo su un elemento creativo, [!DNL Marketo Measure] può assegnare tag allo Share così com’è senza dover ricreare alcun Creatives o Shares e la cronologia di tutti gli annunci (impression, clic, condivisioni) rimarrà.

Non appena un Condivisione viene rilevato come condiviso tra più Creativi, [!DNL Marketo Measure] Per creare un set univoco, è necessario eseguire un processo di pausa, copia e riassegnazione tag. [!DNL Marketo Measure] mette in pausa e archivia i contenuti creativi in tempo reale, il che significa che vengono archiviati anche i contenuti creativi contenenti impression, clic e condivisioni social.

## Piattaforme non integrate {#non-integrated-platforms}

Per piattaforme non integrate con [!DNL Marketo Measure], il [!DNL Marketo Measure] impossibile utilizzare la funzionalità di assegnazione tag automatica. I parametri dovranno essere aggiunti manualmente.
