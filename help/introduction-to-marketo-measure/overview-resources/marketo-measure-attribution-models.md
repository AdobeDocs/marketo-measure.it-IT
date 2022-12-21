---
unique-page-id: 18874568
description: Modelli di attribuzione delle misure Marketo - Misura Marketo - Documentazione del prodotto
title: Modelli di attribuzione delle misure Marketo
exl-id: d8f76f29-e7c9-4b2d-b599-e80fd93c4687
source-git-commit: 0aa263053aa8dd804b03a67ab446dc0cda3850c5
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# Modelli di attribuzione delle misure Marketo {#marketo-measure-attribution-models}

Marketo Measure offre sei tipi di modelli di attribuzione:

* Primo contatto
* Creazione di lead
* A forma di U
* A forma di W
* Percorso completo
* Modello personalizzato

Questi modelli variano a seconda della complessità. Creazione di primo contatto e lead sono i nostri modelli semplici a sfioramento singolo. Gli altri quattro sono i nostri modelli multi-touch più complessi. La struttura dei modelli di attribuzione di Marketo Measure riflette i quattro principali punti di contatto che si verificano nel percorso di clienti:

* Primo contatto (FT)
* Creazione di lead (LC)
* Creazione di opportunità (OC)
* Offerta chiusa (CW)

![](assets/1-1.png)

In **modelli single-touch**, il credito di attribuzione è attribuito a un solo punto di contatto cardine, da cui il nome &quot;single-touch&quot;.
In **modelli multi-touch**, la maggior parte del credito di attribuzione viene assegnata a due o più punti di contatto cardine. Il credito rimanente è attribuito ai punti di contatto che si verificano tra i punti di contatto delle attività cardine.

Nelle prossime sezioni vengono descritti ogni modello di attribuzione e il modo in cui viene assegnato il credito di attribuzione.

## Modelli a sfioramento singolo {#single-touch-models}

**Modello primo contatto**

Il modello Primo contatto si concentra solo sulla prima interazione che un lead ha con la tua organizzazione. Questo modello attribuisce il 100% del credito di attribuzione alla prima volta che il lead viene a conoscenza dell’azienda, il primo contatto (FT).

Di&#39; che Kate visita www.adobe.com per la prima volta tramite un annuncio pubblicitario Adwords e visualizza un white paper. Il canale Adwords riceverebbe il 100% del credito di attribuzione da tale opportunità.

![](assets/2.png)

**Modello di creazione di lead**

Il modello Creazione di lead attribuisce il 100% del credito di attribuzione al punto di contatto LC, quando un potenziale cliente fornisce le proprie informazioni di contatto e diventa un lead.

Proseguendo dall&#39;esempio precedente, dopo la prima visita di Kate a www.adobe.com via Adwords, Austin visita il sito web tramite un post su Linkedin. Austin compila un modulo e diventa Lead. In questo modello, Linkedin riceverebbe il 100% del credito di attribuzione.

![](assets/3.png)

## Modelli multi-touch {#multi-touch-models}

I modelli multi-touch vengono utilizzati per cicli di vendita più lunghi e complessi. Questi modelli sono particolarmente utili se nel percorso dell’acquirente sono coinvolte più persone di un account/società.

**Modello a forma di U**

Il modello a forma di U si concentra sia sui punti di contatto FT che LC. In questo modello, i punti di contatto FT e LC ricevono ciascuno il 50% del credito sul ricavo.

La prima visita di Kate a www.adobe.com tramite un annuncio Adwords riceverebbe il 50% del credito di attribuzione. Il restante 50% sarebbe attribuito al post di Linkedin che ha spinto Austin a compilare un modulo e diventare un lead.

![](assets/4.png)

**Modello a forma di W**

Tre dei punti di contatto cardine sono inclusi nel modello a forma di W. In questo modello, ai punti di contatto FT, LC e OC viene attribuito il 30% del credito di attribuzione. Il restante 10% è attribuito in modo proporzionale a qualsiasi punto di contatto intermedio che si verifica tra i tre punti di contatto cardine.

Kate e Austin citano Marketo Measure al loro collega, Hillary. Trova un contenuto tramite una ricerca su Google e compila un modulo. In seguito, Austin riceve un&#39;e-mail per una registrazione del webinar e compila il modulo di registrazione sul sito web. Kate ha una conversazione con un rappresentante commerciale sul prodotto Marketo Measure.

Hillary riceve un&#39;e-mail con un collegamento alla pagina dei prezzi e visita la pagina. Quindi viene creata un&#39;opportunità per il loro account. La visita web di Hillary alla pagina dei prezzi riceve credito per la creazione delle opportunità, perché è stata l&#39;interazione di marketing più vicina alla data di creazione delle opportunità. A ciascun punto di contatto cardine viene assegnato il 30% del credito di attribuzione, mentre ai punti di contatto intermedi viene attribuito il restante 10%.

![](assets/5.png)

**Modello a percorso completo**

Il modello di percorso completo include tutti e quattro i punti di contatto cardine. FT, LC, OC e CW ricevono ciascuno il 22,5% del credito sul ricavo e il restante 10% è distribuito equamente tra i contatti intermedi.

Dopo la creazione di opportunità, Kate, Austin e Hillary decidono di piazzare Marketo Measure alla loro CMO, Elizabeth. Elizabeth partecipa a una conferenza in cui Marketo Measure ospita un evento. Kate vede un post di Linkedin su un caso di studio e compila un modulo per scaricare il contenuto. Elizabeth partecipa a una cena di vendita ospitata da Marketo Measure. Dopo la cena decide di acquistare Marketo Measure e diventa cliente. In questo scenario, alla cena di vendita verrebbe attribuito il 22,5% del credito di ricavo dall&#39;operazione chiusa. Anche i punti di contatto FT, LC e OC ricevono il 22,5% del credito. Ai punti di contatto intermedi viene assegnato anche il restante 10% del credito sul reddito.

![](assets/6.png)

**Modello di attribuzione personalizzato**

Marketo Measure offre anche un modello di attribuzione personalizzato che consente agli utenti di scegliere quali punti di contatto o stadi personalizzati includere nel proprio modello. Inoltre, gli utenti possono controllare la percentuale di credito di attribuzione attribuita a questi punti di contatto e fasi.
