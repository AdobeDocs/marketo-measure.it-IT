---
unique-page-id: 18874684
description: Date di sincronizzazione campagna - [!DNL Marketo Measure] - Documentazione del prodotto
title: Date di sincronizzazione della campagna
exl-id: 66ce9948-9297-47ef-8b16-0ac45c5664fc
feature: Channels
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Date di sincronizzazione della campagna {#campaign-sync-dates}

Scopri le funzionalità della funzione Campaign Sync Dates e offre alcuni casi d’uso per questa funzione.

**[!DNL Marketo Measure]Pacchetto richiesto: 6.9 o superiore**

Questa funzione è costituita da due semplici campi data sul [!DNL Salesforce] Oggetto campagna:

* Data di inizio punto di contatto
* Data di fine punto di contatto

Una volta abilitati i punti di contatto dell’acquirente in una determinata campagna, le date di sincronizzazione della campagna ti consentiranno di impostare i parametri della data del punto di contatto nella singola campagna. Quindi, se dovessi aggiungere una data di fine punto di contatto il 1° marzo 2017, [!DNL Marketo Measure] crea punti di contatto solo per i membri della campagna che sono stati aggiunti alla campagna prima di tale data. [!DNL Marketo Measure] non creerà punti di contatto per i membri della campagna aggiunti dopo il 1° marzo 2017.

![](assets/1.gif)

Analogamente, se si desidera aggiungere una data di inizio punto di contatto in una campagna (ad esempio, 1° gennaio 2017), [!DNL Marketo Measure] non crea punti di contatto sui membri della campagna aggiunti alla campagna prima del 1° gennaio 2017. Non è necessario aggiungere una data di inizio punto di contatto se si aggiunge una data di fine punto di contatto e viceversa.

## Casi d’uso {#use-cases}

**Punti di contatto di riempimento**

In alcuni casi, un team di marketing potrebbe non riuscire ad aggiungere parametri utm a una particolare attività di marketing. Le date di sincronizzazione delle campagne consentono di (se utilizzi le campagne SFDC per le attività online) eseguire il backfill di alcuni dati mancanti. Supponiamo che tu stia eseguendo una campagna e-mail avviata il 1° maggio, ma il tuo team non ha aggiunto parametri utm alla campagna e-mail fino al 15 maggio. Se tieni traccia delle conversioni e-mail tramite una campagna SFDC, potrai impostare per tale campagna una Data di fine punto di contatto del 15 maggio e abilitare i punti di contatto per i membri &quot;con risposta&quot; della campagna. Questa azione ti dirà [!DNL Marketo Measure] creare punti di contatto per tutte queste risposte fino al 15 maggio.

**Punti di contatto di iscrizione retroattiva alla campagna**

Se sei un nuovo [!DNL Marketo Measure] cliente, potresti essere interessato a portare alcuni dei dati di marketing tracciati tramite le campagne SFDC. Tuttavia, se abiliti i punti di contatto per le campagne SFDC online, potresti riscontrare il problema del doppio conteggio dell’attribuzione da [!DNL Marketo Measure] crea automaticamente punti di contatto per le attività di marketing online. Per evitare il doppio conteggio dei dati, puoi utilizzare le Date di fine del punto di contatto di Campaign per impostare un limite per le date di punto di contatto create da [!DNL Marketo Measure] sulla campagna SFDC. Ad esempio, se desideri aggiungere conversioni retroattive per una campagna social network di cui hai eseguito il tracciamento in SFDC, ma sai di aver aggiunto il [!DNL Marketo Measure] JavaScript (che sta creando punti di contatto online) il 1° luglio, quindi puoi modificare la campagna SFDC per social network in modo che contenga una data di fine punto di contatto uguale al 1° luglio e abilitare i punti di contatto dell’acquirente per tale campagna.

Ci possono essere molti altri casi d’uso per le Date di fine del punto di contatto. Se hai bisogno di aiuto per capire una situazione specifica, non esitare a contattare [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Università: Campi membri della campagna](https://learn.bizible.com/2-bizible-customization/137720https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63007334d9f0367662b758)
