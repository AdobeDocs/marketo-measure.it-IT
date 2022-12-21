---
unique-page-id: 42762310
description: Sincronizzazione dei dati storici - [!DNL Marketo Measure] - Documentazione del prodotto
title: Sincronizzazione dei dati storici
exl-id: 5a3c1a71-463a-4d75-98b9-fc225839512a
source-git-commit: 02f686645e942089df92800d8d14c76215ae558f
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 0%

---

# Sincronizzazione dei dati storici {#syncing-historical-data}

[!DNL Marketo Measure] è una soluzione che fornisce i dati più granulari e actionable. Sappiamo tuttavia che potresti disporre di dati esistenti per i quali desideri essere attribuito. È possibile generare punti di contatto per i dati storici, ma è importante prendere in considerazione alcuni fattori prima di procedere con questo processo.

## Fattori da considerare {#factors-to-consider}

**I dati sono già organizzati in campagne?**

a) I dati devono essere organizzati in Campagne da sincronizzare in [!DNL Marketo Measure] per generare punti di contatto. Se non è attualmente organizzato in Campagne, è necessario valutare se vale la pena di tempo e risorse necessari per segmentare i dati nelle campagne appropriate.

b) La data in cui il membro è stato aggiunto alla campagna o contrassegnato come risposta verrà utilizzata per la data del punto di contatto, quindi anche questo deve essere preciso. [!DNL Marketo Measure] offre soluzioni alternative sia in SFDC che in MSD per aggiornare le date, ma questo potrebbe richiedere molto tempo a seconda del volume.

**Hai una quantità di dati abbastanza uguale organizzata in campagne per tutti i canali (ricerca a pagamento, eventi, biologici, ecc.)?**

È importante avere un quadro equilibrato dell&#39;attribuzione per ottenere un reporting accurato ed equo. Ad esempio, se disponi solo di dati per le attività storiche del canale offline come Eventi, i dati saranno intrinsecamente di parte senza i dati online storici per completarli.

**Che livello di granularità si aspetta?**

Conoscerai essenzialmente solo il nome del canale, del canale secondario e della campagna.

**Quali sono i tuoi obiettivi di reporting in futuro?**

Questi dati saranno limitati, quindi è importante considerare come si intende utilizzarli. Potrebbe non avere senso confrontare dati storici con dati futuri.

**Quanto tempo indietro vuoi andare?**

[!DNL Marketo Measure] consiglia vivamente di non andare oltre l&#39;anno precedente.

Questo è un argomento che incoraggiamo vivamente a discutere con il vostro [!DNL Marketo Measure] contatta prima. Se hai considerato quanto sopra e desideri procedere, istruzioni generali (separate per [!DNL Salesforce] e [!DNL Microsoft Dynamics]) sono riportate di seguito.

## Sincronizzazione delle campagne storiche in [!DNL Salesforce] {#syncing-historic-campaigns-in-salesforce}

**Online:**

Per sincronizzare i dati cronologici online, è necessario organizzarli in campagne Salesforce a cui eseguire la sincronizzazione [!DNL Marketo Measure] tramite [!DNL Salesforce] Regole di sincronizzazione delle campagne nel [!DNL Marketo Measure] app. È importante assicurarsi che i punti di contatto non vengano generati da nessuna di queste campagne dopo la data in cui il tuo JavaScript è diventato attivo. Questo accade perché evita la duplicazione dei punti di contatto. Una volta che JavaScript è attivo, gli sforzi online vengono tracciati automaticamente, quindi non vogliamo monitorarli anche tramite una campagna SFDC. Per evitare questo problema, assicurati di aggiungere un senso di tempo alla regola. Forse qualcosa come &quot;Data creazione membro della campagna&quot; è minore di [Data di pubblicazione JavaScript]&quot;.

![](assets/syncing-historical-data-1.png)

Il componente di mappatura dei canali per i dati online storici può essere un po&#39; complicato. Vogliamo che corrisponda il più possibile alle regole del canale online correnti (dal foglio delle regole online) per un reporting pulito. Di seguito è riportato un esempio di mappatura del canale ideale.

