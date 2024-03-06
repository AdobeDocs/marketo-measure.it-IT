---
unique-page-id: 18874556
description: "[!DNL Marketo Measure] Manutenzione - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Manutenzione"
exl-id: 4e1d53bb-0af8-4774-9f69-6a95516b3d11
feature: Tracking
source-git-commit: fca2db86611d16f4e74467405521a89dd5d825ab
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# [!DNL Marketo Measure] Manutenzione {#marketo-measure-maintenance}

[!DNL Marketo Measure] richiama quasi tutto ciò di cui ha bisogno dal tuo CRM su base giornaliera, ma ci sono alcune attività di manutenzione che dovresti pianificare regolarmente per mantenere [!DNL Marketo Measure] canticchiando e producendo informazioni il più possibile accurate.

**Sincronizza i punti di contatto dell&#39;acquirente per le nuove campagne offline (2x/mese)**

Come hai imparato durante l’onboarding, [!DNL Marketo Measure] ottiene informazioni sulle attività di marketing offline sincronizzandosi con le campagne del CRM. Quando la tua organizzazione avvia nuove campagne, assicurati di abilitare i punti di contatto dell’acquirente per ogni campagna in base alle esigenze.

**Spesa di caricamento per tutti i canali (1x/mese)**

Sfruttare appieno le funzionalità di reporting sul fatturato e sul ROI per[!DNL Marketo Measure], è necessario comunicare [!DNL Marketo Measure] quanto spendi per ciascuno dei tuoi canali e sottocanali di marketing. Designare il proprietario di ogni canale/sottocanale e far sì che tali persone segnalino le spese a una singola parte responsabile del caricamento di nuove informazioni sui costi su base mensile.

Aggiorna la memoria su come caricare le informazioni sui costi leggendo [questo articolo](/help/marketing-spend/spend-management/marketing-channel-costs.md).

**Aggiorna elenco domini da monitorare (1x/mese)**

Marketo Measure tiene traccia di tutte le pagine e i sottodomini in cui è attivo JavaScript, ma solo dei domini che conosciamo. Se di recente hai pubblicato un nuovo dominio, lo hai esteso a livello internazionale o hai modificato il tuo dominio principale, contatta [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} per assicurarci di aggiornare di conseguenza il tuo account.

**Controlla la mappatura del canale personalizzata per la precisione (1x/mese)**

Durante l’onboarding puoi impostare la mappatura personalizzata dei canali per le attività di marketing online e offline. Con l’evolversi della tua strategia di marketing e dell’utilizzo di Marketo Measure, vuoi tenere d’occhio tale logica di mappatura per garantire che tutti i tuoi punti di contatto siano suddivisi in categorie appropriate.

Ricorda: [!DNL Marketo Measure] rielabora i dati quando modifichi la logica di mappatura, in modo da non poter modificare queste regole più di una volta ogni sette giorni.

Riferimento [questo articolo](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md) per la configurazione online, [questo articolo](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md) per la configurazione offline e questo elenco di best practice curato dai nostri clienti:

* Rivedi i punti di contatto che attualmente rientrano in qualsiasi canale &quot;Altro&quot; o &quot;NULL&quot; che potresti aver configurato. Se appropriato, aggiorna la logica di mappatura per riclassificare tali punti di contatto in canali più precisi.
* Rivedi i punti di contatto che attualmente rientrano nei tuoi canali diretti. Se in alcune campagne di e-mail marketing o altre attività mancano i parametri UTM, esiste una buona probabilità che il traffico venga inserito in modo inappropriato in un canale diretto. Prendi in considerazione l’aggiornamento dei parametri UTM per acquisire l’origine di riferimento.

**Valutare le impostazioni di soppressione dei punti di contatto (1x/trimestre)**

Se vedi molti punti di contatto che preferisci non vengano considerati nella tua storia di attribuzione (da un [!DNL Login] o [!DNL Unsubscribe forms], una pagina delle carriere o un’app interna, ad esempio), puoi valutare le impostazioni di soppressione dei punti di contatto esistenti. Una volta al trimestre, individua eventuali gruppi di punti di contatto che creano disturbi non necessari e aggiorna la logica di soppressione in modo appropriato. [Ecco un articolo utile](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md)  con le istruzioni.

**Verifica la mappatura personalizzata dello stadio per la precisione (1x/trimestre) (se applicabile)**

Se utilizzi un [!UICONTROL Lead], [!UICONTROL Contact], o [!UICONTROL Opportunities] stadi, potresti anche aver personalizzato la parte della pipeline in cui tali stadi sono mappati e se sono inclusi in un modello di attribuzione personalizzato. Una volta al trimestre, visita [questo articolo](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md) per aggiornare la memoria sulla mappatura personalizzata degli stadi e assicurarti di monitorare accuratamente gli stadi personalizzati.

**Confronta modello di apprendimento automatico con ponderazione del modello personalizzato (1x/trimestre) (se applicabile)**

Se hai la licenza per [!DNL Marketo Measure] Modello personalizzato, sono disponibili anche dati del nostro Modello di apprendimento automatico (MLM) in [!UICONTROL Settings] > [!UICONTROL Attribution Settings]. MLM calcola l’importanza di ogni fase utilizzando i dati dei punti di contatto del tuo account e può aiutarti a decidere come allocare il peso dell’attribuzione nel modello personalizzato. È consigliabile confrontare il modello MLM con il modello personalizzato una volta al trimestre e discutere le implicazioni delle potenziali modifiche al modello personalizzato con il modello SM.

Per ulteriori informazioni su [!DNL Marketo Measure] Modello di apprendimento automatico, vedi [questo articolo](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md).
