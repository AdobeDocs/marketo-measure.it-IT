---
description: Costi campagna CRM
title: Costi campagna CRM
exl-id: d967cabe-b9f1-4ea1-a81b-e4484c703ecf
feature: Spend Management
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '1194'
ht-degree: 0%

---


# Costi campagna CRM {#crm-campaign-costs}

La maggior parte dei clienti [!DNL Marketo Measure] utilizza campagne CRM per tenere traccia delle attività di marketing offline. Gli addetti al marketing che utilizzano queste campagne monitorano anche i costi all’interno del sistema CRM. Questa funzione semplifica il lavoro degli esperti di marketing consentendo a [!DNL Marketo Measure] di leggere tali costi e applicarli alle spese di marketing riportate entro [!DNL Marketo Measure]. Ad oggi, i clienti hanno dovuto immettere manualmente i costi per ogni campagna al mese, ma con le informazioni necessarie fornite a [!DNL Marketo Measure], gli utenti possono automatizzare questo processo in modo che gli addetti al marketing possano dedicare più tempo all&#39;analisi della spesa e del ROI.

## Disponibilità {#availability}

Questa funzionalità è disponibile per tutti i clienti [!DNL Salesforce] e Dynamics.

## Come funziona {#how-it-works}

[!DNL Marketo Measure] cerca innanzitutto le campagne che sono state &quot;abilitate&quot; per i punti di contatto, quindi è stata creata una regola di sincronizzazione campagna corrispondente oppure il valore di Abilita punti di contatto buyer è &quot;Includi tutti i membri della campagna&quot; o &quot;Includi i membri della campagna &quot;Con risposta&quot;.&quot; Inoltre, [!DNL Marketo Measure] deve importare i valori corretti e sapere come distribuire i costi, pertanto è necessario che i campi seguenti contengano un valore:

**[!DNL Salesforce]**: `ActualCost`, `StartDate`, `EndDate`

**[!DNL Microsoft Dynamics]**: `totalactualcost`, `actualstart`, `actualend`

Se in uno dei 3 campi manca un valore, [!DNL Marketo Measure] non importa i costi. Puoi correggere questo problema aggiornando il record Campaign nel CRM. I costi non vengono importati se è impostato su $0 perché [!DNL Salesforce] considera vuoto e $0 come lo stesso.

Affinché [!DNL Marketo Measure] determini la distribuzione di una campagna tra mesi, la data di inizio e di fine della campagna viene utilizzata per distribuire l&#39;importo in modo uniforme al giorno.

![Esempio di distribuzione dei costi della campagna CRM per mese](assets/1.jpg)

In questo esempio, una campagna dura 109 giorni, quindi con un costo totale di $ 18.000, la spesa al giorno arriva a ~ $ 165,14.

In base al numero di giorni al mese, si ottengono questi totali mensili, come puoi vedere nella tabella:

Lug 2018: ($ 18.000/109) x 31 = $ 5.119,27

Ago 2018: ($ 18.000/109) x 31 = $ 5.119,27

Set 2018: ($ 18.000/109) x 30 = $ 4.954,13

Ott 2018: ($ 18.000/109) x 17 = $ 2.807,34

## Spesa dichiarata cronologica {#historical-reported-spend}

Se hai inserito una spesa per le campagne che sono state tracciate in passato e mappate a una campagna CRM, questo non sostituisce nessuno dei costi inseriti. Se la stessa campagna nel CRM viene modificata, la ignora e assegna priorità alle modifiche precedentemente apportate nel caricamento CSV.

Se preferisci che il costo della campagna CRM venga preso da ora in poi, modifica il valore nel file CSV in $0, annullando la voce. Alla successiva esecuzione dei processi per l’importazione dei costi, vengono inseriti i rapporti modificati in precedenza.

## Campagne senza punti di contatto {#campaigns-with-no-touchpoints}

Molti esperti di marketing scelgono di segnalare le spese di marketing per le campagne CRM che non hanno generato punti di contatto o che non hanno membri della campagna ai fini del tracciamento delle spese. Se i tre campi sono compilati (data di inizio, data di fine, costo) e la campagna è abilitata per i punti di contatto, [!DNL Marketo Measure] inserisce tale costo, anche se a esso non sono associati punti di contatto.

Questo potrebbe essere utile per tenere traccia delle spese per i costi di marketing in eccesso o per utilizzare strumenti per aggregare tali costi nei calcoli del ROI.

## Sincronizzazione programmi Marketo {#marketo-program-sync}

