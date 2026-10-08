---
description: Tipo di rapporto per le indicazioni su Contatti senza opportunità per gli utenti di Marketo Measure
title: Tipo di rapporto per contatti senza opportunità
exl-id: 255048be-16ff-4964-85fd-cc07888a05af
feature: Reporting
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: d24e0b99-7796-5c7d-831d-d71a1d725f01
    internal-label: Reporting
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 3%
---
# Tipo di rapporto per contatti senza opportunità {#report-type-for-contacts-without-opportunities}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedere comunque &quot;[!DNL Bizible]&quot; nel CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

Per creare rapporti sui contatti con i punti di contatto dell&#39;acquirente non associati a un&#39;opportunità, è necessario creare un tipo di rapporto personalizzato.

1. Vai a **[!UICONTROL Setup]** > **[!UICONTROL Create]** > **[!UICONTROL Report Types]**.

   ![1. Vai a Imposta Crea tipi di report.](assets/new-types-1.png)

1. Seleziona **[!UICONTROL New Custom Report Type]**.

   ![1. Seleziona nuovo tipo di report personalizzato.](assets/new-types-10.jpg)

1. Imposta [!UICONTROL Primary Object] come &quot;[!UICONTROL Contacts]&quot;. Assegna all&#39;etichetta del tipo di rapporto il nome &quot;Contatti con i punti di contatto dell&#39;acquirente&quot;. Utilizza la stessa denominazione per Nome tipo di rapporto. All&#39;interno dell&#39;input della descrizione, &quot;Contatti con i punti di contatto dell&#39;acquirente&quot;. Salvare il report in &quot;[!UICONTROL Other]&quot; e impostare il report su &quot;[!UICONTROL Deployed]&quot;.

   ![1. Impostare l&#39;oggetto principale come &quot;Contatti&quot;. Denomina il report](assets/new-types-11.png)

1. A questo punto, verrà collegato l&#39;oggetto Contatti all&#39;oggetto Punti di contatto buyer. Assicurarsi di scegliere il pulsante &quot;Ogni record &quot;A&quot; deve avere almeno un record &quot;B&quot; correlato.&quot;

   ![1. Da qui verrà collegato l&#39;oggetto Contacts all&#39;acquirente](assets/new-types-12.png)

1. Fai clic su **[!UICONTROL Save]** e l&#39;operazione è terminata.
