---
description: Indicazioni sulla sincronizzazione dei dati storici per gli utenti di Marketo Measure
title: Sincronizzazione dei dati cronologici
exl-id: 5a3c1a71-463a-4d75-98b9-fc225839512a
feature: Channels
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 1%

---

# Sincronizzazione dei dati cronologici {#syncing-historical-data}

[!DNL Marketo Measure] è una soluzione che fornisce i dati più granulari e actionable. Tuttavia, è possibile che tu disponga di dati esistenti di cui desideri l’attribuzione. È possibile generare punti di contatto per i dati storici, ma è importante prendere in considerazione alcuni fattori prima di procedere con questo processo.

>[!NOTE]
>
>Questo articolo riguarda un processo obsoleto. Invitiamo gli utenti a utilizzare il [nuovo processo in-app migliorato](/help/channel-tracking-and-setup/custom-campaign-sync.md){target="_blank"}.

## Fattori da considerare {#factors-to-consider}

**I dati sono già organizzati in campagne?**

a. Per poter generare i punti di contatto, i dati devono essere organizzati in campagne da sincronizzare con [!DNL Marketo Measure]. Se al momento non è organizzato in Campagne, dovrai valutare se vale la pena dedicare tempo e risorse per segmentare i dati nelle campagne appropriate.

b. La data in cui il membro è stato aggiunto alla campagna o contrassegnato come risposta verrà utilizzata per la data del punto di contatto, quindi anche questo deve essere accurato. [!DNL Marketo Measure] offre soluzioni alternative sia in SFDC che in MSD per aggiornare le date, ma potrebbe richiedere tempo a seconda del volume.

**La quantità di dati organizzati in campagne è abbastanza uguale per tutti i canali (ricerca a pagamento, eventi, organica, ecc.)?**

È importante avere un quadro equilibrato dell’attribuzione al fine di ottenere rapporti accurati e &quot;corretti&quot;. Ad esempio, se disponi solo di dati per attività di canale offline storiche come Eventi, i dati saranno intrinsecamente distorti senza dati online storici a complemento di essi.

**Quale livello di granularità ti aspetti?**

In sostanza conoscerai solo il nome del canale, del sottocanale e della campagna.

**Quali sono i tuoi obiettivi di reporting in futuro?**

Poiché questi dati saranno limitati, è importante considerare il modo in cui intendi utilizzarli. Potrebbe non avere senso confrontare i dati storici con quelli futuri.

**Quanto indietro vuoi andare?**

[!DNL Marketo Measure] consiglia vivamente di non superare l&#39;anno precedente.

Questo è un argomento di cui si consiglia vivamente di discutere con il contatto [!DNL Marketo Measure]. Se si considera quanto sopra e si desidera procedere, di seguito sono riportate le istruzioni generali (separate per [!DNL Salesforce] e [!DNL Microsoft Dynamics]).

## Sincronizzazione delle campagne cronologiche in [!DNL Salesforce] {#syncing-historic-campaigns-in-salesforce}

**In linea:**

Per sincronizzare i dati cronologici online, i dati devono essere organizzati in campagne Salesforce da sincronizzare con [!DNL Marketo Measure] tramite [!DNL Salesforce] regole di sincronizzazione campagne nell&#39;app [!DNL Marketo Measure]. È importante assicurarsi che i punti di contatto non vengano generati da nessuna di queste campagne dopo la data di pubblicazione del JavaScript. Questo per evitare di duplicare il punto di contatto. Una volta che JavaScript è attivo, le attività online vengono tracciate automaticamente, quindi non vogliamo tracciarle anche tramite una campagna SFDC. Per evitare questo problema, assicurati di aggiungere un senso del tempo alla regola. Ad esempio, &quot;Data di creazione del membro della campagna è inferiore a [Data di pubblicazione di JavaScript]&quot;.

![Per sincronizzare i dati cronologici in linea, è necessario organizzare i dati in Salesforce](assets/dynamics-lists-1.png)

Il componente di mappatura del canale per i dati online storici può essere un po’ complicato. Vogliamo che corrisponda il più possibile alle tue regole del canale online correnti (dalla scheda delle regole online) per un reporting pulito. Di seguito è riportato un esempio di mappatura del canale ideale.

