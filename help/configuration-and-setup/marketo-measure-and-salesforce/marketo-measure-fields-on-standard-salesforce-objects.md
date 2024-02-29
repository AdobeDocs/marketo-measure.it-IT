---
unique-page-id: 18874574
description: "[!DNL Marketo Measure] Campi su Standard [!DNL Salesforce] Oggetti - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Campi su Standard [!DNL Salesforce] Oggetti"
exl-id: c9d5254f-06bd-4813-bb29-1a4955b37041
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '1280'
ht-degree: 0%

---

# [!DNL Marketo Measure] Campi su Standard [!DNL Salesforce] Oggetti {#marketo-measure-fields-on-standard-salesforce-objects}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedi ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

Scopri i vari [!DNL Marketo Measure] campi aggiunti a [!DNL Salesforce] oggetti standard.

## Account {#account}

Punteggio di coinvolgimento predittivo: questo campo viene utilizzato con la funzione ABM per fornire un punteggio relativo al livello di coinvolgimento dell’account e tiene conto di molti fattori quali l’attualità delle visualizzazioni di pagina, il numero di contatti associati all’account, la presenza di un’operazione chiusa e così via.

## Caso {#case}

Aggiungiamo campi all’oggetto Case relativo alle attività cardine di contatto Primo contatto e Creazione lead. Questo è per i clienti che utilizzano l’oggetto Case al posto del lead o del contatto e ha anche lo scopo di visualizzare i dati nel caso in cui un cliente non volesse che creassimo record di punti di contatto.

Sorgente del punto di contatto (FT): è la sorgente della prima interazione di contatto.

Sorgente del punto di contatto (LC): è la sorgente dell’interazione di contatto per la creazione di lead.

Canale di marketing (FT): questo è il canale di marketing dell’interazione di primo contatto.

Canale di marketing (LC): questo è il canale di marketing dell’interazione touch per la creazione di lead.

Ad Campaign Name (FT): si tratta della campagna UTM, della campagna pubblicitaria dalle reti pubblicitarie o [!DNL Salesforce] Campagna dell’interazione di primo contatto.

Ad Campaign Name (LC): si tratta della campagna UTM, della campagna pubblicitaria dalle reti pubblicitarie o [!DNL Salesforce] Campagna del [!UICONTROL lead creation] interazione touch.

Pagina di destinazione (FT): è la pagina di destinazione della prima interazione di contatto.

Pagina di destinazione (LC): è la pagina di destinazione del [!UICONTROL lead creation] interazione touch.

Data del punto di contatto (FT): è la data della prima interazione di contatto.

Data punto di contatto (LC): è la data dell’interazione di contatto per la creazione di lead.

## Campaign {#campaign}

Sono stati aggiunti solo 4 campi, 1 pulsante e 1 regola di convalida.

UniqueID: questo campo viene utilizzato internamente per consentire il tracciamento delle diverse campagne sincronizzate con [!DNL Marketo Measure].

Abilita punti di contatto acquirenti: questo campo è destinato alla sincronizzazione effettiva delle campagne per l’inclusione di attribuzione offline e dei dati storici.

Data di inizio punto di contatto: questo campo viene utilizzato per impostare una data di inizio per l’applicazione di punti di contatto alle campagne storiche.

Data di fine punto di contatto: questo campo viene utilizzato per impostare una data di fine per l’applicazione di punti di contatto alle campagne storiche. Un esempio comune sarebbe l’inclusione delle campagne digitali pre-[!DNL Marketo Measure] e quindi impostando la data di fine come giorno in cui lo script è stato applicato.

Bulk Update Touchpoint Date (Button): questo pulsante viene utilizzato per gestire la data di contatto dei membri della campagna quando questa viene sincronizzata, in quanto fa riferimento alla data di iscrizione alla campagna o alla prima data di risposta predefinita. Nel caso in cui tali campi di data non rappresentino in modo accurato la data effettiva del punto di contatto, utilizzeremo questo pulsante per impostare la data del punto di contatto.

Aggiorna [!DNL Marketo Measure] Attribuzione (regola di convalida): questa regola è obsoleta dopo la versione 6.0 del pacchetto.

## Membro della campagna {#campaign-member}

Con il pacchetto sono stati aggiunti 5 campi e 1 trigger Apex.

Stato del punto di contatto (lead): campo diagnostico relativo a una funzione non attivata. Questo consente di capire se è stato creato un punto di contatto rispetto al record Lead correlato o, in caso contrario, perché.

Stato del punto di contatto (contatto): campo diagnostico relativo a una funzione non attivata come predefinita. Questo consente di capire se è stato creato un punto di contatto rispetto al record Contatto correlato o, in caso contrario, perché.

Stato del punto di contatto (opportunità): campo diagnostico relativo a una funzione non attivata come predefinita. Questo consente di capire se è stato creato un punto di contatto rispetto al record Opportunità correlato o, in caso contrario, perché.

Data stato punto di contatto: data in cui i campi diagnostici sono stati compilati.

