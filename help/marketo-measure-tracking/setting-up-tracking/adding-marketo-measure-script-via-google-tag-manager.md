---
unique-page-id: 18874797
description: Aggiunta [!DNL Marketo Measure] Script tramite [!DNL Google Tag Manager] - [!DNL Marketo Measure]
title: Aggiunta [!DNL Marketo Measure] Script tramite [!DNL Google Tag Manager]
exl-id: 539efb10-35cb-4146-8eea-728c3948a11e
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] Script tramite [!DNL Google Tag Manager] {#adding-marketo-measure-script-via-google-tag-manager}

Durante l&#39;installazione di [!DNL Marketo Measure] JavaScript, si consiglia di: [codifica a livello di codice dello script](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md){target="_blank"} direttamente nel sito. Se ciò non è possibile, puoi anche utilizzare [!DNL Google Tag Manager] (GTM) per caricare [!DNL Marketo Measure] JS. Tieni presente che [!DNL Marketo Measure] JS caricato tramite GTM è soggetto a latenza. La latenza causa un ritardo nei tempi di caricamento dello script che può comportare la perdita di circa il 3-5% di tutte le richieste del modulo.

Se decidi di aggiungere il nostro script tramite GTM, imposta il [!DNL Marketo Measure] script alla massima priorità nell&#39;ordine di attivazione e assicurarsi che non vi siano script sincroni davanti al [!DNL Marketo Measure] per ridurre eventuali effetti dalla latenza GTM.

>[!NOTE]
>
>Usa questo [articolo di supporto di Google](https://support.google.com/tagmanager/answer/2772421?hl=en){target="_blank"} per ulteriori informazioni.

## Come aggiungere [!DNL Marketo Measure] JS tramite [!DNL Google Tag Manager] {#how-to-add-marketo-measure-js-via-google-tag-manager}

1. Apri GTM e aggiungi [!DNL Marketo Measure] script nel contenitore del sito web. Assicurati di selezionare **[!UICONTROL Custom HTML tag]**.

1. Utilizza il [!DNL Marketo Measure] inseriscilo nello script sottostante e incorporalo nel contenitore.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Clic **[!UICONTROL Add a Firing Rule]** in modo da poter dire a Google di caricare il frammento su *Tutte le pagine*.

1. Vai alla sezione Panoramica bozza contenitore a sinistra. Fai clic sul pulsante per creare una versione del contenitore e pubblicare le modifiche.
