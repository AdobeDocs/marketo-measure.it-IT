---
description: Note sulla versione corrente - [!DNL Marketo Measure]
title: Note sulla versione corrente
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
source-git-commit: 24cb14c0f5db13c791966d21b4a1145b655ecc1b
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 0%

---

# Note sulla versione: 2024 {#release-notes-2024}

Di seguito trovi tutte le funzioni nuove e aggiornate per le versioni del 2024.

## Versione Q4 {#q4-release}

### Regole di segmento migliorate

Ora puoi creare segmenti utilizzando i campi Membro di Campaign e Campaign, oltre ai campi Punto di contatto e Contatto. Questo miglioramento consente di analizzare e sezionare i dati in modo più efficace in Discover.

![Regole segmento per membri](assets/campaign-member.png)

### Aggiornamento: impostazione di gestione degli errori per le esportazioni CRM

Abbiamo ascoltato il tuo feedback sull’approccio alla sospensione dei processi e stiamo introducendo una nuova funzione nell’interfaccia utente. A partire da oggi, è possibile scegliere se i processi di esportazione devono essere messi in pausa quando si verificano errori. Utilizza il nuovo interruttore in **Il mio account** > **Impostazioni** → **CRM** → **Generale**. Questo switch è attivato per impostazione predefinita per migliorare l’integrità e la visibilità dei dati. Tuttavia, se preferisci non utilizzare questa funzione, puoi disattivarla nell’interfaccia utente e i processi di esportazione riprenderanno. Questo aggiornamento è progettato per migliorare l’affidabilità dei processi di gestione dei dati, fornendo al contempo un maggiore controllo.

#### Date chiave e rollout graduale

Disponibilità immediata: l’interruttore è ora attivo nell’interfaccia utente ed è abilitato per impostazione predefinita per impedire che i dati vengano ignorati durante i processi di esportazione. Se preferisci che i processi di esportazione continuino a essere in esecuzione nonostante gli errori, disattiva l’interruttore.

Processo in pausa attivazione il 1° ottobre: a partire dal 1° ottobre 2024, se l’interruttore è attivo e si verifica un errore a livello di record durante un processo di esportazione, il processo viene sospeso per garantire che non venga perso alcun dato. Questi errori sono in genere dovuti a autorizzazioni mancanti, regole di convalida personalizzate applicate in modo errato o problemi nei flussi di lavoro/trigger. Riceverai notifiche relative al problema e, una volta corretto, il processo di esportazione riprenderà dal punto di interruzione. Se rinunci alla sospensione del processo, riceverai comunque le notifiche dei problemi e, una volta corretti, i record saltati vengono automaticamente riesportati.

#### Perché è importante

**Integrità dei dati migliorata e sicurezza dell&#39;integrazione per il futuro:** sospendendo il processo al primo segnale di un problema, si evita la perdita di dati e si garantisce l&#39;accuratezza. Ciò consente una rapida risoluzione degli errori, con conseguente miglioramento della qualità dell&#39;esportazione dei dati e dell&#39;affidabilità complessiva del sistema.

**Visibilità immediata:** Tramite notifiche Pulse, riceverai avvisi tempestivi per gli errori di autorizzazione, consentendo risposte tempestive e riducendo al minimo il potenziale impatto sulle operazioni.

#### Supporto della transizione

Per aiutarti ad adattarti a questa modifica, abbiamo creato la documentazione sulla nuova funzione e chiare descrizioni degli errori con passaggi completi per la risoluzione dei problemi.

* Nuova documentazione: [Impostazione gestione errori per esportazioni CRM](/help/configuration-and-setup/marketo-measure-and-salesforce/crm-error-handling.md)
* [Notifiche di errore](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md)

## Versione Q3 {#q3-release}

<p>

**Promemoria: campo Salesforce obsoleto - 14 giugno**

