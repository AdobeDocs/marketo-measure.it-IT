---
description: Procedure consigliate per l’utilizzo di un importo di ricavi personalizzato - [!DNL Marketo Measure] - Documentazione del prodotto
title: Procedure consigliate per l’utilizzo di un importo di ricavi personalizzato
exl-id: 553bd75a-512a-4733-a24b-8112eb420afc
feature: Custom Revenue Amount
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# Procedure consigliate per l’utilizzo di un importo di ricavi personalizzato {#best-practices-for-utilizing-a-custom-revenue-amount}

## Panoramica {#overview}

Funzionalità di base di [!DNL Marketo Measure] è la capacità di assegnare il credito dei ricavi ai punti di contatto di marketing in tutto il percorso dell’acquirente. La chiave per un’attribuzione accurata dei ricavi è la capacità di [!DNL Marketo Measure] per fare riferimento all’importo corretto dei ricavi su un’opportunità, che a sua volta viene distribuita tra i punti di contatto di marketing tramite i vari modelli di attribuzione.

Se non diversamente specificato durante l&#39;implementazione, [!DNL Marketo Measure] L&#39;istanza verrà impostata per fare riferimento all&#39;importo dell&#39;opportunità standard (predefinito SFDC) per l&#39;attribuzione dei ricavi. Tuttavia, per molti [!DNL Marketo Measure] conti, questo campo non riflette l’importo preciso dei ricavi per le opportunità. In questi casi, [!DNL Marketo Measure] offre la possibilità di impostare un importo di ricavi personalizzato per [!DNL Marketo Measure] per fare riferimento e distribuire tra i punti di contatto di attribuzione (BAT).

## Best practice {#best-practice}

Quando imposti un importo del ricavo personalizzato, tieni presente le seguenti best practice per garantire [!DNL Marketo Measure] i dati di attribuzione sono accurati e coerenti.

Aspetti da considerare:

* Seleziona il campo dei ricavi accurato e utilizzato per tutte le opportunità
   * ARR o valore totale del contratto consigliato
* Non utilizzare un campo formula
* Se utilizzi un importo di ricavi personalizzato per le conversioni di valuta, il [!UICONTROL Marketo Measure Multiple Currencies] Il metodo preferito è la funzionalità.
   * Il [!DNL Marketo Measure] La funzionalità Più valute fa riferimento ai tassi di conversione stabiliti in [!DNL Salesforce] per garantire al meglio l&#39;allineamento tra le conversioni di valuta. Questo ti consente di continuare a utilizzare il campo standard &quot;Importo&quot; (predefinito SFDC) o qualsiasi altro campo Importo personalizzato relativo al [!DNL Salesforce] tassi di conversione.
* Se si aggiorna il campo Importo desiderato [!DNL Marketo Measure] Per fare riferimento a, utilizza Data Loader per aggiornare le opportunità passate in modo da garantire che i dati sui ricavi siano coerenti e che il campo corretto venga popolato tramite il flusso di lavoro

## Procedure consigliate per la manutenzione {#best-practice-for-maintenance}

La revisione annuale della configurazione dell’importo dei ricavi assicurerà che i dati di attribuzione siano accurati e allineati con il resto dei rapporti sui ricavi dell’organizzazione.

Se utilizzi un importo dei ricavi personalizzato, verifica l’impostazione dei ricavi come segue.

* Nel tuo [!DNL Marketo Measure] account, vai a &#39;[!UICONTROL Opportunities]&#39; sezione in CRM
* Identificare [!UICONTROL Custom Opportunity Amount] Campo, qui il tuo [!UICONTROL custom revenue amount API] campo da elencare
* Conferma che questo è ancora il campo corretto
* Inoltre, puoi [!DNL Salesforce] L’Amministratore conferma che il flusso di lavoro Importo ricavi personalizzato in [!DNL Salesforce] è ancora in esecuzione

A parte una revisione annuale, alcune modifiche organizzative potrebbero segnalare la necessità di rivedere la configurazione dell’importo dei ricavi...

* Fatturato del team marketing
* Modifiche al campo Retribuzione personalizzata
* Modifiche dell&#39;organizzazione nella modalità di dichiarazione dei ricavi

>[!MORELIKETHIS]
>
>* [Utilizzo di un campo personalizzato per l&#39;importo dei ricavi](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
>* [Utilizzo di Data Loader per aggiornare il campo Importo personalizzato](/help/advanced-marketo-measure-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md)
>* [Panoramica di più divise](/help/advanced-marketo-measure-features/multi-currency/overview.md)
>* [Impostazioni multi-valuta](/help/advanced-marketo-measure-features/multi-currency/settings.md)
