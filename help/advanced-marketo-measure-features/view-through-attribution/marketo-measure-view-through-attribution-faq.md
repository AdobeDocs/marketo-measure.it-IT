---
unique-page-id: 18874652
description: "[!DNL Marketo Measure] Domande frequenti sull’attribuzione View Through - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Domande frequenti sull’attribuzione Visualizza tramite"
exl-id: d20e88f3-3ff8-4381-a4b8-6862798caa74
feature: Attribution
source-git-commit: 518a984b0d8d640290bd9b637221fcdc0948e5b9
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 1%

---

# [!DNL Marketo Measure] Domande frequenti su View Through Attribution {#marketo-measure-view-through-attribution-faq}

## Cos’è la visualizzazione tramite attribuzione? {#what-is-view-through-attribution}

Il [!DNL Marketo Measure] [!UICONTROL View Through Attribution] Questa funzione include la possibilità di includere le ad impression nel modello di attribuzione.

## Perché è [!UICONTROL View Through Attribution] Importante? {#why-is-view-through-attribution-important}

Storicamente, il re-targeting o la pubblicità sulle impression era difficile per gli esperti di marketing tenere conto nell’analisi di attribuzione. I potenziali clienti, di volta in volta, possono essere esposti agli annunci di retargeting, ma è improbabile che facciano clic su uno di questi annunci e compilino un modulo all’interno della stessa sessione. La nostra soluzione View Through Attribution consente ora di verificare se qualcuno è stato esposto o meno a un annuncio di impression. Questo punto di contatto verrà aggiunto al record individuale e continuerà fino a quando il potenziale cliente non diventerà un cliente. Con queste informazioni, l’addetto al marketing potrà ora ottenere informazioni migliori sulle prestazioni della pubblicità di re-targeting.

## Cosa c&#39;entra con questa creazione? {#what-is-involved-in-setting-this-up}

Per ottenere [!DNL Marketo Measure] per iniziare a misurare le impression dell’annuncio, è necessario inserire un tag impression in Doubleclick Campaign Manager. Una volta implementato il tag, le impression vengono memorizzate nei nostri registri e ci occupiamo del resto. Per misurare la visualizzazione tramite l’attribuzione, rivolgiti al tuo Success Manager.

## Quali piattaforme di annunci sono supportate? {#which-ad-platforms-are-supported}

Al momento supportiamo [!DNL Doubleclick] Gestione campagne.

## Come viene calcolata l’attribuzione? {#how-is-the-attribution-calculated}

Abbiamo eseguito un’attenta analisi dei dati sulle impression e della loro influenza sulle conversioni in tutte le fasi e i canali di marketing. La distribuzione varia a seconda del modello, come illustrato nella tabella seguente:

<table> 
 <colgroup> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th><br></th> 
   <th>Primo contatto</th> 
   <th>Creazione di lead</th> 
   <th>A forma di U</th> 
   <th>A forma di W</th> 
   <th>Percorso completo</th> 
   <th>Modello personalizzato</th> 
  </tr> 
  <tr> 
   <td><strong>Impression</strong></td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>10%</td> 
   <td>10%</td> 
   <td>10%</td> 
   <td>Personalizzato</td> 
  </tr> 
  <tr> 
   <td><strong>FT</strong></td> 
   <td>100%</td> 
   <td>0%</td> 
   <td>35%</td> 
   <td>26,6%</td> 
   <td>20%</td> 
   <td>Personalizzato</td> 
  </tr> 
  <tr> 
   <td><strong>LC</strong></td> 
   <td>0%</td> 
   <td>100%</td> 
   <td>35%</td> 
   <td>26,6%</td> 
   <td>20%</td> 
   <td>Personalizzato</td> 
  </tr> 
  <tr> 
   <td><strong>OC</strong></td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>26,6%</td> 
   <td>20%</td> 
   <td>Personalizzato</td> 
  </tr> 
  <tr> 
   <td><strong>Chiuso</strong></td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>20%</td> 
   <td>Personalizzato</td> 
  </tr> 
  <tr> 
   <td><strong>In mezzo</strong></td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>20%</td> 
   <td>10%</td> 
   <td>10%</td> 
   <td>Personalizzato</td> 
  </tr> 
 </tbody> 
</table>

## Come apparirà questo in [!DNL Salesforce?] {#what-will-this-look-like-in-salesforce}

[!DNL Marketo Measure] creerà un singolo punto di contatto di impression su qualsiasi lead esposto all’annuncio display. Siamo in grado di mappare l&#39;utente anche dopo che è venuto per la prima volta al tuo sito web (FT) e compilare un modulo (LC). Il punto di contatto conterrà informazioni sugli annunci come Nome/ID campagna pubblicitaria, ID annuncio, Contenuto annuncio, Nome/ID sito, Nome/ID posizionamento, Canale di marketing, Geo, Pagina referente e altro ancora.

Il modello di attribuzione view-through dipenderà dal client e dai relativi dati.
