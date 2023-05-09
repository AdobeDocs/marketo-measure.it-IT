---
description: Note sulla versione corrente - [!DNL Marketo Measure] - Documentazione del prodotto
title: Note sulla versione corrente
source-git-commit: 8e8ddd80d69102455fa678a32f31a9fe8319822c
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Note sulla versione: 2023 {#release-notes-2023}

Di seguito sono elencate tutte le funzioni nuove e aggiornate per le versioni del 2023.

## Versione Q2 {#q2-release}

<p>

**Consolidamento pacchetti Salesforce**

* Stiamo unendo tutti i pacchetti Salesforce in un unico pacchetto completo per una migliore esperienza utente e un utilizzo semplificato. I pacchetti V1, V2_EXT e Reporting verranno ritirati il prossimo trimestre. Il nuovo pacchetto combina tutte le funzioni precedenti, consentendo un monitoraggio più efficiente e approfondendo le informazioni sui clienti.
* I clienti che hanno già installato il pacchetto V2 devono aggiornarlo alla nuova versione consolidata.
* Sono stati aggiunti due nuovi campi per migliorare le funzionalità di reporting:
   * nome_modulo: Ora disponibile negli oggetti BT/BAT, questo campo consente agli utenti di creare rapporti basati sui nomi dei moduli.
   * user_touchpoint_id: Questo campo consente agli utenti di creare rapporti con conteggi univoci dei punti di contatto dell’utente.
* [Questo articolo](/help/configuration-and-setup/marketo-measure-and-salesforce/salesforce-package-consolidation.md){target="_blank"} include guide sulla ricreazione di report e dashboard dai pacchetti di reporting legacy.

**Aggiornamenti alla versione API di Salesforce**

* Tutte le versioni API Salesforce delle classi Apex, inclusa la classe UserActivityContext, vengono aggiornate alle versioni supportate. (da 31.0 a 57.0)

**Nuova installazione del pacchetto**

* Il nuovo collegamento all&#39;installazione del pacchetto consolidato [si trova qui](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t1P000000VY6Z){target="_blank"}

### Che sta venendo? {#whats-coming}

<p>

**Modifiche all&#39;archivio indirizzi IP**

* Gli indirizzi IP non verranno più archiviati nel nostro sistema per considerazioni sulla privacy. Continueremo a identificare e memorizzare la geolocalizzazione dell&#39;indirizzo IP, ma il formato cambierà (ad esempio, &quot;Stati Uniti&quot; a &quot;Stati Uniti&quot;).
