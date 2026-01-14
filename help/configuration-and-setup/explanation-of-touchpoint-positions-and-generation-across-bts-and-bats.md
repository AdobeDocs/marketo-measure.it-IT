---
description: Spiegazione delle posizioni e della generazione dei punti di contatto tra i BT e  [!DNL BATs]  indicazioni per gli utenti di Marketo Measure
title: Spiegazione delle posizioni dei punti di contatto e della generazione tra BT e  [!DNL BATs]
exl-id: 4903f917-a366-4767-a126-5216d2377399
feature: Touchpoints
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 0%

---


# Spiegazione delle posizioni dei punti di contatto e della generazione tra BT e [!DNL BATs] {#explanation-of-touchpoint-positions-and-generation-across-bts-and-bats}

**Generazione di posizioni dei punti di contatto e flusso attraverso il Percorso di acquirenti**

Comprendere le posizioni di Buyer Touchpoint e come vengono attivate è fondamentale per creare report con i dati di [!DNL Marketo Measure]. Desideri avere una chiara comprensione di ciò che hanno fatto i potenziali clienti quando si sono spostati nel percorso dell’acquirente e, a sua volta, di ciò che apparirà nei dati del punto di contatto. Per ulteriori informazioni su questo argomento, si consiglia di rivedere l&#39;articolo [[!UICONTROL Touchpoint Generation & Mapping]](/help/configuration-and-setup/touchpoint-generation-and-mapping.md).

[!DNL Marketo Measure] dispone di diverse posizioni di punti di contatto attivate da vari passaggi nel percorso dell&#39;acquirente. Quando si generano rapporti sui dati di [!DNL Marketo Measure], sono disponibili due set di dati relativi ai punti di contatto, ovvero i punti di contatto dell&#39;acquirente (BT) e i punti di contatto di attribuzione dell&#39;acquirente (BAT). Potresti notare che questi set di dati hanno posizioni leggermente diverse in quanto si riferiscono a oggetti diversi. Per ulteriori informazioni su questo argomento, si consiglia di rivedere l&#39;articolo [Difference Between Buyer Touchpoints (BTs) &amp; Buyer Attribution Touchpoints (BATs)](/help/configuration-and-setup/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md).

**Punti di contatto dell&#39;acquirente (BT)**: si tratta dei punti di contatto associati a una singola persona e al relativo percorso e saranno univoci per tale persona. I seguenti rapporti predefiniti sono costituiti da dati di Buyer Touchpoint.

* [!DNL Marketo Measure] 101: lead per ID
* [!DNL Marketo Measure] 101: Lead per canale
* [!DNL Marketo Measure] 101: ID lead/contatto
* [!DNL Marketo Measure] 101: lead/contatto per canale

Di seguito vengono illustrate le posizioni di Buyer Touchpoint che descrivono dove si trova un individuo nel suo percorso e quali azioni ha intrapreso per guadagnarsi quella posizione.

<table>
 <tbody>
  <tr>
   <th>Posizione Buyer Touchpoint (BTs)</th>
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
   <td>Compilazione modulo <strong>OR</strong> Inclusione campagna/programma</td>
   <td>Il primo modulo riempie una singola pagina (in genere l’invio di un modulo, ma potrebbe anche essere un’inclusione di campagna/programma)</td>
  </tr>
  <tr>
   <td>Pubblica LC</td>
   <td>Compilazione modulo <strong>OR</strong> Inclusione campagna/programma</td>
   <td>Qualsiasi modulo completato da un individuo dopo la sua LC (o una successiva inclusione di Campagna/Programma)</td>
  </tr>
 </tbody>
</table>

**Punti di contatto per l&#39;attribuzione dell&#39;acquirente (BATS)**: si tratta dei punti di contatto associati a un&#39;opportunità e al relativo percorso. Questi punti di contatto sono collegati ai ricavi in quanto sono collegati all’opportunità e ai relativi contatti. I seguenti rapporti predefiniti sono costituiti da dati di Buyer Attribution Touchpoint.

* [!DNL Marketo Measure] 101: Opportunità per ID
* [!DNL Marketo Measure] 101: Opportunità per canale ID

<table>
 <tbody>
  <tr>
   <th>Posizione Buyer Attribution Touchpoint (BAT)</th>
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
   <td>Compilazione modulo <strong>OR</strong> Inclusione campagna/programma</td>
   <td>Il primo modulo compilava un contatto (in genere era un invio di modulo, ma poteva anche essere un’inclusione di campagna/programma)</td>
  </tr>
  <tr>
   <td>Creazione di opportunità</td>
   <td>Compilazione modulo <strong>OR</strong> Visita Web <strong>OR</strong> Inclusione campagna/programma</td>
   <td>L’interazione di marketing più simile a quando viene creata l’Opp</td>
  </tr>
  <tr>
   <td>Vinto/Perso chiuso</td>
   <td>Compilazione modulo <strong>OR</strong> Visita Web <strong>OR</strong> Inclusione campagna/programma</td>
   <td>L’interazione di marketing più vicina a quando l’Opp viene chiusa (vinta o persa)</td>
  </tr>
  <tr>
   <td>Contatti intermedi</td>
   <td>Compilazione modulo <strong>OR</strong> Inclusione campagna/programma</td>
   <td>Quando un contatto compila un modulo online e questo non coincide con il punto di contatto milestone</td>
  </tr>
 </tbody>
</table>

[!DNL Marketo Measure] dispone di questi due insiemi di dati dei punti di contatto per comprendere chiaramente il percorso di una persona e le opportunità. Questi due set di dati relativi ai punti di contatto forniscono una chiara mappa di ciò che è successo dall’alto di funnel al basso di funnel.

L’esempio seguente mostra il flusso di dati dai punti di contatto dell’acquirente (BT) ai punti di contatto di attribuzione dell’acquirente (BAT). In questo esempio, la persona A e la persona B fanno entrambe parte della stessa opportunità con data di creazione 3/7/2020 e data di chiusura 5/6/2020.

**Persona A** Set di dati Buyer Touchpoint

* Primo contatto (FT) - Ricerca a pagamento.AdWords - 9/1/2019
* Creazione di lead (LC) - Ricerca organica.Google - 11/20/2019
* Post LC (compilazione modulo) - Webinar - 3/4/2020

**Persona B** Set di dati Buyer Touchpoint

* Primo contatto (FT) - Social a pagamento.Facebook - 8/26/2019
* Creazione di lead (LC) - Ricerca organica.Yahoo - 2/20/2020
* Pubblica LC (compilazione modulo) - E-mail - 5/1/2020

**Opportunità** I dati di Buyer Attribution Touchpoint verrebbero letti come segue...

* Primo contatto (FT) - Social a pagamento.Facebook - 8/26/2019
   * (da **Persona B** perché hanno il _Primo contatto_ vero per l&#39;account/Opp)
* Creazione di lead (LC) - Ricerca organica.Google - 11/20/2019
   * (da **Persona A** perché hanno la vera _Creazione lead_ per l&#39;account/Opp)
* Creazione di opportunità (OC) - Webinar - 3/4/2020
   * Il punto di contatto LC post da **Persona A** sarebbe il punto di contatto _OC_ perché è stata l&#39;interazione più recente che abbiamo per l&#39;opportunità creata il 3/7/2020
* Vinto chiuso - E-mail - 5/1/2020
   * Il punto di contatto PostLC della **persona B** sarebbe il _punto di contatto Chiuso con Won_, in quanto si tratta dell&#39;interazione più recente di cui disponiamo per la chiusura dell&#39;opportunità il 5/6/2020
