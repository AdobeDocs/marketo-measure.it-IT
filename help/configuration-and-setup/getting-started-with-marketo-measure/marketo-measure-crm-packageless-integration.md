---
unique-page-id: 37356027
description: "[!DNL Marketo Measure] Integrazione senza pacchetti CRM - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] Integrazione senza pacchetti CRM"
exl-id: a4f31d82-63ec-4bb2-bc8b-d3495e61af4f
source-git-commit: 993a326c377b3b6ff48c4e0114b59297f9ca2ca6
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# [!DNL Marketo Measure] Integrazione senza pacchetti CRM {#marketo-measure-crm-packageless-integration}

Sappiamo che non tutti i team Marketing desiderano (o hanno accesso) eseguire rapporti di marketing fuori dal CRM, sia per via di un accesso limitato, della proprietà CRM, di un tempo di valutazione più lungo o di implicazioni legali. Andando lungo il percorso [!DNL Marketo Measure] Quick Start consente di implementare ed eseguire in modo efficace [!DNL Marketo Measure] con il minor ricorso possibile al CRM.

## Standard [!DNL Marketo Measure] Installazione {#standard-marketo-measure-installation}

Attraverso lo standard [!DNL Marketo Measure] installazione, è necessario installare un [!DNL Salesforce] Pacchetto o [!DNL Microsoft Dynamics] Soluzione gestita. L&#39;installazione include oggetti/entità personalizzati e campi personalizzati che vengono aggiunti al CRM che [!DNL Marketo Measure] può quindi scrivere dati in.

Integrazione senza pacchetti con [!DNL Marketo Measure] è per i clienti che non desiderano creare oggetti/entità personalizzati o campi personalizzati nel CRM. È inoltre una buona opzione per i clienti che utilizzano un data warehouse esterno.

## Autorizzazioni {#permissions}

A [!DNL Marketo Measure] L&#39;integrazione senza pacchetti CRM richiede ancora l&#39;accesso a oggetti CRM standard come Lead e Contatti. Consigliamo vivamente un utente dedicato che funga da utente connesso, in quanto avrà i privilegi di accesso ai dati appropriati.

Per garantire che tutti i dati siano correttamente estratti dal CRM, è necessario disporre delle seguenti impostazioni di sicurezza e accessibilità: Visualizza tutti i dati per il profilo dell&#39;utente dedicato. Questo set di autorizzazioni fornisce [!DNL Marketo Measure] l’accesso necessario per scaricare i dati dagli oggetti standard. Questo set di autorizzazioni è a livello di profilo.

## Configurazione del provider di identità e delle connessioni dati {#setup-your-identity-provider-and-data-connections}

Nelle guide seguenti, salta i passaggi per installare il [!DNL Salesforce] pacchetto o [!DNL Microsoft Dynamics] Soluzione gestita e seguire solo le istruzioni di autorizzazione e integrazione.

[!DNL Salesforce] clienti, fai clic su [qui](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md).

[!DNL Microsoft Dynamics] clienti, fai clic su [qui](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/microsoft-dynamics-crm-installation-guide.md).

Una volta completati tutti i passaggi di cui sopra, siete pronti ad andare. Se incontri qualche problema lungo il percorso, non esitare a contattarti [!DNL Marketo Measure] rappresentante o [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target=&quot;_blank&quot;}.

>[!NOTE]
>
>Se si inizia con [!DNL Marketo Measure] Integrazione senza pacchetti di gestione delle relazioni con i clienti potrai installare il pacchetto Salesforce o la soluzione gestita da Microsoft Dynamics in un secondo momento.
