---
unique-page-id: 18874646
description: Differenza tra punti di contatto dell'acquirente e punti di contatto di attribuzione dell'acquirente - [!DNL Marketo Measure]
title: Differenza tra i punti di contatto dell’acquirente e i punti di contatto di attribuzione dell’acquirente
exl-id: 19109271-7b59-44c0-b1ff-e3b0bba9f5ce
feature: Touchpoints
source-git-commit: bdc32fdfe24d57fd7770654f1238896c7b59acf6
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Differenza tra i punti di contatto dell’acquirente e i punti di contatto di attribuzione dell’acquirente {#difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints}

Scopri cosa definisce un Buyer Touchpoint (BT) e un Buyer Attribution Touchpoint (BAT), le differenze tra i due e rispondi alle domande più frequenti.

Il punto di contatto principale tra i punti di contatto dell&#39;acquirente e i punti di contatto di attribuzione dell&#39;acquirente è la relazione con [!DNL Salesforce] oggetti. L’BT si riferisce agli oggetti Lead, Contact e Case, ma non all’oggetto Opportunity. Ciò significa che non ci sono mai ricavi associati ai punti di contatto dell’acquirente.

Sebbene l&#39;oggetto Buyer Attribution Touchpoint sia correlato agli oggetti Contatto, Account e Opportunità, ma non all&#39;oggetto Lead, i punti di contatto di attribuzione buyer non sono legati ai lead. L’oggetto BAT è il luogo in cui vedrai i ricavi legati a specifiche interazioni di marketing.

Differenza tra BT e BAT:

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td>Buyer Touchpoint (BT)</td> 
   <td>Buyer Attribution Touchpoint (BAT)</td> 
  </tr> 
  <tr> 
   <td> 
    <ul> 
     <li>Correlato agli oggetti lead, contatto e caso</li> 
     <li>Non si riferisce all'oggetto Opportunity</li> 
     <li>Il ricavo non è associato a un Buyer Touchpoint</li> 
    </ul></td> 
   <td> 
    <ul> 
     <li>Correlato agli oggetti Contatto, Account e Opportunità</li> 
     <li>Non si riferisce all'oggetto lead</li> 
     <li>Poiché un Buyer Attribution Touchpoint è associato a un’opportunità, a tutti gli BAT sono associati dei ricavi</li> 
    </ul></td> 
  </tr> 
 </tbody> 
</table>

## Domande frequenti {#faq}

**Quando un Buyer Touchpoint diventa un Buyer Attribution Touchpoint?**

Un BT diventa BAT quando questo BT è associato a un contatto a cui è associata un’opportunità. Una cosa importante da capire è che una specifica interazione di marketing può essere un BT e un BAT.

**Un Buyer Touchpoint può avere una posizione punto di contatto per la creazione di opportunità (OC)?**

Un Buyer Touchpoint avrà solo una posizione del punto di contatto Primo contatto (FT), Creazione di lead (LC) o Invio di moduli (punti di contatto intermedi). Poiché l’BT non è correlato alle opportunità, non è possibile per un BT avere un punto di contatto Posizione di creazione opportunità o Chiuso.

**Utilizzo dei dati di Buyer Touchpoint**

In genere i clienti utilizzano i dati di Buyer Touchpoint per comprendere il punto più alto e il punto centrale del coinvolgimento funnel. Ciò significa che [!DNL Marketo Measure] utenti sanno chi sta inviando i moduli, chi sta visualizzando il loro sito, cosa funziona bene il post di blog, cosa l&#39;annuncio AdWords sta guidando porta a conversioni e così via. I dati di Buyer Touchpoint sono ideali per comprendere il coinvolgimento dei lead e dei contatti.

**Che aspetto ha un Buyer Touchpoint in Salesforce?**

Ecco la schermata di un BT in [!DNL Salesforce]:

![](assets/buyer-touchpoints-and-buyer-attribution-touchpoints-1.png){width="600" zoomable="yes"}

**Che aspetto ha un Buyer Attribution Touchpoint in Salesforce?**

Ecco la schermata di un BAT in [!DNL Salesforce]:

![](assets/buyer-touchpoints-and-buyer-attribution-touchpoints-2.png){width="600" zoomable="yes"}
