---
unique-page-id: 18874660
description: Domande frequenti - [!DNL Marketo Measure] - Documentazione del prodotto
title: Domande frequenti
exl-id: f1896bf8-2216-427e-ac3e-98d87efede76
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '1072'
ht-degree: 0%

---

# Domande frequenti {#faq}

[!DNL Marketo Measure Discover]: Domande frequenti.

**Come si salvano i filtri in un rapporto?**

Come oggi, i risultati delle query vengono salvati nell’URL e possono essere salvati o condivisi con l’URL copiato.

**Come si utilizzano gli intervalli di date predefiniti come Ultimo anno o Trimestre corrente?**

Invece di utilizzare intervalli di date predefiniti, ora è disponibile una maggiore flessibilità. È ancora possibile impostare l&#39;Anno scorso, ma è possibile selezionare Ultimo 1 anno, che è l&#39;ultimo 365 giorni da oggi o Ultimo 1 Anno completo, che è l&#39;ultimo anno completo dall&#39;1/1 al 12/31. Un altro buon utilizzo del nuovo selettore data è quello di impostare un intervallo di date relativo, che tenderà a fornire una finestra temporale continua per una data in movimento.

**Come posso ottenere dati CPL o CPC?**

Queste metriche si trovano solo sulla scheda a pagamento.

**Perché non visualizzi Visualizzazioni pagina sulla scheda Crescita?**

Una delle caratteristiche della scheda Crescita è che non è possibile raggruppare i grafici di tendenza per una dimensione, come Canale o Campagna. Non disponiamo di tali dati a livello di Visualizzazione pagina, in quanto le Visualizzazioni pagina non hanno sempre un’origine come Canale o Campagna perché si verificano nel mezzo delle visite web. Utilizza File multimediali a pagamento o Traffico web per visualizzare i dati Visualizzazioni pagina.

**Quando modifico il raggruppamento, i totali non corrispondono sempre alla stessa quantità. Perché?**

I valori non esistono per ogni singola gerarchia di dati perché la gerarchia non è sempre un flusso di taglio trasparente. Ad esempio, se i costi vengono segnalati o importati da un provider di annunci, il costo totale per Channel 1 potrebbe essere di $ 10.000, ma per singola campagna è stato effettivamente riportato solo un totale di $ 5.500, quindi quando il raggruppamento cambia tra Channel e Campaign, i totali variano.

**Cosa significa &quot;corrisponde a un attributo utente&quot; negli operatori Filter?**

Gli attributi utente vengono applicati agli utenti come ID business, nome o cognome, ma poiché i nostri utenti siete voi (i nostri clienti) e non i vostri clienti, gli attributi utente non possono essere utilizzati nel [!DNL Marketo Measure Discover] esperienza. Non esitare a ignorare questa opzione. Stiamo lavorando a una migliore esperienza di filtro personalizzata che rimuoverà i filtri che non si applicano ai nostri clienti.

**Perché alcuni intervalli di date predefiniti passano attraverso il primo del mese successivo?**

Anche se l’intervallo di date non è sempre intuitivo, l’interfaccia utente del filtro predefinito dispone dell’utile testo &quot;prima&quot; che corrisponde alla data di fine, questo ti dovrebbe aiutare a ricordare che la data di fine utilizzata deve essere 1 giorno al di fuori dell’intervallo desiderato.

**Quale modello di attribuzione viene utilizzato per lead e contatti?**

I punti di contatto dell’acquirente mappati su Lead e contatti consentono di misurare fino al tocco Creazione lead, pertanto si consiglia il modello Primo contatto, Creazione lead e A forma di U. Se si modifica il modello di attribuzione in W-Shaped o Full Path, viene applicato automaticamente un modello a forma di U per lead e contatti.

**Perché le mie visite, visite univoche e i riquadri Forms sono vuoti sulla Crescita?**

Se questi riquadri sono uguali a 0 o vuoti nella visualizzazione, significa che non è stato effettuato il provisioning dei riquadri per il tuo account. In caso di domande, contatta il tuo Success Manager.

**Per i lead nel tempo e i contatti nel tempo, quale è il riferimento al conteggio?**

