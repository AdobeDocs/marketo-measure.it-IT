---
unique-page-id: 18874604
description: Segmentazione personalizzata - [!DNL Marketo Measure]
title: Segmentazione personalizzata
exl-id: c20a2add-250e-45ff-97a6-1b1c03351b6a
feature: Segmentation
source-git-commit: e1ad563aac12ceb6bea6c28621ebd1cb7ec0a923
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# Segmentazione personalizzata {#custom-segmentation}

I segmenti consentono di filtrare i dati nel dashboard ROI [!DNL Marketo Measure] per eseguire un ulteriore drill-down su un set di dati specifico. Ad esempio, un segmento può essere definito per territorio geografico o sistema di scarpate.

**Perché la segmentazione personalizzata?**

La segmentazione personalizzata consente di filtrare i punti di contatto per categorie (nome filtro) e regole (valori filtro). I clienti di livello 1 ottengono un segmento, quelli di livello 2 e dieci. A seconda dell’oggetto a cui punta il trattino ROI (lead o contatto), puoi creare segmenti in base ai campi presenti nell’oggetto lead/contatto. Inoltre, potrai creare segmenti in base a qualsiasi campo trovato nell’oggetto Opportunità.

**Quando è utile la funzione di segmentazione personalizzata?**

La segmentazione personalizzata può essere utilizzata per visualizzare i dati per un particolare tipo di record. Una volta mappata la logica del filtro, dovresti essere in grado di visualizzare nella vista cascata della domanda del dashboard [!DNL Marketo Measure] gli stessi dati visualizzati nel CRM.

**Come si configura?**

>[!NOTE]
>
>L’aggiornamento delle regole dei segmenti rielabora i dati storici.

Passaggio 1: determinare quali informazioni si desidera visualizzare.

Prima di utilizzare questa funzione, individua le informazioni sui punti di contatto in base alle quali desideri filtrare. Ricorda di utilizzare i valori esatti nel CRM per i tipi di record. La configurazione filtrerà i punti di contatto dalla parte superiore a quella inferiore del funnel di marketing.

Passaggio 2: accedere e individuare la funzionalità [!UICONTROL Segments].

* Vai a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} e accedi
* Nella scheda [!UICONTROL My Account], seleziona [!UICONTROL Settings]
* Seleziona [!UICONTROL Segments] dalle opzioni sulla barra laterale a sinistra, nella sezione [!UICONTROL Reporting]

Passaggio 3: comprendere i componenti.

* Utilizza questa legenda per comprendere le varie icone presenti in questa pagina.

![](assets/1.png)

Passaggio 4: Aggiungere Regole Di Filtro.

* Immettere innanzitutto il nome della categoria. [!UICONTROL Business Type] è un esempio. Al termine, fai clic sul segno di spunta. Inserisci un nome per la categoria prima di poter aggiungere segmenti
* Fai clic sul segno più per aggiungere un segmento
* Immetti un nome per il segmento. Ad esempio, puoi avere un segmento per Nuova azienda, Partner, Rinnovo o Upselling

![](assets/2.png)

* Fai clic sull’icona più per visualizzare i campi di input della regola. Le opzioni nell’elenco a discesa Campo estraggono i campi direttamente dal CRM

![](assets/3.png)

>[!NOTE]
>
>I campi formula non possono essere utilizzati nelle regole e non verranno visualizzati nell&#39;elenco a discesa. Poiché le formule vengono calcolate in background e non modificano un record, [!DNL Marketo Measure] non è in grado di rilevare se un record soddisfa o meno una regola.

* L&#39;opzione [!UICONTROL Value] non è un elenco a discesa e il relativo valore deve essere immesso manualmente. Verifica i valori nell’organizzazione Salesforce
* Ripeti questo processo per le regole del segmento Opportunità
* La categoria &quot;Altro&quot; è un segmento predefinito che acquisirà eventuali punti di contatto non definiti. Puoi modificare il nome del segmento predefinito
* Fai clic sull’icona del cestino per eliminare un’intera categoria o una singola regola all’interno di una categoria. In alternativa, fai clic sull’icona della matita per modificare la categoria o la regola
* Si noti che sono presenti un pulsante &quot;[!UICONTROL Save]&quot; e un pulsante &quot;Salva ed elabora&quot;. Utilizzare il pulsante Salva per salvare il lavoro e le modifiche nel tempo. Utilizzare il pulsante Salva ed elabora SOLO dopo aver verificato che:

   * La mappatura è accurata
   * Hai aggiunto tutti i segmenti di cui desideri tenere traccia all’interno di una categoria
   * Il pulsante Salva ed elabora attiva [!DNL Marketo Measure] per sincronizzare tutti i punti di contatto e applicare le nuove informazioni aggiunte. Questo processo richiede 7 giorni e non è possibile modificare le regole durante questo periodo

**_Note aggiuntive:_**

Se le regole non sono impostate sia per lead/contatti che per opportunità, verrà visualizzata solo una parte dei dati. Per approfondire, se non configuri le regole Opportunità, visualizzerai solo i dati di lead/contatti senza le opportunità associate. Lo stesso vale se non si impostano regole per lead/contatti: verranno visualizzate solo le opportunità senza i lead/contatti associati.

Al termine, fare clic su [!UICONTROL Save], controllare tutto e quindi fare clic su [!UICONTROL Save and Process]. Ricorda che non puoi modificare le impostazioni per sette giorni dopo il salvataggio ed l&#39;elaborazione perché [!DNL Marketo Measure] sta riformattando i dati in questo periodo.

Se sei un cliente di Marketo Measure Ultimate e hai impostato l&#39;oggetto dashboard predefinito come contatto, non utilizzare i due campi seguenti specifici per il lead ([ulteriori informazioni](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).

* b2b.personStatus
* b2b.isConverted

**Come si salvano i report generati?**

Non puoi salvare i rapporti generati direttamente nell’interfaccia utente. Tuttavia, [!DNL Marketo Measure] salva i nomi dei segmenti nell&#39;URL in modo da poter tenere un record di ogni report contrassegnando la pagina con un segnalibro.
