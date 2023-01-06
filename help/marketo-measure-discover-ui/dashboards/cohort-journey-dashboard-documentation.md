---
unique-page-id: 42762648
description: Documentazione del dashboard del Percorso di coorte - [!DNL Marketo Measure] - Documentazione del prodotto
title: Documentazione del dashboard del Percorso di coorte
exl-id: b139f720-86ae-4f6d-9dfc-cc67b4186f88
source-git-commit: 28f1400e8e13c091e8ea2a3bef115a0db810c2e0
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Documentazione del dashboard del Percorso di coorte {#cohort-journey-dashboard-documentation}

Le dashboard Impatto coorte e Funnel consentono agli addetti al marketing di visualizzare la progressione da una fase di coorte iniziale per un intervallo di tempo selezionato e di misurare il tasso di conversione.

La differenza principale è il modo in cui conteggiamo ogni entità dalla fase coorte.

* Funnel coorte: Il risultato di ciascuna fase è direttamente derivato dalla fase precedente.

   * Vengono conteggiati solo i record che attraversano ogni fase dell’imbuto dopo l’ora di inizio della coorte impostata.

![](assets/cohort-journey-dashboard-documentation-1.png)

* Impatto sulla coorte: Il risultato di ogni fase è derivato dalla fase coorte, non dalla fase precedente.

   * Tutti i record in ogni fase vengono conteggiati purché siano accaduti dopo l’ora di inizio della coorte impostata. Questo dashboard avrà naturalmente più record del dashboard Funnel, dato che stiamo osservando come le entità sono state influenzate dal passaggio della coorte, non solo il movimento attraverso il funnel.

![](assets/cohort-journey-dashboard-documentation-2.png)

Ogni dashboard ha due riquadri:

* Entrate coorte: L&#39;importo totale delle opportunità da tutte le opportunità nella fase Offerte del Percorso Cohort.
* Percorso per coorte: La progressione a ogni fase del percorso dalla fase iniziale della coorte per un intervallo di tempo selezionato.

>[!NOTE]
>
>In tutte le dashboard di Discover, è possibile segnalare un solo oggetto persona, Lead o Contatto. È impostato in [!UICONTROL Settings] > [!UICONTROL Reporting] > [!UICONTROL Attribution Settings] > [!UICONTROL Default Dashboard Object].

Le dashboard supportano i seguenti filtri:

* Fase coorte: seleziona la fase di coorte iniziale. I record in tutte le fasi successive vengono evoluti dai record nella fase coorte.
* Intervallo date coorte: seleziona l’intervallo di tempo per lo stadio coorte selezionato. Insieme a Cohort Stage, definisce il set di dati iniziale.
* Data limite: selezionare la data in cui deve verificarsi la progressione del record in tutte le fasi successive. Il valore predefinito è oggi. Questo vale per tutti gli stadi diversi da quello della coorte.
* Canale: filtrare i record in base ai canali. Un record è associato a un canale se uno dei suoi punti di contatto è associato al canale.
* Canale secondario: filtrare i record per sottocanali. Un record è associato a un canale secondario se uno dei suoi punti di contatto è associato al canale secondario.
* Campagna: filtrare i record in base alle campagne. Un record è associato a una campagna se uno dei relativi punti di contatto è associato alla campagna.
* Origine campagna: filtrare i record in base alle origini della campagna. Esempio di origini di campagne [!DNL Adwords], [!DNL BingAds], [!DNL Facebook], [!DNL LinkedIn], ecc. Un record è associato a un’origine della campagna se uno dei relativi punti di contatto è associato all’origine della campagna.
* Filtri del segmento: filtrare i record in base ai segmenti personalizzati. Un record è associato a un segmento se uno dei suoi punti di contatto è associato al segmento.

In tutti i filtri viene utilizzata la logica &quot;AND&quot; (E).

>[!NOTE]
>
>I filtri dei segmenti si applicano solo allo stadio LC e dopo. Se Cohort Stage è sconosciuto o noto e uno dei filtri del segmento ha un valore, il dashboard non restituirà alcun risultato.

Le fasi includono Sconosciuto, Noto, LC, le fasi funnel selezionate in Stadi lead/contatti aperti (Impostazioni > CRM > Mappatura stage), OC, le fasi funnel selezionate in Fasi opportunità aperte (Impostazioni > CRM > Mappatura stage) e Offerte (Opportunità di esecuzione chiuse).

>[!NOTE]
>
>Il conteggio dei record per uno stadio percorso, definito come qualsiasi altro stadio diverso da quello della coorte, include tutti i nuovi record relativi ai record della coorte creati dopo la data di inizio dell’intervallo di tempo selezionato e prima della data di interruzione. Questa è causalità dedotta.

È possibile approfondire da ogni barra per visualizzare i record di ogni fase.

* Per Sconosciuto, mostra i dettagli dei visitatori anonimi.
* Per Dati noti, mostra i dettagli dei visitatori noti.
* Per le fasi LC e lead/contatto aperti, mostra i dettagli lead/contatti.
* Per OC, le fasi Opportunità aperte e Offerte, mostra i dettagli Opportunità.
