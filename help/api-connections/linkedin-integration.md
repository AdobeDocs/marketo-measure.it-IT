---
description: LinkedIn - Linee guida per l’integrazione per gli utenti di Marketo Measure
title: Integrazione LinkedIn
exl-id: 705209ef-1ece-496c-ac2f-6a31055bd993
feature: APIs, Integration
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '2694'
ht-degree: 0%

---

# Integrazione LinkedIn {#linkedin-integration}

## Panoramica {#overview}

L&#39;integrazione di [!DNL Marketo Measure] con LinkedIn è costituita da due parti:

Contenuto sponsorizzato: l&#39;integrazione del contenuto sponsorizzato consente a [!DNL Marketo Measure] di assegnare tag agli URL di destinazione negli annunci [!DNL LinkedIn], il che alla fine consente a [!DNL Marketo Measure] di seguire un utente attraverso l&#39;intero percorso di punti di contatto e mappare l&#39;attività sulla specifica campagna [!DNL LinkedIn] e Creative. In questo modo i clienti possono ottenere informazioni sul ROI dell&#39;attività [!DNL LinkedIn].

Lead Gen Forms: grazie all’integrazione con Lead Gen Forms di LinkedIn, Marketo Measure acquisisce insight in moduli che sono stati inviati tramite la piattaforma LinkedIn. Questi riempimenti di modulo vengono confrontati con i lead della tua istanza di CRM o [!DNL Marketo Engage] in modo che siano idonei per l&#39;attribuzione. Con insight in Campaign, Creative e Form che hanno contribuito a generare i moduli, i team possono ora ottimizzare ulteriormente le spese di marketing e annunci LinkedIn.

## Disponibilità {#availability}

Disponibile per tutti gli utenti.

## Requisiti {#requirements}

### Ruoli di Campaign Manager

Affinché [!DNL Marketo Measure] possa scaricare i dati sui costi di Ads Data &amp; Ads, devi avere uno dei seguenti ruoli in Campaign Manager:

* Amministratore fatturazione
* Account Manager
* Gestione campagne

