---
unique-page-id: 18874560
description: Perché Non Eliminare Mai I Punti Di Contatto - [!DNL Marketo Measure] - Documentazione del prodotto
title: Perché Non Eliminare Mai I Punti Di Contatto
exl-id: e74c14ff-0399-4ee9-b732-6686823ff5c7
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Perché Non Eliminare Mai I Punti Di Contatto {#why-you-should-never-delete-touchpoints}

Se noti che esiste un punto di contatto su un’opportunità a cui viene assegnato un credito di attribuzione in modo errato, contatta il tuo Account Manager per determinare i passaggi successivi. In queste situazioni, si consiglia di utilizzare la funzione di soppressione dei punti di contatto dell’acquirente per rimuovere il punto di contatto dall’SFDC e dal dashboard del ROI. Il tuo account manager può aiutarti a creare queste regole. Non eliminare manualmente questi punti di contatto.

La [!DNL Marketo Measure] Il sistema di elaborazione non registra l’eliminazione manuale di un punto di contatto da SFDC. A partire da oggi, non c&#39;è alcun trigger che segnala al nostro sistema per regolare i dati. [!DNL Marketo Measure] non invia automaticamente un altro punto di contatto per sostituire quello eliminato, né riassegnerà la posizione o l’attribuzione del punto di contatto al punto di contatto successivo.

Quando un punto di contatto viene eliminato, crea un buco nei dati di attribuzione. In genere questo si manifesta nei punti di contatto di attribuzione su un’opportunità. Nell’immagine seguente, il punto di contatto che avrebbe ricevuto il tocco Creazione opportunità è stato eliminato. Di conseguenza, a questa opportunità manca il punto di contatto OC e la percentuale di attribuzione per questo Opp non salirà al 100%.

![](assets/1.png)

Se i punti di contatto sono stati cancellati dal tuo SFDC, contatta [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} per richiedere una reimportazione dei dati.
