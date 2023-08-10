---
unique-page-id: 18874660
description: Domande frequenti - [!DNL Marketo Measure] - Documentazione del prodotto
title: Domande frequenti
exl-id: f1896bf8-2216-427e-ac3e-98d87efede76
feature: Reporting
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '1072'
ht-degree: 0%

---

# Domande frequenti {#faq}

[!DNL Marketo Measure Discover]: Domande frequenti.

**Come si salvano i filtri in un rapporto?**

Come oggi, i risultati delle query vengono salvati nell’URL e possono essere salvati o condivisi con l’URL copiato.

**Come si utilizzano intervalli di date predefiniti, ad esempio Ultimo anno o Trimestre corrente?**

Invece di utilizzare intervalli di date predefiniti, ora abbiamo aggiunto la flessibilità delle date. Puoi ancora impostare Ultimo anno, ma puoi selezionare Ultimo anno 1 che è gli ultimi 365 giorni da oggi o Ultimo anno completo che è l’ultimo anno completo da 1/1 a 12/31. Un altro buon utilizzo del nuovo selettore di date è quello di impostare un intervallo di date relativo, che tenderà a fornire un intervallo di tempo continuo per una data mobile.

**Come si ottengono i dati CPL o CPC?**

Queste metriche sono disponibili solo sulla scheda Paid Media.

**Perché non mostri le Visualizzazioni pagina sulla bacheca Crescita?**

Una delle caratteristiche della bacheca Crescita è che non è possibile raggruppare i grafici di tendenza per una dimensione, come Canale o Campagna. Non disponiamo di tali dati a livello di visualizzazione pagina, in quanto le visualizzazioni di pagina non hanno sempre un’origine come Canale o Campagna, perché si verificano nel mezzo di visite web. Utilizza il traffico web o a pagamento per visualizzare i dati delle visualizzazioni di pagina.

**Quando modifico il raggruppamento, i totali non equivalgono sempre allo stesso importo. Perché?**

Non esistono valori per ogni singola gerarchia di dati perché la gerarchia non è sempre un flusso di taglio chiaro. Ad esempio, sia che i costi vengano autodichiarati o importati da un provider di annunci, il costo totale per Canale 1 potrebbe essere di 10.000 dollari ma per singola campagna, è stato effettivamente segnalato solo un totale di 5.500 dollari, quindi quando il raggruppamento cambia tra Canale e Campagna, i totali variano.

**Che cos’è &quot;corrisponde a un attributo utente&quot; negli operatori di filtro?**

Gli attributi utente vengono applicati a utenti quali ID business, nome o cognome. Poiché tuttavia si tratta di utenti (clienti) e non di clienti, gli attributi utente non possono essere utilizzati in [!DNL Marketo Measure Discover] esperienza. Non esitare a ignorare questa opzione. Stiamo lavorando a una migliore esperienza di filtro personalizzata che rimuoverà i filtri non applicabili ai nostri clienti.

**Come mai alcuni intervalli di date predefiniti attraversano il primo del mese successivo?**

Anche se l’intervallo di date non è sempre intuitivo, l’interfaccia utente filtro predefinita include un utile testo &quot;prima&quot; che corrisponde alla data di fine; questo dovrebbe ricordare all’utente che la data di fine utilizzata dovrebbe essere 1 giorno al di fuori dell’intervallo desiderato.

**Quale modello di attribuzione viene utilizzato per lead e contatti?**

I punti di contatto dell’acquirente mappati su lead e contatti misurano fino al contatto di creazione del lead, pertanto si consiglia di utilizzare i modelli Primo contatto, Creazione di lead e A forma di U. Se si modifica il modello di attribuzione impostandolo su A forma di W o Percorso completo, viene automaticamente applicato un modello a forma di U per lead e contatti.

**Perché le sezioni Visite, Visite univoche e Forms sono vuote nella bacheca Crescita?**

Se nella vista questi riquadri sono vuoti o uguali a 0, significa che non è stato eseguito il provisioning dei riquadri per il tuo account. Per eventuali domande relative a questo argomento, contatta il tuo Success Manager.

