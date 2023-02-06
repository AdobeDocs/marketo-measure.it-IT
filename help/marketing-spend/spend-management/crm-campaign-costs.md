---
unique-page-id: 18874688
description: Costi della campagna CRM - [!DNL Marketo Measure] - Documentazione del prodotto
title: Costi della campagna CRM
exl-id: d967cabe-b9f1-4ea1-a81b-e4484c703ecf
source-git-commit: 54337a0a65b79d80ebeae6531f5e92f4f48721a7
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 0%

---

# Costi della campagna CRM {#crm-campaign-costs}

Più [!DNL Marketo Measure] I clienti utilizzano le campagne CRM per tenere traccia delle attività di marketing offline. Gli addetti al marketing che utilizzano queste campagne monitoreranno anche i costi all’interno del sistema di gestione delle relazioni con i clienti, pertanto questa funzione semplifica l’attività agli addetti al marketing consentendo [!DNL Marketo Measure] per leggere tali costi e applicarli alla spesa di marketing segnalata entro [!DNL Marketo Measure]. Ad oggi, i clienti hanno dovuto inserire manualmente i costi per ogni campagna al mese, ma con le informazioni necessarie fornite, [!DNL Marketo Measure] può automatizzare questo processo in modo che gli esperti di marketing possano trascorrere più tempo ad analizzare la spesa e il ROI.

## Disponibilità {#availability}

Questa funzione è disponibile per tutti [!DNL Salesforce] e i clienti Dynamics.

## Come funziona {#how-it-works}

[!DNL Marketo Measure] cerca innanzitutto le campagne che sono state &quot;abilitate&quot; per i punti di contatto, quindi è stata creata una regola di sincronizzazione di campagna corrispondente, oppure il valore Abilita punti di contatto dell’acquirente è &quot;Includi tutti i membri della campagna&quot; o &quot;Includi i membri della campagna &quot;Rispondi&quot;.&quot; Inoltre, [!DNL Marketo Measure] è necessario importare i valori corretti e sapere come distribuire i costi, pertanto è necessario che i campi seguenti contengano un valore:

**[!DNL Salesforce]**: CostoEffettivo, DataInizio, DataFine

**[!DNL Microsoft Dynamics]**: costo totale, avvio effettivo, attualend

Se manca un valore in uno dei tre campi, [!DNL Marketo Measure] non importa i costi. Puoi correggerlo aggiornando il record Campaign nel CRM. Importante anche notare che non importeremo i costi se è esplicitamente impostato a $0 perché [!DNL Salesforce] considera vuoto e $0 come lo stesso.

Per [!DNL Marketo Measure] per determinare la distribuzione di una campagna in più mesi, utilizziamo la data di inizio e di fine della campagna e distribuiamo l’importo in modo uniforme al giorno.

![](assets/1.jpg)

Quindi in questo esempio, abbiamo una campagna che dura 109 giorni, quindi con un costo totale di $18.000, la spesa al giorno arriva a ~$165,14.

In base al numero di giorni al mese, otteniamo questi totali mensili, come puoi vedere nella tabella:

Lug 2018: ($18.000/109) x 31 = $5.119,27

Ago 2018: ($18.000/109) x 31 = $5.119,27

Set 2018: ($18.000/109) x 30 = $4.954,13

Ott 2018: ($18.000/109) x 17 = $2.807,34

## Spesa segnalata cronologica {#historical-reported-spend}

Non ti preoccupare! Se hai inserito spese per campagne che abbiamo tracciato in passato mappate a una campagna CRM, non sovrascriveremo nessuno dei costi che hai inserito. Se la stessa campagna nel CRM viene modificata, la ignoreremo comunque e daremo priorità alle modifiche che hai apportato in precedenza nel caricamento CSV.

Se preferisci che il costo della campagna di gestione delle relazioni con i clienti prosegua, puoi modificare il valore nel CSV in $0, il che annullerà la voce. Poi, la prossima volta che eseguiremo i nostri lavori per importare i costi, analizzeremo tutti i record che sono stati precedentemente modificati e li inseriremo.

## Campagne senza punti di contatto {#campaigns-with-no-touchpoints}

Molti addetti al marketing scelgono di segnalare le spese di marketing per le campagne CRM che non generavano punti di contatto o che, consapevolmente, non hanno membri della campagna ai fini del tracciamento della spesa. Se i 3 campi sono compilati (data di inizio, data di fine, costo) e la campagna è abilitata per i punti di contatto, [!DNL Marketo Measure] esegue comunque il pull di tale costo indipendentemente dal fatto che siano associati o meno punti di contatto.

Questo potrebbe essere utile per monitorare la spesa in eccesso di costi di marketing o strumenti per inserirla nei calcoli del ROI.