Se si inseriscono i programmi Marketo nel CRM come campagne, assicurarsi di avere impostato la data di inizio, la data di fine e il mapping dei costi del periodo nei campi CRM richiesti. Poiché non è disponibile alcuna mappatura per il campo Abilita punti di contatto buyer, è comunque necessario abilitare queste campagne in modo da poter estrarre i costi.

## Modifica dei costi {#editing-the-costs}

Una volta importata dal CRM, una campagna viene trattata in modo simile a un provider di annunci API e non verrà visualizzata nel file CSV per apportare modifiche ai costi.

Qualsiasi modifica al costo o alla distribuzione deve essere fatta nel CRM in modo che possiamo puntare a un singolo punto di verità.

## Domande frequenti {#faq}

**Ho apportato una modifica alla mia campagna - quando devo aspettarmi di vedere le modifiche nella tabella delle spese di marketing o nei miei rapporti?**

3-4 ore

**Sono stati compilati la data di inizio, la data di fine e il costo, ma perché i costi non vengono ancora visualizzati in [!DNL Marketo Measure]?**

Verifica di avere il valore &quot;Abilita Buyer Touchpoint&quot; impostato su &quot;Includi tutti i membri della campagna&quot; o almeno &quot;Includi i membri della campagna con risposta&quot;, oppure di aver creato una regola di sincronizzazione della campagna personalizzata che include questa campagna. Se hai confermato questa operazione e non vedi ancora la campagna, contatta il [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} per verificare che le tue campagne siano importate correttamente.

**È necessario modificare la distribuzione della campagna in modo da poterla pesare più pesantemente in alcuni mesi. Come posso fare?**

La ripartizione dei costi si basa esclusivamente su una ripartizione equilibrata tra la data di inizio e la data di fine. Sfortunatamente, non possiamo modificarlo in modo che i costi abbiano una ponderazione diversa oltre alle date stabilite. Puoi controllare questo passaggio regolando la data di inizio e di fine della campagna in quanto ogni giorno del mese è importante.

**Ho impostato i costi per la campagna principale - in che modo le campagne secondarie vengono allocate dai costi della campagna principale?**

In realtà, il modo in cui i costi verranno inseriti sarà direttamente da una singola campagna, indipendentemente da qualsiasi relazione Genitore o Figlio. Consigliamo di addebitare il costo alle campagne per bambini, insieme alle date della campagna, quindi di utilizzare la campagna principale come campagna principale in cui la campagna principale non sarebbe abilitata per i punti di contatto.

**Come posso modificare il costo per un mese in [!DNL Marketo Measure]?**

Poiché ci affidiamo al CRM come unica fonte di verità, tutte le modifiche devono essere fatte nel CRM. Una volta che la campagna è stata importata da [!DNL Marketo Measure], i valori della campagna non sono modificabili in [!DNL Marketo Measure] o nel file CSV.

**In quale scenario una campagna verrà visualizzata nella tabella Spesa marketing?**

Continuiamo a richiedere che tutti e tre i campi chiave abbiano un valore: Data di inizio, Data di fine e Costo. Per impostazione predefinita, importi solo le campagne con un valore superiore a $ 0. Idealmente, importiamo le campagne in cui è presente un valore $0 esplicito e non importiamo quelle che vengono lasciate vuote, ma l’API Salesforce le importa entrambe come $0 indipendentemente dal valore. Inoltre, se il valore Abilita Buyer Touchpoint cambia da &quot;Includi tutto&quot; o &quot;Includi &quot;Risposto&quot; a &quot;Escludi tutto&quot;, la campagna e il costo vengono rimossi dalla tabella Spese di marketing.

**Quale costo avrebbe la priorità se una riga fosse già stata scaricata dal CRM e se avessi immesso un&#39;altra riga nel file CSV con lo stesso ID campagna?**

Anche se il caricamento del file potrebbe essere riuscito, [!DNL Marketo Measure] non utilizzerà tale riga perché disponiamo già di un ID campagna con lo stesso valore estratto automaticamente dall&#39;integrazione.

**Come suggerisci di portare i costi dalle campagne digitali che abbiamo configurato nel sistema di gestione delle relazioni con i clienti?**

Poiché il codice JavaScript [!DNL Marketo Measure] sta già monitorando l&#39;attività Web dal sito, si sconsiglia di sincronizzare le campagne che tengono traccia dei membri della campagna dai moduli Web o da altre attività del sito, in quanto conteggerà due volte i contatti. Per questo motivo, potrebbe essere utile continuare a utilizzare l’opzione Caricamento CSV in Marketing Spend per tenere traccia di tali costi online/digitali, se non siamo già integrati con tale piattaforma (ovvero, Twitter, Adroll).
