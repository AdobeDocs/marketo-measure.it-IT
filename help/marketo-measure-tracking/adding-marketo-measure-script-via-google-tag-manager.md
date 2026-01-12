---
description: Aggiunta di  [!DNL Marketo Measure] script tramite [!DNL Google Tag Manager] - [!DNL Marketo Measure]
title: Aggiunta di  [!DNL Marketo Measure] script tramite [!DNL Google Tag Manager]
exl-id: 539efb10-35cb-4146-8eea-728c3948a11e
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---


# Aggiunta dello script [!DNL Marketo Measure] tramite [!DNL Google Tag Manager] {#adding-marketo-measure-script-via-google-tag-manager}

Durante l&#39;installazione di [!DNL Marketo Measure] JavaScript, si consiglia di [codificare lo script](/help/marketo-measure-tracking/adding-marketo-measure-script.md){target="_blank"} direttamente nel sito. Se ciò non è possibile, puoi anche utilizzare [!DNL Google Tag Manager] (GTM) per caricare [!DNL Marketo Measure] JS. [!DNL Marketo Measure] JS caricato tramite GTM è soggetto a latenza. La latenza causa un ritardo nei tempi di caricamento dello script che può comportare la perdita di circa il 3-5% di tutte le richieste del modulo.

Se decidi di aggiungere lo script tramite GTM, imposta lo script [!DNL Marketo Measure] alla massima priorità nell&#39;ordine di attivazione e assicurati che non vi siano script sincroni davanti al tag [!DNL Marketo Measure] per ridurre eventuali effetti dalla latenza GTM.

>[!NOTE]
>Utilizza questo articolo di supporto [di Google](https://support.google.com/tagmanager/answer/2772421?hl=en){target="_blank"} per ulteriori informazioni.

## Come aggiungere [!DNL Marketo Measure] JS tramite [!DNL Google Tag Manager] {#how-to-add-marketo-measure-js-via-google-tag-manager}

1. Apri GTM e aggiungi lo script [!DNL Marketo Measure] nel contenitore del tuo sito Web. Assicurarsi di selezionare **[!UICONTROL Custom HTML tag]**.

1. Utilizza lo script [!DNL Marketo Measure] di seguito e incorporalo nel tuo contenitore.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Fai clic su **[!UICONTROL Add a Firing Rule]** per dire a Google di caricare il nostro snippet su *Tutte le pagine*.

1. Vai alla sezione Panoramica bozza contenitore a sinistra. Fai clic sul pulsante per creare una versione del contenitore e pubblicare le modifiche.
