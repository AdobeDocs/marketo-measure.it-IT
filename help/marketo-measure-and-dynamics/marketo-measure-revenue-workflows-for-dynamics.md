---
description: Flussi di lavoro per allineare i ricavi di Dynamics e i campi data di chiusura per i rapporti di Marketo Measure
title: '[!DNL Marketo Measure] flussi di lavoro ricavi per Dynamics'
exl-id: 0e64201a-bc65-4a6d-9192-09c14c810c4a
feature: Microsoft Dynamics
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# [!DNL Marketo Measure] flussi di lavoro ricavi per Dynamics {#marketo-measure-revenue-workflows-for-dynamics}

## Parte 1: Ricavi stimati rispetto ai ricavi effettivi {#part-estimated-revenue-vs-actual-revenue}

[!DNL Marketo Measure] punta a un campo di ricavo standard preconfigurato (Ricavo effettivo), ma Dynamics dispone di due campi di ricavo standard: Ricavo effettivo e Ricavo stimato. Affinché i ricavi della pipeline siano disponibili nel pannello di controllo Individua, sono necessari un campo personalizzato e un flusso di lavoro per acquisire l’importo corretto dal campo Ricavo stimato o Ricavo effettivo, a seconda che l’opportunità sia aperta o chiusa (acquisita).

Passaggio 1: creare un campo importo opportunità personalizzato in Dynamics

>[!NOTE]
>
>Tutti i campi Ricavo Dynamics hanno un campo base e un campo regolare. Ignorare il campo di base.

Passaggio 2: creare un flusso di lavoro che aggiorni sia il campo importo opportunità personalizzato creato nel passaggio 1 che il campo importo opportunità [!DNL Marketo Measure].

>[!NOTE]
>
>Non è possibile puntare al campo Importo opportunità [!DNL Marketo Measure] (bizible2_bizible_OPPORTUNITY_amount) in Discover con account Dynamics. I clienti Dynamics devono creare un campo quantità opportunità personalizzato per [!DNL Marketo Measure] per puntare a in Discover. Una volta completato, il cliente deve creare un flusso di lavoro che aggiorna **entrambi** l&#39;importo dell&#39;opportunità [!DNL Marketo Measure] (bizible2_bizible_OPPORTUNITY_amount) **e** il campo dell&#39;importo dell&#39;opportunità personalizzato. Il campo Importo opportunità [!DNL Marketo Measure] viene fornito con il pacchetto, ma è necessario creare un campo personalizzato.

Istruzioni flusso di lavoro importo:

**FLUSSO DI LAVORO #1**: Opportunità - Aggiorna campo importo opportunità [!DNL Marketo Measure] e campo personalizzato = Ricavo stimato

Questo flusso di lavoro viene eseguito sulle opportunità aperte ogni volta che il Ricavo stimato cambia e aggiorna il campo Importo opportunità [!DNL Marketo Measure] e il campo personalizzato in modo che corrispondano al campo Ricavo stimato. Il flusso di lavoro deve essere impostato per essere eseguito in tempo reale, ma può anche essere eseguito &quot;on demand&quot; per aggiornare le opportunità aperte.

Fornisci il contatto [!DNL Marketo Measure] con il nome del campo personalizzato dell&#39;importo dell&#39;opportunità. Aggiorna le impostazioni dell&#39;opportunità di app [!DNL Marketo Measure] per includere il nome del campo dell&#39;importo dell&#39;opportunità personalizzato. Questo comunica a Scopri quale campo utilizzare nel reporting.

**FLUSSO DI LAVORO #2**: Opportunità - Aggiorna campo importo opportunità [!DNL Marketo Measure] e campo personalizzato = Reddito effettivo

Questo flusso di lavoro viene avviato quando un utente chiude un&#39;opportunità e aggiorna il campo Importo opportunità [!DNL Marketo Measure] e il campo personalizzato con la retribuzione effettiva aggiunta al modulo Chiusura opportunità prima che l&#39;opportunità si blocchi come chiusa.

