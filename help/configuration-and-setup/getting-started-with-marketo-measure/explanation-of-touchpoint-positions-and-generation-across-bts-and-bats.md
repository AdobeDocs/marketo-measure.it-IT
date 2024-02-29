---
description: Spiegazione delle posizioni dei punti di contatto e della generazione tra BT e BAT - [!DNL Marketo Measure]
title: Spiegazione delle posizioni dei punti di contatto e della generazione tra BT e [!DNL BATs]
exl-id: 4903f917-a366-4767-a126-5216d2377399
feature: Touchpoints
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---

# Spiegazione delle posizioni dei punti di contatto e della generazione tra BT e [!DNL BATs] {#explanation-of-touchpoint-positions-and-generation-across-bts-and-bats}

**Generazione di posizioni dei punti di contatto e flusso attraverso il Percorso degli acquirenti**

Comprendere le posizioni dei punti di contatto dell’acquirente e come vengono attivate è fondamentale per creare rapporti con successo con [!DNL Marketo Measure] dati. Vorrai avere una chiara comprensione di ciò che hanno fatto i tuoi potenziali clienti mentre si spostavano nel percorso dell’acquirente e, a sua volta, di ciò che apparirà nei dati del punto di contatto. Per ulteriori informazioni su questo argomento, si consiglia di rivedere [[!UICONTROL Touchpoint Generation & Mapping]](/help/configuration-and-setup/getting-started-with-marketo-measure/touchpoint-generation-and-mapping.md) articolo.

