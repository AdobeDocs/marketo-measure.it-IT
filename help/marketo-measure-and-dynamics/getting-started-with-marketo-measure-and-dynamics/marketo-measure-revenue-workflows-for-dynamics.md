---
unique-page-id: 37356132
description: "[!DNL Marketo Measure] Flussi di lavoro sui ricavi per Dynamics - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] Flussi di lavoro sui ricavi per Dynamics"
exl-id: 0e64201a-bc65-4a6d-9192-09c14c810c4a
source-git-commit: 54337a0a65b79d80ebeae6531f5e92f4f48721a7
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---

# [!DNL Marketo Measure] Flussi di lavoro sui ricavi per Dynamics {#marketo-measure-revenue-workflows-for-dynamics}

## Parte 1: Ricavi stimati e ricavi effettivi {#part-estimated-revenue-vs-actual-revenue}

[!DNL Marketo Measure] punta a un campo ricavo standard pronto all’uso (Entrate effettive), ma Dynamics ha due campi ricavo standard: Ricavi effettivi e ricavi stimati. Per rendere disponibili i ricavi della pipeline nel dashboard di Discover, sono necessari un campo personalizzato e un flusso di lavoro per acquisire l’importo corretto dal campo Ricavo stimato o Ricavo effettivo a seconda che l’opportunità sia aperta o chiusa (vinta).

Passaggio 1: Crea un campo personalizzato per l’importo delle opportunità in Dynamics

>[!NOTE]
>
>Tutti i campi delle entrate di Dynamics hanno un campo base e un campo regolare. Ignora il campo base.

Passaggio 2: Crea un flusso di lavoro che aggiorna sia il campo dell’importo delle opportunità personalizzate creato nel passaggio 1 che il [!DNL Marketo Measure] Campo Importo opportunità.

>[!NOTE]
>
>Non possiamo indicare [!DNL Marketo Measure] Campo Importo opportunità (bizible2_bizible_opportunità_amount) in Scopri con gli account Dynamics. I clienti Dynamics devono creare un campo di importo opportunità personalizzato per [!DNL Marketo Measure] puntare a Discover. Una volta completato, il cliente deve creare un flusso di lavoro che esegua gli aggiornamenti **entrambi** la [!DNL Marketo Measure] Importo opportunità (bizible2_bizible_opportunità_amount) **e** il campo dell&#39;importo opportunità personalizzato. La [!DNL Marketo Measure] Il campo Importo opportunità viene fornito con il pacchetto, ma è necessario creare un campo personalizzato.

Istruzioni per il flusso di lavoro dell&#39;importo:

**FLUSSO DI LAVORO N. 1**: Opportunità - Aggiornamento [!DNL Marketo Measure] Campo importo opportunità e campo personalizzato = ricavi stimati

Questo flusso di lavoro viene eseguito sulle opportunità aperte ogni volta che le modifiche ai Ricavi stimati vengono apportate e aggiornerà il [!DNL Marketo Measure] Il campo Importo opportunità e il campo personalizzato devono corrispondere al campo Ricavo stimato . Il flusso di lavoro deve essere impostato per l’esecuzione di &quot;Real Time&quot; (Tempo reale), ma può anche essere eseguito &quot;on demand&quot; per aggiornare le opportunità aperte.

Fornisci le [!DNL Marketo Measure] punto di contatto con il nome del campo dell&#39;importo opportunità personalizzato. Aggiorna [!DNL Marketo Measure] Impostazioni opportunità app per includere il nome del campo di importo opportunità personalizzato. Questo ti dirà Scopri quale campo utilizzare nel reporting.

**FLUSSO DI LAVORO 2**: Opportunità - Aggiornamento [!DNL Marketo Measure] Campo importo opportunità e campo personalizzato = ricavi effettivi

Questo flusso di lavoro viene eseguito in tempo reale. Viene attivato quando un utente chiude un&#39;opportunità e aggiorna l&#39; [!DNL Marketo Measure] Campo Importo opportunità e campo personalizzato con Ricavo effettivo aggiunto al modulo Chiudi opportunità prima che l&#39;opportunità venga bloccata come chiusa.

