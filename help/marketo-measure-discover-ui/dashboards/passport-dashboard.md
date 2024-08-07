---
description: Dashboard Passport - [!DNL Marketo Measure] - Prodotto
title: Dashboard Passport
feature: Reporting
exl-id: 0fbd9714-7d9c-4330-b35f-d011e17c3bfe
source-git-commit: 403b31acce25ddc9c1dcafbd53008b6e2868b3df
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Dashboard Passport {#passport-dashboard}

Il dashboard Passport offre agli addetti al marketing una visualizzazione dinamica di lead, contatti e opportunità durante la transizione attraverso varie fasi entro un periodo specificato. Filtrando per una data specifica, gli utenti possono ottenere anche un’istantanea dei record per quel giorno.

**Risposte alle domande della bacheca:**

* Quanti lead, contatti o opportunità esistevano in ogni fase non terminale in un giorno scelto?
* Durante un periodo specificato, quanti lead o contatti distinti sono progrediti in ogni fase transitoria?
   * _Esempio_: se il Lead A si trovava nella fase 1 il 1/1/2023 e fosse avanzato alla fase 5 entro il 3/31/2023, l&#39;analisi Passport Q1 2023 conterà il Lead A nelle fasi da 1 a 5.
* Quante opportunità uniche sono passate attraverso ogni fase transitoria durante un determinato intervallo di tempo?

## Componenti del dashboard {#dashboard-components}

### Opportunità nella fase per nome fase {#opportunities-in-stage-by-stage-name}

* Ogni fase mostra il numero di opportunità con punti di contatto che sono passate attraverso di esse in un determinato arco temporale.
   * Se un’opportunità progredisce attraverso più fasi all’interno dell’intervallo, viene conteggiata in ogni fase che passa.
* Sono escluse le fasi terminali come &quot;Closed Won&quot; e &quot;Closed Lost&quot;.
* Le date di inizio e di fine sono entrambe inclusive.

![](assets/passport-dashboard-1.png)

### Lead o contatti nell&#39;area di visualizzazione per nome area di visualizzazione {#leads-or-contacts-in-stage-by-stage-name}

* Ogni fase mostra il numero di lead o contatti con punti di contatto che li hanno attraversati in un determinato arco temporale.
   * La visualizzazione di &quot;Lead&quot; o &quot;Contatto&quot; è determinata dalla preferenza impostata in: Impostazioni > Impostazioni attribuzione > Oggetto dashboard predefinito.
   * Se un lead o un contatto progredisce attraverso più stadi all&#39;interno di tale estensione, viene conteggiato in ogni stadio che passa.
* Sono escluse le fasi terminali come &quot;Closed Won&quot; e &quot;Closed Lost&quot;.
* Le date di inizio e di fine sono entrambe inclusive.

![](assets/passport-dashboard-2.png)

## Riquadro Filtro {#filter-pane}

Questo cruscotto è dotato delle seguenti impostazioni e filtri:

* Data (basata sulla data di transizione)
* Canale, Sottocanale
* Campaign
* Segmenti

>[!MORELIKETHIS]
>
>* [Nozioni di base sulla dashboard](/help/marketo-measure-discover-ui/dashboards/discover-dashboard-basics.md){target="_blank"}
>* [Criteri di visibilità dei dati del dashboard](/help/marketo-measure-discover-ui/dashboards/dashboard-data-visibility-policy.md){target="_blank"}