Utilizza i conteggi dei punti di contatto, distribuiti in base al modello di attribuzione selezionato. Sarà il totale dei lead e dei conteggi distribuiti nel tempo. Non è un conteggio univoco.

**Il grafico per gli URL dei moduli per canale in Content Marketing mostra visite web o riempimenti dei moduli?**

Sono solo riempimenti dei moduli tracciati.

**Qual è il vantaggio di Discover rispetto a Measure?**

[!DNL Marketo Measure Discover] fornisce funzionalità migliori, ad esempio drill-through, e filtri migliori, come canali secondari e canali. Stiamo anche tramontando Misura un po&#39; di tempo nel 2019.

**In Misura, sono stato in grado di filtrare per gruppo di annunci e account quando vengono filtrati negli account di annunci - come posso vedere questo in Discover?**

Questo sarà disponibile solo con la scheda a pagamento.

**In che modo l’Funnel coorte è diverso dall’Funnel Passport?**

L’imbuto per coorte ti consente di controllare il tasso di conversione dell’imbuto di vendita, misurando l’impatto tra le varie fasi. È possibile selezionare l’area di visualizzazione da misurare utilizzando i filtri, che consentono di visualizzare il tasso di conversione da tale fase a tutte le fasi successive. La scheda Passport mostra tutti i lead/contatti e le opportunità che hanno attraversato ogni fase della pipeline entro un determinato intervallo di tempo.

**Come vengono determinati i contenuti della scheda a pagamento?**

Su ciascuno dei riquadri della bacheca, abbiamo aggiunto un filtro per includere solo i dati in cui disponiamo di un Ad Provider noto da Facebook, Google, Bing, LinkedIn o Doubleclick, poiché la nostra integrazione ci consente di estrarre i dati dell&#39;annuncio da tali fonti. Inoltre, abbiamo aggiunto un nome sfocato che corrisponde a Canali e Sottocanali per Visualizzazione, Ricerca a pagamento, Social a pagamento, PPC, SEM, Mobile a pagamento, Twitter a pagamento, Adroll, Terminus, Madison Logic, Madisonlogic e Demandbase.

**Qual è la differenza tra visite e visite univoche?**

Le visite univoche sono un sottoinsieme di visite. Mentre le visite sono un conteggio di ogni visita del sito, le Visite univoche sono cookie unici di quelle visite del sito. Una persona può tenere conto di più visite univoche se restituisce con un diverso identificatore di cookie.

**Conteggia i punti di contatto dell’acquirente o dei punti di contatto dell’attribuzione dell’acquirente?**

È un conteggio di ciò che consideriamo punti di contatto &quot;grezzi&quot;, o &quot;punti di contatto utente&quot;, in cui è un aggregato di entrambi, oltre a quelli che non hanno portato a un punto di contatto sul lead/contatto o opportunità.

**Quando filtro per URL, perché il costo per riquadri mostra solo $ 0,00?**

Questo è il comportamento previsto a causa del fatto che non abbiamo costi segmentati per URL, quindi non è applicabile in quello scenario.

**Perché non vengono visualizzate tutte le opzioni Segmento per i filtri Categoria?**

Nel filtro Segmenti verranno visualizzati solo i Segmenti con record validi mappati ad essi. Ad esempio, se non ci sono record con il segmento &quot;Altro&quot;, allora &quot;Altro&quot; non verrà visualizzato come opzione.

**Does [!DNL Marketo Measure Discover] supporta il set di caratteri GB18030?**

Discover utilizza strumenti di terze parti e al momento non supporta il set di caratteri GB18030.

**Quando si carica Discover, perché viene visualizzato un errore 401 che indica &quot;Non sei autenticato per visualizzare questa pagina&quot;?**

[!DNL Marketo Measure Discover] richiede la corretta visualizzazione dei cookie di terze parti. Per utilizzare Discover, abilita i cookie di terze parti nel browser e aggiorna la pagina.

>[!NOTE]
>
>Alcuni browser, tra cui Chrome in Incognito, disattivano i cookie di terze parti per impostazione predefinita.

![](assets/faq-1.png)