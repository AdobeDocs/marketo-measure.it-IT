---
unique-page-id: 18874696
description: Consigliato [!DNL Salesforce] Autorizzazioni per [!DNL Marketo Measure] Utente connesso - [!DNL Marketo Measure] - Documentazione del prodotto
title: Consigliato [!DNL Salesforce] Autorizzazioni per [!DNL Marketo Measure] Utente connesso
exl-id: b74aa28b-4a7b-42d1-8df0-d1ae0ff1f338
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Consigliato [!DNL Salesforce] Autorizzazioni per [!DNL Marketo Measure] Utente connesso {#recommended-salesforce-permissions-for-marketo-measure-connected-user}

[!DNL Marketo Measure] invia e riceve i dati tramite una connessione [!DNL Salesforce] all&#39;interno di [!DNL Marketo Measure] app.

Per inviare i dati dei punti di contatto al tuo [!DNL Salesforce] istanza, l&#39;utente connesso deve avere accesso a [!DNL Marketo Measure] oggetti personalizzati (ad esempio punto di contatto per l’acquirente e punto di contatto per l’attribuzione dell’acquirente) e standard [!DNL Salesforce] oggetti quali Lead e Contatti (vedere [[!DNL Marketo Measure] Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md).

[!DNL Salesforce] Le licenze utente amministratore possono fungere da utente connesso in quanto spesso dispongono dei privilegi di dati necessari per impostazione predefinita. Tuttavia, il tuo team può preferire un utente di integrazioni o un [!DNL Salesforce] licenza utente per monitorare l&#39;impatto di [!DNL Marketo Measure] sulla tua istanza.

Per garantire che: [!DNL Marketo Measure] il flusso dei dati è accurato:

* [!DNL Marketo Measure] Set Di Autorizzazioni Amministratore Per Utente Dedicato

Il set di autorizzazioni gestito consente a un amministratore SFDC di creare, leggere, scrivere ed eliminare record da [!DNL Marketo Measure] oggetti.

* Visualizza e modifica set di autorizzazioni lead convertiti

Ciò consente [!DNL Marketo Measure] per decorare i lead dopo che sono stati convertiti in contatti. Se questo set di autorizzazioni non è abilitato, possono esserci rilevanti lacune nel tracciamento dei dati. Puoi trovare ulteriori informazioni in [[!DNL Salesforce Trailblazer] community](https://help.salesforce.com/articleView?id=leads_view_edit_converted.htm&amp;type=5).

* [!DNL Salesforce] Casella di controllo Utente marketing

La [!UICONTROL Marketing User] consente all’utente di creare campagne e utilizzare le procedure guidate per l’importazione di campagne. Se questa opzione non è selezionata, l’utente può visualizzare solo le campagne e la configurazione avanzata della campagna, modificare la cronologia della campagna per un singolo lead o contatto ed eseguire i rapporti sulle campagne. [!DNL Marketo Measure] deve essere in grado di leggere e scrivere sull&#39;oggetto campagna.

**Risoluzione dei problemi aggiuntivi**

Se [!DNL Marketo Measure] si verificano ancora problemi durante la lettura o la scrittura di dati. Potrebbe essere utile indagare i seguenti elementi:

* Accesso a [!DNL Salesforce] Code

Se l’utente dedicato non ha accesso ai lead in coda, non può modificare i lead con [!DNL Marketo Measure] dati. A tal fine, puoi svolgere un ruolo nella gerarchia che consente l’accesso alle code o concedere l’accesso agli utenti singolarmente.

* Sicurezza e accessibilità a livello di campo

La sicurezza a livello di campo e l’accessibilità dei campi sono correlate, ma presentano alcune differenze chiave. Sicurezza a livello di campo definisce la visibilità del campo per un determinato profilo, mentre l’accessibilità del campo determina se un campo è modificabile in base alla protezione a livello di campo e alla configurazione del layout di pagina. Utilizzo della [!DNL Marketo Measure] i set di autorizzazioni del pacchetto ti verranno fornite le impostazioni di protezione dell’oggetto campo necessarie. In alcuni casi, per garantire la corretta accessibilità dei campi, l’utente connesso deve disporre della [!DNL Marketo Measure] campi nei layout di pagina. [!DNL Marketo Measure] i campi nel layout consentono [!DNL Marketo Measure] dati da mappare in [!DNL Salesforce]. Questo dipenderà dal vostro particolare [!DNL Salesforce] ambiente.

Ogni organizzazione [!DNL Salesforce] ha esigenze individuali ma vi forniamo i nostri requisiti per bilanciare il [!DNL Marketo Measure] le esigenze di accesso con i protocolli di sicurezza. Non esitate a contattarci [[!DNL Marketo Support]](https://nation.marketo.com/t5/support/ct-p/Support){target=&quot;_blank&quot;}.