## Sincronizzazione dei programmi Marketo {#marketo-program-sync}

Se inserisci i programmi Marketo nel CRM come campagne, assicurati di disporre della mappatura Data inizio, Data fine e Costo periodo impostata sui campi CRM richiesti. Poiché non è presente alcuna mappatura al campo Abilita punti di contatto acquirente , sarà comunque necessario abilitare queste campagne in modo che sappiamo di estrarre i costi per loro.

## Modifica dei costi {#editing-the-costs}

Una volta importata dalla gestione delle relazioni con i clienti, una campagna verrà trattata come un provider di annunci API e non verrà visualizzata nel CSV per apportare modifiche ai costi.

Qualsiasi modifica al costo o alla distribuzione deve essere fatta nel CRM in modo da poter puntare a un singolo punto di verità.

## Domande frequenti {#faq}

**Ho apportato una modifica alla mia campagna: quando dovrei aspettarmi di vedere le modifiche nella tabella delle spese di marketing o nel mio reporting?**

3-4 ore

**Ho la data di inizio, la data di fine e i costi compilati ma perché i miei costi non sono ancora visualizzati in [!DNL Marketo Measure]?**

Verifica di aver impostato il valore Abilita punto di contatto dell’acquirente su &quot;Includi tutti i membri della campagna&quot; o almeno su &quot;Includi i membri della campagna &quot;Rispondi&quot; oppure di aver creato una regola di sincronizzazione personalizzata della campagna che include questa campagna. Se hai confermato questo e non vedi ancora la campagna, contatta [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} per verificare che le campagne vengano importate correttamente.

**Devo cambiare la distribuzione della mia campagna in modo da poterla appendere più pesante in alcuni mesi. Come lo faccio?**

La distribuzione dei costi si basa esclusivamente su una distribuzione uniforme dalla data di inizio alla data di fine. Sfortunatamente, non possiamo cambiarlo in modo che i vostri costi abbiano un peso diverso rispetto alle date stabilite. Puoi controllare questo problema regolando la data di inizio e di fine della campagna, poiché ogni giorno del mese conta.

**Ho impostato i costi per la mia campagna padre: come vengono assegnati i costi per le campagne figlio dalla campagna padre?**

In realtà, il modo in cui i costi verranno inseriti sarà direttamente da una singola campagna, indipendentemente da qualsiasi relazione padre o figlio. È consigliabile che il costo vada alle campagne per bambini, insieme alle date della campagna, quindi utilizzare l’elemento padre come campagna ombrello in cui la campagna padre non verrebbe abilitata per i punti di contatto.

**Come posso modificare il costo per un mese in [!DNL Marketo Measure]?**

Poiché ci affidiamo al CRM come unica fonte di verità, tutte le modifiche devono essere apportate nel CRM. Una volta importata la campagna da [!DNL Marketo Measure], i valori Campaign non sono modificabili in [!DNL Marketo Measure] o nel file CSV.

**In quale scenario una campagna apparirebbe nella tabella Marketing Spend (Spesa di marketing), quindi non verrà più visualizzata?**

Continueremo a richiedere che tutti e tre i campi chiave abbiano un valore: Data inizio, Data fine e Costo. Per impostazione predefinita, le campagne vengono importate solo con un valore maggiore di $0. È consigliabile importare le campagne in cui è presente un valore $0 esplicito e non importarle che sono lasciate vuote, ma l’API Salesforce le importa entrambe come $0, indipendentemente dal valore. Inoltre, se il valore Abilita punto di contatto dell’acquirente cambia da &quot;Includi tutto&quot; o &quot;Includi tutti&quot; a &quot;Escludi tutto&quot;, verranno rimossi la campagna e il costo dalla tabella Spese di marketing.

**Quale costo avrebbe la priorità se una riga fosse già stata scaricata dal CRM e io avessi inserito un’altra riga nel CSV con lo stesso ID campagna?**

Anche se puoi caricare correttamente il file, [!DNL Marketo Measure] non utilizzerà questa riga perché disponiamo già di un ID campagna con lo stesso valore prelevato automaticamente dall’integrazione.

**Come suggeriremmo di portarli i costi dalle nostre campagne digitali che abbiamo impostato nel CRM?**

Perché il nostro [!DNL Marketo Measure] javascript sta già monitorando le attività web dal tuo sito, consigliamo di non sincronizzare eventuali campagne che tengono traccia dei membri di Campaign da moduli web o altre attività del sito, in quanto conteggerà due volte i contatti. Per questo motivo, potresti voler continuare a utilizzare l’opzione Caricamento CSV in Marketing Spend per tenere traccia dei costi online/digitali se non siamo già integrati con quella piattaforma (ad esempio, Twitter, Adroll).
