---
unique-page-id: 18874594
description: Piattaforme integrate di annunci - [!DNL Marketo Measure] - Documentazione del prodotto
title: Piattaforme integrate di annunci
exl-id: df30ee8a-8b07-4f14-94e8-cc482fca8b18
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '1696'
ht-degree: 0%

---

# Piattaforme integrate di annunci {#integrated-ad-platforms}

[!DNL Marketo Measure] dispone di connessioni API con Google AdWords, Microsoft BingAds, [!DNL Facebook] Annunci e DoubleClick Campaign Manager. Attraverso queste connessioni API, [!DNL Marketo Measure] è in grado di estrarre facilmente i dati e inviarli al tuo CRM insieme all&#39;app esterna Buyer. Non è necessario caricare manualmente i costi o i dati. Piuttosto, i tuoi account devono semplicemente essere collegati e autorizzati al [!DNL Marketo Measure] app. [!DNL Marketo Measure] quindi scarica automaticamente i costi di marketing dalle piattaforme e li carica nel [!DNL Marketo Measure] app. Se si seleziona per abilitare l’assegnazione tag automatica per AdWords, BingAds o [!DNL Facebook] Annunci [!DNL Marketo Measure] aggiungerà automaticamente i relativi parametri agli URL degli annunci.

## Come collegare piattaforme di annunci {#how-to-connect-ad-platforms}

Prima di conoscere le specifiche di ciascuna piattaforma, esamineremo come collegare uno di questi account a [!DNL Marketo Measure]. Accedi per primo al [!DNL Marketo Measure] e passa all&#39;app **[!UICONTROL Settings]** nella sezione **[!UICONTROL My Account]** in alto a sinistra dello schermo. Quindi, seleziona **[!UICONTROL Connections]** in **[!UICONTROL Integrations]** a sinistra.

Come mostrato nell&#39;immagine seguente, vedrai un pulsante per impostare nuove connessioni agli annunci.

![](assets/2.png)

Dopo aver fatto clic sul pulsante [!UICONTROL Set up New Ads Connection] viene visualizzata una finestra (mostrata di seguito) con quattro annunci [!UICONTROL connect]tipi di ioni. Fare clic su Connetti e verrà visualizzata un&#39;altra finestra in cui si richiedono le credenziali. Immetti le credenziali e fai clic su [!UICONTROL authorize] per collegare l’account a [!DNL Marketo Measure].

![](assets/select-account-type.png)

## Google AdWords {#google-adwords}

Quando crei i tuoi annunci in [!DNL Google AdWords], ti consigliamo di assegnare tag alle campagne in uno dei tre modi seguenti: assegnazione tag manuale, assegnazione tag automatica o creazione di un modello di tracciamento. L’assegnazione tag manuale all’URL di AdWords si basa sulla definizione e l’aggiunta di parametri alla fine degli URL degli annunci. L’assegnazione tag manuale consente a qualsiasi piattaforma non Google di leggere facilmente i dati raccolti dai parametri.

Il modello di tracciamento è uno strumento fornito da Google per aggiungere i cosiddetti parametri ValueTrack. Funzionano nello stesso modo degli UTM e di altri parametri di assegnazione tag.

## Cosa accade quando l’assegnazione tag automatica è abilitata {#what-happens-when-auto-tagging-is-enabled}

[!DNL Marketo Measure] Cerca modelli di tracciamento nel tuo [!DNL AdWords] account:

* *Opzione A*: Modello di tracciamento trovato. [!DNL Marketo Measure] aggiunge i relativi parametri al modello.
* *Opzione B*: Reindirizzamento di terze parti trovato. Se nel modello di tracciamento si trova un reindirizzamento di terze parti, [!DNL Marketo Measure] non può intraprendere alcuna azione. Sarà necessario aggiungere manualmente il [!DNL Marketo Measure] al sistema di terze parti. Un esempio di reindirizzamento di terze parti sarebbe uno strumento di gestione delle offerte come Kenshoo o Marin. Ulteriori informazioni su come [gli strumenti di gestione delle offerte [!DNL Marketo Measure]](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md){target="_blank"}.