>[!NOTE]
>
>Questa mappatura dei canali viene eseguita nella sezione [!UICONTROL Offline Channels] dell&#39;app [!DNL Marketo Measure] poiché si utilizzano campagne SFDC.

| Tipo di campagna Salesforce | Channel | Sottocanale |
|---|---|---|
| Ricerca a pagamento - AdWords | Ricerca pagata | AdWords |
| Ricerca a pagamento - Bing | Ricerca pagata | Bing |
| Ricerca a pagamento - Yahoo | Ricerca pagata | Yahoo |

I dati online aggiunti in questo modo saranno intrinsecamente meno granulari dei dati online [!DNL Marketo Measure] rilevati tramite JavaScript. Ad esempio, i campi come URL modulo, pagina di destinazione, pagina di riferimento e così via non verranno compilati. Pertanto, se possibile, si consiglia di suddividere le campagne in ogni origine. Come mostrato nell’esempio precedente, per avere granularità nel reporting è necessario disporre di più tipi di campagna per ogni origine.

Potrebbe non essere possibile o ragionevole disporre del numero di tipi di campagna SFDC per supportare la mappatura granulare dei canali, pertanto puoi ricorrere solo alla mappatura a livello di canale ignorando i sottocanali. Se anche il livello del canale non è noto, puoi impostare un canale proxy come &quot;Historic Digital&quot; in modo da sapere se era un contatto online.

