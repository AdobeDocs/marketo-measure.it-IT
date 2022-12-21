---
unique-page-id: 18874797
description: Aggiunta [!DNL Marketo Measure] Script tramite [!DNL Google Tag Manager] - [!DNL Marketo Measure] - Documentazione del prodotto
title: Aggiunta [!DNL Marketo Measure] Script tramite [!DNL Google Tag Manager]
exl-id: 539efb10-35cb-4146-8eea-728c3948a11e
source-git-commit: 82cc8269bfdb26b6acf039d0ce0e06564f5e2612
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] Script tramite [!DNL Google Tag Manager] {#adding-marketo-measure-script-via-google-tag-manager}

Quando installi [!DNL Marketo Measure] javascript, consigliamo vivamente [codifica dello script](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md){target=&quot;_blank&quot;} direttamente nel sito. Tuttavia, se ciò non è possibile, puoi anche utilizzare [!DNL Google Tag Manager] (GTM) per caricare [!DNL Marketo Measure] JS. Si prega di notare che [!DNL Marketo Measure] JS caricato attraverso GTM è suscettibile di latenza. La latenza causa un ritardo nei tempi di caricamento degli script che può causare la perdita di circa il 3-5% di tutti gli invii dei moduli.

Se decidi di aggiungere il nostro script tramite GTM, imposta la [!DNL Marketo Measure] esegui lo script con la priorità più elevata nell&#39;ordine di attivazione e assicurati che non vi siano script sincroni davanti al [!DNL Marketo Measure] per ridurre eventuali effetti della latenza GTM.

>[!NOTE]
>
>Utilizza questo [articolo di supporto di Google](https://support.google.com/tagmanager/answer/2772421?hl=en){target=&quot;_blank&quot;} per ulteriori informazioni.

## Come aggiungere [!DNL Marketo Measure] JS tramite [!DNL Google Tag Manager] {#how-to-add-marketo-measure-js-via-google-tag-manager}

1. Apri GTM e aggiungi la [!DNL Marketo Measure] nel contenitore del sito web. Assicurati di selezionare **[!UICONTROL Custom HTML tag]**.

1. Utilizza la [!DNL Marketo Measure] esegui lo script sottostante e incorporalo nel contenitore .

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Fai clic su **[!UICONTROL Add a Firing Rule]** in modo che Google possa caricare lo snippet su *Tutte le pagine*.

1. Vai alla sezione Panoramica della bozza del contenitore a sinistra. Fai clic sul pulsante per creare una nuova versione del contenitore e pubblicare le modifiche.
