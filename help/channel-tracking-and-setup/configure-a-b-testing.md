---
description: Configurazione della guida all'integrazione dei test A/B [!DNL Marketo Measure] per gli utenti di Marketo Measure
title: Configurazione dell'integrazione del test A/B [!DNL Marketo Measure]
exl-id: 25fc25eb-9a72-4824-9a98-cc286e5c1e4a
feature: A/B Testing, Integration
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: 348f752d-f464-5239-ab5e-c1faaeafb983
    internal-label: A/B Testing
  - id: 7da342c5-06ee-5869-b3e8-b73d5bf75a9d
    internal-label: Integration
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 5%
---

# Configurazione dell&#39;integrazione del test A/B [!DNL Marketo Measure] {#configuring-a-b-testing}

Aggiungere le sezioni del test A/B [!DNL Marketo Measure] su lead, contatto, caso e opportunità. [!DNL Marketo Measure] L&#39;integrazione di test A/B consente di tenere traccia dell&#39;impatto sui ricavi degli esperimenti sul sito [Optimizely](https://www.optimizely.com/){target="_blank"} e [VWO](https://vwo.com/){target="_blank"}.

1. Verificare di utilizzare il pacchetto [[!DNL Marketo Measure] v3.9 o versione successiva](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"}.
1. Aggiungi l&#39;elenco &quot;[!DNL Marketo Measure] ABTests&quot; ai layout di pagina, quindi fai clic sul pulsante **Impostazioni** (chiave inglese).
1. Rimuovi il campo &quot;Id&quot; stock dall’elenco dei campi Selezionati. Aggiungere i campi [!UICONTROL Experiment], [!UICONTROL Variation] e [!UICONTROL DateReported] e modificare &quot;Ordina per&quot; in &quot;Data rapporto&quot;. Fare clic sul pulsante **[!UICONTROL Descending]**.
1. In &quot;[!UICONTROL Buttons]&quot;, deselezionare **[!UICONTROL New]**.
1. Contatta il tuo account manager o il [supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} per abilitare questa funzione.
