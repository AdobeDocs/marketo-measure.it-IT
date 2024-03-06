---
description: "[!DNL Marketo Measure] Guida al reporting - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Guida al reporting"
exl-id: 9b991f9e-c187-4b43-b0a8-8ed3e9a6056b
feature: Reporting
source-git-commit: 4787f765348da71bc149c997470ce678ba498772
workflow-type: tm+mt
source-wordcount: '6437'
ht-degree: 0%

---

# [!DNL Marketo Measure] Guida al reporting {#marketo-measure-reporting-guide}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedi ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

Prima di creare un [!DNL Marketo Measure] report, è fondamentale confermare la tua [!DNL Marketo Measure] Le impostazioni dell’account sono state riviste e configurate per garantire che i dati all’interno dei rapporti siano accurati e riflettano le specificità della tua azienda. Inoltre, i progetti di reporting funzionano meglio quando seguono un processo strutturato. Justin Norris, a [!DNL Marketo Measure] utenti esperti, sostenitori e partner di [Perkuto](https://perkuto.com/) riassunto esperto [approccio al reporting in [!DNL Marketo Measure]](https://perkuto.com/blog/turning-attribution-data-into-actionable-insights/):

**Stabilisci obiettivi**: &quot;La prima domanda da porsi è &#39;perché misuriamo?&#39; Lori Wizdo di [Forrester Research](https://go.forrester.com/) l&#39;ho riassunto bene in una [Webinar Marketo](https://www.marketo.com/webinars/beyond-revenue-performance-real-kpis-of-b2b-marketing/). Secondo lei, &quot;misuriamo a dimostrare o convalidare una decisione o il valore del marketing o a migliorare (miglioramento del processo).&quot; Potremmo aggiungere che le informazioni provenienti da una buona misurazione forniscono anche input e indicazioni nel processo di pianificazione del marketing.

Prima di iniziare, è essenziale essere chiarissimi sugli obiettivi, sulle domande a cui state cercando di rispondere, o sui problemi che state cercando di risolvere. Che storia vuoi raccontare? Quali decisioni saranno prese di conseguenza? Troppo spesso questi fondamentali sono mal pensati, portando a frustrazione per tutti coloro che sono coinvolti.&quot;

**Progettazione report**: &quot;Poi, devi progettare il rapporto e determinare le dimensioni, le metriche e il set di dati specifici che conterrà. Un’esperienza comune è quella di fornire a un utente aziendale esattamente ciò che chiede, solo per fargli sentire ancora che le sue esigenze non sono soddisfatte. Questo perché le informazioni che un utente aziendale sta cercando non sono sempre contenute nel rapporto richiesto. Un buon analista (o una persona MOPS con un cappello da analista) farà domande chiarificatrici, stabilirà definizioni comuni (&quot;quindi, cosa intendi veramente per lead?&quot;), e persino schizzerà una vista del rapporto finale per assicurarsi che ci sia un allineamento. Solo a quel punto potrai creare il rapporto, sapendo di avere un solido set di requisiti.&quot;

**Report Build**: &quot;Una volta che vai a costruire, non è raro trovarsi in blocchi stradali o vicoli ciechi. Ad esempio, potresti scoprire che non disponi di un punto dati essenziale o che i tuoi oggetti non si collegano nel modo desiderato. Per risolvere questi problemi, credo anche che sia fondamentale capire cosa sta accadendo &quot;sotto il cofano&quot; nella vostra &quot;macchina&quot; di reporting. Questa fluenza ti consentirà di dimensionare rapidamente una richiesta di reporting e di valutare se è raggiungibile (e di concepire più facilmente soluzioni creative quando non lo è).&quot;

Diamo un&#39;occhiata &quot;sotto il cofano&quot; per capire meglio che cosa rende [!DNL Marketo Measure] esecuzione del computer per la generazione di rapporti di attribuzione.

## Oggetti punto di contatto dell&#39;acquirente (CRM) {#buyer-touchpoint-objects-crm}

Al livello più alto, esistono due categorie di reporting basate sui due diversi oggetti punto di contatto buyer: Queste categorie determinano il tipo di [!DNL Marketo Measure] dati di cui vuoi generare un rapporto: dati relativi ad un _singolo_, o dati relativi a un _opportunità_.

1. **Punti di contatto dell&#39;acquirente** (BTs) / Individui / Coinvolgimento totale

   * Comunemente utilizzato per le metriche &quot;top of the funnel&quot; (TOFU) e per i rapporti relativi a _singoli utenti_ (lead, contatti, [!DNL Marketo Measure] Persone)
   * I BTs sono utilizzati per comprendere tutte le interazioni di marketing relative a **persone**, in quanto contengono la cronologia completa dei punti di contatto per ogni persona. Come promemoria, questi punti di contatto vengono creati in CRM per il primo contatto anonimo, il contatto per la creazione di lead e qualsiasi successivo invio di moduli o punto di contatto scelto di sincronizzare da una campagna o attività offline.

1. **Punti di contatto di attribuzione acquirente** (BAT) / Opportunità / Livello account / Ricavi

   * Comunemente utilizzato per le metriche e i rapporti relativi a &quot;metà e/o fondo del funnel&quot; (MOFU e BOFU) _Opportunità_.
   * Le BAT rappresentano i punti di contatto pertinenti di tutte le persone collegate al **opportunità** (tramite i Ruoli di contatto dell’opportunità o tramite un ID account condiviso, a seconda delle impostazioni). A differenza delle BT che riguardano solo le persone, le BAT possono anche essere associate a **ricavi**. Di conseguenza, è possibile utilizzare le BAT per rispondere a domande relative alle opportunità, incluso il numero di opportunità aperte o chiuse oppure il valore della pipeline e i ricavi ottenuti.

>[!NOTE]
>
>Le BAT sono create da BT. In sostanza, il tracciamento inizia a livello individuale tramite i BT. Una volta creata un&#39;opportunità su un account, tutti i BT provenienti dai contatti dello stesso account sono referenziati e idonei a creare BAT che si riferiscono all&#39;opportunità, quindi si desidera utilizzare l&#39;uno o l&#39;altro a seconda delle domande a cui si sta cercando di rispondere: domande relative alle metriche &quot;Persone&quot; (report BT) o domande relative alle metriche &quot;Opportunità&quot; (report BAT)

Articolo di supporto: [Differenza tra i punti di contatto dell’acquirente e i punti di contatto di attribuzione dell’acquirente](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md#configuration-and-setup)

## Punto di contatto dell&#39;acquirente (BT) {#buyer-touchpoint-bt}

Il punto di contatto dell&#39;acquirente (BT) è l&#39;oggetto utilizzato per tenere traccia di ogni interazione di marketing con il materiale di marketing. Di ogni individuo (Lead/Contact/[!DNL Marketo Measure] Persona) il percorso sarebbe rappresentato dai loro BT collegati. In entrata [!DNL Marketo Measure], il percorso di un individuo è costituito da:

1. Come ha fatto questa persona a interagire per la prima volta con il nostro marchio? (Primo contatto o _FT_)
1. Come ha fatto questa persona a convertirsi / diventare nota / diventare un lead? (Creazione di lead o _LC_)
1. In che altro modo questa persona ha interagito con il nostro marchio e materiali di marketing da quando è diventata Lead? (_PostLC_)

I punti di contatto dell&#39;acquirente vengono utilizzati per rispondere a domande relative a _persone_ (&quot;persone&quot; sono rappresentate da lead o contatti all’interno di un CRM), come la generazione di lead/contatti o le metriche di acquisizione, anziché le metriche relative all’opportunità. Ad esempio:

* Quali canali offrono più lead?
* Quali canali costano di più o di meno per creare un nuovo lead?
* Con quali contenuti interagiscono i miei lead/contatti?
* Qual è la storia di marketing di titoli, ruoli e utenti tipo particolari?
* Quali canali generano MQL o altri stati di lead/contatti?

In primo luogo, le aziende devono sapere &quot;da dove vengono i miei lead/contatti?&quot;. Storicamente, questa risposta veniva fornita con un singolo valore unidimensionale (ad esempio, Origine lead). Tuttavia, come descritto in #1 e #2, sappiamo che i lead possono avere più punti di contatto durante il percorso in cui diventano lead. Il punto di contatto dell’acquirente ci consente di ottenere informazioni sulle due interazioni più cruciali che rappresentano come è stato generato un lead: il primo contatto e il contatto per la creazione di un lead. I punti di contatto dell&#39;acquirente sono inoltre _multidimensionale_ Ciò significa che trasportano un sacco di dati di marketing, principalmente da dove proviene la persona (Canale di marketing) e ciò che la persona ha coinvolto (Contenuto).

Il [modelli di attribuzione](/help/introduction-to-marketo-measure/overview-resources/marketo-measure-attribution-models.md) per ottenere informazioni approfondite sulle metriche basate sulle persone:

* **Primo contatto** - 100% di credito di attribuzione al primo contatto del lead (FT)
* **Creazione di lead** - Attribuzione del 100% del credito al lead Creation Touch (LC) del lead
* **A forma di U** - approccio multi-touch, con il 40% di credito al FT, il 40% di credito al LC

<table> 
 <tbody>
  <tr>
   <td><img src="assets/bizible-reporting-guide-1.png"></td> 
   <td>Il modello a forma di U è progettato per dare credito a qualsiasi punto di contatto dell'acquirente che riassuma come un lead è diventato un lead. Anche se è possibile segnalare i punti di contatto successivi di questi lead per comprendere il coinvolgimento aggiuntivo (Post LC), non fanno parte del <strong>Percorso di creazione lead</strong> quindi non ricevono alcun credito di attribuzione nei modelli FT, LC o a forma di U.<p>

&#42;Più comunemente, l&#39;attribuzione a U riflette una divisione pari 50/50 tra FT e LC. Se il lead converte nella stessa sessione del primo contatto, un singolo punto di contatto rappresenterebbe sia le posizioni FT che quelle LC. Pertanto, il 100% dell’attribuzione verrebbe assegnato a un singolo punto di contatto.</td>
</tr>
 </tbody>
</table>

Questi modelli pongono molta enfasi sulle interazioni in fase iniziale e sul coinvolgimento funnel. L’attribuzione a forma di U è il modello consigliato in quanto tiene conto dei punti di contatto FT e LC garantendo che venga dato credito a qualsiasi contatto che abbia influenzato il lead nella creazione. Tuttavia, è possibile ottenere ulteriori informazioni dai modelli di contatto Primo contatto e Creazione lead se si desidera comprendere tali parti specifiche del percorso lead in modo più dettagliato.

## Rapporti consigliati utilizzando il punto di contatto dell&#39;acquirente (BT) {#recommended-reports-using-the-buyer-touchpoint-bt}

1. **LEAD CON PUNTI DI CONTATTO ACQUIRENTE**

**1,1 | Nuovi lead per canale di marketing**

Riepilogare i dati dei punti di contatto acquirenti del lead per il campo &quot;Canale di marketing&quot; è la visualizzazione di livello più alto che indica quali canali/tattiche stanno influenzando i nuovi lead nella creazione. Strutturando questo rapporto su un &quot;Tipo di data&quot; = &quot;Data di creazione&quot; si assicura che una coorte di &quot;Nuovi lead netti&quot; (quando il lead è stato creato nel CRM) sia stabilita nel rapporto.

<table> 
 <tbody>
  <tr>
   <td>Domanda</td> 
   <td>Quali canali di marketing stanno influenzando i lead nella creazione?</td> 
  </tr>
  <tr>
   <td>Tipo di rapporto</td> 
   <td>Punti di contatto lead e acquirenti (CRM)<br>
   Metrica: lead ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Campo data / Tipo data</td> 
   <td>Data di creazione lead (CRM) / Data di creazione (Discover)</td> 
  </tr>
  <tr>
   <td>Intervallo date</td> 
   <td><i>seleziona l’intervallo di date desiderato</i></td> 
  </tr>
  <tr>
   <td>Gruppo/Dimension</td> 
   <td>Canale di marketing</td> 
  </tr>
  <tr>
   <td>Modelli ottimali</td> 
   <td>Primo contatto, Creazione di lead, <strong>A forma di U</strong><br>
   *SOMMARE i campi "Conteggio" nei rapporti CRM (Conteggio - Primo contatto, Conteggio - Creazione di lead, Conteggio - A forma di U)</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Per qualsiasi tipo di rapporto &quot;Lead con punti di contatto acquirenti&quot;, inizia personalizzando il rapporto predefinito con titolo &quot;[!DNL Marketo Measure] 101 | Lead per canale. Questo rapporto è disponibile come standard ed è un ottimo ambiente sandbox predefinito, come descritto nella tabella precedente, e può essere rapidamente personalizzato per esigenze di reporting più specifiche.

**1,2 | Nuovi lead per campagna (o informazioni più granulari)**

Per informazioni più granulari sui dati riepilogati nel rapporto &quot;Nuovi lead per canale di marketing&quot; (1.1), aggiungi un ulteriore riepilogo a livello di campagna. Questo consente non solo di comprendere cosa &quot;Canali di marketing&quot; stanno guidando nuovi lead nella creazione, ma più specificamente, quali campagne all’interno di tali canali stanno ottenendo i migliori risultati:

<table> 
 <tbody>
  <tr>
   <td>Domanda</td> 
   <td>Cosa <i>campagne</i> sta influenzando i lead nella creazione?</td> 
  </tr>
  <tr>
   <td>Tipo di rapporto</td> 
   <td>Punti di contatto lead e acquirenti (CRM)<br>
   Metrica: lead ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Campo data / Tipo data</td> 
   <td>Data di creazione lead (CRM) / Data di creazione (Discover)</td> 
  </tr>
  <tr>
   <td>Intervallo date</td> 
   <td><i>seleziona l’intervallo di date desiderato</i></td> 
  </tr>
  <tr>
   <td>Gruppo/Dimension</td> 
   <td>Nome campagna pubblicitaria (CRM)</td> 
  </tr>
  <tr>
   <td>Modelli ottimali</td> 
   <td>Primo contatto, Creazione di lead, <strong>A forma di U</strong><br>
   *SOMMARE i campi "Conteggio" nei rapporti CRM (Conteggio - Primo contatto, Conteggio - Creazione di lead, Conteggio - A forma di U)</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Ottieni informazioni ancora più dettagliate riepilogando il rapporto con altri campi disponibili dall’oggetto punto di contatto dell’acquirente. Per farlo, imposta raggruppamenti aggiuntivi (CRM) o dimensioni (Discover). A seconda del canale (che può essere rappresentativo del tuo ruolo), ci possono essere ulteriori dettagli oltre al livello della campagna in cui desideri ottenere informazioni approfondite. Analizziamo la ricerca a pagamento, ad esempio nella tabella seguente...

<table> 
 <tbody>
  <tr>
   <td>Domanda</td> 
   <td>Cosa <i>parole chiave</i> sta influenzando i lead nella creazione?</td> 
  </tr>
  <tr>
   <td>Tipo di rapporto</td> 
   <td>Punti di contatto lead e acquirenti (CRM)<br>
   Metrica: lead ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filtri</td> 
   <td>Canale di marketing = ricerca a pagamento</td> 
  </tr>
  <tr>
   <td>Campo data / Tipo data</td> 
   <td>Data di creazione lead (CRM) / Data di creazione (Discover)</td> 
  </tr>
  <tr>
   <td>Intervallo date</td> 
   <td><i>seleziona l’intervallo di date desiderato</i></td> 
  </tr>
  <tr>
   <td>Gruppo/Dimension</td> 
   <td>Testo parola chiave (CRM) / Parola chiave (Discover)</td> 
  </tr>
  <tr>
   <td>Modelli ottimali</td> 
   <td>Primo contatto, Creazione di lead, <strong>A forma di U</strong><br>
   *SOMMARE i campi "Conteggio" nei rapporti CRM (Conteggio - Primo contatto, Conteggio - Creazione di lead, Conteggio - A forma di U)</td> 
  </tr>
 </tbody>
</table>

Il livello di granularità può variare a seconda del canale. L&#39;approccio consigliato sarebbe quello di chiedersi, &quot;che cosa circa &#39;canale X&#39; sto cercando di capire più dettagliatamente?&quot;. I Paid Search Manager possono essere interessati anche a dimensioni aggiuntive, ad esempio:

* Nome campagna pubblicitaria
* Contenuto annuncio
* Gruppo di annunci

I gestori di eventi, tuttavia, potrebbero essere più interessati a quali eventi specifici o a quali tipi di eventi hanno influenzato di più la creazione di lead:

* Nome campagna annuncio/Campagna Salesforce = Evento specifico
* Medio = Tipo di campagna

**PROMEMORIA**: potrebbe essere necessario aggiungere altri filtri a una qualsiasi delle varianti di rapporto descritte sopra o sotto. Questi filtri sono specifici per la tua organizzazione e possono essere consigliati dai team Marketing Ops o Sales Ops. Non è raro che un’organizzazione esegua gli stessi filtri in tutti i rapporti per garantire che il rapporto sia il più pulito e accurato possibile. Esempi comuni possono essere:

* Esclusione di record interni dai test, in genere per indirizzo e-mail
* Filtraggio basato su determinati &quot;Tipi di record&quot; che possono essere specifici per la tua unità aziendale

**1,3 | Nuovi lead per contenuto (solo report CRM)**

<table> 
 <tbody>
  <tr>
   <td>Domanda</td> 
   <td>Cosa <i>contenuto</i> sta influenzando i lead nella creazione?</td> 
  </tr>
  <tr>
   <td>Tipo di rapporto</td> 
   <td>Punti di contatto lead e acquirenti (CRM)</td> 
  </tr>
  <tr>
   <td>Campo data</td> 
   <td>Data creazione lead</td> 
  </tr>
  <tr>
   <td>Intervallo date</td> 
   <td><i>seleziona l’intervallo di date desiderato</i></td> 
  </tr>
  <tr>
   <td>Gruppo/Dimension</td> 
   <td>Pagina di destinazione<br> 
   URL modulo</td> 
  </tr>
  <tr>
   <td>Modelli ottimali</td> 
   <td>Primo contatto, Creazione di lead, <strong>A forma di U</strong><br></td> 
  </tr>
 </tbody>
</table>

**PROMEMORIA**: i due campi principali per la generazione di rapporti su contenuti/risorse digitali sono &quot;Pagina di destinazione&quot; e &quot;URL modulo&quot;. Questi due valori possono essere identici se il lead converte (invia un modulo) nella stessa pagina in cui sono &quot;arrivati&quot; (pagina di destinazione), _tuttavia_, a volte questi valori sono diversi. Ad esempio, il lead può fare clic su un collegamento in Facebook che porta a una pagina del sito Web (si tratta del valore &quot;Pagina di destinazione&quot;). Il lead può quindi spostarsi da tale pagina, continuare la propria sessione sul sito e infine inviare un modulo su un’altra pagina (URL modulo). Questo sarebbe riassunto in un singolo punto di contatto che rappresenta da dove proviene il lead (canale di marketing), quali contenuti li hanno portati al sito (pagina di destinazione) e quali contenuti hanno finito per scaricare (URL modulo). &quot;URL modulo&quot; è anche il campo di destinazione per i rapporti su altri moduli non associati a contenuto scaricabile come i moduli &quot;Contattaci&quot; o &quot;Richiesta demo&quot;.

>[!TIP]
>
>Ottieni informazioni approfondite su &quot;contenuti&quot; specifici con filtri aggiuntivi
>
>* Filtra per: &quot;Pagina di destinazione&quot; CONTIENE (ad esempio):
>   * /blog
>   * /ebook
>   * /webinar
>
>* OPPURE: &quot;URL modulo&quot; CONTIENE (ad esempio)
>   * /contact
>   * /demo

I rapporti basati su &quot;Contenuto&quot; forniscono un ottimo valore quando si generano rapporti su qualsiasi parte del funnel, ma sono più comunemente utilizzati nella parte superiore del funnel per fornire informazioni aggiuntive sul coinvolgimento iniziale dei lead. Considerando che &quot;Ricerca organica&quot; tende ad essere il canale più forte per promuovere il coinvolgimento iniziale (FT), non ci sono così tanti dati a livello di &quot;Campagna&quot;.

I rapporti basati su &#39;Contenuto&#39; sono utili per ottenere informazioni approfondite su ciò che guida i Lead in modo più specifico all&#39;interno del canale di marketing di livello superiore, in questo caso &quot;Ricerca organica&quot;.

**1,4 | Coinvolgimento lead totale in un determinato intervallo di date**

<table> 
 <tbody>
  <tr>
   <td>Domanda</td> 
   <td>Quali canali di marketing hanno avuto più successo <i>coinvolgimento lead totale</i> nell’ultimo (settimana/mese/trimestre)?</td> 
  </tr>
  <tr>
   <td>Tipo di rapporto</td> 
   <td>Punti di contatto lead e acquirenti (CRM)<br> 
   Metrica: lead ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Campo data / Tipo data</td> 
   <td>Data punto di contatto</td> 
  </tr>
  <tr>
   <td>Intervallo date</td> 
   <td><i>seleziona l’intervallo di date desiderato</i></td> 
  </tr>
  <tr>
   <td>Gruppo/Dimension</td> 
   <td>Canale di marketing (o più granulare)</td> 
  </tr>
  <tr>
   <td>Modelli ottimali*</td> 
   <td>*Questo rapporto non riguarda tanto la misurazione dell’origine dei lead con un modello di attribuzione, quanto piuttosto <i>numero totale di punti di contatto (quantità di ingaggio)</i>, inclusi quelli successivi al contatto per la creazione di lead. Il conteggio totale dei record di punti di contatto indicherebbe quali canali hanno registrato il maggior coinvolgimento come lead.</td> 
  </tr>
 </tbody>
</table>

**PROMEMORIA**: basare i rapporti sulla &quot;Data punto di contatto&quot; è il modo più riflessivo di comprendere le prestazioni di marketing durante un determinato intervallo di date. &quot;Data punto di contatto&quot; struttura il rapporto in un modo in cui l’attribuzione non è solo correlata al canale, alla campagna o al contenuto, ma mostra anche quando si è verificato il punto di contatto. Questo è il modo più efficace per capire quale coinvolgimento marketing si verificava in un determinato momento ed è anche il modo consigliato per misurare l’impatto del marketing rispetto alla spesa di marketing investita nello stesso periodo. Si consiglia di tenerne conto quando si esegue un’analisi della spesa di marketing o del ROI (vedere paragrafo 5.1).

**2. LEAD QUALIFICATI PER IL MARKETING CON PUNTI DI CONTATTO PER L’ACQUIRENTE**

Uno dei rapporti più comuni è incentrato non solo sui nuovi lead o sul coinvolgimento a livello di lead, ma più specificamente sui &quot;lead qualificati per il marketing&quot; (MQL). Esistono un paio di approcci diversi per quanto riguarda la generazione di rapporti sulle MQL, a seconda di cosa [!DNL Marketo Measure] funzionalità a cui hai accesso.

**2,1 | Lead qualificati per il marketing per canale (multi-touch)**

Questo approccio per misurare l’impatto del marketing sull’influenza degli MQL è essenzialmente una continuazione del rapporto &quot;Nuovi lead per canale di marketing&quot; (1.1), ma con i criteri aggiuntivi che i lead da misurare sono più specificamente MQL. Il modello di attribuzione a forma di U è ancora consigliato qui per identificare quali canali di marketing e contenuti generano Lead che sono quindi _probabile_ per diventare un MQL:

<table> 
 <tbody>
  <tr>
   <td>Domanda</td> 
   <td>Quali canali di marketing sono più adatti a generare nuovi lead che diventano <i>MQL</i>?</td> 
  </tr>
  <tr>
   <td>Tipo di rapporto</td> 
   <td>Punti di contatto lead e acquirenti (CRM)<br> 
   Metrica: lead ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filtri</td> 
   <td>MQL = true*<br>
   *<i>Le MQL possono essere definite in modo diverso a seconda dell’organizzazione. Assicurati che [!DNL Marketo Measure] Il report viene filtrato per MQL utilizzando gli stessi campi degli altri report basati su MQL. È necessario creare un filtro Segmento nello stesso modo per i rapporti sulle MQL in [!DNL Marketo Measure] Scopri.</i></td> 
  </tr>
  <tr>
   <td>Campo data / Tipo data</td> 
   <td>Data MQL (o equivalente) / Data di creazione ([!DNL Marketo Measure] Discover)<br> <i>La data di creazione del lead può essere utilizzata anche nei rapporti CRM se "Data MQL" non è un'opzione nel CRM. È importante tenere presente il campo data utilizzato in che definisce il set di dati coorte.</i></td> 
  </tr>
  <tr>
   <td>Intervallo date</td> 
   <td><i>seleziona l’intervallo di date desiderato</i></td> 
  </tr>
  <tr>
   <td>Gruppo/Dimension</td> 
   <td>Canale di marketing</td> 
  </tr>
  <tr>
   <td>Modelli ottimali</td> 
   <td>Primo contatto, Creazione di lead, <strong>A forma di U</strong><br> 
   SOMMA i campi "Conteggio" nei rapporti CRM (Conteggio - Primo contatto, Conteggio - Creazione lead, Conteggio - A forma di U)</td> 
  </tr>
 </tbody>
</table>

**2,2 | Marketing Qualified Leads by Channel (contatto singolo, solo CRM)**

Questo approccio per misurare l’impatto del marketing sull’influenza delle MQL si concentra maggiormente sull’identificazione di quali _punto di contatto singolo_ è stato l’ultimo contatto prima che il lead raggiungesse MQL.

>[!NOTE]
>
>Per eseguire questo report, è necessario un valore &quot;Stato lead&quot; di &quot;MQL&quot; per definire la fase MQL a scopo di tracciamento (fase funnel). Se non si tiene traccia degli MQL tramite il campo &quot;Stato lead&quot;, è necessaria la funzione Custom Attribution Model with Custom Stages per creare uno stadio &quot;MQL&quot; personalizzato in [!DNL Marketo Measure] Impostazioni account.

<table> 
 <tbody>
  <tr>
   <td>Domanda</td> 
   <td>Quali canali di marketing sono più efficaci nel spingere i lead per raggiungere lo stato MQL?</td> 
  </tr>
  <tr>
   <td>Tipo di rapporto</td> 
   <td>Punti di contatto lead e acquirenti (CRM)<br>
   <i>questo rapporto è possibile solo all’interno del reporting CRM. Non è possibile filtrare alcuni valori di "Posizione punto di contatto" in [!DNL Marketo Measure] Scoprire</i></td> 
  </tr>
  <tr>
   <td>Filtri</td> 
   <td><strong>La posizione del punto di contatto CONTIENE "MQL"</strong></td> 
  </tr>
  <tr>
   <td>Campo data / Tipo data</td> 
   <td>Data MQL (o equivalente)</td> 
  </tr>
  <tr>
   <td>Intervallo date</td> 
   <td><i>seleziona l’intervallo di date desiderato</i></td> 
  </tr>
  <tr>
   <td>Gruppo/Dimension</td> 
   <td>Canale di marketing</td> 
  </tr>
  <tr>
   <td>Modelli ottimali</td> 
   <td><i>Poiché questo rapporto viene filtrato su un singolo punto di contatto, i modelli di attribuzione a livello di lead non sono così rilevanti. Come nel "Rapporto sul coinvolgimento del lead" (1.4), anche in questo caso viene utilizzato il numero di record dei punti di contatto per capire quali canali sono più forti (ogni lead avrebbe un solo punto di contatto MQL).</i></td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Esplora altri raggruppamenti o dimensioni per ottenere informazioni aggiuntive sugli MQL. Come menzionato negli altri rapporti &quot;Lead con punti di contatto dell’acquirente&quot;, il punto di contatto dell’acquirente offre una granularità molto maggiore rispetto al solo canale di marketing. Un rapporto basato su &quot;Contenuto&quot; può anche essere combinato con uno dei rapporti MQL riportati sopra per comprendere meglio quale contenuto influenzi al meglio gli MQL.

**3. [!DNL MARKETO MEASURE] PERSONE CON PUNTI DI CONTATTO ACQUIRENTE**

C&#39;è una terza personalizzazione [!DNL Marketo Measure] oggetto in Salesforce che può essere molto utile quando si generano rapporti su metriche relative alle persone: **il [!DNL Marketo Measure] Persona (BP)**. BP risolve il vecchio problema di come rappresentare le informazioni di lead e contatti nello stesso rapporto. Unisce tutti i BT relativi a una &quot;persona&quot; (un [!DNL Marketo Measure] L’ID della persona è il suo indirizzo e-mail). Indipendentemente dal fatto che esistano come lead o contatto, la BP funge da oggetto ponte per aiutare i rapporti a estendersi a lead e contatto ed è molto utile per produrre rapporti più sofisticati sulle persone.

Il [!DNL Marketo Measure] La persona fa riferimento a uno solo degli oggetti punto di contatto, il punto di contatto dell’acquirente (BT). Questo significa che non può essere utilizzato per un’opportunità o per metriche relative ai ricavi. A &#39;[!DNL Marketo Measure] Il tipo di rapporto Punti di contatto per persona e acquirente è ottimo per la comprensione _coinvolgimento totale_ in quanto mette in evidenza tutti i BT, indipendentemente dal fatto che si riferisca più specificamente a un lead o a un contatto. Ad esempio, se utilizzi una campagna Salesforce per tenere traccia di un evento, all’interno della campagna CRM potrebbero essere presenti membri della campagna come lead o contatti. [!DNL Marketo Measure] creerà punti di contatto per i membri della campagna indipendentemente, ma senza [!DNL Marketo Measure] Persona, la generazione di rapporti standard di Salesforce richiederebbe due rapporti separati per capire quanti _totale_ Punti di contatto dell’Evento: uno &quot;Leads with Buyer Touchpoints&quot; (Lead con punti di contatto dell’acquirente) e uno &quot;Contatti con punti di contatto dell’acquirente&quot;. Qualche altro [!DNL Marketo Measure] Di seguito sono elencati i casi di utilizzo dei rapporti basati su persona:

**3,1 [!DNL Marketo Measure] Persone che hanno scaricato &#39;ebook&#39; o &#39;white paper&#39; (download totali)**

Questo rapporto equivale a un rapporto basato su &quot;Contenuto&quot; a livello di lead. Tuttavia, invece di cercare di misurare il numero di lead attribuibili a ogni elemento di contenuto, utilizzando un [!DNL Marketo Measure] Il rapporto Persone sarà utile per comprendere il totale _numero di download_ se la risorsa è gestita (il numero totale di punti di contatto rappresenterebbe il numero totale di download/invii di moduli).

<table> 
 <tbody>
  <tr>
   <td>Domanda</td> 
   <td>Quante persone hanno scaricato una particolare risorsa?</td> 
  </tr>
  <tr>
   <td>Tipo di rapporto</td> 
   <td>[!DNL Marketo Measure] Punti di contatto per persone e acquirenti (CRM)</td> 
  </tr>
  <tr>
   <td>Filtri</td> 
   <td>'URL modulo' CONTIENE (ad esempio)<br>
   <li>/ebook</li>
   <li>/whitepaper</li>
   <i>I valori del filtro riportati sopra sono solo esempi. Il valore effettivo sarà basato sulla struttura URL di ogni organizzazione.</i></td> 
  </tr>
  <tr>
   <td>Campo data / Tipo data</td> 
   <td>Data punto di contatto <i>(quando è stata scaricata la risorsa)</i></td> 
  </tr>
  <tr>
   <td>Intervallo date</td> 
   <td><i>seleziona l’intervallo di date desiderato</i></td> 
  </tr>
  <tr>
   <td>Gruppo/Dimension</td> 
   <td>URL modulo</td> 
  </tr>
  <tr>
   <td>Modelli ottimali</td> 
   <td>Questo rapporto non riguarda tanto la misurazione dell’origine dei lead o dei contatti con un modello di attribuzione, quanto piuttosto <i>numero totale di punti di contatto (quantità di ingaggio)</i>, inclusi quelli successivi al contatto per la creazione di lead. Con questo rapporto cerchiamo di capire <i>quantità di coinvolgimento totale</i>. Il conteggio totale dei record dei punti di contatto indica le risorse più scaricate.</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Per qualsiasi lead con [!DNL Marketo Measure] Tipo di rapporto delle persone, inizia personalizzando il rapporto predefinito con titolo &quot;**[!DNL Marketo Measure]101 | Lead/contatti per canale**&quot;. Questo rapporto è disponibile come standard ed è un ottimo [!DNL Marketo Measure] Sandbox basata su persone. È predefinito e può essere personalizzato rapidamente per esigenze di reporting più specifiche.

>[!TIP]
>
>Puoi utilizzare questo rapporto per ottenere informazioni sul coinvolgimento totale di qualsiasi dimensione di marketing dall’oggetto punto di contatto acquirente, non solo sui download di contenuto come illustrato nell’esempio. Il rapporto può invece essere raggruppato o filtrato in base a dimensioni quali &quot;Canale di marketing&quot; o &quot;Nome campagna annuncio&quot; per comprendere al meglio il coinvolgimento totale sia dei lead che dei contatti nel database. Cambia i filtri o i raggruppamenti all’interno del rapporto a zero in altre dimensioni rappresentate da altri campi dell’oggetto punto di contatto.

**3,2 [!DNL Marketo Measure] Persone che si sono registrate per un evento (solo CRM)**

_Questo rapporto è applicabile solo se i moduli di registrazione sono ospitati su siti Web che [!DNL Marketo Measure] è in grado di tenere traccia digitalmente._

<table> 
 <tbody>
  <tr>
   <td>Domanda</td> 
   <td>Quali canali di marketing sono più determinanti per la registrazione agli eventi?</td> 
  </tr>
  <tr>
   <td>Tipo di rapporto</td> 
   <td>[!DNL Marketo Measure] Punti di contatto per persone e acquirenti (CRM)</td> 
  </tr>
  <tr>
   <td>Filtri</td> 
   <td>'URL modulo' CONTIENE (ad esempio)<br>
   <li>/event</li>
   <i>Il valore del filtro riportato sopra è solo esemplificativo. Il valore effettivo sarà basato sulla struttura URL di ogni organizzazione.</i></td> 
  </tr>
  <tr>
   <td>Campo data / Tipo data</td> 
   <td>Data punto di contatto <i>(quando è stato inviato il modulo di registrazione)</i></td> 
  </tr>
  <tr>
   <td>Intervallo date</td> 
   <td><i>seleziona l’intervallo di date desiderato</i></td> 
  </tr>
  <tr>
   <td>Gruppo/Dimension</td> 
   <td>URL modulo<br>
   Canale di marketing</td> 
  </tr>
  <tr>
   <td>Modelli ottimali</td> 
   <td>Questo rapporto non riguarda tanto la misurazione dell’origine dei lead o dei contatti con un modello di attribuzione, quanto piuttosto <i>numero totale di punti di contatto (numero di registrazioni)</i>, inclusi quelli successivi al contatto per la creazione di lead. Con questo report vogliamo ottenere informazioni approfondite sulle principali registrazioni di eventi. Il conteggio totale dei record di punti di contatto per "Canale di marketing" rifletterebbe quali canali hanno registrato il maggior numero di registrazioni.</td> 
  </tr>
 </tbody>
</table>

Il vantaggio principale di questo rapporto è che i dati dei punti di contatto dell’acquirente forniranno anche i dati del canale di marketing. Anche se potresti avere già informazioni sul numero di persone che si sono registrate per i tuoi eventi, questo rapporto fornirà anche informazioni su quali canali di marketing digitale, origini e/o campagne stanno portando le persone sul tuo sito web per poi registrarsi all’evento.

>[!TIP]
>
>Lo stesso approccio può essere utilizzato quando si desidera ottenere informazioni approfondite sulle registrazioni di webinar o sui download di webinar on-demand (se si tratta di una risorsa gestita). L’unica differenza consiste nel valore del filtro in &quot;URL modulo&quot; se tali moduli sono ospitati su pagine univoche del sito web. L&#39;obiettivo è comunque lo stesso. Risponde alle domande, &quot;quali dei miei canali di marketing sono più determinanti per il maggior numero di registrazioni/download di webinar on-demand.

**3,3 [!DNL Marketo Measure] Persone con punti di contatto dell&#39;acquirente (convalida punti di contatto)**

Considerando [!DNL Marketo Measure] Persona consente di creare rapporti su tutti i punti di contatto in un singolo rapporto, è il tipo di rapporto ideale da utilizzare quando si cercano di convalidare i dati. Vogliamo assicurarci di non trascurare i punti di contatto che potrebbero rivelare dove, ad esempio, si verifica un problema nella configurazione dei tuoi &quot;Canali di marketing&quot; (consulta gli articoli di supporto collegati di seguito per ulteriori informazioni sulla configurazione dei tuoi &quot;Canali di marketing&quot;).

* [Impostazione canale personalizzato online](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
* [Impostazione canale personalizzato offline](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)

In sostanza, i dati del punto di contatto rifletteranno ciò che è stato tracciato da [!DNL Marketo Measure] e possono essere controllati per garantire che la configurazione corrisponda agli input in base a elementi come: valori dei parametri UTM, pagine di riferimento o tipi di campagna. Se i dati del punto di contatto non corrispondono alla configurazione, è probabile che sia necessario apportare delle modifiche. Oltre alla configurazione &quot;Canale di marketing&quot;, puoi esaminare i dati dei punti di contatto per determinare quali potrebbero essere i punti di contatto [soppresso](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md) o [segmentato](/help/advanced-marketo-measure-features/segmentation/custom-segmentation.md). Si consiglia di controllare i dati del punto di contatto all’interno di un’[!DNL Marketo Measure] Il rapporto Punti di contatto per persone e acquirenti alla fine di ogni mese o trimestre, se possibile. In questo modo l’attribuzione sarà il più accurata possibile. L&#39;&#39;[!DNL Marketo Measure] 101 | Il rapporto Lead/Contatti per canale, disponibile da subito, rappresenta un ottimo punto di partenza. Includi i campi seguenti, se non sono già inclusi, per rivedere alcune delle parti più importanti della configurazione:

* **Canale di marketing** - Percorso = Marketing Channel.Subchannel (valori impostati in [!DNL Marketo Measure])
* **Sorgente punto di contatto** = utm_source
* **Medio** = utm_medium (punti di contatto online) O tipo di campagna CRM (punti di contatto offline)
* **Pagina referrer** (utilizzato con la configurazione &quot;Canali online&quot;)
* **Pagina di destinazione - Raw** (utilizzato nella configurazione &quot;Canali online&quot;) è anche un input comune per la soppressione dei punti di contatto nella scheda &quot;Impostazioni punto di contatto&quot; delle impostazioni.
* **URL modulo** (un input comune per la soppressione dei punti di contatto nella scheda Impostazioni punto di contatto delle impostazioni)

**PUNTO DI CONTATTO ATTRIBUZIONE ACQUIRENTE (BAT)**

I punti di contatto di attribuzione dell’acquirente (BAT) rappresentano i punti di contatto rilevanti di tutti i contatti connessi all’opportunità (tramite i ruoli di contatto dell’opportunità o tramite un ID account condiviso, a seconda delle impostazioni). A differenza delle BT (che sono principalmente collegate alle persone), le BAT possono essere associate ai ricavi. In quanto tale, è possibile utilizzare le BAT per rispondere a domande relative alle opportunità, principalmente aperte _Opportunità/Ricavi pipeline_ e won chiuso _Opportunità/Offerte/Ricavi_. Una BAT viene creata tramite i record BT di un contatto non appena viene creata un&#39;opportunità con lo stesso account del contatto (il BT non viene convertito in una BAT. I dati BT sono semplicemente referenziati per creare un record aggiuntivo (la BAT che poi si riferisce all&#39;opportunità).

Il punto di contatto per l’attribuzione dell’acquirente ci consente di misurare l’impatto del marketing più a fondo nel funnel. _La profondità del funnel in cui desideri misurare può essere rappresentata dai vari modelli di attribuzione multi-touch_.

Considerando che la relazione principale delle BAT è con l’opportunità, esse vengono utilizzate per rispondere a domande quali:

* Quale delle mie attività di marketing ha influenzato il maggior numero di opportunità?
* Quanti nuovi ricavi della pipeline posso attribuire a ciascuno dei miei canali di marketing?
* Quale delle mie campagne ha registrato il ROI più elevato lo scorso trimestre?

Il [modelli di attribuzione](/help/introduction-to-marketo-measure/overview-resources/marketo-measure-attribution-models.md) per ottenere informazioni approfondite sulle metriche basate su opportunità:

**A forma di W** - L’_Modello di pipeline_&quot;. Nel modello a forma di W sono inclusi tre punti di contatto milestone. In questo modello, i punti di contatto FT, LC e OC vengono attribuiti a ciascuno il 30% del credito di attribuzione. Il restante 10% è attribuito ugualmente a qualsiasi punto di contatto intermedio che si verifica tra i tre punti di contatto milestone.

<table> 
 <tbody>
  <tr>
   <td><img src="assets/bizible-reporting-guide-2.png"></td> 
   <td>Questo modello riassume essenzialmente il percorso di una nuova opportunità, che in genere è sinonimo di generazione di nuovi ricavi della pipeline.<p>
   <p>
   Per misurare l’impatto del marketing sulle nuove opportunità o sulla generazione di nuove pipeline, si consiglia di utilizzare il modello a forma di W.</td> 
  </tr>
 </tbody>
</table>

**Percorso completo** - L’_Modello vinto chiuso_&quot;. Questo modello include i quattro punti di contatto milestone: FT, LC, OC e Closed. A ciascuno è assegnato il 22,5% del credito Opportunity e il restante 10% è distribuito equamente tra i contatti intermediari.

<table> 
 <tbody>
  <tr>
   <td><img src="assets/bizible-reporting-guide-3.png"></td> 
   <td>Questo modello riassume essenzialmente il percorso di un'operazione di vincita chiusa, che in genere è sinonimo di ricavi/prenotazioni di vincita chiusa.<p>
   <p>
   Quando si cerca di misurare l’impatto del marketing sulle opportunità di vendita realizzate o sui ricavi ottenuti, si consiglia il modello a percorso completo.</td> 
  </tr>
 </tbody>
</table>

Questo modello riassume essenzialmente il percorso di un&#39;operazione di vincita chiusa, che in genere è sinonimo di ricavi/prenotazioni di vincita chiusa.

Quando si cerca di misurare l’impatto del marketing sulle opportunità di vendita realizzate o sui ricavi ottenuti, si consiglia il modello a percorso completo.

**Personalizzato** - [!DNL Marketo Measure] offre anche un modello di attribuzione personalizzata che consente agli utenti di scegliere quali punti di contatto o fasi personalizzate includere nel modello. Inoltre, gli utenti possono controllare la percentuale di credito di attribuzione attribuito a questi punti di contatto e stadi. A seconda dell’impostazione del modello personalizzato, può essere utilizzato in modo più appropriato per misurare le Opportunità e la Pipeline OPPURE, le Offerte e i Ricavi ottenuti con la chiusura. Tieni presente questo aspetto quando lo utilizzi nei rapporti.

>[!NOTE]
>
>Il modello di attribuzione personalizzato è una funzione aggiuntiva non disponibile per tutti i clienti. Per ulteriori informazioni su come aggiungere questa funzione al tuo account, contatta l’Adobe Account Team (il tuo Account Manager).

Di solito, gli esperti di marketing devono sapere &quot;da dove vengono le mie opportunità?&quot;. Analogamente al reporting a livello di lead, a questa domanda veniva risposto storicamente con un singolo valore unidimensionale (ad esempio Origine campagna principale). Tuttavia, sappiamo che nello sviluppo di un’opportunità c’è molto di più di un singolo punto di contatto da un singolo contatto. In genere sono presenti diversi punti di contatto provenienti da vari canali e da più soggetti interessati che influenzano un’opportunità nella creazione. Con [!DNL Marketo Measure], possiamo far emergere tutti i punti di contatto da un account per capire meglio da dove proviene un’opportunità. Oltre a questo, tuttavia, possiamo continuare a far emergere qualsiasi punto di contatto che si è verificato dopo la creazione dell’opportunità e fino al punto in cui l’opportunità viene chiusa. Questo ci permette non solo di adottare un approccio multi-touch per capire da dove proviene un&#39;opportunità, ma anche cosa l&#39;ha influenzata a chiudere e, in ultima analisi, a rappresentare un fatturato vinto chiuso. Questo offre approfondimenti su diverse domande come, &quot;qual è l’impatto del marketing sull’influenzare le trattative per chiuderle?&quot;, &quot;quale marketing determina ricavi vinti chiusi?&quot; e, in ultima analisi, &quot;a quale delle mie attività di marketing corrisponde il ROI più elevato?&quot;

## RAPPORTI CONSIGLIATI UTILIZZANDO IL PUNTO DI CONTATTO DI ATTRIBUZIONE ACQUIRENTE (BAT) {#recommended-reports-using-the-buyer-attribution-touchpoint}

**4,1 | Nuove opportunità per canale di marketing**

Riepilogare i dati dei punti di contatto di attribuzione acquirenti delle opportunità per il campo &quot;Canale di marketing&quot; è la visualizzazione di livello più alto che indica quali canali/tattiche stanno influenzando le nuove opportunità nella creazione. Strutturando questo rapporto su un &quot;Tipo di data&quot; = &quot;Data di creazione dell’opportunità&quot; si assicura che il rapporto venga riepilogato anche in base a quando l’opportunità è stata effettivamente creata nel CRM. I punti di contatto possono essere stati creati in un momento precedente, ma si riferiranno comunque alle opportunità create all’interno dell’intervallo di date definito e riceveranno quindi il credito di attribuzione in quanto vengono riconosciuti come influenti sull’opportunità.

<table> 
 <tbody>
  <tr>
   <td>Domanda</td> 
   <td>Cosa <i>canali di marketing</i> Influenzano le Opportunità nella creazione?</td> 
  </tr>
  <tr>
   <td>Tipo di rapporto</td> 
   <td>Punti di contatto di attribuzione acquirente con opportunità (CRM)<br> 
   Metrica: opportunità ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filtri</td> 
   <td>
   <li>Fase dell’opportunità* <i>(facoltativo a seconda delle opportunità specifiche che si desidera limitare al rapporto. È possibile creare rapporti solo sulle BAT ancora associate solo alle opportunità "aperte" (ad esempio)</i></li>
   <li>Tipo di opportunità (è comune filtrare in base a determinate opportunità, ad esempio "Nuova azienda" anziché <i>tutto</i> opportunità)</li><br>
   *Un filtro di segmento per il "Tipo di opportunità" deve essere utilizzato in [!DNL Marketo Measure] Scoprire</td> 
  </tr>
  <tr>
   <td>Campo data / Tipo data</td> 
   <td>Data di creazione dell’opportunità (CRM) / Data di creazione (Discover)</td> 
  </tr>
  <tr>
   <td>Intervallo date</td> 
   <td><i>seleziona l’intervallo di date desiderato</i></td> 
  </tr>
  <tr>
   <td>Gruppo/Dimension</td> 
   <td>Canale di marketing</td> 
  </tr>
  <tr>
   <td>Modelli ottimali</td> 
   <td><strong>A forma di W</strong><br>
   SOMMA i campi a forma di W nei rapporti CRM (Conteggio - A forma di W, Ricavi - A forma di W)</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Per qualsiasi tipo di rapporto &quot;Punti di contatto di attribuzione buyer con opportunità&quot;, inizia personalizzando il rapporto predefinito con titolo &quot;[!DNL Marketo Measure] 101 | Opportunità per canale&quot;. Questo rapporto è disponibile come standard, è un ottimo ambiente sandbox predefinito come descritto nella tabella precedente e può essere rapidamente personalizzato per esigenze di reporting più specifiche (il rapporto utilizza un modello predefinito di percorso completo; assicurati quindi di personalizzare il rapporto in modo da includere qualsiasi altro modello di attribuzione, in questo caso il modello a forma di W).

>[!TIP]
>
>Il rapporto descritto sopra sarebbe anche utilizzato quando si cerca di capire quanto valuta dovrebbe anche essere attribuita. Quando si effettua la generazione di rapporti a livello di opportunità utilizzando le BAT, è necessario riepilogare due metriche chiave: la valuta (la quantità di opportunità) e il record Opportunità stesso. Nell’esempio precedente, stiamo misurando in modo più specifico le opportunità aperte e i nuovi ricavi derivanti dalla pipeline.

>[!TIP]
>
>Ottieni informazioni ancora più dettagliate riepilogando il rapporto con altri campi disponibili dall’oggetto punto di contatto di attribuzione buyer. Questa operazione viene eseguita nello stesso modo in cui è stata eseguita a livello di lead con i punti di contatto dell’acquirente (1.2). Per farlo, aggiungi ulteriori raggruppamenti (CRM) o dimensioni (Discover). A seconda del canale (che può essere rappresentativo del tuo ruolo), ci possono essere ulteriori dettagli oltre al livello della campagna in cui desideri ottenere ulteriori informazioni. Di seguito viene fornita un&#39;analisi della ricerca a pagamento:

<table> 
 <tbody>
  <tr>
   <td>Domanda</td> 
   <td>Quale <i>parole chiave</i> I miei annunci di ricerca a pagamento generano la maggior parte dei ricavi della pipeline?
</td> 
  </tr>
  <tr>
   <td>Tipo di rapporto</td> 
   <td>Punti di contatto di attribuzione acquirente con opportunità (CRM)<br> 
   Metrica: opportunità ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filtri</td> 
   <td>
   <li>Canale di marketing = ricerca a pagamento</li>
   <li>Fase dell’opportunità* <i>(facoltativo a seconda delle opportunità specifiche che si desidera limitare al rapporto. Questo esempio si basa sui Ricavi della pipeline definiti in [!DNL Marketo Measure] Opportunità "aperte" (che rappresentano potenziali ricavi/pipeline aperta)</i></li>
   <li>Tipo di opportunità (è comune filtrare in base a determinate opportunità, ad esempio "Nuova azienda" anziché <i>tutto</i> opportunità)</li><br>
   *Un filtro di segmento per il "Tipo di opportunità" deve essere utilizzato in [!DNL Marketo Measure] Scoprire</td> 
  </tr>
  <tr>
   <td>Campo data / Tipo data</td> 
   <td>Data di creazione dell’opportunità</td> 
  </tr>
  <tr>
   <td>Intervallo date</td> 
   <td><i>seleziona l’intervallo di date desiderato</i></td> 
  </tr>
  <tr>
   <td>Gruppo/Dimension</td> 
   <td>Testo parola chiave (CRM)<br> 
   Parola chiave (Discover)</td> 
  </tr>
  <tr>
   <td>Modelli ottimali</td> 
   <td><strong>A forma di W</strong><br>
   SOMMA i campi a forma di W nei rapporti CRM (Conteggio - A forma di W, Ricavi - A forma di W)</td> 
  </tr>
 </tbody>
</table>

**4,2 | Offerte per canale di marketing**

Questo rapporto è essenzialmente lo stesso del primo esempio di punto di contatto per l’attribuzione dell’acquirente (4.1), tranne per il fatto che ora la metrica è cambiata da Opportunità aperte a Offerte concluse. La metrica dovrebbe sempre essere quella che informa su quale modello di attribuzione utilizzare. Considerando che stiamo esaminando le offerte chiuse e le relative BAT, dovremmo utilizzare un modello che rappresenti l&#39;intero percorso dell&#39;acquirente (offerta). In questo modo, durante il percorso dell’acquirente, viene garantita la tracciabilità dei contatti di marketing che ricevono il credito di attribuzione:

<table> 
 <tbody>
  <tr>
   <td>Domanda</td> 
   <td>Cosa <i>canali di marketing</i> Influenzare la chiusura degli accordi?</td> 
  </tr>
  <tr>
   <td>Tipo di rapporto</td> 
   <td>Punti di contatto di attribuzione acquirente con opportunità (CRM)<br> 
   Metrica: offerte ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filtri</td> 
   <td>
   <li>Fase dell’opportunità (<i>solo le opportunità acquisite chiuse devono essere incluse nel rapporto</i>) OPPURE,</li>
   <li>Opportunità acquisita = True</li>
   <li>Tipo di opportunità (è comune filtrare in base a determinate opportunità, ad esempio "Nuova azienda" anziché tutte)<br>
   </td> 
  </tr>
  <tr>
   <td>Campo data / Tipo data</td> 
   <td>Data di chiusura dell’opportunità</td> 
  </tr>
  <tr>
   <td>Intervallo date</td> 
   <td><i>seleziona l’intervallo di date desiderato</i></td> 
  </tr>
  <tr>
   <td>Gruppo/Dimension</td> 
   <td>Canale di marketing</td> 
  </tr>
  <tr>
   <td>Modelli ottimali</td> 
   <td><strong>Percorso completo</strong><br>
   SOMMA i campi "Percorso completo" nei rapporti CRM (Conteggio - Percorso completo, Ricavi - Percorso completo)</td> 
  </tr>
 </tbody>
</table>

**PROMEMORIA**: è fondamentale ricordarsi di filtrare le opportunità specifiche che si desidera includere nei rapporti basati sulle BAT, soprattutto quando si tratta di &quot;Opportunità aperte e ricavi da pipeline&quot; rispetto a &quot;Offerte e ricavi da acquisto chiusi&quot;. Questa operazione viene in genere eseguita tramite un filtro &quot;Fase opportunità&quot; (il filtro &quot;Opportunità vinta&quot; = true/false può essere molto utile anche qui).

**5. ROI ([!DNL Marketo Measure] Solo individuazione)**

Il [!DNL Marketo Measure] Scopri le dashboard per ottenere una visione di alto livello delle prestazioni di marketing con [!DNL Marketo Measure] dati di attribuzione. Queste dashboard aggregate forniscono dati chiave sulla spesa di marketing e sul ROI che non sono disponibili nei rapporti CRM. Questo ambiente predefinito consente di visualizzare le prestazioni di marketing in linea con i dati sul ROI, consentendo di prendere decisioni fruibili per quanto riguarda il marketing.

>[!TIP]
>
>Quando hai domande relative a ROI, Spesa o Costo, [!DNL Marketo Measure] Scopri sarà il posto migliore per la generazione di rapporti!

Il [!DNL Marketo Measure] Le dashboard di individuazione sono composte dai dati dei punti di contatto di attribuzione acquirente e Acquirente e dai dati CRM chiave. La differenza principale tra reporting CRM e reporting in [!DNL Marketo Measure] Scopri che i dati dei punti di contatto in Discover sono presentati di più in modo &quot;aggregato&quot; e riepilogati per dimensione (canale di marketing, campagna, ecc.) al contrario dei singoli record dei punti di contatto che possono quindi essere riepilogati. [!DNL Marketo Measure] Discover è utilizzato per capire ad alto livello quale dei tuoi sforzi sta avendo il maggior impatto su lead, opp, offerte e quanto reddito dovrebbe essere attribuito a loro. Una volta calcolati i ricavi attribuiti tramite i vari modelli di attribuzione (si consiglia il percorso completo per l’attribuzione di ricavi/prenotazioni acquisiti chiusi), possiamo misurarli in base a quanto è stato speso nella stessa dimensione (Canale di marketing, Sottocanale o Campagna). Questo ci dà la **ROI**.

>[!TIP]
>
>Una delle cose più importanti da ricordare quando si crea un rapporto in Discover è il tipo di dati che si sta utilizzando per filtrare. Tipo di data determinerà quale set di dati [!DNL Marketo Measure] sta utilizzando nelle varie tessere.

* **Data punto di contatto**: visualizza i dati correlati con una &quot;Data punto di contatto&quot; nell’arco temporale specificato
* **Data di creazione**: visualizza i dati correlati con una &quot;Data di creazione&quot; nell’intervallo di tempo specificato
* **Data di chiusura**: visualizza i dati correlati con una &quot;Data di chiusura&quot; nell’arco temporale specificato

Quando si segnala il ROI in [!DNL Marketo Measure] Scopri, si consiglia di utilizzare un &quot;Tipo di data&quot; = &quot;Data punto di contatto&quot;. Per determinare il rendimento di ogni dollaro investito, dobbiamo assicurarci che il ricavo venga attribuito alla data in cui è stato effettuato l’investimento. &#39;Tipo di data&#39; = &quot;Data punto di contatto&quot; assicura che i rapporti siano strutturati in questo modo, anziché in base a quando l&#39;opportunità è stata creata (Data creazione) o chiusa (Data chiusura). Diamo un’occhiata più da vicino:

I filtri evidenziati di seguito sono fondamentali per un rapporto incentrato sul ROI in [!DNL Marketo Measure] (molto probabilmente imposterai questi filtri nelle schede &quot;Panoramica&quot;, &quot;CMO&quot; o &quot;ROI&quot;):

**5,1 | ROI nella scheda &quot;Panoramica&quot;**

![](assets/bizible-reporting-guide-4.png)

L’intervallo &quot;Date&quot; (Data) non solo imposta la coorte dei punti di contatto (per Data punto di contatto) che ricevono l’attribuzione, ma definisce anche l’intervallo rappresentato dalla sezione o dalle colonne &quot;Spesa&quot;.
[!DNL Marketo Measure] osserva semplicemente l’intervallo di date per determinare quanto è stato speso in totale oppure a livello di canale di marketing, sottocanale o campagna Vedi di seguito:

![](assets/bizible-reporting-guide-5.png)

La schermata precedente mostra i dati sulla spesa di marketing negli ultimi 3 mesi completi. In questo esempio, sono stati spesi $ 12.970 per tutti i canali. Questo numero è composto dai dati della spesa di marketing [!DNL Marketo Measure] proviene dalle integrazioni con uno qualsiasi degli account degli annunci collegati (Google AdWords, Bing Ads, Facebook Ads, LinkedIn, DoubleClick) ed eventuali spese di marketing aggiuntive che sono state caricate all’interno dell’account o estratte automaticamente dai record di una campagna nel CRM. L’esempio mostra anche quanto &quot;Entrate&quot; vinto chiuso può essere attribuito anche ai punti di contatto che si sono verificati durante lo stesso intervallo di date (caselle verdi). Questo è il modo in cui viene calcolato il ROI: ricavi attribuiti ai punti di contatto provenienti dall’investimento nello stesso intervallo di date:

![](assets/bizible-reporting-guide-6.png)

**PROMEMORIA**: [!DNL Marketo Measure] definisce &quot;Ricavi&quot; come ricavi o prenotazioni vinti chiusi e definisce &quot;Ricavi pipeline&quot; come _ricavi potenziali/aperti da opportunità aperte_.

Un altro importante vantaggio dal rapporto sul ROI di cui sopra è il &quot;Ricavo della pipeline&quot; rappresentato all’interno della casella rossa. Ciò significa che dai 12.970 dollari investiti negli ultimi 3 mesi completi, attualmente stiamo attribuendo 705.199 dollari di &#39;Entrate&#39; realizzate e chiuse, ma stiamo anche attribuendo 6.905.532 dollari di entrate potenziali aperte (&#39;Entrate della pipeline&#39;) ai punti di contatto creati dallo stesso investimento! Ciò che ci aspetteremmo di vedere è una porzione del &quot;Ricavo della pipeline&quot; vicino nel tempo, che alimenta il numero &quot;Ricavo&quot;, e quindi, il numero del ROI aumenterebbe nel tempo. Il numero di &quot;Spesa&quot; è fisso perché non è possibile tornare indietro nel tempo per spendere di più negli ultimi 3 mesi completi. Questo è l’importanza di utilizzare un &quot;Tipo di data&quot; di &quot;Data punto di contatto&quot; all’interno di qualsiasi reporting sul ROI: definisce l’importo (**I**) investito e garantisce l&#39;importo di (**R**)le entrate attribuite sono attribuite agli stessi punti di contatto che sono stati ottenuti dall’investimento (per ogni dollaro speso, quanto è stato fatto?).

>[!TIP]
>
>Puoi filtrare in base a canali di marketing, sottocanali e/o campagne in cui sai che i dati sulla spesa di marketing sono completi e precisi. L’esempio precedente si riferisce a tutti i canali di marketing, ma se in alcuni canali non vengono caricati i dati relativi alla spesa di marketing, la generazione di rapporti sul ROI potrebbe non essere accurata. Vedi l’esempio seguente, questa volta nella bacheca &quot;ROI&quot; che si concentra sulle campagne all’interno del canale di marketing di &quot;Paid Search&quot;, un canale con dati molto granulari sulla spesa di marketing tramite le integrazioni.

![](assets/bizible-reporting-guide-7.png)
