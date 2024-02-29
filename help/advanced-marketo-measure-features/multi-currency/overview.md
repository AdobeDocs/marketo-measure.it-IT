---
unique-page-id: 27656735
description: Panoramica - [!DNL Marketo Measure]
title: Panoramica
exl-id: 2076521c-b579-457c-ab1c-263b1da4dd89
feature: Multi-Currency
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 1%

---

# Panoramica {#overview}

Oggi, il [!DNL Marketo Measure] L&#39;applicazione supporta solo una valuta unica (che si presume essere USD), mentre sappiamo e siamo consapevoli del fatto che abbiamo clienti in tutto il mondo che devono segnalare la propria valuta aziendale e quella dell&#39;utente. Questa funzione consente agli utenti di passare tra le stesse valute utilizzate nel CRM per la visualizzazione delle spese o dei ricavi di vendita riportati in [!DNL Marketo Measure].

## Disponibilità {#availability}

Livello 2 e superiore.

## Requisiti {#requirements}

[!DNL Marketo Measure] richiamerà automaticamente l’impostazione della valuta dal CRM del cliente. Configurazione manuale in [!DNL Marketo Measure] per corrispondere al CRM non è più necessario. L’impostazione della valuta si trova nella pagina &quot;Generale&quot; in &quot;CRM&quot;.

In entrata [!DNL Salesforce], il cliente deve avere &quot;Activate Multiple Currencies&quot; abilitato. Facoltativamente, il cliente può anche selezionare &quot;Sì, desidero abilitare Gestione avanzata valuta&quot;.

In Dynamics, il cliente può impostare tassi di cambio statici nelle Impostazioni per più valute. In Dynamics non esiste un concetto di &quot;gestione avanzata della valuta&quot;.

## Termini {#terms}

| **Termine** | Descrizione |
|---|---|
| **Valuta avanzata** | Il cliente dispone di Advanced Currency Management e Multiple Currencies abilitati, il che significa che possono avere tassi di conversione diversi per periodi di tempo diversi. |
| **Valuta aziendale** | Si tratta delle varie valute elencate e dichiarate da un’organizzazione nel CRM, tutte con tassi di conversione. [!DNL Marketo Measure] importerà questi valori e li renderà disponibili agli utenti all’interno del nostro prodotto. |
| **Impostazioni internazionali valuta** | La valuta unica utilizzata per un&#39;organizzazione, impostata nella pagina Informazioni società. |
| **Valuta locale (o valuta utente)** | La valuta impostata per un singolo utente sul profilo utente, in modo che possa visualizzare qualsiasi importo nella propria valuta locale. L’organizzazione dovrà dichiarare e impostare la valuta prima che un utente possa selezionare la propria valuta locale. |
| **Moneta Unica** | Utilizzato per i clienti che non utilizzano più valute nel CRM, ma la cui organizzazione viene eseguita in una valuta diversa, quindi hanno una &quot;Lingua valuta&quot;. Questa è ancora una valuta unica per l’organizzazione, ma senza alcuna conversione. |
| **Valuta semplice** | Il cliente ha più valute abilitate, ma ha un tasso di conversione statico per valuta. |
