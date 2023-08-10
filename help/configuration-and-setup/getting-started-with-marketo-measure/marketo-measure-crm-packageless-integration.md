---
unique-page-id: 37356027
description: "[!DNL Marketo Measure] Integrazione senza pacchetti CRM - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] Integrazione senza pacchetti CRM"
exl-id: a4f31d82-63ec-4bb2-bc8b-d3495e61af4f
feature: Integration
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# [!DNL Marketo Measure] Integrazione senza pacchetti CRM {#marketo-measure-crm-packageless-integration}

Sappiamo che non tutti i team di marketing desiderano (o hanno accesso) eseguire rapporti di marketing al di fuori del sistema CRM, sia per via dell’accesso limitato, della proprietà del sistema CRM, di tempi di realizzazione più lunghi o di implicazioni legali. Andando lungo il percorso di [!DNL Marketo Measure] Quick Start consente di implementare ed eseguire in modo efficace [!DNL Marketo Measure] con il minor affidamento possibile sul sistema CRM.

## Standard [!DNL Marketo Measure] Installazione {#standard-marketo-measure-installation}

Attraverso lo standard [!DNL Marketo Measure] installazione, è necessario installare un [!DNL Salesforce] Pacchetto o [!DNL Microsoft Dynamics] Soluzione gestita. L’installazione include oggetti/entità personalizzati e campi personalizzati aggiunti al CRM che [!DNL Marketo Measure] può quindi scrivere i dati in.

Integrazione senza pacchetti con [!DNL Marketo Measure] è per i clienti che non desiderano creare oggetti/entità personalizzati o campi personalizzati nel CRM. È anche una buona opzione per i clienti che utilizzano un data warehouse esterno.

## Autorizzazioni {#permissions}

A [!DNL Marketo Measure] L’integrazione senza pacchetti CRM richiede ancora l’accesso a oggetti CRM standard come lead e contatti. Consigliamo vivamente a un utente dedicato di fungere da utente connesso, in quanto disporrà dei privilegi di accesso ai dati appropriati.

Per garantire che tutti i dati vengano estratti correttamente dal CRM, sono necessarie le seguenti impostazioni di sicurezza e accessibilità: Visualizza tutti i dati per il profilo dell’utente dedicato. Questo set di autorizzazioni fornisce [!DNL Marketo Measure] l&#39;accesso necessario per scaricare i dati dagli oggetti standard. Questo set di autorizzazioni è a livello di profilo.

## Configurare il provider di identità e le connessioni dati {#setup-your-identity-provider-and-data-connections}

Nelle guide seguenti, salta i passaggi per installare il [!DNL Salesforce] pacchetto o [!DNL Microsoft Dynamics] Managed Solution e seguire solo le autorizzazioni e le istruzioni di integrazione.

[!DNL Salesforce] clienti, fai clic su [qui](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md).

[!DNL Microsoft Dynamics] clienti, fai clic su [qui](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/microsoft-dynamics-crm-installation-guide.md).

Una volta completati tutti i passaggi precedenti, sei a posto. Se incontrate problemi durante il percorso, non esitate a contattare il vostro [!DNL Marketo Measure] rappresentante o [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!NOTE]
>
>Se inizi con [!DNL Marketo Measure] Integrazione senza pacchetti CRM sarà possibile installare il pacchetto Salesforce o la soluzione gestita Microsoft Dynamics in un secondo momento.