* *Opzione C*: Nessun modello di tracciamento trovato. [!DNL Marketo Measure] eseguirà la scansione di tutti gli URL di destinazione dell&#39;annuncio per [!DNL Marketo Measure] Parametri. In base alla scansione, se:
   * Parametri trovati: configurazione completata.
   * Parametri non trovati: [!DNL Marketo Measure] aggiungerà i suoi parametri alla fine degli URL di destinazione dell’annuncio. [!DNL Marketo Measure] aggiunge nuovi annunci entro due ore dalla loro creazione. Tieni presente che i parametri non verranno aggiunti a un modello.

Ulteriori informazioni sulle nostre [[!DNL AdWords] funzionalità di assegnazione tag automatica](/help/api-connections/utilizing-marketo-measures-api-connections/understanding-marketo-measure-adwords-tagging.md){target="_blank"}.

## Come abilitare [!DNL Marketo Measure] Assegnazione automatica tag per Adwords {#how-to-enable-marketo-measure-auto-tagging-for-adwords}

Prima di attivare [!DNL Marketo Measure] assegnazione di tag automatici, **assicurati di avere un modello di tracciamento abilitato a livello di account, campagna o gruppo di annunci all’interno del tuo account Adwords. Questo è necessario per qualsiasi account Adwords che avrà [!DNL Marketo Measure] assegnazione tag automatica abilitata.** L’abilitazione di un modello di tracciamento impedisce qualsiasi perdita di dati della cronologia delle prestazioni degli annunci. Tieni presente che l’abilitazione dei modelli di tracciamento a livello di Parola chiave, Sitelink o Annuncio causerà l’attraversamento del processo di revisione e approvazione dell’annuncio e potrebbe potenzialmente riavviare la cronologia delle prestazioni degli annunci. Se non è abilitato alcun modello di tracciamento, [!DNL Marketo Measure] aggiunge [!DNL Marketo Measure] i parametri di tracciamento direttamente nell’&quot;URL finale&quot; dell’annuncio, che può anche causare la perdita di dati della cronologia degli annunci.

Una volta installato un modello di tracciamento, segui le istruzioni riportate di seguito per abilitare [!DNL Marketo Measure] Assegnazione tag automatica. Nota: [!DNL Marketo Measure] taggerà automaticamente anche tutti gli annunci in pausa nel tuo account.

1. Accedi al tuo [!DNL Marketo Measure] conto a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

1. Vai a [!UICONTROL My Account] > [!UICONTROL Settings] > [!UICONTROL Integrations] > [!UICONTROL Connections].

   ![](assets/4.png)

1. Fai clic sull’icona a forma di matita accanto all’account Adwords che avrà [!DNL Marketo Measure] assegnazione tag automatica abilitata.

   ![](assets/5.png)

1. Nell’angolo in alto a destra, attiva/disattiva la **[!UICONTROL Autotagging]** passa a **[!UICONTROL Yes]**. Nella parte inferiore della pagina, fai clic su **[!UICONTROL Learn More]** per espandere la casella di testo e fare clic su **[!UICONTROL Save]**. Impostazione assegnazione tag automatica completata.

   ![](assets/6.png)

## Come impostare un modello di tracciamento in AdWords con [!DNL Marketo Measure] Parametri {#how-to-set-up-a-tracking-template-in-adwords-with-marketo-measure-parameters}

