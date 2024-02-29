---
unique-page-id: 27656441
description: Domande frequenti sull’integrazione della deriva - [!DNL Marketo Measure]
title: Domande frequenti sull’integrazione della deriva
exl-id: ae5706b1-1f6c-4201-8585-0d7c587746e1
feature: Integration
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Domande frequenti sull’integrazione della deriva {#drift-integration-faq}

Nell&#39;ambito del programma [!DNL Marketo Measure] Integrazione con Drift, ecco alcune delle domande più frequenti. Per eventuali domande non trattate qui sotto, rivolgiti al team dell’account Adobe (il tuo Account Manager) oppure [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

**Come viene abilitata l’integrazione?**

Tracciamento della chat di deriva per [!DNL Marketo Measure] è attivato per impostazione predefinita. Se desideri disattivarla (e non creare punti di contatto da Drift Chats per impostazione predefinita), aggiungi un attributo aggiuntivo al tuo [!DNL Marketo Measure] Implementazione JavaScript, aggiunta in grassetto di seguito:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" id="bizible-settings" data-chatEnabled="false"></script>`

Per coloro che utilizzano [!DNL Google Tag Manager] per caricare [!DNL Marketo Measure] Script: per escludere le chat di deriva dall’idoneità per i punti di contatto, aggiungi al seguente `<span>` subito dopo il [!DNL Marketo Measure] Script:

`<span id="bizible-settings" data-chatEnabled="false"></span>`

**Che funzione svolge l’integrazione?**

L’integrazione ora consente [!DNL Marketo Measure] per tenere traccia di quando un utente finale fornisce il proprio indirizzo e-mail in una chat di deriva. Da qui creiamo punti di contatto da queste interazioni con un tipo di punto di contatto &quot;Chat web&quot;. Questa integrazione consente agli esperti di marketing di comprendere le prestazioni delle interazioni chat, insieme ai canali, ai sottocanali o alle campagne che spingono le persone a interagire con queste chat.

**Cosa succede se tengo traccia di Drift tramite le regole di sincronizzazione delle campagne?**

Se sono presenti regole di sincronizzazione della campagna per creare punti di contatto per le interazioni di chat di deriva, assicurati di non aggiungere più questi particolari utenti finali nella campagna CRM corrispondente. Altrimenti, una volta che il bit della funzione è abilitato, crea un punto di contatto e un punto di contatto digitale per la campagna CRM per un’interazione chat in deriva.

**Cosa succede se tengo traccia di Drift tramite campagne CRM?**

Se sono presenti campagne CRM per la creazione di punti di contatto per le interazioni con le chat in arrivo, è necessario impostare una data di fine punto di contatto per tali campagne specifiche (la data di fine punto di contatto deve essere la data in cui il bit della funzione di integrazione chat web è abilitato).

**Cosa succede se si tiene traccia di Drift tramite Attività?**

Se sono presenti regole di attività per creare punti di contatto per le interazioni di chat in modalità drift, è necessario aggiungere alle regole un ulteriore elemento di logica. Aggiungi la logica utilizzando il campo Data di creazione attività per impedire la creazione di duplicazioni di punti di contatto (ossia CrmTask.CreatedDate è minore della data in cui è stato abilitato il bit della funzione). Vedi la schermata seguente, ad esempio.

![](assets/activity-rule-drift.png)
