---
description: Tecniche consigliate per le impostazioni dei punti di contatto per gli utenti di Marketo Measure
title: Best practice per le impostazioni dei punti di contatto
exl-id: 01e314a6-e33d-45cd-aaa3-c212afec07d1
feature: Touchpoints
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---

# Best practice per le impostazioni dei punti di contatto {#best-practices-for-touchpoint-settings}

## Panoramica {#overview}

La sezione [!UICONTROL Touchpoint Settings] dell&#39;app [!DNL Marketo Measure] consente di impostare regole che elimineranno o rimuoveranno i punti di contatto dai dati di [!DNL Marketo Measure] e dai sistemi correlati. Queste regole possono aiutarti a isolare alcuni set di dati che non devono essere rappresentati nei dati del punto di contatto dell’acquirente o che non desideri ricevere il credito di attribuzione senza disturbare il tracciamento e la raccolta dei dati.

**Rimozione punto di contatto** significa che [!DNL Marketo Measure] eliminerà (ovvero rimuoverà) eventuali punti di contatto dal CRM che soddisfano i criteri della regola. I dati possono essere segnalati in nella dashboard ROI di [!DNL Marketo Measure] (individuazione), ma non vengono visualizzati nella gestione delle relazioni con i clienti. Solitamente utilizzato per alleviare lo stress sui limiti di archiviazione dei dati all’interno del CRM

**La soppressione del punto di contatto** è simile alla rimozione del punto di contatto, ma i dati NON POSSONO essere segnalati nel dashboard ROI. Eventuali punti di contatto soppressi non saranno accessibili nel CRM o nell’individuazione. L’eliminazione assicurerà la corrispondenza tra i dati CRM e i dati di Discover. Comunemente utilizzato per perfezionare e specificare ulteriormente quali dati del punto di contatto desideri ricevere il credito di attribuzione.

Nell&#39;app [!DNL Marketo Measure], la sezione [!UICONTROL Touchpoint Settings] verrà suddivisa in quattro sezioni chiave. Ogni sezione sopprime o rimuove un diverso set di dati. Utilizza il tasto seguente per assicurarti che le tue regole eliminino o rimuovano i punti di contatto desiderati.

* Rimuovi punti di contatto dell&#39;acquirente da CRM
   * Usa questa sezione quando vuoi creare una regola che rimuova **dati Buyer Touchpoint** (i punti di contatto associati all&#39;individuo, non l&#39;opportunità) dal tuo **CRM**
* Elimina punti di contatto dell&#39;acquirente da CRM
   * Usa questa sezione quando vuoi creare una regola che rimuova **dati Buyer Touchpoint** (i punti di contatto associati all&#39;individuo, non l&#39;opportunità) dal tuo **CRM** e **Discover**
* Rimuovi punti di contatto di attribuzione buyer da CRM
   * Usa questa sezione quando vuoi creare una regola che rimuova i dati di **Buyer Attribution Touchpoint** (i punti di contatto associati all&#39;opportunità e ai ricavi) dal tuo **CRM**
* Elimina punti di contatto di attribuzione buyer da CRM
   * Usa questa sezione quando vuoi creare una regola che rimuova i dati di **Buyer Attribution Touchpoint** (i punti di contatto associati all&#39;opportunità e ai ricavi) dal tuo **CRM** e **Discover**

## Best practice {#best-practice}

Se stabilisci le regole di impostazione del punto di contatto per la prima volta o le stai solo esaminando per verificarne l’accuratezza, tieni presente le seguenti best practice.

* Stabilisci l’elenco dei dati da eliminare o rimuovere prima di creare le regole
* Identifica esattamente quali campi denoteranno chiaramente la regola o le regole che stai impostando
* Assicurati di aver specificato l’operatore corretto per la regola
* Utilizzando il tasto di cui sopra, assicurati che la regola sia specificata nella sezione corretta delle Impostazioni del punto di contatto
* Verifica le regole prima di implementarle replicando la logica della regola in un rapporto di punto di contatto acquirente in CRM per assicurarti che vengano eliminati o rimossi i dati desiderati

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

La revisione di [!UICONTROL Touchpoint Settings] è importante in quanto può modificare drasticamente i tuoi dati quando non sono definiti in modo appropriato. Come best practice, ti consigliamo di rivedere le impostazioni del punto di contatto almeno due volte all’anno. Si tratta di una semplice revisione visiva delle regole impostate nella sezione Impostazioni punto di contatto dell&#39;app [!DNL Marketo Measure]. Questa revisione ti consentirà di essere certo che le impostazioni del punto di contatto siano aggiornate e che sia possibile apportare le modifiche necessarie.

I motivi per rivedere le impostazioni di [!UICONTROL Touchpoint] includono...

* Fatturato del team marketing
* Aggiornamenti principali alla struttura del sito web
* Identificazione dei dati del punto di contatto che non sono più utili
   * Ogni volta che ti imbatti in dati punto di contatto che non dovresti ricevere il merito di attribuzione, le regole di [!DNL touchpoint suppression] sono la funzionalità per garantire la massima pulizia e precisione possibile dei tuoi dati.
* Modifiche ai campi utilizzati per definire le regole di soppressione o rimozione

>[!MORELIKETHIS]
>
>* [Panoramica sulla rimozione e l&#39;eliminazione dei punti di contatto](/help/channel-tracking-and-setup/touchpoint-removal-and-touchpoint-suppression.md)
>* [Perché i punti di contatto non devono mai essere eliminati](/help/channel-tracking-and-setup/why-you-should-never-delete-touchpoints.md)
>* [Punti di contatto buyer (BT) e Punti di contatto attribuzione buyer (BAT)](/help/configuration-and-setup/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md)

