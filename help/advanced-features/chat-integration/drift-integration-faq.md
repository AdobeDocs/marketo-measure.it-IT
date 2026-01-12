---
description: Domande frequenti sull'integrazione della deriva - [!DNL Marketo Measure]
title: Domande frequenti sull’integrazione della deriva
exl-id: ae5706b1-1f6c-4201-8585-0d7c587746e1
feature: Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# Domande frequenti sull’integrazione della deriva {#drift-integration-faq}

Come parte dell&#39;integrazione di [!DNL Marketo Measure] con Drift, ecco alcune delle domande più frequenti. Per eventuali domande non descritte di seguito, contatta il team dell&#39;account Adobe (il tuo Account Manager) o il [supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

**Come è abilitata l&#39;integrazione?**

Il rilevamento della chat di deriva per [!DNL Marketo Measure] è abilitato per impostazione predefinita. Se desideri disattivarla (e non creare punti di contatto da Drift Chats per impostazione predefinita), aggiungi un attributo aggiuntivo all&#39;implementazione JavaScript [!DNL Marketo Measure], in grassetto qui sotto:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" id="bizible-settings" data-chatEnabled="false"></script>`

Per coloro che utilizzano [!DNL Google Tag Manager] per caricare lo script [!DNL Marketo Measure], se si desidera escludere le chat di deriva dall&#39;idoneità per il punto di contatto, aggiungere al seguente `<span>` subito dopo lo script [!DNL Marketo Measure]:

`<span id="bizible-settings" data-chatEnabled="false"></span>`

**Funzionamento dell&#39;integrazione:**

L&#39;integrazione ora consente a [!DNL Marketo Measure] di tenere traccia di quando un utente finale fornisce il proprio indirizzo e-mail in una chat Drift. Da qui creiamo punti di contatto da queste interazioni con un tipo di punto di contatto &quot;Chat web&quot;. Questa integrazione consente agli esperti di marketing di comprendere le prestazioni delle interazioni chat, insieme ai canali, ai sottocanali o alle campagne che spingono le persone a interagire con queste chat.

**Cosa succede se si tiene traccia di Drift tramite le regole di sincronizzazione della campagna?**

Se sono presenti regole di sincronizzazione della campagna per creare punti di contatto per le interazioni di chat di deriva, assicurati di non aggiungere più questi particolari utenti finali nella campagna CRM corrispondente. Altrimenti, una volta che il bit della funzione è abilitato, crea un punto di contatto e un punto di contatto digitale per la campagna CRM per un’interazione chat in deriva.

**Cosa succede se si tiene traccia di Drift tramite campagne CRM?**

Se sono presenti campagne CRM per la creazione di punti di contatto per le interazioni con le chat in arrivo, è necessario impostare una data di fine punto di contatto per tali campagne specifiche (la data di fine punto di contatto deve essere la data in cui il bit della funzione di integrazione chat web è abilitato).

**Cosa succede se si tiene traccia di Drift tramite attività?**

Se sono presenti regole di attività per creare punti di contatto per le interazioni di chat in modalità drift, è necessario aggiungere alle regole un ulteriore elemento di logica. Aggiungi la logica utilizzando il campo Data di creazione attività per impedire la creazione di duplicazioni di punti di contatto (ossia CrmTask.CreatedDate è minore della data in cui è stato abilitato il bit della funzione). Vedi la schermata seguente, ad esempio.

![Esempio di regola di attività CRM configurata per i punti di contatto della chat di deriva](assets/activity-rule-drift.png)