[!DNL Marketo Measure] dispone di una varietà di posizioni di punto di contatto attivate da vari passaggi nel percorso dell’acquirente. Quando si segnala [!DNL Marketo Measure] Esistono due set di dati relativi ai punti di contatto: i punti di contatto dell’acquirente (BT) e i punti di contatto di attribuzione dell’acquirente (BAT). Potresti notare che questi set di dati hanno posizioni leggermente diverse in quanto si riferiscono a oggetti diversi. Per ulteriori informazioni su questo argomento, si consiglia di rivedere [Differenza tra i punti di contatto dell&#39;acquirente (BT) e i punti di contatto di attribuzione dell&#39;acquirente (BAT)](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md) articolo.

**Punti di contatto dell&#39;acquirente (BT)**: questi sono i punti di contatto associati a una singola persona e al suo percorso e saranno specifici per tale persona. I seguenti rapporti predefiniti sono costituiti dai dati dei punti di contatto dell’acquirente.

* [!DNL Marketo Measure] 101: Lead per ID
* [!DNL Marketo Measure] 101: Lead per canale
* [!DNL Marketo Measure] 101: ID lead/contatto
* [!DNL Marketo Measure] 101: Lead/Contatto Per Canale

Di seguito vengono descritte le posizioni dei punti di contatto dell&#39;acquirente che descrivono dove si trova un individuo nel suo percorso e quali azioni ha intrapreso per guadagnare tale posizione.

<table> 
 <tbody>
  <tr>
   <th>Posizione punto di contatto acquirente (BT)</th> 
   <th>Tipo di punto di contatto (azione che può attivare il punto di contatto)</th> 
   <th>Descrizione del punto di contatto</th> 
  </tr>
  <tr>
   <td>Primo contatto (FT)</td> 
   <td>Visita web</td> 
   <td>La prima interazione di marketing che un individuo ha con il tuo marchio</td> 
  </tr>
  <tr>
   <td>Creazione di lead (LC)</td> 
   <td>Compilazione modulo <strong>OPPURE</strong> Inclusione di campagne/programmi</td> 
   <td>Il primo modulo compilato da un individuo ha (in genere l’invio di un modulo, ma potrebbe anche essere un’inclusione di Campagna/Programma)</td> 
  </tr>
  <tr>
   <td>Pubblica LC</td> 
   <td>Compilazione modulo <strong>OPPURE</strong> Inclusione di campagne/programmi</td> 
   <td>Qualsiasi modulo completato da un individuo dopo la sua LC (o una successiva inclusione di Campagna/Programma)</td> 
  </tr>
 </tbody>
</table>

**Punti di contatto per l&#39;attribuzione dell&#39;acquirente (BATS)**: questi sono i punti di contatto associati a un’opportunità e al relativo percorso. Questi punti di contatto saranno collegati ai ricavi in quanto sono collegati all’opportunità e ai relativi contatti. I seguenti rapporti predefiniti sono costituiti dai dati dei punti di contatto di attribuzione buyer.

* [!DNL Marketo Measure] 101: Opportunità per ID
* [!DNL Marketo Measure] 101: Opportunità per canale ID

<table> 
 <tbody>
  <tr>
   <th>Posizione punto di contatto di attribuzione acquirente (BAT)</th> 
   <th>Tipo di punto di contatto (azione che può attivare il punto di contatto)</th> 
   <th>Descrizione del punto di contatto</th> 
  </tr>
  <tr>
   <td>Primo contatto (FT)</td> 
   <td>Visita web</td> 
   <td>La prima interazione di marketing che un contatto ha avuto con il tuo marchio</td> 
  </tr>
  <tr>
   <td>Creazione di lead (LC)</td> 
   <td>Compilazione modulo <strong>OPPURE</strong> Inclusione di campagne/programmi</td> 
   <td>Il primo modulo compilato da un contatto (in genere l’invio di un modulo, ma potrebbe anche includere una campagna o un programma)</td> 
  </tr>
  <tr>
   <td>Creazione di opportunità</td> 
   <td>Compilazione modulo <strong>OPPURE</strong> Visita web <strong>OPPURE</strong> Inclusione di campagne/programmi</td> 
   <td>L’interazione di marketing più simile a quando viene creata l’Opp</td> 
  </tr> 
  <tr>
   <td>Vinto/Perso chiuso</td> 
   <td>Compilazione modulo <strong>OPPURE</strong> Visita web <strong>OPPURE</strong> Inclusione di campagne/programmi</td> 
   <td>L’interazione di marketing più vicina a quando l’Opp viene chiusa (vinta o persa)</td> 
  </tr>
  <tr>
   <td>Contatti intermedi</td> 
   <td>Compilazione modulo <strong>OPPURE</strong> Inclusione di campagne/programmi</td> 
   <td>Quando un contatto compila un modulo online e questo non coincide con il punto di contatto milestone</td> 
  </tr>
 </tbody>
</table>

[!DNL Marketo Measure] dispone di questi due set di dati dei punti di contatto per acquisire una chiara comprensione del percorso di una singola persona e delle opportunità. Questi due set di dati punto di contatto forniscono una chiara mappa di ciò che è successo dall’alto del funnel al fondo del funnel.

L’esempio seguente mostra il flusso di dati dai punti di contatto dell’acquirente (BT) ai punti di contatto di attribuzione dell’acquirente (BAT). In questo esempio, la persona A e la persona B fanno entrambe parte della stessa opportunità con data di creazione 3/7/2020 e data di chiusura 5/6/2020.

**Persona A** Set di dati dei punti di contatto dell&#39;acquirente

* Primo contatto (FT) - Ricerca a pagamento.AdWords - 9/1/2019
* Creazione di lead (LC) - Ricerca organica.Google - 11/20/2019
* Post LC (compilazione modulo) - Webinar - 3/4/2020

**Persona B** Set di dati dei punti di contatto dell&#39;acquirente

* Primo contatto (FT) - Social a pagamento.Facebook - 8/26/2019
* Creazione di lead (LC) - Ricerca organica.Yahoo - 2/20/2020
* Pubblica LC (compilazione modulo) - E-mail - 5/1/2020

**Opportunità** I dati dei punti di contatto di attribuzione dell&#39;acquirente vengono letti come segue...

* Primo contatto (FT) - Social a pagamento.Facebook - 8/26/2019
   * (da **Persona B** perché hanno il vero _Primo contatto_ per Account/Opp)
* Creazione di lead (LC) - Ricerca organica.Google - 11/20/2019
   * (da **Persona A** perché hanno il vero _Creazione di lead_ per Account/Opp)
* Creazione di opportunità (OC) - Webinar - 3/4/2020
   * (punto di contatto Post LC da **Persona A** sarebbe il _Punto di contatto OC_ perché è stata l’interazione più recente che abbiamo per l’opportunità creata il 3/7/2020)
* Vinto chiuso - E-mail - 5/1/2020
   * (punto di contatto Post LC da **Persona B** sarebbe il _Punto di contatto vinto chiuso_ perché è stata l’interazione più recente che abbiamo per l’opportunità di essere chiuso il 5/6/2020)
