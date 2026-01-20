---
unique-page-id: 18874590
description: '[!DNL Marketo Measure] cookie - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] cookie'
exl-id: de6e35ae-af92-43ba-8416-3e07d3dd470c
feature: Tracking
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 10%

---

# Cookie di Marketo Measure {#marketo-measure-cookies}

Scopri i vari cookie [!DNL Marketo Measure] caricati sul tuo sito quando applichi il JavaScript [!DNL Marketo Measure] alle pagine di destinazione. Queste informazioni possono essere utili al team di sviluppo web durante l’implementazione.

>[!IMPORTANT]
>
>A causa di problemi di privacy, i cookie di terze parti sono in uscita. L’annuncio della rimozione dei cookie di terze parti, annunciata nel terzo trimestre 2024 da Google Chrome, segna di fatto la fine di questa forma di tracciamento. Di conseguenza, Adobe rende obsolete le funzioni di Marketo Measure che si basano su cookie di terze parti; in particolare, il tracciamento tra domini diversi e l’attribuzione view-through, che utilizzano il cookie di impression Google/DoubleClick. Nessun’altra funzione di Marketo Measure sarà interessata. Anche l’utilizzo di cookie di prime parti non è interessato. Alla luce della pianificazione di Google, la data prevista di deprecazione per le due funzioni di cui sopra è il 6/1/2024. I dati correlati raccolti prima di questa data rimangono disponibili per i clienti Adobe.

<table>
<thead>
  <tr>
    <th>Nome cookie</th>
    <th>Tipo di cookie</th>
    <th>Finalità</th>
    <th>Scadenza</th>
    <th>Il flag Secure è impostato?<br></th>
    <th>Il flag Solo HTTP è impostato?</th>
    <th>Impostazione cookie</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>_biz_uid</td>
    <td>Prima parte</td>
    <td>Identifica in modo univoco un utente nel dominio corrente.</td>
    <td>1 anno</td>
    <td>No</td>
    <td>No</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_nA</td>
    <td>Prima parte</td>
    <td>Un numero di sequenza che Marketo Measure include per tutte le richieste a scopo di diagnostica interna.</td>
    <td>1 anno</td>
    <td>No</td>
    <td>No</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_flagsA</td>
    <td>Prima parte</td>
    <td>Un cookie che memorizza varie informazioni utente, come l’invio di moduli, la migrazione tra domini diversi, il pixel view-through, lo stato di rinuncia al tracciamento e così via.</td>
    <td>1 anno</td>
    <td>No</td>
    <td>No</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_pendingA</td>
    <td>Prima parte</td>
    <td>Memorizza temporaneamente i dati di analisi fino a quando non vengono inviati correttamente al server Marketo Measure.</td>
    <td>1 anno</td>
    <td>No</td>
    <td>No</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_ABTestA</td>
    <td>Prima parte</td>
    <td>Elenco di checksum da Optimize e Visual Web Optimizer ABTest dati che sono già stati segnalati, impedendo a bizible.js di inviare nuovamente i dati raccolti.</td>
    <td>1 anno</td>
    <td>No</td>
    <td>No</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_EventA</td>
    <td>Prima parte</td>
    <td>Elenco di checksum segnalati da Bizible Events per impedire a bizible.js di inviare nuovamente i dati raccolti.</td>
    <td>1 anno</td>
    <td>No</td>
    <td>No</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_su</td>
    <td>Prima parte</td>
    <td>ID utente universale per identificare un utente tra più domini, applicabile solo ai tenant con integrazione che aggira le limitazioni ITP.</td>
    <td>1 anno</td>
    <td>Sì</td>
    <td>No</td>
    <td>Edgecast</td>
  </tr>
  <tr>
    <td>_BUID</td>
    <td>Terza parte, dominio=.<a href="https://business.adobe.com/products/marketo/bizible.html">bizible.com</a></td>
    <td>ID utente universale per identificare un utente tra più domini.</td>
    <td>1 anno</td>
    <td>Sì</td>
    <td>No</td>
    <td>Edgecast</td>
  </tr>
  <tr>
    <td>_BUID</td>
    <td>Terza parte, dominio=.<a href="https://bizibly.com/">bizibly.com</a></td>
    <td>Mappatura tra l’ID cookie di Marketo Measure sul dominio del tenant e il relativo ID cookie di impression a doppio clic.</td>
    <td>1 anno</td>
    <td>Sì</td>
    <td>No</td>
    <td>Edgecast</td>
  </tr>
</tbody>
</table>

Se durante la configurazione di JavaScript viene attivato un avviso di Firewall applicazione Web (WAF), gli utenti possono disabilitare la regola di WAF o inserire nell&#39;elenco Consentiti i cookie, come nell’esempio seguente:

![](assets/marketo-measure-cookies-1.png)
