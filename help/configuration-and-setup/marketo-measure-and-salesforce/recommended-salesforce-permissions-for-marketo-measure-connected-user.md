---
unique-page-id: 18874696
description: Consigliato [!DNL Salesforce] Autorizzazioni per [!DNL Marketo Measure] Utente connesso - [!DNL Marketo Measure] - Documentazione del prodotto
title: Consigliato [!DNL Salesforce] Autorizzazioni per [!DNL Marketo Measure] Utente connesso
exl-id: b74aa28b-4a7b-42d1-8df0-d1ae0ff1f338
feature: Salesforce
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Consigliato [!DNL Salesforce] Autorizzazioni per [!DNL Marketo Measure] Utente connesso {#recommended-salesforce-permissions-for-marketo-measure-connected-user}

[!DNL Marketo Measure] invia e riceve dati tramite una connessione [!DNL Salesforce] utente all&#39;interno di [!DNL Marketo Measure] app.

Per inviare i dati del punto di contatto al tuo [!DNL Salesforce] , l&#39;utente connesso deve avere accesso a [!DNL Marketo Measure] oggetti personalizzati (ad esempio punto di contatto dell’acquirente e punto di contatto di attribuzione dell’acquirente) e standard [!DNL Salesforce] oggetti quali lead e contatti (vedere [[!DNL Marketo Measure] in Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md).

[!DNL Salesforce] Le licenze utente amministratore possono fungere da utente connesso in quanto spesso dispongono dei privilegi di dati necessari per impostazione predefinita. Tuttavia, il tuo team potrebbe preferire l’utilizzo di un utente di integrazioni o di un [!DNL Salesforce] licenza utente per tenere traccia dell’impatto di [!DNL Marketo Measure] nella tua istanza.

Per garantire che [!DNL Marketo Measure] i dati scorrono con precisione:

* [!DNL Marketo Measure] Autorizzazioni Amministratore Impostate Per Utente Dedicato

Il set di autorizzazioni gestite consente a un amministratore SFDC di creare, leggere, scrivere ed eliminare record da [!DNL Marketo Measure] oggetti.

* Visualizza e modifica set di autorizzazioni lead convertiti

Ciò consente [!DNL Marketo Measure] per decorare i lead dopo la conversione in contatti. Se questo set di autorizzazioni non è abilitato, possono verificarsi significative lacune nel tracciamento dei dati. Per ulteriori informazioni, consulta [[!DNL Salesforce Trailblazer] community](https://help.salesforce.com/articleView?id=leads_view_edit_converted.htm&amp;type=5).

* [!DNL Salesforce] Casella di controllo Utente marketing

Il [!UICONTROL Marketing User] La casella di controllo consente all’utente di creare campagne e utilizzare l’Importazione guidata campagne. Se questa opzione non è selezionata, l’utente può solo visualizzare le campagne e la configurazione avanzata della campagna, modificare la cronologia della campagna per un singolo lead o contatto ed eseguire i rapporti sulle campagne. [!DNL Marketo Measure] deve essere in grado di leggere e scrivere sull’oggetto campaign.

**Risoluzione dei problemi aggiuntiva**

Se [!DNL Marketo Measure] riscontra ancora problemi durante la lettura o la scrittura di dati. Potrebbe essere utile esaminare i seguenti aspetti:

* Accesso a [!DNL Salesforce] Code

Se l’utente dedicato non ha accesso ai lead nelle code, non può modificarli con [!DNL Marketo Measure] dati. A tale scopo, è possibile avere un ruolo nella gerarchia che consenta l&#39;accesso alle code o ai singoli utenti.

* Sicurezza e accessibilità a livello di campo

La sicurezza a livello di campo e l’accessibilità del campo sono correlate, ma presentano alcune differenze chiave. La sicurezza a livello di campo definisce la visibilità del campo per un determinato profilo, mentre l’accessibilità dei campi determina se un campo è modificabile in base alla sicurezza a livello di campo e alla configurazione del layout di pagina. Utilizzo di [!DNL Marketo Measure] set di autorizzazioni del pacchetto verranno ricevute le impostazioni di protezione degli oggetti campo necessarie. In alcuni casi, per ottenere la corretta accessibilità dei campi, l’utente connesso deve disporre di [!DNL Marketo Measure] nei layout di pagina. [!DNL Marketo Measure] i campi nel layout consentono [!DNL Marketo Measure] dati in cui eseguire il mapping [!DNL Salesforce]. Questo dipenderà dal tuo [!DNL Salesforce] ambiente.

Di ogni organizzazione [!DNL Salesforce] ha esigenze individuali, ma ti forniamo i nostri requisiti per bilanciare [!DNL Marketo Measure] le esigenze di accesso con i protocolli di sicurezza. Non esitare a contattare [[!DNL Marketo Support]](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