**Per i lead nel tempo e i contatti nel tempo, a cosa fa riferimento il conteggio?**

Utilizza i conteggi dei punti di contatto, distribuiti in base al modello di attribuzione selezionato. Si tratta del totale di lead e conteggi distribuiti nel tempo. Non è un conteggio univoco.

**Il grafico relativo agli URL dei moduli per canale nel marketing dei contenuti mostra visite web o riempimenti di moduli?**

Questi sono solo riempimenti modulo tracciati.

**Quali vantaggi offre Discover rispetto a Measure?**

[!DNL Marketo Measure Discover] offre funzionalità migliori, ad esempio drill-through, e un filtro migliore, ad esempio Sottocanali e Canali. Siamo anche sunsetting Misura un po&#39; di tempo nel 2019.

**In Measure, ho potuto filtrare per gruppo di annunci e account quando sono filtrati in account di annunci - come posso vedere questo in Discover?**

Questo sarà disponibile solo con la scheda Paid Media.

**In che modo il funnel di coorte è diverso da Passport Funnel?**

Il funnel di coorte ti consente di esaminare il tasso di conversione del funnel di vendita e di misurare l’impatto tra le fasi. È possibile selezionare la fase da misurare utilizzando i filtri, che consentono di visualizzare il tasso di conversione da quella fase a tutte le fasi successive. La bacheca Passport mostra tutti i lead/contatti e le opportunità che hanno attraversato ogni fase della pipeline in un determinato intervallo di tempo.

**Come viene determinato il contenuto della bacheca Supporti a pagamento?**

In ciascuna sezione della bacheca, abbiamo aggiunto un filtro per includere solo i dati in cui disponiamo di un provider di annunci noto da Facebook, Google, Bing, LinkedIn o Doubleclick, poiché la nostra integrazione ci consente di estrarre i dati dell’annuncio da tali sorgenti. Inoltre, abbiamo aggiunto un nome fuzzy corrispondente a Canali e Sottocanali per Display, Paid Search, Paid Social, PPC, SEM, Paid Mobile, Paid Twitter, Adroll, Terminus, Madison Logic, Madisonlogic e Demandbase.

**Qual è la differenza tra Visite e Visite univoche?**

Visite univoche è un sottoinsieme di Visite. Mentre Visite è un conteggio di ogni visita del sito, Visite univoche sono cookie univoci di tali visite del sito. Una persona può rendere conto di più visite univoche se restituisce un identificatore di cookie diverso.

**I punti di contatto sono conteggiati come punti di contatto dell’acquirente o come punti di contatto di attribuzione dell’acquirente?**

Si tratta di un conteggio di quelli che consideriamo punti di contatto &quot;grezzi&quot;, o &quot;punti di contatto dell’utente&quot;, in cui si tratta di un aggregato di entrambi, più i contatti che non hanno generato un punto di contatto su lead/contatto o opportunità.

**Quando si filtra in base all&#39;URL, perché nelle sezioni Costo per viene visualizzato solo $0,00?**

Questo è il comportamento previsto a causa del fatto che non abbiamo costi segmentati per URL, quindi non è applicabile in quello scenario.

**Perché non vengono visualizzate tutte le opzioni Segmento per i filtri Categoria?**

Solo i segmenti a cui sono mappati record validi verranno visualizzati nel filtro Segmenti. Ad esempio, se non ci sono record con il segmento &quot;Altro&quot;, &quot;Altro&quot; non verrà visualizzato come opzione.

**Does [!DNL Marketo Measure Discover] supporta il set di caratteri GB18030?**

Discover utilizza strumenti di terze parti e al momento non supporta il set di caratteri GB18030.

**Quando si carica Discover, perché viene visualizzato un errore 401 che indica &quot;Non si è autenticati per visualizzare questa pagina&quot;?**

[!DNL Marketo Measure Discover] richiede che i cookie di terze parti vengano visualizzati correttamente. Per utilizzare Discover, abilita i cookie di terze parti nel browser e aggiorna la pagina.

>[!NOTE]
>
>Per impostazione predefinita, alcuni browser, tra cui Chrome in Incognito, disabilitano i cookie di terze parti.

![](assets/faq-1.png)