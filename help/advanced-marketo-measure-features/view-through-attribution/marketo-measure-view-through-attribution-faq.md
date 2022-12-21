---
unique-page-id: 18874652
description: "[!DNL Marketo Measure] Domande frequenti su Attribution View Through - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] Domande frequenti su View Through Attribution"
exl-id: d20e88f3-3ff8-4381-a4b8-6862798caa74
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 9%

---

# [!DNL Marketo Measure] Domande frequenti su View Through Attribution {#marketo-measure-view-through-attribution-faq}

## Cos’è View Through Attribution? {#what-is-view-through-attribution}

La [!DNL Marketo Measure] La funzione Visualizza tramite attribuzione consente di includere impressioni di annunci nel modello di attribuzione.

## Perché la visualizzazione tramite attribuzione è importante? {#why-is-view-through-attribution-important}

Storicamente, nell’analisi dell’attribuzione, è stato difficile per gli addetti al marketing rendere conto del nuovo targeting o della pubblicità sulle impression. I potenziali clienti possono, di tanto in tanto, essere esposti a nuovi annunci di targeting, ma è improbabile che facciano effettivamente clic su uno di questi annunci e compilino un modulo all&#39;interno della stessa sessione. La nostra soluzione View Through Attribution ora è in grado di tracciare se qualcuno è stato esposto o meno a un annuncio di impression. Questo punto di contatto verrà aggiunto al singolo record e continuerà fino a quando il potenziale cliente non diventerà un cliente. Con queste informazioni, l’addetto al marketing ora avrà maggiori informazioni sulle prestazioni della pubblicità di retargeting.

## Che cosa è coinvolto nella creazione di questo sistema? {#what-is-involved-in-setting-this-up}

Per [!DNL Marketo Measure] per iniziare a misurare le impression dell’annuncio, è necessario inserire un tag di impression in Doubleclick Campaign Manager. Una volta implementato il tag, le impression vengono memorizzate nei nostri registri e ci occupiamo del resto. Contatta il tuo Success Manager se sei interessato a misurare la visualizzazione tramite l’attribuzione.

## Quali piattaforme di annunci sono supportate? {#which-ad-platforms-are-supported}

Al momento supportiamo Doubleclick Campaign Manager.

## Come viene calcolata l’attribuzione? {#how-is-the-attribution-calculated}

Abbiamo analizzato attentamente i dati sulle impression e la loro influenza sulle conversioni in tutte le fasi e i canali di marketing. La distribuzione varia a seconda del modello, come illustrato nella tabella seguente:

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
   <td><strong>Impressioni</strong></td> 
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
   <td>26.6%</td> 
   <td>20%</td> 
   <td>Personalizzato</td> 
  </tr> 
  <tr> 
   <td><strong>LC</strong></td> 
   <td>0%</td> 
   <td>100%</td> 
   <td>35%</td> 
   <td>26.6%</td> 
   <td>20%</td> 
   <td>Personalizzato</td> 
  </tr> 
  <tr> 
   <td><strong>OC</strong></td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>26.6%</td> 
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
   <td><strong>Medio</strong></td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>20%</td> 
   <td>10%</td> 
   <td>10%</td> 
   <td>Personalizzato</td> 
  </tr> 
 </tbody> 
</table>

## Che aspetto avrà in Salesforce? {#what-will-this-look-like-in-salesforce}

[!DNL Marketo Measure] crea un singolo punto di contatto di impression su qualsiasi lead esposto all’annuncio di visualizzazione. Siamo in grado di mappare l&#39;utente anche dopo che sono arrivati al tuo sito web (FT) e compilare un modulo (LC). Il punto di contatto conterrà informazioni sugli annunci quali Nome/ID campagna pubblicitaria, ID annuncio, contenuto annuncio, nome/ID sito, nome/ID posizionamento, canale di marketing, Geo, pagina referente e altro ancora.

Il modello di attribuzione view-through dipenderà dal client e dai relativi dati.
