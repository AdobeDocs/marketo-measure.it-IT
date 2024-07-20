---
unique-page-id: 18874773
description: Configurazione e reporting test A/B - [!DNL Marketo Measure]
title: Configurazione e reporting dei test A/B
exl-id: 9a3f0731-5909-4fbf-a35a-9608ff561061
feature: A/B Testing
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# Configurazione e reporting dei test A/B {#a-b-testing-set-up-and-reporting}

L&#39;integrazione del test A/B di [!DNL Marketo Measure] consente di tenere traccia dell&#39;impatto sui ricavi degli esperimenti [in modo ottimale](https://www.optimizely.com/){target="_blank"} e del sito VWO. Questo articolo fornisce istruzioni su come aggiungere [!DNL Marketo Measure] sezioni di test A/B ai layout di pagina Lead, [!UICONTROL Contact], Case e [!UICONTROL Opportunity]. Vengono inoltre trattate le procedure di reporting generali e le raccomandazioni per l&#39;esecuzione di [!DNL Marketo Measure] tipi di report A/B.

## Configurazione {#set-up}

Aggiungere le sezioni del test A/B [!DNL Marketo Measure] su lead, contatto, caso e opportunità. L&#39;integrazione del test A/B [!DNL Marketo Measure] consente di tenere traccia dell&#39;impatto sui ricavi degli esperimenti sul sito [Optimizely](https://www.optimizely.com/){target="_blank"} e [VWO](https://vwo.com/){target="_blank"}.

1. Verificare di utilizzare il pacchetto [!DNL Marketo Measure] v3.9 o versione successiva. Per eseguire questa operazione, vai a [!UICONTROL Salesforce] >[!UICONTROL Set Up] > [!UICONTROL Installed packages].
1. Modificare il layout della pagina del lead e aggiungere l&#39;elenco **[!DNL Marketo Measure]test A/B** correlati alla pagina.

   ![](assets/1.png)

1. Fare clic sul pulsante [!UICONTROL Wrench]. Rimuovi il campo &quot;Id&quot; stock dall’elenco dei campi Selezionati. Aggiungere **[!UICONTROL Experiment]**, **[!UICONTROL Variation]** e **[!UICONTROL DateReported]** campi. Cambia &quot;[!UICONTROL Sort by]&quot; in **[!UICONTROL Date Reported]** e seleziona **[!UICONTROL Descending]** nel menu a discesa.

   ![](assets/2.png)

1. In [!UICONTROL Buttons], deselezionare **[!UICONTROL New]**.

   ![](assets/3.png)

1. Contatta il tuo rappresentante [!DNL Marketo Measure] o il [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} per abilitare la funzione.

## Reporting {#reporting}

I clienti hanno accesso a due tipi di report A/B [!DNL Marketo Measure] che consentono di creare rapporti su test A/B in relazione a lead, contatti e opportunità:

* [!DNL Marketo Measure] A/BTests
* [!DNL Marketo Measure] test A/BT con contatto
* [!DNL Marketo Measure] test A/BT con lead
* [!DNL Marketo Measure] test A/BT con opportunità

![](assets/4.png)

I tipi di rapporto A/B vengono utilizzati per indicare su quale lead, contatto o opportunità è stato esposto a un test A/B. Questi rapporti mostrano anche l’importo dei ricavi legati a un’opportunità che è stata esposta a un test A/B.

È importante notare che Optimizely/VWO è una piattaforma di variazione dei contenuti e non un canale di marketing. Pertanto, questi tipi di report A/B [!DNL Marketo Measure] vengono utilizzati in modo diverso rispetto ai report Buyer Touchpoint. I tipi di rapporti sui punti di contatto dell’acquirente vengono utilizzati per capire quale canale di marketing (pubblicità a pagamento, web direct, social) ha portato un lead o un contatto a una pagina specifica. Tuttavia, non è possibile utilizzare i tipi di rapporto A/B [!DNL Marketo Measure] per generare rapporti sull&#39;influenza di una variante su un lead o un&#39;opportunità. Poiché una variante di test A/B non è un canale, i dettagli sulla variante non vengono visualizzati nel punto di contatto dell’acquirente.

Di seguito sono riportati alcuni campi consigliati da utilizzare durante la generazione di rapporti su un test A/B per migliorare chiarezza e approfondimenti:

* Lead convertito
* Esperimento
* ID esperimento
* Variante
* ID variante
* Data rapporto

## [!DNL Salesforce] Report di esempio {#salesforce-example-reports}

**[!DNL Marketo Measure]test A/B con lead**

![](assets/5.png)

**[!DNL Marketo Measure]test A/B con opportunità**

![](assets/6.png)
