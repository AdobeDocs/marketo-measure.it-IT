---
unique-page-id: 35586080
description: Integrazione linkedIn - [!DNL Marketo Measure] - Documentazione del prodotto
title: Integrazione linkedIn
exl-id: 705209ef-1ece-496c-ac2f-6a31055bd993
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '2594'
ht-degree: 0%

---

# Integrazione linkedIn {#linkedin-integration}

## Panoramica {#overview}

La [!DNL Marketo Measure] L’integrazione con LinkedIn è suddivisa in due parti:

Contenuto sponsorizzato: L’integrazione dei contenuti sponsorizzati consente [!DNL Marketo Measure] per assegnare tag agli URL di destinazione [!DNL LinkedIn] annunci, che alla fine consente [!DNL Marketo Measure] per seguire un utente attraverso l’intero percorso di punti di contatto e mappare l’attività sullo specifico [!DNL LinkedIn] Campagna e creativo. Questo fornisce ai clienti informazioni sul ROI del loro [!DNL LinkedIn] attività.

Lead Gen Forms: Grazie all’integrazione con LinkedIn Lead Gen Forms, Marketo Measure offre informazioni approfondite sui moduli inviati tramite la piattaforma LinkedIn. Queste compilazioni vengono confrontate con i lead provenienti dal tuo CRM o [!DNL Marketo Engage] in modo che siano idonei all’attribuzione. Grazie alle informazioni approfondite su Campaign, Creative e Form che hanno contribuito alla generazione dei moduli, i team possono ora ottimizzare ulteriormente le attività di marketing e di spesa pubblicitaria di LinkedIn.

## Disponibilità {#availability}

Disponibile per tutti i clienti.

## Requisiti {#requirements}

**Ruoli di Campaign Manager**

Per [!DNL Marketo Measure] per poter scaricare i dati dei costi di Ads Data &amp; Ads, in Campaign Manager devi disporre di uno dei seguenti ruoli:

* Amministratore fatturazione
* Account Manager
* Campaign Manager

