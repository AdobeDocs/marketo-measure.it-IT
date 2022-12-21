---
description: Best practice per [!DNL Marketo Measure] Pacchetto di gestione delle relazioni con i clienti - [!DNL Marketo Measure] - Documentazione del prodotto
title: Best practice per [!DNL Marketo Measure] Pacchetto di gestione delle relazioni con i clienti
exl-id: 97ce0ff3-8aa5-4789-9ee0-25d68c001def
source-git-commit: 00268f49ff6e5dfc105fa7ea21837375eae49647
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# Best practice per [!DNL Marketo Measure] Pacchetto di gestione delle relazioni con i clienti {#best-practices-for-marketo-measure-crm-package}

>[!NOTE]
>
>È possibile visualizzare istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella nostra documentazione, ma vedi ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riflesso nel tuo CRM presto.

## Panoramica {#overview}

[!DNL Marketo Measure] si integra con [!DNL Salesforce] e [!DNL Microsoft Dynamics], questo documento si concentrerà sul [!DNL Marketo Measure] best practice per i pacchetti CRM progettati per [!DNL Salesforce].

Durante l&#39;implementazione, i due pacchetti seguenti sarebbero stati installati nel tuo [!DNL Salesforce] istanza.

Pacchetto di base: Questo è il nostro pacchetto base che include i nostri oggetti e campi personalizzati. È consigliabile installare in Produzione per tutti gli utenti.
Pacchetto estensione dashboard: Questo è il nostro pacchetto di estensione del dashboard, che contiene 3 dashboard predefiniti. È consigliabile installare in Produzione per tutti gli utenti. Questo è facoltativo, ma invitiamo i clienti a eseguire l’installazione.

Questi pacchetti consentono di [!DNL Marketo Measure] gli utenti possono accedere facilmente ai dati dei punti di contatto [!DNL Salesforce] istanza. La conferma della corretta configurazione di questi pacchetti è fondamentale per verificare che i layout di pagina, i set di autorizzazioni, i rapporti e le dashboard vengano presentati al tuo [!DNL Marketo Measure] come previsto.

## Best practice {#best-practice}

Quando si tratta di implementare e gestire il [!DNL Marketo Measure] [!DNL Salesforce] Crea un pacchetto con le seguenti best practice.

* Conferma che ogni membro del team necessario abbia accesso al [!DNL Marketo Measure] cartelle di report. Ci dovrebbe essere 1-3 [!DNL Marketo Measure] cartelle (queste sono spiegate di seguito). Per aprire l&#39;accesso, la persona che ha installato i pacchetti deve condividere le cartelle dei rapporti con gli utenti o i ruoli appropriati.
   * **Rapporti sui punti di contatto per gli acquirenti** - disponibile a tutti
   * **[!DNL Marketo Measure]Report di marketing basati su account** - i report verranno compilati solo per i clienti di livello 2 e superiore
   * **Dashboard punto di contatto dell&#39;acquirente** - disponibile a tutti, anche se questo pacchetto è facoltativo.

## Best practice per la manutenzione {#best-practice-for-maintenance}

Anche se la configurazione del pacchetto CRM è coperta durante l&#39;implementazione iniziale, ti consigliamo di rivedere la configurazione del pacchetto CRM una volta all&#39;anno. Questa revisione verifica che tutti i layout di pagina siano configurati correttamente e che tutti i membri del team appropriati abbiano accesso a [!DNL Marketo Measure] rapporti e dashboard.

Altri motivi potrebbero provocare una revisione...

* Aggiunta di nuovi membri del team
* Aggiornamenti [!DNL Salesforce] layout di pagina
* Migrazione per [!DNL Salesforce] Da classico a luminoso
* Aggiornamenti al [!DNL Marketo Measure] contratto
* Verifica di avere installato la versione più recente del pacchetto Punti di contatto per l&#39;acquirente in [!DNL Salesforce]

>[!NOTE]
>
>Quando disattivi l’esportazione di dati da Marketo Measure a Salesforce, non verranno rimossi i dati esistenti. Per rimuoverlo, segui i passaggi descritti in [questo articolo della guida Salesforce](https://help.salesforce.com/s/articleView?id=sf.c360_a_delete_data_stream_records.htm&amp;type=5){target=&quot;_blank&quot;}.

>[!MORELIKETHIS]
>
>* [Aggiorna pacchetto punto di contatto dell&#39;acquirente](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md)
>* [[!DNL Marketo Measure] Set di autorizzazioni](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)
>* [Condivisione di cartelle di report e dashboard](https://help.salesforce.com/articleView?id=analytics_share_folder.htm&amp;type=0)
>* [Collegare la misura Marketo a Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/connect-marketo-measure-to-salesforce.md)

