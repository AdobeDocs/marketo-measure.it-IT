---
description: Perché non eliminare mai le indicazioni sui punti di contatto per gli utenti di Marketo Measure
title: Perché non eliminare mai i punti di contatto
exl-id: e74c14ff-0399-4ee9-b732-6686823ff5c7
feature: Touchpoints
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Perché non eliminare mai i punti di contatto {#why-you-should-never-delete-touchpoints}

Se riscontri che è presente un punto di contatto in un’opportunità a cui viene assegnato erroneamente il credito di attribuzione, contatta il tuo Account Manager per determinare i passaggi successivi. In queste situazioni, consigliamo di utilizzare la funzione di eliminazione dei punti di contatto dell’acquirente per rimuovere il punto di contatto da SFDC e dalla dashboard del ROI. Il tuo account manager può aiutarti a creare queste regole. Non eliminare manualmente questi punti di contatto.

Il sistema di elaborazione [!DNL Marketo Measure] non registrerà che un punto di contatto è stato eliminato manualmente da SFDC. A partire da oggi, non esiste un trigger che segnali al nostro sistema per la regolazione dei dati. [!DNL Marketo Measure] non invierà automaticamente un altro punto di contatto per sostituire quello eliminato, né riassegnerà la posizione o l&#39;attribuzione al punto di contatto successivo.

Quando un punto di contatto viene eliminato, crea un buco nei dati di attribuzione. In genere, questo si manifesta nei punti di contatto di attribuzione su un’opportunità. Nell’immagine seguente, il punto di contatto che avrebbe ricevuto il contatto Creazione opportunità è stato eliminato. Di conseguenza, a questa opportunità manca il punto di contatto OC e la percentuale di attribuzione per questa Opp non si sommerà fino al 100%.

![](assets/touchpoint-settings-10.png)

Se i punti di contatto sono stati eliminati dal SFDC, rivolgiti al [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} per richiedere la reimportazione dei dati.
