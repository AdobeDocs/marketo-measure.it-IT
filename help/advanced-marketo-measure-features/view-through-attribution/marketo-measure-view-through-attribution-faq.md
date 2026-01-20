---
unique-page-id: 18874652
description: '[!DNL Marketo Measure] Domande frequenti sulla visualizzazione tramite attribuzione - [!DNL Marketo Measure]'
title: Domande frequenti sulla visualizzazione di [!DNL Marketo Measure] tramite attribuzione
exl-id: d20e88f3-3ff8-4381-a4b8-6862798caa74
feature: Attribution
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 3%

---

# Domande frequenti sulla visualizzazione di [!DNL Marketo Measure] tramite attribuzione {#marketo-measure-view-through-attribution-faq}

## Cos’è la visualizzazione tramite attribuzione? {#what-is-view-through-attribution}

La funzionalità [!DNL Marketo Measure] [!UICONTROL View Through Attribution] include la possibilità di includere le impression pubblicitarie nel modello di attribuzione.

>[!IMPORTANT]
>
>A causa di problemi di privacy, i cookie di terze parti sono in uscita. L’annuncio della rimozione dei cookie di terze parti, annunciata nel terzo trimestre 2024 da Google Chrome, segna di fatto la fine di questa forma di tracciamento. Di conseguenza, Adobe rende obsolete le funzioni di Marketo Measure che si basano su cookie di terze parti; in particolare, il tracciamento tra domini diversi e l’attribuzione view-through, che utilizzano il cookie di impression Google/DoubleClick. Nessun’altra funzione di Marketo Measure sarà interessata. Anche l’utilizzo di cookie di prime parti non è interessato. Alla luce della pianificazione di Google, la data prevista di deprecazione per le due funzioni di cui sopra è il 6/1/2024. I dati correlati raccolti prima di questa data rimangono disponibili per i clienti Adobe.

## Perché [!UICONTROL View Through Attribution] è importante? {#why-is-view-through-attribution-important}

Storicamente, il re-targeting o la pubblicità sulle impression era difficile per gli esperti di marketing tenere conto nell’analisi di attribuzione. I potenziali clienti, di volta in volta, possono essere esposti agli annunci di retargeting, ma è improbabile che facciano clic su uno di questi annunci e compilino un modulo all’interno della stessa sessione. La nostra soluzione View Through Attribution consente ora di verificare se qualcuno è stato esposto o meno a un annuncio di impression. Questo punto di contatto verrà aggiunto al record individuale e continuerà fino a quando il potenziale cliente non diventerà un cliente. Con queste informazioni, l’addetto al marketing otterrà ora migliori insight sulle prestazioni della pubblicità di re-targeting.

## Cosa c&#39;entra con questa creazione? {#what-is-involved-in-setting-this-up}

Affinché [!DNL Marketo Measure] possa iniziare a misurare le impression dell&#39;annuncio, è necessario inserire un tag di impression in Doubleclick Campaign Manager. Una volta implementato il tag, le impression vengono memorizzate nei nostri registri e ci occupiamo del resto. Contatta il tuo Success Manager se sei interessato a misurare la visualizzazione tramite l’attribuzione.

## Quali piattaforme di annunci sono supportate? {#which-ad-platforms-are-supported}

Al momento è supportato [!DNL Doubleclick] Campaign Manager.

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

## Come si presenterà in [!DNL Salesforce?] {#what-will-this-look-like-in-salesforce}

[!DNL Marketo Measure] creerà un singolo punto di contatto di impression su qualsiasi lead esposto all&#39;annuncio di visualizzazione. Siamo in grado di mappare l&#39;utente anche dopo che è venuto per la prima volta al tuo sito web (FT) e compilare un modulo (LC). Il punto di contatto conterrà informazioni sugli annunci come Nome/ID campagna pubblicitaria, ID annuncio, Contenuto annuncio, Nome/ID sito, Nome/ID posizionamento, Canale di marketing, Geo, Pagina referente e altro ancora.

Il modello di attribuzione view-through dipenderà dal client e dai relativi dati.
