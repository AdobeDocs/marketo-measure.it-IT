---
description: Utilizzo di Data Loader per aggiornare le linee guida del campo Importo personalizzato di Marketo Measure per gli utenti di Marketo Measure
title: Utilizzo di Data Loader per aggiornare il campo personalizzato Importo di Marketo Measure
exl-id: 55e91ac4-a835-48e0-a6ce-1d85b32aeac0
feature: Custom Revenue Amount
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Utilizzo di Data Loader per aggiornare il campo personalizzato dell&#39;importo [!DNL Marketo Measure] {#using-data-loader-to-update-marketo-measure-custom-amount-field}

[!DNL Marketo Measure] consiglia di utilizzare Data Loader come opzione pratica per aggiornare i valori dell&#39;opportunità quando si utilizza un campo di ricavi personalizzato (viene utilizzato il campo Quantità preconfigurato) in [!DNL Marketo Measure]. Data Loader è da preferirsi rispetto all&#39;utilizzo dello script di aggiornamento [!DNL Marketo Measure], in quanto richiede agli utenti di disabilitare tutte le regole di convalida di Salesforce durante l&#39;esecuzione dello script [!DNL Marketo Measure].

## Utilizzo di Data Loader per aggiornare il campo personalizzato dell&#39;importo [!DNL Marketo Measure]{#using-data-loader-to-update-marketo-measure-custom-amount-field-1}

1. Creare un foglio Excel con:

   * ID opportunità
   * Campo Importo opportunità personalizzato (campo dei ricavi preferiti)
   * Campo Importo opportunità [!DNL Marketo Measure]

1. Copia e incolla i valori dal campo delle entrate preferite nel campo [!UICONTROL [!DNL Marketo Measure] Opportunity Amount]. Quindi, aggiorna queste Opp utilizzando il file .csv.

**_In alternativa, è possibile accedere a Salesforce e utilizzare una visualizzazione elenco personalizzata per modificare in massa tutte le opportunità..._**

1. Crea una visualizzazione elenco personalizzata per tutte le opportunità.
1. L&#39;aggiunta di un filtro per il campo ricavi preferiti non è vuota _e_ il campo Importo opportunità misura [!UICONTROL Marketo] è vuoto.
1. Fai clic su **[!UICONTROL Mass Edit]**, ma non modificare nulla.
1. Fare clic su **[!UICONTROL Save]**. In questo modo il flusso di lavoro compilerà i campi Importo opportunità [!DNL Marketo Measure] con il campo Ricavo software.
