---
description: Esclusione di  [!DNL Marketo Measure]  da Forms specifico - [!DNL Marketo Measure]
title: Esclusione di  [!DNL Marketo Measure]  da Forms specifici
exl-id: ce39a3b2-2ac6-4385-b6d1-3c36b51c03fa
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# Esclusione di [!DNL Marketo Measure] da Forms specifico {#excluding-marketo-measure-from-specific-forms}

Per impostazione predefinita, [!DNL Marketo Measure] viene allegato a tutti i moduli del sito. Tuttavia, non tutti gli invii di moduli devono essere necessariamente tracciati o inclusi in un modello di attribuzione. Questo perché non tutti i riempimenti del modulo sono considerati &quot;buoni&quot;. Un esempio è dato da una pagina/modulo per l’annullamento dell’abbonamento. Inoltre, i moduli di accesso generalmente non vengono tracciati, in quanto diluirebbero il modello di attribuzione.

## Come aggiungere codice di esclusione [!DNL Marketo Measure]:  {#how-to-add-marketo-measure-exclude-code}

Per impedire a [!DNL Marketo Measure] di tenere traccia di moduli specifici, è sufficiente aggiungere &quot;[!DNL Bizible-Exclude]&quot; come &quot;classe&quot; nel modulo. Il codice è il seguente:

`<form id="myForm" action="/Home/TestPage" method="POST" class="Bizible-Exclude">`
