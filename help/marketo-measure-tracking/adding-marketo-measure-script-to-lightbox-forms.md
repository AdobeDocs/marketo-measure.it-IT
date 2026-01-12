---
description: Aggiunta dello script  [!DNL Marketo Measure]  a Lightbox Forms in corso - [!DNL Marketo Measure]
title: Aggiunta dello script  [!DNL Marketo Measure]  a Lightbox Forms
exl-id: fa9ce480-fc4f-4abd-8555-dbb74849747e
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Aggiunta dello script [!DNL Marketo Measure] a Lightbox Forms {#adding-marketo-measure-script-to-lightbox-forms}

Scopri come aggiungere correttamente il JavaScript [!DNL Marketo Measure] a un modulo all&#39;interno di un lightbox.

Una lightbox apre un modulo di fronte al contenuto quando il visitatore esegue un’azione specifica, ovvero facendo clic su una parte specifica della pagina, passando un certo periodo di tempo sulla pagina e così via. In genere viene richiesto di posizionare il JavaScript [!DNL Marketo Measure] nella parte superiore della pagina di destinazione, ma per i moduli all&#39;interno di un lightbox è necessario un ulteriore passaggio.

Poiché un modulo all’interno di un lightbox è fondamentalmente un modulo all’interno di un iFrame, lo script viene posizionato all’interno di tale iFrame.

Individuare innanzitutto l&#39;iFrame in cui si trova il modulo [!UICONTROL lightbox].

![Individuazione dell&#39;iFrame del modulo Lightbox nell&#39;origine della pagina](assets/1.png)

Posizionare il JavaScript [!DNL Marketo Measure] nell&#39;iFrame.

![Script Marketo Measure inserito nell&#39;iFrame Lightbox](assets/2.png)

Infine, quando viene aggiunto il JavaScript, viene tenuta traccia degli invii di moduli di convalida seguendo queste istruzioni:

1. Copia l&#39;URL della pagina di destinazione contenente il modulo [!UICONTROL lightbox].
1. Apri un browser in incognito e incolla l’URL.
1. Invia il modulo utilizzando un indirizzo e-mail univoco.
1. Verifica che il test sia stato tracciato controllando nel CRM l’indirizzo e-mail univoco utilizzato, assicurati che i dati del punto di contatto vengano popolati.
