---
unique-page-id: 18874753
description: Aggiunta [!DNL Marketo Measure] su Forms at - [!DNL Marketo Measure] - Documentazione del prodotto
title: Aggiunta [!DNL Marketo Measure] su Forms at-on
exl-id: 3d246e6a-ad3b-4683-b2b7-ab3f0f4c5ab2
source-git-commit: b910e5aedb9e178058f7af9a6907a1039458ce7a
workflow-type: tm+mt
source-wordcount: '73'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] su Forms at-on {#adding-marketo-measure-to-act-on-forms}

## Indicazioni {#directions}

1. Nel modulo che stai modificando, seleziona la **[!UICONTROL Settings]** nell&#39;angolo a destra.
1. Ricerca di un&#39;area etichettata [!UICONTROL "External Web Analytics."] In questa posizione viene rilasciata la [!DNL Marketo Measure] frammento di codice di tracciamento.

## [!DNL Marketo Measure] JavaScript {#marketo-measure-javascript}

`script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

>[!NOTE]
>
>Potrebbero esserci già altri frammenti di codice di tracciamento in quest&#39;area, ad esempio [!DNL Google Analytics] codice. Assicurati di separarli utilizzando un punto e virgola `;` e un singolo spazio, come questo:
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>**; **<script async="true" type="someothercode" src="someotherfile.js" ></script>`
