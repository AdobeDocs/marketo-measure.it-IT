---
unique-page-id: 18874755
description: Aggiunta [!DNL Marketo Measure] a [!DNL Marketo] Pagine di destinazione - [!DNL Marketo Measure] - Documentazione del prodotto
title: Aggiunta [!DNL Marketo Measure] alle pagine di destinazione Marketo
exl-id: 3771d4d2-8723-452a-b23d-cea3b11ab9ee
source-git-commit: 82cc8269bfdb26b6acf039d0ce0e06564f5e2612
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] alle pagine di destinazione Marketo {#adding-marketo-measure-to-marketo-landing-pages}

Scopri come aggiungere il tracciamento a [!DNL Marketo Engage] Pagine di destinazione in quanto richiedono una gestione aggiuntiva. [!DNL Marketo Measure] JavaScript deve essere installato sia sulla pagina di destinazione che sul [!DNL Marketo Engage] formare se stesso. A questo scopo, dovrai caricare il [!DNL Marketo Measure] JavaScript in [!DNL Marketo Engage] come spiegato nelle seguenti direzioni.

>[!NOTE]
>
>Se distribuisci JavaScript tramite un provider di gestione dei tag come [!DNL Google Tag Manager], non è necessario aggiungere manualmente [!DNL Marketo Measure] JS a [!DNL Marketo Engage].

## Come aggiungere [!DNL Marketo Measure] Script per [!DNL Marketo Engage] Pagine di destinazione {#how-to-add-marketo-measure-script-to-marketo-engage-landing-pages}

1. Accedi al tuo [!DNL Marketo Engage] conto.
1. Seleziona la pagina di destinazione e fai clic su **[!UICONTROL Edit Draft]**.
1. Trascina l’elemento HTML .
1. Inserisci il [!DNL Marketo Measure] JavaScript nel [!UICONTROL head] sezione:

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Esempio nella schermata sottostante

1. Clic **[!UICONTROL Save]**.

   ![](assets/adding-bizible-to-marketo-landing-pages-1.png)

## Note aggiuntive {#additional-notes}

* Potrebbero essere già presenti altri frammenti di codice di tracciamento, ad esempio [!DNL Google Analytics] codice. Non c&#39;è problema, basta essere sicuri di separarli con un punto e virgola `;` e un unico spazio. Un esempio di come dovrebbe essere:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`

* È probabile che siano in uso più modelli di pagina di destinazione, assicurarsi di aggiungere il codice a tutti i modelli che contengono moduli.

* A volte, quando modifichi il modello per le pagine di destinazione, devi riapprovare le pagine da cui viene utilizzata la pagina di destinazione. Questo articolo spiega [come approvare in massa](https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/landing-page-actions/approve-multiple-landing-pages-at-once.html){target=&quot;_blank&quot;}.
