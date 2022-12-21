---
unique-page-id: 18874771
description: Utilizzo di Data Loader per l'aggiornamento [!DNL Marketo Measure] Campo Importo personalizzato - [!DNL Marketo Measure] - Documentazione del prodotto
title: Utilizzo di Data Loader per aggiornare il campo Importo personalizzato misura Marketo
exl-id: 55e91ac4-a835-48e0-a6ce-1d85b32aeac0
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Utilizzo di Data Loader per l&#39;aggiornamento [!DNL Marketo Measure] Campo Importo personalizzato {#using-data-loader-to-update-marketo-measure-custom-amount-field}

[!DNL Marketo Measure] consiglia di utilizzare Data Loader come opzione conveniente per aggiornare i valori delle opportunità quando si utilizza un campo Ricavo personalizzato (usiamo il campo Importo preconfigurato) in [!DNL Marketo Measure]. Data Loader è da preferirsi all&#39;utilizzo del [!DNL Marketo Measure] aggiorna lo script come script richiede agli utenti di disabilitare tutte le regole di convalida Salesforce mentre [!DNL Marketo Measure] viene eseguito lo script.

## Utilizzo di Data Loader per l&#39;aggiornamento [!DNL Marketo Measure] Campo Importo personalizzato{#using-data-loader-to-update-marketo-measure-custom-amount-field-1}

1. Crea un foglio excel con:

   * ID opportunità
   * Campo Importo opportunità personalizzato (campo Ricavo preferito)
   * [!DNL Marketo Measure] Campo Importo opportunità

1. Copia e incolla i valori dal campo Ricavo preferito in [!UICONTROL [!DNL Marketo Measure] Opportunity Amount] campo . Quindi, aggiorna queste Opps utilizzando il file .csv .

**_In alternativa, è possibile accedere a Salesforce e utilizzare una visualizzazione elenco personalizzata per modificare in massa tutte le opportunità..._**

1. Crea una visualizzazione Elenco personalizzato per tutte le opportunità.
1. Aggiungi un filtro per il campo Ricavo preferito non vuoto _e_ [!UICONTROL Marketo] Il campo Importo opportunità misura è vuoto.
1. Fai clic su **[!UICONTROL Mass Edit]** Ma non cambiate niente.
1. Clic **[!UICONTROL Save]**. Questo attiverà il flusso di lavoro per compilare il [!DNL Marketo Measure] Campi Importo opportunità con il campo Ricavo software.
