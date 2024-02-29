---
unique-page-id: 18874690
description: Autorizzazione di nuovo account connessi - [!DNL Marketo Measure]
title: Autorizzazione di nuovo account collegati
exl-id: 7abd1d67-5bed-45bb-844f-0ffd23c3d7f8
feature: APIs, Integration
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Autorizzazione di nuovo account collegati {#reauthorizing-connected-accounts}

Quando un account viene disconnesso dal tuo [!DNL Marketo Measure] , lo stato della piattaforma passerà a &quot;Autorizzazione richiesta&quot; e visualizzerà un&#39;icona a forma di chiave rossa.

Se la piattaforma dell’annuncio viene disconnessa, [!DNL Marketo Measure] non sarà in grado di scaricare i dati sui costi o, se l’assegnazione automatica dei tag è abilitata, aggiungi [!DNL Marketo Measure] Parametri UTM per qualsiasi annuncio appena creato. [!DNL Marketo Measure] non potrà aggiungere retroattivamente i parametri UTM ai punti di contatto creati dalla piattaforma pubblicitaria mentre l’account era disconnesso.

Se la piattaforma CRM viene disconnessa, [!DNL Marketo Measure] non potrà aggiornare [!DNL Marketo Measure] o inserisci nuovi punti di contatto nell’organizzazione. Una volta ristabilita la connessione CRM, [!DNL Marketo Measure] invierà tutti i dati mancanti durante la disconnessione dell’account.

![](assets/1-1.png)

## Autorizzazione di nuovo account disconnessi {#re-authorizing-disconnected-accounts}

1. Vai a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} e accedi.
1. Seleziona **[!UICONTROL Settings]** sotto [!UICONTROL My Account] nell’angolo in alto a sinistra.
1. Trova la sezione Integrazioni a sinistra e fai clic su **[!UICONTROL Connections]**.
1. Selezionare il simbolo del tasto rosso accanto all&#39;account da riconnettere.
1. Viene visualizzata una finestra pop-up in cui viene richiesto di fornire i dettagli di accesso per l&#39;account.