>[!NOTE]
>
>Questa mappatura del canale viene eseguita nel [!UICONTROL Offline Channels] della sezione [!DNL Marketo Measure] da quando utilizziamo campagne SFDC.

| Tipo campagna Salesforce | Canale | Canale secondario |
|---|---|---|
| Ricerca a pagamento - AdWords | Ricerca a pagamento | AdWords |
| Ricerca a pagamento - Bing | Ricerca a pagamento | Bing |
| Ricerca a pagamento - Yahoo | Ricerca a pagamento | Yahoo |

I dati online aggiunti in questo modo saranno intrinsecamente meno granulari dei dati online [!DNL Marketo Measure] traccia tramite JavaScript. Ad esempio, i campi come URL modulo, Pagina di destinazione, Pagina di riferimento e così via non verranno compilati. Pertanto, si consiglia di suddividere le campagne in ogni origine, se possibile. Come mostrato nell’esempio precedente, per ottenere granularità nei rapporti è necessario disporre di più tipi di campagna per ogni origine.

Potrebbe non essere possibile o ragionevole avere il numero di tipi di campagne SFDC per supportare la mappatura granulare dei canali, pertanto puoi ricorrere alla semplice mappatura a livello di canale e ignorare i sottocanali. Se neanche il livello del Canale è noto, è possibile impostare un canale proxy come &quot;Historic Digital&quot; in modo che si sappia almeno che si tratta di un tocco online.

Se hai bisogno di modificare in massa la data del punto di contatto che verrà inviato per questi sforzi storici online, utilizza il [!DNL Marketo Measure] personalizzato &quot;[!UICONTROL Bulk Update Touchpoint Date]&quot; pulsante (disponibile come campo personalizzato nell’oggetto Campaign in SFDC). Se la campagna ha un intervallo di tempo breve, forse varrebbe la pena modificare in massa la data del punto di contatto in un intervallo di giorno per giorno, mentre potrebbe essere utile aggiornare in massa settimanalmente se la campagna ha un intervallo di tempo più lungo. Se sfrutti la funzionalità Aggiorna in blocco data punto di contatto , assicurati di aggiornare la regola di sincronizzazione della campagna per utilizzare la data del punto di contatto dell’acquirente nel campo data. Tieni presente che questo potrebbe richiedere di essere creativo con le regole di sincronizzazione di Campaign se questo si applica solo a una campagna o due e non a tutte.

**Non in linea:**

Anche i dati storici delle attività di marketing offline (quelle che non possono essere tracciate tramite JavaScript) dovranno essere organizzati in campagne SFDC. Le campagne SFDC sono il modo migliore [!DNL Marketo Measure] tiene traccia degli sforzi offline indipendentemente dal fatto che l&#39;attività sia &quot;storica&quot; o &quot;corrente/post-attività[!DNL Marketo Measure] implementazione&quot; quindi segui la stessa mappatura del canale decisa nel corso di formazione originale Configurazione del canale offline.

Se necessario, utilizza il pulsante &quot;Bulk Update Touchpoint Date&quot; per modificare in massa la data del punto di contatto per i membri della campagna. Ad esempio, se crei campagne SFDC dopo il verificarsi dell’evento, desideri eseguire la modifica in massa per la data corretta. Se sfrutti la funzionalità Aggiorna in blocco data punto di contatto , assicurati di aggiornare la regola di sincronizzazione della campagna per utilizzare la data del punto di contatto dell’acquirente nel campo data. Tieni presente che questo potrebbe richiedere di essere creativo con le regole di sincronizzazione di Campaign se questo si applica solo a una campagna o due e non a tutte.

## Sincronizzazione delle campagne storiche in [!DNL Dynamics] {#syncing-historic-campaigns-in-dynamics}

[!DNL Marketo Measure] è in grado di generare in modo retroattivo punti di contatto per le interazioni che si sono verificate in passato, purché siano organizzate in Campagne all’interno di [!DNL Dynamics].

Questo di solito implica il lavoro nel CRM per tenere conto delle date storiche. La gestione sarà diversa anche per gli sforzi online (tracciati da JS) e per gli sforzi offline (non monitorabili da JS).

