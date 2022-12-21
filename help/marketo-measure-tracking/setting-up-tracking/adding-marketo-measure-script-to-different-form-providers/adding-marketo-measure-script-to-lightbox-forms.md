---
unique-page-id: 18874519
description: Aggiunta [!DNL Marketo Measure] Script su Forms Lightbox - [!DNL Marketo Measure] - Documentazione del prodotto
title: Aggiunta [!DNL Marketo Measure] Script to Lightbox Forms
exl-id: fa9ce480-fc4f-4abd-8555-dbb74849747e
source-git-commit: ae5b77744d523606ce6cfcf48d7e8d5049d5ccb7
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] Script to Lightbox Forms {#adding-marketo-measure-script-to-lightbox-forms}

Scopri come aggiungere correttamente il [!DNL Marketo Measure] JavaScript per un modulo all’interno di una Lightbox.

Una Lightbox apre un modulo davanti al contenuto quando il visitatore esegue un’azione specifica (ad esempio, facendo clic su una particolare parte della pagina, trascorrendo un certo periodo di tempo sulla pagina, ecc.). In genere chiediamo solo di avere [!DNL Marketo Measure] JavaScript inserito nella parte superiore della pagina di destinazione, ma per i moduli all’interno di una Lightbox c’è un ulteriore passaggio necessario.

Poiché un modulo all&#39;interno di una Lightbox è fondamentalmente una forma all&#39;interno di un iFrame, avremo bisogno del nostro script posizionato all&#39;interno di quell&#39;iFrame.

Per prima cosa, individua l’iFrame come [!UICONTROL lightbox] Forma vite in.

![](assets/1.png)

Quindi, inserisci il [!DNL Marketo Measure] JavaScript all’interno dell’iFrame.

![](assets/2.png)

Infine, quando viene aggiunto JavaScript, ti consigliamo di convalidare che gli invii dei moduli vengano tracciati seguendo queste indicazioni:

1. Copia l’URL della pagina di destinazione contenente [!UICONTROL lightbox] modulo.
1. Apri un browser in incognito e incolla l’URL.
1. Invia il modulo utilizzando un indirizzo e-mail univoco.
1. Conferma che il test sia stato tracciato controllando il CRM per l’indirizzo e-mail univoco utilizzato, assicurati che i dati del punto di contatto si popolino.
