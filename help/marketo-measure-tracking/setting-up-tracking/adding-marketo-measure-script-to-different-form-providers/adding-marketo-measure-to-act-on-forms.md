---
unique-page-id: 18874753
description: Aggiunta [!DNL Marketo Measure] a Forms di azione - [!DNL Marketo Measure] - Documentazione del prodotto
title: Aggiunta [!DNL Marketo Measure] per Forms di attivazione
exl-id: 3d246e6a-ad3b-4683-b2b7-ab3f0f4c5ab2
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '73'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] per Forms di attivazione {#adding-marketo-measure-to-act-on-forms}

## Indicazioni stradali {#directions}

1. Nel modulo che stai modificando, seleziona la **[!UICONTROL Settings]** nell&#39;angolo a destra.
1. Cercare un&#39;area etichettata [!UICONTROL "External Web Analytics."] In questo punto rilascerai il [!DNL Marketo Measure] frammento di codice di tracciamento.

## [!DNL Marketo Measure] JavaScript {#marketo-measure-javascript}

`script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

>[!NOTE]
>
>In quest’area potrebbero già essere presenti altri snippet di codice di tracciamento, ad esempio [!DNL Google Analytics] codice. Assicurarsi di separarli con un punto e virgola `;` e un singolo spazio, così:
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>**; **<script async="true" type="someothercode" src="someotherfile.js" ></script>`
