---
description: Note sulla versione corrente - [!DNL Marketo Measure] - Documentazione del prodotto
title: Note sulla versione corrente
exl-id: 64b8fce8-af7d-4991-b01e-3fcf375d14e7
feature: Release Notes
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Note sulla versione: 2023 {#release-notes-2023}

Di seguito sono elencate tutte le funzioni nuove e aggiornate per le versioni del 2023.

## Versione secondo trimestre {#q2-release}

<p>

**Consolidamento dei pacchetti Salesforce**

* Stiamo unendo tutti i pacchetti Salesforce in un unico pacchetto completo per migliorare l’esperienza utente e semplificarne l’utilizzo. I pacchetti V1, V2_EXT e Reporting verranno ritirati il prossimo trimestre. Il nuovo pacchetto combina tutte le funzioni precedenti, consentendo un tracciamento più efficiente e informazioni più approfondite sui clienti.
* I clienti che hanno già installato il pacchetto V2 devono aggiornarlo alla nuova versione consolidata.
* Sono stati aggiunti due nuovi campi per migliorare le funzionalità di reporting:
   * nome_modulo: ora disponibile negli oggetti BT/BAT, questo campo consente agli utenti di creare report basati sui nomi dei moduli.
   * user_touchpoint_id: questo campo consente agli utenti di creare rapporti con conteggi univoci dei punti di contatto degli utenti.
* [Questo articolo](/help/configuration-and-setup/marketo-measure-and-salesforce/salesforce-package-consolidation.md){target="_blank"} Include guide sulla ricreazione di report e dashboard dai pacchetti di reporting legacy.

**Aggiornamenti della versione API di Salesforce**

* Tutte le versioni API Salesforce delle classi Apex, inclusa la classe UserActivityContext, vengono aggiornate alle versioni supportate. (da 31,0 a 57,0)

**Installazione nuovo pacchetto**

* Il nuovo collegamento di installazione del pacchetto consolidato [si trova qui](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t1P000000VY6Z){target="_blank"}

### Cosa sta succedendo? {#whats-coming}

<p>

**Modifiche nell’archiviazione degli indirizzi IP**

* Non memorizzeremo più gli indirizzi IP nel nostro sistema in base a considerazioni sulla privacy. Continueremo a identificare e archiviare la geolocalizzazione dell’indirizzo IP, ma il formato cambierà (ad esempio, &quot;Stati Uniti&quot; in &quot;Stati Uniti&quot;).
