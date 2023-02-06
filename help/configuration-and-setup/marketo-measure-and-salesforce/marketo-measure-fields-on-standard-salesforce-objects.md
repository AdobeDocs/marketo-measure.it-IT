---
unique-page-id: 18874574
description: "[!DNL Marketo Measure] Campi standard [!DNL Salesforce] Oggetti - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] Campi standard [!DNL Salesforce] Oggetti"
exl-id: c9d5254f-06bd-4813-bb29-1a4955b37041
source-git-commit: b910e5aedb9e178058f7af9a6907a1039458ce7a
workflow-type: tm+mt
source-wordcount: '1273'
ht-degree: 0%

---

# [!DNL Marketo Measure] Campi standard [!DNL Salesforce] Oggetti {#marketo-measure-fields-on-standard-salesforce-objects}

>[!NOTE]
>
>È possibile visualizzare istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella nostra documentazione, ma vedi ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riflesso nel tuo CRM presto.

Scopri le varie [!DNL Marketo Measure] campi aggiunti a [!DNL Salesforce] oggetti standard.

## Account {#account}

Punteggio di coinvolgimento predittivo: Questo campo viene utilizzato con la nostra funzione ABM per fornire un punteggio relativo al livello di coinvolgimento dell&#39;account e prende in considerazione molti fattori come la recente visualizzazione della pagina, quanti contatti sono associati all&#39;account, se c&#39;è un opp chiuso, ecc.

## Case {#case}

Aggiungiamo campi all’oggetto Case relativi alle tappe di contatto Primo contatto e Creazione di lead . Questo è per i clienti che utilizzano l’oggetto Case al posto del Lead o del Contatto e serve anche allo scopo di un altro modo per visualizzare i dati nel caso in cui un cliente non volesse che creassimo record Touchpoint.

Origine punto di contatto (FT): Questa è la fonte dell’interazione con il primo contatto.

Origine punto di contatto (LC): È la fonte dell’interazione touch per la creazione del lead.

Canale di marketing (FT): Questo è il canale di marketing dell’interazione con il primo contatto.

Canale di marketing (LC): Questo è il canale di marketing dell’interazione touch per la creazione di lead.

Nome campagna pubblicitaria (FT): Si tratta della campagna UTM, della campagna pubblicitaria dalle reti pubblicitarie, o [!DNL Salesforce] Campagna dell’interazione con il primo contatto.

Nome campagna pubblicitaria (LC): Si tratta della campagna UTM, della campagna pubblicitaria dalle reti pubblicitarie, o [!DNL Salesforce] Campagna di [!UICONTROL lead creation] interazione touch.

Pagina di destinazione (FT): Questa è la pagina di destinazione dell’interazione con il primo contatto.

Pagina di destinazione (LC): Questa è la pagina di destinazione del [!UICONTROL lead creation] interazione touch.

Data punto di contatto (FT): Data dell’interazione con il primo contatto.

Data punto di contatto (LC): Data dell’interazione touch per la creazione del lead.

## Campaign {#campaign}

Sono aggiunti solo 4 campi, 1 pulsante e 1 regola di convalida.

ID univoco: Questo campo viene utilizzato internamente per tenere traccia delle diverse campagne sincronizzate con [!DNL Marketo Measure].

Abilita i punti di contatto dell’acquirente: Questo campo è destinato all’effettiva sincronizzazione di Campagne per l’inclusione dell’attribuzione offline e i dati storici.

Data inizio punto di contatto: Questo campo viene utilizzato per impostare una data di inizio dell’applicazione di punti di contatto a campagne cronologiche.

Data fine punto di contatto: Questo campo viene utilizzato per impostare una data di fine per applicare punti di contatto a campagne cronologiche. Un esempio comune potrebbe essere l&#39;inclusione di campagne digitali pre-[!DNL Marketo Measure] e quindi impostare la data di fine come il giorno in cui lo script è stato applicato.

Aggiornamento in blocco della data del punto di contatto (pulsante): Questo pulsante viene utilizzato per gestire la data del punto di contatto dei membri della campagna quando questa viene sincronizzata, in quanto farà riferimento alla data di iscrizione alla campagna o alla prima data di risposta preconfigurata. Se tali campi data non rappresentano in modo preciso la data effettiva del punto di contatto, viene utilizzato questo pulsante per impostare la data del punto di contatto.

Aggiorna [!DNL Marketo Measure] Attribuzione (regola di convalida): Questa regola è obsoleta dopo la versione 6.0 del pacchetto.

## Membro della campagna {#campaign-member}

Ci sono 5 campi e 1 trigger Apex aggiunto con il pacchetto.

Stato punto di contatto (lead): Si tratta di un campo diagnostico relativo a una funzione che non è attivata. Questo viene utilizzato per capire se un punto di contatto è stato creato rispetto al relativo record Lead o, in caso contrario, perché.

Stato punto di contatto (contatto): Si tratta di un campo diagnostico relativo a una funzione che non è attivata. Questo viene utilizzato per capire se è stato creato un punto di contatto rispetto al record Contatto correlato o, in caso contrario, perché.

Stato punto di contatto (opportunità): Si tratta di un campo diagnostico relativo a una funzione che non è attivata. Questo viene utilizzato per capire se un punto di contatto è stato creato rispetto al record Opportunità correlato o, in caso contrario, perché.

