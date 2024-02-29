---
unique-page-id: 18874648
description: Differenza tra una conversione Google Analytics e un punto di contatto acquirente - [!DNL Marketo Measure]
title: Differenza tra una conversione Google Analytics e un punto di contatto acquirente
exl-id: d09d963c-3207-467c-852a-d1edd49511fa
feature: Touchpoints
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Differenza tra una conversione Google Analytics e un punto di contatto acquirente {#difference-between-a-google-analytics-conversion-and-a-buyer-touchpoint}

Scopri che cos’è un [!DNL Google Analytics (GA)] L&#39;obiettivo è e come si differenzia da un punto di contatto dell&#39;acquirente.

**Cosa sono le conversioni delle Google Analytics?**

[!UICONTROL Google Analytics] le conversioni sono completamente determinate dal modo in cui un addetto marketing o uno sviluppatore web codifica i completamenti &quot;obiettivo&quot; su un particolare sito web. Gli obiettivi, secondo Google, possono essere considerati come &quot;fare un acquisto (per un sito di e-commerce), completare un livello di gioco (per un’app di gioco mobile) o inviare un modulo di informazioni di contatto (per un sito di marketing o generazione di lead)&quot;. Nella maggior parte dei casi, gli esperti di marketing considerano gli obiettivi/conversioni come se stessero compilando un modulo informativo.

Tuttavia, gli obiettivi non possono essere codificati per gestire un comportamento molto specifico. Piuttosto, esistono Tipi di Obiettivo che uno sviluppatore web può configurare. Di seguito sono riportati alcuni di questi esempi:

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
   <td>Caricamenti di una posizione specifica</td> 
   <td><em>Grazie per la registrazione.</em> pagina web o schermata dell’app</td> 
  </tr> 
  <tr> 
   <td>Durata</td> 
   <td>Sessioni che durano una specifica quantità di tempo o più</td> 
   <td>10 minuti o più trascorsi su un sito di supporto</td> 
  </tr> 
  <tr> 
   <td>Pagine/Schermate per sessione</td> 
   <td>Un utente visualizza un numero specifico di pagine o schermate</td> 
   <td>Sono state caricate 5 pagine o schermate</td> 
  </tr> 
  <tr> 
   <td>Evento</td> 
   <td>Viene attivata un'azione definita come evento</td> 
   <td>Consigli social, riproduzione video e clic</td> 
  </tr> 
 </tbody> 
</table>

La maggior parte degli esperti di marketing configura le conversioni come &quot;Obiettivi di destinazione&quot;, il che significa che solitamente creano una pagina di ringraziamento dopo un modulo per considerare tale conversione formale.

Ciò significa che Google considererà le visualizzazioni di pagina di ringraziamento come una conversione. Dal punto di vista della Google Analytics, si tratta di una realizzazione che la maggior parte degli addetti al marketing considera positivamente.

Tuttavia, i punti di contatto dell’acquirente agiscono in modo molto diverso.

**Quali sono le differenze tra i punti di contatto dell&#39;acquirente?**

[!DNL Marketo Measure] JavaScript tiene traccia dei dati di sessione e degli invii di moduli in tutti i moduli di un particolare sito. Non è necessario programmare gli obiettivi da un [!DNL Marketo Measure] punto di vista. Questo processo è automatico. Per l’invio di moduli, [!DNL Marketo Measure] segnala il completamento di un modulo ogni volta che un utente anonimo compila campi di informazioni su un modulo specifico e fa clic sul pulsante di invio del modulo. [!DNL Marketo Measure] non ha bisogno di una pagina di ringraziamento per registrare l’invio del modulo.

[!DNL Marketo Measure] creerà un punto di contatto del modulo quando:

* Un lead/contatto associato a tali conversioni viene visualizzato nel CRM.
* Il [!DNL Marketo Measure] JS è presente nelle pagine web che contengono il modulo.
* Un modulo viene inviato entro una sessione di 30 minuti.

[!DNL Marketo Measure] ignora le conversioni di Destination Google Analytics quando:

* Un bot invia moduli su un sito web (di solito non entrano nel sistema CRM del cliente).
* Un utente invia più moduli dopo il primo invio. [!DNL Marketo Measure] invierà solo la prima conversione da quella sessione.
* L’utente fa clic più volte sull’invio del modulo. [!DNL Marketo Measure] prenderà in considerazione solo il primo invio del modulo.
* L’utente ricarica la pagina di ringraziamento più volte.
* L’utente utilizza qualsiasi strumento di Ad Blocking.

Come puoi vedere ci sono differenze fondamentali tra ciò che GA e [!DNL Marketo Measure] considera una conversione come. Pertanto, è molto probabile che il numero di conversioni e il numero di punti di contatto in forma differiscano.
