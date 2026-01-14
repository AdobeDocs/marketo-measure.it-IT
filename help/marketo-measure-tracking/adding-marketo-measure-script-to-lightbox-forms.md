---
description: Aggiunta di  [!DNL Marketo Measure] script alle linee guida di Lightbox Forms per gli utenti di Marketo Measure
title: Aggiunta dello script  [!DNL Marketo Measure]  a Lightbox Forms
exl-id: fa9ce480-fc4f-4abd-8555-dbb74849747e
feature: Tracking
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# Aggiunta dello script [!DNL Marketo Measure] a Lightbox Forms {#adding-marketo-measure-script-to-lightbox-forms}

Scopri come aggiungere correttamente il JavaScript [!DNL Marketo Measure] a un modulo all&#39;interno di un lightbox.

Una lightbox apre un modulo di fronte al contenuto quando il visitatore esegue un’azione specifica, ovvero facendo clic su una parte specifica della pagina, passando un certo periodo di tempo sulla pagina e così via. In genere viene richiesto di posizionare il JavaScript [!DNL Marketo Measure] nella parte superiore della pagina di destinazione, ma per i moduli all&#39;interno di un lightbox è necessario un ulteriore passaggio.

Poiché un modulo all’interno di un lightbox è fondamentalmente un modulo all’interno di un iFrame, lo script viene posizionato all’interno di tale iFrame.

Individuare innanzitutto l&#39;iFrame in cui si trova il modulo [!UICONTROL lightbox].

![Individuare innanzitutto l&#39;iFrame in cui si trova il modulo lightbox.](assets/adding-providers-8.png)

Posizionare il JavaScript [!DNL Marketo Measure] nell&#39;iFrame.

![Inserire il JavaScript di Marketo Measure nell&#39;iFrame.](assets/adding-providers-5.png)

Infine, quando viene aggiunto il JavaScript, viene tenuta traccia degli invii di moduli di convalida seguendo queste istruzioni:

1. Copia l&#39;URL della pagina di destinazione contenente il modulo [!UICONTROL lightbox].
1. Apri un browser in incognito e incolla l’URL.
1. Invia il modulo utilizzando un indirizzo e-mail univoco.
1. Verifica che il test sia stato tracciato controllando nel CRM l’indirizzo e-mail univoco utilizzato, assicurati che i dati del punto di contatto vengano popolati.
