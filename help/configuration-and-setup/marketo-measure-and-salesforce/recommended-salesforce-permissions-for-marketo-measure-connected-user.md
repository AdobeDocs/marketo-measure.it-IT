---
unique-page-id: 18874696
description: ' [!DNL Salesforce] Autorizzazioni consigliate per [!DNL Marketo Measure] Utente connesso - [!DNL Marketo Measure]'
title: ' [!DNL Salesforce] Autorizzazioni consigliate per [!DNL Marketo Measure] Utente connesso'
exl-id: b74aa28b-4a7b-42d1-8df0-d1ae0ff1f338
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Autorizzazioni [!DNL Salesforce] consigliate per [!DNL Marketo Measure] utente connesso {#recommended-salesforce-permissions-for-marketo-measure-connected-user}

[!DNL Marketo Measure] invia e riceve dati tramite un utente [!DNL Salesforce] connesso all&#39;interno dell&#39;app [!DNL Marketo Measure].

Per inviare i dati dei punti di contatto all&#39;istanza [!DNL Salesforce], l&#39;utente connesso deve avere accesso a [!DNL Marketo Measure] oggetti personalizzati (ovvero, Buyer Touchpoint e Buyer Attribution Touchpoint) e a [!DNL Salesforce] oggetti standard come lead e contatti. Vedi [[!DNL Marketo Measure] in Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md).

[!DNL Salesforce] Le licenze utente amministratore possono fungere da utente connesso in quanto spesso dispongono dei privilegi di dati necessari per impostazione predefinita. Tuttavia, il tuo team potrebbe preferire l&#39;utilizzo di un utente di integrazione o di una licenza utente [!DNL Salesforce] dedicata per monitorare l&#39;impatto di [!DNL Marketo Measure] sulla tua istanza.

Per garantire che i dati di [!DNL Marketo Measure] scorrano con precisione, si consiglia di utilizzare le seguenti autorizzazioni:

* [!DNL Marketo Measure] Autorizzazioni Amministratore Impostate Per L&#39;Utente Dedicato

Il set di autorizzazioni gestite consente a un amministratore SFDC di creare, leggere, scrivere ed eliminare record da [!DNL Marketo Measure] oggetti.

* Visualizza e modifica set di autorizzazioni lead convertiti

Questo consente a [!DNL Marketo Measure] di decorare i lead dopo che sono stati convertiti in contatti. Se questo set di autorizzazioni non è abilitato, possono verificarsi significative lacune nel tracciamento dei dati. Puoi trovare ulteriori informazioni in [[!DNL Salesforce Trailblazer] community](https://help.salesforce.com/s/articleView?language=en_US&id=leads_view_edit_converted.htm&type=5).

* Casella di controllo [!DNL Salesforce] utente marketing

La casella di controllo [!UICONTROL Marketing User] consente all&#39;utente di creare campagne e utilizzare l&#39;Importazione guidata campagne. Se questa opzione non è selezionata, l’utente può solo visualizzare le campagne e la configurazione avanzata della campagna, modificare la cronologia della campagna per un singolo lead o contatto ed eseguire i rapporti sulle campagne. [!DNL Marketo Measure] deve essere in grado di leggere e scrivere nell&#39;oggetto della campagna.

**Risoluzione dei problemi aggiuntivi**

Se [!DNL Marketo Measure] riscontra ancora problemi durante la lettura o la scrittura dei dati, potrebbe essere utile analizzare i seguenti aspetti:

* Accesso a [!DNL Salesforce] code

Se l&#39;utente dedicato non ha accesso ai lead nelle code, non può modificare i lead con i dati [!DNL Marketo Measure]. A tale scopo, è possibile avere un ruolo nella gerarchia che consenta l&#39;accesso alle code o ai singoli utenti.

* Sicurezza e accessibilità a livello di campo

La sicurezza a livello di campo e l’accessibilità del campo sono correlate, ma presentano alcune differenze chiave. La sicurezza a livello di campo definisce la visibilità del campo per un determinato profilo, mentre l’accessibilità dei campi determina se un campo è modificabile in base alla sicurezza a livello di campo e alla configurazione del layout di pagina. Utilizzando i set di autorizzazioni del pacchetto [!DNL Marketo Measure], si ricevono le impostazioni di sicurezza necessarie per gli oggetti campo. A volte, per avere la corretta accessibilità dei campi, l&#39;utente connesso deve avere i campi [!DNL Marketo Measure] nei layout di pagina. I campi [!DNL Marketo Measure] nel layout consentono il mapping dei dati [!DNL Marketo Measure] in [!DNL Salesforce]. Dipende dall&#39;ambiente [!DNL Salesforce] specifico.

Ogni [!DNL Salesforce] organizzazione ha esigenze individuali, ma ti forniamo i nostri requisiti per bilanciare le esigenze di accesso a [!DNL Marketo Measure] con i tuoi protocolli di sicurezza. Non esitare a contattare [[!DNL Marketo Support]](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
