---
description: '[!DNL Marketo Measure] Guida all''implementazione di Ultimate - [!DNL Marketo Measure]'
title: Guida all'implementazione di Ultimate [!DNL Marketo Measure]
feature: Integration, Tracking, Attribution
exl-id: 0c707875-5d05-49b9-b1ff-c3f7b711ebd1
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 2%

---


# Guida all&#39;implementazione di Ultimate [!DNL Marketo Measure] {#marketo-measure-ultimate-implementation-guide}

Questo articolo funge da guida all’implementazione per Marketo Measure Ultimate e fornisce passaggi chiari e informazioni approfondite per garantire un’integrazione e un utilizzo corretti.

## Differenze principali nell’utilizzo di Ultimate rispetto ai livelli standard {#main-differences-when-using-ultimate-over-standard-tiers}

Importare dati B2B tramite AEP: gli addetti al marketing devono inserire i propri dati B2B (ad esempio account, opportunità, contatto, lead, campagna, membro della campagna, attività) tramite AEP. Acquisisci da quasi tutte le origini dati e da più origini dati dello stesso tipo per inserire tutti i dati per l’attribuzione.

* Da utilizzare con quasi tutte le CRM, non solo con Salesforce e Dynamics.
* Connettere più istanze di CRM e/o istanze MAP a una singola istanza di Marketo Measure.
* Importa dati di registrazione e partecipazione a webinar di terze parti.

Le connessioni dirette CRM e Marketo Engage non sono più disponibili per Ultimate.

* Ultimate non invia nuovamente i dati al sistema CRM. I clienti possono utilizzare i dati provenienti dal data warehouse.
* Gli addetti al marketing continuano a importare dati di Ad Platform tramite connessioni dirette e a monitorare le attività web tramite JavaScript di Marketo Measure.

Agli utenti di Ultimate viene fornito AEP. Se dispongono già di AEP, non verrà eseguito il riprovisioning di una nuova istanza.

* La versione di AEP fornita include tutti i connettori di origine, la modellazione dati dello schema, i set di dati, il servizio di query ad hoc e una destinazione solo per Marketo Measure.

Ulteriori informazioni su [Marketo Measure Ultimate](/help/marketo-measure-ultimate/overview.md){target="_blank"}.

## Schemi e set di dati {#schemas-and-datasets}