Segui le istruzioni riportate di seguito per organizzare i dati storici in [!DNL Dynamics] in un formato sincronizzabile con [!DNL Marketo Measure].

**Online:**

I dati digitali storici devono essere organizzati in [!DNL Dynamics] campagne per essere riempite in backfill. Idealmente, questa struttura è già in funzione.

Se i dati sono memorizzati altrove (ad esempio se si vive ancora in Marketing Automation), sarà necessario inserirli in [!DNL Dynamics] e sono organizzate nelle campagne appropriate. A quel punto, dovrai tenere conto della data del punto di contatto in quanto desideri che rifletta la data del passato, non la data in cui l’hai inviato [!DNL Dynamics]. Per ignorare questa data, puoi utilizzare il campo personalizzato &quot;Data punto di contatto dell’acquirente&quot; per modificare la data. È necessario aggiungerlo al modulo elenco marketing.

![](assets/syncing-historical-data-2.png)

Di conseguenza, è possibile impostare in massa la data per tutti gli utenti della lista di marketing che verranno utilizzati per la data del punto di contatto. Per ottenere date storiche più precise, crea più elenchi di marketing per la stessa campagna, ognuno con la propria data punto di contatto. Se la campagna ha un periodo di tempo breve, forse varrebbe la pena creare un elenco di marketing per ogni giorno. Se la campagna ha un intervallo di tempo più lungo, potrebbe essere utile creare una lista di marketing su base settimanale.

Maggiori informazioni sulle liste di marketing sincronizzate sono disponibili qui: [[!DNL Dynamics] Campagne ed elenchi di marketing](/help/marketo-measure-and-dynamics/dynamics-reporting/dynamics-campaigns-and-marketing-lists.md)

>[!NOTE]
>
>Se per qualsiasi motivo hai un’attività online di tracciamento campagna che è attiva oltre la data di pubblicazione JavaScript, assicurati di impostare &quot;[!UICONTROL Touchpoint End Date]&quot; fino alla data in cui il JS è diventato attivo. In questo modo si evita di duplicare i punti di contatto per la stessa interazione.

Considerazioni: I dati online aggiunti in questo modo saranno intrinsecamente meno granulari dei dati online [!DNL Marketo Measure] traccia tramite JavaScript. Ad esempio, campi quali: L’URL del modulo, la pagina di destinazione, la pagina di riferimento, ecc. non verranno compilati. Pertanto, si consiglia di suddividere le campagne in ogni origine, se possibile. Di seguito è riportato un esempio di mappatura ideale.

| Tipo di campagna Dynamics | Canale | Canale secondario |
|---|---|---|
| Ricerca a pagamento - AdWords | Ricerca a pagamento | AdWords |
| Ricerca a pagamento - Bing | Ricerca a pagamento | Bing |
| Ricerca a pagamento - Yahoo | Ricerca a pagamento | Yahoo |

Se non hai un modo di identificare una sorgente o se non vale la pena di tempo e fatica, puoi utilizzare un tipo di campagna mappato su un canale chiamato qualcosa come &quot;legacy digitale&quot; o &quot;sito web storico&quot;.

**Non in linea:**

Per poter disporre di punti di contatto per le attività di marketing offline del passato, i dati devono essere organizzati in [!DNL Dynamics] campagne e sincronizzate con [!DNL Marketo Measure]. Il processo è lo stesso dei canali offline correnti (sincronizzazione della campagna tramite elenchi di marketing o risposte della campagna). Di seguito è riportato un esempio di mappatura dei canali.

| Tipo di campagna Dynamics | Canale | Canale secondario |
|---|---|---|
| Eventi - Conferenze sponsorizzate | Eventi | Conferenze sponsorizzate |
| Eventi - Eventi dei partner | Eventi | Eventi dei partner |
| Eventi - Eventi in hosting | Eventi | Eventi in hosting |
| Webinar - Webinar sui partner | Webinar | Webinar sui partner |

Se questi dati non sono già organizzati in Campagne con le date corrette impostate, puoi utilizzare il campo &quot;Data punto di contatto dell’acquirente&quot; per riflettere la data esatta dell’attività offline passata.

