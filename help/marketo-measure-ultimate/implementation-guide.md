---
description: '[!DNL Marketo Measure] Guida all’implementazione di Ultimate: [!DNL Marketo Measure] - Documentazione del prodotto'
title: '''[!DNL Marketo Measure] Guida all’implementazione di Ultimate'
hide: true
hidefromtoc: true
feature: Integration, Tracking, Attribution
source-git-commit: d8c1962aaf1830970c4cbde4385d05ca4ad3139e
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 0%

---

# [!DNL Marketo Measure] Guida all’implementazione di Ultimate {#marketo-measure-ultimate-implementation-guide}

INTRODUZIONE FRASE

## Differenze principali nell’utilizzo di Ultimate rispetto ai livelli standard {#main-differences-when-using-ultimate-over-standard-tiers}

Importare dati B2B tramite AEP: gli addetti al marketing devono inserire i propri dati B2B (ad esempio account, opportunità, contatto, lead, campagna, membro della campagna, attività) tramite AEP. Acquisisci da quasi tutte le origini dati e da più origini dati dello stesso tipo per inserire tutti i dati per l’attribuzione.

* Utilizza con quasi tutte le CRM, non solo Salesforce e Dynamics.
* Connettere più istanze di CRM e/o istanze MAP a una singola istanza di Marketo Measure.
* Importa dati di registrazione e partecipazione a webinar di terze parti.

Le connessioni dirette CRM e di Marketo Engage non sono più disponibili per Ultimate.

* Ultimate non invia nuovamente i dati al CRM. I clienti possono utilizzare i dati provenienti dal data warehouse.
* Gli addetti al marketing continueranno a portare i dati di Ad Platform tramite connessioni dirette e il tracciamento delle attività web tramite JavaScript di Marketo Measure.

AEP verrà fornito agli utenti Ultimate. Se dispongono già di AEP, non verrà eseguito il provisioning di una nuova istanza.

* La versione di AEP fornita includerà tutti i connettori di origine, la modellazione dati dello schema, i set di dati, il servizio di query ad hoc e una destinazione solo per Marketo Measure.

Ulteriori informazioni su [Marketo Measure Ultimate](/help/marketo-measure-ultimate/marketo-measure-ultimate-overview.md).

## Schemi e set di dati {#schemas-and-datasets}

>[!NOTE]
>
>Estrai [Blocchi predefiniti di uno schema](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en#building-blocks-of-a-schema) per una panoramica di schemi, classi e gruppi di campi.

**Schema XDM = Classe + Gruppo di campi schema&#42;**

* I campi obbligatori non sono modificabili. I clienti possono creare e aggiungere campi personalizzati in base alle esigenze.
* Esempio di nome del campo basato sulla gerarchia: accountOrganization.annualRevenue.amount

&#42; _Uno schema comprende una classe e zero o più gruppi di campi dello schema. Ciò significa che è possibile comporre uno schema di set di dati senza utilizzare i gruppi di campi._

![](assets/marketo-measure-ultimate-implementation-guide-1.png)

[Panoramica sui set di dati](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html): tutti i dati acquisiti correttamente in AEP vengono mantenuti all’interno del Data Lake come set di dati. Un set di dati è un costrutto di archiviazione e gestione per una raccolta di dati, in genere una tabella, che contiene uno schema (colonne) e dei campi (righe).

## Creazione di uno schema {#creating-a-schema}

È consigliabile utilizzare un’utility di generazione automatica per creare 10 schemi B2B standard.

* Passaggi per scaricare e configurare l&#39;utility [si trova qui](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo-namespaces.html#set-up-b2b-namespaces-and-schema-auto-generation-utility).

Per chi ha un _**Adesione a CDP**_: per creare gli schemi, vai alla pagina Origini.

* Da un’origine, seleziona Aggiungi dati > Usa modelli

![](assets/marketo-measure-ultimate-implementation-guide-2.png)

* Seleziona un account e tutti i modelli B2B per creare 10 schemi B2B standard.

![](assets/marketo-measure-ultimate-implementation-guide-3.png)

## Flussi di dati {#dataflows}

[Panoramica dei flussi di dati](https://experienceleague.adobe.com/docs/experience-platform/dataflows/home.html)

**Passaggi per creare un flusso di dati:**

1. Selezionare un&#39;origine.
1. Seleziona un account esistente o creane uno esistente.
1. Selezionare un tipo di dati dall&#39;elenco dei tipi disponibili per l&#39;importazione dall&#39;origine.
1. Seleziona un set di dati esistente o creane uno nuovo.
1. Mappa i campi dall’origine allo schema.

   >[!NOTE]
   >
   >* Se mappi un tipo di schema a un altro identico, l’operazione verrà eseguita automaticamente.
   >* Potete anche importare la mappatura da un altro flusso nel sistema.
   >* È possibile mappare un campo di origine a più campi di destinazione, ma non è possibile eseguire l&#39;operazione opposta.
   >* Puoi creare campi calcolati (ad esempio, funzioni di mappatura della preparazione dati).

   >[!CAUTION]
   >
   >* Puoi modificare un flusso di dati, ma i dati non vengono recuperati quando viene modificata una mappatura.
   >* Se un campo obbligatorio è NULL, l’intero flusso verrà rifiutato.

   >[!NOTE]
   >
   >[Requisiti di integrità dei dati di Marketo Measure Ultimate](help/marketo-measure-ultimate/data-integrity-requirement.md)

1. Imposta una cadenza di caricamento dati.
1. Revisione e completamento.
1. Per informazioni sullo stato del flusso di dati, controlla la pagina &quot;Stato account&quot; nelle impostazioni dell’interfaccia utente Misura.

**Monitoraggio**

Origini > Pagina Flussi dati per controllare lo stato dei flussi dati

* Per visualizzare i dettagli di un set di dati, fai clic sul set di dati.
* Per visualizzare gli errori del flusso di dati, seleziona un flusso di dati, scegli un’esecuzione del flusso di dati e fai clic su &quot;Anteprima diagnostica errori&quot;.

## Ispezione dei dati {#data-inspection}

ExL: Requisiti di integrità dei dati di Marketo Measure Ultimate Questo documento include i campi obbligatori per ogni XDM e le query di ispezione. Sarà pubblicato in ExL. - È GIÀ TAGGATO IN ALTO - POST DI NUOVO???

Opzione 1: per eseguire le query direttamente dall’interfaccia utente, accedi alla scheda Query in Gestione dati.

![](assets/marketo-measure-ultimate-implementation-guide-4.png)

Opzione 2: [Scaricare e utilizzare PSQL](https://experienceleague.adobe.com/docs/experience-platform/query/clients/psql.html) (più veloce e affidabile)

## Attiva set di dati per Marketo Measure {#activate-dataset-for-marketo-measure}

Prima di iniziare, passa alla sezione &quot;Experience Platform > Mappatura sandbox&quot; nelle impostazioni dell’interfaccia utente Misura e mappa una sandbox.

>[!CAUTION]
>
>Una volta selezionata, questa opzione non può essere modificata.

1. In AEP, vai a &quot;Destinazioni > pagina Marketo Measure&quot; per esportare i set di dati.
1. Configurare la destinazione.
1. Attiva il set di dati.
1. Per informazioni sullo stato del flusso di dati, controlla la pagina &quot;Stato account&quot; nelle impostazioni dell’interfaccia utente Misura.

>[!NOTE]
>
>* I dati per una determinata entità (ad esempio, Conto) da una determinata origine possono essere inseriti in un solo set di dati. Ogni set di dati può essere incluso in un solo flusso di dati. Le violazioni arresteranno il flusso di dati in fase di esecuzione.
>* Elimina l’intera destinazione in AEP per eliminare i dati in Measure. La disattivazione interrompe solo le nuove esportazioni di dati e mantiene i dati precedenti.
>* La configurazione Misura avrà per lo più lo stesso aspetto, ma alcune parti, come Mappatura area di visualizzazione, avranno un aspetto diverso.
>* La generazione di un’esecuzione del flusso richiede alcune ore per un nuovo flusso di dati, che vengono quindi eseguiti a intervalli orari regolari.

In Measure, la valuta predefinita deve essere impostata nella sezione &quot;Valuta&quot;

* Se utilizzi più valute, lo schema del tasso di conversione della valuta deve essere popolato in AEP per consentirne la lettura e l’utilizzo per le conversioni.

**Mappatura stadio:**

Non importiamo automaticamente gli stadi dai dati utente, pertanto tutti gli stadi devono essere mappati manualmente.

* Gli utenti possono mappare gli stadi da sorgenti diverse.

![](assets/marketo-measure-ultimate-implementation-guide-5.png)

Se le fasi non sono mappate, il sistema non funzionerà perché non ci sarà nessun posto dove spostare i dati.

**Regole membro della campagna:**

È necessario scegliere un set di dati e impostare regole per ciascuno di essi.

**Regole degli eventi esperienza:**

È necessario scegliere un set di dati e selezionare i tipi di attività.

* Attività personalizzate non ancora supportate.
* Se il cliente ha attività che non rientrano nelle opzioni disponibili, consigliamo di classificarle come &quot;Momenti di interesse&quot; e di utilizzare campi personalizzati per distinguerli.

**Canali offline:**

* Non facciamo regole di mappatura dei canali specifiche per i set di dati, quindi sarebbe globale.
* Alla fine dobbiamo far corrispondere sia il tipo di campagna CRM che il canale, ma per ora, possiamo mappare il nome del canale a entrambi i campi come soluzione alternativa.
* **Regole del canale: i dati in backfill non contengono dati di transizione dell’area di visualizzazione.**

Le impostazioni dei punti di contatto e dei segmenti rimangono invariate.
