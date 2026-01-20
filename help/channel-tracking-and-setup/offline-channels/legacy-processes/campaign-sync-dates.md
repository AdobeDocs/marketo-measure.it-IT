---
unique-page-id: 18874684
description: Date di sincronizzazione campagna - [!DNL Marketo Measure]
title: Date di sincronizzazione della campagna
exl-id: 66ce9948-9297-47ef-8b16-0ac45c5664fc
feature: Channels
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Date di sincronizzazione della campagna {#campaign-sync-dates}

Scopri le funzionalità della funzione Campaign Sync Dates e offre alcuni casi d’uso per questa funzione.

>[!NOTE]
>
>Questo articolo riguarda un processo obsoleto. Invitiamo gli utenti a utilizzare il [nuovo processo in-app migliorato](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

Pacchetto **[!DNL Marketo Measure]richiesto: 6.9 o versione successiva**

Questa funzione è costituita da due semplici campi data sull&#39;oggetto campagna [!DNL Salesforce]:

* Data di inizio punto di contatto
* Data di fine punto di contatto

Una volta abilitati i punti di contatto dell’acquirente in una determinata campagna, le date di sincronizzazione della campagna ti consentiranno di impostare i parametri della data del punto di contatto nella singola campagna. Pertanto, se aggiungi un punto di contatto con data di fine 1 marzo 2017, [!DNL Marketo Measure] creerà solo punti di contatto sui membri della campagna aggiunti alla campagna prima di tale data. [!DNL Marketo Measure] non creerà punti di contatto per i membri della campagna aggiunti dopo il 1° marzo 2017.

![](assets/1.gif)

Analogamente, se si aggiunge una data di inizio punto di contatto in una campagna (ad esempio, 1° gennaio 2017), [!DNL Marketo Measure] non creerà punti di contatto sui membri della campagna aggiunti alla campagna prima del 1° gennaio 2017. Non è necessario aggiungere una data di inizio punto di contatto se si aggiunge una data di fine punto di contatto e viceversa.

## Casi d’uso {#use-cases}

**Punti di contatto precompilati**

In alcuni casi, un team di marketing potrebbe non riuscire ad aggiungere parametri utm a una particolare attività di marketing. Le date di sincronizzazione delle campagne ti consentiranno di (se utilizzi le campagne SFDC per le attività online) eseguire il backfill di alcuni dati mancanti. Supponiamo che tu stia eseguendo una campagna e-mail avviata il 1° maggio, ma il tuo team non ha aggiunto parametri utm alla campagna e-mail fino al 15 maggio. Se tieni traccia delle conversioni e-mail tramite una campagna SFDC, potrai impostare per tale campagna una Data di fine punto di contatto il 15 maggio e abilitare i punti di contatto per i membri &quot;con risposta&quot; della campagna. Questa azione indicherà a [!DNL Marketo Measure] di creare punti di contatto per tutte le risposte fino al 15 maggio.

**Punti Di Contatto Di Iscrizione Retroattiva Alla Campagna**

Se sei un nuovo cliente di [!DNL Marketo Measure], potresti essere interessato a portare alcuni dei dati di marketing tracciati tramite SFDC Campaigns. Tuttavia, se devi abilitare i punti di contatto per le campagne SFDC online, potresti riscontrare il problema del doppio conteggio dell&#39;attribuzione, poiché [!DNL Marketo Measure] sta creando automaticamente punti di contatto per le tue attività di marketing online. Per evitare il doppio conteggio dei dati, puoi utilizzare le date di fine del punto di contatto della campagna per impostare un limite per le date di punto di contatto create da [!DNL Marketo Measure] nella campagna SFDC. Ad esempio, se desideri aggiungere conversioni retroattive per una campagna social di cui hai eseguito il tracciamento in SFDC, ma sai di aver aggiunto il JavaScript [!DNL Marketo Measure] (che sta creando punti di contatto online) il 1° luglio, puoi modificare la campagna social SFDC in modo che contenga una data di fine punto di contatto uguale al 1° luglio e abilitare i punti di contatto acquirenti per tale campagna.

Ci possono essere molti altri casi d’uso per le Date di fine del punto di contatto. Se hai bisogno di aiuto per risolvere una situazione specifica, non esitare a contattare il [supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