Se devi modificare in massa la data del punto di contatto che verrà inviata per queste attività online storiche, utilizza il pulsante &quot;[!DNL Marketo Measure]&quot; personalizzato [!UICONTROL Bulk Update Touchpoint Date] (disponibile come campo personalizzato nell&#39;oggetto Campaign in SFDC). Se la campagna ha un breve intervallo di tempo, forse sarebbe utile modificare in massa la data del punto di contatto in un intervallo giorno per giorno, mentre potrebbe essere utile aggiornare in massa su base settimanale se la campagna ha un intervallo di tempo più lungo. Se utilizzi la funzionalità Bulk Update Touchpoint Date (Data punto di contatto per aggiornamento in blocco), assicurati di aggiornare la regola di sincronizzazione delle campagne per utilizzare la data Buyer Touchpoint nel campo data. Tieni presente che potrebbe essere necessario diventare creativi con le regole di sincronizzazione delle campagne se questo si applica solo a una o due campagne e non a tutte.

**Non in linea:**

Anche i dati storici delle attività di marketing offline (che non possono essere tracciati tramite JavaScript) dovranno essere organizzati in campagne SFDC. Le campagne SFDC sono il modo in cui [!DNL Marketo Measure] tiene traccia delle attività offline indipendentemente dal fatto che l&#39;attività sia &quot;storica&quot; o &quot;implementazione corrente/post[!DNL Marketo Measure]&quot;. Pertanto, segui la stessa mappatura del canale decisa nel corso di formazione originale sulla configurazione del canale offline.

Se necessario, utilizza il pulsante &quot;Bulk Update Touchpoint Date&quot; (Aggiorna data punto di contatto in blocco) per modificare in massa la data del punto di contatto per i membri della campagna. Ad esempio, se crei campagne SFDC dopo che si è verificato l’evento, puoi effettuare modifiche di massa per la data corretta. Se utilizzi la funzionalità Bulk Update Touchpoint Date (Data punto di contatto per aggiornamento in blocco), assicurati di aggiornare la regola di sincronizzazione delle campagne per utilizzare la data Buyer Touchpoint nel campo data. Tieni presente che potrebbe essere necessario diventare creativi con le regole di sincronizzazione delle campagne se questo si applica solo a una o due campagne e non a tutte.

## Sincronizzazione delle campagne cronologiche in [!DNL Dynamics] {#syncing-historic-campaigns-in-dynamics}

[!DNL Marketo Measure] è in grado di generare retroattivamente punti di contatto per le interazioni che si sono verificate in passato, purché organizzate in campagne all&#39;interno di [!DNL Dynamics].

Questo di solito comporta il lavoro nel CRM per tenere conto delle date storiche. La gestione sarà diversa anche per le attività online (tracciate da JS) e offline (non possono essere tracciate da JS).

Seguire le istruzioni riportate di seguito per organizzare i dati storici in [!DNL Dynamics] in un formato che può essere sincronizzato in [!DNL Marketo Measure].

**In linea:**

I dati digitali cronologici devono essere organizzati in [!DNL Dynamics] campagne per essere recuperati. Idealmente, questa struttura è già al suo posto.

Se i dati sono ospitati altrove (ad esempio, vivono ancora in Marketing Automation), dovranno essere inviati in [!DNL Dynamics] e organizzati nelle campagne appropriate. Sarà quindi necessario tenere conto della data del punto di contatto in quanto si desidera che rifletta la data del passato, non la data in cui è stato inviato in [!DNL Dynamics]. Per ignorare questa data, puoi utilizzare il campo personalizzato &quot;Data Buyer Touchpoint&quot; per modificare la data. Dovrai aggiungerlo al modulo Elenco di marketing.

![Se i dati sono memorizzati altrove (ad esempio se si trova ancora nel reparto Marketing](assets/dynamics-lists-10.png)

Di conseguenza, puoi impostare in massa la data per tutti gli utenti dell’elenco di marketing che verrà utilizzata per la data del punto di contatto. Per ottenere date storiche più precise, crea più elenchi di marketing per la stessa campagna, ciascuno con la propria data di punto di contatto. Se la campagna ha un periodo di tempo breve, forse sarebbe utile creare un elenco di marketing per ogni giorno. Se la campagna ha un periodo di tempo più lungo, potrebbe essere utile creare un elenco di marketing su base settimanale.

Ulteriori informazioni sulla sincronizzazione degli elenchi marketing sono disponibili qui: [[!DNL Dynamics] Campagne ed elenchi marketing](/help/channel-tracking-and-setup/dynamics-campaigns-and-marketing-lists.md)

>[!NOTE]
>
>Se per qualsiasi motivo disponi di un&#39;attività online di tracciamento delle campagne attiva oltre la data di JavaScript Live, assicurati di impostare il campo &quot;[!UICONTROL Touchpoint End Date]&quot; sulla data di attivazione di JS. In questo modo si evita di avere punti di contatto duplicati per la stessa interazione.

Considerazioni: i dati online aggiunti in questo modo saranno intrinsecamente meno granulari rispetto ai dati online [!DNL Marketo Measure] rilevati tramite JavaScript. Ad esempio, i campi come: URL modulo, pagina di destinazione, pagina di riferimento e così via non verranno compilati. Pertanto, se possibile, si consiglia di suddividere le campagne in ogni origine. Di seguito è riportato un esempio di mappatura ideale.

| Tipo di campagna Dynamics | Channel | Sottocanale |
|---|---|---|
| Ricerca a pagamento - AdWords | Ricerca pagata | AdWords |
| Ricerca a pagamento - Bing | Ricerca pagata | Bing |
| Ricerca a pagamento - Yahoo | Ricerca pagata | Yahoo |

Se non disponi di un modo per identificare una sorgente o se non ne vale la pena dedicare tempo e fatica, puoi utilizzare un tipo di campagna mappato su un canale denominato ad esempio &quot;Legacy Digital&quot; (Digitale legacy) o &quot;Historic Website&quot; (Sito web storico).

**Non in linea:**

Per avere punti di contatto per le attività di marketing offline passate, i dati devono essere organizzati in [!DNL Dynamics] campagne e sincronizzati in [!DNL Marketo Measure]. Il processo è lo stesso dei canali offline correnti (sincronizza la campagna tramite elenchi di marketing o risposte alle campagne). Di seguito è riportato un esempio di mappatura dei canali.

| Tipo di campagna Dynamics | Channel | Sottocanale |
|---|---|---|
| Eventi - Conferenze sponsorizzate | Eventi | Conferenze sponsorizzate |
| Eventi - Eventi partner | Eventi | Eventi partner |
| Eventi - Eventi in hosting | Eventi | Eventi ospitati |
| Webinar - Webinar per i partner | Webinar | Webinar per i partner |

Se questi dati non sono già organizzati in campagne con le date corrette impostate, puoi utilizzare il campo &quot;Data Buyer Touchpoint&quot; per riflettere la data precisa dell’attività offline nel passato.

