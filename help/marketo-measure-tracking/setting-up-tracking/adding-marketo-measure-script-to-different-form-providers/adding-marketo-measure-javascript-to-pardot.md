---
unique-page-id: 18874757
description: Aggiunta [!DNL Marketo Measure] JavaScript in [!DNL Pardot] - [!DNL Marketo Measure] - Documentazione del prodotto
title: Aggiunta [!DNL Marketo Measure] JavaScript in [!DNL Pardot]
exl-id: e49190ad-aa86-4f8f-a9ed-48de9e937a7e
source-git-commit: ae5b77744d523606ce6cfcf48d7e8d5049d5ccb7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] JavaScript in [!DNL Pardot] {#adding-marketo-measure-javascript-to-pardot}

[!DNL Pardot] i moduli richiedono una gestione aggiuntiva all’interno del modello di modulo, oltre a inserire script sul sito per [!DNL Marketo Measure] per riconoscere gli invii dei moduli. Il processo è semplice; richiede solo il posizionamento [!DNL Marketo Measure] script di tracciamento nel [!DNL Pardot] modello di modulo.

## Istruzioni dettagliate {#step-by-step-instructions}

Una volta effettuato l’accesso al [!DNL Pardot] , segui i passaggi seguenti.

1. Passa a **[!UICONTROL Marketing]**.

1. Fai clic su **[!UICONTROL Landing Pages]**.

1. Seleziona **[!UICONTROL Layout Template]**.

   ![](assets/1-3.png)

1. Determina il modello di layout appropriato e fai clic su **[!UICONTROL Edit]** a destra.

   ![](assets/2-1.png)

1. Copiare e incollare [!DNL Marketo Measure] Codice JavaScript subito prima del tag di intestazione di chiusura nella pagina HTML.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Segui questi passaggi per tutti i modelli di layout di pagina di destinazione applicabili.

1. Assicurati che [!DNL Marketo Measure] JavaScript si trova anche nella pagina del sito generale.

   All&#39;interno di [!DNL Pardot] Modello di layout, il codice avrà un aspetto simile al seguente:

```text
<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>
   </head>
   <body>
```

## Note aggiuntive {#additional-notes}

Se la [!DNL Pardot] IFrame ha il seguente tag HTML:

`<base href="http://go.pardot.com">`

_E_ IFrame stesso si trova in una pagina protetta (HTTPS) invece di una pagina non protetta (HTTP), quando si tenta di caricare il proprio script sul [!DNL Pardot] IFrame, il browser cercherà di caricare una versione HTTP del nostro script su una pagina HTTPS che avrà esito negativo e ci impedirà di tenere traccia. La soluzione è aggiornare lo script sul [!DNL Pardot] IFrame per caricare la versione sicura del nostro script:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Anche in quest’area possono essere già presenti altri frammenti di codice di tracciamento, ad esempio un [!DNL Google Analytics] codice. Assicurati di separarli con un punto e virgola `;` e un singolo spazio, come mostrato in questo esempio:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="othercode_example" src="otherfile_example.js" ></script>`
