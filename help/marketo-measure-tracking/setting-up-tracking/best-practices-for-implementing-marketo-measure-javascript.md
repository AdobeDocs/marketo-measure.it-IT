---
description: Best practice per l’implementazione [!DNL Marketo Measure] JavaScript - [!DNL Marketo Measure] - Documentazione del prodotto
title: Best practice per l’implementazione [!DNL Marketo Measure] JavaScript
exl-id: 0359ad27-81e8-4902-a23a-49a5646a44d0
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Best practice per l’implementazione [!DNL Marketo Measure] JavaScript {#best-practices-for-implementing-marketo-measure-javascript}

## Panoramica {#overview}

Il [!DNL Marketo Measure] JavaScript tiene traccia delle interazioni di marketing digitale dei visitatori Web ed è fondamentale per [!DNL Marketo Measure] possibilità di creare dati di punti di contatto online. Avere [!DNL Marketo Measure] JavaScript implementato correttamente e in modo completo nell’intero sito o negli interi siti garantirà che i dati della sessione raccolti producano dati dei punti di contatto accurati.

Le incoerenze nell&#39;attuazione del [!DNL Marketo Measure] JavaScript causerà interruzioni nei dati della sessione che possono causare i seguenti effetti:

* Attribuzione canale/sottocanale errata
* Perdita di dati di origine
* Livelli elevati di traffico diretto errato
* Generazione rapporti non coerente

[!DNL Marketo Measure] JavaScript è un elemento fondamentale della [!DNL Marketo Measure] account e chiave per il tuo successo.

## Best practice {#best-practice}

Quando si tratta di implementare e gestire [!DNL Marketo Measure] JavaScript, considera le seguenti best practice.

* Conferma che tutti i tuoi domini siano elencati nel tuo [!DNL Marketo Measure] account
   * In caso di dubbi sui tuoi domini, contatta il supporto tecnico
* Distribuisci JavaScript su TUTTE le pagine.
   * L’inserimento di JavaScript solo su determinate pagine causerà interruzioni nei dati della sessione che causeranno errori [!DNL Marketo Measure] dati
* Per un modulo sul sito da cui non desideri creare punti di contatto, assicurati di aggiungere la [!DNL Marketo Measure] Escludi script
   * Questo script di esclusioni garantirà che [!DNL Marketo Measure] i dati della sessione non verranno interrotti e i dati di origine rimarranno attivi
      * Di seguito sono riportati alcuni esempi di moduli comuni da eliminare:
         * Accessi cliente
         * Moduli per password dimenticate
         * Annulla iscrizione moduli
         * Moduli per la richiesta di lavoro
* Consultate le sezioni &quot;Considerazioni aggiuntive&quot; e &quot;Forms per prestare maggiore attenzione&quot; nella sezione Aggiunta di [!DNL Marketo Measure] Script della risorsa elencata di seguito per verificare la presenza di scenari che potrebbero richiedere una gestione speciale

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

Durante l&#39;impostazione di [!DNL Marketo Measure] JavaScript è coperto durante l’implementazione iniziale; le modifiche al sito o al team che lo gestisce possono causare interruzioni in [!DNL Marketo Measure] tracciamento. Si consiglia di confermare [!DNL Marketo Measure] JavaScript viene distribuito correttamente e completamente una volta all’anno. Inoltre, se la tua organizzazione dispone di qualsiasi tipo di documentazione sul protocollo di modifica per il sito web, assicurati che sia presente una parte in cui viene spiegato che [!DNL Marketo Measure] JavaScript deve essere mantenuto/aggiunto a tutte le nuove pagine.

Altri motivi per cui potrebbe essere necessario rivedere la configurazione JavaScript sono...

* Fatturato del team marketing
* Modifiche e aggiornamenti alla struttura del sito
* Migrazioni del sito
* Modifiche al dominio
* Acquisizione di altre aziende e delle loro proprietà web
