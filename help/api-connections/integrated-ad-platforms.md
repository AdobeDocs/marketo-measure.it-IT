---
description: Linee guida sulle piattaforme di annunci integrate per gli utenti di Marketo Measure
title: Piattaforme di annunci integrate
exl-id: df30ee8a-8b07-4f14-94e8-cc482fca8b18
feature: APIs, Integration
hidefromtoc: true
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '1649'
ht-degree: 0%

---

# Piattaforme di annunci integrate {#integrated-ad-platforms}

[!DNL Marketo Measure] dispone di connessioni API con Google AdWords, Microsoft BingAds, [!DNL Facebook] Ads e DoubleClick Campaign Manager. Tramite queste connessioni API, [!DNL Marketo Measure] è in grado di estrarre facilmente i dati e inviarli al tuo CRM insieme all&#39;app Buyer esterna. Non è richiesto alcun caricamento manuale di costi o dati. Piuttosto, i tuoi account devono semplicemente essere connessi e autorizzati all&#39;app [!DNL Marketo Measure]. [!DNL Marketo Measure] scaricherà quindi automaticamente i costi di marketing dalle piattaforme e li caricherà nell&#39;app [!DNL Marketo Measure]. Se si sceglie di abilitare l&#39;assegnazione tag automatica per AdWords, BingAds o [!DNL Facebook] annunci, [!DNL Marketo Measure] aggiungerà automaticamente i relativi parametri agli URL dei propri annunci.

## Come collegare le piattaforme di annunci {#how-to-connect-ad-platforms}

Prima di entrare nelle specifiche di ciascuna piattaforma, esamineremo come collegare uno qualsiasi di questi account a [!DNL Marketo Measure]. Accedi all&#39;app [!DNL Marketo Measure] e passa all&#39;opzione **[!UICONTROL Settings]** nella scheda **[!UICONTROL My Account]** in alto a sinistra dello schermo. Selezionare **[!UICONTROL Connections]** nella sezione **[!UICONTROL Integrations]** a sinistra.

Come mostrato nell’immagine seguente, verrà visualizzato un pulsante per impostare nuove connessioni di annunci.

![](assets/bizible-guide-1.png)

Dopo aver fatto clic sul pulsante [!UICONTROL Set up New Ads Connection], verrà visualizzata una finestra (mostrata di seguito) con quattro tipi di annunci [!UICONTROL connect] ioni. Facendo clic su Connetti verrà visualizzata un&#39;altra finestra in cui viene richiesto di immettere le credenziali. Immettere le credenziali e fare clic su [!UICONTROL authorize] per connettere l&#39;account a [!DNL Marketo Measure].

![](assets/five-five-1.png)

## Google AdWords {#google-adwords}

Quando crei i tuoi annunci in [!DNL Google AdWords], ti consigliamo di assegnare tag alle campagne in uno dei tre modi seguenti: tag manuali, tag automatici o creazione di un modello di tracciamento. L’assegnazione manuale di tag all’URL di AdWords si basa sulla definizione e sull’aggiunta dei parametri alla fine degli URL degli annunci. L’assegnazione manuale dei tag consente a qualsiasi piattaforma non Google di leggere facilmente i dati raccolti dai parametri.

Il modello di tracciamento è uno strumento fornito da Google per aggiungere quelli che chiama parametri ValueTrack. Funzionano allo stesso modo degli UTM e di altri parametri di assegnazione tag.

## Che cosa accade quando è abilitata l’assegnazione tag automatica {#what-happens-when-auto-tagging-is-enabled}

[!DNL Marketo Measure] Cerca modelli di tracciamento nel tuo account [!DNL AdWords]:

* *Opzione A*: modello di tracciamento trovato. [!DNL Marketo Measure] aggiunge i relativi parametri al modello.
* *Opzione B*: trovato reindirizzamento di terze parti. Se nel modello di tracciamento viene trovato un reindirizzamento di terze parti, [!DNL Marketo Measure] non può eseguire alcuna azione. Sarà necessario aggiungere manualmente i tag [!DNL Marketo Measure] al sistema di terze parti. Un esempio di reindirizzamento di terze parti potrebbe essere uno strumento di gestione delle offerte come Kenshoo o Marin. Ulteriori informazioni sugli effetti degli strumenti di gestione delle offerte [su [!DNL Marketo Measure]](/help/api-connections/how-bid-management-tools-affect-marketo-measure.md){target="_blank"}.