Ulteriori informazioni: [Ruoli utente e funzioni in Campaign Manager](https://www.linkedin.com/help/lms/answer/a425731/user-roles-and-functions-in-campaign-manager).

### Ruoli di amministratore media a pagamento

Affinché [!DNL Marketo Measure] possa creare/aggiornare i contenuti creati da Sponsorizzati, devi avere uno dei seguenti ruoli di Amministratore di contenuti multimediali a pagamento:

* Poster contenuto sponsorizzato
* Lead Gen Forms Manager

Ulteriori informazioni: [Ruoli di amministratore pagina collegati](https://www.linkedin.com/help/linkedin/answer/4783/linkedin-page-admin-roles-overview).

Ci sono altri [!DNL LinkedIn] ruoli che **non** richiedono per la nostra integrazione. Questi ruoli vengono spesso scambiati per i ruoli richiesti, quindi tieni presente che c’è una differenza!

### Ruoli di amministratore pagina

Affinché [!DNL Marketo Measure] possa scaricare/integrare lead dai moduli lead gen, è necessario disporre del seguente ruolo Amministratore pagina:

* Amministratore privilegiato

Ulteriori informazioni: [Ruoli di amministratore pagina collegati](https://www.linkedin.com/help/linkedin/answer/4783/linkedin-page-admin-roles-overview).

## Tipi di annunci LinkedIn {#linkedin-ad-types}

[!DNL Marketo Measure] supporterà:

Contenuto sponsorizzato consente di distribuire contenuto al feed [!DNL LinkedIn] dei membri oltre a quelli che seguono l&#39;azienda. I contenuti sponsorizzati possono essere indirizzati a un pubblico specifico e possono aiutare gli inserzionisti a raggiungere [!DNL LinkedIn] membri ovunque e in qualsiasi momento si trovino coinvolti nella piattaforma [!DNL LinkedIn] su desktop, dispositivi mobili e tablet. Sono supportati i contenuti sponsorizzati con Lead Gen Forms.

I tipi di formati di annunci di contenuti sponsorizzati supportati da [!DNL Marketo Measure] sono Annunci immagine singola e Annunci video (tramite Forms di generazione lead). A causa della complessità dello schema, non sono supportati gli annunci Carosello.

[!DNL Marketo Measure] non supporta la messaggistica sponsorizzata, gli annunci di testo o gli annunci dinamici.

![Marketo Measure non supporta la messaggistica sponsorizzata, gli annunci di testo o Dynamic](assets/bizible-guide-1.png)

>[!TIP]
>
>Per qualsiasi campagna/spesa proveniente da un&#39;origine di contenuto non sponsorizzato, ad esempio il tipo di campagna &quot;Annuncio testuale&quot; o &quot;InMail sponsorizzato&quot;, [!DNL Marketo Measure] non supporta _non_ intrinsecamente il tracciamento di questi tipi di campagna. Se desideri tenere traccia della spesa per campagne come queste insieme alla spesa per &quot;contenuti sponsorizzati&quot;, assicurati di utilizzare il CSV della spesa di marketing per registrare manualmente tale spesa.

## Come funziona: contenuti sponsorizzati {#how-it-works-sponsored-content}

>[!NOTE]
>
>Prima del primo utilizzo, questa impostazione della funzionalità deve essere abilitata passando a [!DNL Marketo Measure] [!UICONTROL Settings] > [!UICONTROL Integrations] > [!UICONTROL Ads] > [!UICONTROL Enable LinkedIn Lead Gen Forms].

### [!DNL LinkedIn's] requisiti univoci di assegnazione tag automatica

[!DNL Marketo Measure] può aiutare a tenere traccia delle prestazioni della tua campagna [!DNL LinkedIn] assegnando tag automatici alle pagine di destinazione.

[!DNL Marketo Measure] cercherà i creativi con una condivisione LinkedIn univoca e aggiungerà un parametro `?_bl={creativeId}` alla fine.

### Copia delle condivisioni

Con questa integrazione di [!DNL Marketo Measure/LinkedIn], chiediamo ai clienti di non copiare, clonare o duplicare elementi creativi esistenti. Se vengono trovate condivisioni che vengono rilevate per essere utilizzate solo su un Creative, [!DNL Marketo Measure] può assegnare i tag di condivisione senza dover ricreare alcuna creativa o condivisione e la cronologia di tutti gli annunci (impression, clic, condivisioni) rimarrà.

Non appena una condivisione verrà trovata condivisa tra più creativi, [!DNL Marketo Measure] dovrà eseguire un processo di pausa, copia e riassegnazione tag per creare un set univoco. [!DNL Marketo Measure] sospenderà e archivierà i creativi in tempo reale e quindi cancellerà la cronologia degli annunci, inclusi impression, clic e condivisioni social per assegnare correttamente i tag automatici a tutto.

In futuro, [!DNL Marketo Measure] consiglia di non duplicare le condivisioni [!DNL LinkedIn] e di mantenere tutte le creative e le condivisioni il più possibile univoche, in modo che sia possibile aggiungere semplicemente il tracciamento senza dover cancellare la cronologia degli annunci.

### URL abbreviati

Il motivo del passaggio aggiuntivo è che LinkedIn consente agli URL di destinazione di essere un URL abbreviato (bit.ly, goog.le, ecc.), il che significa che [!DNL Marketo Measure] non vede l&#39;URL lungo e risolto e [!DNL Marketo Measure] deve aggiungere parametri di tracciamento a un URL risolto. Per risolvere il problema, [!DNL Marketo Measure] cerca gli URL abbreviati prima di ricreare un annuncio, espande l&#39;URL, quindi crea il nuovo annuncio con l&#39;URL risolto e tutti i relativi parametri, consentendo a [!DNL Marketo Measure] di aggiungere tag. La creazione di un nuovo annuncio cancellerà la cronologia degli annunci (impression, clic, condivisioni), per cui è necessario disporre dell’autorizzazione per assegnare tag agli URL abbreviati.

Se utilizzi URL abbreviati in modo massiccio, questo potrebbe avere un forte impatto sui tuoi creativi. È consigliabile non utilizzare più URL abbreviati in modo che [!DNL Marketo Measure] possa assegnare tag alle pagine di destinazione senza dover creare nuovi annunci e cancellare la cronologia degli annunci.

### Il processo

Cominciamo con alcuni esempi. Supponiamo di sì....

Creative A: Share 123\
Creative B: Share 234\
Creative C: Share 234\
Creative D : Share 234

![Creative D: Condividi 234](../assets/marketo-engage-activities-05.png)

`1)` [!DNL Marketo Measure] esamina innanzitutto tutte le campagne, i contenuti creativi e le condivisioni con stato &quot;Attivo&quot;. [!DNL Marketo Measure] non assegnerà tag agli annunci in pausa, archiviati o annullati. Se un annuncio è stato messo in pausa e poi impostato su [!UICONTROL active], verrà contrassegnato una volta riattivato. Se è possibile trovare una condivisione univoca, ovvero che non viene utilizzata in più creative o campagne (ad esempio, Creative A: Share 123), [!DNL Marketo Measure] aggiungerà il parametro personalizzato `>> ?_bl={creativeId}` all&#39;URL di condivisione.

`2)` Se la condivisione è stata condivisa e ha perso la sua unicità (ad esempio, Creative B: Share 234 e Creative C: Share 234 e Creative D: Share 234), [!DNL Marketo Measure] sospenderà e archivierà tutte le creazioni simili (ovvero Creative B, Creative C e Creative D).

`3)` [!DNL Marketo Measure] creerà 3 nuovi creativi, Creative E, Creative F e Creative G, che copia il contenuto di Creative B, che viene archiviato.

`4)` [!DNL Marketo Measure] creerà anche 3 nuove condivisioni, Share 345, Share 456 e Share 567, che copia il contenuto di Share 234, tranne per il fatto che avrà un tag `?_bl` univoco.

`5)` [!DNL Marketo Measure] dovrà controllare regolarmente che le condivisioni non vengano condivise. In tal caso, il processo verrà riavviato al passaggio 2 di cui sopra.

>[!NOTE]
>
>Implementando questa impostazione, i nostri clienti perderanno la cronologia degli annunci di Creative B: Share 234, Creative C: Share 234 e Creative D: Share 234 perché ora viene ricreato con Creative E: Share 345, Share F: Share 456 e Creative G: Share 567 rispettivamente.

![Implementando questa impostazione, i nostri clienti perderanno la cronologia degli annunci](assets/api-connections-01.png)

## Come Funziona: Lead Gen Forms {#how-it-works-lead-gen-forms}

[!DNL Marketo Measure] può aiutare a tenere traccia delle prestazioni della tua campagna [!DNL LinkedIn] assegnando tag automatici alle pagine di destinazione.

[!DNL Marketo Measure] cercherà i creativi con una condivisione LinkedIn univoca e aggiungerà un parametro `?_bl={creativeId}` alla fine.

Tramite l&#39;API del modulo annunci di [!DNL LinkedIn's] e l&#39;API di risposta del modulo annunci, siamo in grado di raccogliere i dati di invio del modulo per un account annuncio e associare l&#39;indirizzo e-mail a un lead dal CRM o dal Marketo.

I moduli LinkedIn possono contenere più indirizzi e-mail. Quando scariciamo le risposte al modulo, cercheremo gli indirizzi e-mail con la seguente priorità: E-mail aziendale, Indirizzo e-mail (campo modulo principale) o campi personalizzati con un valore e-mail valido.

Indipendentemente dallo stato di Campaign o Creative, tutte le risposte al modulo daranno luogo a un punto di contatto. [!DNL Marketo Measure] ha una restrizione di lookback di 90 giorni, pertanto [!DNL Marketo Measure] non è in grado di accedere alle risposte del modulo più vecchie di 90 giorni. Tuttavia, più a lungo l&#39;integrazione di [!DNL Marketo Measure] e [!DNL LinkedIn] è abilitata, più punti di contatto del modulo generazione lead saranno visibili tramite [!DNL Marketo Measure].

>[!NOTE]
>
>I costi di LinkedIn vengono comunque scaricati come parte delle campagne di contenuti sponsorizzati.


Prima dell&#39;esistenza dell&#39;integrazione di Forms con [!DNL Marketo Measure] e LinkedIn Lead Gen, era prassi comune per i clienti inviare i moduli a un programma Marketo e/o a una campagna CRM per tenere traccia dei moduli e ricevere l&#39;attribuzione su tali attività. Una volta abilitata l’impostazione Lead Gen Forms, vogliamo assicurarci che gli invii dei moduli non vengano conteggiati due volte. Verifica quanto segue:

* Il campo &quot;Abilita punti di contatto buyer&quot; nell’oggetto CRM è impostato su &quot;Nessuno&quot; o &quot;Escludi tutti i membri della campagna&quot;
* Aggiornare eventuali regole di attività del programma Marketo o Marketo correlate
* Aggiorna eventuali regole della campagna CRM correlate

>[!NOTE]
>
>L&#39;API LinkedIn ha un limite di lookback di 90 giorni, pertanto se utilizzi regole di Marketo o di gestione delle relazioni con i clienti, è consigliabile impostare la data di fine sulla regola su 90 giorni prima della data in cui hai abilitato l&#39;integrazione in [!DNL Marketo Measure].

## Dettagli punto di contatto {#touchpoint-details}

Dopo che [!DNL Marketo Measure] ha taggato correttamente la pagina di destinazione nella creatività di LinkedIn, puoi visualizzare i dati degli annunci risolti nel punto di contatto. Di seguito è riportata la mappatura dei valori di dati che si prevede di visualizzare:

<table>
 <colgroup>
  <col>
  <col>
 </colgroup>
 <tbody>
  <tr>
   <th style="width:30%">Campo punto di contatto</th>
   <th>Valore di esempio</th>
  </tr>
  <tr>
   <td>ID annuncio</td>
   <td>84186224</td>
  </tr>
  <tr>
   <td>Contenuto annuncio</td>
   <td>copy-1-image-2-man Il 95% degli esperti di marketing #B2B considera la strategia di creazione della domanda un successo. Ulteriori informazioni: [!DNL https]://lnkd.in/jgdi50vKrgv</td>
  </tr>
  <tr>
   <td>ID gruppo di annunci</td>
   <td>(vuoto)</td>
  </tr>
  <tr>
   <td>Nome gruppo di annunci</td>
   <td>(vuoto)</td>
  </tr>
  <tr>
   <td>ID campagna pubblicitaria</td>
   <td>138949954</td>
  </tr>
  <tr>
   <td>Nome campagna pubblicitaria</td>
   <td>Account SU - COM - Abilità della domanda</td>
  </tr>
  <tr>
   <td>URL di destinazione annuncio <b>*</b></td>
   <td>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders?_bl=84186217</td>
  </tr>
  <tr>
   <td>URL modulo</td>
   <td>info.bizible.com/demo</td>
  </tr>
  <tr>
   <td>URL modulo - Non elaborato</td>
   <td>info.bizible.com/demo</td>
  </tr>
  <tr>
   <td>ID parola chiave</td>
   <td>(vuoto)</td>
  </tr>
  <tr>
   <td>Tipo di corrispondenza parole chiave</td>
   <td>(vuoto)</td>
  </tr>
  <tr>
   <td>Pagina di destinazione</td>
   <td>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders</td>
  </tr>
  <tr>
   <td>Pagina di destinazione - Raw</td>
   <td>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders?_bl=84186217</td>
  </tr>
  <tr>
   <td>Canale di marketing</td>
   <td>Social a pagamento</td>
  </tr>
  <tr>
   <td>Canale di marketing - Percorso</td>
   <td>Social a pagamento.LinkedIn</td>
  </tr>
  <tr>
   <td>Canale</td>
   <td>"cpc" o "Modulo generazione lead"</td>
  </tr>
  <tr>
   <td>Pagina referrer</td>
   <td>www.linkedin.com/</td>
  </tr>
  <tr>
   <td>Pagina referrer - Raw</td>
   <td>www.linkedin.com/</td>
  </tr>
  <tr>
   <td>Frase di ricerca</td>
   <td>(vuoto)</td>
  </tr>
  <tr>
   <td>Tipo di punto di contatto</td>
   <td>Modulo web</td>
  </tr>
  <tr>
   <td>Source punto di contatto</td>
   <td>LinkedIn</td>
  </tr>
 </tbody>
</table>

Il campo &quot;URL di destinazione dell&#39;annuncio&quot; di **&#42;** _è compilato solo per il contenuto sponsorizzato. Non è compilata per la generazione di lead Forms._

<br>

## Costi {#costs}

Poiché [!DNL Marketo Measure] ha un&#39;integrazione diretta con [!DNL LinkedIn], ogni giorno vengono scaricate le spese registrate per ogni campagna e Creative. Non è più necessario che un cliente presenti un rapporto sulla spesa [!DNL LinkedIn] nell&#39;applicazione [!DNL Marketo Measure].

Come per altre integrazioni di annunci, [!DNL Marketo Measure] ha definito una regola del canale di marketing per inserire tutte le [!DNL LinkedIn] campagne, creatività e costo. Per utilizzare la regola, il cliente dovrà inserire una nuova riga per le attività di [!DNL LinkedIn] a pagamento. Può essere un canale nuovo o esistente. Nella colonna Referrer, utilizza la definizione &quot;[[!DNL LinkedIn] Paid]&quot; che [!DNL Marketo Measure] ha definito come qualsiasi punto di contatto con un tag [!DNL Marketo Measure].

![Come per altre integrazioni pubblicitarie, Marketo Measure ha definito un marketing](../assets/marketo-engage-activities-01.png)

## [!DNL Marketo Measure] individuazione {#marketo-measure-discover}

Sono stati apportati alcuni miglioramenti a [!DNL Marketo Measure] Discover per supportare la generazione di rapporti di Forms lead.

**Bacheca supporti a pagamento**

Titolo Forms di generazione lead: nuova tessera che include il conteggio dei riempimenti modulo di LinkedIn. Il drill-through di questo conteggio visualizzerà l’ID attività, la data del modulo, il nome del modulo e l’indirizzo e-mail.

**Scheda del percorso di coinvolgimento**

Percorso di eventi: include il tipo di evento &quot;Attività&quot; e il supporto &quot;Modulo generazione lead&quot; per i moduli che passano attraverso l’integrazione. La visualizzazione drill-through include i dettagli di Campaign, Creative e Form.

## Domande frequenti sui contenuti sponsorizzati {#sponsored-content-faq}

**Cos&#39;è una condivisione scura?**

Una dark share è un post in cui non viene mai pubblicato sulla pagina dell&#39;azienda e viene immediatamente creato e aggiunto direttamente come Creative. Affinché i Creativi creati da [!DNL Marketo Measure] non vengano visualizzati nella parte superiore della pagina di un&#39;azienda e vengano nuovamente promossi, vengono utilizzate condivisioni scure in modo che possa essere lanciato dietro le quinte.

**Quali sono gli stati contrassegnati da [!DNL Marketo Measure]?**

In una campagna [!DNL LinkedIn] e in Creative sono disponibili quattro stati diversi: Attivo, In pausa, Archiviato e Annullato. Eseguiamo il tag solo per le campagne e le creatività attive. Se si assegnano tag ad altri stati, questi verranno impostati nuovamente su Attivo. [!DNL Marketo Measure] non assegnerà tag alle campagne o alle creatività in pausa, archiviate o annullate, ma riprenderà l&#39;assegnazione tag se lo stato diventa Attivo.

**Qual è il valore utilizzato da [!DNL Marketo Measure] per assegnare tag?**

Alla fine dell&#39;URL di destinazione, [!DNL Marketo Measure] sta aggiungendo il parametro `&_bl={creativeId}`, dove `{creativeId}` è l&#39;ID Creative da LinkedIn. Con l&#39;ID Creative, [!DNL Marketo Measure] può anche determinare l&#39;ID campagna poiché [!DNL LinkedIn] ha una struttura di annunci piuttosto semplice, in quanto ogni Creative può appartenere a una sola campagna.

**Cosa succede al mio vecchio contenuto creativo quando [!DNL Marketo Measure] ne crea una nuova versione?**

Quando [!DNL Marketo Measure] ricrea una condivisione e la inserisce in un nuovo Creative, il vecchio Creative viene archiviato. Questo è anche il motivo per cui [!DNL Marketo Measure] non assegnerà tag alle campagne o ai creativi archiviati; in caso contrario, [!DNL Marketo Measure] tenterebbe di assegnare tag indefinitamente.

**Perché l&#39;URL di destinazione dell&#39;annuncio creato non corrisponde all&#39;annuncio originale?**

[!DNL Marketo Measure] deve aggiungere i parametri di tracciamento a un URL risolto, ma l&#39;URL presentato nell&#39;API può potenzialmente essere un URL abbreviato senza tutti i parametri presenti. Per ovviare a questo problema, [!DNL Marketo Measure] cerca gli URL abbreviati prima di ricreare un&#39;aggiunta, la risolve, quindi crea il nuovo annuncio con l&#39;URL risolto e tutti i relativi parametri, consentendo a [!DNL Marketo Measure] di aggiungere tag.

**Stai assegnando tag a tutti i miei annunci? Il parametro bl non viene visualizzato in tutte le pagine di destinazione?**

Alcuni esperti di marketing hanno rilevato che inseriranno un collegamento immagine nell&#39;URL di destinazione, al quale [!DNL Marketo Measure] non può assegnare tag, pertanto cerchiamo l&#39;URL all&#39;interno del contenuto dell&#39;annuncio. Se [!DNL Marketo Measure] dispone delle autorizzazioni per assegnare tag agli URL abbreviati, espanderemo l&#39;URL e il tag che, ma a causa della struttura di copia di LinkedIn, viene automaticamente abbreviato all&#39;interno del testo. Il tag si troverà nell’URL abbreviato di LinkedIn, che verrà visualizzato nel campo Ad Content (Contenuto annuncio) del punto di contatto anziché nel campo Landing Page - Raw (Pagina di destinazione - Non elaborato).

**Oh no, qualcuno nel mio team ha clonato accidentalmente una condivisione. Posso metterlo in pausa?**

Nessun problema. [!DNL Marketo Measure] controllerà a livello di programmazione la presenza di condivisioni non più univoche, ovvero che sono state copiate in un altro Creative. Una volta rilevata la copia, [!DNL Marketo Measure] seguirà il solito flusso per assegnare tag e creare nuovi annunci.

**Il mio annuncio era in attesa di revisione in precedenza. Perché è di nuovo in attesa di revisione dopo che [!DNL Marketo Measure] l&#39;ha taggata?**

LinkedIn richiede che tutti gli annunci creati o modificati vengano sottoposti al normale processo di sicurezza prima della pubblicazione. [!DNL Marketo Measure] tenta di intercettare l&#39;annuncio il più rapidamente possibile, eseguendo la scansione per nuovi annunci ogni 6 ore, ma con [!DNL LinkedIn's] passaggio aggiuntivo, può ritardare il lancio di alcune ore.

**Sono presenti 2 URL nel mio annuncio. A quale viene assegnato un tag?**

Entrambi. L&#39;integrazione di [!DNL Marketo Measure] consente di assegnare tag all&#39;URL di destinazione dall&#39;immagine click-through nell&#39;annuncio, ma aggiorna anche automaticamente l&#39;URL abbreviato nella descrizione dell&#39;annuncio.

![Entrambi. L&#39;integrazione di Marketo Measure ci consente di assegnare tag alla destinazione](assets/select-type-1.png)

**Ho connesso il mio account [!DNL LinkedIn ads]. Perché [!DNL Marketo Measure] non sta assegnando tag ai miei collegamenti?**

L&#39;utente [!DNL LinkedIn] connesso deve disporre dell&#39;accesso di modifica corretto, ovvero deve essere un Account Manager, Campaign Manager o Creative Manager.

**Come posso sapere se la mia creatività verrà copiata? Posso vedere se i miei creativi usano la stessa condivisione?**

L&#39;ID di condivisione non viene fornito in un report [!DNL LinkedIn], pertanto non esiste un modo chiaro e ovvio per verificare la presenza di mappature da creatività a condivisione. Se si sospetta che un contenuto creativo possa essere una copia, è possibile controllare manualmente aprendo l&#39;annuncio dall&#39;interno del gestore [!DNL LinkedIn] Campaign. In questo modo l&#39;annuncio verrà aperto in una nuova scheda e sarà possibile trovare l&#39;ID condivisione nell&#39;URL.

![L&#39;ID di condivisione non è specificato in un report LinkedIn, quindi](assets/linkedin-integration-02.png)

## Domande frequenti su Forms della generazione lead {#lead-gen-forms-faq}

**Qual è il costo di questo miglioramento?**

Questa offerta è inclusa in qualsiasi abbonamento a pagamento di [!DNL Marketo Measure].

**L&#39;integrazione è retroattiva?**

Sì, scaricheremo le risposte storiche ai moduli pubblicitari da LinkedIn, anche se siamo limitati all’intervallo di lookback di 90 giorni. Più a lungo l&#39;integrazione di [!DNL Marketo Measure] e LinkedIn è abilitata, più punti di contatto del modulo della generazione lead saranno visibili tramite [!DNL Marketo Measure].

Non è possibile impostare una data specifica per il download, ma è possibile impostare facoltativamente le regole di eliminazione dei punti di contatto se sono presenti punti di contatto da eliminare.

**L&#39;opzione verrà attivata automaticamente se si sta già utilizzando l&#39;integrazione degli annunci LinkedIn di [!DNL Marketo Measure]?**

No, non inizieremo automaticamente a scaricarlo per tutti i clienti, ma è un passaggio molto semplice per abilitare questa funzione nelle impostazioni.

**I dati del modulo sono disponibili?**

I dati del modulo sono disponibili tramite [!DNL Marketo Measure] Discover, inclusi ID modulo e nome modulo. I dettagli del modulo non sono ancora disponibili sugli oggetti punto di contatto nel sistema di gestione delle relazioni con i clienti.

**Cosa succederà a qualsiasi lead [!DNL LinkedIn] che sia stato precedentemente sincronizzato con i programmi di Marketo o con le campagne CRM?**

È consigliabile modificare le regole di [!DNL Marketo Measure] per generare punti di contatto da tali programmi o campagne specifiche, al fine di evitare duplicazioni. L&#39;API LinkedIn ha un limite di lookback di 90 giorni, pertanto se utilizzi regole di Marketo o di gestione delle relazioni con i clienti, è consigliabile impostare la data di fine sulla regola su 90 giorni prima della data in cui hai abilitato l&#39;integrazione in [!DNL Marketo Measure]. Da questo momento in poi, [!DNL Marketo Measure] potrà scaricare i lead con maggiori dettagli e insight.

**Sono coinvolti l&#39;assegnazione di tag automatici o il tracciamento?**

No, è diverso dalle altre integrazioni [!DNL Marketo Measure]. Anziché modificare la pagina di destinazione (poiché non vi è alcun click-through nella pagina di destinazione), stiamo solo scaricando le informazioni rilevanti da LinkedIn e le stiamo trattando come attività all&#39;interno di [!DNL Marketo Measure].
