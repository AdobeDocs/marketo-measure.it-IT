---
description: Scopri la dashboard Coinvolgimento per monitorare i punti di contatto che le persone hanno toccato e il coinvolgimento per canale nel tempo
title: Dashboard di coinvolgimento
feature: Reporting
exl-id: dc8bcbe4-d470-4cd3-a2d9-804fdebe7121
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 0%

---


# Dashboard di coinvolgimento {#engagement-dashboard}

La dashboard di coinvolgimento tiene traccia meticolosamente delle metriche di coinvolgimento degli utenti. Mostra i punti di contatto, il numero di persone impegnate e la media dei punti di contatto per persona. Utilizza il grafico a barre delle serie temporali per una visualizzazione mensile, trimestrale o annuale e il grafico a barre per approfondimenti dettagliati su canale, sottocanale e campagna. Questo strumento è essenziale per comprendere i pattern di coinvolgimento e perfezionare le strategie di coinvolgimento.

Monitoriamo ogni interazione con il cliente come punti di contatto utente (UT), i punti di dati raccolti &quot;grezzi&quot;, che fungono da base per le metriche di coinvolgimento sul nostro dashboard. Non tutte le UT evolvono in punti di contatto dell’acquirente (BT) o in punti di contatto di attribuzione dell’acquirente (BAT), in quanto si tratta di risultati selezionati per attribuire interazioni specifiche dei clienti ad attività correlate ai ricavi. È importante notare che le regole di soppressione non influiscono sulle UT o sul dashboard di coinvolgimento.

* **Punti di contatto utente**: punti di contatto creati da tutti gli impegni.
* **Punti di contatto buyer**: punti di contatto selezionati per l&#39;attribuzione di lead e contatti. Le BT non sono collegate alle opportunità e non hanno ricavi associati.
* **Punti di contatto di attribuzione buyer**: punti di contatto selezionati per l&#39;attribuzione dell&#39;opportunità. Le BAT hanno implicazioni in termini di ricavi in quanto sono collegate alle opportunità.

L’utilizzo di BT o BAT solo per misurare il coinvolgimento sottovaluterebbe la reale portata delle interazioni dei clienti, poiché il coinvolgimento è più ampio della semplice attribuzione.

Risposte alle domande della dashboard:

* Quante persone erano fidanzate? Qual è il numero medio di contatti per persona coinvolta?
* Come si confronta il numero di punti di contatto con le persone toccate all’interno di un canale/sottocanale/campagna specifico?
* Quanti punti di contatto c&#39;erano in un dato canale o sottocanale? Come è cambiata nel tempo?

>[!NOTE]
>Le metriche di coinvolgimento per account e opportunità sono pianificate per il rilascio nella prima metà del 2024.

## Componenti del dashboard {#dashboard-components}

### Riquadri KPI {#kpi-tiles}

* Punti di contatto: numero totale di punti di contatto non elaborati generati.
   * I punti di contatto per l’acquirente e l’attribuzione dell’acquirente sono risultati di attribuzione creati selezionando punti di contatto specifici da attribuire. Non tutti i punti di contatto sono selezionati come BT e BAT.
* Persone toccate: il numero totale di persone che hanno punti di contatto.
* Punti di contatto per persona: numero medio di punti di contatto per persona che è stata toccata.

### Punti di contatto e persone toccate nel tempo {#touchpoints-and-people-touched-over-time}

Il grafico a barre delle serie temporali mostra il numero di punti di contatto, persone toccate e punti di contatto per persona per ogni mese, trimestre e anno.

* utilizzare le funzionalità di espansione e aumento per categorizzare i dati in base a mese, trimestre o anno.
* Passa il cursore del mouse su una barra o su una riga per visualizzare informazioni dettagliate.

Risposte alle domande del grafico:

* Come si è evoluto nel tempo il numero di punti di contatto e Persone toccate?
* Come si confrontano i punti di contatto per persona da un trimestre/mese all’altro?

![Come si confrontano i punti di contatto per persona da un trimestre/mese al](assets/engagement-dashboard-1.png)

### Punti di contatto/Persone toccate dal canale {#touchpoints-people-touched-by-channel}

Grafico a barre che mostra i punti di contatto o le persone toccate segmentati per canale/sottocanale/campagna.

* utilizza le funzionalità drill-down e up per classificare i dati per sottocanale e campagna.
* Passa il puntatore del mouse su ciascuna barra per visualizzare i punti di contatto o le persone toccate.

Risposte alle domande del grafico:

* Quale canale/sottocanale/campagna ha determinato il maggior coinvolgimento?
* Come si confronta il numero di punti di contatto con le persone toccate all’interno di un canale/sottocanale/campagna specifico?

![Come si confronta il numero di punti di contatto con le persone toccate all&#39;interno di un](assets/engagement-dashboard-2.png)

## Riquadro Filtro {#filter-pane}

Questo cruscotto è dotato delle seguenti impostazioni e filtri:

* Data (basata sulla data del punto di contatto)
* Canale, Sottocanale
* Campaign
