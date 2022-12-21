---
unique-page-id: 18874779
description: Modello di attribuzione e configurazione personalizzati - [!DNL Marketo Measure] - Documentazione del prodotto
title: Modello di attribuzione e configurazione personalizzati
exl-id: 7b156db2-9ac6-4d32-ac67-06c0aa15d651
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---

# Modello di attribuzione e configurazione personalizzati {#custom-attribution-model-and-setup}

Vedi sotto per una panoramica del [!DNL Marketo Measure] modello di attribuzione personalizzato e modalità di configurazione.

## Modello di attribuzione personalizzato {#custom-attribution-model}

La [!DNL Marketo Measure] Il modello Attribution personalizzato consente agli utenti di scegliere quali punti di contatto o stadi personalizzati includere nel modello. Gli utenti sono in grado di controllare la percentuale di credito sul ricavo attribuito a questi punti di contatto e fasi, oppure possono utilizzare i valori percentuali di attribuzione suggeriti dal [!DNL Marketo Measure] Modello di apprendimento automatico.

## Come impostare il modello di attribuzione personalizzato {#how-to-set-up-your-custom-attribution-model}

1. Determinare quali fasi includere nel modello personalizzato.

   Per iniziare a creare il modello di attribuzione personalizzato, dovrai selezionare gli stadi importanti per il team di marketing. Oltre al [!DNL Marketo Measure] le fasi cardine (FT, LC, OC, Closed) possono aggiungere fino a sei ulteriori stati di lead/contatti o opportunità nel modello personalizzato. Ad esempio, è comune che l’area di visualizzazione MQL sia inclusa nel modello personalizzato. I team di marketing spesso desiderano sapere quali sforzi o canali stanno portando le transizioni al passaggio MQL.

   Accedi a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target=&quot;_blank&quot;}. Vai a [!UICONTROL My Account] > [!UICONTROL Settings] > e nella sezione CRM, seleziona **[!UICONTROL Stage Mapping]**.

   Una volta qui, è necessario selezionare gli stadi Lead/Contatti e Opportunità da includere selezionando la **[!UICONTROL Include in Model]** scatola.

   >[!NOTE]
   >
   >Sono consentite fino a sei fasi personalizzate (escluse le impostazioni predefinite: FT, LC, OC, Closed).

   ![](assets/1-1.png)

   >[!NOTE]
   >
   >_Tutto_ Gli stadi Lead/Contatti e Opportunità verranno visualizzati qui, anche se l’area di visualizzazione è inattiva o non è più utilizzata in [!DNL Salesforce]. Se desideri rimuovere questi stadi, dovrai eliminarli a fondo in [!DNL Salesforce].

   Quando hai selezionato le aree di visualizzazione, assicurati di fare clic sul pulsante **[!UICONTROL Save & Process]** nella parte inferiore della pagina. Gli stadi verranno ora visualizzati nella sezione **[!UICONTROL Attribution Settings]** e potrai assegnare percentuali di attribuzione a ogni passaggio. Le fasi personalizzate verranno visualizzate anche nella suite di prestazioni di marketing come fase Lead o Opportunità nella cascata domanda.

   Se nel modello sono presenti altri stadi che si desidera includere, ma non sono nella [!UICONTROL Lead/Contact Status] o [!UICONTROL Opportunity Stage] elenco, puoi definire il tuo stage personalizzato in base ai campi nel tuo CRM.

   Nell’esempio seguente, viene definito un passaggio &quot;MQL&quot; personalizzato utilizzando un campo data. La regola indica semplicemente che se il campo Data MQL non è vuoto, deve essere considerato un MQL e deve essere incluso nel modello personalizzato. Si prega di notare che è anche importante ordinare le fasi personalizzate una volta create in modo che segua l&#39;avanzamento del ciclo di vendita.

   ![](assets/2-1.png)

   >[!CAUTION]
   >
   >Non dimenticare di abilitare il tracciamento della cronologia per i campi personalizzati.

Se un campo personalizzato viene utilizzato nel modello personalizzato, il tracciamento della cronologia dei campi DEVE essere abilitato nel CRM. Per istruzioni su come abilitare il tracciamento della cronologia dei campi, [fai clic qui](/help/advanced-marketo-measure-features/custom-attribution-models/custom-model-setup-enable-field-history-tracking.md).

1. Determina le percentuali di attribuzione per il modello personalizzato.

   Vai a **[!UICONTROL Attribution Settings]** in [!DNL Marketo Measure] Apps; gli stadi personalizzati verranno visualizzati qui nella tabella di attribuzione. Nella tabella di attribuzione vengono visualizzati tutti gli [!DNL Marketo Measure] modelli di attribuzione e ponderazione di ciascun modello. Le percentuali di attribuzione dei primi cinque modelli sono fisse e non possono essere modificate.

   Nella colonna a destra con etichetta &quot;**[!UICONTROL Custom]**,&quot; puoi impostare la ponderazione percentuale per ogni fase nel modello di attribuzione personalizzato. È sufficiente inserire i valori per ogni fase nella colonna Personalizzato . Then **[!UICONTROL Save and Reprocess]** una volta completato.

   A sinistra della colonna &quot;Personalizzato&quot; è **[!DNL Marketo Measure]Modello di apprendimento automatico**. Il modello di apprendimento automatico calcola la ponderazione dell’attribuzione in base all’importanza relativa di vincere un’offerta in base a quanto accaduto in ogni fase personalizzata. Per ulteriori informazioni sul modello di apprendimento automatico, [fai clic qui](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md).

   ![](assets/3.png)

## Posizioni dei punti di contatto {#touchpoint-positions}

Dopo aver salvato ed elaborato le percentuali di attribuzione, i punti di contatto vengono aggiornati e ricevono le nuove posizioni e fasi. Il punto di contatto che si è verificato più di recente, prima di una transizione di fase, riceverà credito per tale fase (come mostrato di seguito). Anche la ponderazione e i ricavi personalizzati vengono ridistribuiti.

![](assets/4.png)

## Differenza tra le fasi funnel e le fasi del modello personalizzato {#the-difference-between-funnel-stages-and-custom-model-stages}

Ora puoi visualizzare le fasi personalizzate nel tuo funnel di marketing, anche se non hai abilitato Modello personalizzato. Ciò avverrà tramite l&#39;utilizzo della funzionalità Funnel Stage. Gli stadi funnel ora consentono di aggiungere gli stadi al funnel, ma non di visualizzarne l’attribuzione.

Gli stadi funnel verranno comunque tracciati come punti di contatto e continueranno a essere visualizzati come posizioni di punti di contatto nel CRM. Senza Modello personalizzato, questi punti di contatto potrebbero comunque ricevere l’attribuzione a livello di punto centrale in caso di compilazione di un modulo (10% per i punti medi), ma senza credito di attribuzione in caso di visita web.

Come potete vedere di seguito, abbiamo incluso la fase di Diligence come parte delle nostre fasi funnel. Ciò significa che avremo punti di contatto in cui la posizione contiene Diligence, ma questi punti di contatto riceveranno il credito di attribuzione Middle Touch solo se Modello personalizzato non è abilitato (al massimo 10%).

![](assets/5.png)

>[!NOTE]
>
>Il comportamento per i modelli personalizzati BAT consiste nel dividere il punto percentuale di contatto intermedio del modello personalizzato in modo uniforme tra le altre fasi, purché non vi siano tocchi intermedi.
