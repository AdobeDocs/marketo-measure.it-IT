---
unique-page-id: 18874648
description: Differenza tra conversione Google Analytics e punto di contatto dell'acquirente - [!DNL Marketo Measure] - Documentazione del prodotto
title: Differenza tra conversione Google Analytics e punto di contatto dell'acquirente
exl-id: d09d963c-3207-467c-852a-d1edd49511fa
source-git-commit: 09ffdbb0b1baeed870a3145268997e63a3707c97
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Differenza tra conversione Google Analytics e punto di contatto dell&#39;acquirente {#difference-between-a-google-analytics-conversion-and-a-buyer-touchpoint}

Scopri cosa è un [!DNL Google Analytics (GA)] l&#39;obiettivo è e come si differenzia da un punto di contatto dell&#39;acquirente.

**Cosa sono le versioni di Google Analytics?**

[!UICONTROL Google Analytics] le conversioni sono completamente determinate dal modo in cui un esperto di marketing o uno sviluppatore web codifica le completazioni &quot;obiettivo&quot; su un particolare sito web. Gli obiettivi, secondo Google, possono essere pensati come &quot;fare un acquisto (per un sito di e-commerce), completare un livello di gioco (per un&#39;app di gioco mobile), o inviare un modulo di informazioni di contatto (per un sito di marketing o di generazione di lead)&quot;. Nella maggior parte dei casi, gli esperti di marketing vedono obiettivi/conversioni come qualcuno che compila un modulo informativo.

Tuttavia, gli obiettivi non possono essere codificati per gestire un comportamento molto specifico. Al contrario, esistono tipi di obiettivi che uno sviluppatore web può configurare. Di seguito sono riportati alcuni esempi:

<table> 
 <colgroup> 
  <col> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td><strong>Tipo di obiettivo</strong></td> 
   <td><p><strong>Descrizione</strong></p></td> 
   <td><strong>Esempio</strong></td> 
  </tr> 
  <tr> 
   <td><p>Destinazione</p></td> 
   <td>Una posizione specifica viene caricata</td> 
   <td><em>Grazie per la registrazione!</em> pagina web o schermata dell’app</td> 
  </tr> 
  <tr> 
   <td>Durata</td> 
   <td>Sessioni con una durata specifica o superiore</td> 
   <td>10 minuti o più dedicati a un sito di assistenza</td> 
  </tr> 
  <tr> 
   <td>Pagine/schermi per sessione</td> 
   <td>Un utente visualizza un numero specifico di pagine o schermate</td> 
   <td>Sono state caricate 5 pagine o schermate</td> 
  </tr> 
  <tr> 
   <td>Evento</td> 
   <td>Viene attivata un’azione definita come Evento</td> 
   <td>Raccomandazione social, riproduzione video e clic</td> 
  </tr> 
 </tbody> 
</table>

La maggior parte degli esperti di marketing configura le conversioni come &quot;Obiettivi di destinazione&quot;, il che significa che di solito creano una pagina di ringraziamento dopo un modulo per considerare tale conversione formale.

Ciò significa che Google considererà le visualizzazioni della pagina di ringraziamento come una conversione. Dal punto di vista delle Google Analytics, questa è una realizzazione con cui la maggior parte degli esperti di marketing sono d&#39;accordo.

Tuttavia, i punti di contatto dell’acquirente agiscono in modo molto diverso.

**Quali sono le differenze tra i punti di contatto dell’acquirente?**

[!DNL Marketo Measure] JavaScript tiene traccia dei dati di sessione e degli invii dei moduli su tutte le forme di un sito specifico. Non è necessario codificare gli obiettivi da un [!DNL Marketo Measure] punto di vista. Questo processo è automatico. Per gli invii di moduli, [!DNL Marketo Measure] segnala il completamento di un modulo ogni volta che un utente anonimo compila i campi di informazioni in un particolare modulo e fa clic sul pulsante di invio del modulo. [!DNL Marketo Measure] non richiede una pagina di ringraziamento per registrare l’invio del modulo.

[!DNL Marketo Measure] crea un punto di contatto modulo quando:

* Un lead/contatto associato a tali conversioni viene visualizzato nel CRM.
* La [!DNL Marketo Measure] JS è presente nelle pagine web contenenti il modulo.
* Un modulo viene inviato entro una sessione di 30 minuti.

[!DNL Marketo Measure] ignorerà le conversioni di Destination Google Analytics quando:

* Un bot invia moduli su un sito web (di solito questi bot non li trasformano in CRM di un cliente).
* Dopo il primo invio, un utente invia più moduli. [!DNL Marketo Measure] invierà solo la prima conversione da quella sessione.
* L’utente fa clic più volte sull’invio del modulo. [!DNL Marketo Measure] prenderà in considerazione solo il primo invio del modulo.
* L’utente ricarica la pagina di ringraziamento più volte.
* L’utente utilizza qualsiasi strumento di blocco degli annunci.

Come potete vedere ci sono differenze fondamentali tra ciò che GA e [!DNL Marketo Measure] considera una conversione da considerare. Pertanto, sarà molto probabile che il numero di conversioni e il numero di punti di contatto del modulo differiscano.
