---
unique-page-id: 18874757
description: Aggiunta di  [!DNL Marketo Measure] JavaScript a  [!DNL Pardot] - [!DNL Marketo Measure] in corso
title: Aggiunta di  [!DNL Marketo Measure] JavaScript a  [!DNL Pardot] in corso
exl-id: e49190ad-aa86-4f8f-a9ed-48de9e937a7e
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Aggiunta di [!DNL Marketo Measure] JavaScript a [!DNL Pardot] {#adding-marketo-measure-javascript-to-pardot}

I moduli [!DNL Pardot] richiedono una gestione aggiuntiva all&#39;interno del modello di modulo, oltre a inserire lo script sul sito per consentire a [!DNL Marketo Measure] di riconoscere gli invii di moduli. Il processo è semplice e richiede solo il posizionamento dello script di monitoraggio [!DNL Marketo Measure] nel modello di modulo [!DNL Pardot].

## Istruzioni dettagliate {#step-by-step-instructions}

Dopo aver effettuato l&#39;accesso all&#39;account [!DNL Pardot], eseguire la procedura seguente.

1. Passa a **[!UICONTROL Marketing]**.

1. Fare clic su **[!UICONTROL Landing Pages]**.

1. Selezionare **[!UICONTROL Layout Template]**.

   ![](assets/1-3.png)

1. Determinare il modello di layout appropriato e fare clic su **[!UICONTROL Edit]** a destra.

   ![](assets/2-1.png)

1. Copia e incolla il codice JavaScript [!DNL Marketo Measure] immediatamente prima del tag di intestazione Close nella pagina di HTML.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Segui questi passaggi per tutti i modelli di layout della pagina di destinazione applicabili.

1. Assicurarsi che il JavaScript [!DNL Marketo Measure] sia presente anche nella pagina del sito generale.

   Nel modello di layout [!DNL Pardot], il codice si presenta così:

```text
<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>
   </head>
   <body>
```

## Note aggiuntive {#additional-notes}

Se l&#39;IFrame [!DNL Pardot] ha il seguente tag HTML:

`<base href="http://go.pardot.com">`

_E_ il IFrame stesso è in realtà una pagina protetta (HTTPS) anziché non protetta (HTTP). Quando si carica lo script nel IFrame [!DNL Pardot], il browser tenta di caricare una versione HTTP dello script su una pagina HTTPS che non riuscirà, interrompendo il tracciamento. La soluzione consiste nell&#39;aggiornare lo script nel IFrame [!DNL Pardot] per caricare la versione protetta dello script:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

In quest&#39;area potrebbero essere già presenti altri snippet di codice di tracciamento, ad esempio un codice [!DNL Google Analytics]. Assicurarsi di separarli con un punto e virgola `;` e un singolo spazio, come illustrato nell&#39;esempio seguente:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="othercode_example" src="otherfile_example.js" ></script>`
