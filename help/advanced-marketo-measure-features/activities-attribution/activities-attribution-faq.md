---
unique-page-id: 18874704
description: Domande frequenti sull’attribuzione delle attività - [!DNL Marketo Measure] - Documentazione del prodotto
title: Domande frequenti su Attribution di attività
exl-id: 6272024f-b6ae-4aa7-ba92-c9f183549614
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 0%

---

# Domande frequenti su Attribution di attività {#activities-attribution-faq}

La [!DNL Marketo Measure] La funzionalità Attività ci consente di importare tutti i tuoi record Attività e di generare relativi punti di contatto, consentendo a queste attività di ricevere un credito di attribuzione. Il caso d’uso più comune è quello di tenere traccia delle attività dal team di vendita, in quanto di solito creano un record di chiamate o e-mail inviate ai potenziali clienti. Altre cose uniche che possono essere tracciate sono le interazioni di contenuto come download di risorse o visualizzazioni video.

**In che modo si differenzia dalle campagne offline?**

La differenza maggiore è che le campagne possono fornire un solo punto di contatto, perché le campagne consentono un solo membro della campagna per ogni lead o contatto. Ciò significa che non è possibile tenere traccia di eventi ricorrenti come chiamate in uscita o demo o partecipanti al webinar, a meno che non si creino singole campagne per ciascun raggruppamento. Le attività ti consentono di misurare ogni singolo evento.

**Esiste una differenza tra Attività, Eventi e Attività?**

L&#39;oggetto Attività funge da ombrello, o elemento principale, sugli oggetti Task ed Event. Le attività riguardano essenzialmente sia Attività che Eventi. Le attività vengono in genere utilizzate per registrare elementi una tantum rapidi, ad esempio una chiamata telefonica o un’e-mail. Gli eventi vengono generalmente utilizzati per elementi che possono avere una data di inizio o di fine, come riunioni o conferenze.

**Se dispongo di un lead o di un contatto con la stessa attività ricorrente, ad esempio un’e-mail o una chiamata, visualizzerò i punti di contatto dell’acquirente per tutti i punti di contatto?**

Sì. Sarà presente una relazione 1:1 tra le attività sincronizzate e i punti di contatto creati.

**Come posso sapere quali record determineranno la creazione di punti di contatto?**

Un buon suggerimento è quello di impostare i filtri utilizzando prima l&#39;oggetto Attività nel CRM. In base alle regole del filtro, questo ti darà una buona idea di quanti record rientrano in quel criterio, allora puoi perfezionarlo in base alle tue esigenze. Non è necessario, ma è utile per gli utenti capire quanti punti di contatto attività verranno creati dopo la configurazione delle regole Attività.

**Che cos&#39;è la [!DNL Marketo Measure] Nome campagna?**

Poiché queste attività si tradurranno in un punto di contatto, [!DNL Marketo Measure] deve sapere a quale canale e sottocanale appartengono. Per ogni regola, ti verrà richiesto di fornire un [!DNL Marketo Measure] Nome campagna. Una volta creato, puoi utilizzare il CSV dei canali online per mappare il [!DNL Marketo Measure] Nome della campagna nel relativo canale appropriato. La [!DNL Marketo Measure] Il nome della campagna verrà visualizzato anche sul punto di contatto stesso all’interno del [!UICONTROL Ad Campaign Name] campo .

**Quali altri campi punto di contatto sono compilati?**

| **Campo punto di contatto** | **Valore** |
|---|---|
| Lead/Contatto | Tutte le attività sono correlate a un lead o a un contatto |
| Campaign | Channel.Subchannel [[!DNL Marketo Measure]] |
| Origine punto di contatto | Attività CRM |
| Medium | Activity.Type |
| Tipo punto di contatto | Activity.Type |
| Nome della campagna pubblicitaria | [!DNL Marketo Measure] Nome campagna |
| Contenuto annuncio | Oggetto attività |
| Id annuncio | ID esterno attività |
| Data punto di contatto | [personalizzato - impostato nelle app] |

**Cosa succede se devo creare una regola diversa per ogni rappresentante commerciale? Devo creare diversi [!DNL Marketo Measure] Campagne per ognuna di esse?**

No, no. Abbiamo introdotto il concetto di &quot;Nomi delle campagne dinamiche&quot;. Questo consente di compilare parte (o tutti) del [!DNL Marketo Measure] Nome campagna utilizzando un &quot;parametro di sostituzione&quot; che fa riferimento a un campo dall’oggetto Attività. Ad esempio, se hai una [!DNL Marketo Measure] Nome campagna denominato &quot;Chiamata in uscita&quot; ma si desidera che il rappresentante vendite sia alla fine, si prende il nome del campo CRM e si chiama il [!DNL Marketo Measure] Nome della campagna &quot;Chiamata in uscita {AssignedTo}&quot; o &quot;Chiamata in uscita {CreatedBy}&quot;.

**Come si impostano le attività nel [!DNL Marketo Measure] app?**

Istruzioni su come configurare le attività all’interno di [!UICONTROL Marketo] L’app di misura si trova nella sezione [!DNL Marketo Measure] Articolo relativo al supporto delle attività.

**Cosa intendono i diversi operatori?**

* è uguale a: corrispondenza esatta con il valore (aka: sociale)
* contiene: il testo è al centro (aka: &#42;sociale&#42;)
* inizia con: il valore inizia con il testo (aka: sociale&#42;)
* termina con: il valore termina con il testo (aka: &#42;sociale)
* corrisponde a qualsiasi: è possibile aggiungere più valori separati da virgole. Se [!UICONTROL starts with], [!UICONTROL ends with], o contiene gli operatori devono essere applicati, utilizzato il carattere jolly (&#42;)
* maggiore di: utilizzato per campi numerici o campi data/ora
* minore di: utilizzato per campi numerici o campi data/ora

**In che canale si svolgeranno queste attività?**

Una volta che la regola di attività e il corrispondente [!DNL Marketo Measure] Nome campagna, vengono create le definizioni dei canali online per posizionare le campagne sotto il canale di marketing corretto. [!DNL Marketo Measure] è in grado di definire i canali utilizzando non solo il supporto e la sorgente, ma anche la campagna.

Nell’esempio precedente, per assegnare la campagna &quot;Chiamata in uscita {assegnata a}&quot; al canale BDR, è necessario inserire una riga nel CSV dei canali online per il canale BDR con una definizione della campagna &quot;Chiamata in uscita&quot;&#42;&quot; - l&#39;asterisco indica un valore jolly, pertanto tutte le campagne che iniziano con &quot;Chiamata in uscita&quot; ricadranno sotto il canale BDR, anziché dover creare una riga separata per ciascun nome della campagna.
