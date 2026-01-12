---
description: Best practice per l'implementazione di  [!DNL Marketo Measure] JavaScript - [!DNL Marketo Measure]
title: Best practice per l'implementazione di [!DNL Marketo Measure] JavaScript
exl-id: 0359ad27-81e8-4902-a23a-49a5646a44d0
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# Procedure consigliate per l&#39;implementazione di [!DNL Marketo Measure] JavaScript {#best-practices-for-implementing-marketo-measure-javascript}

## Panoramica {#overview}

Il JavaScript [!DNL Marketo Measure] tiene traccia delle interazioni di marketing digitale dei visitatori Web ed è fondamentale per la possibilità di [!DNL Marketo Measure] di creare dati di punti di contatto online. Se il JavaScript [!DNL Marketo Measure] viene distribuito correttamente e in modo completo sull&#39;intero sito o sui siti, i dati della sessione raccolti produrranno dati accurati sui punti di contatto.

Le incoerenze nella distribuzione del JavaScript [!DNL Marketo Measure] causeranno interruzioni nei dati della sessione che possono causare quanto segue:

* Attribuzione canale/sottocanale errata
* Perdita di dati di origine
* Livelli elevati di traffico diretto errato
* Generazione rapporti non coerente

[!DNL Marketo Measure] JavaScript è un elemento fondamentale del tuo account [!DNL Marketo Measure] e la chiave del tuo successo.

## Best practice {#best-practice}

Quando si tratta di implementare e gestire il JavaScript [!DNL Marketo Measure], tieni presenti le seguenti best practice.

* Conferma che tutti i tuoi domini siano elencati nel tuo account [!DNL Marketo Measure]
   * In caso di dubbi relativi ai tuoi domini, contatta il supporto tecnico
* Distribuire JavaScript su TUTTE le pagine.
   * Se si inserisce JavaScript solo in determinate pagine, si verificheranno interruzioni nei dati della sessione che causeranno dati [!DNL Marketo Measure] errati
* Per un modulo sul sito da cui non si desidera creare punti di contatto, aggiungere lo script di esclusione [!DNL Marketo Measure]
   * Questo script di esclusioni garantirà che i dati della sessione [!DNL Marketo Measure] non vengano interrotti e che i dati di origine rimangano attivi
      * Di seguito sono riportati alcuni esempi di moduli comuni da eliminare:
         * Accessi cliente
         * Moduli per password dimenticate
         * Annulla iscrizione moduli
         * Moduli per la richiesta di lavoro
* Esaminare le sezioni &quot;Considerazioni aggiuntive&quot; e &quot;Forms per prestare maggiore attenzione&quot; della risorsa Aggiunta di script [!DNL Marketo Measure] elencata di seguito per verificare la presenza di scenari che potrebbero richiedere una gestione speciale

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

Anche se la configurazione del JavaScript [!DNL Marketo Measure] è coperta durante l&#39;implementazione iniziale, le modifiche al sito o al team che lo gestisce possono causare interruzioni nel monitoraggio di [!DNL Marketo Measure]. È consigliabile verificare che il JavaScript [!DNL Marketo Measure] sia distribuito correttamente e completamente una volta all&#39;anno. Inoltre, se la tua organizzazione dispone di qualsiasi tipo di documentazione sul protocollo di modifica per il sito Web, assicurati che sia presente una parte in cui viene spiegato che [!DNL Marketo Measure] JavaScript deve essere mantenuto/aggiunto a tutte le nuove pagine.

Altri motivi per cui potrebbe essere necessario rivedere la configurazione di JavaScript sono...

* Fatturato del team marketing
* Modifiche e aggiornamenti alla struttura del sito
* Migrazioni del sito
* Modifiche al dominio
* Acquisizione di altre aziende e delle loro proprietà web
