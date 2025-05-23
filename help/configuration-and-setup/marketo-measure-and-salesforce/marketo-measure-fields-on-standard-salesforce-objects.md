---
unique-page-id: 18874574
description: '[!DNL Marketo Measure] campi in Standard [!DNL Salesforce] Oggetti - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] campi in Oggetti Standard [!DNL Salesforce] '
exl-id: c9d5254f-06bd-4813-bb29-1a4955b37041
feature: Salesforce
source-git-commit: 05ba9e487d492ba4352a7f0577c7221f6ec9567e
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---

# [!DNL Marketo Measure] campi in [!DNL Salesforce] oggetti standard {#marketo-measure-fields-on-standard-salesforce-objects}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedere ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

Scopri i vari campi [!DNL Marketo Measure] aggiunti agli oggetti standard [!DNL Salesforce].

## Account {#account}

Punteggio di coinvolgimento predittivo: questo campo viene utilizzato con la funzione ABM per fornire un punteggio relativo al livello di coinvolgimento dell’account e tiene conto di molti fattori quali l’attualità delle visualizzazioni di pagina, il numero di contatti associati all’account, la presenza di un’operazione chiusa e così via.

## Campaign {#campaign}

Sono stati aggiunti solo 4 campi, 1 pulsante e 1 regola di convalida.

UniqueID: questo campo viene utilizzato internamente per consentire il monitoraggio delle diverse campagne sincronizzate con [!DNL Marketo Measure].

Abilita punti di contatto acquirenti: questo campo è destinato alla sincronizzazione effettiva delle campagne per l’inclusione di attribuzione offline e dei dati storici.

Data di inizio punto di contatto: questo campo viene utilizzato per impostare una data di inizio per l’applicazione di punti di contatto alle campagne storiche.

Data di fine punto di contatto: questo campo viene utilizzato per impostare una data di fine per l’applicazione di punti di contatto alle campagne storiche. Un esempio comune è l&#39;inclusione di campagne digitali precedenti a [!DNL Marketo Measure] e quindi l&#39;impostazione della data di fine come giorno in cui lo script è stato applicato.

Bulk Update Touchpoint Date (Button): questo pulsante viene utilizzato per gestire la data di contatto dei membri della campagna quando questa viene sincronizzata, in quanto fa riferimento alla data di iscrizione alla campagna o alla prima data di risposta predefinita. Nel caso in cui tali campi di data non rappresentino in modo accurato la data effettiva del punto di contatto, utilizzeremo questo pulsante per impostare la data del punto di contatto.

Attribuzione aggiornamento [!DNL Marketo Measure] (regola di convalida): questa regola è obsoleta dopo la versione del pacchetto 6.0.

## Membro della campagna {#campaign-member}

Con il pacchetto sono stati aggiunti 5 campi e 1 trigger Apex.

Stato del punto di contatto (lead): campo diagnostico relativo a una funzione non attivata. Questo consente di capire se è stato creato un punto di contatto rispetto al record Lead correlato o, in caso contrario, perché.

Stato del punto di contatto (contatto): campo diagnostico relativo a una funzione non attivata come predefinita. Questo consente di capire se è stato creato un punto di contatto rispetto al record Contatto correlato o, in caso contrario, perché.

Stato del punto di contatto (opportunità): campo diagnostico relativo a una funzione non attivata come predefinita. Questo consente di capire se è stato creato un punto di contatto rispetto al record Opportunità correlato o, in caso contrario, perché.

Data stato punto di contatto: data in cui i campi diagnostici sono stati compilati.

Data Buyer Touchpoint: è correlato al pulsante [!UICONTROL Bulk Update Touchpoint date] dell&#39;oggetto Campaign. Quando viene utilizzata, la data del punto di contatto definita viene applicata al membro della campagna.

OnCampaignMemberDelete: [!DNL Salesforce] non viene visualizzato automaticamente quando i membri della campagna vengono eliminati, il che può causare problemi con rapporti di attribuzione accurati. Quando un membro della campagna viene eliminato, questo viene attivato per informare [!DNL Marketo Measure] di rimuovere i punti di contatto relativi a quel membro della campagna inesistente.

## Lead {#lead}

Il campo Account Bizible viene utilizzato per la mappatura lead-account per la funzione ABM. Compiliamo questo campo per creare la relazione di ricerca tra i due oggetti.

## Account {#account-1}

Viene utilizzato per la mappatura Lead to Account per la funzione ABM. Compiliamo questo campo per creare la relazione di ricerca tra i due oggetti.

## Opportunità {#opportunity}

[!DNL Marketo Measure] importo opportunità: questo campo viene utilizzato nello scenario in cui viene utilizzato un campo importo personalizzato nell&#39;opportunità. Il valore del campo personalizzato viene mappato sull&#39;importo dell&#39;opportunità [!DNL Marketo Measure] utilizzando un flusso di lavoro, quindi il campo viene letto per i campi di attribuzione Ricavi dell&#39;oggetto Buyer Attribution Touchpoint.

## Attività {#activity}

BizibleID: consente di correlare un punto di contatto alle attività per l’attribuzione delle attività e l’integrazione delle metriche di tracciamento delle chiamate.

Data Buyer Touchpoint: questo è un campo che può essere popolato tramite un flusso di lavoro da utilizzare come data per l’attribuzione delle attività e che verrà compilato affinché l’integrazione calltrackingmetrics possa sapere quando si è verificata l’interazione.
