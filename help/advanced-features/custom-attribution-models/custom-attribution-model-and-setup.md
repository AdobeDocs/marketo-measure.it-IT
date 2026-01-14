---
description: Modello di attribuzione personalizzato e linee guida per l’installazione per gli utenti di Marketo Measure
title: Modello di attribuzione e configurazione personalizzati
exl-id: 7b156db2-9ac6-4d32-ac67-06c0aa15d651
feature: Attribution, Custom Models
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 0%

---

# Modello di attribuzione e configurazione personalizzati {#custom-attribution-model-and-setup}

Di seguito è riportata una panoramica del modello di attribuzione personalizzato [!DNL Marketo Measure] e la relativa configurazione.

## Modello di attribuzione personalizzato {#custom-attribution-model}

Il modello di attribuzione personalizzata [!DNL Marketo Measure] consente agli utenti di scegliere quali punti di contatto o fasi personalizzate includere nel modello. Gli utenti possono controllare la percentuale di credito di ricavo attribuita a questi punti di contatto e stadi oppure possono utilizzare i valori di percentuale di attribuzione suggeriti dal modello di apprendimento automatico [!DNL Marketo Measure].

## Come impostare il modello di attribuzione personalizzato {#how-to-set-up-your-custom-attribution-model}

1. Determina quali stadi desideri includere nel modello personalizzato.

   Per iniziare a creare il modello di attribuzione personalizzato, seleziona le fasi più importanti per il team Marketing. Oltre alle [!DNL Marketo Measure] fasi cardine (FT, LC, OC, Closed) è possibile aggiungere fino a sei ulteriori stati di lead/contatti o opportunità nel modello personalizzato. Ad esempio, è comune che lo stadio MQL sia incluso nel modello personalizzato. I team di marketing spesso desiderano sapere quali sforzi o canali stanno guidando le transizioni alla fase MQL.

   Accedi a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}. Vai a [!UICONTROL My Account] > [!UICONTROL Settings] > e nella sezione CRM seleziona **[!UICONTROL Stage Mapping]**.

   Scegliere quindi le fasi lead/contatti e opportunità da includere selezionando la casella **[!UICONTROL Include in Model]**.

   >[!NOTE]
   >
   >Sono consentiti fino a sei stadi personalizzati (esclusi i valori predefiniti: FT, LC, OC, Closed).

   ![](assets/custom-models-1.png)

   >[!NOTE]
   >
   >_Tutte_ le fasi Contatti/lead e Opportunità verranno visualizzate qui, anche se la fase è inattiva o non è più utilizzata in [!DNL Salesforce]. Se si desidera rimuovere queste fasi, sarà necessario eliminarle definitivamente in [!DNL Salesforce].

   Dopo aver selezionato le fasi, fare clic sul pulsante **[!UICONTROL Save & Process]** nella parte inferiore della pagina. Le fasi verranno ora visualizzate nella scheda **[!UICONTROL Attribution Settings]** e sarà possibile assegnare percentuali di attribuzione a ciascuna fase. Le fasi personalizzate vengono visualizzate anche nella suite di prestazioni marketing come fase lead o opportunità all’interno della cascata della domanda.

   Se nel modello sono presenti altri stadi che si desidera includere ma non sono inclusi nell&#39;elenco [!UICONTROL Lead/Contact Status] o [!UICONTROL Opportunity Stage], è possibile definire uno stadio personalizzato in base ai campi presenti nel CRM.

   Nell’esempio seguente, viene definita una fase &quot;MQL&quot; personalizzata utilizzando un campo data. La regola afferma semplicemente che se il campo Data MQL non è vuoto, deve essere considerato un MQL e deve essere incluso nel modello personalizzato. È inoltre importante ordinare le fasi personalizzate una volta create in modo che seguano l’avanzamento del ciclo di vendita.

   ![](assets/custom-models-10.png)

   >[!CAUTION]
   >
   >Non dimenticare di abilitare il tracciamento della cronologia per i campi personalizzati.

Se nel modello personalizzato viene utilizzato un campo personalizzato, il tracciamento della cronologia dei campi DEVE essere abilitato nel CRM. Per istruzioni su come abilitare il tracciamento della cronologia dei campi, fare riferimento a [Impostazione modello personalizzato: Abilita tracciamento cronologia campi](/help/advanced-features/custom-attribution-models/custom-model-setup-enable-field-history-tracking.md).

1. Determina le percentuali di attribuzione per il modello personalizzato.

   Vai a **[!UICONTROL Attribution Settings]** in [!DNL Marketo Measure] app; le fasi personalizzate verranno visualizzate qui nella tabella di attribuzione. La tabella di attribuzione visualizza tutti i modelli di attribuzione [!DNL Marketo Measure] e la ponderazione dell&#39;attribuzione di ciascun modello. Le percentuali di attribuzione dei primi cinque modelli sono fisse e non possono essere modificate.

   Nella colonna a destra con etichetta &quot;**[!UICONTROL Custom]**&quot; è possibile impostare la ponderazione percentuale per ogni fase del modello di attribuzione personalizzato. Immettere i valori per ogni fase nella colonna Personalizzato e fare clic su **[!UICONTROL Save and Reprocess]** al termine.

   A sinistra della colonna _Personalizzato_ si trova il modello **[!DNL Marketo Measure]di Machine Learning**. Il modello di apprendimento automatico calcola la ponderazione dell’attribuzione in base all’importanza relativa per la vincita di un’offerta, in base a ciò che è successo in ogni fase personalizzata. Per ulteriori informazioni sul modello di apprendimento automatico, consulta [Domande frequenti sul modello di apprendimento automatico](/help/advanced-features/custom-attribution-models/machine-learning-model-faq.md).

   ![](assets/custom-models-2.png)

## Posizioni dei punti di contatto {#touchpoint-positions}

Una volta salvate ed elaborate le percentuali di attribuzione, i punti di contatto verranno aggiornati e riceveranno i loro nuovi stadi e posizioni. Al punto di contatto che si è verificato più di recente, prima di una transizione di fase, verrà attribuito il merito per quella fase (come mostrato di seguito). Anche la ponderazione personalizzata e le entrate vengono ridistribuite.

![](assets/custom-models-3.png)

## Differenza tra gli stadi di Funnel e gli stadi di modello personalizzati {#the-difference-between-funnel-stages-and-custom-model-stages}

Ora puoi visualizzare le fasi personalizzate nel Funnel di marketing, anche se non hai abilitato Modello personalizzato. Ciò avviene tramite l&#39;utilizzo della funzionalità di Funnel Stage. Gli stadi di funnel ora consentono di aggiungere stadi a funnel, ma non di visualizzarne l’attribuzione.

Le fasi di funnel verranno comunque tracciate come punti di contatto e verranno comunque visualizzate come posizioni dei punti di contatto nel CRM. Senza modello personalizzato, questi punti di contatto possono ancora ricevere l’attribuzione del contatto intermedio in caso di compilazione di un modulo (10% per i contatti intermedi), ma zero credito di attribuzione in caso di semplice visita web.

Come puoi vedere qui sotto, abbiamo incluso la fase Diligence tra le nostre fasi Funnel. Ciò significa che avremo punti di contatto in cui la posizione contiene Diligence, ma che riceveranno credito di attribuzione Middle Touch solo se il modello personalizzato non è abilitato (al massimo il 10%).

![](assets/custom-models-7.png)

>[!NOTE]
>
>Il comportamento dei modelli personalizzati BAT consiste nel dividere in modo uniforme la percentuale di contatto medio del modello personalizzato in altri stadi, purché non vi siano contatti intermedi.