* *Opzione C*: nessun modello di tracciamento trovato. [!DNL Marketo Measure] eseguirà la scansione di tutti gli URL di destinazione dell&#39;annuncio per i parametri [!DNL Marketo Measure]. In base alla scansione, se:
   * Sono stati trovati dei parametri: la configurazione è stata completata.
   * Parametri non trovati: [!DNL Marketo Measure] aggiungerà i suoi parametri alla fine degli URL di destinazione dell&#39;annuncio. [!DNL Marketo Measure] aggiunge nuovi annunci entro due ore dalla loro creazione. I parametri non verranno aggiunti a un modello.

Ulteriori informazioni sulla [[!DNL AdWords] funzionalità di assegnazione tag automatica](/help/api-connections/understanding-marketo-measure-adwords-tagging.md){target="_blank"}.

## Come abilitare l&#39;assegnazione tag automatici a [!DNL Marketo Measure] per Adwords {#how-to-enable-marketo-measure-auto-tagging-for-adwords}

Prima di abilitare l&#39;assegnazione tag automatici a [!DNL Marketo Measure], **assicurati di disporre di un modello di tracciamento abilitato a livello di account, campagna o gruppo di annunci nel tuo account Adwords. Questa operazione è necessaria per tutti gli account Adwords per i quali è abilitata l&#39;assegnazione tag automatica [!DNL Marketo Measure].** L&#39;abilitazione di un modello di tracciamento impedisce qualsiasi perdita di dati della cronologia delle prestazioni degli annunci. Tieni presente che l’abilitazione dei modelli di tracciamento a livello di parola chiave, Sitelink o Annuncio determinerà il completamento del processo di revisione e approvazione dell’annuncio e potrebbe potenzialmente riavviare la cronologia delle prestazioni degli annunci. Se non è abilitato alcun modello di tracciamento, [!DNL Marketo Measure] aggiungerà i parametri di tracciamento [!DNL Marketo Measure] direttamente all&#39;URL finale dell&#39;annuncio, con conseguente perdita di dati della cronologia dell&#39;annuncio.

Dopo aver impostato un modello di tracciamento, seguire le istruzioni riportate di seguito per abilitare l&#39;assegnazione tag automatici a [!DNL Marketo Measure]. Nota: [!DNL Marketo Measure] assegnerà automaticamente i tag anche agli annunci in pausa nel tuo account.

1. Accedi al tuo account [!DNL Marketo Measure] all&#39;indirizzo [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

1. Vai a [!UICONTROL My Account] > [!UICONTROL Settings] > [!UICONTROL Integrations] > [!UICONTROL Connections].

   ![](assets/utilizing-connections-8.png)

1. Fare clic sull&#39;icona a forma di matita accanto all&#39;account Adwords per il quale verrà attivata l&#39;assegnazione tag automatica [!DNL Marketo Measure].

   ![](assets/utilizing-connections-9.png)

1. Nell&#39;angolo in alto a destra, impostare il parametro **[!UICONTROL Autotagging]** su **[!UICONTROL Yes]**. Nella parte inferiore della pagina fare clic su **[!UICONTROL Learn More]** per espandere la casella di testo e fare clic su **[!UICONTROL Save]**. Impostazione assegnazione automatica tag completata.

   ![](assets/utilizing-connections-10.png)

## Impostare un modello di tracciamento in AdWords con [!DNL Marketo Measure] parametri {#how-to-set-up-a-tracking-template-in-adwords-with-marketo-measure-parameters}