Data del punto di contatto dell&#39;acquirente: relativa al [!UICONTROL Bulk Update Touchpoint date] dall’oggetto Campaign. Quando viene utilizzata, la data del punto di contatto definita viene applicata al membro della campagna.

OnCampaignMemberDelete: pronto all’uso, [!DNL Salesforce] non compare quando i membri della campagna vengono eliminati, il che può causare problemi con rapporti di attribuzione accurati. Quando un membro della campagna viene eliminato, viene attivato per informare [!DNL Marketo Measure] per rimuovere i punti di contatto relativi al membro della campagna inesistente.

## Contatto {#contact}

Aggiungiamo campi all’oggetto Contact relativo alle attività cardine di contatto Primo contatto e Creazione lead. Questo è per i clienti che preferiscono che l’attribuzione venga segnalata direttamente ai campi invece di creare record di punti di contatto. La maggior parte dei nostri clienti utilizza il percorso record Touchpoint, ma utilizza anche questi campi all’interno della piattaforma di automazione.

Sorgente del punto di contatto (FT): è la sorgente della prima interazione di contatto.

Sorgente del punto di contatto (LC): è la sorgente dell’interazione di contatto per la creazione di lead.

Canale di marketing (FT): questo è il canale di marketing dell’interazione di primo contatto.

Canale di marketing (LC): questo è il canale di marketing dell’interazione touch per la creazione di lead.

Ad Campaign Name (FT): si tratta della campagna UTM, della campagna pubblicitaria dalle reti pubblicitarie o [!DNL Salesforce] Campagna dell’interazione di primo contatto.

Ad Campaign Name (LC): si tratta della campagna UTM, della campagna pubblicitaria dalle reti pubblicitarie o [!DNL Salesforce] Campagna del [!UICONTROL lead creation] interazione touch.

Pagina di destinazione (FT): è la pagina di destinazione della prima interazione di contatto.

Pagina di destinazione (LC): è la pagina di destinazione del [!UICONTROL lead creation] interazione touch.

Data del punto di contatto (FT): è la data della prima interazione di contatto.

Data punto di contatto (LC): è la data dell’interazione di contatto per la creazione di lead.

BizibleID: viene utilizzato in relazione all’attribuzione delle attività e all’integrazione delle metriche di tracciamento delle chiamate per l’associazione dei contatti al punto di contatto.

## Lead {#lead}

Aggiungiamo campi all’oggetto Lead relativi alle attività cardine di contatto Primo contatto e Creazione lead. Questo è per i clienti che preferiscono che l’attribuzione venga segnalata direttamente ai campi invece di creare record di punti di contatto. La maggior parte dei nostri clienti utilizza il percorso record Touchpoint, ma utilizza anche questi campi all’interno della piattaforma di automazione.

Sorgente del punto di contatto (FT): è la sorgente della prima interazione di contatto.

Sorgente del punto di contatto (LC): è la sorgente dell’interazione di contatto per la creazione di lead.

Canale di marketing (FT): questo è il canale di marketing dell’interazione di primo contatto.

Canale di marketing (LC): questo è il canale di marketing dell’interazione touch per la creazione di lead.

Ad Campaign Name (FT): si tratta della campagna UTM, della campagna pubblicitaria dalle reti pubblicitarie o [!DNL Salesforce] Campagna dell’interazione di primo contatto.

Ad Campaign Name (LC): si tratta della campagna UTM, della campagna pubblicitaria dalle reti pubblicitarie o [!DNL Salesforce] Campagna di interazione touch per la creazione di lead.

Pagina di destinazione (FT): è la pagina di destinazione della prima interazione di contatto.

Pagina di destinazione (LC): è la pagina di destinazione dell’interazione touch per la creazione di lead.

Data del punto di contatto (FT): è la data della prima interazione di contatto.

Data punto di contatto (LC): è la data dell’interazione di contatto per la creazione di lead.

BizibleID: viene utilizzato in relazione all’attribuzione delle attività e all’integrazione delle metriche di tracciamento delle chiamate per l’associazione di lead al punto di contatto.

## Account {#account-1}

Viene utilizzato per la mappatura Lead to Account per la funzione ABM. Compiliamo questo campo per creare la relazione di ricerca tra i due oggetti.

## Opportunità {#opportunity}

[!DNL Marketo Measure] Importo opportunità: questo campo viene utilizzato nello scenario in cui viene utilizzato un campo importo personalizzato nell’opportunità. Il valore del campo personalizzato viene mappato su [!DNL Marketo Measure] Importo opportunità utilizzando un flusso di lavoro e quindi leggere questo campo per i campi di attribuzione Ricavi nell&#39;oggetto punto di contatto di attribuzione buyer.

## Attività {#activity}

BizibleID: consente di correlare un punto di contatto alle attività per l’attribuzione delle attività e l’integrazione delle metriche di tracciamento delle chiamate.

Data punto di contatto acquirente: si tratta di un campo che può essere popolato tramite un flusso di lavoro da utilizzare come data per l’attribuzione delle attività e che verrà compilato affinché l’integrazione delle metriche di tracciamento delle chiamate possa sapere quando si è verificata l’interazione.
