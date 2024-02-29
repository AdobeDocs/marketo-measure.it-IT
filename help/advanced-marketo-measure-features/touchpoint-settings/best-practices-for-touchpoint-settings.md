---
description: Best practice per le impostazioni dei punti di contatto - [!DNL Marketo Measure]
title: Best practice per le impostazioni dei punti di contatto
exl-id: 01e314a6-e33d-45cd-aaa3-c212afec07d1
feature: Touchpoints
source-git-commit: 518a984b0d8d640290bd9b637221fcdc0948e5b9
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---

# Best practice per le impostazioni dei punti di contatto {#best-practices-for-touchpoint-settings}

## Panoramica {#overview}

Il [!UICONTROL Touchpoint Settings] sezione del tuo [!DNL Marketo Measure] consente di impostare regole che elimineranno o rimuoveranno i punti di contatto dal [!DNL Marketo Measure] dati e relativi sistemi. Queste regole possono aiutarti a isolare alcuni set di dati che non devono essere rappresentati nei dati del punto di contatto dell’acquirente o che non desideri ricevere il credito di attribuzione senza disturbare il tracciamento e la raccolta dei dati.

**Rimozione punto di contatto** significa [!DNL Marketo Measure] rimuoverà (ovvero rimuoverà) dal CRM tutti i punti di contatto che soddisfano i criteri della regola. I dati possono essere segnalati all&#39;interno del [!DNL Marketo Measure] Dashboard ROI (individuazione), ma non viene visualizzato nel CRM. Solitamente utilizzato per alleviare lo stress sui limiti di archiviazione dei dati all’interno del CRM

**Soppressione punto di contatto** è simile a Rimozione punto di contatto, ma i dati NON POSSONO essere riportati all’interno della dashboard ROI. Eventuali punti di contatto soppressi non saranno accessibili nel CRM o nell’individuazione. L’eliminazione assicurerà la corrispondenza tra i dati CRM e i dati di Discover. Comunemente utilizzato per perfezionare e specificare ulteriormente quali dati del punto di contatto desideri ricevere il credito di attribuzione.

Nel tuo [!DNL Marketo Measure] app, il [!UICONTROL Touchpoint Settings] sarà suddivisa in quattro sezioni chiave. Ogni sezione sopprime o rimuove un diverso set di dati. Utilizza il tasto seguente per assicurarti che le tue regole eliminino o rimuovano i punti di contatto desiderati.

* Rimuovi punti di contatto dell&#39;acquirente da CRM
   * Utilizzare questa sezione quando si desidera creare una regola che rimuoverà **Dati punto di contatto acquirente** (i punti di contatto associati all’individuo, non l’opportunità) dal tuo **CRM**
* Elimina punti di contatto dell&#39;acquirente da CRM
   * Utilizzare questa sezione quando si desidera creare una regola che rimuoverà **Dati punto di contatto acquirente** (i punti di contatto associati all’individuo, non l’opportunità) dal tuo **CRM** e **Scoprire**
* Rimuovi punti di contatto di attribuzione buyer da CRM
   * Utilizzare questa sezione quando si desidera creare una regola che rimuoverà **Punto di contatto di attribuzione acquirente** i dati (i punti di contatto associati all’opportunità e ai ricavi) dal tuo **CRM**
* Elimina punti di contatto di attribuzione buyer da CRM
   * Utilizzare questa sezione quando si desidera creare una regola che rimuoverà **Punto di contatto di attribuzione acquirente** i dati (i punti di contatto associati all’opportunità e ai ricavi) dal tuo **CRM** e **Scoprire**

## Best practice {#best-practice}

Se stabilisci le regole di impostazione del punto di contatto per la prima volta o le stai solo esaminando per verificarne l’accuratezza, tieni presente le seguenti best practice.

* Stabilisci l’elenco dei dati da eliminare o rimuovere prima di creare le regole
* Identifica esattamente quali campi denoteranno chiaramente la regola o le regole che stai impostando
* Assicurati di aver specificato l’operatore corretto per la regola
* Utilizzando il tasto di cui sopra, assicurati che la regola sia specificata nella sezione corretta delle Impostazioni del punto di contatto
* Verifica le regole prima di implementarle replicando la logica della regola in un rapporto di punto di contatto acquirente in CRM per assicurarti che vengano eliminati o rimossi i dati desiderati

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

Revisione [!UICONTROL Touchpoint Settings] è importante in quanto può modificare drasticamente i dati quando non sono definiti in modo appropriato. Come best practice, ti consigliamo di rivedere le impostazioni del punto di contatto almeno due volte all’anno. Si tratta di una semplice revisione visiva delle regole impostate nella sezione Impostazioni punto di contatto del [!DNL Marketo Measure] app. Questa revisione ti consentirà di essere certo che le impostazioni del punto di contatto siano aggiornate e che sia possibile apportare le modifiche necessarie.

Motivi per rivedere [!UICONTROL Touchpoint] Le impostazioni includono...

* Fatturato del team marketing
* Aggiornamenti principali alla struttura del sito web
* Identificazione dei dati del punto di contatto che non sono più utili
   * Ogni volta che ti imbatti in dati punto di contatto che non dovresti ricevere il merito di attribuzione, [!DNL touchpoint suppression] Le regole sono la funzionalità per garantire dati il più possibile puliti e precisi.
* Modifiche ai campi utilizzati per definire le regole di soppressione o rimozione

>[!MORELIKETHIS]
>
>* [Panoramica sulla rimozione e l’eliminazione dei punti di contatto](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md)
>* [Perché i punti di contatto non devono mai essere eliminati](/help/advanced-marketo-measure-features/touchpoint-settings/why-you-should-never-delete-touchpoints.md)
>* [Punti di contatto dell&#39;acquirente (BT) e punti di contatto di attribuzione dell&#39;acquirente (BAT)](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md)