## Parte 2: Data di chiusura stimata rispetto a Data di chiusura effettiva {#part-estimated-close-date-vs-actual-close-date}

I dati predefiniti sui ricavi della pipeline non saranno disponibili nel dashboard perché, per impostazione predefinita, Dynamics dispone di due campi data di chiusura scorte: Data di chiusura stimata e Data di chiusura effettiva. [!DNL Marketo Measure] può puntare solo a un campo data di chiusura nel dashboard e attualmente stiamo puntando alla data di chiusura effettiva.

Se le opportunità aperte non contengono dati nel campo Data di chiusura effettiva, non verranno visualizzati dati nel dashboard per le opportunità aperte. Detto questo, è necessario un flusso di lavoro basato sulla fase delle opportunità per supportare entrambi i campi data.

1. Crea campo data di chiusura personalizzato sull&#39;oggetto opportunità (ovvero [!DNL Marketo Measure] Data di chiusura personalizzata).
1. Crea un flusso di lavoro per aggiornare il [!DNL Marketo Measure] Campo Custom Close Date con la data dalla Data di chiusura stimata o dalla Data di chiusura effettiva, a seconda che l&#39;opportunità sia aperta o chiusa (il flusso di lavoro deve essere salvato per essere eseguito in tempo reale, ma deve essere eseguito &quot;su richiesta&quot; almeno una volta per aggiornare tutte le opzioni aperte correnti).
1. Verifica il flusso di lavoro e conferma il suo funzionamento.
1. Il cliente deve fornire il nome dell’API Custom Close Date a [!DNL Marketo Measure].
1. [!DNL Marketo Measure] per aggiornare [!DNL Marketo Measure] impostazioni dell’app per puntare a [!DNL Marketo Measure] Campo personalizzato Data di chiusura nel dashboard.

   Al completamento dei passaggi precedenti, sarà necessario eseguire flussi di lavoro per aggiornare sia il [!DNL Marketo Measure] Campo Importo Opp e [!DNL Marketo Measure] Campo Custom Close Date (Data di chiusura personalizzata) sulle opportunità storiche per riflettere i dati corretti. Questo cambierà probabilmente i campi Attivato/Da modificati, quindi dovrai verificare con il tuo team se questo presenta dei problemi.

Per aggiornare le opportunità chiuse...

1. Isolare le opportunità chiuse dal tuo [!DNL Marketo Measure] avvia la data di attivazione del flusso di lavoro. Questo è il gruppo di opportunità storiche che dovrai aggiornare tramite il flusso di lavoro.
1. Esporta tutti i record in Excel.
1. Apri il file Excel e abilita il contenuto.
1. Copia dati di chiusura effettiva in [!DNL Marketo Measure] Data di chiusura personalizzata.
1. Copia dati ricavi effettivi in [!DNL Marketo Measure] Importo opportunità personalizzato **e** [!DNL Marketo Measure] Importo opportunità (sono disponibili due campi).
1. Salva il file.
1. Importa file. Dynamics riconoscerà questo file come un file con record esistenti da aggiornare.
1. Verifica la presenza di errori nel file di importazione.

>[!NOTE]
>
>I flussi di lavoro descritti in questo documento sono solo uno dei modi per aggiornare i campi in modo che [!DNL Marketo Measure] può mostrare i dati corretti in Discover. Se hai un altro modo di eseguire lo stesso compito, puoi farlo. In sostanza, ciò di cui abbiamo bisogno è un tipo di flusso di lavoro che esegua quanto segue:
>
> * Se Opp = Apri, aggiorna il campo personalizzato per la data di chiusura, il campo personalizzato per l&#39;importo dell&#39;opp e [!DNL Marketo Measure] campo dell&#39;importo dell&#39;opp uguale rispettivamente a Data di chiusura stimata e Ricavo stimato.
> * Se Opp = chiuso, aggiorna il campo della data di chiusura personalizzato, il campo dell&#39;importo dell&#39;opp personalizzato e [!DNL Marketo Measure] campo importo opp uguale rispettivamente a Data di chiusura effettiva e Ricavo effettivo.

