---
unique-page-id: 18874755
description: Aggiunta [!DNL Marketo Measure] a [!DNL Marketo] Pagine di destinazione - [!DNL Marketo Measure]
title: Aggiunta [!DNL Marketo Measure] alle pagine di destinazione di Marketo
exl-id: 3771d4d2-8723-452a-b23d-cea3b11ab9ee
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] alle pagine di destinazione di Marketo {#adding-marketo-measure-to-marketo-landing-pages}

Scopri come aggiungere il tracciamento a [!DNL Marketo Engage] Pagine di destinazione in quanto richiedono una gestione aggiuntiva. [!DNL Marketo Measure] JavaScript deve essere presente sia nella pagina di destinazione che nella [!DNL Marketo Engage] la forma stessa. A questo scopo, devi caricare [!DNL Marketo Measure] JavaScript in [!DNL Marketo Engage] come spiegato nelle seguenti direzioni.

>[!NOTE]
>
>Se distribuisci JavaScript tramite un provider di gestione dei tag come [!DNL Google Tag Manager], non è necessario aggiungere manualmente [!DNL Marketo Measure] JS a [!DNL Marketo Engage].

## Come aggiungere [!DNL Marketo Measure] Script per [!DNL Marketo Engage] Pagine di destinazione {#how-to-add-marketo-measure-script-to-marketo-engage-landing-pages}

1. Accedi al tuo [!DNL Marketo Engage] account.
1. Seleziona la pagina di destinazione e fai clic su **[!UICONTROL Edit Draft]**.
1. Trascina nell’elemento HTML.
1. Inserisci il [!DNL Marketo Measure] JavaScript in [!UICONTROL head] sezione:

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Esempio nella schermata seguente

1. Clic **[!UICONTROL Save]**.

   ![](assets/adding-bizible-to-marketo-landing-pages-1.png)

## Note aggiuntive {#additional-notes}

* Potresti avere già altri snippet di codice di tracciamento, ad esempio [!DNL Google Analytics] codice. Questo problema non si verifica, assicurati di separarli con un punto e virgola `;` e un singolo spazio. Ecco un esempio di come apparirebbe:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`

* È probabile che siano in uso più modelli di pagina di destinazione; assicurati di aggiungere il codice a tutti i modelli che contengono moduli.

* A volte, quando modifichi il modello per le pagine di destinazione, devi approvare nuovamente le pagine da cui viene utilizzata la pagina di destinazione. Questo articolo spiega [approvazione di massa](https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/landing-page-actions/approve-multiple-landing-pages-at-once.html){target="_blank"}.
