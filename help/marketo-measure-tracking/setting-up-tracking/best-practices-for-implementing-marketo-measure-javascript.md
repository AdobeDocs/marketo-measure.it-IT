---
description: Best practice per l’implementazione [!DNL Marketo Measure] JavaScript - [!DNL Marketo Measure] - Documentazione del prodotto
title: Best practice per l’implementazione [!DNL Marketo Measure] JavaScript
exl-id: 0359ad27-81e8-4902-a23a-49a5646a44d0
source-git-commit: cf144eb4bc9282ae6a260acd3735f24644292a19
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Best practice per l’implementazione [!DNL Marketo Measure] JavaScript {#best-practices-for-implementing-marketo-measure-javascript}

## Panoramica {#overview}

La [!DNL Marketo Measure] JavaScript tiene traccia delle interazioni di marketing digitale dei visitatori web ed è fondamentale per [!DNL Marketo Measure] possibilità di creare dati per punti di contatto online. Avere [!DNL Marketo Measure] JavaScript implementato correttamente e in modo completo nell’intero sito/i garantirà che i dati di sessione raccolti producano dati precisi sui punti di contatto.

Incongruenze nella distribuzione [!DNL Marketo Measure] JavaScript causerà interruzioni nei dati della sessione che possono causare quanto segue:

* Attribuzione canale/canale errata
* Perdita di dati di origine
* Elevati livelli di traffico diretto errato
* Reporting incoerente

[!DNL Marketo Measure] JavaScript è un elemento fondamentale del tuo [!DNL Marketo Measure] account e chiave per il tuo successo!

## Best practice {#best-practice}

Quando si tratta di implementare e gestire il [!DNL Marketo Measure] JavaScript, considera le seguenti best practice.

* Conferma che tutti i domini siano elencati nella [!DNL Marketo Measure] account
   * Se hai dei dubbi sui tuoi domini, contatta il supporto
* Distribuisci JavaScript su TUTTE le pagine.
   * Il posizionamento di JavaScript solo su determinate pagine causerà interruzioni nei dati della sessione che causeranno errori [!DNL Marketo Measure] dati
* Per un modulo sul sito da cui non desideri creare punti di contatto, assicurati di aggiungere il [!DNL Marketo Measure] Script di esclusione
   * Questo script di esclusione assicura che la [!DNL Marketo Measure] i dati di sessione non verranno interrotti e i dati di origine rimarranno in vigore
      * Esempi comuni di moduli da eliminare sono:
         * Accesso cliente
         * Moduli Password dimenticata
         * Annulla sottoscrizione moduli
         * Moduli di domanda di carriera
* Rivedi le sezioni &quot;Considerazioni aggiuntive&quot; e &quot;Forms a cui prestare ulteriore attenzione&quot; della sezione Aggiunta di [!DNL Marketo Measure] Risorsa di script elencata di seguito per verificare eventuali scenari che potrebbero richiedere una gestione speciale

## Best practice per la manutenzione {#best-practice-for-maintenance}

Durante la configurazione del [!DNL Marketo Measure] JavaScript viene trattato durante l&#39;implementazione iniziale, le modifiche al sito o al team che lo gestisce possono causare interruzioni [!DNL Marketo Measure] tracciamento. Ti consigliamo di confermare la [!DNL Marketo Measure] JavaScript viene distribuito correttamente e in modo completo una volta all’anno. Inoltre, se la tua organizzazione dispone di qualsiasi tipo di documentazione relativa al protocollo di modifica per il sito web, assicurati che sia presente una parte che spieghi che [!DNL Marketo Measure] JavaScript deve essere mantenuto/aggiunto a tutte le nuove pagine.

Altri motivi per cui potrebbe innescare una revisione della configurazione JavaScript includono..

* Fatturato del team di marketing
* Modifiche e aggiornamenti alla struttura del sito
* Migrazioni siti
* Modifiche al dominio
* Acquisizione di altre società e delle loro proprietà web
