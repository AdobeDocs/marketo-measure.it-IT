---
description: Creazione di un profilo  [!DNL Marketo Measure]  - [!DNL Marketo Measure]
title: 'Creazione di un profilo  [!DNL Marketo Measure] '
exl-id: dab2e2cb-fbd3-464a-9bd7-e9bf153d9848
feature: Salesforce
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Creazione di un profilo [!DNL Marketo Measure] {#creating-a-marketo-measure-profile}

Scopri come creare un profilo [!DNL Marketo Measure]. La creazione di un profilo [!DNL Marketo Measure] garantisce che non si verifichino errori di convalida durante il push dei dati al CRM.

1. Crea un profilo [!DNL Marketo Measure] specifico:

   * Assegna il set di autorizzazioni amministratore [!DNL Marketo Measure]
   * Abilitare l&#39;autorizzazione per visualizzare e modificare i lead convertiti

   >[!NOTE]
   >Questo profilo può essere un clone di un profilo [!DNL System Admin]

1. Creato un utente [!DNL Marketo Measure] dedicato:

   * Assegna il nuovo profilo [!DNL Marketo Measure] a tale utente
   * Abilitare &quot;Utente di marketing&quot; come autorizzazione a livello di utente

1. Escludi questo profilo da tutti i trigger, i flussi di lavoro e i processi.
1. Accedi al tuo account [!DNL Marketo Measure] e autorizza nuovamente la connessione [!DNL Salesforce] con il nuovo utente:

   * Vai a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} e accedi con le nuove credenziali Salesforce di produzione utente
   * Seleziona &quot;[!UICONTROL Settings]&quot; nel menu a discesa &quot;[!UICONTROL My Account]&quot;
   * Seleziona &quot;[!UICONTROL Connections]&quot; nel raggruppamento &quot;[!UICONTROL Integrations]&quot;
   * Fare clic sull&#39;icona della chiave a destra della connessione [!DNL Salesforce] attualmente connessa e selezionare Riautorizza con Produzione. Quindi, se richiesto, accedi di nuovo con le nuove credenziali utente

   Fine.

   Per qualsiasi domanda sulla creazione di un profilo [!DNL Marketo Measure] dedicato, rivolgiti al team dell&#39;account Adobe (il tuo Account Manager) o al [supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
