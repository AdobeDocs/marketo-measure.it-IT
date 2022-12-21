---
unique-page-id: 18874773
description: Impostazione e reporting dei test A/B - [!DNL Marketo Measure] - Documentazione del prodotto
title: Impostazione e reporting dei test A/B
exl-id: 9a3f0731-5909-4fbf-a35a-9608ff561061
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Impostazione e reporting dei test A/B {#a-b-testing-set-up-and-reporting}

La [!DNL Marketo Measure] L’integrazione dei test A/B consente di monitorare l’impatto dei ricavi [Ottimizzato](https://optimizely.com/){target=&quot;_blank&quot;} ed esperimenti sul sito VWO. Queste guide forniscono istruzioni su come aggiungere [!DNL Marketo Measure] sezioni di test A/B al lead, [!UICONTROL Contact], Case e [!UICONTROL Opportunity] layout di pagina. Verranno inoltre illustrate le pratiche generali di reporting e le raccomandazioni per l&#39;esecuzione [!DNL Marketo Measure] Tipi di rapporti A/B.

## Configurazione {#set-up}

Aggiungi il [!DNL Marketo Measure] Sezioni di test A/B su lead, contatti, case e opportunità. [!DNL Marketo Measure] L’integrazione dei test A/B consente di monitorare l’impatto dei ricavi [Ottimizzato](https://optimizely.com/){target=&quot;_blank&quot;} e [VWO](https://vwo.com/){target=&quot;_blank&quot;} esperimenti del sito.

1. Verifica di utilizzare il pacchetto [!DNL Marketo Measure] v3.9 o versioni successive. Puoi farlo andando a [!UICONTROL Salesforce] >[!UICONTROL Set Up] > [!UICONTROL Installed packages].
1. Modificate il layout della pagina Lead e aggiungete il **[!DNL Marketo Measure]Test A/B** Elenco correlato alla pagina.

   ![](assets/1.png)

1. Fai clic sul pulsante [!UICONTROL Wrench] pulsante . Rimuovere il campo &quot;Id&quot; dall&#39;elenco dei campi Selezionati. Aggiungi **[!UICONTROL Experiment]**, **[!UICONTROL Variation]** e **[!UICONTROL DateReported]** campi. Cambia &quot;[!UICONTROL Sort by]&quot; **[!UICONTROL Date Reported]**, quindi seleziona **[!UICONTROL Descending]** nel menu a discesa .

   ![](assets/2.png)

1. Sotto [!UICONTROL Buttons], deseleziona **[!UICONTROL New]**.

   ![](assets/3.png)

1. Contatta il tuo [!DNL Marketo Measure] o [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target=&quot;_blank&quot;} per abilitare la funzione.

## Reporting {#reporting}

I clienti hanno accesso a un paio di [!DNL Marketo Measure] Tipi di rapporti A/B che consentono di creare rapporti sui test A/B in relazione a lead, contatti e opportunità:

* [!DNL Marketo Measure] Test A/BT
* [!DNL Marketo Measure] Test A/BT con contatto
* [!DNL Marketo Measure] Test A/BT con piombo
* [!DNL Marketo Measure] Test A/BT con opportunità

![](assets/4.png)

I tipi di report A/B vengono utilizzati per creare rapporti in cui Lead o Contact o Opportunity è stato esposto a un test A/B. Inoltre, questi rapporti possono mostrare la quantità di ricavi legati a un’opportunità esposta a un test A/B.

È importante notare che Optimizely/VWO è una piattaforma di variazione dei contenuti e non un canale di marketing. Pertanto, questi [!DNL Marketo Measure] I tipi di report A/B vengono utilizzati in modo diverso rispetto ai report punto di contatto dell&#39;acquirente. I tipi di rapporti sui punti di contatto dell’acquirente vengono utilizzati per comprendere quale canale di marketing (ad esempio, pubblicità a pagamento, web direct, social) ha guidato un lead o un contatto per una pagina specifica. Tuttavia, [!DNL Marketo Measure] Non è possibile utilizzare i tipi di rapporto A/B per generare rapporti su come una variante ha influenzato un lead o un’opportunità. Inoltre, poiché una variante di test A/B non è un canale, i dettagli sulla variante non verranno visualizzati sul punto di contatto Acquirente.

Di seguito sono riportati alcuni campi comuni che consigliamo di utilizzare per generare rapporti sui test A/B per migliorare la chiarezza e le informazioni:

* Lead convertiti
* Esperimento
* ID esperimento
* Variazione
* ID variante
* Data Segnalata

## [!DNL Salesforce] Report di esempio {#salesforce-example-reports}

**[!DNL Marketo Measure]Test A/B con lead**

![](assets/5.png)

**[!DNL Marketo Measure]Test A/B con opportunità**

![](assets/6.png)
