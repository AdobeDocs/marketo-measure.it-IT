---
unique-page-id: 37356132
description: "[!DNL Marketo Measure] Flussi di lavoro ricavi per Dynamics - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] Flussi di lavoro dei ricavi per Dynamics"
exl-id: 0e64201a-bc65-4a6d-9192-09c14c810c4a
feature: Microsoft Dynamics
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---

# [!DNL Marketo Measure] Flussi di lavoro dei ricavi per Dynamics {#marketo-measure-revenue-workflows-for-dynamics}

## Parte 1: Ricavi stimati rispetto ai ricavi effettivi {#part-estimated-revenue-vs-actual-revenue}

[!DNL Marketo Measure] punta a un campo di ricavo standard preconfigurato (Ricavo effettivo), ma Dynamics dispone di due campi di ricavo standard: Ricavo effettivo e Ricavo stimato. Affinché i ricavi della pipeline siano disponibili nel pannello di controllo Individua, sono necessari un campo personalizzato e un flusso di lavoro per acquisire l’importo corretto dal campo Ricavo stimato o Ricavo effettivo, a seconda che l’opportunità sia aperta o chiusa (acquisita).

Passaggio 1: creare un campo importo opportunità personalizzato in Dynamics

>[!NOTE]
>
>Tutti i campi Ricavo Dynamics hanno un campo base e un campo regolare. Ignorare il campo di base.

Passaggio 2: creare un flusso di lavoro che aggiorni sia il campo quantità opportunità personalizzato creato nel passaggio 1 che il [!DNL Marketo Measure] Campo Importo opportunità.

>[!NOTE]
>
>Non è possibile indicare [!DNL Marketo Measure] Campo Importo opportunità (bizible2_bizible_OPPORTUNITY_amount) in Discover con account Dynamics. I clienti Dynamics devono creare un campo importo opportunità personalizzato per [!DNL Marketo Measure] per puntare a in Discover. Una volta completato, il cliente deve creare un flusso di lavoro che si aggiorna **entrambi** il [!DNL Marketo Measure] Importo opportunità (bizible2_bizible_option_amount) **e** il campo importo opportunità personalizzato. Il [!DNL Marketo Measure] Il campo Importo opportunità viene fornito con il pacchetto, ma è necessario creare un campo personalizzato.

Istruzioni flusso di lavoro importo:

**#1 FLUSSO DI LAVORO**: Opportunità - Aggiornamento [!DNL Marketo Measure] Campo Importo Opportunità E Campo Personalizzato = Ricavi Stimati

Questo flusso di lavoro viene eseguito su opportunità aperte ogni volta che cambia la Retribuzione stimata e aggiorna la [!DNL Marketo Measure] Campo Importo opportunità e campo personalizzato per equivalere al campo Ricavo stimato. Il flusso di lavoro deve essere impostato per essere eseguito in tempo reale, ma può anche essere eseguito &quot;on demand&quot; per aggiornare le opportunità aperte.

Fornisci [!DNL Marketo Measure] punto di contatto con il nome del campo importo opportunità personalizzato. Aggiorneranno il [!DNL Marketo Measure] Impostazioni opportunità app per includere il nome del campo quantità opportunità personalizzato. Questo dirà a Scopri quale campo utilizzare nel reporting.

**#2 FLUSSO DI LAVORO**: Opportunità - Aggiornamento [!DNL Marketo Measure] Campo importo opportunità e campo personalizzato = retribuzione effettiva

Questo flusso di lavoro viene eseguito in tempo reale. Viene avviato quando un utente chiude un’opportunità e aggiorna il [!DNL Marketo Measure] Il campo Importo opportunità e il campo personalizzato con la Retribuzione effettiva aggiunti alla maschera Chiusura opportunità prima che l’opportunità si blocchi come chiusa.

## Parte 2: data di chiusura stimata rispetto alla data di chiusura effettiva {#part-estimated-close-date-vs-actual-close-date}

