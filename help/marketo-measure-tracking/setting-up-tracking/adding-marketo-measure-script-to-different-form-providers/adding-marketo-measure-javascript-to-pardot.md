---
unique-page-id: 18874757
description: Aggiunta [!DNL Marketo Measure] JavaScript per [!DNL Pardot] - [!DNL Marketo Measure]
title: Aggiunta [!DNL Marketo Measure] JavaScript per [!DNL Pardot]
exl-id: e49190ad-aa86-4f8f-a9ed-48de9e937a7e
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] JavaScript per [!DNL Pardot] {#adding-marketo-measure-javascript-to-pardot}

[!DNL Pardot] i moduli richiedono una gestione aggiuntiva all&#39;interno del modello di modulo, oltre all&#39;inserimento di script nel sito per [!DNL Marketo Measure] per riconoscere gli invii di moduli. Il processo è semplice e richiede solo l&#39;inserimento [!DNL Marketo Measure] script di tracciamento in [!DNL Pardot] modello di modulo.

## Istruzioni dettagliate {#step-by-step-instructions}

Dopo aver effettuato l’accesso a [!DNL Pardot] account, segui i passaggi seguenti.

1. Accedi a **[!UICONTROL Marketing]**.

1. Clic **[!UICONTROL Landing Pages]**.

1. Seleziona **[!UICONTROL Layout Template]**.

   ![](assets/1-3.png)

1. Determinare il modello di layout appropriato e fare clic su **[!UICONTROL Edit]** a destra.

   ![](assets/2-1.png)

1. Copiare e incollare [!DNL Marketo Measure] Codice JavaScript immediatamente prima del tag di intestazione close nella pagina HTML.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Segui questi passaggi per tutti i modelli di layout della pagina di destinazione applicabili.

1. Assicurati che le [!DNL Marketo Measure] JavaScript si trova anche nella pagina generale del sito.

   All&#39;interno del [!DNL Pardot] Modello di layout, il codice si presenta così:

```text
<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>
   </head>
   <body>
```

## Note aggiuntive {#additional-notes}

Se il [!DNL Pardot] IFrame ha il seguente tag HTML:

`<base href="http://go.pardot.com">`

_E_ IFrame è una pagina protetta (HTTPS) anziché non protetta (HTTP) quando si carica lo script in [!DNL Pardot] IFrame, il browser tenta di caricare una versione HTTP dello script su una pagina HTTPS che avrà esito negativo, interrompendo il tracciamento. La soluzione consiste nell&#39;aggiornare lo script [!DNL Pardot] IFrame per caricare la versione protetta dello script:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

In quest’area potrebbero già essere presenti altri snippet di codice di tracciamento, ad esempio [!DNL Google Analytics] codice. Assicurarsi di separarli con un punto e virgola `;` e un singolo spazio, come mostrato in questo esempio:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="othercode_example" src="otherfile_example.js" ></script>`
