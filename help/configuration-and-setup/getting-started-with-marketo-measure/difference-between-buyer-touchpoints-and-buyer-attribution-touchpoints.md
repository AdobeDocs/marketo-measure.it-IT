---
unique-page-id: 18874646
description: Differenza tra punti di contatto dell’acquirente e punti di contatto dell’attribuzione dell’acquirente - [!DNL Marketo Measure] - Documentazione del prodotto
title: Differenza tra punti di contatto dell’acquirente e punti di contatto dell’attribuzione dell’acquirente
exl-id: 19109271-7b59-44c0-b1ff-e3b0bba9f5ce
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Differenza tra punti di contatto dell’acquirente e punti di contatto dell’attribuzione dell’acquirente {#difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints}

Scopri cosa definisce un punto di contatto dell’acquirente (BT) e un punto di contatto per l’attribuzione dell’acquirente (BAT), le differenze tra i due e rispondi alle domande più frequenti.

La differenza chiave tra i punti di contatto dell’acquirente e i punti di contatto dell’attribuzione dell’acquirente è la loro relazione con [!DNL Salesforce] Oggetti. I BT si riferiscono agli oggetti Lead, Contact e Case, ma non all’oggetto Opportunity. Ciò significa che non ci saranno mai ricavi associati ai punti di contatto dell&#39;acquirente.

Mentre l’oggetto punto di contatto dell’attribuzione dell’acquirente è correlato agli oggetti contatto, account e opportunità, ma non all’oggetto principale. Ciò significa che non ci saranno mai punti di contatto per l’attribuzione dell’acquirente associati ai lead. L’oggetto BAT è il luogo in cui vengono visualizzati i ricavi associati a specifiche interazioni di marketing.

Differenza tra BT e BAT:

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td>Punto di contatto dell'acquirente (BT)</td> 
   <td>Punto di contatto per l’attribuzione dell’acquirente (BAT)</td> 
  </tr> 
  <tr> 
   <td> 
    <ul> 
     <li>Si riferisce agli oggetti Lead, Contatto e Case</li> 
     <li>Non si riferisce all'oggetto Opportunity</li> 
     <li>I ricavi non sono associati a un punto di contatto dell’acquirente</li> 
    </ul></td> 
   <td> 
    <ul> 
     <li>Si riferisce agli oggetti contatto, account e opportunità</li> 
     <li>Non si riferisce all’oggetto lead</li> 
     <li>Poiché un punto di contatto di attribuzione dell’acquirente è associato a un’opportunità, a tutte le BAT sono associati dei ricavi</li> 
    </ul></td> 
  </tr> 
 </tbody> 
</table>

## Domande frequenti {#faq}

**Quando un punto di contatto dell’acquirente diventa un punto di contatto per l’attribuzione dell’acquirente?**

Un BT diventa BAT una volta che questo BT è associato a un contatto con un&#39;opportunità associata. Una cosa molto importante da capire è che una specifica interazione di marketing può essere un BT e un BAT.

**Un punto di contatto dell&#39;acquirente può avere una posizione di contatto nella creazione di opportunità (OC)?**

Un punto di contatto dell’acquirente avrà solo una posizione punto di contatto di Primo contatto (FT), Creazione di lead (LC) o invio di moduli (punti di contatto intermedi). Poiché i BT non sono correlati alle opportunità, non è possibile che un BT abbia una posizione di contatto nella creazione delle opportunità o sia chiusa.

**Come vengono utilizzati i dati dei punti di contatto dell’acquirente?**

In genere, i clienti sfruttano i dati dei punti di contatto dell’acquirente per comprendere i concetti di base e di alto livello del coinvolgimento di Funnel. Significato [!DNL Marketo Measure] gli utenti sanno chi invia i moduli, chi visualizza il sito, quali sono le prestazioni del post del blog, quali sono i risultati dell&#39;annuncio pubblicitario di AdWords che porta alla conversione, ecc. I dati del punto di contatto dell&#39;acquirente sono ideali per comprendere l&#39;impegno dei lead e dei contatti.

**Che aspetto ha un punto di contatto dell&#39;acquirente in Salesforce?**

Ecco una schermata di un BT in [!DNL Salesforce]:

![](assets/1.png)

**Che aspetto ha un punto di contatto di attribuzione dell’acquirente in Salesforce?**

Ecco uno screenshot di un BAT in [!DNL Salesforce]:

![](assets/2.png)
