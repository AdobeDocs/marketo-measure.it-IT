---
description: Procedure consigliate per l'utilizzo di un importo di ricavi personalizzato - [!DNL Marketo Measure]
title: Procedure consigliate per l’utilizzo di un importo di ricavi personalizzato
exl-id: 553bd75a-512a-4733-a24b-8112eb420afc
feature: Custom Revenue Amount
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---


# Procedure consigliate per l’utilizzo di un importo di ricavi personalizzato {#best-practices-for-utilizing-a-custom-revenue-amount}

## Panoramica {#overview}

La funzionalità di base di [!DNL Marketo Measure] è la possibilità di assegnare il credito dei ricavi ai punti di contatto di marketing in tutto il percorso dell&#39;acquirente. La chiave per un&#39;attribuzione accurata dei ricavi è la capacità di [!DNL Marketo Measure] di fare riferimento all&#39;importo corretto dei ricavi su un&#39;opportunità, che a sua volta è distribuita tra i punti di contatto di marketing tramite i vari modelli di attribuzione.

Se non viene specificato diversamente durante l&#39;implementazione, l&#39;istanza [!DNL Marketo Measure] verrà impostata per fare riferimento all&#39;importo di opportunità standard (predefinito SFDC) per l&#39;attribuzione dei ricavi. Tuttavia, per molti account [!DNL Marketo Measure], questo campo non riflette l&#39;importo preciso dei ricavi per le opportunità. In questi casi, [!DNL Marketo Measure] offre la possibilità di impostare un importo di ricavi personalizzato per [!DNL Marketo Measure] da utilizzare come riferimento e distribuire tra i punti di contatto di attribuzione (BAT).

## Best practice {#best-practice}

Quando si imposta un importo di ricavi personalizzato, tenere presenti le best practice seguenti per garantire che i dati di attribuzione [!DNL Marketo Measure] siano accurati e coerenti.

Aspetti da considerare:

* Seleziona il campo dei ricavi accurato e utilizzato per tutte le opportunità
   * ARR o valore totale del contratto consigliato
* Non utilizzare un campo formula
* Se si utilizza un importo di ricavi personalizzato per le conversioni di valuta, il metodo preferito è la funzionalità [!UICONTROL Marketo Measure Multiple Currencies].
   * La funzionalità [!DNL Marketo Measure] più valute fa riferimento ai tassi di conversione stabiliti in [!DNL Salesforce] per garantire al meglio l&#39;allineamento tra le conversioni di valuta. Ciò ti consente di continuare a utilizzare il campo standard &quot;Importo&quot; (predefinito SFDC) o qualsiasi altro campo personalizzato relativo ai tassi di conversione [!DNL Salesforce].
* Se aggiorni il campo Importo a cui desideri fare riferimento [!DNL Marketo Measure], utilizza Data Loader per aggiornare le opportunità passate in modo da garantire che i dati dei ricavi siano coerenti e che il campo corretto venga popolato tramite il flusso di lavoro

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

La revisione annuale della configurazione dell’importo dei ricavi assicurerà che i dati di attribuzione siano accurati e allineati con il resto dei rapporti sui ricavi dell’organizzazione.

Se utilizzi un importo dei ricavi personalizzato, verifica l’impostazione dei ricavi come segue.

* Nel tuo account [!DNL Marketo Measure], vai alla sezione &#39;[!UICONTROL Opportunities]&#39; in CRM
* Identifica il campo [!UICONTROL Custom Opportunity Amount], in cui il campo [!UICONTROL custom revenue amount API] deve essere elencato
* Conferma che questo è ancora il campo corretto
* Chiedi inoltre all&#39;amministratore di [!DNL Salesforce] di confermare che il flusso di lavoro per l&#39;importo del ricavo personalizzato in [!DNL Salesforce] è ancora in esecuzione

A parte una revisione annuale, alcune modifiche organizzative potrebbero segnalare la necessità di rivedere la configurazione dell’importo dei ricavi...

* Fatturato del team marketing
* Modifiche al campo Retribuzione personalizzata
* Modifiche dell&#39;organizzazione nella modalità di dichiarazione dei ricavi

>[!MORELIKETHIS]
> [Utilizzo di un campo personalizzato per l&#39;importo dei ricavi](/help/advanced-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
> [Utilizzo di Data Loader per aggiornare il campo personalizzato &#x200B;](/help/advanced-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md)
> [Panoramica di più valute](/help/advanced-features/multi-currency/overview.md)
> [Impostazioni multivaluta](/help/advanced-features/multi-currency/settings.md)
