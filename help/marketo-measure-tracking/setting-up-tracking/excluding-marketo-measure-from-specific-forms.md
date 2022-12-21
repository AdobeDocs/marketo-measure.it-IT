---
unique-page-id: 18874783
description: Esclusione [!DNL Marketo Measure] da Forms specifico - [!DNL Marketo Measure] - Documentazione del prodotto
title: Esclusione [!DNL Marketo Measure] da Forms specifico
exl-id: ce39a3b2-2ac6-4385-b6d1-3c36b51c03fa
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Esclusione [!DNL Marketo Measure] da Forms specifico {#excluding-marketo-measure-from-specific-forms}

Per impostazione predefinita, [!DNL Marketo Measure] si allega a tutti i moduli sul sito. Tuttavia, non tutti gli invii di moduli devono necessariamente essere tracciati o inclusi in un modello di attribuzione. Questo perché non tutti i riempimenti dei moduli sono considerati &quot;buoni&quot;. Un esempio è la pagina o il modulo di annullamento dell’abbonamento. Inoltre, i moduli di accesso generalmente non vengono tracciati in quanto diluirebbero il modello di attribuzione.

## Come aggiungere [!DNL Marketo Measure]-escludi codice:  {#how-to-add-marketo-measure-exclude-code}

Per evitare [!DNL Marketo Measure] dal tracciamento di moduli specifici, è sufficiente aggiungere &quot;[!DNL Bizible-Exclude]&quot; come &quot;classe&quot; sul modulo. Il codice è il seguente:

`<form id="myForm" action="/Home/TestPage" method="POST" class="Bizible-Exclude">`
