---
unique-page-id: 27656441
description: Domande frequenti sull’integrazione delle versioni precedenti - [!DNL Marketo Measure] - Documentazione del prodotto
title: Domande frequenti sull’integrazione delle versioni
exl-id: ae5706b1-1f6c-4201-8585-0d7c587746e1
source-git-commit: 51397a02872035fef41d308c1f855bcaecc29c4e
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# Domande frequenti sull’integrazione delle versioni {#drift-integration-faq}

Come parte del [!DNL Marketo Measure] integrazione con Drift, abbiamo delineato alcune delle domande più frequenti. In caso di domande non descritte di seguito, contatta il team dell’account Adobe (il tuo Account Manager) o [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

**Come è abilitata l’integrazione?**

Tracciamento della chat per [!DNL Marketo Measure] è attivato per impostazione predefinita. Se per qualsiasi motivo desideri disattivarlo (e non creare punti di contatto da Disegno chat per impostazione predefinita), sarà necessario aggiungere un attributo aggiuntivo al tuo [!DNL Marketo Measure] Implementazione Javascript, con grassetto qui sotto:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" id="bizible-settings" data-chatEnabled="false"></script>`

Per coloro che utilizzano [!DNL Google Tag Manager] per caricare [!DNL Marketo Measure] Script: per escludere le chat di tipo Drift da un punto di contatto, devi aggiungere a quanto segue `<span>` dopo il [!DNL Marketo Measure] Script:

`<span id="bizible-settings" data-chatEnabled="false"></span>`

**Cosa fa l&#39;integrazione?**

L’integrazione ora consente [!DNL Marketo Measure] per tenere traccia di quando un utente finale fornisce il proprio indirizzo e-mail in una chat Drift. Da lì creiamo punti di contatto da queste interazioni con un tipo di punto di contatto di &quot;Web Chat&quot;. Questa integrazione consente agli addetti al marketing di comprendere le prestazioni delle loro interazioni con le chat, insieme ai canali/sottocanali/campagne che spingono le persone a interagire con queste chat.

**Cosa succede se si tiene traccia di Drift tramite regole di sincronizzazione delle campagne?**

Se sono presenti regole di sincronizzazione delle campagne per creare punti di contatto per le interazioni con le chat di Drift, dovrai accertarti di smettere di aggiungere tali utenti finali specifici alla campagna CRM corrispondente. In caso contrario, una volta abilitato il bit di funzionalità, creeremo un punto di contatto e un punto di contatto digitali per una singola interazione con la chat di Drift.

**Cosa succede se si tiene traccia di Drift tramite le campagne CRM?**

Se esistono campagne CRM per la creazione di punti di contatto per le interazioni con chat Drift, è necessario impostare una data di fine punto di contatto su tali campagne specifiche (la data di fine punto di contatto deve essere la data in cui il bit della funzione di integrazione con chat Web è abilitato).

**Cosa succede se si tiene traccia di Drift tramite Attività?**

Se sono presenti regole di attività per creare punti di contatto per le interazioni con la chat di Drift, sarà necessario aggiungere alle regole un ulteriore elemento logico. Per evitare la duplicazione dei punti di contatto, è necessario aggiungere logica utilizzando il campo Data creazione attività (IE CrmTask.CreatedDate è minore della data in cui è stato abilitato il bit di funzione). Vedi la schermata sottostante per esempio.

![](assets/activity-rule-drift.png)
