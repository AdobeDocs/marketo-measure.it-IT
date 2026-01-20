---
description: Best practice per  [!DNL Marketo Measure] pacchetto CRM - [!DNL Marketo Measure]
title: 'Best practice per il pacchetto CRM [!DNL Marketo Measure] '
exl-id: 97ce0ff3-8aa5-4789-9ee0-25d68c001def
feature: Salesforce
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# Best practice per il pacchetto CRM [!DNL Marketo Measure] {#best-practices-for-marketo-measure-crm-package}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedere ancora &quot;Bizible&quot; nel tuo CRM. Questo è stato aggiornato e il rebranding verrà presto rispecchiato nel CRM.

## Panoramica {#overview}

[!DNL Marketo Measure] si integra sia con [!DNL Salesforce] che con [!DNL Microsoft Dynamics]. Questo documento si concentra sulle [!DNL Marketo Measure] best practice per i pacchetti CRM progettati per [!DNL Salesforce].

Durante l&#39;implementazione, i due pacchetti seguenti sarebbero stati installati nell&#39;istanza [!DNL Salesforce].

Pacchetto base: è il pacchetto base che include oggetti e campi personalizzati. Si consiglia di eseguire l’installazione all’interno di Produzione per tutti gli utenti.
Pacchetto di estensione per dashboard: questo è il nostro pacchetto di estensione per dashboard, che contiene tre dashboard predefiniti. Per tutti gli utenti, consigliamo di installare all’interno di Produzione. Questo è facoltativo, ma invitiamo i clienti a installarlo.

Questi pacchetti consentono agli utenti [!DNL Marketo Measure] di accedere facilmente ai dati dei punti di contatto in tutta la loro istanza [!DNL Salesforce]. Per verificare che i layout di pagina, i set di autorizzazioni, i report e le dashboard vengano presentati come previsto agli utenti di [!DNL Marketo Measure], è fondamentale verificare che questi pacchetti siano configurati correttamente.

## Best practice {#best-practice}

Quando implementi e gestisci il pacchetto [!DNL Marketo Measure] [!DNL Salesforce], tieni presenti le seguenti best practice.

* Verificare che tutti i membri del team necessari abbiano accesso alle cartelle dei report [!DNL Marketo Measure]. Ci dovrebbero essere 1-3 [!DNL Marketo Measure] cartelle (queste sono spiegate di seguito). Per aprire l&#39;accesso, l&#39;utente che ha installato i pacchetti deve condividere le cartelle dei report con gli utenti o i ruoli appropriati.
   * **Rapporti Buyer Touchpoint** - disponibili per tutti
   * **[!DNL Marketo Measure]rapporti di marketing basati sull&#39;account** - i rapporti verranno compilati solo per i clienti di livello 2 e superiore
   * **Dashboard di Buyer Touchpoint** - disponibili per tutti, anche se questo pacchetto è facoltativo.

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

Anche se la configurazione del pacchetto CRM è coperta durante l’implementazione iniziale, si consiglia di rivedere la configurazione del pacchetto CRM una volta all’anno. Questa verifica conferma che tutti i layout di pagina sono configurati correttamente e che tutti i membri del team appropriati hanno accesso ai report e alle dashboard di [!DNL Marketo Measure].

Altri motivi potrebbero determinare una revisione...

* Aggiunta di nuovi membri del gruppo
* Aggiornamenti ai layout di pagina [!DNL Salesforce]
* Migrazione da [!DNL Salesforce] Classic a Lightening
* Aggiornamenti al contratto [!DNL Marketo Measure]
* Verifica di avere installato la versione più recente del pacchetto dei punti di contatto dell&#39;acquirente in [!DNL Salesforce]

>[!NOTE]
>
>Se disattivi l’esportazione dei dati da Marketo Measure a Salesforce, i dati esistenti non verranno eliminati. Per rimuoverlo, seguire i passaggi descritti in [questo articolo della Guida di Salesforce](https://help.salesforce.com/s/articleView?language=en_US&id=sf.c360_a_delete_data_stream_records.htm&type=5){target="_blank"}.

>[!MORELIKETHIS]
>
>* [Aggiorna pacchetto Buyer Touchpoint](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md)
>* [[!DNL Marketo Measure] Set di autorizzazioni](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)
>* [Condivisione di report e dashboard](https://help.salesforce.com/s/articleView?language=en_US&id=analytics_share_folder.htm&type=0)
>* [Connetti Marketo Measure a Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/connect-marketo-measure-to-salesforce.md)
