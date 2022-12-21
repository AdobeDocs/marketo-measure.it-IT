---
unique-page-id: 18874539
description: Creazione personalizzata [!DNL Marketo Measure] Tipi di report - [!DNL Marketo Measure] - Documentazione del prodotto
title: Creazione personalizzata [!DNL Marketo Measure] Tipi di rapporti
exl-id: 1d72a04f-6a2d-4607-ad09-3b025125156a
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Creazione personalizzata [!DNL Marketo Measure] Tipi di rapporti {#creating-custom-marketo-measure-report-types}

>[!NOTE]
>
>È possibile visualizzare istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella nostra documentazione, ma ancora vedi &quot;[!DNL Bizible]&quot; nel CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riflesso nel tuo CRM presto.

Scopri come creare un&#39;interfaccia personalizzata [!DNL Marketo Measure] [!DNL Salesforce] tipi di report. È consigliabile creare tre tipi di rapporti diversi: Lead con punti di contatto dell’acquirente (personalizzati), [!DNL Marketo Measure] Persona con punti di contatto per l’acquirente (personalizzati), opportunità con punto di contatto per l’attribuzione dell’acquirente (personalizzati).

## Lead con punti di contatto dell’acquirente (personalizzati) {#leads-with-buyer-touchpoints-custom}

1. Vai a **[!UICONTROL Setup]** > **[!UICONTROL Build]** > **[!UICONTROL Report Types]** > **[!UICONTROL New Custom Report Types]**.

   ![](assets/1.png)

1. Definisci il tipo di rapporto personalizzato.

   * [!UICONTROL Report Type Focus] > [!UICONTROL [!UICONTROL Primary Object]]: Lead
   * Identificazione > [!UICONTROL Report Type Label]: Lead con punti di contatto dell’acquirente (personalizzati)
   * [!UICONTROL Store in Category]: Altri rapporti
   * [!UICONTROL Deployment] > [!UICONTROL Deployment Status]: Distribuito

   ![](assets/2.png)

1. Definire le relazioni tra gli oggetti.

   * Collegare l’oggetto Lead (A) al [!DNL Marketo Measure] Oggetto Persona (B) e quindi all’oggetto punto di contatto dell’acquirente (C)
   * Assicurati che &quot;[!UICONTROL Each A/B record must have at least one B/C]&quot; record selezionato
   * [!UICONTROL Save]

   ![](assets/3.png)

## [!DNL Marketo Measure] Persona con punti di contatto dell’acquirente (personalizzati) {#marketo-measure-person-with-buyer-touchpoints-custom}

1. Vai a **[!UICONTROL Setup]** > **[!UICONTROL Build]** > **[!UICONTROL Report Types]** > **[!UICONTROL New Custom Report Types]**.

   ![](assets/4.png)

1. Definisci il tipo di rapporto personalizzato.

   * [!UICONTROL Report Type Focus] > [!UICONTROL Primary Object]: [!DNL Marketo Measure] Persone
   * [!UICONTROL Identification] > [!UICONTROL Report Type Label]: [!DNL Marketo Measure] Persona con punti di contatto dell’acquirente (personalizzati)
   * [!UICONTROL Store in Category]: Altri rapporti
   * [!UICONTROL Deployment] > [!UICONTROL Deployment Status]: Distribuito

   ![](assets/5.png)

1. Definire le relazioni tra gli oggetti.

   * Collega [!DNL Marketo Measure] Oggetto Persona (A) all’oggetto punto di contatto dell’acquirente (B)
   * Assicurati che &quot;[!UICONTROL Each A record must have at least one B]&quot; record selezionato
   * [!UICONTROL Save]

   ![](assets/6.png)

## Opportunità con punto di contatto per l’attribuzione dell’acquirente (personalizzato) {#opportunities-with-buyer-attribution-touchpoint-custom}

1. Vai a **[!UICONTROL Setup]** > **[!UICONTROL Build]** > **[!UICONTROL Report Types]** > **[!UICONTROL New Custom Report Types]**.

   ![](assets/7.png)

1. Definisci il tipo di rapporto personalizzato.

   * [!UICONTROL Report Type Focus] > [!UICONTROL Primary Object]: Opportunità
   * [!UICONTROL Identification] > [!UICONTROL Report Type Label]: Opportunità con punto di contatto per l’attribuzione dell’acquirente (personalizzato)
   * [!UICONTROL Store in Category]: Altri rapporti
   * [!UICONTROL Deployment] > [!UICONTROL Deployment Status]: Distribuito

   ![](assets/8.png)

1. Definire le relazioni tra gli oggetti.

   * Collegare l’oggetto Opportunità (A) all’oggetto punto di contatto Attribuzione acquirente (B)
   * Assicurati che &quot;[!UICONTROL Each A record must have at least one B]&quot; record selezionato
   * [!UICONTROL Save]

   ![](assets/9.png)

## Aggiunta di campi personalizzati a tipi di rapporti personalizzati {#adding-custom-fields-to-custom-report-types}

1. Una volta creati i rapporti, verrai reindirizzato a una panoramica del tipo di rapporto. Clic **[!UICONTROL Edit Layout]**.

   ![](assets/10.png)

1. Assicurarsi che i campi personalizzati che si desidera aggiungere al rapporto siano visualizzati nella sezione Proprietà layout campo . Se sono presenti altri campi da aggiungere, utilizza &quot;[!UICONTROL Add fields related via lookup]&quot; opzione.

   ![](assets/11.png)
