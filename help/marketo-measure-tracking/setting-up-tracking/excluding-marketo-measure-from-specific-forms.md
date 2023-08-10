---
unique-page-id: 18874783
description: Esclusione [!DNL Marketo Measure] da Forms specifico - [!DNL Marketo Measure] - Documentazione del prodotto
title: Esclusione [!DNL Marketo Measure] da Forms specifico
exl-id: ce39a3b2-2ac6-4385-b6d1-3c36b51c03fa
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Esclusione [!DNL Marketo Measure] da Forms specifico {#excluding-marketo-measure-from-specific-forms}

Per impostazione predefinita, [!DNL Marketo Measure] viene allegato a tutti i moduli del sito. Tuttavia, non tutti gli invii di moduli devono necessariamente essere tracciati o inclusi in un modello di attribuzione. Questo perché non tutti i riempimenti del modulo sono considerati &quot;buoni&quot;. Un esempio è dato da una pagina/modulo per l’annullamento dell’abbonamento. Inoltre, i moduli di accesso in genere non vengono tracciati, in quanto diluirebbero il modello di attribuzione.

## Come aggiungere [!DNL Marketo Measure]-codice di esclusione:  {#how-to-add-marketo-measure-exclude-code}

Per evitare [!DNL Marketo Measure] dal tracciamento di moduli specifici, aggiungi semplicemente &quot;[!DNL Bizible-Exclude]&quot; come &#39;classe&#39; nel modulo. Il codice è il seguente:

`<form id="myForm" action="/Home/TestPage" method="POST" class="Bizible-Exclude">`
