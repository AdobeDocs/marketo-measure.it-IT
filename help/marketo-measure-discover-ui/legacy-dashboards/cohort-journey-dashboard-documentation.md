---
unique-page-id: 42762648
description: Documentazione del dashboard per Percorso coorte - [!DNL Marketo Measure]
title: Documentazione del dashboard per Percorso coorte
exl-id: b139f720-86ae-4f6d-9dfc-cc67b4186f88
feature: Reporting
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Documentazione del dashboard per Percorso coorte {#cohort-journey-dashboard-documentation}

I dashboard Impatto coorte e Funnel consentono agli addetti al marketing di visualizzare la progressione da una fase di coorte iniziale per un intervallo di tempo selezionato e di misurare il tasso di conversione.

La differenza principale sta nel modo in cui contiamo ogni entità dalla fase della coorte.

* Funnel coorte: il risultato di ogni fase è derivato direttamente dalla fase precedente.

   * Vengono conteggiati solo i record che sono passati attraverso ogni fase nel funnel dopo l’ora di inizio della coorte impostata.

![](assets/cohort-journey-dashboard-documentation-1.png)

* Impatto sulla coorte: il risultato di ogni fase è derivato dalla fase della coorte e non dalla fase precedente.

   * Tutti i record in ogni fase vengono conteggiati a condizione che si verifichino dopo l’ora di inizio della coorte impostata. Questo dashboard avrà naturalmente più record rispetto al dashboard Funnel poiché stiamo osservando come le entità sono state influenzate dalla fase della coorte, non solo il movimento attraverso il funnel.

![](assets/cohort-journey-dashboard-documentation-2.png)

Ogni dashboard ha due sezioni:

* Entrate coorte: l’importo totale delle opportunità da tutte le opportunità nella fase Offerte del riquadro Percorso coorte.
* Percorso di coorte: progressione a ogni fase del percorso dalla fase iniziale della coorte per un intervallo di tempo selezionato.

>[!NOTE]
>
>In tutti i dashboard di individuazione è possibile segnalare un solo oggetto persona, lead o contatto. Questo è impostato in [!UICONTROL Settings] > [!UICONTROL Reporting] > [!UICONTROL Attribution Settings] > [!UICONTROL Default Dashboard Object].

Le dashboard supportano i seguenti filtri:

* Cohort Stage (Fase coorte): seleziona la fase iniziale della coorte. I record in tutte le fasi successive vengono sviluppati dai record nella fase coorte.
* Intervallo date coorte: seleziona l’intervallo di tempo per la fase della coorte selezionata. Insieme a Cohort Stage, definisce il set di dati iniziale.
* Data limite: selezionare la data entro la quale deve verificarsi la progressione del record in tutte le fasi successive. Il valore predefinito è oggi. Tieni presente che questo vale per tutte le fasi diverse dalla fase della coorte.
* Canale: filtra i record in base ai canali. Un record è associato a un canale se uno qualsiasi dei suoi punti di contatto è associato al canale.
* Sottocanale: filtra i record per sottocanali. Un record è associato a un sottocanale se uno qualsiasi dei suoi punti di contatto è associato al sottocanale.
* Campagna: filtra i record per campagne. Un record è associato a una campagna se uno qualsiasi dei suoi punti di contatto è associato alla campagna.
* Origine campagna: filtra i record per origini campagna. Le origini della campagna di esempio sono [!DNL Adwords], [!DNL BingAds], [!DNL Facebook], [!DNL LinkedIn], ecc. Un record è associato a un’origine della campagna se uno qualsiasi dei suoi punti di contatto è associato all’origine della campagna.
* Filtri di segmenti: filtra i record per segmenti personalizzati. Un record è associato a un segmento se uno qualsiasi dei suoi punti di contatto è associato al segmento.

In tutti i filtri, viene utilizzata la logica &quot;AND&quot;.

>[!NOTE]
>
>I filtri di segmento si applicano solo allo stadio LC e dopo. Se lo stadio della coorte è Sconosciuto o Noto e uno dei filtri dei segmenti ha un valore, il dashboard non restituisce alcun risultato.

Gli stadi includono Unknown, Known, LC, gli stadi funnel selezionati in stadi lead/contatto aperti (Impostazioni > CRM > Mappatura stadio), OC, gli stadi funnel selezionati in stadi opportunità aperte (Impostazioni > CRM > Mappatura stadio) e le offerte (opportunità realizzate chiuse).

>[!NOTE]
>
>Il conteggio dei record per una fase del percorso, definita come qualsiasi fase diversa dalla fase della coorte, include tutti i nuovi record, correlati ai record della coorte, creati dopo la data di inizio dell’intervallo di tempo selezionato e prima della data limite. Questa è la causalità dedotta.

È possibile eseguire un drill-down da ogni barra per visualizzare i record di ogni fase.

* Per Sconosciuto, mostra i dettagli del visitatore anonimo.
* Per Known (Noto) vengono visualizzati i dettagli dei visitatori noti.
* Per le fasi LC e Open Lead/Contact (Apri lead/contatto), vengono visualizzati i relativi dettagli.
* Per OC, fasi di apertura dell&#39;opportunità e offerte, vengono visualizzati i dettagli dell&#39;opportunità.
