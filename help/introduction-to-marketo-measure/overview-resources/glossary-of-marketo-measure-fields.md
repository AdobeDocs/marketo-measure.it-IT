---
unique-page-id: 18874586
description: Glossario dei campi di misura di Marketo - Misura di Marketo - Documentazione del prodotto
title: Glossario dei campi di misura di Marketo
exl-id: 8e23b102-6d4f-4919-b361-04d1b184e710
source-git-commit: 334dcd3dcbddacc4920d182d94908babd3cb8c89
workflow-type: tm+mt
source-wordcount: '3211'
ht-degree: 0%

---

# Glossario dei campi di misura di Marketo {#glossary-of-marketo-measure-fields}

Questo articolo fornisce un glossario di tutti i campi di misura Marketo che vengono aggiunti alla tua Salesforce dal pacchetto di base delle misure di Marketo. Troverai inoltre informazioni su quale oggetto è possibile trovare il campo e su come ogni campo è compilato con le informazioni.

Per una mappa dell&#39;oggetto a cui si riferisce ciascun campo di misura Marketo, si prega di contattare [fai clic qui](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-object-and-field-taxonomy.md).

[A](#a) ・ [B](#b) ・ [C](#c) ・ [D](#d) ・ [E](#e) ・ [F](#f) ・ [G](#g) ・ H ・ I ・ J ・ [K](#k) ・ [L](#l) ・ [M](#m) ・ N ・ [O](#o) ・ [P](#p) ・ Q ・ [R](#r) ・ [S](#s) ・ [T](#t) ・ [U](#u) ・ [V](#v) ・ W ・ X ・ Y ・ Z

## A {#a}

**Account** | Trovato su punto di contatto Attribuzione acquirente

Questo campo viene compilato con il nome account associato al BAT.

**Id campagna annunci** | Trovato su punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

Questo campo può essere compilato in tre modi:

`1)` Se il punto di contatto proviene da un’attività di ricerca a pagamento (AdWords o BingAds), l’ID della campagna pubblicitaria dalla piattaforma pubblicitaria verrà visualizzato qui.

`2)` Se il punto di contatto non proviene dalla ricerca a pagamento, il campo viene compilato utilizzando il valore utm_campaign dell’URL della pagina di destinazione.

ad esempio `http://info.marketomeasure.com/adwords-for-lead-generation?utm_source=Event&utm_medium=booth&utm_campaign=Marketo%20Virtual%20Event%20sep2014`

In questo esempio, l’ID campagna pubblicitaria viene visualizzato: __GAId__ Set di eventi virtuali di marketing 2014

`3)` Se il punto di contatto proviene da una campagna Salesforce offline (una conferenza, una cena, ecc.), l’ID campagna pubblicitaria apparirà sull’ID campagna Salesforce

In caso contrario, questo campo sarà vuoto.

**Nome della campagna pubblicitaria** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento (AdWords/Bing Ads), il nome della campagna pubblicitaria dalla piattaforma pubblicitaria verrà visualizzato qui.

`2)` Se il punto di contatto non proviene dalla ricerca a pagamento e l’URL della pagina di destinazione contiene un valore per utm_campaign, tale valore verrà popolato qui.

`3)` Se il punto di contatto proviene da una campagna Salesforce, il nome della campagna Salesforce verrà visualizzato qui.

`4)` Questo si popolerà con il Nome campagna definito per i punti di contatto generati dalle attività come generato all’interno del tuo account di misura Marketo.

In caso contrario, questo campo sarà vuoto.

**Nome campagna pubblicitaria (FT)** | Punto di contatto dell&#39;acquirente

Questo campo viene popolato allo stesso modo del Nome della campagna pubblicitaria. Tuttavia, questo campo mostra in modo specifico il nome della campagna pubblicitaria che ha generato il punto di contatto Primo contatto.

**Nome campagna pubblicitaria (LC)** | Punto di contatto dell&#39;acquirente

Questo campo viene popolato allo stesso modo del Nome della campagna pubblicitaria. Tuttavia, questo campo mostra in modo specifico il nome della campagna pubblicitaria che ha generato il punto di contatto Creazione di lead.

**Contenuto annuncio** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento (AdWords/Bing Ads), il campo visualizza la copia completa dell’annuncio dalla piattaforma dell’annuncio.

`2)` Se il punto di contatto non proviene dalla ricerca a pagamento, in questo campo viene visualizzato il valore utm_content nell’URL della pagina di destinazione.

`3)` Questo si popolerà con il valore Oggetto dell’attività correlata che ha generato il punto di contatto.

In caso contrario, questo campo sarà vuoto.

**URL destinazione annuncio** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento, questo campo visualizza la destinazione URL a cui sei indirizzato dopo aver fatto clic sull’annuncio dal motore di ricerca.

Se il punto di contatto non proviene dalla ricerca a pagamento, il campo è vuoto.

**Id Gruppo Di Annunci** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento, l’ID del gruppo di annunci da AdWords/Bing Ads verrà visualizzato qui.

Se il punto di contatto non proviene da una ricerca a pagamento, il campo è vuoto.

**Nome gruppo di annunci** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento, il Nome del gruppo di annunci da AdWords/Bing Ads verrà visualizzato qui.

Se il punto di contatto non proviene da una ricerca a pagamento, il campo è vuoto.

**Id annuncio** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento, l’Ad Id di AdWords/Bing Ads verrà visualizzato qui.

`2)` Questo si popolerà con l’ID esterno dell’attività se il punto di contatto viene generato da un’attività CRM.

Se il punto di contatto non proviene da una ricerca a pagamento, il campo è vuoto.

**Modello personalizzato % attribuzione** | Punto di contatto dell’attribuzione dell’acquirente

Se utilizzi un modello di attribuzione personalizzato, in questo campo viene visualizzata la percentuale di ricavi attribuiti a un punto di contatto in base ai valori impostati nel modello personalizzato.

Se non si utilizza un modello personalizzato, questo campo sarà vuoto.

**Attribution % First Touch** | Punto di contatto dell’attribuzione dell’acquirente

In questo campo viene visualizzata la percentuale di ricavi attribuiti a un punto di contatto in base a un modello di primo contatto.

**% attribuzione completa** | Punto di contatto dell’attribuzione dell’acquirente

In questo campo viene visualizzata la percentuale di ricavi attribuiti a un punto di contatto in base a un modello di percorso completo.

**Attribuzione % creazione lead** | Punto di contatto dell’attribuzione dell’acquirente

In questo campo viene visualizzata la percentuale di ricavi attribuiti a un punto di contatto, in base a un modello di creazione lead.

**Attribuzione % a forma di U** | Punto di contatto dell’attribuzione dell’acquirente

In questo campo viene visualizzata la percentuale di ricavi attribuiti a un punto di contatto in base a un modello a forma di U.

**Attribuzione % a forma di W** | Punto di contatto dell’attribuzione dell’acquirente

In questo campo viene visualizzata la percentuale di ricavi attribuiti a un punto di contatto in base a un modello a forma di W.

[Fai clic qui per tornare alla parte superiore della pagina](#top)

## B {#b}

**Importo opportunità misura Marketo** | Opportunità Salesforce

Se si utilizza un campo Importo personalizzato per segnalare i ricavi Opportunità, Marketo Measure non è in grado di leggere questi campi Importo personalizzati. L&#39;importo opportunità misura Marketo è un campo nascosto utilizzato per creare un flusso di lavoro che consente a Marketo Measure di leggere i campi Importo personalizzati sull&#39;opportunità.

**Browser** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

Questo campo visualizza il tipo di browser web utilizzato durante la sessione web (Chrome, Safari, Firefox, ecc.).

[Fai clic qui per tornare alla parte superiore della pagina](#top)

## C {#c}

**Contatto** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

Nel campo viene visualizzato il contatto a cui appartiene il punto di contatto.

**Conteggio - Modello personalizzato** | Punto di contatto dell’attribuzione dell’acquirente

Se utilizzi un modello di attribuzione personalizzato, in questo campo viene visualizzata la forma decimale della percentuale di credito sulle entrate attribuito a un punto di contatto in base ai valori impostati nel modello personalizzato.

Se non si utilizza un modello personalizzato, questo campo sarà vuoto.

**Conteggio - Modello personalizzato** | Punto di contatto dell&#39;acquirente

Se utilizzi un modello di attribuzione personalizzato, in questo campo viene visualizzata la percentuale di credito di attribuzione attribuita a un punto di contatto in base ai valori impostati nel modello personalizzato. Poiché questo campo si riferisce all’oggetto punto di contatto dell’acquirente, non riflette il credito sul ricavo, ma solo il credito di attribuzione.

Se non si utilizza un modello personalizzato, questo campo sarà vuoto.

**Conteggio - Primo contatto** | Punto di contatto dell’attribuzione dell’acquirente

Questo campo mostra, in forma decimale, la percentuale di credito sulle entrate attribuito a un punto di contatto in base a un modello Primo contatto.

**Conteggio - Primo contatto** | Punto di contatto dell&#39;acquirente

Questo campo mostra, in forma decimale, la percentuale di credito di attribuzione attribuita a un punto di contatto in base a un modello Primo contatto. Se il punto di contatto è Primo contatto, questo campo sarà sempre 1,0 (che indica il credito di attribuzione al 100%). Se il punto di contatto non è il primo contatto, questo campo sarà sempre 0 (che indica un credito di attribuzione dello 0 %).

Poiché questo campo si riferisce all’oggetto punto di contatto dell’acquirente, non riflette il credito sul ricavo, ma solo il credito di attribuzione.

**Conteggio - Percorso completo** | Punto di contatto dell’attribuzione dell’acquirente

Questo campo mostra, in formato decimale, la percentuale di ricavi dati a un punto di contatto in base a un modello di percorso completo.

**Conteggio - Contatto per la creazione di lead** | Punto di contatto dell’attribuzione dell’acquirente

Questo campo mostra, in forma decimale, la percentuale di credito di ricavi attribuito a un punto di contatto in base a un modello di creazione lead.

**Conteggio - Contatto per la creazione di lead** | Punto di contatto dell&#39;acquirente

Questo campo mostra, in forma decimale, la percentuale di credito di attribuzione attribuita a un punto di contatto in base a un modello di creazione di lead. Se il punto di contatto è il tocco Creazione lead, questo campo sarà sempre 1,0 (che indica il credito di attribuzione al 100%). Se il punto di contatto non è il tocco Creazione lead, questo campo sarà sempre 0 (a indicare un credito di attribuzione pari a 0%).

Poiché questo campo si riferisce all’oggetto punto di contatto dell’acquirente, non riflette il credito sul ricavo, ma solo il credito di attribuzione.

**Conteggio - A forma di U** | Punto di contatto dell’attribuzione dell’acquirente

Questo campo mostra, in forma decimale, la percentuale di credito sulle entrate attribuito a un punto di contatto in base a un modello a forma di U.

**Conteggio - A forma di U** | Punto di contatto dell&#39;acquirente

Questo campo mostra, in forma decimale, la percentuale di credito di attribuzione attribuita a un punto di contatto in base a un modello a forma di U. Nel modello a forma di U, il credito è diviso tra il primo contatto, il contatto per la creazione di lead e qualsiasi invio intermedio di moduli che si è verificato tra il primo contatto e il contatto per la creazione di lead.

Poiché questo campo si riferisce all’oggetto punto di contatto dell’acquirente, non riflette il credito sul ricavo, ma solo il credito di attribuzione.

**Conteggio - A forma di W** | Punto di contatto dell’attribuzione dell’acquirente

Questo campo mostra, in forma decimale, la percentuale di credito attribuita a un punto di contatto in base a un modello a forma di W.

[Fai clic qui per tornare alla parte superiore della pagina](#top)

## D {#d}

Data Segnalata | Marketo Measure ABTest, evento Marketo Measure

Evento di misura Marketo : la data in cui un utente ha eseguito un’azione specifica sul sito web attivando un evento

Marketo Measure ABTest : la data in cui un utente ha partecipato a un test A/B sul sito web

[Fai clic qui per tornare alla parte superiore della pagina](#top)

## E {#e}

**Nome evento** | Evento Marketo Measure

In questo campo viene visualizzato il nome dell’azione che ha attivato l’evento (ad esempio Visualizzazione pagina).

**Valore evento** | Evento Marketo Measure

Descrizione dell’evento (ad es. Homepage)

**Nome esperimento** | Misura Marketo ABTest

In questo campo viene visualizzato il nome dell’esperimento (ad es. Pulsante di prova)

**ID esperimento** |Test AB della misura Marketo

Codice identificativo unico per ogni esperimento

[Fai clic qui per tornare alla parte superiore della pagina](#top)

## F {#f}

URL modulo | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

Questo campo visualizza una versione ridotta dell’URL di una pagina in cui si è verificato il riempimento del modulo (nessun parametro UTM)

URL del modulo - Raw | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

Questo campo visualizza l’URL dell’intera pagina in cui si è verificato il riempimento del modulo, inclusi i parametri UTM

[Fai clic qui per tornare alla parte superiore della pagina](#top)

## G {#g}

Città geografica | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

In questo campo viene visualizzato il nome della città in cui il lead/contatto ha visitato il sito web. Questa operazione viene eseguita tramite ricerca IP inversa.

Paese geografico | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

In questo campo viene visualizzato il paese in cui il lead/contatto ha visitato il sito web. Questa operazione viene eseguita tramite ricerca IP inversa.

Regione geografica | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

In questo campo viene visualizzata la regione o lo stato in cui il lead/contatto ha visitato il sito web. Questa operazione viene eseguita tramite ricerca IP inversa.

[Fai clic qui per tornare alla parte superiore della pagina](#top)

## K {#k}

**ID parola chiave** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

Se il punto di contatto proviene dalla ricerca a pagamento, questo campo visualizza l’ID della parola chiave dalla piattaforma dell’annuncio (Adwords/BingAds).

Se questo punto di contatto non proviene da una ricerca a pagamento, questo campo sarà vuoto.

**Tipo di corrispondenza parola chiave** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

Se il punto di contatto proviene da una ricerca a pagamento, questo campo visualizza il tipo di corrispondenza dalla piattaforma dell’annuncio (Adwords/Bing).

**Testo della parola chiave** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

`1)` Se il punto di contatto proviene dalla ricerca a pagamento, questo campo visualizza il testo della parola chiave dalla piattaforma dell’annuncio (Adwords/BingAds) O il valore dal parametro _bk nell’URL della pagina di destinazione.

ad esempio `http://info.marketomeasure.com/intro-guide-b2b-marketing-attribution?_bt=12345678&_bk=marketing%20attribution&_bm=p&gclid=ABc123def456ghi789jkl`

`2)` Se il punto di contatto non proviene dalla ricerca a pagamento, questo campo visualizza il valore utm_term dall’URL della pagina di destinazione.

`http://www.marketomeasure.com/blog/lead-generation?utm_source=linkedin&utm_medium=Social&utm_campaign=ABC%20Blog&utm_content=Lead%20Gen&utm_term=lead%20gen`.

Se il punto di contatto non proviene da una ricerca a pagamento o non è presente alcun valore utm_term, questo campo sarà vuoto.

[Fai clic qui per tornare alla parte superiore della pagina](#top)

## L {#l}

**Pagina di destinazione** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

Questo campo visualizza la versione ridotta dell’URL (nessun parametro UTM) della prima pagina web visitata durante una sessione web.

**Pagina di destinazione - Raw** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

Questo campo visualizza l’intero URL (inclusi i parametri UTM) della prima pagina web visitata durante una sessione web.

**Lead** | Punto di contatto dell&#39;acquirente, persona di misura Marketo

In questo campo viene visualizzato il nome del lead a cui appartiene un punto di contatto.

[Fai clic qui per tornare alla parte superiore della pagina](#top)

## M {#m}

**Canale di marketing** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

Questo campo ti mostra il gruppo generale di attività di marketing o di canale di marketing a cui appartiene il punto di contatto (ad esempio Ricerca a pagamento, Diretta, Social, ecc.). I punti di contatto sono raggruppati in base alla configurazione dei canali nell’app di misura di Marketo. Per ulteriori informazioni sui canali di marketing o su come impostare i canali, [fai clic qui](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md).

**Canale di marketing - Percorso** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

Questo campo mostra il canale di marketing e il canale secondario a cui appartiene un punto di contatto. Nell’esempio seguente, Marketing Channel - Path è Social.Linkedin, dove il canale di marketing è Social e il sottocanale è LinkedIn.

![](assets/1-3.png)

**Media** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento, il supporto di Adwords/BingAds verrà visualizzato qui (cioè CPC).

`2)` Se il punto di contatto non proviene dalla ricerca a pagamento, in questo campo viene visualizzato il valore utm_medium dall’URL della pagina di destinazione.

`3)` Se il punto di contatto proviene da una campagna offline, in questo campo viene visualizzato il campo &quot;Tipo&quot; nella campagna Salesforce.

`4)` Questo si popolerà con il valore Tipo di attività dell’attività correlata che ha generato il punto di contatto.

In caso contrario, Marketo Measure imposta automaticamente un valore Medium.

[Fai clic qui per tornare alla parte superiore della pagina](#top)

O

**Opportunità** | Punto di contatto dell’attribuzione dell’acquirente

In questo campo viene visualizzata l’opportunità a cui appartiene la BAT.

[Fai clic qui per tornare alla parte superiore della pagina](#top)

P

**Piattaforma** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

Questo campo visualizza il tipo di computer o telefono e il tipo di sistema operativo utilizzato durante la sessione Web.

[Fai clic qui per tornare alla parte superiore della pagina](#top)

R

**Pagina di riferimento** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

In questo campo viene visualizzato l’URL (senza parametri UTM) dell’ultima pagina web in cui il lead/contatto li ha indirizzati al sito web.

Ad esempio:

- Se il punto di contatto proviene dalla ricerca a pagamento/Organico, nel campo viene visualizzato l’URL del motore di ricerca

- Se il punto di contatto proviene da Social, il campo mostra l’URL del sito web social (ad es. LinkedIn)

**Pagina di riferimento - Raw** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

Questo campo visualizza le stesse informazioni della pagina di riferimento, tranne per il fatto che questo campo visualizzerà l’intero URL di riferimento (inclusi i parametri UTM).

**Ricavi - Modello personalizzato** | Punto di contatto dell’attribuzione dell’acquirente

Se utilizzi un modello di attribuzione personalizzato, questo campo mostra l’importo dei ricavi in dollari attribuiti a un punto di contatto in base alla percentuale di attribuzione impostata nel modello personalizzato.

Se non si utilizza un modello personalizzato, l&#39;importo in dollari sarà 0.

**Ricavi - Primo contatto** | Punto di contatto dell’attribuzione dell’acquirente

Questo campo mostra l’importo dei ricavi in dollari attribuiti a un punto di contatto in base alla percentuale di attribuzione nel modello Primo contatto.

**Ricavi - Percorso completo** | Punto di contatto dell’attribuzione dell’acquirente

Questo campo mostra l’importo dei ricavi in dollari attribuiti a un punto di contatto in base alla percentuale di attribuzione nel modello a percorso completo.

**Entrate - Contatto per la creazione di lead** | Punto di contatto dell’attribuzione dell’acquirente

Questo campo mostra l’importo dei ricavi in dollari attribuiti a un punto di contatto in base alla percentuale di attribuzione nel modello di creazione del lead.

**Entrate - A forma di U** | Punto di contatto dell’attribuzione dell’acquirente

Questo campo mostra l’importo dei ricavi in dollari attribuiti a un punto di contatto in base alla percentuale di attribuzione nel modello a forma di U.

**Ricavi - A forma di W** | Punto di contatto dell’attribuzione dell’acquirente

Questo campo mostra l’importo dei ricavi in dollari attribuiti a un punto di contatto in base alla percentuale di attribuzione nel modello a forma di W.

[Fai clic qui per tornare alla parte superiore della pagina](#top)

S

**Campagna Salesforce** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

In questo campo viene visualizzata la campagna Salesforce a cui appartiene il punto di contatto.

**Frase di ricerca** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

Se il punto di contatto proviene da una ricerca a pagamento o organica, in questo campo viene visualizzata la frase di ricerca digitata nel motore di ricerca. Tuttavia, per motivi di privacy, queste informazioni solitamente non sono disponibili.

**Segmento** | Punto di contatto dell’attribuzione dell’acquirente

In questo campo vengono visualizzati i segmenti a cui appartiene il punto di contatto. Questo dipenderà da come hai configurato le regole di segmentazione nell’app Marketo Measure.

[Fai clic qui per tornare alla parte superiore della pagina](#top)

T

**Data punto di contatto** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

`1)` Se il punto di contatto proviene da un’origine online, in questo campo viene visualizzata la data e l’ora in cui si è verificato il punto di contatto.

`2)` Se il punto di contatto proviene da un evento offline, in questo campo vengono visualizzati la data e l’ora impostate nella campagna Salesforce o dal campo data selezionato nelle regole di sincronizzazione della campagna.

`3)` Se il punto di contatto proviene da un’attività, in questo campo vengono visualizzate la data e l’ora del campo selezionato come data del punto di contatto nelle regole dell’attività.

**Data punto di contatto (FT)** | Punto di contatto dell&#39;acquirente

Si tratta dello stesso campo della data del punto di contatto, ma questo campo visualizza in modo specifico la data e l’ora in cui si è verificato il punto di contatto Primo contatto.

**Data punto di contatto (LC)** | Punto di contatto dell&#39;acquirente

Si tratta dello stesso campo della data del punto di contatto, tuttavia in questo campo viene visualizzata in modo specifico la data e l’ora in cui si è verificato il punto di contatto Creazione lead.

**Posizione punto di contatto** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

In questo campo viene visualizzata la posizione del punto di contatto. La posizione del punto di contatto riflette i principali punti di contatto cardine nel percorso del cliente (ad esempio FT, Form, LC, OC, Closed). La posizione del punto di contatto dipende da quando si è verificato nel percorso del cliente e un singolo punto di contatto può avere più di una posizione. Le diverse posizioni dei punti di contatto sono le seguenti:

Primo contatto (FT) - La prima interazione di marketing che qualcuno ha con il tuo marchio

Creazione di lead (LC) - La prima interazione di marketing nota (tipicamente invio di moduli o inclusione in una campagna Salesforce)

Modulo : quando un visitatore compila un modulo online

Creazione di opportunità (OC) - L&#39;interazione di marketing più simile al momento della creazione dell&#39;Opp

Chiuso : l’interazione di marketing più simile a quando Opp viene chiuso (won o perso)

**Origine punto di contatto** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

`1)` Se il punto di contatto proviene da una ricerca a pagamento, in questo campo viene visualizzato il nome della piattaforma di annunci (AdWords/BingAds)

`2)` Se il punto di contatto proviene da una ricerca organica, in questo campo viene visualizzato il nome del motore di ricerca

`3)` Se non #1 o #2 e il valore utm_source è presente nell’URL della pagina di destinazione per il punto di contatto, tale valore verrà visualizzato qui

`4)` Questo verrà popolato come campagna CRM se il punto di contatto viene generato da una campagna CRM.

`5)` Questo si popolerà come attività CRM se il punto di contatto viene generato da un’attività CRM.

In nessuno dei casi precedenti, questo campo verrà popolato come &#39;Web Direct&#39; o &#39;Web&#39;.

**Origine punto di contatto (FT)** | Punto di contatto dell&#39;acquirente

Si tratta dello stesso campo dell’origine del punto di contatto , tuttavia questo campo visualizza in modo specifico l’origine del punto di contatto Primo contatto.

**Origine punto di contatto (LC)** | Punto di contatto dell&#39;acquirente

Si tratta dello stesso campo dell&#39;origine punto di contatto, tuttavia questo campo visualizza in modo specifico l&#39;origine del punto di contatto Creazione lead.

**Tipo punto di contatto** | Trovato sul punto di contatto dell’acquirente e sul punto di contatto dell’attribuzione dell’acquirente.

In questo campo viene visualizzato il tipo di interazione del punto di contatto. Viene visualizzato come: Visita web, modulo web o chat web per punti di contatto JavaScript. Per i punti di contatto della campagna di gestione delle relazioni con i clienti, verrà visualizzato come CRM. Viene compilata con l’attività o il tipo di evento per i punti di contatto dell’attività.

[Fai clic qui per tornare alla parte superiore della pagina](#top)

U

**UniqueId** | Punto di contatto dell&#39;acquirente, punto di contatto dell&#39;attribuzione dell&#39;acquirente

ID univoco associato a ciascun punto di contatto

**ID utente** | Misura Marketo ABTest

Codice di identificazione univoco di ogni utilizzo

[Fai clic qui per tornare alla parte superiore della pagina](#top)

## V {#v}

**Variazione** | Misura Marketo ABTest

Nome della variazione del test A/B

**ID variante** | Misura Marketo ABTest

Codice di identificazione univoco per ciascuna variante del test A/B.

[Fai clic qui per tornare alla parte superiore della pagina](#top)
