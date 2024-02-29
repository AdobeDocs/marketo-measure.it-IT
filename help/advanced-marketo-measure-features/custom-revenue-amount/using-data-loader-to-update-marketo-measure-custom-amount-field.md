---
unique-page-id: 18874771
description: Utilizzo di Data Loader per l’aggiornamento [!DNL Marketo Measure] Campo importo personalizzato - [!DNL Marketo Measure]
title: Utilizzo di Data Loader per aggiornare il campo personalizzato Importo di Marketo Measure
exl-id: 55e91ac4-a835-48e0-a6ce-1d85b32aeac0
feature: Custom Revenue Amount
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 0%

---

# Utilizzo di Data Loader per l’aggiornamento [!DNL Marketo Measure] Campo importo personalizzato {#using-data-loader-to-update-marketo-measure-custom-amount-field}

[!DNL Marketo Measure] consiglia di utilizzare Data Loader come opzione pratica per aggiornare i valori delle opportunità quando si utilizza un campo personalizzato per le entrate (viene utilizzato il campo Importo predefinito) in [!DNL Marketo Measure]. Data Loader è da preferirsi rispetto all’utilizzo di [!DNL Marketo Measure] aggiorna lo script in quanto lo script richiede che gli utenti disabilitino tutte le regole di convalida Salesforce mentre [!DNL Marketo Measure] viene eseguito lo script.

## Utilizzo di Data Loader per l’aggiornamento [!DNL Marketo Measure] Campo importo personalizzato{#using-data-loader-to-update-marketo-measure-custom-amount-field-1}

1. Creare un foglio Excel con:

   * ID opportunità
   * Campo Importo opportunità personalizzato (campo dei ricavi preferiti)
   * [!DNL Marketo Measure] Campo Importo opportunità

1. Copia e incolla i valori dal campo delle entrate preferite nel [!UICONTROL [!DNL Marketo Measure] Opportunity Amount] campo. Quindi, aggiorna queste Opp utilizzando il file .csv.

**_In alternativa, puoi accedere a Salesforce e utilizzare una vista a elenco personalizzata per modificare in massa tutte le opportunità..._**

1. Crea una visualizzazione elenco personalizzata per tutte le opportunità.
1. L’aggiunta di un filtro per il campo delle entrate preferite non è vuota _e_ [!UICONTROL Marketo] Il campo Misura importo opportunità è vuoto.
1. Clic **[!UICONTROL Mass Edit]**, ma non cambiare niente.
1. Clic **[!UICONTROL Save]**. Questo attiverà il flusso di lavoro per compilare [!DNL Marketo Measure] Campi Importo opportunità con il campo Ricavi software.
