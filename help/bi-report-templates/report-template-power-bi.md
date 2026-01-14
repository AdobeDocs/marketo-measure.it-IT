---
description: Modello di report [!DNL Marketo Measure] - Power BI - [!DNL Marketo Measure]
title: Modello di report [!DNL Marketo Measure] - Power BI
exl-id: c296b8f9-4033-4723-9a71-63a458640d27
feature: Reporting
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '2526'
ht-degree: 0%

---

# Modello di report [!DNL Marketo Measure] - Power BI {#marketo-measure-report-template-power-bi}

## Guida introduttuva {#getting-started}

È possibile accedere al modello di report di Power BI [qui](https://github.com/adobe/Marketo-Measure-BI-Templates){target="_blank"}.

Aprire il file Power BI del modello di reporting di Adobe [!DNL Marketo Measure].

![](assets/marketo-bi-1.png)

È possibile trovare informazioni specifiche su server, warehouse e schema nell&#39;interfaccia utente [!DNL Marketo Measure] nella pagina delle informazioni di [!DNL Data Warehouse]. Le istruzioni per individuare questa pagina sono dettagliate [qui](/help/marketo-measure-data-warehouse/data-warehouse-access-reader-account.md){target="_blank"}.

I parametri QueryFilterStartDate e QueryFilterEndDate vengono utilizzati per limitare la quantità di dati importati. Questi parametri devono essere in formato SQL come vengono utilizzati nelle query inviate a [!DNL Snowflake]. Ad esempio, se si desidera limitare i dati agli ultimi due anni, QueryFilterStartDate sarà `dateadd` (anno,-2,current_date()). Questi parametri vengono confrontati con i tipi di dati datetime, pertanto si consiglia di utilizzare `dateadd` (day,1,current_date()) per QueryFilterEndDate per restituire tutti i dati all&#39;ora corrente.

## Connessione dati {#data-connection}

I parametri immessi all&#39;apertura del file vengono utilizzati per strutturare le query native che importano tabelle dal data warehouse. È comunque necessario impostare una connessione dati all&#39;istanza [!DNL Snowflake]. A questo scopo, è necessario disporre degli stessi nomi di server e warehouse insieme al nome utente e alla password. I dettagli su dove trovare il tuo nome utente e reimpostare la password, se necessario, sono documentati [qui](/help/marketo-measure-data-warehouse/data-warehouse-access-reader-account.md){target="_blank"}.

## Importazione dati {#data-import}

Per migliorare le prestazioni dei report e sfruttare le funzionalità di trasformazione di Power Query, impostare questo modello utilizzando il metodo di archiviazione di importazione.

### Parametri di query {#query-parameters}

Per limitare i dati importati nel modello, ogni tabella viene impostata utilizzando una query nativa come origine. Per eseguire le query native è necessaria l’approvazione, è necessario fare clic su Esegui per ogni query. Questo passaggio è necessario solo la prima volta che vengono eseguite le query o se i parametri cambiano.

![](assets/marketo-bi-2.png)

Tutte le query escludono le righe eliminate e le tabelle [!UICONTROL facts] sono impostate per filtrare le righe con una data di modifica compresa tra le date di inizio e di fine immesse come parametri.

>[!NOTE]
>
>Poiché i filtri di data vengono applicati alla data modificata di una riga, presta attenzione quando esegui rapporti su date che non rientrano nell’intervallo di date limitato. Ad esempio, l’intervallo di date modificato è limitato agli ultimi due anni. Può includere un evento con una data evento di tre anni fa, ma che è stato modificato di recente. Tuttavia, la segnalazione degli eventi di tre anni fa restituisce risultati incompleti, in quanto non tutte le righe sono state modificate nell’intervallo di tempo di due anni.

![](assets/marketo-bi-3.png)

Le tabelle seguenti sono trattate come tabelle dei fatti; i limiti di data della data di modifica sono stati aggiunti a queste query.

* Attività
* Punto di contatto
* Punto di contatto lead
* Punto di contatto di attribuzione
* Costo
* Modulo sito
* Session
* Membro della campagna
* Attività
* Evento
* Transizione fase lead/contatto
* Transizione fase opportunità

Le tabelle seguenti vengono trattate come tabelle dimensione; per queste query non vengono impostati limiti di data.

* Account
* Campaign
* Contatto
* Tasso di conversione
* Opportunità
* Lead
* Fase
* Channel

## Trasformazioni dati {#data-transformations}

Sono state applicate alcune trasformazioni ai dati in Power Query. Per visualizzare le trasformazioni specifiche di una tabella, aprire Power Query, passare a una tabella e annotare i passi applicati sul lato sinistro della finestra. Alcune delle trasformazioni specifiche sono descritte di seguito.

![](assets/marketo-bi-6.png)

### Colonne rimosse {#removed-columns}

Per semplificare il modello dati e rimuovere i dati ridondanti e non necessari, è stato ridotto il numero di colonne importate in Power BI dalla tabella [!DNL Snowflake] originale. Le colonne rimosse includono chiavi esterne non necessarie, dati dimensionali denormalizzati meglio applicati tramite relazioni ad altre tabelle nel modello, colonne di controllo e campi utilizzati per l&#39;elaborazione interna di [!DNL Marketo Measure]. Puoi aggiungere o rimuovere colonne in base alle tue esigenze aziendali. Passa al passaggio &quot;Altre colonne rimosse&quot; dopo il passaggio &quot;Source&quot; in una tabella, fai clic sull’icona a forma di ingranaggio e aggiorna le colonne selezionate nell’elenco fornito.

>[!NOTE]
>
>* Presta attenzione quando aggiungi ulteriori valori di chiave esterna. Power BI è spesso impostato per rilevare automaticamente le relazioni nel modello e l’aggiunta di valori di chiave esterna può causare collegamenti indesiderati tra tabelle e/o la disabilitazione delle relazioni esistenti.
>
>* La maggior parte delle tabelle del data warehouse [!DNL Marketo Measure] contiene dati dimensionali denormalizzati. Abbiamo lavorato per normalizzare e ripulire il modello in Power BI il più possibile per migliorare le prestazioni e la precisione dei dati. Prestare attenzione quando si includono campi denormalizzati aggiuntivi nelle tabelle dei fatti. Questo può interrompere il filtro dimensionale tra le tabelle e può inoltre causare rapporti non accurati.


![](assets/marketo-bi-7.png)

### Colonne rinominate {#renamed-columns}

Le tabelle e le colonne sono state rinominate per renderle più facili da usare e per standardizzare le convenzioni di denominazione. Per visualizzare le modifiche al nome della colonna, passare al passaggio &quot;Colonne rinominate&quot; dopo il passaggio &quot;Altre colonne rimosse&quot; in qualsiasi tabella.

![](assets/marketo-bi-5.png)

### Segmenti rinominati {#renamed-segments}

Poiché i nomi dei segmenti sono personalizzabili, nel data warehouse di Snowflake dispongono di nomi di colonna generici. [!DNL BIZ_SEGMENT_NAMES] è una tabella di mappatura che elenca il nome del segmento generico e il nome del relativo segmento personalizzato mappato, definito nella sezione del segmento nell&#39;interfaccia utente [!DNL Marketo Measure]. La tabella Nome segmento viene utilizzata per rinominare le colonne del segmento nelle tabelle Punto di contatto lead e Punto di contatto attribuzione. Se non esiste alcun segmento personalizzato, viene mantenuto il nome del segmento generico.

![](assets/marketo-bi-4.png)

### Conversione ID sensibile a maiuscole e minuscole {#case-sensitive-id-conversion}

I dati [!DNL Marketo Measure] contengono alcune tabelle in cui i valori della chiave primaria (ID) fanno distinzione tra maiuscole e minuscole, ovvero punto di contatto e Campaign. Il motore dati che gestisce il livello di modellazione di Power BI non distingue tra maiuscole e minuscole, determinando quindi valori ID &quot;duplicati&quot;. Per mantenere la distinzione tra maiuscole e minuscole di questi valori chiave, sono stati implementati passaggi di trasformazione che associano caratteri invisibili ai caratteri minuscoli, mantenendo l’univocità dell’ID quando valutato nel livello del motore dati. Ulteriori dettagli sul problema e sui passaggi dettagliati sul metodo che abbiamo utilizzato sono disponibili [qui] (https://blog.crossjoin.co.uk/2019
/10/06/power-bi-and-case-sensitive/){target="_blank"}. Questi valori ID con distinzione tra maiuscole e minuscole sono etichettati come &quot;ID join&quot; e vengono utilizzati come chiavi di join nel livello di relazione. Abbiamo nascosto gli ID di unione dal livello di reporting, mantenendo i valori ID originali visibili per l’utilizzo nei rapporti, poiché i caratteri invisibili possono interferire con il taglio
/incolla funzioni e filtro.

![](assets/marketo-bi-8.png)

![](assets/marketo-bi-11.png)

### Righe aggiunte {#rows-added}

Per aggiungere le funzionalità di conversione della valuta ai calcoli nel modello, è stata aggiunta una colonna del tasso di conversione aziendale alle tabelle Opportunità e Costo. Il valore di questa colonna viene aggiunto a livello di riga e viene valutato unendo alla tabella Tasso di conversione sia la data che l&#39;ID valuta. Per ulteriori dettagli sul funzionamento della conversione di valuta in questo modello, consulta la sezione [Conversione valuta](#currency-conversion) in questa documentazione.

![](assets/marketo-bi-10.png)

La tabella Tasso di conversione archiviata in [!DNL Snowflake] contiene un intervallo di date per ogni conversione. Power BI non consente criteri di unione in un calcolo, ovvero tra un intervallo di date. Per eseguire il join di una data, sono stati aggiunti dei passaggi alla tabella Tasso di conversione per espandere le righe in modo da creare una riga per ogni data nell’intervallo di date di conversione.

![](assets/marketo-bi-9.png)

## Modello di dati {#data-model}

Fai clic sull’immagine seguente per la versione di dimensioni intere.

[![](assets/marketo-bi-12.png)](/help/bi-report-templates/assets/power-model-1.png){target="_blank"}

### Relazioni e flusso di dati {#relationships-and-data-flow}

I dati evento, utilizzati per la creazione dei punti di contatto, sono memorizzati nelle tabelle [!UICONTROL Session], [!UICONTROL Task], [!UICONTROL Event], [!UICONTROL Activity] e Membri della campagna. Queste tabelle degli eventi si uniscono alla tabella dei punti di contatto tramite i rispettivi ID e, se l’evento ha generato un punto di contatto, i dettagli vengono memorizzati nella tabella dei punti di contatto.

I punti di contatto lead e i punti di contatto di attribuzione vengono memorizzati in tabelle personalizzate, con un collegamento alla tabella dei punti di contatto. La maggior parte dei dati dimensionali per i punti di contatto di lead e attribuzione proviene dal collegamento al punto di contatto corrispondente.

In questo modello, le dimensioni Campaign e Canale sono collegate al punto di contatto, pertanto tutti i rapporti su tali dimensioni si basano su questo collegamento e indicano che il reporting dimensionale sui dati dell’evento può essere incompleto. Questo perché molti eventi non dispongono di collegamenti a queste dimensioni fino a quando non vengono elaborati in punti di contatto. Nota: alcuni eventi, come Sessioni, dispongono di collegamenti diretti alle dimensioni Campaign e Canale. Per generare rapporti a livello di sessione su queste dimensioni, si consiglia di creare un modello dati separato a questo scopo.

I dati relativi ai costi vengono memorizzati a diversi livelli di aggregazione nella tabella dei costi del data warehouse [!DNL Snowflake]. Per tutti i provider di annunci, è possibile eseguire il rollup dei dati a livello di campagna fino al livello di canale. Per questo motivo, questo modello richiama i dati dei costi in base al flag &quot;campaign_is_aggregatable_cost&quot;. I costi autodichiarati possono essere inviati solo a livello di canale e non è necessario che dispongano di dati di Campaign. Per fornire una dichiarazione dei costi il più accurata possibile, i costi autodichiarati vengono estratti in base al flag &quot;channel_is_aggregatable_cost&quot;. La query che importa i dati sui costi viene scritta con la seguente logica: Se ad_provider = &quot;SelfReported&quot; then channel_is_aggregatable_cost = true, else campaign_is_aggregatable_cost = true.

I dati dei costi e i dati dei punti di contatto hanno alcune dimensioni comuni, pertanto entrambe le tabelle dei fatti hanno relazioni con le tabelle delle dimensioni Campaign e Canale.

Nel contesto di questo modello, i dati [!UICONTROL Lead], [!UICONTROL Contact], [!UICONTROL Account] e [!UICONTROL Opportunity] sono considerati dati dimensionali e uniti direttamente alle tabelle dei punti di contatto [!UICONTROL Lead] e dei punti di contatto [!UICONTROL Attribution].

### Tabelle aggiunte {#added-tables}

**Data**

Poiché Power BI consente solo le relazioni tra tabelle in una colonna, è stata aggiunta una tabella dimensione Data per facilitare il join necessario tra le tabelle contenenti gli importi (Opportunità e Costo) e la tabella Tasso di conversione. Consulta la sezione Conversione valuta per ulteriori dettagli sul calcolo delle conversioni di valuta in questo modello.

**Misure**

Tutte le misure sono state aggiunte a un’apposita tabella Misure. Non è collegato al modello, ma funge da posizione singola per memorizzare tutte le misure, per facilitarne l’utilizzo.

**Modello di attribuzione**

È stata aggiunta una tabella separata per memorizzare i nomi dei modelli di attribuzione. Questa tabella viene utilizzata per creare filtri che consentono all’utente di passare da un modello di attribuzione all’altro per il calcolo dei ricavi attribuiti.

### Conversione valuta {#currency-conversion}

I tassi nella tabella Tasso di conversione rappresentano il valore necessario per convertire un importo dalla valuta aziendale. Le conversioni in qualsiasi valuta richiedono una doppia conversione, prima dalla valuta originale alla valuta aziendale e quindi dalla valuta aziendale alla valuta selezionata. Il primo passo di questa catena nel modello consiste nell&#39;aggiungere una colonna con il tasso di conversione da aziendale alle tabelle con importi, opportunità e costo. Questi passaggi sono descritti nell’intestazione Righe aggiunte della sezione Trasformazioni dati in questo documento. La conversione dalla valuta originale alla valuta aziendale consiste nel dividere il valore per questa colonna aggiunta. Il passaggio successivo consiste nel moltiplicare il valore della valuta aziendale per il tasso nella tabella Tasso di conversione che corrisponde alla valuta selezionata.

* Converti il valore originale in valuta aziendale / tasso di conversione aziendale = valore in valuta aziendale
* Converte il valore da società a valuta selezionata nella valuta aziendale `*` Tasso di conversione della valuta selezionata = valore nella valuta selezionata

Poiché i tassi di conversione non devono necessariamente essere statici e possono variare in base a intervalli di date specifici, tutti i calcoli di conversione della valuta devono essere eseguiti a livello di riga. Anche in questo caso, poiché i tassi di conversione si riferiscono a un intervallo di date specifico, il calcolo della ricerca deve essere eseguito all’interno del DAX della misura, in modo che la relazione possa essere definita sia sul codice valuta che sulla data.

Se non è possibile identificare un tasso di conversione, le misure di conversione della valuta in questo modello sostituiscono il valore 1,0 per il tasso. Sono state create misure separate per visualizzare il valore di valuta della misura e avvisare se un calcolo include più di un valore di valuta, ovvero se non è stato possibile convertire un valore nella valuta selezionata.

![](assets/marketo-bi-13.png)

## Definizioni dei dati {#data-definitions}

Al modello Power BI sono state aggiunte le definizioni per tabelle, colonne personalizzate e misure.

![](assets/marketo-bi-15.png)

![](assets/marketo-bi-16.png)

![](assets/marketo-bi-14.png)

Per visualizzare le definizioni per le colonne provenienti direttamente da [!DNL Snowflake], consulta la [documentazione del data warehouse](/help/marketo-measure-data-warehouse/data-warehouse-schema.md){target="_blank"}

## Discrepanze tra modelli e individuazione {#discrepancies-between-templates-and-discover}

### Reddito Attribuito {#attributed-revenue}

I punti di contatto lead e i punti di contatto di attribuzione ereditano i dati dimensionali dal punto di contatto originale. Il modello di modello di reporting origina tutti i dati dimensionali ereditati dalla relazione con il punto di contatto, mentre nel modello Discover i dati dimensionali vengono denormalizzati nei record Punto di contatto lead e attribuzione. I valori complessivi dei ricavi attribuiti o dei ricavi attribuiti della pipeline devono essere allineati tra i due rapporti. Tuttavia, possono essere osservate discrepanze quando i ricavi vengono suddivisi o filtrati per dati dimensionali (canale, sottocanale o campagna). Se gli importi delle entrate dimensionali non corrispondono tra il modello e Discover, è probabile che manchino record di punti di contatto nel set di dati del rapporto del modello. Ciò si verifica quando è presente un record di lead o punto di contatto attribuzione, ma nessun record corrispondente nella tabella dei punti di contatto all’interno del set di dati importato nel rapporto. Poiché queste tabelle vengono filtrate in base alla data di modifica, è possibile che il record Punto di contatto Lead/Attribuzione sia stato modificato più di recente rispetto al record Punto di contatto e che quindi il punto di contatto Lead/Attribuzione sia stato importato nel set di dati, mentre il record Punto di contatto originale non lo era. Per risolvere questo problema, allarga l’intervallo di date filtrato per la tabella dei punti di contatto oppure prova a rimuovere il vincolo di data che lo vincola completamente. Nota: il punto di contatto è una tabella di grandi dimensioni, pertanto considera i compromessi di un set di dati più completo rispetto alla quantità di dati che deve essere importata.

### Costo {#cost}

La generazione di rapporti sui costi nei modelli è disponibile solo a livello di campagna e di canale, tuttavia, Scopri le offerte con livelli di granularità inferiori per alcuni provider di annunci (creativi, parole chiave, gruppi di annunci e così via). Per ulteriori dettagli sulla modellazione dei dati sui costi nei modelli, consulta la sezione Modello dati di questa documentazione. Se il filtro dimensione in [!UICONTROL Discover] è impostato su canale o campagna, i costi a livello di canale, sottocanale e campagna devono essere allineati tra Discover e i modelli di rapporto.

### ROI {#roi}

Poiché il ROI è calcolato in base ai ricavi e ai costi attribuiti, le stesse discrepanze che potrebbero sorgere in uno di questi calcoli possono sorgere nel ROI e per gli stessi motivi, come indicato in tali sezioni.

### Punti di contatto {#touchpoints}

Queste metriche, come mostrato nei modelli di reporting, non si riflettono in Discover. Attualmente non è possibile alcun confronto diretto tra i due.

### Traffico web {#web-traffic}

Il modello dati del modello di reporting normalizza i dati dimensionali di canale, sottocanale e campagna tramite la relazione tra sessione e punto di contatto. Questa funzione è diversa dal modello di dati Discover, che denormalizza queste dimensioni in Session. A causa di questa distinzione, i conteggi complessivi per visite e visitatori devono corrispondere tra Discover e il modello di reporting; tuttavia, una volta visualizzati o filtrati per dimensione, non è previsto che tali numeri si allineino. Questo perché i dati dimensionali nel modello sono disponibili solo per gli eventi web che hanno generato un punto di contatto (ad esempio eventi non anonimi). Per ulteriori dettagli, consulta la sezione [Modello dati](#data-model) di questa documentazione.

Potrebbero esserci piccole discrepanze nel conteggio totale dei moduli del sito tra [!DNL Discover] e il modello. Questo perché il modello dati nel modello di reporting ottiene i dati dimensionali per il modulo del sito tramite una relazione con Session e quindi Touchpoint; esistono alcune istanze in cui i dati del modulo del sito non hanno una sessione correlata.

### Lead e account {#leads-and-accounts}

La generazione di rapporti dimensionali per gli account toccati può variare leggermente tra Discover e il modello, anche questo a causa della modellazione dimensionale derivante dalla relazione tra punto di contatto e punto di contatto lead o punto di contatto attribuzione. Fai riferimento ai dettagli descritti nella sezione Entrate attribuite per ulteriori dettagli.

Tutti i conteggi di lead in Discover sono conteggi di lead attribuiti e nel modello di reporting la metrica è lead toccati. Pertanto, non è possibile un confronto diretto tra le due relazioni per questa misura.

### Percorso di coinvolgimento {#engagement-path}

Non esiste alcun confronto diretto tra il report [!UICONTROL Engagement Path] in Discover e il modello. Il report in [!DNL Discover] è modellato sul punto di contatto, mentre il report nel modello è modellato sul punto di contatto di attribuzione. Invece di visualizzare tutti i dati dei punti di contatto, il modello si concentra solo sulle opportunità e sui relativi punti di contatto.

### Velocità offerta {#deal-velocity}

Non dovrebbe esserci alcuna discrepanza tra questo rapporto nel modello e la sezione Velocità di offerta nel dashboard Velocità in Discover.