È necessario aggiungere modelli di tracciamento nella sezione [!UICONTROL Account], [!UICONTROL Campaign] o a livello di gruppo di annunci in AdWords. Se aggiungi modelli di tracciamento a livello di Parola chiave, Sitelink o Annuncio, il tuo annuncio dovrà passare attraverso il processo di revisione e approvazione e rischiare di riavviare la cronologia delle prestazioni degli annunci. Ulteriori informazioni [creazione di modelli di tracciamento](https://support.google.com/adwords/answer/6076199?hl=en#tracking){target="_blank"}.

1. Accedi al tuo [!DNL Google AdWords] Conto.
1. Vai al tuo [!UICONTROL Campaigns] vista dalla barra di navigazione a sinistra
1. Passa a &quot;[!UICONTROL Settings]&quot;, anche nella barra di navigazione a sinistra
1. Passa a &quot;[!UICONTROL Account Settings]&quot; vista dall&#39;alto
1. Espandi &quot;[!UICONTROL Tracking]&quot; sezione
1. Incolla una delle seguenti stringhe di testo nel modello di tracciamento per impostare il valore del modello:

   * Se hai punti interrogativi in TUTTI gli URL, utilizza il seguente testo URL:

   `{lpurl}&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

   * Se non hai punti interrogativi su nessuno degli URL, aggiungi il seguente testo URL:

   `{lpurl}?_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}*`

   Per evitare che si verifichino errori quando si applicano tag manuali agli URL, in genere si consiglia di generare automaticamente i parametri UTM. Questo non deve necessariamente comportare l’assegnazione automatica dei tag con AdWords o [!DNL Marketo Measure] , esistono più strumenti che semplificano il processo generando automaticamente i parametri per l&#39;URL in base alle informazioni fornite.

   >[!TIP]
   >
   >Se ricevi un errore che indica che il modello di tracciamento non è valido, prova a cancellare la cache del browser e riprova - questo spesso risolve il problema.

## Come generare automaticamente tag UTM per [!DNL Google AdWords] {#how-to-automatically-generate-utm-tags-for-google-adwords}

I tag UTM possono sembrare difficili da creare inizialmente, ma sono disponibili molti strumenti per creare facilmente URL con parametri UTM. Puoi utilizzare una qualsiasi delle seguenti risorse o cercare sul web altri strumenti. Nota bene [!DNL Marketo Measure] non approva o garantisce nulla con queste piattaforme e strumenti.

**[!DNL Google URL]Builder**

Google URL Builder è uno strumento standard per la creazione di URL formattati correttamente con tag UTM. Inserisci semplicemente l’URL e il valore desiderato di ciascun parametro e fai clic su &quot;[!UICONTROL Generate URL]&quot;. Si tratta di uno strumento ideale da utilizzare se devi assegnare un solo numero limitato di URL. Accedere allo strumento [qui](https://support.google.com/analytics/answer/1033867?hl=en){target="_blank"}.

**Foglio di calcolo Google generato da EpikOne**

Questo foglio di calcolo contiene una formula che genera automaticamente gli URL di destinazione con tag. Si tratta di un ottimo strumento per assegnare tag a un numero elevato di collegamenti. Accedere al foglio di calcolo [qui](https://spreadsheets.google.com/ccc?key=p7c_HKcmspSUfEYSO0gskKw&amp;hl=en){target="_blank"}.

**Strumento per l’assegnazione tag dei collegamenti Rafflecopter**

Il foglio di calcolo creato da Rafflecopter è una versione modificata di [!DNL EpikOne's] foglio di calcolo. Contiene anche una formula che genererà automaticamente collegamenti di destinazione con tag da utilizzare.

Ognuno di questi strumenti contiene istruzioni dettagliate su come utilizzarlo e modificarlo in base alle tue esigenze. Lo strumento è disponibile [qui](https://docs.google.com/spreadsheets/d/1QCIr1WUJQHE68cA4VTks2XE7nxuryaUymCEy_23-Oew/edit#gid=0){target="_blank"}.

**Generatore UTM straordinario**

Questo strumento è un&#39;estensione Chrome che consente di generare rapidamente tag UTM. Trova [qui](https://chrome.google.com/webstore/detail/effin-amazing-utm-builder/eoaapiimcaimddnfhfnifgkinmpcbccp?hl=en){target="_blank"}.

## Annunci Bing {#bing-ads}

Bing Ads è una piattaforma integrata che consente di abilitare l’assegnazione tag automatica agli URL o di utilizzare uno strumento di terze parti, ad esempio [!DNL Marketo Measure], per assegnare tag agli annunci. [!DNL Bing Ads] si basa anche sui parametri UTM.

La funzione di assegnazione tag automatica di Bing Ads aggiunge i seguenti parametri UTM:

* Utm_source
* Utm_medium
* Utm_term

L’assegnazione tag automatica di Bing Ads aggiunge anche il seguente parametro personalizzato:

`_bt={adid}`

La stringa sarà simile alla seguente:

`{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`

È importante notare che [!DNL Bing Ads] consente di aggiungere altri parametri utilizzando i relativi tag personalizzati negli URL finali per ottenere una maggiore granularità, se lo desideri.

Se lo desideri, puoi utilizzare un modello di tracciamento, ma non è necessario per [!DNL Bing Ads] e [!DNL Marketo Measure] per l&#39;integrazione. Questo perché [!DNL Bing] consente di modificare gli annunci senza modificare la cronologia, in modo da [!DNL Marketo Measure] è in grado di aggiornare l&#39;URL di destinazione.

L’assegnazione automatica dei tag deve essere abilitata tramite [!DNL Marketo Measure] in modo che [!DNL Marketo Measure] i parametri possono essere aggiunti automaticamente. Non c&#39;è alcun rischio di perdere la storia passata delle prestazioni pubblicitarie con Bing Ads.

Visita il [[!DNL Bing Ads]](https://advertise.bingads.microsoft.com/en-us/blog/post/august-2016/upgraded-urls-now-available-in-bing-ads-an-easier-way-to-manage-your-tracking-urls){target="_blank"} per ulteriori informazioni sull’aggiunta di tag sulla piattaforma.

## Facebook Ads {#facebook-ads}

La [!DNL Marketo Measure] integrazione con [!DNL Facebook] consente di scaricare automaticamente le informazioni sugli annunci e di assegnare all’URL i relativi parametri. [!DNL Marketo Measure] riceverà le informazioni sulla campagna e sul set di annunci tramite l’assegnazione tag automatica. Il set di annunci compilerà il campo Nome gruppo di annunci . Per ulteriori informazioni sulla configurazione dei tag URL nel [!DNL Facebook] piattaforma, visita [!DNL Facebook] [business](https://www.facebook.com/business/help/1016122818401732/?ref=u2u){target="_blank"} pagina.

Prima di abilitare l’assegnazione tag automatica con [!DNL Facebook Ads], è importante esportare la cronologia delle prestazioni precedenti come CSV. A questo punto, quando [!DNL Marketo Measure] tag [!DNL Facebook Ads] con il parametro _bf, [!DNL Facebook] legge gli annunci come nuovi di zecca e cancella la cronologia delle prestazioni. Pertanto è importante esportare un record delle prestazioni precedenti se questo rappresenta un valore per te e per la tua organizzazione.

È possibile collegare il [!DNL Facebook] in qualsiasi momento al [!DNL Marketo Measure] l’app e nessun dato andrà perso; solo quando l’assegnazione tag automatica è abilitata, la cronologia delle prestazioni viene cancellata.

[Vedi questo articolo](https://www.facebook.com/business/help/393890194130036){target="_blank"} da Facebook per ulteriori informazioni sull&#39;esportazione [!DNL Facebook] Rapporti sugli annunci.

## Contenuto sponsorizzato da linkedIn {#linkedin-sponsored-content}

L&#39;integrazione LinkedIn consente [!DNL Marketo Measure] per assegnare tag agli URL di destinazione [!DNL LinkedIn] Contenuto sponsorizzato, che in ultima analisi consente [!DNL Marketo Measure] per seguire un utente attraverso l’intero percorso di punti di contatto e mappare l’attività sullo specifico [!DNL LinkedIn] Campagna e creativo. Questo fornisce ai clienti informazioni sul ROI del loro [!DNL LinkedIn] attività. [!DNL Marketo Measure] cercherà creativi con un unico [!DNL LinkedIn] Condividi e aggiungi un `?_bl={creativeId}` alla fine.

Perché [!DNL LinkedIn] Le condivisioni possono essere utilizzate in più campagne e creativi; chiediamo ai clienti di non copiare/clonare/duplicare i creativi esistenti in modo da mantenere la loro unicità. Se le azioni sono trovate e sono rilevate per essere utilizzate solo su un creativo, [!DNL Marketo Measure] Puoi assegnare il tag Condividi così come è senza dover ricreare alcun creativo o condivisione e la cronologia di tutti gli annunci (impression, clic, condivisioni) rimarrà invariata.

Non appena si scopre che una condivisione è condivisa tra più creativi, [!DNL Marketo Measure] per creare un set univoco, sarà necessario eseguire un processo di sospensione, copia e riassegnazione tag. [!DNL Marketo Measure] mette in pausa e archivia i creativi in tempo reale, il che significa che vengono archiviati anche i creativi contenenti le impression, i clic e le condivisioni social.

## Piattaforme non integrate {#non-integrated-platforms}

Per piattaforme non integrate con [!DNL Marketo Measure], [!DNL Marketo Measure] non è possibile utilizzare la funzionalità di assegnazione tag automatica. I parametri dovranno essere aggiunti manualmente.
