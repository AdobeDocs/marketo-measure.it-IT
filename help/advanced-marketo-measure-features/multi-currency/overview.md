---
unique-page-id: 27656735
description: Panoramica - [!DNL Marketo Measure] - Documentazione del prodotto
title: Panoramica
exl-id: 2076521c-b579-457c-ab1c-263b1da4dd89
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 1%

---

# Panoramica {#overview}

Oggi, il [!DNL Marketo Measure] L&#39;applicazione supporta solo una moneta unica (presumibilmente USD), mentre sappiamo e sappiamo che abbiamo clienti in tutto il mondo che hanno bisogno di segnalare le proprie valute aziendali e utente. Questa funzione consente agli utenti di passare da una valuta all’altra quando osservano le spese riportate o i ricavi di vendita.

## Disponibilità {#availability}

Livello 2 e superiore.

## Requisiti {#requirements}

In [!DNL Salesforce], il cliente deve avere l&#39;opzione &quot;Attiva più valute&quot; abilitata. Facoltativamente, il cliente può anche selezionare &quot;Sì, voglio abilitare Advanced Currency Management&quot;.

In Dynamics, il cliente può impostare tassi di cambio statici nelle proprie Impostazioni per più valute. In Dynamics non esiste alcun concetto di &quot;gestione avanzata della valuta&quot;.

## Termini {#terms}

| **Termine** | Descrizione |
|---|---|
| **Valuta avanzata** | Il cliente dispone di Gestione avanzata delle divise e di Valute multiple abilitate, il che significa che possono avere tassi di conversione diversi per periodi di tempo diversi. |
| **Valuta aziendale** | Queste sono le varie valute elencate e dichiarate da un&#39;organizzazione nel CRM, tutte con tassi di conversione. [!DNL Marketo Measure] Importerà questi valori e renderà queste valute disponibili agli utenti all&#39;interno del nostro prodotto. |
| **Impostazioni internazionali valuta** | La moneta unica utilizzata per un&#39;organizzazione, impostata nella pagina Informazioni società. |
| **Valuta locale (o valuta utente)** | La valuta impostata per un singolo utente nel profilo utente, in modo che possano visualizzare qualsiasi importo nella propria valuta locale. L&#39;organizzazione dovrà dichiarare e impostare la valuta prima che un utente possa selezionare la propria valuta locale. |
| **Moneta unica** | Utilizzato per i clienti che non utilizzano più divise nel CRM, ma la loro organizzazione viene eseguita in una valuta diversa, quindi dispongono di una &quot;Impostazioni internazionali valuta&quot;. Si tratta ancora di una moneta unica per l&#39;organizzazione, ma senza alcuna conversione. |
| **Valuta semplice** | Il cliente dispone di più divise abilitate, ma dispone di un tasso di conversione statico per valuta. |
