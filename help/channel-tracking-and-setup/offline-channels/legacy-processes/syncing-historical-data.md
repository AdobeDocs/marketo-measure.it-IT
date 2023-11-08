---
unique-page-id: 42762310
description: Sincronizzazione dei dati storici - [!DNL Marketo Measure] - Documentazione del prodotto
title: Sincronizzazione dei dati cronologici
exl-id: 5a3c1a71-463a-4d75-98b9-fc225839512a
feature: Channels
source-git-commit: b8ea008c594ed114323dedd3762d1265287193c7
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 0%

---

# Sincronizzazione dei dati cronologici {#syncing-historical-data}

[!DNL Marketo Measure] è una soluzione che fornisce i dati più granulari e actionable. Tuttavia, è possibile che tu disponga di dati esistenti di cui desideri l’attribuzione. È possibile generare punti di contatto per i dati storici, ma è importante prendere in considerazione alcuni fattori prima di procedere con questo processo.

>[!NOTE]
>
>Questo articolo riguarda un processo obsoleto. Invitiamo gli utenti a utilizzare [processo in-app nuovo e migliorato](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

## Fattori da considerare {#factors-to-consider}

**I dati sono già organizzati in campagne?**

a. I dati devono essere organizzati in Campagne da sincronizzare con [!DNL Marketo Measure] per generare i punti di contatto. Se non è attualmente organizzato in Campagne, puoi valutare se vale la pena dedicare tempo e risorse per segmentare i dati nelle campagne appropriate.

b. La data in cui il membro è stato aggiunto alla campagna o contrassegnato come risposta verrà utilizzata per la data del punto di contatto, quindi anche questo deve essere accurato. [!DNL Marketo Measure] offre soluzioni alternative sia in SFDC che in MSD per aggiornare le date, ma potrebbe richiedere tempo a seconda del volume.

**Disponi di una quantità abbastanza uguale di dati organizzati in campagne per tutti i canali (ricerca a pagamento, eventi, organica, ecc.)?**

È importante avere un quadro equilibrato dell’attribuzione al fine di ottenere rapporti accurati e &quot;corretti&quot;. Ad esempio, se disponi solo di dati per attività di canale offline storiche come Eventi, i dati saranno intrinsecamente distorti senza dati online storici a complemento di essi.

**Quale livello di granularità ti aspetti?**

In sostanza conoscerai solo il nome del canale, del sottocanale e della campagna.

**Quali sono i tuoi obiettivi di reporting in futuro?**

Poiché questi dati saranno limitati, è importante considerare il modo in cui intendi utilizzarli. Potrebbe non avere senso confrontare i dati storici con quelli futuri.

**Quanto indietro vuoi andare?**

[!DNL Marketo Measure] raccomanda vivamente di non superare l&#39;anno precedente.

Questo è un argomento di cui si consiglia vivamente di discutere con il proprio [!DNL Marketo Measure] contatta prima. Se si è considerato quanto sopra e si desidera procedere, istruzioni generali (separate per [!DNL Salesforce] e [!DNL Microsoft Dynamics]) sono riportati di seguito.

## Sincronizzazione delle campagne storiche in [!DNL Salesforce] {#syncing-historic-campaigns-in-salesforce}

**Online:**

Per sincronizzare i dati storici online, i dati devono essere organizzati in campagne Salesforce a cui eseguire la sincronizzazione [!DNL Marketo Measure] tramite [!DNL Salesforce] Regole di sincronizzazione delle campagne in [!DNL Marketo Measure] app. È importante assicurarsi che i punti di contatto non vengano generati da nessuna di queste campagne dopo la data di pubblicazione del codice JavaScript. Questo per evitare di duplicare il punto di contatto. Una volta che JavaScript è attivo, le attività online vengono tracciate automaticamente, quindi non vogliamo tracciarle anche tramite una campagna SFDC. Per evitare questo problema, assicurati di aggiungere un senso del tempo alla regola. Ad esempio, &quot;La data di creazione del membro della campagna è inferiore a [Data di pubblicazione JavaScript]&quot;.

![](assets/syncing-historical-data-1.png)

Il componente di mappatura del canale per i dati online storici può essere un po’ complicato. Vogliamo che corrisponda il più possibile alle tue regole del canale online correnti (dalla scheda delle regole online) per un reporting pulito. Di seguito è riportato un esempio di mappatura del canale ideale.

>[!NOTE]
>
>Questa mappatura dei canali viene eseguita in [!UICONTROL Offline Channels] sezione del [!DNL Marketo Measure] poiché stiamo utilizzando campagne SFDC.

| Tipo di campagna Salesforce | Canale | Sottocanale |
|---|---|---|
| Ricerca a pagamento - AdWords | Ricerca a pagamento | AdWords |
| Ricerca a pagamento - Bing | Ricerca a pagamento | Bing |
| Ricerca a pagamento - Yahoo | Ricerca a pagamento | Yahoo |

I dati online aggiunti in questo modo saranno intrinsecamente meno granulari dei dati online [!DNL Marketo Measure] tracce tramite JavaScript. Ad esempio, i campi come URL modulo, pagina di destinazione, pagina di riferimento e così via non verranno compilati. Pertanto, se possibile, si consiglia di suddividere le campagne in ogni origine. Come mostrato nell’esempio precedente, per avere granularità nel reporting è necessario disporre di più tipi di campagna per ogni origine.

Potrebbe non essere possibile o ragionevole disporre del numero di tipi di campagna SFDC per supportare la mappatura granulare dei canali, pertanto puoi ricorrere solo alla mappatura a livello di canale ignorando i sottocanali. Se anche il livello del canale non è noto, puoi impostare un canale proxy come &quot;Historic Digital&quot; in modo da sapere se era un contatto online.

Se devi modificare in massa la data del punto di contatto che verrà inviata per queste attività online storiche, utilizza [!DNL Marketo Measure] personalizzato &quot;[!UICONTROL Bulk Update Touchpoint Date]Pulsante &quot; (disponibile come campo personalizzato nell’oggetto Campaign in SFDC). Se la campagna ha un breve intervallo di tempo, forse sarebbe utile modificare in massa la data del punto di contatto in un intervallo giorno per giorno, mentre potrebbe essere utile aggiornare in massa su base settimanale se la campagna ha un intervallo di tempo più lungo. Se utilizzi la funzionalità Bulk Update Touchpoint Date (Data punto di contatto aggiornamento in blocco), assicurati di aggiornare la regola di sincronizzazione della campagna per utilizzare la data del punto di contatto acquirente nel campo data. Tieni presente che potrebbe essere necessario diventare creativi con le regole di sincronizzazione delle campagne se questo si applica solo a una o due campagne e non a tutte.

**Non in linea:**

Anche i dati storici delle attività di marketing offline (che non possono essere tracciati tramite JavaScript) dovranno essere organizzati in campagne SFDC. Le campagne SFDC sono il modo [!DNL Marketo Measure] tiene traccia delle attività offline indipendentemente dal fatto che l’attività sia &quot;storica&quot; o &quot;corrente/post-elaborazione&quot;[!DNL Marketo Measure] implementazione&quot;, quindi segui la stessa mappatura del canale decisa nel corso di formazione originale sulla configurazione del canale offline.

Se necessario, utilizza il pulsante &quot;Bulk Update Touchpoint Date&quot; (Aggiorna data punto di contatto in blocco) per modificare in massa la data del punto di contatto per i membri della campagna. Ad esempio, se crei campagne SFDC dopo che si è verificato l’evento, esegui una modifica di massa per la data corretta. Se utilizzi la funzionalità Bulk Update Touchpoint Date (Data punto di contatto aggiornamento in blocco), assicurati di aggiornare la regola di sincronizzazione della campagna per utilizzare la data del punto di contatto acquirente nel campo data. Tieni presente che potrebbe essere necessario diventare creativi con le regole di sincronizzazione delle campagne se questo si applica solo a una o due campagne e non a tutte.

## Sincronizzazione delle campagne storiche in [!DNL Dynamics] {#syncing-historic-campaigns-in-dynamics}

[!DNL Marketo Measure] è in grado di generare retroattivamente punti di contatto per le interazioni che si sono verificate in passato, purché siano organizzate in Campagne all’interno di [!DNL Dynamics].

Questo di solito comporta il lavoro nel CRM per tenere conto delle date storiche. La gestione sarà diversa anche per le attività online (tracciate da JS) e offline (non possono essere tracciate da JS).

Segui le istruzioni riportate di seguito per organizzare i dati storici in [!DNL Dynamics] in un formato che può essere sincronizzato con [!DNL Marketo Measure].

**Online:**

I dati digitali storici devono essere organizzati in [!DNL Dynamics] campagne per essere compilate. Idealmente, questa struttura è già al suo posto.

Se i dati sono memorizzati altrove (ad esempio se risiedono ancora in Marketing Automation), sarà necessario inviarli a [!DNL Dynamics] e organizzate nelle campagne appropriate. Quindi dovrai tenere conto della data del punto di contatto in quanto desideri che rifletta la data del passato, non la data in cui l’hai inserito [!DNL Dynamics]. Per sostituire questa data, puoi utilizzare il campo personalizzato &quot;Data punto di contatto acquirente&quot; per modificare la data. Dovrai aggiungerlo al modulo Elenco di marketing.

![](assets/syncing-historical-data-2.png)

Di conseguenza, puoi impostare in massa la data per tutti gli utenti dell’elenco di marketing che verrà utilizzata per la data del punto di contatto. Per ottenere date storiche più precise, crea più elenchi di marketing per la stessa campagna, ciascuno con la propria data di punto di contatto. Se la campagna ha un periodo di tempo breve, forse sarebbe utile creare un elenco di marketing per ogni giorno. Se la campagna ha un periodo di tempo più lungo, potrebbe essere utile creare un elenco di marketing su base settimanale.

Ulteriori informazioni sulla sincronizzazione degli elenchi di marketing sono disponibili qui: [[!DNL Dynamics] Campagne ed elenchi di marketing](/help/channel-tracking-and-setup/offline-channels/legacy-processes/dynamics-campaigns-and-marketing-lists.md)

>[!NOTE]
>
>Se per qualsiasi motivo disponi di un’attività online di tracciamento delle campagne attiva oltre la data live JavaScript, assicurati di impostare la &quot;[!UICONTROL Touchpoint End Date]&quot; alla data di pubblicazione di JS. In questo modo si evita di avere punti di contatto duplicati per la stessa interazione.

Considerazioni: i dati online aggiunti in questo modo saranno intrinsecamente meno granulari rispetto ai dati online [!DNL Marketo Measure] tracce tramite JavaScript. Ad esempio, i campi come: URL modulo, pagina di destinazione, pagina di riferimento e così via non verranno compilati. Pertanto, se possibile, si consiglia di suddividere le campagne in ogni origine. Di seguito è riportato un esempio di mappatura ideale.

| Tipo di campagna Dynamics | Canale | Sottocanale |
|---|---|---|
| Ricerca a pagamento - AdWords | Ricerca a pagamento | AdWords |
| Ricerca a pagamento - Bing | Ricerca a pagamento | Bing |
| Ricerca a pagamento - Yahoo | Ricerca a pagamento | Yahoo |

Se non disponi di un modo per identificare una sorgente o se non ne vale la pena dedicare tempo e fatica, puoi utilizzare un tipo di campagna mappato su un canale denominato ad esempio &quot;Legacy Digital&quot; (Digitale legacy) o &quot;Historic Website&quot; (Sito web storico).

**Non in linea:**

Per avere punti di contatto per le attività di marketing offline del passato, i dati devono essere organizzati in [!DNL Dynamics] campagne e sincronizzati in [!DNL Marketo Measure]. Il processo è lo stesso dei canali offline correnti (sincronizza la campagna tramite elenchi di marketing o risposte alle campagne). Di seguito è riportato un esempio di mappatura dei canali.

| Tipo di campagna Dynamics | Canale | Sottocanale |
|---|---|---|
| Eventi - Conferenze sponsorizzate | Eventi | Conferenze sponsorizzate |
| Eventi - Eventi partner | Eventi | Eventi partner |
| Eventi - Eventi in hosting | Eventi | Eventi ospitati |
| Webinar - Webinar per i partner | Webinar | Webinar per i partner |

Se questi dati non sono già organizzati in campagne con le date corrette impostate, puoi utilizzare il campo &quot;Data punto di contatto acquirente&quot; per riflettere la data precisa dell’attività offline nel passato.

