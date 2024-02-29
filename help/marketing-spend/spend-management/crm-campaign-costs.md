---
unique-page-id: 18874688
description: Costi campagna CRM - [!DNL Marketo Measure]
title: Costi campagna CRM
exl-id: d967cabe-b9f1-4ea1-a81b-e4484c703ecf
feature: Spend Management
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '1253'
ht-degree: 0%

---

# Costi campagna CRM {#crm-campaign-costs}

Più [!DNL Marketo Measure] I clienti utilizzano le campagne CRM per tenere traccia delle attività di marketing offline. Gli addetti al marketing che utilizzano queste campagne monitoreranno anche i costi all’interno del sistema CRM, pertanto questa funzione semplifica il lavoro degli addetti al marketing consentendo [!DNL Marketo Measure] per leggere tali costi e applicarli alla spesa di marketing riportata entro [!DNL Marketo Measure]. Ad oggi, i clienti hanno dovuto inserire manualmente i costi per ogni campagna al mese, ma con le informazioni necessarie fornite, [!DNL Marketo Measure] può automatizzare questo processo in modo che gli esperti di marketing possano dedicare più tempo all’analisi della spesa e del ROI.

## Disponibilità {#availability}

Questa funzione è disponibile per tutti [!DNL Salesforce] e i clienti Dynamics.

## Come funziona {#how-it-works}

[!DNL Marketo Measure] cerca innanzitutto le campagne che sono state &quot;abilitate&quot; per i punti di contatto, quindi è stata creata una regola di sincronizzazione campagna corrispondente oppure il valore Abilita punti di contatto buyer è &quot;Includi tutti i membri della campagna&quot; o &quot;Includi i membri della campagna &quot;Con risposta&quot;.&quot; Inoltre, [!DNL Marketo Measure] è necessario importare i valori corretti e sapere come distribuire i costi, pertanto è necessario che i campi seguenti contengano un valore:

**[!DNL Salesforce]**: Costo effettivo, DataInizio, DataFine

**[!DNL Microsoft Dynamics]**: totalactualcost, actualstart, actualend

Se in uno dei 3 campi manca un valore, [!DNL Marketo Measure] non importa i costi. Puoi correggere questo problema aggiornando il record Campaign nel CRM. È inoltre importante notare che non importeremo i costi se è impostato esplicitamente su $0 perché [!DNL Salesforce] considera il valore vuoto e $0 allo stesso modo.

Per ottenere [!DNL Marketo Measure] per determinare la distribuzione di una campagna in mesi, utilizziamo le date di inizio e di fine della campagna e distribuiamo l’importo in modo uniforme al giorno.

![](assets/1.jpg)

In questo esempio, abbiamo una campagna che dura 109 giorni, quindi con un costo totale di 18.000 dollari, la spesa giornaliera arriva a ~ 165,14 dollari.

In base al numero di giorni al mese, si ottengono questi totali mensili, come puoi vedere nella tabella:

Lug 2018: ($ 18.000/109) x 31 = $ 5.119,27

Ago 2018: ($ 18.000/109) x 31 = $ 5.119,27

Set 2018: ($ 18.000/109) x 30 = $ 4.954,13

Ott 2018: ($ 18.000/109) x 17 = $ 2.807,34

## Spesa dichiarata cronologica {#historical-reported-spend}

Non si preoccupi! Se hai inserito una spesa per le campagne che abbiamo tracciato in passato e che sono state mappate su una campagna di gestione delle relazioni con i clienti, non sostituiremo nessuno dei costi inseriti. Se la stessa campagna nel CRM viene modificata, la ignoreremo comunque e daremo priorità alle modifiche che hai apportato in precedenza nel caricamento CSV.

Se preferisci che il costo della campagna CRM venga portato avanti, puoi modificare il valore nel file CSV in $0, annullando l’immissione. Quindi, la prossima volta che eseguiremo i nostri processi per importare i costi, eseguiremo la scansione di tutti i record che sono stati precedentemente modificati e li inseriremo.

## Campagne senza punti di contatto {#campaigns-with-no-touchpoints}

Molti esperti di marketing scelgono di segnalare le spese di marketing per le campagne CRM che non hanno generato alcun punto di contatto, o che non hanno consapevolmente membri della campagna a scopo di tracciamento delle spese. Purché i 3 campi siano compilati (data di inizio, data di fine, costo) e la campagna sia abilitata per i punti di contatto, [!DNL Marketo Measure] continuerà ad applicare quel costo indipendentemente dal fatto che ad esso siano associati o meno punti di contatto.

Questo potrebbe essere utile per tenere traccia delle spese per i costi di marketing in eccesso o per utilizzare strumenti per aggregare tali costi nei calcoli del ROI.