>[!NOTE]
>Consulta [Blocchi predefiniti di uno schema](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=it#building-blocks-of-a-schema){target="_blank"} per una panoramica di schemi, classi e gruppi di campi.

**Schema XDM = Classe + Gruppo di campi schema&#42;**

* I campi obbligatori non sono modificabili. I clienti possono creare e aggiungere campi personalizzati in base alle esigenze.
* Esempio di nome del campo basato sulla gerarchia: accountOrganization.annualRevenue.amount

&#42; _Uno schema include una classe e zero o più gruppi di campi schema. Ciò significa che è possibile comporre uno schema di set di dati senza utilizzare i gruppi di campi._

![Diagramma struttura schema che mostra le relazioni tra classi e gruppi di campi](assets/marketo-measure-ultimate-implementation-guide-1.png)

[Panoramica sui set di dati](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html?lang=it){target="_blank"}: tutti i dati acquisiti correttamente in AEP vengono mantenuti all&#39;interno del Data Lake come set di dati. Un set di dati è un costrutto di archiviazione e gestione per una raccolta di dati, in genere una tabella, che contiene uno schema (colonne) e dei campi (righe).

## Creazione di uno schema {#creating-a-schema}

È consigliabile utilizzare un’utility di generazione automatica per creare dieci schemi B2B standard.

* I passaggi per scaricare e configurare l&#39;utilità [sono disponibili qui](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo-namespaces.html?lang=it#set-up-b2b-namespaces-and-schema-auto-generation-utility){target="_blank"}.

Per coloro che dispongono di un _&#x200B;**diritto CDP**&#x200B;_: crea gli schemi dalla pagina Origini.

* Da un’origine, seleziona Aggiungi dati > Usa modelli

![Pagina Origini con opzioni Aggiungi dati e Usa modelli](assets/marketo-measure-ultimate-implementation-guide-2.png)

* Seleziona un account e tutti i modelli B2B per creare dieci schemi B2B standard.

![Selezione di modelli che mostra i modelli di schema B2B per la configurazione account](assets/marketo-measure-ultimate-implementation-guide-3.png)

## Flussi di dati {#dataflows}

>[!IMPORTANT]
>Quando aggiungi un nuovo set di dati, ti consigliamo di creare un flusso invece di utilizzarne uno esistente.

[Panoramica dei flussi di dati](https://experienceleague.adobe.com/docs/experience-platform/dataflows/home.html?lang=it){target="_blank"}

**Passaggi per creare un flusso di dati:**

1. Seleziona un Source.
1. Seleziona un account esistente o creane uno esistente.
1. Selezionare un tipo di dati dall&#39;elenco dei tipi disponibili da importare da Source.
1. Seleziona un set di dati esistente o creane uno.
1. Mappa i campi da Source allo schema.

   >[!NOTE]
   > Se mappi un tipo di schema a un altro identico, l’operazione viene eseguita automaticamente.
   > Potete anche importare la mappatura da un altro flusso nel sistema.
   > È possibile mappare un campo Source a più campi di destinazione, ma non è possibile eseguire l&#39;operazione opposta.
   > È possibile creare campi calcolati ([funzioni di mappatura della preparazione dati](https://experienceleague.adobe.com/docs/experience-platform/data-prep/functions.html?lang=it){target="_blank"}).

   >[!CAUTION]
   > Puoi modificare un flusso di dati, ma i dati non vengono recuperati quando viene modificata una mappatura.
   > Se un campo obbligatorio è NULL, l&#39;intero flusso viene rifiutato.

   >[!NOTE]
   >[Requisiti di integrità dei dati di Marketo Measure Ultimate](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}

1. Imposta una cadenza di caricamento dati.
1. Revisione e completamento.
1. Per informazioni sullo stato del flusso di dati, controlla la pagina &quot;Stato account&quot; nelle impostazioni dell’interfaccia utente Misura.

**Monitoraggio:**

Origini > Pagina Flussi dati per controllare lo stato dei flussi dati

* Per visualizzare i dettagli di un set di dati, fai clic sul set di dati.
* Per visualizzare gli errori del flusso di dati, seleziona un flusso di dati, scegli un’esecuzione del flusso di dati e fai clic su &quot;Anteprima diagnostica errori&quot;.

## Ispezione dei dati {#data-inspection}

Opzione 1: per eseguire le query direttamente dall’interfaccia utente, accedi alla scheda Query in Gestione dati.

![Scheda Query in Gestione dati che mostra l&#39;interfaccia query](assets/marketo-measure-ultimate-implementation-guide-4.png)

Opzione 2: [Scaricare e utilizzare PSQL](https://experienceleague.adobe.com/docs/experience-platform/query/clients/psql.html?lang=it){target="_blank"} (più veloce e affidabile).

## Attiva set di dati per Marketo Measure {#activate-dataset-for-marketo-measure}

Prima di iniziare, passa alla sezione &quot;Experience Platform > Mappatura sandbox&quot; nelle impostazioni dell’interfaccia utente Misura e mappa una sandbox.

>[!CAUTION]
>Una volta selezionata, questa opzione non può essere modificata.

1. In AEP, vai a &quot;Destinazioni > pagina Marketo Measure&quot; per esportare i set di dati.
1. Configurare la destinazione.
1. Attiva il set di dati.
1. Per informazioni sullo stato del flusso di dati, controlla la pagina &quot;Stato account&quot; nelle impostazioni dell’interfaccia utente Misura.

>[!NOTE]
> Si consiglia di includere un solo set di dati per flusso di dati.
> I dati di una determinata entità (ad esempio, Conto) da una determinata origine possono essere inseriti in un solo set di dati. Ogni set di dati può essere incluso in un solo flusso di dati. Le violazioni arrestano il flusso di dati in fase di esecuzione.
> Elimina l’intera destinazione in AEP per eliminare i dati in Measure. La disabilitazione interrompe le nuove esportazioni di dati e mantiene i dati precedenti.
> La configurazione Misura avrà per lo più lo stesso aspetto, ma alcune parti, come Mappatura area di visualizzazione, avranno un aspetto diverso.
> La generazione di un’esecuzione del flusso richiede alcune ore per un nuovo flusso di dati, che vengono quindi eseguiti a intervalli orari regolari.

In Measure, la valuta predefinita deve essere impostata nella sezione &quot;Valuta&quot;.

* Se utilizzi più valute, lo schema del tasso di conversione della valuta deve essere popolato in AEP per consentirne la lettura e l’utilizzo per le conversioni.

**Mappatura fase:**

Non importiamo automaticamente gli stadi dai dati utente, pertanto tutti gli stadi devono essere mappati manualmente.

* Gli utenti possono mappare gli stadi da sorgenti diverse.

![Interfaccia di mappatura stadio che mostra la configurazione dell&#39;area di visualizzazione da più origini](assets/marketo-measure-ultimate-implementation-guide-5.png)

Se le fasi non sono mappate, il sistema non funzionerà perché non ci sarà nessun posto dove spostare i dati.

Se sei un cliente Marketo Measure Ultimate e hai impostato l&#39;oggetto dashboard predefinito come contatto, non utilizzare i due campi seguenti specifici per lead ([ulteriori informazioni qui](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).

* b2b.personStatus
* b2b.isConverted

**Regole membro campagna:**

Scegli un set di dati e imposta le regole per ciascuno di essi.

**Regole eventi esperienza:**

Scegli un set di dati e seleziona i tipi di attività.

* Attività personalizzate non ancora supportate.
* Se il cliente ha attività che non rientrano nelle opzioni disponibili, consigliamo di classificarle come &quot;Momenti di interesse&quot; e di utilizzare campi personalizzati per distinguerli.

**Canali offline:**

* Non facciamo regole di mappatura dei canali specifiche per i set di dati, quindi sarebbe globale.
* Alla fine dobbiamo trovare una corrispondenza tra Tipo di campagna CRM e Canale, ma per ora, possiamo mappare il nome del canale su entrambi i campi come soluzione alternativa.
* **Regole canale: i dati in backfill non contengono dati di transizione fase.**

Le impostazioni dei punti di contatto e dei segmenti rimangono invariate.
