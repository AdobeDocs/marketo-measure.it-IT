---
unique-page-id: 18874519
description: Aggiunta [!DNL Marketo Measure] Script per Lightbox Forms - [!DNL Marketo Measure]
title: Aggiunta [!DNL Marketo Measure] Script per Lightbox Forms
exl-id: fa9ce480-fc4f-4abd-8555-dbb74849747e
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] Script per Lightbox Forms {#adding-marketo-measure-script-to-lightbox-forms}

Scopri come aggiungere correttamente il [!DNL Marketo Measure] JavaScript in un modulo all’interno di un lightbox.

Una lightbox apre un modulo di fronte al contenuto quando il visitatore esegue un’azione specifica, ovvero facendo clic su una parte specifica della pagina, passando un certo periodo di tempo sulla pagina e così via. In genere si richiede di avere [!DNL Marketo Measure] JavaScript posizionato nella parte superiore della pagina di destinazione, ma per i moduli all’interno di una lightbox è necessario un ulteriore passaggio.

Poiché un modulo all’interno di un lightbox è fondamentalmente un modulo all’interno di un iFrame, lo script viene posizionato all’interno di tale iFrame.

Per prima cosa, individua l’iFrame [!UICONTROL lightbox] La forma vive in.

![](assets/1.png)

Quindi, inserisci [!DNL Marketo Measure] JavaScript all’interno dell’iFrame.

![](assets/2.png)

Infine, quando viene aggiunto JavaScript, viene tenuta traccia degli invii di moduli di convalida seguendo queste istruzioni:

1. Copia l’URL della pagina di destinazione contenente [!UICONTROL lightbox] modulo.
1. Apri un browser in incognito e incolla l’URL.
1. Invia il modulo utilizzando un indirizzo e-mail univoco.
1. Verifica che il test sia stato tracciato controllando nel CRM l’indirizzo e-mail univoco utilizzato, assicurati che i dati del punto di contatto vengano popolati.
