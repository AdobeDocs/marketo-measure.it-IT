---
unique-page-id: 18874684
description: Date di sincronizzazione della campagna - [!DNL Marketo Measure] - Documentazione del prodotto
title: Date di sincronizzazione della campagna
exl-id: 66ce9948-9297-47ef-8b16-0ac45c5664fc
source-git-commit: 65e7f8bc198ceba2f873ded23c94601080ad0546
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Date di sincronizzazione della campagna {#campaign-sync-dates}

Scopri le funzioni della funzione Date di sincronizzazione di Campaign e offre alcuni casi d’uso per questa funzione.

**[!DNL Marketo Measure]Pacchetto richiesto: 6.9 o superiore**

Questa funzione è costituita da due semplici campi data [!DNL Salesforce] Oggetto campagna:

* Data inizio punto di contatto
* Data fine punto di contatto

Una volta abilitati i punti di contatto dell’acquirente in una determinata campagna, le date di sincronizzazione della campagna ti consentono di impostare i parametri della data del punto di contatto sulla singola campagna. Quindi, se devi aggiungere una data di fine punto di contatto del 1° marzo 2017, allora [!DNL Marketo Measure] creerà solo punti di contatto sui membri della campagna che sono stati aggiunti alla campagna prima di tale data. [!DNL Marketo Measure] non crea punti di contatto per i membri della campagna che sono stati aggiunti dopo il 1° marzo 2017.

![](assets/1.gif)

Allo stesso modo, se devi aggiungere una data di inizio punto di contatto su una campagna (ad esempio il 1° gennaio 2017), allora [!DNL Marketo Measure] non creerà punti di contatto sui membri della campagna che sono stati aggiunti alla campagna prima del 1° gennaio 2017. Non è necessario aggiungere una data di inizio punto di contatto se si aggiunge una data di fine punto di contatto e viceversa.

## Casi d’uso {#use-cases}

**Punti di contatto di riempimento posteriori**

In alcuni casi, un team di marketing potrebbe perdere l’aggiunta di parametri utm a una particolare attività di marketing. Le date di sincronizzazione delle campagne ti permetteranno di (se utilizzi campagne SFDC per attività online) recuperare alcuni dati persi. Supponiamo che tu stia eseguendo una campagna e-mail iniziata il 1° maggio, ma il tuo team non ha aggiunto parametri utm a quella campagna e-mail fino al 15 maggio. Se tieni traccia delle conversioni e-mail tramite una campagna SFDC, puoi impostare una data di fine punto di contatto del 15 maggio su tale campagna e abilitare i punti di contatto per i membri &quot;Rispondi&quot; della campagna. Questa azione indica [!DNL Marketo Measure] per creare punti di contatto per tutte le risposte fino al 15 maggio.

**Punti di contatto per l’iscrizione retroattiva alla campagna**

Se sei un nuovo [!DNL Marketo Measure] cliente, potresti essere interessato a inserire alcuni dei dati di marketing che hai monitorato tramite le campagne SFDC. Tuttavia, se desideri abilitare i punti di contatto per le tue campagne SFDC online, puoi affrontare il problema dell’attribuzione del doppio conteggio a partire da [!DNL Marketo Measure] crea automaticamente punti di contatto per le attività di marketing online. Per evitare il doppio conteggio dei dati, puoi utilizzare Date di fine punto di contatto di Campaign per impostare un limite per le date dei punti di contatto create da [!DNL Marketo Measure] sulla campagna SFDC. Ad esempio, se desideri aggiungere conversioni retroattive per una campagna Social hai monitorato in SFDC, ma capisci che hai aggiunto il [!DNL Marketo Measure] JavaScript (che sta creando punti di contatto online) il 1° luglio, puoi modificare la campagna Social SFDC in modo che contenga una data di fine punto di contatto uguale al 1° luglio e abilitare i punti di contatto dell’acquirente per quella campagna.

Possono essere presenti molti altri casi d’uso per le date di fine punto di contatto. Se hai bisogno di aiuto per trovare una situazione specifica, non esitare a contattare [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Università: Campi membri campagna e campagna](https://learn.bizible.com/2-bizible-customization/137720https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63007334d9f0367662b758)
