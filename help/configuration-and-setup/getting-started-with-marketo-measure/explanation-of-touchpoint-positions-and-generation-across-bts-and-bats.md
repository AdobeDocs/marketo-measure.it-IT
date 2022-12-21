---
description: Spiegazione delle posizioni e della generazione di punti di contatto tra BT e BAT - [!DNL Marketo Measure] - Documentazione del prodotto
title: Spiegazione delle posizioni e della generazione di punti di contatto tra BT e [!DNL BATs]
exl-id: 4903f917-a366-4767-a126-5216d2377399
source-git-commit: b910e5aedb9e178058f7af9a6907a1039458ce7a
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 0%

---

# Spiegazione delle posizioni e della generazione di punti di contatto tra BT e [!DNL BATs] {#explanation-of-touchpoint-positions-and-generation-across-bts-and-bats}

**Generazione di posizioni punto di contatto e flusso attraverso il Percorso Acquirenti**

È fondamentale comprendere le posizioni dei punti di contatto dell’acquirente e il modo in cui vengono attivati per creare rapporti con successo con [!DNL Marketo Measure] dati. Vorrai avere una chiara comprensione di cosa hanno fatto i tuoi potenziali clienti mentre si spostavano attraverso il percorso dell&#39;acquirente e a loro volta che aspetto avrà nei dati del punto di contatto. Per ulteriori informazioni su questo argomento, si consiglia di rivedere [[!UICONTROL Touchpoint Generation & Mapping]](/help/configuration-and-setup/getting-started-with-marketo-measure/touchpoint-generation-and-mapping.md) articolo.

[!DNL Marketo Measure] dispone di una varietà di posizioni punto di contatto attivate da vari passaggi nel percorso dell’acquirente. Quando si esegue il reporting su [!DNL Marketo Measure] I dati disponibili sono due set di dati punto di contatto, punti di contatto per gli acquirenti (BT) e punti di contatto per l’attribuzione degli acquirenti (BAT). È possibile notare che questi set di dati hanno posizioni leggermente diverse in relazione a oggetti diversi. Per ulteriori informazioni su questo argomento, si consiglia di rivedere [Differenza tra punti di contatto dell’acquirente (BT) e punti di contatto dell’attribuzione dell’acquirente (BAT)](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md) articolo.

**Punti di contatto dell’acquirente (BT)**: Questi sono i punti di contatto associati a una singola persona e al suo percorso e saranno unici per tale persona. I seguenti rapporti predefiniti sono costituiti dai dati dei punti di contatto dell’acquirente.

* [!DNL Marketo Measure] 101 Lead per ID
* [!DNL Marketo Measure] 101 Lead per canale
* [!DNL Marketo Measure] 101 Lead/contatto per ID
* [!DNL Marketo Measure] 101 Lead/Contatto per canale

Di seguito sono illustrate le posizioni dei punti di contatto dell&#39;acquirente che descrivono dove si trova un individuo nel suo percorso e quali azioni ha intrapreso per ottenere tale posizione.

<table> 
 <tbody>
  <tr>
   <th>Posizione punto di contatto dell’acquirente</th> 
   <th>Tipo di punto di contatto (azione che può attivare un punto di contatto)</th> 
   <th>Descrizione del punto di contatto</th> 
  </tr>
  <tr>
   <td>Primo contatto (FT)</td> 
   <td>Visita web</td> 
   <td>La prima interazione di marketing di un individuo con il tuo marchio</td> 
  </tr>
  <tr>
   <td>Creazione di lead (LC)</td> 
   <td>Riempimento modulo <strong>O</strong> Inclusione campagna/programma</td> 
   <td>Il primo modulo compilato da un singolo utente (in genere un modulo inviato, ma potrebbe anche essere un’inclusione di Campaign/Program)</td> 
  </tr>
  <tr>
   <td>Post LC</td> 
   <td>Riempimento modulo <strong>O</strong> Inclusione campagna/programma</td> 
   <td>Qualsiasi modulo di una persona completa dopo la sua LC (o una successiva inclusione di Campaign/Program)</td> 
  </tr>
 </tbody>
</table>

**Punti di contatto dell’attribuzione dell’acquirente (BATS)**: Si tratta dei punti di contatto associati a un’opportunità e al relativo percorso. Questi punti di contatto saranno collegati ai ricavi in quanto sono collegati all’opportunità e ai suoi contatti. I seguenti rapporti predefiniti sono dati di Buyer Attribution Touchpoint .

