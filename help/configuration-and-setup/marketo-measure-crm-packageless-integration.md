---
description: Integrazione senza pacchetti CRM [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Integrazione senza pacchetti CRM [!DNL Marketo Measure]
exl-id: a4f31d82-63ec-4bb2-bc8b-d3495e61af4f
feature: Integration
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---


# Integrazione senza pacchetti CRM [!DNL Marketo Measure] {#marketo-measure-crm-packageless-integration}

Non tutti i team di marketing desiderano (o hanno accesso) eseguire rapporti di marketing al di fuori del sistema CRM, sia per via dell’accesso limitato, della proprietà del sistema CRM, di tempi di realizzazione più lunghi o di implicazioni legali. Andando lungo il percorso di [!DNL Marketo Measure] Quick Start è possibile implementare ed eseguire [!DNL Marketo Measure] in modo efficace, affidandosi il meno possibile al CRM.

## Installazione standard di [!DNL Marketo Measure] {#standard-marketo-measure-installation}

Tramite l&#39;installazione standard di [!DNL Marketo Measure], è necessario installare un pacchetto [!DNL Salesforce] o una soluzione gestita [!DNL Microsoft Dynamics]. L&#39;installazione include oggetti/entità personalizzati e campi personalizzati aggiunti al CRM a cui [!DNL Marketo Measure] può quindi scrivere i dati.

Un&#39;integrazione senza pacchetti con [!DNL Marketo Measure] è destinata ai clienti che non desiderano creare oggetti/entità o campi personalizzati nel CRM. È inoltre una buona opzione per i clienti che utilizzano un Data Warehouse esterno.

## Autorizzazioni {#permissions}

Un&#39;integrazione senza pacchetti CRM [!DNL Marketo Measure] richiede ancora l&#39;accesso agli oggetti CRM standard come lead e contatti. È consigliabile che un utente dedicato funga da utente connesso, in quanto dispone dei privilegi di accesso ai dati appropriati.

Per garantire che tutti i dati vengano estratti correttamente dal CRM, sono necessarie le seguenti impostazioni di sicurezza e accessibilità: Visualizza tutti i dati per il profilo dell’utente dedicato. Questo set di autorizzazioni concede a [!DNL Marketo Measure] l&#39;accesso necessario per scaricare i dati dagli oggetti standard. Questo set di autorizzazioni è a livello di profilo.

## Configurare il provider di identità e le connessioni dati {#setup-your-identity-provider-and-data-connections}

Nelle guide seguenti, ignorare i passaggi per installare il pacchetto [!DNL Salesforce] o la soluzione gestita [!DNL Microsoft Dynamics] e seguire solo le autorizzazioni e le istruzioni di integrazione.

I clienti [!DNL Salesforce] fanno clic [qui](/help/configuration-and-setup/install-set-up.md).

I clienti [!DNL Microsoft Dynamics] fanno clic [qui](/help/microsoft-dynamics-crm-installation-guide.md).

Dopo aver completato questi passaggi, l’integrazione dovrebbe essere operativa. In caso di problemi, contatta il tuo rappresentante [!DNL Marketo Measure] o il [supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!NOTE]
>Se si inizia con l&#39;integrazione senza pacchetti di CRM [!DNL Marketo Measure], sarà possibile installare il pacchetto Salesforce o la soluzione gestita Microsoft Dynamics in un secondo momento.
