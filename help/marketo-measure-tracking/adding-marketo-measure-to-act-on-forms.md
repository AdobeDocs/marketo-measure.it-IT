---
description: Aggiunta di  [!DNL Marketo Measure]  a Forms Act-On - [!DNL Marketo Measure]
title: Aggiunta di  [!DNL Marketo Measure]  a Forms Act-On
exl-id: 3d246e6a-ad3b-4683-b2b7-ab3f0f4c5ab2
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---


# Aggiunta di [!DNL Marketo Measure] a Act-On Forms {#adding-marketo-measure-to-act-on-forms}

## Indicazioni stradali {#directions}

1. Nel modulo che stai modificando, seleziona l&#39;opzione **[!UICONTROL Settings]** nell&#39;angolo destro.
1. Cercare un&#39;area con l&#39;etichetta [!UICONTROL "External Web Analytics."] Dove verrà eliminato lo snippet del codice di tracciamento [!DNL Marketo Measure].

## [!DNL Marketo Measure] JavaScript {#marketo-measure-javascript}

`script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

>[!NOTE]
>In quest&#39;area potrebbero essere già presenti altri snippet di codice di tracciamento, ad esempio un codice [!DNL Google Analytics]. Assicurarsi di separarli utilizzando un punto e virgola `;` e un singolo spazio, come segue:
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>*; **<script async="true" type="someothercode" src="someotherfile.js" ></script>`