## Parte 2: data di chiusura stimata rispetto alla data di chiusura effettiva {#part-estimated-close-date-vs-actual-close-date}

I dati sui ricavi della pipeline non sono immediatamente disponibili nel dashboard perché, per impostazione predefinita, in Dynamics sono disponibili due campi data di chiusura scorte: Data di chiusura stimata e Data di chiusura effettiva. [!DNL Marketo Measure] può puntare a un solo campo data di chiusura nel dashboard e punta alla data di chiusura effettiva.

Se nel campo Data di chiusura effettiva non sono presenti dati per le opportunità aperte, nel dashboard non sarà presente alcun dato. Detto questo, è necessario un flusso di lavoro basato sulla fase dell’opportunità per supportare entrambi i campi data.

1. Crea campo data di chiusura personalizzato nell&#39;oggetto opportunità ([!DNL Marketo Measure] data di chiusura personalizzata).
1. Creare un flusso di lavoro per aggiornare il campo Data di chiusura personalizzata [!DNL Marketo Measure] con la data a partire dalla Data di chiusura stimata o dalla Data di chiusura effettiva, a seconda che l&#39;opportunità sia aperta o chiusa (il flusso di lavoro deve essere salvato per essere eseguito in tempo reale, ma deve essere eseguito &quot;su richiesta&quot; almeno una volta per aggiornare tutte le opzioni aperte correnti).
1. Verifica il funzionamento del flusso di lavoro.
1. Il cliente deve fornire il nome API data di chiusura personalizzata a [!DNL Marketo Measure].
1. [!DNL Marketo Measure] per aggiornare le impostazioni dell&#39;app [!DNL Marketo Measure] in modo che puntino al campo Data di chiusura personalizzata [!DNL Marketo Measure] nel dashboard.

   Al termine dei passaggi precedenti, eseguire i flussi di lavoro per aggiornare sia il campo personalizzato Importo operazione [!DNL Marketo Measure] che il campo Data chiusura personalizzata [!DNL Marketo Measure] sulle opportunità storiche per riflettere i dati corretti. Questo probabilmente cambierà i campi di attivazione/disattivazione modificati; pertanto, verifica con il team se si verificano problemi.

Per aggiornare le opportunità chiuse...

1. Isolare le opportunità chiuse dalla data di inizio [!DNL Marketo Measure] fino a quando il flusso di lavoro non è attivo. Questo è il gruppo di opportunità storiche da aggiornare tramite il flusso di lavoro.
1. Esporta tutti i record in Excel.
1. Apri un file Excel e abilita il contenuto.
1. Copia i dati della data di chiusura effettiva alla data di chiusura personalizzata [!DNL Marketo Measure].
1. Copiare i dati dei ricavi effettivi nell&#39;importo dell&#39;opportunità personalizzato [!DNL Marketo Measure] **e** [!DNL Marketo Measure] (sono disponibili due campi).
1. Salva file.
1. Importa file. Dynamics lo riconoscerà come file con record esistenti da aggiornare.
1. Verifica la presenza di errori nel file di importazione.

>[!NOTE]
>
>I flussi di lavoro descritti in questo documento sono solo uno dei modi per aggiornare i campi in modo che [!DNL Marketo Measure] possa mostrare i dati corretti in Discover. Se si dispone di un altro modo di eseguire la stessa attività, è possibile andare per esso. Fondamentalmente ciò di cui abbiamo bisogno da loro è un qualche tipo di flusso di lavoro che esegua le seguenti operazioni:
>
> * Se Opp = Apri, aggiorna il campo della data di chiusura personalizzata, il campo dell&#39;importo opp personalizzato e il campo dell&#39;importo opp [!DNL Marketo Measure] in modo che corrispondano rispettivamente alla data di chiusura stimata e alla retribuzione stimata.
> * Se Opp = Closed Won, aggiornare il campo della data di chiusura personalizzato, il campo dell&#39;importo opp personalizzato e il campo dell&#39;importo opp [!DNL Marketo Measure] in modo che corrispondano rispettivamente alla data di chiusura effettiva e alla retribuzione effettiva.
