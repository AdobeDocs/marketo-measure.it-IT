---
unique-page-id: 18874560
description: Perché non eliminare mai i punti di contatto - [!DNL Marketo Measure] - Documentazione del prodotto
title: Perché non eliminare mai i punti di contatto
exl-id: e74c14ff-0399-4ee9-b732-6686823ff5c7
feature: Touchpoints
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Perché non eliminare mai i punti di contatto {#why-you-should-never-delete-touchpoints}

Se riscontri che è presente un punto di contatto in un’opportunità a cui viene assegnato il credito di attribuzione in modo errato, contatta il tuo Account Manager per determinare i passaggi successivi. In queste situazioni, consigliamo di utilizzare la funzione di eliminazione dei punti di contatto dell’acquirente per rimuovere il punto di contatto da SFDC e dalla dashboard ROI. Il tuo account manager può aiutarti a creare queste regole. Non eliminare manualmente questi punti di contatto.

Il [!DNL Marketo Measure] Il sistema di elaborazione non registrerà che un punto di contatto è stato eliminato manualmente da SFDC. A partire da oggi, non esiste un trigger che segnali al nostro sistema per la regolazione dei dati. [!DNL Marketo Measure] non invierà automaticamente un altro punto di contatto in sostituzione di quello eliminato, né riassegnerà la posizione o l’attribuzione al punto di contatto successivo.

Quando un punto di contatto viene eliminato, crea un buco nei dati di attribuzione. In genere, questo si manifesta nei punti di contatto di attribuzione su un’opportunità. Nell’immagine seguente, il punto di contatto che avrebbe ricevuto il contatto Creazione opportunità è stato eliminato. Di conseguenza, a questa opportunità manca il punto di contatto OC e la percentuale di attribuzione per questa Opp non si sommerà fino al 100%.

![](assets/1.png)

Se i punti di contatto sono stati eliminati dall&#39;SFDC, contatta [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} per richiedere la reimportazione dei dati.