Ulteriori informazioni: [Ruoli utente e funzioni in Campaign Manager](https://www.linkedin.com/help/lms/answer/a425731/user-roles-and-functions-in-campaign-manager).

**Ruoli dell’amministratore di file multimediali a pagamento**

Per [!DNL Marketo Measure] per poter creare/aggiornare i creativi sponsorizzati, devi disporre di uno dei seguenti ruoli di amministratore di file multimediali a pagamento:

* Poster contenuto sponsorizzato
* Direttore generale Forms Manager

Ulteriori informazioni: [Ruoli dell’amministratore della pagina linkedIn](https://www.linkedin.com/help/linkedin/answer/4783/linkedin-page-admin-roles-overview).

Ce ne sono altri [!DNL LinkedIn] ruoli che svolgiamo **not** richiedono la nostra integrazione. Questi ruoli sono spesso erronei per i ruoli richiesti, quindi si prega di notare che c&#39;è una differenza!

**Ruoli amministratore pagina**

Per [!DNL Marketo Measure] per poter scaricare/integrare i lead dai moduli lead gen, devi disporre del seguente ruolo Amministratore pagina:

* Super amministratore

Ulteriori informazioni: [Ruoli dell’amministratore della pagina linkedIn](https://www.linkedin.com/help/linkedin/answer/4783/linkedin-page-admin-roles-overview).

## Tipi di annunci linkedIn {#linkedin-ad-types}

[!DNL Marketo Measure] supporterà:

**Contenuto sponsorizzato:** Il contenuto sponsorizzato consente di fornire contenuti al [!DNL LinkedIn] feed di membri oltre a quelli che seguono la tua azienda. Il contenuto sponsorizzato può essere indirizzato a un pubblico specifico e può aiutare gli inserzionisti a raggiungere [!DNL LinkedIn] i membri, ovunque e ogni volta che sono impegnati nel [!DNL LinkedIn] piattaforma per desktop, dispositivi mobili e tablet. Sono supportati i contenuti sponsorizzati con lead Gen Forms .

Tipi di formati di annunci di contenuto sponsorizzato supportati da [!DNL Marketo Measure] sono Annunci per immagini singole e annunci video (tramite Lead Gen Forms). A causa della complessità dello schema, gli annunci Carosello non sono supportati.

[!DNL Marketo Measure] non supporta messaggi sponsorizzati, annunci di testo o annunci dinamici.

![](assets/one.png)

>[!TIP]
>
>Per una campagna/spesa che proviene da un’origine di contenuto non sponsorizzata (come il tipo di campagna &quot;Annuncio di testo&quot; o &quot;Posta sponsorizzata&quot;), [!DNL Marketo Measure] does _not_ supporta intrinsecamente il tracciamento di questi tipi di campagne. Se desideri tenere traccia della spesa per campagne come queste insieme alla spesa per &quot;contenuto sponsorizzato&quot;, assicurati di utilizzare il CSV della spesa marketing per registrare manualmente la spesa.

## Come funziona: Contenuto sponsorizzato {#how-it-works-sponsored-content}

>[!NOTE]
>
>Prima del primo utilizzo, questa impostazione della funzione deve essere attivata selezionando [!DNL Marketo Measure] [!UICONTROL Settings] > [!UICONTROL Integrations] > [!UICONTROL Ads] > [!UICONTROL Enable LinkedIn Lead Gen Forms].

**[!DNL LinkedIn's]Requisiti unici di assegnazione tag automatica**

[!DNL Marketo Measure] può aiutare a tenere traccia delle [!DNL LinkedIn] prestazioni della campagna tramite l’assegnazione automatica dei tag alle pagine di destinazione.

[!DNL Marketo Measure] cercherà i creativi con una condivisione LinkedIn univoca e aggiungerà una `?_bl={creativeId}` alla fine.

**Copia delle azioni**

Con questo [!DNL Marketo Measure/LinkedIn] Integrazione, si chiede ai clienti di non copiare/duplicare Creative esistenti. Se le azioni sono trovate e sono rilevate per essere utilizzate solo su un creativo, [!DNL Marketo Measure] Puoi assegnare il tag Condividi così come è senza dover ricreare alcun creativo o condivisione e la cronologia di tutti gli annunci (impression, clic, condivisioni) rimarrà invariata.

Non appena si scopre che una condivisione è condivisa tra più creativi, [!DNL Marketo Measure] per creare un set univoco, sarà necessario eseguire un processo di sospensione, copia e riassegnazione tag. [!DNL Marketo Measure] mette in pausa e archivia i contenuti creativi in diretta e cancella quindi la cronologia degli annunci, compresi impression, clic e condivisioni social, per assegnare automaticamente i tag desiderati a tutto.

Progredire, [!DNL Marketo Measure] consiglia di non duplicare nessuna [!DNL LinkedIn] Condividi e mantieni tutti i creativi e le condivisioni il più possibile unici in modo da poter semplicemente aggiungere il nostro tracciamento senza dover cancellare la cronologia degli annunci.

**URL abbreviati**

Il motivo del passaggio aggiuntivo è che LinkedIn consente agli URL di destinazione di essere un URL abbreviato (bit.ly, goog.le, ecc.), il che significa [!DNL Marketo Measure] non visualizza l&#39;URL lungo e risolto e [!DNL Marketo Measure] deve aggiungere parametri di tracciamento a un URL risolto. Per aggirare il problema, [!DNL Marketo Measure] cerca gli URL abbreviati prima di ricreare un annuncio, espande l&#39;URL, quindi crea il nuovo annuncio con l&#39;URL risolto e tutti i relativi parametri, consentendo [!DNL Marketo Measure] per aggiungere tag. La creazione di un nuovo annuncio cancellerà la cronologia degli annunci (impression, clic, condivisioni), quindi la necessità di disporre delle autorizzazioni per assegnare tag agli URL abbreviati.

Se utilizzi URL abbreviati, questo potrebbe avere un forte impatto sui tuoi creativi. È consigliabile non utilizzare più URL abbreviati in modo da [!DNL Marketo Measure] può assegnare tag alle pagine di destinazione senza dover creare nuovi annunci e cancellare la cronologia degli annunci.

**Il processo**

Cominciamo con alcuni esempi. Diciamo che abbiamo....

Creative A : Condividi 123\
Creative B : Condividi 234\
Creative C : Condividi 234\
Creative D : Condividi 234

![](assets/two.png)

`1)` [!DNL Marketo Measure] esamina innanzitutto tutte le campagne, i creativi e le azioni con uno stato &quot;Attivo&quot;. [!DNL Marketo Measure] gli annunci messi in pausa, archiviati o annullati non verranno assegnati a tag. Se un annuncio è stato messo in pausa, imposta su [!UICONTROL active], lo taggeremo una volta che è di nuovo attivo. Se è disponibile una condivisione univoca, ovvero non viene utilizzata per più creativi o campagne (ad esempio, Creative A : 123), [!DNL Marketo Measure] aggiungerà il nostro parametro personalizzato `>> ?_bl={creativeId}` all&#39;URL di condivisione.

`2)` Ora se la condivisione è stata condivisa e ha perso la sua unicità (per esempio, Creative B : Condividi 234 e Creative C : Share 234 and Creative D : Share 234), [!DNL Marketo Measure] mette in pausa e archivia tutte le creatività simili (che sarebbero Creative B, Creative C e Creative D).

`3)` [!DNL Marketo Measure] Creerà 3 nuovi creativi, Creative E, Creative F e Creative G, che copia il contenuto di Creative B, che è archiviato.

`4)` [!DNL Marketo Measure] creerà anche 3 nuove azioni, Share 345, Share 456 e Share 567, che copia il contenuto di Share 234, tranne che avrà il proprio unico `?_bl` assegnazione tag.

`5)` [!DNL Marketo Measure] Dovremo controllare regolarmente che le azioni non vengano condivise e, in caso affermativo, riavvieremo il processo al punto 2.

>[!NOTE]
>
>Implementare questo significa che i nostri clienti perderanno la cronologia degli annunci del Creative B : Condividi 234, creativo C : Share 234 and Creative D : Condividi 234 perché ora viene ricreato con Creative E : Share 345, Share F : Condividi 456 e Creative G : Condividi rispettivamente 567.

![](assets/three.png)

## Come funziona: Forms a capo generale {#how-it-works-lead-gen-forms}

**Il processo**

Attraverso [!DNL LinkedIn's] API per moduli di annunci e API per la risposta a moduli di annunci, siamo in grado di raccogliere i dati di invio del modulo per un account di annunci e di associare l’indirizzo e-mail a un lead dal CRM o da Marketo.

I moduli linkedIn possono contenere più indirizzi e-mail. Quando scaricheremo le risposte dei moduli, cercheremo gli indirizzi e-mail con la seguente priorità: Posta elettronica di lavoro, indirizzo e-mail (campo modulo principale) o campi personalizzati con un valore e-mail valido.

Indipendentemente dallo stato Campaign o Creative, tutte le risposte modulo creeranno un punto di contatto. [!DNL Marketo Measure] ha un limite di lookback di 90 giorni, quindi [!DNL Marketo Measure] non è in grado di accedere alle risposte del modulo per più di 90 giorni, ma più a lungo il [!DNL Marketo Measure] e [!DNL LinkedIn] l’integrazione è abilitata, più punti di contatto per i moduli lead Gen saranno visibili tramite [!DNL Marketo Measure].

>[!NOTE]
>
>I costi di linkedIn vengono ancora scaricati come parte delle campagne sui contenuti sponsorizzati.

**Tracciamento del lead Gen Forms in CRM o Marketo**

Prima della [!DNL Marketo Measure] Esisteva l’integrazione di LinkedIn Lead Gen Forms , era pratica comune per i clienti inviare i propri moduli a un programma Marketo e/o a una campagna CRM per tenere traccia dei moduli e ricevere l’attribuzione su tali attività. Una volta abilitata l’impostazione Lead Gen Forms , vogliamo assicurarci che gli invii dei moduli non siano conteggiati due volte. Controlla quanto segue:

* Il campo &quot;Abilita punti di contatto dell’acquirente&quot; nell’oggetto CRM è impostato su &quot;Nessuno&quot; o &quot;Escludi tutti i membri della campagna&quot;
* Aggiornare eventuali regole correlate relative al programma Marketo o all’attività Marketo
* Aggiorna tutte le regole correlate alla campagna CRM

>[!NOTE]
>
>L’API LinkedIn dispone di un limite di lookback di 90 giorni; pertanto, se utilizzi le regole Marketo o CRM, ti consigliamo di impostare la data di fine della regola su 90 giorni prima della data in cui hai abilitato l’integrazione in [!DNL Marketo Measure].

## Dettagli dei punti di contatto {#touchpoint-details}

Una volta [!DNL Marketo Measure] la pagina di destinazione è stata contrassegnata correttamente nel contenuto creativo di LinkedIn e potrai visualizzare i dati degli annunci risolti sul punto di contatto. Di seguito è riportata la mappatura dei valori dei dati che dovrebbero essere visualizzati:

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th>Campo punto di contatto</th> 
   <th>Valore di esempio</th> 
  </tr> 
  <tr> 
   <td><p>Id annuncio </p></td> 
   <td><p>84186224 </p></td> 
  </tr> 
  <tr> 
   <td><p>Contenuto annuncio </p></td> 
   <td><p>copy-1-image-2-man 95% degli esperti di marketing #B2B ritiene che la strategia di creazione della domanda abbia successo. Ulteriori informazioni: [!DNL https]://lnkd.in/jgdi50vKrgv</p></td> 
  </tr> 
  <tr> 
   <td><p>Id Gruppo Di Annunci </p></td> 
   <td><p>(vuoto) </p></td> 
  </tr> 
  <tr> 
   <td><p>Nome gruppo di annunci </p></td> 
   <td><p>(vuoto) </p></td> 
  </tr> 
  <tr> 
   <td><p>Id campagna annunci </p></td> 
   <td><p>138949954 </p></td> 
  </tr> 
  <tr> 
   <td><p>Nome della campagna pubblicitaria </p></td> 
   <td><p>SU - Account COM - Competenze della domanda </p></td> 
  </tr> 
  <tr> 
   <td><p>URL destinazione annuncio </p></td> 
   <td><p>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders?_bl=84186217 </p></td> 
  </tr> 
  <tr> 
   <td><p>URL modulo </p></td> 
   <td><p>info.bizible.com/demo </p></td> 
  </tr> 
  <tr> 
   <td><p>URL del modulo - Raw </p></td> 
   <td><p>info.bizible.com/demo </p></td> 
  </tr> 
  <tr> 
   <td><p>ID parola chiave </p></td> 
   <td><p>(vuoto) </p></td> 
  </tr> 
  <tr> 
   <td><p>Tipo di corrispondenza parola chiave </p></td> 
   <td><p>(vuoto) </p></td> 
  </tr> 
  <tr> 
   <td><p>Pagina di destinazione </p></td> 
   <td><p>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders </p></td> 
  </tr> 
  <tr> 
   <td><p>Pagina di destinazione - Raw </p></td> 
   <td><p>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders?_bl=84186217 </p></td> 
  </tr> 
  <tr> 
   <td><p>Canale di marketing </p></td> 
   <td><p>Social a pagamento </p></td> 
  </tr> 
  <tr> 
   <td><p>Canale di marketing - Percorso </p></td> 
   <td><p>Social.LinkedIn a pagamento </p></td> 
  </tr> 
  <tr> 
   <td><p>Medium </p></td> 
   <td><p>"cpc" o "Modulo lead Gen"</p></td> 
  </tr> 
  <tr> 
   <td><p>Pagina di riferimento </p></td> 
   <td><p>www.linkedin.com/ </p></td> 
  </tr> 
  <tr> 
   <td><p>Pagina di riferimento - Raw </p></td> 
   <td><p>www.linkedin.com/ </p></td> 
  </tr> 
  <tr> 
   <td><p>Frase di ricerca </p></td> 
   <td><p>(vuoto) </p></td> 
  </tr> 
  <tr> 
   <td><p>Tipo punto di contatto </p></td> 
   <td><p>Modulo Web </p></td> 
  </tr> 
  <tr> 
   <td><p>Origine punto di contatto </p></td> 
   <td><p>LinkedIn </p></td> 
  </tr> 
 </tbody> 
</table>

## Costi {#costs}

Perché [!DNL Marketo Measure] ha un’integrazione diretta con [!DNL LinkedIn], scaricamo ogni giorno la spesa registrata per ogni campagna e creativo. Non è necessario che un cliente presenti rapporti su [!DNL LinkedIn] spendere entro [!DNL Marketo Measure] applicazione ancora.

Come con altre integrazioni pubblicitarie, [!DNL Marketo Measure] ha definito una regola del canale di marketing per posizionare tutto [!DNL LinkedIn] campagne, creativi e costi. Per utilizzare la regola, il cliente vorrà inserire una nuova riga per la propria Pagata [!DNL LinkedIn] sforzi. Può essere un canale nuovo o esistente. Nella colonna Referente, utilizza la definizione &quot;[[!DNL LinkedIn] Pagato]&quot; che [!DNL Marketo Measure] ha definito come qualsiasi punto di contatto con un [!DNL Marketo Measure] tag .

![](assets/four.png)

## [!DNL Marketo Measure] Scopri {#marketo-measure-discover}

Sono stati apportati alcuni miglioramenti a [!DNL Marketo Measure] Scopri come supportare i rapporti di Lead Gen Forms.

**Scheda madre a pagamento**

Riquadro Forms lead Gen: Nuovo riquadro che include il conteggio dei riempimenti dei moduli LinkedIn. Il drill-through di questo conteggio mostrerà l&#39;ID attività, la data del modulo, il nome del modulo e l&#39;indirizzo e-mail.

**Scheda del percorso di coinvolgimento**

Percorso di eventi: Include il tipo di evento &quot;Attività&quot; e il formato &quot;Lead Gen Form&quot; per i moduli che passano attraverso l’integrazione. La visualizzazione drill-through include i dettagli di Campaign, Creative e Form.

## Domande frequenti sui contenuti sponsorizzati {#sponsored-content-faq}

**Cos&#39;è una condivisione scura?**

Una condivisione scura è un post in cui non viene mai pubblicato sulla pagina aziendale e viene immediatamente creato e aggiunto direttamente come creativo. Così [!DNL Marketo Measure]I creativi creati non appaiono nella parte superiore della pagina di un&#39;azienda e vengono promossi di nuovo, le condivisioni scure vengono utilizzate in modo che possano essere lanciati dietro le quinte.

**Funzionamento degli stati [!DNL Marketo Measure] davvero tag?**

Ci sono quattro stati diversi su un [!DNL LinkedIn] Campagna e creativo: Attivo, In pausa, Archiviato e Annullato. Assegniamo tag solo a Campagne e creativi attivi. Assegnare tag ad altri stati impostarli nuovamente su Attivo. [!DNL Marketo Measure] Non contrassegna campagne o creativi in pausa, archiviati o annullati, ma riprende l’assegnazione tag se lo stato cambia in Attivo.

**Qual è il valore [!DNL Marketo Measure] utilizza per assegnare tag?**

Alla fine dell’URL di destinazione, [!DNL Marketo Measure] sta aggiungendo il parametro `&_bl={creativeId}`, dove `{creativeId}` è l&#39;ID creativo di LinkedIn. Con l&#39;ID creativo, [!DNL Marketo Measure] può inoltre determinare l’ID campagna dal [!DNL LinkedIn] dispone di una struttura di annunci abbastanza semplice, in quanto ogni creativo può appartenere a una sola campagna.

**Cosa succede una volta con il mio vecchio creativo [!DNL Marketo Measure] crea una nuova versione?**

Quando [!DNL Marketo Measure] ricrea una condivisione e la inserisce in un nuovo Creative, il vecchio Creative viene archiviato. Anche per questo [!DNL Marketo Measure] non contrassegnerà campagne o creativi archiviati, altrimenti verrà ripetuto con [!DNL Marketo Measure] cercando di etichettarlo a tempo indefinito.

**Perché l&#39;URL di destinazione dell&#39;annuncio creato non corrisponde al mio annuncio originale?**

[!DNL Marketo Measure] deve aggiungere i parametri di tracciamento a un URL risolto, ma l’URL presentato nell’API può potenzialmente essere un URL abbreviato senza tutti i parametri presenti. Per aggirare il problema, [!DNL Marketo Measure] cerca gli URL abbreviati prima di ricreare un add, lo risolve, quindi crea il nuovo annuncio con l&#39;URL risolto e tutti i suoi parametri, consentendo [!DNL Marketo Measure] per aggiungere tag.

**Stai contrassegnando tutti i miei annunci? Il parametro bl non viene visualizzato su tutte le pagine di destinazione?**

Abbiamo osservato che alcuni addetti al marketing inseriranno un collegamento immagine nell’URL di destinazione, che [!DNL Marketo Measure] Non è possibile assegnare tag, quindi cerchiamo l’URL all’interno del contenuto dell’annuncio. Se [!DNL Marketo Measure] dispone delle autorizzazioni per assegnare tag agli URL abbreviati, verrà espanso l’URL e il tag che, ma a causa della struttura di copia di LinkedIn, viene automaticamente abbreviato all’interno del testo. Il tag vivrà all’interno dell’URL abbreviato di LinkedIn, che verrà visualizzato nel campo Ad Content del punto di contatto anziché nel campo Landing Page - Raw .

**Oh no, qualcuno della mia squadra ha accidentalmente clonato una parte. Posso metterlo in pausa?**

Niente preoccupazioni. [!DNL Marketo Measure] controllerà programmaticamente le condivisioni che non sono più univoche, il che significa che da allora sono state copiate in un Creative diverso. Una volta rilevata la copia, [!DNL Marketo Measure] seguirà il flusso consueto per assegnare tag e creare nuovi annunci.

**Il mio annuncio era in attesa di revisione prima. Perché la revisione è ancora in sospeso dopo [!DNL Marketo Measure] etichettato?**

linkedIn richiede che tutti gli annunci creati o modificati passino attraverso il normale processo di sicurezza prima che venga pubblicato. [!DNL Marketo Measure] cerca di intercettare l&#39;annuncio il più rapidamente possibile, in quanto cerca nuovi annunci ogni 6 ore ma con [!DNL LinkedIn's] inoltre, può ritardare il lancio di qualche ora.

**Il mio annuncio contiene 2 URL. Quale viene taggato?**

Entrambi. La [!DNL Marketo Measure] l’integrazione ci consente di assegnare tag all’URL di destinazione dall’immagine di click-through nell’annuncio, ma aggiorna anche automaticamente l’URL abbreviato nella descrizione dell’annuncio.

![](assets/five.png)

**Ho collegato il mio [!DNL LinkedIn ads] conto. Perché no? [!DNL Marketo Measure] assegnare tag ai collegamenti?**

Collegato [!DNL LinkedIn] l’utente deve disporre di un accesso di modifica adeguato, il che significa che deve essere un Account Manager, Campaign Manager o Creative Manager.

**Come posso sapere se il mio creativo verrà copiato? Posso vedere se i miei creativi usano la stessa condivisione?**

L&#39;ID della condivisione non viene fornito in un [!DNL LinkedIn] quindi non esiste un modo chiaro e ovvio per verificare la presenza di mappature creative-to-share. Se sospetti che un creativo possa essere una copia, puoi controllare manualmente aprendo l&#39;annuncio dall&#39;interno del tuo [!DNL LinkedIn] Campaign manager: questo aprirà l’annuncio in una nuova scheda e troverai l’ID condivisione nell’URL.

![](assets/six.png)

## Domande frequenti su Forms di lead Gen {#lead-gen-forms-faq}

**Qual è il costo di questo miglioramento?**

Questa offerta è inclusa con qualsiasi pagamento [!DNL Marketo Measure] abbonamento.

**L&#39;integrazione è retroattiva?**

Sì, scaricheremo le risposte per i moduli di annunci storici da LinkedIn, anche se siamo limitati all’intervallo di lookback di 90 giorni. Più il [!DNL Marketo Measure] e l’integrazione di LinkedIn è abilitata, più i punti di contatto per i moduli lead Gen saranno visibili tramite [!DNL Marketo Measure].

Non è disponibile alcuna opzione per impostare una data specifica per il download, ma è possibile impostare facoltativamente le regole di eliminazione dei punti di contatto in presenza di punti di contatto da eliminare.

**Questo verrà attivato automaticamente se sto già utilizzando il [!DNL Marketo Measure] Integrazione di annunci linkedIn?**

No, non inizieremo automaticamente a scaricarlo per tutti i clienti, ma è un interruttore molto semplice per abilitare questa funzione nelle impostazioni.

**I dati del modulo sono disponibili?**

I dati del modulo sono disponibili tramite [!DNL Marketo Measure] Scopri l’ID del modulo e il nome del modulo. I dettagli del modulo non sono ancora disponibili sugli oggetti punto di contatto nel CRM.

**Cosa succede a qualsiasi [!DNL LinkedIn] lead precedentemente sincronizzati con i programmi Marketo o le campagne CRM?**

Si consiglia di regolare qualsiasi [!DNL Marketo Measure] regole per generare punti di contatto da programmi o campagne specifici per evitare duplicazioni. L’API LinkedIn dispone di un limite di lookback di 90 giorni; pertanto, se utilizzi le regole Marketo o CRM, ti consigliamo di impostare la data di fine della regola su 90 giorni prima della data in cui hai abilitato l’integrazione in [!DNL Marketo Measure]. Da questo punto in poi, [!DNL Marketo Measure] Puoi scaricare questi lead con maggiori informazioni e dettagli.

**Sono coinvolti tag o tracciamento automatici?**

No, è diverso dagli altri [!DNL Marketo Measure] integrazioni. Invece di modificare la pagina di destinazione (poiché non esiste una pagina di destinazione per il click-through), stiamo solo scaricando le informazioni rilevanti da LinkedIn e le consideriamo come attività all’interno di [!DNL Marketo Measure].
