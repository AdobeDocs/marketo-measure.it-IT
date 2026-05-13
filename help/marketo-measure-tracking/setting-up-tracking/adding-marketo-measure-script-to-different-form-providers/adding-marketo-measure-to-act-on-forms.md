---
unique-page-id: 18874753
description: Aggiunta di  [!DNL Marketo Measure]  a Forms Act-On - [!DNL Marketo Measure]
title: Aggiunta di  [!DNL Marketo Measure]  a Forms Act-On
exl-id: 3d246e6a-ad3b-4683-b2b7-ab3f0f4c5ab2
feature: Tracking
TQID: https://experienceleague.adobe.com/BUdHiCxfaG7a8Tays-Oqg9ZJQjSZJMM4-ChPHuF0RCg
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
source-git-commit: 9ceb54139bfa9b6ce7c2c5fbb4e25e649f5708a3
workflow-type: tm+mt
source-wordcount: 73
ht-degree: 0%

---

# Aggiunta di [!DNL Marketo Measure] a Act-On Forms {#adding-marketo-measure-to-act-on-forms}

## Indicazioni stradali {#directions}

1. Nel modulo che stai modificando, seleziona l&#39;opzione **[!UICONTROL Settings]** nell&#39;angolo destro.
1. Cercare un&#39;area con l&#39;etichetta [!UICONTROL "External Web Analytics."] Dove verrà eliminato lo snippet del codice di tracciamento [!DNL Marketo Measure].

## [!DNL Marketo Measure] JavaScript {#marketo-measure-javascript}

`script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

>[!NOTE]
>
>In quest&#39;area potrebbero essere già presenti altri snippet di codice di tracciamento, ad esempio un codice [!DNL Google Analytics]. Assicurarsi di separarli utilizzando un punto e virgola `;` e un singolo spazio, come segue:
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>**; **<script async="true" type="someothercode" src="someotherfile.js" ></script>`
