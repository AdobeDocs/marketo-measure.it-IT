---
description: Dashboard ROI - [!DNL Marketo Measure] - Prodotto
title: Dashboard ROI
hide: true
hidefromtoc: true
feature: Reporting
source-git-commit: c6d9471ece2d249b68bcbfa259c328a6ab5e6192
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 4%

---

# Dashboard ROI {#roi-dashboard}

La dashboard ROI offre agli addetti al marketing una visualizzazione granulare del ritorno sull’investimento per canali, sottocanali e campagne. Suddivide meticolosamente i modelli di costi e ricavi, evidenziando al contempo metriche quali costo per lead, offerta e opportunità, garantendo una comprensione completa dell’attribuzione marketing.

Risponde alle domande della bacheca:

* Quali erano i valori del ROI per ogni canale, sottocanale e campagna?
* In che modo i costi e i ricavi sono stati distribuiti su ciascun canale, sottocanale e campagna?
* Qual è stato il costo per lead, costo per opportunità e costo per opportunità?

<table style="table-layout:auto"> 
<tbody>
 <tr> 
   <th>Componente</th> 
   <th>Descrizione</th>
   <th>Tipo di data</th>
   <th>Campi drill-through</th>
   <th>Filtri</th>
  </tr>
  <tr>
    <td>Sezione costo</td>
    <td>Costo totale sostenuto</td>
    <td>Data costo sostenuto</td>
    <td><li>ID campagna</li>
<li>Nome campagna</li>
<li>Canale</li>
<li>Sottocanale</li>
<li>Data</li>
<li>Spesa</li></td>
    <td rowspan="15"><li>Data</li>
<li>Modello di attribuzione (impostazione)</li>
<li>Canale</li>
<li>Sottocanale</li>
<li>Campagna</li></td>
  </tr>
  <tr>
    <td>Sezione ricavi attribuiti</td>
    <td>Ricavi attribuiti totali</td>
    <td>Data di chiusura</td>
    <td><li>ID opportunità</li>
<li>Nome dell’opportunità</li>
<li>Data di creazione dell’opportunità</li>
<li>Data di chiusura dell’opportunità</li>
<li>È chiuso (S/N)</li>
<li>Vinto (S/N)</li>
<li>Modello di attribuzione</li>
<li>Reddito Attribuito</li>
<li>Reddito Realizzato</li></td>
  </tr>
  <tr>
    <td>Sezione ROI semplice</td>
    <td>ROI legacy: ricavi divisi per costi in un determinato arco temporale. 
    <li>Costo: costo sostenuto nel periodo di date filtrate.</li>
    <li>Ricavi: i ricavi derivanti da opportunità "Closed Won" in tale arco temporale.</li></td>
    <td>Data di chiusura</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>Sezione ROI realizzata</td>
    <td>ROI realizzato: rappresenta i risultati tangibili dei punti di contatto generati dalle campagne entro un intervallo di tempo specificato.
    <li>Costo: costo sostenuto nel periodo di date filtrate.</li>
    <li>Ricavi: ricavi realizzati da tutte le offerte "Closed Won", in particolare quelle influenzate dai punti di contatto entro il periodo di tempo indicato.</li>
    <br/><img src="assets/roi-dashboard-1.png" width="600"></td>
    <td>Data costo sostenuto</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>Sezione Totale nuovi lead</td>
    <td>Numero totale di nuovi lead (conteggio intero) generati in un periodo specificato, inclusi i lead sia toccati che non toccati.</td>
    <td>Data di creazione</td>
    <td rowspan="2">
    <li>ID lead</li>
    <li>E-mail Lead</li>
    <li>Data LC</li></td>
  </tr>
  <tr>
    <td>Costo per nuova sezione lead</td>
    <td>Numero totale di nuovi lead (conteggio intero) diviso per i costi.</td>
    <td>Data di creazione</td>
  </tr>
  <tr>
    <td>Sezione Totale nuove opportunità</td>
    <td>Numero totale di nuove opportunità (conteggio intero) generate in un periodo specificato, inclusi i lead sia toccati che non toccati.</td>
    <td>Data di creazione</td>
    <td rowspan="2">
    <li>ID opportunità</li>
    <li>Nome dell’opportunità</li>
    <li>Data di creazione dell’opportunità</li>
    <li>Data di chiusura dell’opportunità</li>
    <li>È chiuso (S/N)</li>
    <li>Vinto (S/N)</li>
    <li>Fase corrente</li></td>
  </tr>
  <tr>
    <td>Sezione Costo per nuova opportunità</td>
    <td>Numero totale di nuove opportunità (conteggio intero) diviso per i costi.</td>
    <td>Data di creazione</td>
  </tr>
  <tr>
    <td>Sezione Offerte totali</td>
    <td>Numero totale di offerte chiuse in un periodo specificato, incluse quelle senza punti di contatto associati.</td>
    <td>Data di chiusura</td>
    <td><li>ID opportunità</li>