Come annunciato lo scorso anno, [elimineremo gradualmente i processi di esportazione negli oggetti lead/contatto](https://nation.marketo.com/t5/employee-blogs/marketo-measure-salesforce-lead-and-contact-field-deprecation-06/ba-p/350179){target="_blank"} per semplificare l&#39;integrazione ed eliminare la necessità di esportare in oggetti standard Salesforce. Puoi ottenere gli stessi dati dagli oggetti punto di contatto seguendo i passaggi [qui documentati](/help/release-notes/previous-releases/2023.md#deprecations){target="_blank"}. Inoltre, condivideremo la documentazione sulla creazione di flussi di lavoro per aggiungere questi dati all’oggetto Lead/Contatto. La rimozione avrà effetto dal 14 giugno 2024.

Questa modifica apporterà due vantaggi chiave:

* **Costi API Salesforce ridotti**: i clienti possono aspettarsi di ridurre i costi API Salesforce di circa il 10%.
* **Integrazione semplificata**: il maggior numero di errori nei processi di esportazione è correlato a questi processi. La loro rimozione semplificherà notevolmente la nostra integrazione.

**Dashboard opportunità attribuita**

Siamo entusiasti di presentare il nuovo [dashboard delle opportunità attribuite](/help/marketo-measure-discover-ui/dashboards/attributed-opportunity-dashboard.md){target="_blank"}, progettato per fornire una visione completa del modo in cui le attività di marketing contribuiscono alle opportunità di pipeline sia nascenti che mature. Questa dashboard consente di approfondire i dettagli di ogni opportunità aperta e chiusa attribuibile alle strategie, con la flessibilità di filtrare per fase di opportunità. Fornisce informazioni sui canali, i sottocanali o le campagne con la classificazione più alta in termini di quantità di opportunità attribuita e visualizza l’importo totale dell’opportunità attribuita insieme al conteggio delle opportunità aperte e chiuse attribuite.

**Sincronizzazione cookie di Marketo Engage per Marketo Measure Ultimate**

Marketo Engage Cookie Sync è ora disponibile per Marketo Measure Ultimate. Per utilizzare questa funzione:

1. Nella pagina Schemi AEP, modifica lo schema Persona B2B e aggiungi il gruppo di campi &quot;Dettagli persona Marketo Engage&quot;.
1. Quando acquisisci i dati su MMU, mappa il campo ID cookie dal gruppo di campi al campo Cookie dal Marketo Engage.

**Stadi Boomerang abilitati per i clienti di livello 2**

Precedentemente disponibile solo per i clienti di livello 3, la funzione Boomerang Stage è disponibile anche per tutti i clienti di livello 2 a partire dal 13 giugno 2024. Per informazioni più dettagliate su questa funzione, consulta la documentazione di seguito.

* [Stadi di Boomerang e punti di contatto](/help/advanced-marketo-measure-features/boomerang/boomerang-stages-and-touchpoints.md){target="_blank"}
* [Configurazione fasi boomerang](/help/advanced-marketo-measure-features/boomerang/setting-up-boomerang-stages.md){target="_blank"}
* [Scenari fase boomerang](/help/advanced-marketo-measure-features/boomerang/boomerang-stage-scenarios.md){target="_blank"}

<p>

## Versione secondo trimestre {#q2-release}

<p>

**Funzionalità Marketo Measure obsolete in risposta alla disattivazione graduale dei cookie di terze parti**

In risposta ai crescenti problemi di privacy, i cookie di terze parti vengono gradualmente eliminati, con la scadenza del terzo trimestre del 2024 di Google Chrome che segnala la loro fine. Marketo Measure renderà obsolete alcune funzioni dipendenti dai cookie di terze parti, in particolare il tracciamento tra domini diversi e l’attribuzione view-through, che si basano sul cookie di impression Google/DoubleClick. Questa modifica non influirà su altre funzionalità di Marketo Measure o sull’utilizzo di cookie di prime parti. Seguendo la timeline di Google, queste funzionalità dovrebbero diventare obsolete entro il 1° giugno, anche se i dati raccolti prima di questa data saranno ancora accessibili ai clienti.

* [Adattamento a cookie di terze parti obsoleti in Marketo Measure](https://nation.marketo.com/t5/employee-blogs/adapting-to-third-party-cookie-deprecation-in-marketo-measure/ba-p/345110){target="_blank"}
* [Cookie Marketo Measure](/help/marketo-measure-tracking/setting-up-tracking/marketo-measure-cookies.md){target="_blank"}

**Rollout graduale della gestione avanzata degli errori**

Stiamo introducendo un rollout graduale della gestione avanzata degli errori per i processi di esportazione, a partire da notifiche immediate in-app per gli errori di autorizzazione e dalla transizione a un nuovo approccio in cui i processi di esportazione verranno messi in pausa al punto dell’errore. Questa modifica mira a migliorare l’integrità e la visibilità dei dati, garantendo processi di gestione dei dati più fluidi e affidabili per i nostri utenti. Per garantire una transizione senza problemi e un&#39;interruzione minima delle operazioni, le modifiche vengono implementate in due fasi:

* Disponibilità immediata di notifiche Pulse: riceverai notifiche Pulse in-app per gli errori di autorizzazione durante i processi di esportazione. Ciò non interromperà le esportazioni, ma ti aiuterà a conoscere gli errori senza influenzare i processi correnti.
* Implementazione della sospensione del processo il 25 aprile: **POSTICIPATA** - Dopo aver preso in considerazione il feedback degli utenti di Marketo Measure, abbiamo deciso di posticipare l&#39;implementazione della sospensione dei processi di esportazione al punto di errore, originariamente pianificata per il 25 aprile. Riconosciamo che arrestare i posti di lavoro potrebbe non essere l&#39;approccio più efficace. Ci impegniamo a trovare una soluzione migliore che mantenga l&#39;integrità dei dati e riduca al minimo le interruzioni. Non riusciremo a modificare il nostro sistema attuale finché non saremo in grado di garantire una soluzione più in linea con le esigenze dei nostri utenti.

_Perché È Importante_

Integrità dei dati migliorata e integrazione a prova di futuro: il processo viene interrotto al primo segnale di guasto per evitare la perdita di dati e garantire l’accuratezza. Ciò consente una rapida risoluzione dei problemi, migliorando la qualità dell’esportazione dei dati e l’affidabilità del sistema.

Visibilità immediata: l’introduzione delle notifiche Pulse consente di rispondere rapidamente agli errori di autorizzazione, evitando potenziali impatti sulle operazioni.

_Supporto della transizione_

Per aiutarti ad adattarti a questa modifica, [abbiamo creato la documentazione](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"} con descrizioni chiare degli errori e passaggi completi per la risoluzione dei problemi.

<br>

**Azione richiesta per l&#39;integrazione di LinkedIn**

LinkedIn ha rilasciato di recente una versione aggiornata dell’API di sincronizzazione dei lead. Per evitare interruzioni, autentica nuovamente la connessione LinkedIn nell’istanza Marketo Measure entro il 20 maggio.

