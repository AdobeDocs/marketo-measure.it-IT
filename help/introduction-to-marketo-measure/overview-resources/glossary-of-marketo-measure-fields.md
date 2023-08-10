---
unique-page-id: 18874586
description: Glossario dei campi Marketo Measure - Marketo Measure - Documentazione del prodotto
title: Glossario dei campi Marketo Measure
exl-id: 8e23b102-6d4f-4919-b361-04d1b184e710
feature: Fundamentals
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '3211'
ht-degree: 0%

---

# Glossario dei campi Marketo Measure {#glossary-of-marketo-measure-fields}

Questo articolo fornisce un glossario di tutti i campi Marketo Measure aggiunti alla Salesforce dal pacchetto base di Marketo Measure. Troverai anche informazioni sull’oggetto sul quale è possibile trovare il campo e su come ogni campo viene compilato con informazioni.

Per una mappa dell&#39;oggetto a cui si riferisce ogni campo Marketo Measure, [fai clic qui](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-object-and-field-taxonomy.md).

[A](#a) · [B](#b) · [C](#c) · [D](#d) · [E](#e) · [F](#f) · [G](#g) · H · I · J · [K](#k) · [L](#l) · [M](#m) · N · [O](#o) · [P](#p) · D · [R](#r) · [S](#s) · [T](#t) · [U](#u) · [V](#v) · L · X · Y · Z

## A {#a}

**Account** | Trovato sul punto di contatto di attribuzione acquirente

Questo campo viene compilato con il nome account associato alla BAT.

**ID campagna pubblicitaria** | Trovato sul punto di contatto Acquirente, Punto di contatto Attribuzione acquirente

È possibile compilare questo campo in tre modi:

`1)` Se il punto di contatto proviene da un’attività di ricerca a pagamento (AdWords o BingAds), verrà visualizzato qui l’ID della campagna pubblicitaria dalla piattaforma pubblicitaria.

`2)` Se il punto di contatto non proviene dalla ricerca a pagamento, il campo verrà popolato utilizzando il valore utm_campaign dall’URL della pagina di destinazione.

ad es. `http://info.marketomeasure.com/adwords-for-lead-generation?utm_source=Event&utm_medium=booth&utm_campaign=Marketo%20Virtual%20Event%20sep2014`

In questo esempio, verrebbe visualizzato l’ID della campagna pubblicitaria: __GAId__ Marketing Virtual Event settembre 2014

`3)` Se il punto di contatto proviene da una campagna Salesforce offline (una conferenza, una cena, ecc.), l’ID della campagna pubblicitaria mostrerà l’ID della campagna Salesforce

Se nessuno dei precedenti, questo campo sarà vuoto.

**Nome campagna pubblicitaria** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento (AdWords/Bing Ads), qui verrà visualizzato il nome della campagna pubblicitaria dalla piattaforma pubblicitaria.

`2)` Se il punto di contatto non proviene da una ricerca a pagamento e l’URL della pagina di destinazione contiene un valore per utm_campaign, tale valore verrà popolato qui.

`3)` Se il punto di contatto proviene da una campagna Salesforce, qui verrà visualizzato il nome della campagna Salesforce.

`4)` Verrà popolato con il Nome campagna definito per i punti di contatto generati dalle attività come generato nel tuo account Marketo Measure.

Se nessuno dei precedenti, questo campo sarà vuoto.

**Nome della campagna pubblicitaria (FT)** | Punto di contatto acquirente

Questo campo viene popolato nello stesso modo del Nome della campagna pubblicitaria. Tuttavia, questo campo mostra in modo specifico il nome della campagna pubblicitaria che ha generato il punto di contatto Primo contatto.

**Nome campagna pubblicitaria (LC)** | Punto di contatto acquirente

Questo campo viene popolato nello stesso modo del Nome della campagna pubblicitaria. Tuttavia, questo campo mostra in modo specifico il nome della campagna pubblicitaria che ha generato il punto di contatto Creazione lead.

**Contenuto annuncio** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento (AdWords/Bing Ads), il campo visualizza la copia completa dell’annuncio dalla piattaforma dell’annuncio.

`2)` Se il punto di contatto non proviene dalla ricerca a pagamento, questo campo visualizza il valore utm_content nell’URL della pagina di destinazione.

`3)` Verrà popolato con il valore Oggetto dell’attività correlata che ha generato il punto di contatto.

Se nessuno dei due valori precedenti, questo campo sarà vuoto.

**URL di destinazione dell’annuncio** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento, in questo campo viene visualizzata la destinazione URL a cui sei indirizzato dopo aver fatto clic sull’annuncio dal motore di ricerca.

Se il punto di contatto non proviene da una ricerca a pagamento, il campo sarà vuoto.

**ID gruppo di annunci** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento, qui verrà visualizzato l’ID del gruppo di annunci di AdWords/Bing Ads.

Se il punto di contatto non proviene dalla ricerca a pagamento, il campo sarà vuoto.

**Nome gruppo di annunci** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento, qui verrà visualizzato il nome del gruppo di annunci di AdWords/Bing Ads.

Se il punto di contatto non proviene dalla ricerca a pagamento, il campo sarà vuoto.

**ID annuncio** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento, qui verrà visualizzato l’ID annuncio di AdWords/Bing Ads.

`2)` Questo verrà compilato con l’ID esterno dell’attività se il punto di contatto viene generato da un’attività di gestione delle relazioni con i clienti.

Se il punto di contatto non proviene dalla ricerca a pagamento, il campo sarà vuoto.

**Modello personalizzato % attribuzione** | Punto di contatto di attribuzione acquirente

Se utilizzi un modello di attribuzione personalizzato, questo campo visualizza la percentuale di ricavi attribuita a un punto di contatto in base ai valori impostati nel modello personalizzato.

Se non utilizzi un modello personalizzato, questo campo sarà vuoto.

**% attribuzione primo contatto** | Punto di contatto di attribuzione acquirente

Questo campo visualizza la percentuale di ricavi attribuita a un punto di contatto in base a un modello di primo contatto.

**Attribuzione % piena** | Punto di contatto di attribuzione acquirente

Questo campo visualizza la percentuale di ricavi attribuita a un punto di contatto in base a un modello a percorso completo.

**Creazione % lead attribuzione** | Punto di contatto di attribuzione acquirente

Questo campo visualizza la percentuale di ricavi attribuita a un punto di contatto, in base a un modello di creazione di lead.

**A forma di U della percentuale di attribuzione** | Punto di contatto di attribuzione acquirente

Questo campo visualizza la percentuale di ricavi attribuita a un punto di contatto in base a un modello a forma di U.

**Attribuzione a forma di % W** | Punto di contatto di attribuzione acquirente

Questo campo visualizza la percentuale di ricavi attribuita a un punto di contatto in base a un modello a forma di W.

[Fai clic qui per tornare all’inizio della pagina](#top)

## B {#b}

**Importo opportunità Marketo Measure** | Opportunità Salesforce

Se utilizzi un campo Importo personalizzato per segnalare i ricavi dell’opportunità, Marketo Measure non è in grado di leggere questi campi. L’importo dell’opportunità Marketo Measure è un campo nascosto utilizzato per creare un flusso di lavoro che consente a Marketo Measure di leggere i campi dell’importo personalizzato nell’opportunità.

**Browser** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

Questo campo mostra il tipo di browser web utilizzato durante la sessione web (Chrome, Safari, Firefox, ecc.).

[Fai clic qui per tornare all’inizio della pagina](#top)

## C {#c}

**Contatto** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

Il campo mostra il Contatto a cui appartiene il punto di contatto.

**Conteggio - Modello personalizzato** | Punto di contatto di attribuzione acquirente

Se utilizzi un modello di attribuzione personalizzato, questo campo mostra, in formato decimale, la percentuale di credito ricavi assegnata a un punto di contatto in base ai valori impostati nel modello personalizzato.

Se non utilizzi un modello personalizzato, questo campo sarà vuoto.

**Conteggio - Modello personalizzato** | Punto di contatto acquirente

Se utilizzi un modello di attribuzione personalizzato, questo campo mostra, in formato decimale, la percentuale di credito di attribuzione data a un punto di contatto in base ai valori impostati nel modello personalizzato. Poiché questo campo si riferisce all’oggetto punto di contatto acquirente, non riflette il credito di ricavo, ma solo il credito di attribuzione.

Se non utilizzi un modello personalizzato, questo campo sarà vuoto.

**Conteggio - Primo contatto** | Punto di contatto di attribuzione acquirente

Questo campo mostra, in formato decimale, la percentuale di credito ricavi assegnata a un punto di contatto in base a un modello di primo contatto.

**Conteggio - Primo contatto** | Punto di contatto acquirente

Questo campo mostra, in forma decimale, la percentuale di credito di attribuzione data a un punto di contatto in base a un modello di primo contatto. Se il punto di contatto è il Primo contatto, questo campo sarà sempre 1,0 (che indica un credito di attribuzione del 100%). Se il punto di contatto non è il Primo contatto, questo campo sarà sempre 0 (che indica un credito di attribuzione dello 0 %).

Poiché questo campo si riferisce all’oggetto punto di contatto acquirente, non riflette il credito di ricavo, ma solo il credito di attribuzione.

**Conteggio - Percorso completo** | Punto di contatto di attribuzione acquirente

Questo campo mostra, in formato decimale, la percentuale di ricavi assegnata a un punto di contatto in base a un modello a percorso completo.

**Conteggio - Tocco creazione lead** | Punto di contatto di attribuzione acquirente

Questo campo mostra, in formato decimale, la percentuale di credito ricavi assegnata a un punto di contatto in base a un modello di creazione di lead.

**Conteggio - Tocco creazione lead** | Punto di contatto acquirente

Questo campo mostra, in formato decimale, la percentuale di credito di attribuzione data a un punto di contatto in base a un modello di creazione di lead. Se il punto di contatto è il contatto di Creazione lead, questo campo sarà sempre 1.0 (che indica un credito di attribuzione del 100%). Se il punto di contatto non è il contatto di creazione del lead, questo campo sarà sempre 0 (che indica un credito di attribuzione dello 0%).

Poiché questo campo si riferisce all’oggetto punto di contatto acquirente, non riflette il credito di ricavo, ma solo il credito di attribuzione.

**Conteggio - A forma di U** | Punto di contatto di attribuzione acquirente

Questo campo mostra, in formato decimale, la percentuale di credito ricavi assegnata a un punto di contatto in base a un modello a forma di U.

**Conteggio - A forma di U** | Punto di contatto acquirente

Questo campo mostra, in forma decimale, la percentuale di credito di attribuzione data a un punto di contatto in base a un modello a forma di U. Nel modello a forma di U, il credito è diviso tra il primo contatto, il contatto di creazione del lead e qualsiasi invio di moduli intermediari che si è verificato tra il primo contatto e il contatto di creazione del lead.

Poiché questo campo si riferisce all’oggetto punto di contatto acquirente, non riflette il credito di ricavo, ma solo il credito di attribuzione.

**Conteggio - A forma di W** | Punto di contatto di attribuzione acquirente

Questo campo mostra, in forma decimale, la percentuale di credito assegnata a un punto di contatto in base a un modello a forma di W.

[Fai clic qui per tornare all’inizio della pagina](#top)

## D {#d}

Data rapporto | Marketo Measure ABTest, Evento Marketo Measure

Evento Marketo Measure: la data in cui un utente ha intrapreso un’azione specifica sul sito web, attivando un Evento

Marketo Measure ABTest: la data in cui un utente ha partecipato a un test A/B sul sito web

[Fai clic qui per tornare all’inizio della pagina](#top)

## E {#e}

**Nome evento** | Evento Marketo Measure

Questo campo visualizza il nome dell’azione che ha attivato l’evento (ovvero Visualizzazione pagina).

**Valore evento** | Evento Marketo Measure

La descrizione dell’evento (ad es. Home page)

**Nome esperimento** | Marketo Measure ABTest

Questo campo visualizza il nome dell’esperimento (ad esempio Pulsante di prova)

**ID esperimento** |Test AB Marketo Measure

Il codice identificativo univoco di ciascun esperimento

[Fai clic qui per tornare all’inizio della pagina](#top)

## F {#f}

URL modulo | Punto di contatto acquirente, punto di contatto attribuzione acquirente

Questo campo visualizza una versione ridotta dell’URL di una pagina in cui si è verificata la compilazione del modulo (nessun parametro UTM)

URL modulo - Non elaborato | Punto di contatto acquirente, punto di contatto attribuzione acquirente

Questo campo visualizza l’intero URL della pagina in cui si è verificato il riempimento del modulo, inclusi i parametri UTM

[Fai clic qui per tornare all’inizio della pagina](#top)

## G {#g}

Geo City | Punto di contatto acquirente, punto di contatto attribuzione acquirente

In questo campo viene visualizzato il nome della città in cui il lead/contatto ha visitato il sito Web. Questa operazione viene eseguita tramite ricerca inversa dell’IP.

Paese geografica | Punto di contatto acquirente, punto di contatto attribuzione acquirente

Questo campo mostra il paese in cui il lead/contatto ha visitato il sito Web. Questa operazione viene eseguita tramite ricerca inversa dell’IP.

Area geografica | Punto di contatto acquirente, punto di contatto attribuzione acquirente

In questo campo viene visualizzata l&#39;area o lo stato in cui il lead/contatto ha visitato il sito Web. Questa operazione viene eseguita tramite ricerca inversa dell’IP.

[Fai clic qui per tornare all’inizio della pagina](#top)

## K {#k}

**ID parola chiave** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

Se il punto di contatto proviene da una ricerca a pagamento, questo campo visualizza l’ID della parola chiave dalla piattaforma dell’annuncio (Adwords/BingAds).

Se questo punto di contatto non proviene da una ricerca a pagamento, questo campo sarà vuoto.

**Keyword MatchType** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

Se il punto di contatto proviene da una ricerca a pagamento, questo campo visualizza il tipo di corrispondenza dalla piattaforma dell’annuncio (Adwords/Bing).

**Testo parola chiave** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento, questo campo visualizza il testo della parola chiave dalla piattaforma dell’annuncio (Adwords/BingAds) OPPURE il valore del parametro _bk nell’URL della pagina di destinazione.

ad es. `http://info.marketomeasure.com/intro-guide-b2b-marketing-attribution?_bt=12345678&_bk=marketing%20attribution&_bm=p&gclid=ABc123def456ghi789jkl`

`2)` Se il punto di contatto non proviene dalla ricerca a pagamento, questo campo visualizza il valore utm_term dall’URL della pagina di destinazione.

`http://www.marketomeasure.com/blog/lead-generation?utm_source=linkedin&utm_medium=Social&utm_campaign=ABC%20Blog&utm_content=Lead%20Gen&utm_term=lead%20gen`.

Se il punto di contatto non proviene da una ricerca a pagamento o se non è presente alcun valore utm_term, questo campo sarà vuoto.

[Fai clic qui per tornare all’inizio della pagina](#top)

## L {#l}

**Pagina di destinazione** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

Questo campo visualizza la versione ridotta dell’URL (nessun parametro UTM) della prima pagina web visitata durante una sessione web.

**Pagina di destinazione - Raw** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

Questo campo visualizza l’intero URL (inclusi i parametri UTM) della prima pagina web visitata durante una sessione web.

**Lead** | Punto di contatto dell&#39;acquirente, persona Marketo Measure

Questo campo visualizza il nome del lead a cui appartiene un punto di contatto.

[Fai clic qui per tornare all’inizio della pagina](#top)

## M {#m}

**Canale di marketing** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

Questo campo mostra il gruppo generale di attività di marketing o canale di marketing a cui appartiene il punto di contatto (ad esempio, Ricerca a pagamento, Diretta, Social, ecc.). I punti di contatto sono raggruppati in base alla configurazione dei canali nell’app Marketo Measure. Per ulteriori informazioni sui canali di marketing o su come impostare i canali, [fai clic qui](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md).

**Canale di marketing - Percorso** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

Questo campo mostra il canale di marketing e il sottocanale a cui appartiene un punto di contatto. Nell’esempio seguente, Canale di marketing - Percorso è Social.Linkedin, dove il canale di marketing è Social e il sottocanale è LinkedIn.

![](assets/1-3.png)

**Medio** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento, qui verrà visualizzato il supporto di Adwords/BingAds (ovvero CPC).

`2)` Se il punto di contatto non proviene dalla ricerca a pagamento, questo campo visualizza il valore utm_medium dall’URL della pagina di destinazione.

`3)` Se il punto di contatto proviene da una campagna offline, questo campo visualizza il campo &quot;Tipo&quot; nella campagna Salesforce.

`4)` Verrà popolato con il valore Tipo di attività dell’attività correlata che ha generato il punto di contatto.

In caso contrario, Marketo Measure imposta automaticamente un valore Medio.

[Fai clic qui per tornare all’inizio della pagina](#top)

O

**opportunità** | Punto di contatto di attribuzione acquirente

In questo campo viene visualizzata l&#39;opportunità a cui appartiene la BAT.

[Fai clic qui per tornare all’inizio della pagina](#top)

P

**Piattaforma** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

In questo campo vengono visualizzati il tipo di computer o telefono e il tipo di sistema operativo utilizzato durante la sessione Web.

[Fai clic qui per tornare all’inizio della pagina](#top)

R

**Pagina referrer** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

In questo campo viene visualizzato l&#39;URL (senza parametri UTM) dell&#39;ultima pagina Web in cui il lead o il contatto ha effettuato l&#39;indirizzamento al sito Web.

Ad esempio:

- Se il punto di contatto proviene da ricerca Pagata/Organica, il campo mostra l’URL del motore di ricerca

- Se il punto di contatto proviene da Social, il campo mostra l’URL del sito web social (ovvero LinkedIn)

**Pagina referrer - Raw** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

Questo campo visualizza le stesse informazioni della pagina Referrer, con la differenza che questo campo visualizza l’intero URL di riferimento (inclusi i parametri UTM).

**Ricavi - Modello personalizzato** | Punto di contatto di attribuzione acquirente

Se utilizzi un modello di attribuzione personalizzato, questo campo mostra l’importo del ricavo in dollari attribuito a un punto di contatto in base alla percentuale di attribuzione impostata nel modello personalizzato.

Se non utilizzi un modello personalizzato, l’importo in dollari sarà 0.

**Ricavi - Primo contatto** | Punto di contatto di attribuzione acquirente

Questo campo mostra l’importo del ricavo in dollari attribuito a un punto di contatto in base alla percentuale di attribuzione nel modello di primo contatto.

**Ricavi - Percorso completo** | Punto di contatto di attribuzione acquirente

Questo campo mostra l’importo delle entrate in dollari attribuito a un punto di contatto in base alla percentuale di attribuzione nel modello a percorso completo.

**Ricavi - Tocco creazione lead** | Punto di contatto di attribuzione acquirente

Questo campo mostra l’importo del ricavo in dollari attribuito a un punto di contatto in base alla percentuale di attribuzione nel modello per la creazione di lead.

**Ricavi - A forma di U** | Punto di contatto di attribuzione acquirente

Questo campo mostra l’importo delle entrate in dollari attribuito a un punto di contatto in base alla percentuale di attribuzione nel modello a forma di U.

**Ricavi - A forma di W** | Punto di contatto di attribuzione acquirente

Questo campo mostra l’importo delle entrate in dollari attribuito a un punto di contatto in base alla percentuale di attribuzione nel modello a forma di W.

[Fai clic qui per tornare all’inizio della pagina](#top)

S

**Campagna Salesforce** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

In questo campo viene visualizzata la campagna Salesforce a cui appartiene il punto di contatto.

**Frase di ricerca** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

Se il punto di contatto proviene da una ricerca organica o a pagamento, in questo campo verrà visualizzata la frase di ricerca digitata nel motore di ricerca. Tuttavia, per motivi di privacy, queste informazioni di solito non sono disponibili.

**Segmento** | Punto di contatto di attribuzione acquirente

Questo campo visualizza i segmenti a cui appartiene il punto di contatto. Questo dipenderà da come hai configurato le regole di segmentazione nell’app Marketo Measure.

[Fai clic qui per tornare all’inizio della pagina](#top)

T

**Data punto di contatto** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

`1)` Se il punto di contatto proviene da un’origine online, in questo campo viene visualizzata la data e l’ora in cui si è verificato.

`2)` Se il punto di contatto proviene da un evento offline, in questo campo verranno visualizzate la data e l’ora impostate nella campagna Salesforce o quelle selezionate nelle regole di sincronizzazione della campagna.

`3)` Se il punto di contatto proviene da un’attività, in questo campo verrà visualizzata la data e l’ora del campo selezionato come data del punto di contatto nelle regole dell’attività.

**Data punto di contatto (FT)** | Punto di contatto acquirente

Questo è lo stesso campo della Data del punto di contatto, tuttavia questo campo visualizza specificamente la data e l’ora in cui si è verificato il primo punto di contatto.

**Data punto di contatto (LC)** | Punto di contatto acquirente

Questo è lo stesso campo della Data punto di contatto, tuttavia questo campo visualizza in modo specifico la data e l’ora in cui si è verificato il punto di contatto per la creazione di lead.

**Posizione punto di contatto** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

Questo campo visualizza la posizione del punto di contatto. La posizione del punto di contatto riflette i principali punti di contatto milestone nel percorso di clienti (ad esempio FT, Form, LC, OC, Closed). La posizione del punto di contatto dipende da quando si è verificato nel percorso di clienti e un singolo punto di contatto può avere più di una posizione. Le diverse posizioni dei punti di contatto sono le seguenti:

First Touch (FT): la prima interazione di marketing con il brand

Creazione di lead (LC): la prima interazione di marketing nota (in genere l’invio di un modulo o l’inclusione di una campagna Salesforce)

Modulo: quando un visitatore compila un modulo online

Creazione opportunità (OC): l&#39;interazione di marketing più vicina alla creazione dell&#39;opportunità

Chiuso: l’interazione di marketing più vicina a quando l’Opp viene chiusa (acquisita o persa)

**Sorgente punto di contatto** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento, in questo campo viene visualizzato il nome della piattaforma dell’annuncio (AdWords/BingAds)

`2)` Se il punto di contatto proviene da una ricerca organica, in questo campo viene visualizzato il nome del motore di ricerca

`3)` Se non #1 o #2 e il valore utm_source è presente nell’URL della pagina di destinazione per il punto di contatto, tale valore verrà visualizzato qui

`4)` Questo verrà popolato come campagna CRM se il punto di contatto viene generato da una campagna CRM.

`5)` Se il punto di contatto viene generato da un’attività di gestione delle relazioni con i clienti, verrà popolato come attività di gestione delle relazioni con i clienti.

Se nessuno dei precedenti, questo campo verrà compilato come &#39;Web Direct&#39; o &#39;Web&#39;.

**Sorgente punto di contatto (FT)** | Punto di contatto acquirente

Questo è lo stesso campo di Sorgente punto di contatto, tuttavia questo campo visualizza in modo specifico l’origine del punto di contatto Primo contatto.

**Sorgente punto di contatto (LC)** | Punto di contatto acquirente

Questo è lo stesso campo di Sorgente punto di contatto, ma questo campo visualizza in modo specifico l’origine del punto di contatto Creazione lead.

**Tipo di punto di contatto** | Trovato sul punto di contatto Acquirente e sul punto di contatto Attribuzione acquirente.

Questo campo visualizza il tipo di interazione del punto di contatto. Verrà visualizzato come: Visita web, Modulo web o Chat web per punti di contatto JavaScript. Per i punti di contatto della campagna CRM, verrà visualizzato come CRM. Verrà compilata con il Tipo di attività o evento per i punti di contatto attività.

[Fai clic qui per tornare all’inizio della pagina](#top)

U

**UniqueId** | Punto di contatto acquirente, punto di contatto attribuzione acquirente

ID univoco associato a ciascun punto di contatto

**ID utente** | Marketo Measure ABTest

Codice di identificazione univoco di Optimizely per ogni utilizzo

[Fai clic qui per tornare all’inizio della pagina](#top)

## V {#v}

**Variante** | Marketo Measure ABTest

Nome della variante del test A/B

**ID variante** | Marketo Measure ABTest

Il codice di identificazione univoco per ogni variante del test A/B.

[Fai clic qui per tornare all’inizio della pagina](#top)
