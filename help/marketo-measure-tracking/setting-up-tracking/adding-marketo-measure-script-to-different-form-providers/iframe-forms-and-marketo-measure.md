---
unique-page-id: 18874741
description: IFrame Forms e [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: IFrame Forms e [!DNL Marketo Measure]
exl-id: fe8d7403-27be-4702-a1b6-d574e1243c0a
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# IFrame Forms e [!DNL Marketo Measure] {#iframe-forms-and-marketo-measure}

Con [!DNL Marketo Measure] una delle funzionalità principali consiste nel monitorare le attività di marketing digitale attraverso sessioni sul sito e l’invio di moduli. In genere, quando Marketo JavaScript viene inserito sul sito, vengono automaticamente allegati a tutti i moduli del sito. Tuttavia, questa funzionalità è limitata se il modulo è contenuto in un IFrame.

Considera un IFrame come una pagina all’interno di una pagina, quindi proprio come richiediamo che lo script venga aggiunto a tutte le pagine del sito, avremmo bisogno dello script posizionato all’interno di IFrame per garantire il tracciamento.

Vediamo in molti casi che IFrame è gestito tramite un provider di automazione marketing, quindi sarà necessario configurarlo all’interno di tale piattaforma o tramite il provider di moduli.

Si consiglia di posizionare JavaScript all’interno dell’intestazione di IFrame e da lì ci allegheremo automaticamente ai moduli all’interno di tale cornice.

![](assets/1-1.png)

Per qualsiasi domanda sull’aggiunta di JavaScript ai moduli IFrame, rivolgiti al team dell’account Adobe (il tuo Account Manager) oppure [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
