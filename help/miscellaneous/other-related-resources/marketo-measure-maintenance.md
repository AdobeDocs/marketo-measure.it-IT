---
unique-page-id: 18874556
description: "[!DNL Marketo Measure] manutenzione - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] manutenzione"
exl-id: 4e1d53bb-0af8-4774-9f69-6a95516b3d11
feature: Tracking
source-git-commit: fca2db86611d16f4e74467405521a89dd5d825ab
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# Manutenzione di [!DNL Marketo Measure] {#marketo-measure-maintenance}

[!DNL Marketo Measure] richiama quasi tutto ciò che serve dal tuo CRM su base giornaliera, ma ci sono alcune attività di manutenzione che dovresti pianificare regolarmente per mantenere [!DNL Marketo Measure] che canta e produce le informazioni più accurate possibili.

**Sincronizza punti di contatto dell&#39;acquirente per nuove campagne offline (2x/mese)**

Come hai appreso durante l&#39;onboarding, [!DNL Marketo Measure] ottiene informazioni sulle tue attività di marketing offline sincronizzandosi con le campagne CRM. Quando la tua organizzazione avvia nuove campagne, assicurati di abilitare i punti di contatto dell’acquirente per ogni campagna in base alle esigenze.

**Spese di caricamento per tutti i canali (1x/mese)**

Per sfruttare appieno le funzionalità di generazione rapporti sulle entrate e sul ROI per [!DNL Marketo Measure], è necessario comunicare a [!DNL Marketo Measure] quanto si spende per ciascuno dei canali di marketing e dei sottocanali. Designare il proprietario di ogni canale/sottocanale e far sì che tali persone segnalino le spese a una singola parte responsabile del caricamento di nuove informazioni sui costi su base mensile.

Aggiorna la memoria su come caricare le informazioni sui costi leggendo [questo articolo](/help/marketing-spend/spend-management/marketing-channel-costs.md).

**Aggiorna l&#39;elenco dei domini da monitorare (1x/mese)**

Marketo Measure tiene traccia di tutte le pagine e i sottodomini in cui è attivo JavaScript, ma solo dei domini che conosciamo. Se di recente hai creato un nuovo dominio, lo hai esteso a livello internazionale o hai modificato il tuo dominio principale, contatta il [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} per assicurarti di aggiornare di conseguenza il tuo account.

**Verifica la precisione della mappatura del canale personalizzata (1x/mese)**

Durante l’onboarding puoi impostare la mappatura personalizzata dei canali per le attività di marketing online e offline. Con l’evolversi della tua strategia di marketing e dell’utilizzo di Marketo Measure, vuoi tenere d’occhio tale logica di mappatura per garantire che tutti i tuoi punti di contatto siano suddivisi in categorie appropriate.

Ricorda che [!DNL Marketo Measure] rielabora i dati quando modifichi la logica di mappatura, pertanto non potrai modificare queste regole più di una volta ogni sette giorni.

Fai riferimento a [questo articolo](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md) per la configurazione online, [questo articolo](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md) per la configurazione offline e questo elenco di best practice elaborate dai nostri clienti:

* Rivedi i punti di contatto che attualmente rientrano in qualsiasi canale &quot;Altro&quot; o &quot;NULL&quot; che potresti aver configurato. Se appropriato, aggiorna la logica di mappatura per riclassificare tali punti di contatto in canali più precisi.
* Rivedi i punti di contatto che attualmente rientrano nei tuoi canali diretti. Se in alcune campagne di e-mail marketing o altre attività mancano i parametri UTM, esiste una buona probabilità che il traffico venga inserito in modo inappropriato in un canale diretto. Prendi in considerazione l’aggiornamento dei parametri UTM per acquisire l’origine di riferimento.

**Valuta impostazioni soppressione punto di contatto (1x/trimestre)**

Se vedi molti punti di contatto che preferisci non vengano considerati nella tua storia di attribuzione (ad esempio da [!DNL Login] o [!DNL Unsubscribe forms], una pagina carriere o un&#39;app interna), puoi valutare le impostazioni di soppressione dei punti di contatto esistenti. Una volta al trimestre, individua eventuali gruppi di punti di contatto che creano disturbi non necessari e aggiorna la logica di soppressione in modo appropriato. [Ecco un articolo utile](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md) con le procedure.

**Verifica la mappatura personalizzata dello stadio per la precisione (1x/trimestre) (se applicabile)**

Se utilizzi uno stadio [!UICONTROL Lead], [!UICONTROL Contact] o [!UICONTROL Opportunities] personalizzato, potresti anche aver personalizzato la parte della pipeline in cui tali stadi sono mappati e se sono inclusi in un modello di attribuzione personalizzato. Una volta al trimestre, visita [questo articolo](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md) per aggiornare la memoria sulla mappatura personalizzata delle fasi e assicurarti di tenere traccia delle fasi personalizzate in modo accurato.

**Confrontare il modello di apprendimento automatico con la ponderazione del modello personalizzato (1x/trimestre) (se applicabile)**

Se si dispone della licenza per il modello personalizzato [!DNL Marketo Measure], sono disponibili dati anche dal modello di apprendimento automatico (MLM) in [!UICONTROL Settings] > [!UICONTROL Attribution Settings]. MLM calcola l’importanza di ogni fase utilizzando i dati dei punti di contatto del tuo account e può aiutarti a decidere come allocare il peso dell’attribuzione nel modello personalizzato. È consigliabile confrontare il modello MLM con il modello personalizzato una volta al trimestre e discutere le implicazioni delle potenziali modifiche al modello personalizzato con il modello SM.

Per ulteriori informazioni sul modello di apprendimento automatico [!DNL Marketo Measure], vedi [questo articolo](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md).
