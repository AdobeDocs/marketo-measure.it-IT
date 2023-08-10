---
unique-page-id: 18874646
description: Differenza tra i punti di contatto dell’acquirente e i punti di contatto di attribuzione dell’acquirente - [!DNL Marketo Measure] - Documentazione del prodotto
title: Differenza tra i punti di contatto dell’acquirente e i punti di contatto di attribuzione dell’acquirente
exl-id: 19109271-7b59-44c0-b1ff-e3b0bba9f5ce
feature: Touchpoints
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Differenza tra i punti di contatto dell’acquirente e i punti di contatto di attribuzione dell’acquirente {#difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints}

Scopri cosa definisce un punto di contatto per l’acquirente (BT) e un punto di contatto per l’attribuzione dell’acquirente (BAT), le differenze tra i due e rispondi alle domande più frequenti.

La distinzione chiave tra punti di contatto dell’acquirente e punti di contatto di attribuzione dell’acquirente è la loro relazione con [!DNL Salesforce] Oggetti. Gli oggetti BT sono correlati agli oggetti lead, contatto e caso, ma non all&#39;oggetto opportunità. Ciò significa che non ci saranno mai ricavi associati ai punti di contatto dell&#39;acquirente.

L&#39;oggetto punto di contatto di attribuzione buyer è correlato agli oggetti contatto, account e opportunità, ma non all&#39;oggetto lead. Ciò significa che non ci saranno mai punti di contatto di attribuzione acquirente collegati ai lead. L’oggetto BAT è il luogo in cui vedrai i ricavi legati a specifiche interazioni di marketing.

Differenza tra BT e BAT:

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td>Punto di contatto dell'acquirente (BT)</td> 
   <td>Punto di contatto di attribuzione acquirente (BAT)</td> 
  </tr> 
  <tr> 
   <td> 
    <ul> 
     <li>Correlato agli oggetti lead, contatto e caso</li> 
     <li>Non si riferisce all'oggetto Opportunity</li> 
     <li>I ricavi non sono associati a un punto di contatto dell'acquirente</li> 
    </ul></td> 
   <td> 
    <ul> 
     <li>Correlato agli oggetti Contatto, Account e Opportunità</li> 
     <li>Non si riferisce all'oggetto lead</li> 
     <li>Poiché un punto di contatto di attribuzione buyer è associato a un'opportunità, tutte le BAT hanno ricavi associati</li> 
    </ul></td> 
  </tr> 
 </tbody> 
</table>

## Domande frequenti {#faq}

**Quando un punto di contatto buyer diventa un punto di contatto di attribuzione buyer?**

Un BT diventa un BAT una volta che questo BT è associato a un contatto a cui è associata un&#39;opportunità. Una cosa molto importante da capire è che una specifica interazione di marketing può essere un BT e un BAT.

**Un punto di contatto dell&#39;acquirente può avere una posizione di contatto per la creazione di opportunità (OC)?**

Un punto di contatto acquirente avrà solo una posizione di primo contatto (FT), creazione di lead (LC) o invio di moduli (punti di contatto intermedi). Dal momento che le BT non sono correlate alle opportunità, non è possibile che una BT abbia una posizione di contatto di creazione dell&#39;opportunità o chiusa.

**In che modo vengono utilizzati i dati dei punti di contatto dell’acquirente?**

In genere i clienti sfruttano i dati dei punti di contatto dell’acquirente per comprendere meglio il coinvolgimento funnel e intermedio del funnel. Significato [!DNL Marketo Measure] Gli utenti sanno chi invia i moduli, chi visualizza il loro sito, quale post di blog funziona bene, quali annunci pubblicitari AdWords spingono alla conversione, ecc. I dati dei punti di contatto dell&#39;acquirente sono utili per comprendere il coinvolgimento dei lead e dei contatti.

**Come si presenta un punto di contatto acquirente in Salesforce?**

Ecco la schermata di un BT in [!DNL Salesforce]:

![](assets/1.png)

**Come si presenta un punto di contatto per l’attribuzione dell’acquirente in Salesforce?**

Ecco uno screenshot di una mazza in [!DNL Salesforce]:

![](assets/2.png)