* [!DNL Marketo Measure] 101 Opportunità per ID
* [!DNL Marketo Measure] 101 Opportunità per canale ID

<table> 
 <tbody>
  <tr>
   <th>Posizione punto di contatto per l’attribuzione dell’acquirente (BAT)</th> 
   <th>Tipo di punto di contatto (azione che può attivare un punto di contatto)</th> 
   <th>Descrizione del punto di contatto</th> 
  </tr>
  <tr>
   <td>Primo contatto (FT)</td> 
   <td>Visita web</td> 
   <td>La prima interazione di marketing che un contatto ha avuto con il tuo marchio</td> 
  </tr>
  <tr>
   <td>Creazione di lead (LC)</td> 
   <td>Riempimento modulo <strong>O</strong> Inclusione campagna/programma</td> 
   <td>Il primo modulo che compila un contatto aveva (in genere un invio del modulo, ma potrebbe anche essere un’inclusione di Campaign/Program)</td> 
  </tr>
  <tr>
   <td>Creazione di opportunità</td> 
   <td>Riempimento modulo <strong>O</strong> Visita web <strong>O</strong> Inclusione campagna/programma</td> 
   <td>L’interazione di marketing più simile alla creazione dell’Opp</td> 
  </tr> 
  <tr>
   <td>Vinto/Perso chiuso</td> 
   <td>Riempimento modulo <strong>O</strong> Visita web <strong>O</strong> Inclusione campagna/programma</td> 
   <td>L’interazione di marketing più simile a quando l’Opp viene chiusa (won o perduta)</td> 
  </tr>
  <tr>
   <td>Tasti centrali</td> 
   <td>Riempimento modulo <strong>O</strong> Inclusione campagna/programma</td> 
   <td>Quando un contatto compila un modulo online e non coincide con un punto di contatto cardine</td> 
  </tr>
 </tbody>
</table>

[!DNL Marketo Measure] dispone di questi due set di dati di punti di contatto per creare una chiara comprensione del percorso di una persona e delle opportunità. Questi due set di dati per punti di contatto forniscono una mappa chiara di ciò che è successo dall’alto dell’imbuto al fondo dell’imbuto.

L’esempio seguente mostra il flusso di dati dai punti di contatto dell’acquirente ai punti di contatto di attribuzione dell’acquirente (BAT). In questo esempio la Persona A e la Persona B fanno entrambe parte della stessa Opportunità che ha una Data creazione del 3/7/2020 e una Data di chiusura del 5/6/2020.

**Persona A** Set di dati punto di contatto dell&#39;acquirente

* Primo contatto (FT) - Ricerca a pagamento.AdWords - 01/09/2019
* Creazione di lead (LC) - Ricerca organica.Google - 20/11/2019
* Post LC (compilazione modulo) - Webinar - 3/4/2020

**Persona B** Set di dati punto di contatto dell&#39;acquirente

* Primo contatto (FT) - Social a pagamento.Facebook - 26/08/2019
* Creazione di piombo (LC) - Ricerca organica.Yahoo - 2/20/2020
* Post LC (compilazione modulo) - Email - 5/1/2020

**Opportunità** I dati dei punti di contatto dell’attribuzione dell’acquirente vengono letti come segue..

* Primo contatto (FT) - Social a pagamento.Facebook - 26/08/2019
   * (da **Persona B** perché hanno il vero _Primo contatto_ per account/Opp)
* Creazione di lead (LC) - Ricerca organica.Google - 20/11/2019
   * (da **Persona A** perché hanno il vero _Creazione di lead_ per account/Opp)
* Creazione di opportunità (OC) - Webinar - 3/4/2020
   * (punto di contatto Post LC da **Persona A** sarebbe _Punto di contatto OC_ perché è stata l&#39;interazione più recente che abbiamo all&#39;opportunità che viene creata il 3/7/2020)
* Chiudi - E-mail - 01/05/2020
   * (punto di contatto Post LC da **Persona B** sarebbe _Punto di contatto chiuso con un risultato finale_ perché è stata l&#39;interazione più recente che abbiamo per l&#39;opportunità che viene chiusa il 5/6/2020)
