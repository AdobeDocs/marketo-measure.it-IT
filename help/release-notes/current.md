---
description: Note sulla versione corrente - [!DNL Marketo Measure] - Documentazione del prodotto
title: Note sulla versione corrente
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
source-git-commit: dc4fda07004398207fb5067eb42ecd9e8ffe8624
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# Note sulla versione: 2023 {#release-notes-2023}

Di seguito sono elencate tutte le funzioni nuove e aggiornate per le versioni del 2023.

## Versione Q4 {#q4-release}

<p>

**Scopri la riprogettazione del dashboard**

Tutti gli utenti di Marketo Measure sperimenteranno le nostre dashboard in-app riprogettate che combinano usabilità avanzata con valore aggiunto. Stiamo inoltre introducendo nuove metriche, come il &quot;ROI realizzato&quot;, che tiene conto del tipico ritardo tra gli investimenti di marketing e gli acquisti nei go-to-market B2B.

Il nuovo set di dashboard predefiniti dovrebbe essere introdotto gradualmente, a partire dalla prima settimana di ottobre fino alla fine dell’anno. Queste nuove dashboard verranno visualizzate automaticamente nelle istanze, insieme alle informazioni interne al prodotto e ai collegamenti alla documentazione.

* [Nuova guida per Discover Dashboard](/help/marketo-measure-discover-ui/dashboards/new-discover-dashboard-guide.md){target="_blank"}
* [Scopri nozioni di base sulla dashboard](/help/marketo-measure-discover-ui/dashboards/discover-dashboard-basics.md){target="_blank"}
* [Dashboard panoramica ricavi](/help/marketo-measure-discover-ui/dashboards/revenue-overview-dashboard.md){target="_blank"}
* [Dashboard ricavi attribuiti](/help/marketo-measure-discover-ui/dashboards/attributed-revenue-dashboard.md){target="_blank"}
* [Dashboard ROI](/help/marketo-measure-discover-ui/dashboards/roi-dashboard.md){target="_blank"}
* [Dashboard Passport](/help/marketo-measure-discover-ui/dashboards/passport-dashboard.md){target="_blank"}

>[!NOTE]
>
>Anche se le dashboard correnti diventeranno obsolete entro metà gennaio 2024, fino ad allora puoi utilizzare entrambe le versioni, garantendo una transizione senza intoppi.

### Obsoleti {#deprecations}

<p>

* **Campo &quot;custom_properties&quot;**

Nel data warehouse, il campo &quot;custom_properties&quot; funge da archivio per punti dati aggiuntivi non coperti dallo schema fisso. Memorizzato in formato JSON, l’utilizzo di questo campo è limitato e la sua integrazione con le query SQL può essere complicata, influendo sulle prestazioni. Dati questi fattori, abbiamo deciso di rendere obsoleto questo campo. Questa modifica interesserà principalmente il livello di elaborazione dei dati nell’archiviazione delle tabelle di Azure e i dati esportati nel data warehouse.

* **Relativo al pacchetto Dynamics**

   * Per rimanere connesso a Dynamics, installa la versione più recente del pacchetto, v6.12. Versioni precedenti `(<v6.12)` non sarà più supportato. Questo aggiornamento ottimizza la creazione di record storici per ridurre l’utilizzo dello storage.

   * Il metodo obsoleto di OAuth con RefreshToken diventerà obsoleto. Fare riferimento a [questa guida](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/oauth-with-azure-active-directory-for-dynamics-crm.md){target="_blank"} per aggiornare le credenziali in modo da rispettare le best practice di Microsoft relative all&#39;utilizzo di ClientSecret.

### Cosa sta succedendo? {#q4-whats-coming}

<p>

**Reporting personalizzato in-app**

I clienti di Marketo Measure, per la prima volta, potranno creare e salvare i propri rapporti direttamente nell’app. Questo farà seguito al rilascio delle dashboard predefinite all’inizio del 2024.

<br>

## Versione secondo trimestre {#q2-release}

<p>

* **Consolidamento dei pacchetti Salesforce**

Stiamo unendo tutti i pacchetti Salesforce in un unico pacchetto completo per migliorare l’esperienza utente e semplificarne l’utilizzo. I pacchetti V1, V2_EXT e Reporting verranno ritirati il prossimo trimestre. Il nuovo pacchetto combina tutte le funzioni precedenti, consentendo un tracciamento più efficiente e informazioni più approfondite sui clienti.

I clienti che hanno già installato il pacchetto V2 devono aggiornarlo alla nuova versione consolidata.

Sono stati aggiunti due nuovi campi per migliorare le funzionalità di reporting:

* nome_modulo: ora disponibile negli oggetti BT/BAT, questo campo consente agli utenti di creare report basati sui nomi dei moduli.
* user_touchpoint_id: questo campo consente agli utenti di creare rapporti con conteggi univoci dei punti di contatto degli utenti.

[Questo articolo](/help/configuration-and-setup/marketo-measure-and-salesforce/salesforce-package-consolidation.md){target="_blank"} Include guide sulla ricreazione di report e dashboard dai pacchetti di reporting legacy.

* **Aggiornamenti della versione API di Salesforce**

Tutte le versioni API Salesforce delle classi Apex, inclusa la classe UserActivityContext, vengono aggiornate alle versioni supportate. (da 31,0 a 57,0)

* **Installazione nuovo pacchetto**

Il nuovo collegamento di installazione del pacchetto consolidato [si trova qui](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t1P000000VY6Z){target="_blank"}

### Cosa sta succedendo? {#q2-whats-coming}

<p>

**Modifiche nell’archiviazione degli indirizzi IP**

Non memorizzeremo più gli indirizzi IP nel nostro sistema in base a considerazioni sulla privacy. Continueremo a identificare e archiviare la geolocalizzazione dell’indirizzo IP, ma il formato cambierà (ad esempio, &quot;Stati Uniti&quot; in &quot;Stati Uniti&quot;).
