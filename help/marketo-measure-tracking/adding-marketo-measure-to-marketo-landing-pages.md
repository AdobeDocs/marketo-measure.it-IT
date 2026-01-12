---
description: Aggiunta di  [!DNL Marketo Measure] alle [!DNL Marketo] pagine di destinazione - [!DNL Marketo Measure] in corso
title: Aggiunta di  [!DNL Marketo Measure]  alle pagine di destinazione di Marketo
exl-id: 3771d4d2-8723-452a-b23d-cea3b11ab9ee
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# Aggiunta di [!DNL Marketo Measure] alle pagine di destinazione di Marketo {#adding-marketo-measure-to-marketo-landing-pages}

Scopri come aggiungere il tracciamento alle pagine di destinazione [!DNL Marketo Engage] che richiedono una gestione aggiuntiva. [!DNL Marketo Measure] JavaScript deve essere presente sia nella pagina di destinazione che nel modulo [!DNL Marketo Engage] stesso. A tale scopo, è necessario caricare il JavaScript [!DNL Marketo Measure] in [!DNL Marketo Engage] come descritto nelle istruzioni seguenti.

>[!NOTE]
>Se si distribuisce JavaScript tramite un provider di gestione tag come [!DNL Google Tag Manager], non è necessario aggiungere manualmente [!DNL Marketo Measure] JS a [!DNL Marketo Engage].

## Come aggiungere lo script [!DNL Marketo Measure] alle pagine di destinazione [!DNL Marketo Engage] {#how-to-add-marketo-measure-script-to-marketo-engage-landing-pages}

1. Accedi al tuo account [!DNL Marketo Engage].
1. Seleziona la pagina di destinazione e fai clic su **[!UICONTROL Edit Draft]**.
1. Trascina nell’elemento HTML.
1. Immettere il JavaScript [!DNL Marketo Measure] nella sezione [!UICONTROL head]:

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Esempio nella schermata seguente

1. Fai clic su **[!UICONTROL Save]**.

   ![Editor pagina di destinazione Marketo con script Bizible aggiunto all&#39;intestazione](assets/adding-bizible-to-marketo-landing-pages-1.png)

## Note aggiuntive {#additional-notes}

* È possibile che siano già presenti altri snippet di codice di tracciamento, ad esempio un codice [!DNL Google Analytics]. Non si è verificato alcun problema. Separarli con un punto e virgola `;` e uno spazio. Ecco un esempio di come apparirebbe:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`

* È probabile che siano in uso più modelli di pagina di destinazione; assicurati di aggiungere il codice a tutti i modelli che contengono moduli.

* A volte, quando modifichi il modello per le pagine di destinazione, devi approvare nuovamente le pagine da cui viene utilizzata la pagina di destinazione. Questo articolo spiega [come approvare in massa](https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/landing-page-actions/approve-multiple-landing-pages-at-once.html){target="_blank"}.
