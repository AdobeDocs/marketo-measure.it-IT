---
description: 'Tecniche consigliate per le impostazioni dei punti di contatto: [!DNL Marketo Measure] - Documentazione del prodotto'
title: Tecniche consigliate per le impostazioni dei punti di contatto
exl-id: 01e314a6-e33d-45cd-aaa3-c212afec07d1
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---

# Tecniche consigliate per le impostazioni dei punti di contatto {#best-practices-for-touchpoint-settings}

## Panoramica {#overview}

La sezione Impostazioni punto di contatto della [!DNL Marketo Measure] l’app ti consente di impostare regole per eliminare o rimuovere punti di contatto dal tuo [!DNL Marketo Measure] dati e sistemi correlati. Queste regole possono aiutarti a isolare alcuni set di dati che non devono essere rappresentati nei dati dei punti di contatto dell’acquirente o che non desideri ricevere crediti di attribuzione senza disturbare il tracciamento e la raccolta dei dati.

**Rimozione punto di contatto** mezzi [!DNL Marketo Measure] eliminerà (ovvero rimuoverà) dal CRM tutti i punti di contatto che soddisfano i criteri della regola. I dati possono essere segnalati all&#39;interno del [!DNL Marketo Measure] Dashboard ROI (Discover), ma non viene visualizzato nel CRM. Comunemente utilizzato per alleviare lo stress sui limiti di archiviazione dei dati all&#39;interno del CRM

**Soppressione punto di contatto** È simile alla rimozione di un punto di contatto, ma i dati NON POSSONO essere segnalati all’interno del dashboard di ROI. Eventuali punti di contatto soppressi non saranno accessibili nel CRM o in Discover. La soppressione garantirà la corrispondenza dei dati CRM e dei dati Discover. Generalmente utilizzato per perfezionare e specificare ulteriormente quali dati dei punti di contatto si desidera ricevere il credito di attribuzione.

Nel tuo [!DNL Marketo Measure] La sezione Impostazioni punto di contatto dell’app verrà suddivisa in quattro sezioni chiave. Ogni sezione sopprime o rimuove un diverso set di dati. Utilizza la chiave qui sotto per assicurarti che le tue regole sopprimano o rimuovano i punti di contatto desiderati.

* Rimuovere i punti di contatto dell&#39;acquirente da CRM
   * Utilizzare questa sezione quando si desidera creare una regola che rimuoverà **Dati punto di contatto dell’acquirente** (i punti di contatto associati all’individuo, non all’opportunità) dal **CRM**
* Eliminare i punti di contatto dell&#39;acquirente da CRM
   * Utilizzare questa sezione quando si desidera creare una regola che rimuoverà **Dati punto di contatto dell’acquirente** (i punti di contatto associati all’individuo, non all’opportunità) dal **CRM** e **Scopri**
* Rimuovere i punti di contatto di attribuzione dell’acquirente da CRM
   * Utilizzare questa sezione quando si desidera creare una regola che rimuoverà **Punto di contatto dell’attribuzione dell’acquirente** i dati (i punti di contatto associati all’opportunità e ai ricavi) provenienti dal tuo **CRM**
* Eliminare i punti di contatto dell’attribuzione dell’acquirente da CRM
   * Utilizzare questa sezione quando si desidera creare una regola che rimuoverà **Punto di contatto dell’attribuzione dell’acquirente** i dati (i punti di contatto associati all’opportunità e ai ricavi) provenienti dal tuo **CRM** e **Scopri**

## Best practice {#best-practice}

Sia che stabiliate le regole di impostazione per punti di contatto per la prima volta sia che le rivediate per verificarne l’accuratezza, tenete presenti le seguenti best practice.

* Stabilire l’elenco di dati da eliminare o rimuovere prima di creare le regole
* Identifica esattamente quali campi indicano chiaramente la regola o le regole che stai impostando
* Assicurati di aver specificato l’operatore corretto per la regola
* Utilizzando la chiave di cui sopra, accertati che la regola sia specificata nella sezione corretta delle impostazioni dei punti di contatto
* Testa le regole prima di implementarle replicando la logica delle regole in un report Buyer touchpoint in CRM per assicurarti che stia sopprimendo o rimuovendo i dati desiderati

## Best practice per la manutenzione {#best-practice-for-maintenance}

La revisione delle impostazioni dei punti di contatto è importante in quanto possono modificare drasticamente i dati quando non sono definiti in modo appropriato. Come best practice, consulta le impostazioni dei punti di contatto almeno due volte all’anno. Questa è una semplice revisione visiva delle regole impostate nella sezione Impostazioni punto di contatto della [!DNL Marketo Measure] app. Questa revisione ti consentirà di verificare che le impostazioni dei punti di contatto siano aggiornate e che eventuali modifiche possano essere apportate di conseguenza.

Motivi per rivedere le impostazioni dei punti di contatto:

* Fatturato del team di marketing
* Aggiornamenti principali alla struttura del sito web
* Identificazione dei dati dei punti di contatto non più utili
   * Ogni volta che ti imbatti in dati di punti di contatto che ritieni non debbano ricevere crediti di attribuzione, le regole di soppressione dei punti di contatto sono la funzionalità per garantire che i dati siano il più puliti e precisi possibile.
* Modifiche ai campi utilizzati per definire le regole di eliminazione o rimozione

>[!MORELIKETHIS]
>
>* [Panoramica sulla rimozione e eliminazione dei punti di contatto](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md)
>* [Perché i punti di contatto non devono mai essere eliminati](/help/advanced-marketo-measure-features/touchpoint-settings/why-you-should-never-delete-touchpoints.md)
>* [Punti di contatto dell’acquirente (BT) rispetto ai punti di contatto dell’attribuzione dell’acquirente (BAT)](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md)

