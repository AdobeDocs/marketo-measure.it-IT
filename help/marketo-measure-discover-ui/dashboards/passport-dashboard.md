---
description: Dashboard Passport - [!DNL Marketo Measure] - Prodotto
title: Dashboard Passport
feature: Reporting
source-git-commit: dc4dd001d319f13ebd1c4ce418acf2faa27cfe81
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 3%

---

# Dashboard Passport {#passport-dashboard}

Il dashboard Passport offre agli addetti al marketing una visualizzazione dinamica di lead, contatti e opportunità durante la transizione attraverso varie fasi entro un periodo specificato. Filtrando per una data specifica, gli utenti possono ottenere anche un’istantanea dei record per quel giorno.

Risponde alle domande della bacheca:

* Quanti lead, contatti o opportunità esistevano in ogni fase non terminale in un giorno scelto?
* Durante un periodo specificato, quanti lead o contatti distinti sono progrediti in ogni fase transitoria?
   * _Esempio_: se il piombo A fosse nella fase 1 il 1/1/2023 e fosse avanzato alla fase 5 entro il 3/31/2023, l’analisi Passport Q1 2023 conterà il piombo A nelle fasi da 1 a 5.
* Quante opportunità univoche sono passate attraverso ogni fase transitoria durante un determinato intervallo di tempo?

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
    <td>Opportunità</td>
    <td><li>Ogni fase mostra il numero di opportunità con BAT che sono passate attraverso di esse in un determinato arco temporale.</li>
<ul style="padding-left: 30px;"><li>Se un’opportunità progredisce attraverso più fasi all’interno dell’intervallo, vengono conteggiate in ogni fase passata.</li></ul>
<li>Sono escluse le fasi terminali come "Closed Won" e "Closed Lost".</li>
<li>Le date di inizio e di fine sono entrambe inclusive.</li>
<br/><img src="assets/passport-dashboard-1.png" width="600"></td>
    <td rowspan="2">Data di transizione</td>
    <td></td>
    <td rowspan="2"><li>Data</li>
<li>Canale</li>
<li>Sottocanale</li>
<li>Campagna</li>
<li>Segmenti</li></td>
  </tr>
  <tr>
    <td>Lead/Contatti</td>
    <td><li>Ogni fase mostra il numero di lead o contatti con BT che sono passati attraverso di essi in un determinato arco temporale.</li>
<ul style="padding-left: 30px;"><li>La visualizzazione di "Lead" o "Contatto" è determinata dalla preferenza impostata in: Impostazioni &gt; Impostazioni attribuzione &gt; Oggetto dashboard predefinito.</li></ul>
<li>Sono escluse le fasi terminali come "Closed Won" e "Closed Lost".</li>
<li>Le date di inizio e di fine sono entrambe inclusive.</li>
<br/><img src="assets/passport-dashboard-2.png" width="600"></td>
    <td><li>ID lead/contatto</li>
<li>E-mail lead/contatto</li>
<li>Data di creazione</li>
<li>Fase corrente</li>
<li>Transizione in data</li>
<li>Data di uscita transizione</li></td>
  </tr>
</tbody>
</table>
