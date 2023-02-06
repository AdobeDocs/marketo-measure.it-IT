---
unique-page-id: 18874556
description: "[!DNL Marketo Measure] Manutenzione - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] Manutenzione"
exl-id: 4e1d53bb-0af8-4774-9f69-6a95516b3d11
source-git-commit: 09ffdbb0b1baeed870a3145268997e63a3707c97
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# [!DNL Marketo Measure] Manutenzione {#marketo-measure-maintenance}

[!DNL Marketo Measure] richiama quasi tutto ciò di cui ha bisogno dal CRM su base giornaliera, ma ci sono alcune attività di manutenzione che si desidera pianificare regolarmente per mantenere [!DNL Marketo Measure] canticchiare e trasmettere le informazioni più accurate possibili.

**Sincronizza punti di contatto dell&#39;acquirente per nuove campagne offline (2x/mese)**

Come avete imparato durante l&#39;onboarding, [!DNL Marketo Measure] ottiene informazioni sulle attività di marketing offline sincronizzandole con le campagne CRM. Quando la tua organizzazione avvia nuove campagne, assicurati di abilitare i punti di contatto dell’acquirente per ogni campagna, a seconda delle necessità. Consulta [articolo](/help/channel-tracking-and-setup/offline-channels/syncing-offline-campaigns.md)per ulteriori informazioni.

**Carica la spesa per tutti i canali (1x/mese)**

Sfruttare appieno le funzionalità di reporting dei ricavi e del ROI per[!DNL Marketo Measure], devi dire [!DNL Marketo Measure] quanto spendi per ciascuno dei tuoi canali di marketing e sottocanali. Si consiglia di designare il proprietario di ciascun canale/canale secondario e di fare in modo che le persone segnalino le spese a un singolo responsabile del caricamento di nuove informazioni sui costi su base mensile.

Aggiornare la memoria su come caricare le informazioni sui costi leggendo [articolo](/help/marketing-spend/spend-management/marketing-channel-costs.md).

**Aggiorna elenco di domini da monitorare (1x/mese)**

Marketo Measure tiene traccia di tutte le pagine e i sottodomini in cui è attivo il nostro JavaScript, ma solo dei domini di cui siamo a conoscenza. Se hai recentemente debuttato un nuovo dominio, esteso a livello internazionale o modificato il dominio primario, contatta [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} per essere certi di aggiornare il tuo account di conseguenza.

**Esamina la mappatura dei canali personalizzati per la precisione (1x/mese)**

Durante l’onboarding, configuri la mappatura dei canali personalizzati per le tue attività di marketing online e offline. Con l’evolversi della tua strategia di marketing e dell’utilizzo di Marketo Measure, dovrai tenere sotto controllo tale logica di mappatura per garantire che tutti i tuoi punti di contatto siano categorizzati in modo appropriato.

Ricorda, [!DNL Marketo Measure] rielabora i dati quando modifichi la logica di mappatura, pertanto non potrai modificare queste regole più di una volta ogni 7 giorni.

Riferimento [articolo](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md) per la configurazione online, [articolo](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md) per la configurazione offline e questo elenco di best practice curate dai nostri clienti:

* Rivedi i punti di contatto che rientrano attualmente in qualsiasi canale &quot;Altro&quot; o &quot;NULL&quot; configurato. Se appropriato, aggiorna la logica di mappatura per riorganizzare tali punti di contatto in canali più precisi.
* Esamina i punti di contatto che rientrano attualmente nei tuoi canali diretti. Se alcune delle tue campagne di marketing e-mail o altre attività non contengono parametri UTM, c&#39;è una buona probabilità che il traffico venga allocato in modo inappropriato in un canale Direct. È consigliabile aggiornare i parametri UTM per acquisire l’origine di riferimento.

**Valutare le impostazioni di soppressione dei punti di contatto (1x/trimestre)**

Se vedi molti punti di contatto che preferisci non essere considerati nel tuo brano di attribuzione (da un [!DNL Login] o [!DNL Unsubscribe forms], una pagina carriere o un’app interna, ad esempio), puoi valutare le impostazioni di soppressione dei punti di contatto esistenti. Una volta ogni trimestre, individua tutti i gruppi di punti di contatto che creano rumore inutile e aggiorna la logica di soppressione in modo appropriato. [Ecco un articolo utile](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md)  con il how-to.

**Rivedi la mappatura personalizzata dell’area di visualizzazione per la precisione (1x/trimestre) (se applicabile)**

Se utilizzi un [!UICONTROL Lead], [!UICONTROL Contact]oppure [!UICONTROL Opportunities] È inoltre possibile che sia stato personalizzato a quale parte della pipeline mappano tali fasi e se tali fasi sono incluse o meno in un modello di attribuzione personalizzato. Una volta al trimestre, visita [articolo](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md) per aggiornare la memoria sulla mappatura personalizzata dell&#39;area di visualizzazione e assicurarsi di monitorare con precisione gli stadi personalizzati.

**Confrontare il modello di apprendimento automatico con la ponderazione del modello personalizzato (1x/trimestre) (se applicabile)**

Se si dispone della licenza per il [!DNL Marketo Measure] Modello personalizzato, hai anche dati disponibili dal nostro modello di apprendimento automatico (MLM) in [!UICONTROL Settings] > [!UICONTROL Attribution Settings]. L’MLM calcola l’importanza di ogni fase utilizzando i dati dei punti di contatto dell’account e può aiutarti a decidere come allocare il peso dell’attribuzione nel modello personalizzato. Si consiglia di confrontare l’MLM con il modello personalizzato una volta al trimestre e di discutere le implicazioni delle potenziali modifiche al modello personalizzato con l’SM.

Per ulteriori informazioni sulla [!DNL Marketo Measure] Modello di apprendimento automatico, check-out [articolo](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md).