Data stato punto di contatto: Data di compilazione dei campi di diagnostica.

Data punto di contatto dell&#39;acquirente: È correlato al [!UICONTROL Bulk Update Touchpoint date] dall’oggetto Campaign. Quando viene utilizzato, applichiamo la data del punto di contatto definito al membro della campagna.

OnCampaignMemberDelete: Fuori dalla scatola, [!DNL Salesforce] non viene visualizzato quando i membri di Campaign vengono eliminati e ciò può causare problemi con rapporti di attribuzione accurati. Quando un membro della campagna viene eliminato, questo viene attivato per informare [!DNL Marketo Measure] per rimuovere i punti di contatto relativi a quel membro della campagna inesistente.

## Contatto {#contact}

Aggiungiamo campi all’oggetto Contact relativi alle tappe di contatto Primo contatto e Creazione di lead . Questo è per i clienti che preferirebbero che l’attribuzione venisse segnalata direttamente ai campi anziché creare record di punti di contatto. La maggior parte dei nostri clienti utilizza il percorso di record Touchpoint, ma anche questi campi all&#39;interno della loro piattaforma di automazione.

Origine punto di contatto (FT): Questa è la fonte dell’interazione con il primo contatto.

Origine punto di contatto (LC): È la fonte dell’interazione touch per la creazione del lead.

Canale di marketing (FT): Questo è il canale di marketing dell’interazione con il primo contatto.

Canale di marketing (LC): Questo è il canale di marketing dell’interazione touch per la creazione di lead.

Nome campagna pubblicitaria (FT): Si tratta della campagna UTM, della campagna pubblicitaria dalle reti pubblicitarie, o [!DNL Salesforce] Campagna dell’interazione con il primo contatto.

Nome campagna pubblicitaria (LC): Si tratta della campagna UTM, della campagna pubblicitaria dalle reti pubblicitarie, o [!DNL Salesforce] Campagna di [!UICONTROL lead creation] interazione touch.

Pagina di destinazione (FT): Questa è la pagina di destinazione dell’interazione con il primo contatto.

Pagina di destinazione (LC): Questa è la pagina di destinazione del [!UICONTROL lead creation] interazione touch.

Data punto di contatto (FT): Data dell’interazione con il primo contatto.

Data punto di contatto (LC): Data dell’interazione touch per la creazione del lead.

BizibleID: Viene utilizzato in relazione all’integrazione delle metriche di attribuzione e di tracciamento delle attività per l’associazione di contatto al punto di contatto.

## Lead {#lead}

Aggiungiamo campi all’oggetto Lead relativi alle tappe di contatto Primo contatto e Creazione di lead . Questo è per i clienti che preferirebbero che l’attribuzione venisse segnalata direttamente ai campi anziché creare record di punti di contatto. La maggior parte dei nostri clienti utilizza il percorso di record Touchpoint, ma anche questi campi all&#39;interno della loro piattaforma di automazione.

Origine punto di contatto (FT): Questa è la fonte dell’interazione con il primo contatto.

Origine punto di contatto (LC): È la fonte dell’interazione touch per la creazione del lead.

Canale di marketing (FT): Questo è il canale di marketing dell’interazione con il primo contatto.

Canale di marketing (LC): Questo è il canale di marketing dell’interazione touch per la creazione di lead.

Nome campagna pubblicitaria (FT): Si tratta della campagna UTM, della campagna pubblicitaria dalle reti pubblicitarie, o [!DNL Salesforce] Campagna dell’interazione con il primo contatto.

Nome campagna pubblicitaria (LC): Si tratta della campagna UTM, della campagna pubblicitaria dalle reti pubblicitarie, o [!DNL Salesforce] Campagna dell’interazione touch per la creazione del lead.

Pagina di destinazione (FT): Questa è la pagina di destinazione dell’interazione con il primo contatto.

Pagina di destinazione (LC): Questa è la pagina di destinazione dell’interazione touch per la creazione del lead.

Data punto di contatto (FT): Data dell’interazione con il primo contatto.

Data punto di contatto (LC): Data dell’interazione touch per la creazione del lead.

BizibleID: Viene utilizzato in relazione all’integrazione delle metriche di attribuzione e di tracciamento delle attività per l’associazione lead al punto di contatto.

## Account {#account-1}

Viene utilizzato per la mappatura da lead a account per la funzionalità ABM. Questo campo viene compilato per creare la relazione di ricerca tra i due oggetti.

## Opportunità {#opportunity}

[!DNL Marketo Measure] Importo opportunità: Questo campo viene utilizzato nello scenario in cui viene utilizzato un campo di importo personalizzato sull&#39;opportunità. Il valore del campo personalizzato viene mappato su [!DNL Marketo Measure] Importo opportunità utilizzando un flusso di lavoro, quindi leggi questo campo per i campi di attribuzione Ricavo sull’oggetto punto di contatto Attribuzione acquirente.

## Attività {#activity}

BizibleID: Questo ci consente di collegare un punto di contatto alle attività per l’integrazione delle metriche di attribuzione e di tracciamento del chiamata dell’attività.

Data punto di contatto dell&#39;acquirente: Si tratta di un campo che può essere compilato tramite un flusso di lavoro da utilizzare come data per l’attribuzione delle attività e verrà popolato affinché l’integrazione delle metriche di calltracking sappia quando si è verificata l’interazione.
