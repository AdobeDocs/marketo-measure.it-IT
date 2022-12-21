---
description: Tecniche consigliate per l’utilizzo di un importo di ricavi personalizzato - [!DNL Marketo Measure] - Documentazione del prodotto
title: Tecniche consigliate per l’utilizzo di un importo di ricavi personalizzato
exl-id: 553bd75a-512a-4733-a24b-8112eb420afc
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# Tecniche consigliate per l’utilizzo di un importo di ricavi personalizzato {#best-practices-for-utilizing-a-custom-revenue-amount}

## Panoramica {#overview}

Funzionalità di base di [!DNL Marketo Measure] è la capacità di assegnare il credito sui ricavi ai punti di contatto di marketing in tutto il percorso dell’acquirente. La chiave per un’attribuzione accurata dei ricavi è la capacità di [!DNL Marketo Measure] per fare riferimento all’importo corretto dei ricavi su un’opportunità, che a sua volta viene distribuita tra i diversi punti di contatto di marketing tramite i vari modelli di attribuzione.

Se non diversamente specificato durante l’implementazione, la [!DNL Marketo Measure] L’istanza verrà impostata per fare riferimento all’importo opportunità standard (impostazione predefinita SFDC) per l’attribuzione dei ricavi. Tuttavia, per molti [!DNL Marketo Measure] conti, questo campo non riflette l&#39;importo esatto dei ricavi per Opportunità. In questi casi, [!DNL Marketo Measure] offre la possibilità di impostare un importo personalizzato per [!DNL Marketo Measure] fare riferimento e distribuire tra i punti di contatto di attribuzione (BAT).

## Best practice {#best-practice}

Quando configuri un importo di ricavo personalizzato, tieni presente le seguenti best practice per garantire che [!DNL Marketo Measure] i dati di attribuzione sono precisi e coerenti!

Aspetti da tenere a mente:

* Selezionare il campo Ricavo accurato e utilizzato per tutte le opportunità
   * ARR o Valore totale del contratto ci consigliato
* Non utilizzare un campo formula
* Se utilizzi un Importo ricavi personalizzato per le conversioni di valuta, la variabile [!UICONTROL Marketo Measure Multiple Currencies] invece è il metodo preferito.
   * La [!DNL Marketo Measure] La funzionalità Valute multiple fa riferimento ai tassi di conversione stabiliti in [!DNL Salesforce] per garantire al meglio l&#39;allineamento tra le conversioni di valuta. Questo ti consente di continuare a utilizzare il campo standard &quot;Amount&quot; (Predefinito SFDC) o qualsiasi altro campo personalizzato Amount relativo al [!DNL Salesforce] tassi di conversione.
* Se si aggiorna il campo Importo desiderato [!DNL Marketo Measure] per fare riferimento, utilizza Data Loader per aggiornare le opportunità passate per garantire che i dati dei ricavi siano coerenti e che il campo corretto venga compilato tramite il flusso di lavoro

## Best practice per la manutenzione {#best-practice-for-maintenance}

La revisione annuale della configurazione dell’importo dei ricavi garantirà che i dati di attribuzione siano accurati e allineati con il resto dei rapporti sui ricavi della tua organizzazione.

Se utilizzi un Importo ricavi personalizzato, controlla la configurazione dei ricavi come segue.

* Nel tuo [!DNL Marketo Measure] account, vai a[!UICONTROL Opportunities]Sezione di CRM
* Identifica la [!UICONTROL Custom Opportunity Amount] Campo, qui il tuo [!UICONTROL custom revenue amount API] campo da elencare
* Conferma che il campo sia ancora corretto
* Anche il tuo [!DNL Salesforce] L&#39;amministratore conferma che il flusso di lavoro Importo ricavi personalizzati in [!DNL Salesforce] è ancora in esecuzione

A parte una revisione annuale, alcune modifiche organizzative possono segnalare la necessità di rivedere la configurazione dell&#39;importo dei ricavi...

* Fatturato del team di marketing
* Modifiche al campo Ricavi personalizzati
* L&#39;organizzazione cambia il modo in cui i ricavi vengono segnalati

>[!MORELIKETHIS]
>
>* [Utilizzo di un campo Importo ricavi personalizzato](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
>* [Utilizzo di Data Loader per aggiornare il campo Importo personalizzato](/help/advanced-marketo-measure-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md)
>* [Panoramica di più valute](/help/advanced-marketo-measure-features/multi-currency/overview.md)
>* [Impostazioni multivaluta](/help/advanced-marketo-measure-features/multi-currency/settings.md)

