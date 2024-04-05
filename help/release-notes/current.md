---
description: Note sulla versione corrente - [!DNL Marketo Measure]
title: Note sulla versione corrente
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
source-git-commit: 4a3b8a1df9d8a675d977b08693b9d7facb64bc02
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Note sulla versione: 2024 {#release-notes-2024}

Di seguito trovi tutte le funzioni nuove e aggiornate per le versioni del 2024.

## Versione secondo trimestre {#q2-release}

<p>

**Funzionalità Marketo Measure obsolete in risposta al ritiro graduale dei cookie di terze parti**

In risposta a crescenti preoccupazioni sulla privacy, i cookie di terze parti vengono gradualmente eliminati, con la scadenza Q3 2024 di Google Chrome che segnala la loro fine. Marketo Measure renderà obsolete alcune funzioni dipendenti dai cookie di terze parti, in particolare il tracciamento tra domini diversi e l’attribuzione view-through, che si basano sul cookie di impression Google/DoubleClick. Questa modifica non influirà su altre funzionalità di Marketo Measure o sull’utilizzo di cookie di prime parti. Seguendo la timeline di Google, queste funzionalità dovrebbero diventare obsolete entro il 1° giugno, anche se i dati raccolti prima di questa data saranno ancora accessibili ai clienti.

* [Adattamento a cookie di terze parti obsoleti in Marketo Measure](https://nation.marketo.com/t5/employee-blogs/adapting-to-third-party-cookie-deprecation-in-marketo-measure/ba-p/345110){target="_blank"}
* [Cookie di Marketo Measure](/help/marketo-measure-tracking/setting-up-tracking/marketo-measure-cookies.md){target="_blank"}

**Rollout graduale della gestione avanzata degli errori**

Stiamo introducendo un rollout graduale della gestione avanzata degli errori per i processi di esportazione, a partire dalle notifiche immediate in-app per gli errori di autorizzazione e dalla transizione del 25 aprile a un nuovo approccio in cui i processi di esportazione verranno messi in pausa al momento dell’errore. Questa modifica mira a migliorare l’integrità e la visibilità dei dati, garantendo processi di gestione dei dati più fluidi e affidabili per i nostri utenti. Per garantire una transizione senza problemi e un&#39;interruzione minima delle operazioni, le modifiche vengono implementate in due fasi:

* Disponibilità immediata di notifiche Pulse: riceverai notifiche Pulse in-app per gli errori di autorizzazione durante i processi di esportazione. Ciò non interromperà le esportazioni, ma ti aiuterà a conoscere gli errori senza influenzare i processi correnti.
* Implementazione del processo in pausa il 25 aprile: a partire dal 25 aprile, se il sistema rileva un errore di autorizzazione durante un processo di esportazione, il processo verrà sospeso per garantire che non vengano saltati dati. Riceverai una notifica di eventuali problemi e, una volta corrette le autorizzazioni, il processo di esportazione riprenderà senza problemi da dove è stato interrotto.

_Perché è importante_

Integrità dei dati migliorata e integrazione a prova di futuro: il processo viene interrotto al primo segnale di guasto per evitare la perdita di dati e garantire l’accuratezza. Ciò consente una rapida risoluzione dei problemi, migliorando la qualità dell’esportazione dei dati e l’affidabilità del sistema.

Visibilità immediata: l’introduzione delle notifiche Pulse consente di rispondere rapidamente agli errori di autorizzazione, evitando potenziali impatti sulle operazioni.

_Supporto della transizione_

Per aiutarti ad adattarti a questa modifica, [abbiamo creato la documentazione](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"} con descrizioni chiare degli errori e passaggi completi per la risoluzione dei problemi.

**Azione richiesta per l’integrazione di LinkedIn**

LinkedIn ha rilasciato di recente una versione aggiornata dell’API di sincronizzazione dei lead. Per evitare interruzioni, autentica nuovamente la connessione LinkedIn nell’istanza Marketo Measure entro il 20 maggio.