<li>Nome dell’opportunità</li>
<li>Data di creazione dell’opportunità</li>
<li>Data di chiusura dell’opportunità</li>
<li>È chiuso (S/N)</li>
<li>Vinto (S/N)</li>
<li>Fase corrente</li>
<li>Valuta</li>
<li>Modello di attribuzione</li>
<li>Reddito Attribuito</li>
<li>Reddito Realizzato</li></td>
  </tr>
  <tr>
    <td>Grafico Costi e ricavi per canale</td>
    <td>Grafico a barre che illustra sia i costi che i ricavi, progettato per offrire una prospettiva comparativa sulla loro grandezza rispetto a vari canali, sottocanali e campagne.
    <br/><img src="assets/roi-dashboard-2.png" width="600"></td>
    <td>Data di chiusura</td>
    <td>Costo:
<br/>
<li>ID campagna</li>
<li>Nome campagna</li>
<li>Canale</li>
<li>Sottocanale</li>
<li>Data costo sostenuto</li>
<li>Valuta</li>
<li>Spesa</li>
<p>
Ricavi:
<br/>
<li>ID opportunità</li>
<li>Nome dell’opportunità</li>
<li>Data di creazione dell’opportunità</li>
<li>Data di chiusura dell’opportunità</li>
<li>È chiuso (S/N)</li>
<li>Vinto (S/N)</li>
<li>Reddito Attribuito</li>
<li>Modello di attribuzione</li>
<li>Reddito Attribuito</li>
<li>Reddito Realizzato</li></td>
  </tr>
  <tr>
    <td>ROI realizzato e semplice nel tempo</td>
    <td>Grafico a linee delle serie temporali che mostra il confronto tra ROI realizzato e ROI semplice, tracciandone la progressione nel tempo.
    <br/><img src="assets/roi-dashboard-3.png" width="600"></td>
    <td>ROI semplice: data costo sostenuto e data chiusura
    <p>ROI realizzato: data costo sostenuto e data punto di contatto</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>Grafico Costo nel tempo</td>
    <td>Grafico a barre in pila che mostra i costi totali trimestrali/mensili, suddivisi per singoli canali per una suddivisione dettagliata.
    <br/><img src="assets/roi-dashboard-4.png" width="600"></td>
    <td>Data costo sostenuto</td>
    <td rowspan="2"><li>ID campagna</li>
<li>Nome campagna</li>
<li>Canale</li>
<li>Sottocanale</li>
<li>Data costo sostenuto</li>
<li>Valuta</li>
<li>Spesa</li></td>
  </tr>
  <tr>
    <td>Grafico Costo per canale</td>
    <td>Grafico a barre che mostra le spese di marketing segmentate per canali.
    <br/><img src="assets/roi-dashboard-5.png" width="600"></td>
    <td>Data costo sostenuto</td>
  </tr>
  <tr>
    <td>Tabella di riepilogo del ROI</td>
    <td>Tabella con ricavi attribuiti, costi e ROI segmentati per singolo canale per una suddivisione dettagliata.
<p>
<b>Colonne:</b>
<p>
<li>Canale/Sottocanale/Campagna</li>
<li>Costo</li>
<li>Reddito Attribuito</li>
<li>ROI semplice</li>
<li>ROI realizzato</li>
<li>Pipeline non realizzata</li>
<ul style="padding-left: 30px;"><li>Pipeline dai punti di contatto (Opportunità aperte) associati alle campagne in un determinato arco temporale</li></ul></td>
    <td>ROI semplice: data costo sostenuto e data chiusura
    <p>ROI realizzato: data costo sostenuto e data punto di contatto</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>Tabella delle spese di marketing</td>
    <td>Tabella con costi, nuovi lead, opportunità e offerte chiusi segmentati per singolo canale per un raggruppamento dettagliato.
<p>
<b>Colonne:</b>
<p>
<li>Canale/Sottocanale/Campagna</li>
<li>Costo</li>
<li>Nuovi lead</li>
<li>Costo per nuovo lead</li>
<li>Nuove opportunità</li>
<li>Costo per nuova opportunità</li>
<li>Offerte chiuse</li>
<li>Costo per transazione chiuso</li></td>
    <td><li>Costo: data costo sostenuto</li>
<li>Nuovi lead: data di creazione</li>
<li>Nuove opportunità: data di creazione</li>
<li>Offerte chiuse: data di chiusura</li></td>
    <td>N/D</td>
  </tr>
</tbody>
</table>

>[!MORELIKETHIS]
>
>[Scopri nozioni di base sulla dashboard](/help/marketo-measure-discover-ui/dashboards/discover-dashboard-basics.md){target="_blank"}
