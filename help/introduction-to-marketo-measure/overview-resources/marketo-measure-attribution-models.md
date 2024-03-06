---
unique-page-id: 18874568
description: Modelli di attribuzione Marketo Measure - Marketo Measure - Documentazione del prodotto
title: Modelli di attribuzione Marketo Measure
exl-id: d8f76f29-e7c9-4b2d-b599-e80fd93c4687
feature: Attribution
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---

# Modelli di attribuzione Marketo Measure {#marketo-measure-attribution-models}

Marketo Measure offre sei tipi di modelli di attribuzione:

* Primo contatto
* Creazione di lead
* A forma di U
* A forma di W
* Percorso completo
* Modello personalizzato

Questi modelli variano in complessità. I modelli First Touch e Lead Creation sono semplici, a sfioramento singolo. I restanti quattro sono modelli più complessi e multi-touch. La struttura dei modelli di attribuzione di Marketo Measure riflette i quattro principali punti di contatto che si verificano nel percorso di clienti:

* Primo contatto (FT)
* Creazione di lead (LC)
* Creazione opportunità (OC)
* Contratto a trattativa privata (CW)

![](assets/1-1.png)

In **modelli a sfioramento singolo**, il credito di attribuzione viene attribuito solo a un punto di contatto milestone, da cui il nome &quot;single-touch&quot;.
In **modelli multi-touch**, la maggior parte del credito di attribuzione viene assegnata a due o più punti di contatto milestone. Il credito rimanente viene attribuito ai punti di contatto che si verificano tra i punti di contatto di milestone.

Le sezioni successive descrivono ogni modello di attribuzione e il modo in cui viene assegnato il credito di attribuzione.

## Modelli a sfioramento singolo {#single-touch-models}

**Modello di primo contatto**

Il modello di primo contatto si concentra solo sulla prima interazione che un lead ha con la tua organizzazione. Questo modello attribuisce il 100% del credito di attribuzione alla prima volta che il lead viene a conoscenza della tua azienda, il Primo contatto (FT).

Dire visite di Kate `www.adobe.com` per la prima volta tramite un annuncio Adwords e visualizza un white paper. Il canale Adwords riceverebbe il 100% del credito di attribuzione da tale opportunità.

![](assets/2.png)

**Modello di creazione lead**

Il modello di creazione di lead attribuisce il 100% del credito di attribuzione al punto di contatto LC, quando un potenziale cliente fornisce le informazioni di contatto e diventa un lead.

Continuando dall&#39;esempio precedente, dopo la prima visita di Kate a `www.adobe.com` tramite Adwords, Austin visita il sito web tramite un post su LinkedIn. Austin compila un modulo e diventa un lead. In questo modello, Linkedin riceverebbe il 100% del credito di attribuzione.

![](assets/3.png)

## Modelli multi-touch {#multi-touch-models}

I modelli multi-touch vengono utilizzati per cicli di vendita più lunghi e complessi. Questi modelli sono particolarmente utili se diverse persone di un account/azienda sono coinvolte nel percorso dell&#39;acquirente.

**Modello a forma di U**

Il modello a forma di U si concentra sui punti di contatto FT e LC. In questo modello, i punti di contatto FT e LC ricevono ciascuno il 50% del credito di ricavo.

La prima visita di Kate a `www.adobe.com` tramite un annuncio Adwords riceverebbe il 50% del credito di attribuzione. Il restante 50% sarebbe stato attribuito al post di Linkedin che spinse Austin a compilare un modulo e diventare un lead.

![](assets/4.png)

**Modello a forma di W**

Tre dei punti di contatto milestone sono inclusi nel modello a forma di W. In questo modello, i punti di contatto FT, LC e OC vengono attribuiti a ciascuno il 30% del credito di attribuzione. Il restante 10% è attribuito in proporzione a qualsiasi punto di contatto intermedio che si verifica tra i tre punti di contatto milestone.

Kate e Austin menzionano Marketo Measure alla loro collega, Hillary. Trova un contenuto tramite una ricerca su Google e compila un modulo. In seguito, Austin riceve un&#39;email per la registrazione a un webinar e compila il modulo di registrazione sul sito web. Kate parla del prodotto Marketo Measure con un rappresentante di vendita.

Hillary riceve un’e-mail con un collegamento alla pagina dei prezzi e visita la pagina. Quindi viene creata un’opportunità per il loro account. La visita web di Hillary alla pagina dei prezzi riceve il merito per la creazione dell’opportunità perché è stata l’interazione di marketing più vicina alla data di creazione dell’opportunità. A ciascuno dei punti di contatto milestone viene assegnato il 30% del credito di attribuzione e ai punti di contatto intermediari viene assegnato il restante 10%.

![](assets/5.png)

**Modello percorso completo**

Il modello del percorso completo include tutti e quattro i punti di contatto milestone. FT, LC, OC e CW ricevono il 22,5% del credito sul reddito, mentre il restante 10% viene distribuito equamente tra i contatti intermedi.

Dopo la creazione dell&#39;opportunità, Kate, Austin e Hillary decidono di presentare Marketo Measure al loro CMO, Elizabeth. Elizabeth partecipa a una conferenza in cui Marketo Measure ospita un evento. Kate vede un post di LinkedIn su un caso di studio e compila un modulo per scaricare il contenuto. Elizabeth partecipa a una cena di vendita ospitata da Marketo Measure. Dopo la cena, decide di acquistare Marketo Measure e diventa un cliente. In questo scenario, alla cena di vendita verrebbe attribuito il 22,5% del credito sul ricavo derivante dall&#39;operazione chiusa. Anche i punti di contatto FT, LC e OC ricevono il 22,5% del credito. Ai punti di contatto intermediari viene assegnato anche il restante 10% del credito sulle entrate.

![](assets/6.png)

**Modello di attribuzione personalizzato**

Marketo Measure offre anche un modello di attribuzione personalizzata che consente agli utenti di scegliere quali punti di contatto o fasi personalizzate includere nel modello. Inoltre, gli utenti possono controllare la percentuale di credito di attribuzione attribuito a questi punti di contatto e stadi. Se un’opportunità non ha contatti intermedi dedicati, la percentuale viene distribuita uniformemente tra le altre posizioni.