È necessario aggiungere modelli di tracciamento a livello di [!UICONTROL Account], [!UICONTROL Campaign] o di gruppo di annunci in AdWords. Se aggiungi modelli di tracciamento al livello Parola chiave, Sitelink o Annuncio, il tuo annuncio dovrà seguire il processo di revisione e approvazione e rischi di riavviare la cronologia delle prestazioni degli annunci. Ulteriori informazioni sulla [creazione di modelli di tracciamento](https://support.google.com/adwords/answer/6076199?hl=en#tracking){target="_blank"}.

1. Accedi al tuo account [!DNL Google AdWords].
1. Passa alla visualizzazione [!UICONTROL Campaigns] dalla barra di navigazione a sinistra
1. Passa a &quot;[!UICONTROL Settings]&quot;, sempre nella barra di spostamento a sinistra
1. Passa alla visualizzazione &quot;[!UICONTROL Account Settings]&quot; nella parte superiore
1. Espandi la sezione &quot;[!UICONTROL Tracking]&quot;
1. Incolla una delle seguenti stringhe di testo nel modello di tracciamento per impostare il valore del modello:

   * Se hai dei punti interrogativi in TUTTI gli URL, utilizza il seguente testo URL:

   `{lpurl}&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

   * Se non hai punti interrogativi su nessuno degli URL, aggiungi il seguente testo URL:

   `{lpurl}?_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}*`

   Per evitare errori quando si applicano tag manuali agli URL, in genere si consiglia di generare automaticamente i parametri UTM. Questo non significa necessariamente assegnare tag automatici ai parametri AdWords o [!DNL Marketo Measure]; esistono diversi strumenti che semplificano il processo generando automaticamente i parametri per l&#39;URL in base alle informazioni fornite.

   >[!TIP]
   >
   >Se ricevi un errore che indica che il modello di tracciamento non è valido, prova a cancellare la cache del browser e riprova, spesso per risolvere il problema.

## Come generare automaticamente i tag UTM per [!DNL Google AdWords] {#how-to-automatically-generate-utm-tags-for-google-adwords}

All’inizio i tag UTM possono sembrare difficili da creare, ma sono disponibili molti strumenti per creare facilmente URL con parametri UTM. Puoi utilizzare una qualsiasi delle seguenti risorse o cercare sul web altri strumenti. Tieni presente che [!DNL Marketo Measure] non offre alcuna garanzia o supporto per queste piattaforme e questi strumenti.

Generatore **[!DNL Google URL]**

Google URL Builder è uno strumento standard per la creazione di URL formattati correttamente con tag UTM. Immettere l&#39;URL e il valore desiderato di ciascun parametro e fare clic su &quot;[!UICONTROL Generate URL]&quot;. Questo è uno strumento ideale da utilizzare se disponi solo di una manciata di URL da assegnare ai tag. Accedi allo strumento [qui](https://support.google.com/analytics/answer/1033867?hl=en){target="_blank"}.

**Foglio di calcolo Google generato da EpikOne**

Questo foglio di calcolo contiene una formula che genererà automaticamente gli URL di destinazione con tag. Questo è un ottimo strumento da utilizzare se è necessario assegnare tag a un numero elevato di collegamenti. Accedi al foglio di calcolo [qui](https://spreadsheets.google.com/ccc?key=p7c_HKcmspSUfEYSO0gskKw&hl=en){target="_blank"}.

**Strumento di assegnazione tag collegamento Rafflecopter**

Il foglio di calcolo creato da Rafflecopter è una versione modificata di [!DNL EpikOne's]. Contiene inoltre una formula che genera automaticamente i collegamenti di destinazione con tag da utilizzare.

Ognuno di questi strumenti contiene istruzioni dettagliate su come utilizzarlo e modificarlo in base alle tue esigenze. Strumento disponibile [qui](https://docs.google.com/spreadsheets/d/1QCIr1WUJQHE68cA4VTks2XE7nxuryaUymCEy_23-Oew/edit#gid=0){target="_blank"}.

**Generatore UTM sorprendente con Effin**

Questo strumento è un’estensione Chrome che consente di generare rapidamente tag UTM. Trovalo [qui](https://chrome.google.com/webstore/detail/effin-amazing-utm-builder/eoaapiimcaimddnfhfnifgkinmpcbccp?hl=en){target="_blank"}.

## Bing Ads {#bing-ads}

Bing Ads è una piattaforma integrata che consente di abilitare l&#39;assegnazione tag automatica per gli URL o di utilizzare uno strumento di terze parti, ad esempio [!DNL Marketo Measure], per assegnare tag agli annunci. [!DNL Bing Ads] si basa anche sui parametri UTM.

La nostra integrazione supporta i seguenti tipi di annunci:

* Annuncio testo
* Annuncio mobile
* Annuncio di testo espanso


La funzione di assegnazione automatica tag di Bing Ads aggiunge i seguenti parametri UTM:

* Utm_source
* Utm_medium
* Utm_term

L’assegnazione automatica tag di Bing Ads aggiunge anche il seguente parametro personalizzato:

`_bt={adid}`

La stringa sarà simile alla seguente:

`{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`

È importante notare che [!DNL Bing Ads] ti consente di aggiungere altri parametri utilizzando i tag personalizzati negli URL finali per ottenere maggiore granularità, se lo desideri.

Se necessario, è possibile utilizzare un modello di tracciamento, ma non è necessario che [!DNL Bing Ads] e [!DNL Marketo Measure] siano integrati. Questo perché [!DNL Bing] consente di modificare gli annunci senza modificare la cronologia, quindi [!DNL Marketo Measure] è in grado di aggiornare l&#39;URL di destinazione.

L&#39;assegnazione tag automatici deve essere abilitata tramite [!DNL Marketo Measure] in modo che i parametri [!DNL Marketo Measure] personalizzati possano essere aggiunti automaticamente. Con Bing Ads non si corre il rischio di perdere la cronologia delle prestazioni degli annunci passati.

Visitare il sito Web [[!DNL Bing Ads]](https://advertise.bingads.microsoft.com/en-us/blog/post/august-2016/upgraded-urls-now-available-in-bing-ads-an-easier-way-to-manage-your-tracking-urls){target="_blank"} per ulteriori informazioni sull&#39;aggiunta di tag sulla piattaforma.

## Facebook Ads {#facebook-ads}

L&#39;integrazione di [!DNL Marketo Measure] con [!DNL Facebook] consente di scaricare automaticamente le informazioni sull&#39;annuncio e di assegnare tag all&#39;URL con i relativi parametri. [!DNL Marketo Measure] richiamerà le informazioni sulla campagna e sul set di annunci tramite l&#39;assegnazione tag automatica. Il set di annunci compilerà il campo Nome gruppo di annunci. Per ulteriori informazioni sulla configurazione dei tag URL sulla piattaforma [!DNL Facebook], visitare la pagina [!DNL Facebook] [business](https://www.facebook.com/business/help/1016122818401732/?ref=u2u){target="_blank"}.

Prima di abilitare l&#39;assegnazione tag automatici con [!DNL Facebook Ads], è importante esportare la cronologia delle prestazioni precedente come file CSV. A questo punto, quando [!DNL Marketo Measure] assegna a [!DNL Facebook Ads] i tag con il relativo parametro _bf, [!DNL Facebook] legge gli annunci come nuovi e cancella la cronologia delle prestazioni. Pertanto, è importante esportare un record delle prestazioni precedenti se questo è qualcosa di valore per te e la tua organizzazione.

È possibile collegare l&#39;account [!DNL Facebook] in qualsiasi momento all&#39;app [!DNL Marketo Measure] e non verrà perso alcun dato. La cronologia delle prestazioni verrà cancellata solo quando è abilitata l&#39;assegnazione tag automatica.

Consulta [questo articolo](https://www.facebook.com/business/help/393890194130036){target="_blank"} da Facebook per ulteriori informazioni sull&#39;esportazione di [!DNL Facebook] report pubblicitari.

## Contenuto sponsorizzato LinkedIn {#linkedin-sponsored-content}

L&#39;integrazione LinkedIn consente a [!DNL Marketo Measure] di assegnare tag agli URL di destinazione nel contenuto sponsorizzato [!DNL LinkedIn], il che alla fine consente a [!DNL Marketo Measure] di seguire un utente attraverso l&#39;intero percorso di punti di contatto e mappare l&#39;attività di nuovo allo specifico Campaign [!DNL LinkedIn] e Creative. In questo modo i clienti possono ottenere informazioni sul ROI dell&#39;attività [!DNL LinkedIn]. [!DNL Marketo Measure] cercherà i creativi con una condivisione [!DNL LinkedIn] univoca e aggiungerà un parametro `?_bl={creativeId}` alla fine.

Poiché le condivisioni [!DNL LinkedIn] possono essere utilizzate in più campagne e creatività, chiediamo ai clienti di non copiare/clonare/duplicare i contenuti creativi esistenti in modo che possano mantenerne l&#39;univocità. Se vengono trovate condivisioni che vengono rilevate per essere utilizzate solo su un Creative, [!DNL Marketo Measure] può assegnare i tag di condivisione senza dover ricreare alcuna creativa o condivisione e la cronologia di tutti gli annunci (impression, clic, condivisioni) rimarrà.

Non appena una condivisione verrà trovata condivisa tra più creativi, [!DNL Marketo Measure] dovrà eseguire un processo di pausa, copia e riassegnazione tag per creare un set univoco. [!DNL Marketo Measure] metterà in pausa e archivierà i contenuti creativi in tempo reale, il che significa che verranno archiviati anche i contenuti creativi contenenti le impression, i clic e le condivisioni social.

## Piattaforme non integrate {#non-integrated-platforms}

Per le piattaforme non integrate con [!DNL Marketo Measure], non è possibile utilizzare la funzionalità di assegnazione tag automatica [!DNL Marketo Measure]. I parametri dovranno essere aggiunti manualmente.
