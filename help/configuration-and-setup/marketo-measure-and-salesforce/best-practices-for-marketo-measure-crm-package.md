---
description: Best practice per [!DNL Marketo Measure] Pacchetto CRM - [!DNL Marketo Measure]
title: Best practice per [!DNL Marketo Measure] Pacchetto CRM
exl-id: 97ce0ff3-8aa5-4789-9ee0-25d68c001def
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# Best practice per [!DNL Marketo Measure] Pacchetto CRM {#best-practices-for-marketo-measure-crm-package}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedi ancora &quot;Bizible&quot; nel tuo CRM. Questo è stato aggiornato e il rebranding verrà presto rispecchiato nel CRM.

## Panoramica {#overview}

[!DNL Marketo Measure] si integra con entrambi [!DNL Salesforce] e [!DNL Microsoft Dynamics], questo documento si concentra sulla [!DNL Marketo Measure] best practice per i pacchetti CRM progettati per [!DNL Salesforce].

Durante l’implementazione, i due pacchetti seguenti sarebbero stati installati nel [!DNL Salesforce] dell&#39;istanza.

Pacchetto base: è il pacchetto base che include oggetti e campi personalizzati. Si consiglia di eseguire l’installazione all’interno di Produzione per tutti gli utenti.
Pacchetto di estensione per dashboard: questo è il nostro pacchetto di estensione per dashboard, che contiene tre dashboard predefiniti. Per tutti gli utenti, consigliamo di installare all’interno di Produzione. Questo è facoltativo, ma invitiamo i clienti a installarlo.

Questi pacchetti consentono [!DNL Marketo Measure] utenti di accedere facilmente ai dati dei punti di contatto in tutta la [!DNL Salesforce] dell&#39;istanza. La verifica della corretta configurazione di questi pacchetti è fondamentale per verificare che layout di pagina, set di autorizzazioni, rapporti e dashboard siano presentati al tuo [!DNL Marketo Measure] come previsto.

## Best practice {#best-practice}

Quando si implementano e si gestiscono le [!DNL Marketo Measure] [!DNL Salesforce] Pacchetto, tieni presenti le seguenti best practice.

* Conferma che tutti i membri del team necessari abbiano accesso a [!DNL Marketo Measure] cartelle di rapporti. Dovrebbe essere 1-3 [!DNL Marketo Measure] cartelle (illustrate di seguito). Per aprire l&#39;accesso, l&#39;utente che ha installato i pacchetti deve condividere le cartelle dei report con gli utenti o i ruoli appropriati.
   * **Rapporti sui punti di contatto dell&#39;acquirente** - disponibile per tutti
   * **[!DNL Marketo Measure]Rapporti di marketing basati sull’account** - i report verranno compilati solo per i clienti di livello 2 e superiore
   * **Dashboard dei punti di contatto dell&#39;acquirente** - disponibile per tutti, anche se questo pacchetto è facoltativo.

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

Anche se la configurazione del pacchetto CRM è coperta durante l’implementazione iniziale, si consiglia di rivedere la configurazione del pacchetto CRM una volta all’anno. Questa verifica conferma che tutti i layout di pagina sono configurati correttamente e che tutti i membri del team appropriato hanno accesso a [!DNL Marketo Measure] rapporti e dashboard.

Altri motivi potrebbero determinare una revisione...

* Aggiunta di nuovi membri del gruppo
* Aggiornamenti al tuo [!DNL Salesforce] layout di pagina
* Migrazione per [!DNL Salesforce] Da classico a schiarente
* Aggiornamenti al tuo [!DNL Marketo Measure] contratto
* Verifica di avere installato la versione più recente del pacchetto dei punti di contatto dell&#39;acquirente in [!DNL Salesforce]

>[!NOTE]
>
>Se disattivi l’esportazione dei dati da Marketo Measure a Salesforce, i dati esistenti non verranno eliminati. Per rimuoverlo, segui i passaggi descritti in [questo articolo della guida di Salesforce](https://help.salesforce.com/s/articleView?language=en_US&amp;id=sf.c360_a_delete_data_stream_records.htm&amp;type=5){target="_blank"}.

>[!MORELIKETHIS]
>
>* [Aggiorna pacchetto punto di contatto dell&#39;acquirente](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md)
>* [[!DNL Marketo Measure] Set di autorizzazioni](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)
>* [Condivisione di report e dashboard, cartella](https://help.salesforce.com/s/articleView?language=en_US&amp;id=analytics_share_folder.htm&amp;type=0)
>* [Connettere Marketo Measure a Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/connect-marketo-measure-to-salesforce.md)