I dati sui ricavi della pipeline non saranno disponibili nel dashboard perché, per impostazione predefinita, in Dynamics sono disponibili due campi data di chiusura scorte: Data di chiusura stimata e Data di chiusura effettiva. [!DNL Marketo Measure] può fare riferimento a un solo campo data di chiusura nel dashboard e attualmente si sta puntando alla data di chiusura effettiva.

Se nel campo Data di chiusura effettiva non sono presenti dati per le opportunità aperte, nel dashboard non verranno visualizzati dati. Detto questo, è necessario un flusso di lavoro basato sulla fase dell’opportunità per supportare entrambi i campi data.

1. Crea un campo data di chiusura personalizzato sull’oggetto opportunità (ad esempio [!DNL Marketo Measure] Data di chiusura personalizzata).
1. Creare un flusso di lavoro per aggiornare [!DNL Marketo Measure] Campo Data di chiusura personalizzato con la data dalla Data di chiusura stimata o dalla Data di chiusura effettiva, a seconda che l’opportunità sia aperta o chiusa (il flusso di lavoro deve essere salvato per essere eseguito in tempo reale, ma deve essere eseguito &quot;on demand&quot; almeno una volta per aggiornare tutte le operazioni aperte correnti).
1. Verifica il funzionamento del flusso di lavoro.
1. Il cliente deve fornire il nome API della data di chiusura personalizzata a [!DNL Marketo Measure].
1. [!DNL Marketo Measure] per aggiornare [!DNL Marketo Measure] impostazioni dell&#39;app per puntare al [!DNL Marketo Measure] Campo Data di chiusura personalizzato nel dashboard.

   Al completamento dei passaggi precedenti, dovremo eseguire dei flussi di lavoro per aggiornare sia il Personalizzato che [!DNL Marketo Measure] Campo Importo Opp e [!DNL Marketo Measure] Il campo personalizzato Data di chiusura nelle opportunità storiche per riflettere i dati corretti. È probabile che i campi di attivazione/disattivazione modificati vengano modificati e sarà quindi necessario verificare con il team se si verificano problemi.

Per aggiornare le opportunità chiuse...

1. Isolare le opportunità chiuse dopo il [!DNL Marketo Measure] data di inizio fino a quando il flusso di lavoro non è attivo. Questo è il gruppo di opportunità storiche da aggiornare tramite il flusso di lavoro.
1. Esporta tutti i record in Excel.
1. Apri un file Excel e abilita il contenuto.
1. Copia dati data di chiusura effettiva in [!DNL Marketo Measure] Data di chiusura personalizzata.
1. Copia dati ricavi effettivi in [!DNL Marketo Measure] Importo dell’opportunità personalizzata **e** [!DNL Marketo Measure] Importo dell’opportunità (sono disponibili due campi).
1. Salva file.
1. Importa file. Dynamics lo riconoscerà come file con record esistenti da aggiornare.
1. Verifica la presenza di errori nel file di importazione.

>[!NOTE]
>
>I flussi di lavoro descritti in questo documento sono solo uno dei modi per aggiornare i campi in modo [!DNL Marketo Measure] può mostrare i dati corretti in Discover. Se si dispone di un altro modo di eseguire la stessa attività, è possibile andare per esso. In sostanza, ciò di cui abbiamo bisogno da loro è una sorta di flusso di lavoro che esegua le seguenti operazioni:
>
> * Se Opp = Apri, aggiorna il campo data di chiusura personalizzato, il campo importo opp personalizzato e [!DNL Marketo Measure] opp importo campo uguale rispettivamente a Data di chiusura stimata e Ricavi stimati.
> * Se Opp = Closed Won, aggiorna il campo data di chiusura personalizzato, il campo importo opp personalizzato e [!DNL Marketo Measure] opp importo campo uguale rispettivamente a Data di chiusura effettiva e Reddito effettivo.