## Sincronizzazione programmi Marketo {#marketo-program-sync}

Se si inseriscono programmi Marketo nel CRM come campagne, è necessario assicurarsi di aver impostato la data di inizio, la data di fine e il mapping dei costi del periodo nei campi obbligatori del CRM. Poiché non esiste alcuna mappatura per il campo Abilita punti di contatto dell’acquirente, dovrai comunque abilitare queste campagne in modo che sappiamo come richiederne i costi.

## Modifica dei costi {#editing-the-costs}

Una volta importata dal CRM, la campagna sarà trattata come un provider di annunci API e non comparirà nel CSV per apportare modifiche ai costi.

Qualsiasi modifica al costo o alla distribuzione deve essere fatta nel CRM in modo che possiamo puntare a un singolo punto di verità.

## Domande frequenti {#faq}

**Ho apportato una modifica alla mia campagna - quando devo aspettarmi di vedere le modifiche nella tabella Spesa marketing o nella reportistica?**

3-4 ore

**Ho la data di inizio, la data di fine e il costo compilato, ma perché i miei costi non vengono ancora visualizzati in [!DNL Marketo Measure]?**

Verifica di avere il valore Abilita punto di contatto acquirente impostato su &quot;Includi tutti i membri della campagna&quot; o almeno su &quot;Includi i membri della campagna con risposta&quot;, oppure di aver creato una regola di sincronizzazione della campagna personalizzata che include questa campagna. Se hai confermato questa impostazione e non vedi ancora la campagna, contatta [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} in modo che possiamo verificare che le tue campagne vengano importate correttamente.

**Devo modificare la distribuzione della mia campagna in modo da poterla pesare più pesantemente in alcuni mesi. Come lo faccio?**

La ripartizione dei costi si basa esclusivamente su una ripartizione equilibrata tra la data di inizio e la data di fine. Sfortunatamente, non possiamo modificarlo in modo che i costi abbiano una ponderazione diversa oltre alle date stabilite. Puoi controllare questo passaggio regolando la data di inizio e di fine della campagna in quanto ogni giorno del mese è importante.

**Ho dei costi impostati sulla campagna principale - come vengono allocati i costi dalla campagna principale alle campagne figlio?**

In realtà, il modo in cui i costi verranno inseriti sarà direttamente da una singola campagna, indipendentemente da qualsiasi relazione Genitore o Figlio. Consigliamo di addebitare il costo alle campagne per bambini, insieme alle date della campagna, quindi di utilizzare la campagna principale come campagna principale in cui la campagna principale non sarebbe abilitata per i punti di contatto.

**Come posso modificare il costo per un mese in [!DNL Marketo Measure]?**

Poiché ci affidiamo al CRM come unica fonte di verità, tutte le modifiche devono essere fatte nel CRM. Una volta che la campagna è stata importata da [!DNL Marketo Measure], i valori di Campaign non sono modificabili in [!DNL Marketo Measure] o nel file CSV.

**In quale scenario una campagna apparirebbe nella tabella Spesa marketing?**

Continueremo a richiedere che tutti e tre i campi chiave abbiano un valore: Data di inizio, Data di fine e Costo. Per impostazione predefinita, importi solo le campagne con un valore superiore a $ 0. Idealmente, importeremmo le campagne in cui è presente un valore $0 esplicito e non quelle che vengono lasciate vuote, ma l’API Salesforce le importa entrambe come $0 indipendentemente dal valore. Inoltre, se il valore del punto di contatto Abilita acquirente cambia da &quot;Includi tutto&quot; o &quot;Includi risposte&quot; a &quot;Escludi tutto&quot;, la campagna e il costo verranno rimossi dalla tabella Spese di marketing.

**Quale costo avrebbe la priorità se una riga fosse già stata scaricata dal sistema di gestione delle relazioni con i clienti e se avessi inserito un’altra riga nel file CSV con lo stesso ID campagna?**

Anche se è possibile caricare il file con successo, [!DNL Marketo Measure] non utilizzerà quella riga perché disponiamo già di un ID campagna con lo stesso valore che è stato automaticamente estratto dall’integrazione.

**Come consiglieresti di portare i costi dalle campagne digitali che abbiamo configurato nel CRM?**

Perché il nostro [!DNL Marketo Measure] JavaScript sta già monitorando l’attività web dal sito. Ti consigliamo di non sincronizzare le campagne che tengono traccia dei membri della campagna dai moduli web o da altre attività del sito, in quanto i contatti conteggiati due volte. Per questo motivo, potrebbe essere utile continuare a utilizzare l’opzione Caricamento CSV in Marketing Spend per monitorare tali costi online/digitali, se non è già stata effettuata l’integrazione con tale piattaforma (ad esempio Twitter, Adroll).
