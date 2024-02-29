---
unique-page-id: 18874704
description: Domande frequenti sull’attribuzione delle attività - [!DNL Marketo Measure]
title: Domande frequenti sull’attribuzione delle attività
exl-id: 6272024f-b6ae-4aa7-ba92-c9f183549614
feature: Attribution
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 0%

---

# Domande frequenti sull’attribuzione delle attività {#activities-attribution-faq}

[!DNL Marketo Measure] Le attività importano tutti i record Attività e generano punti di contatto per esse, consentendo a queste attività di ricevere il credito di attribuzione. Il caso d’uso più comune consiste nel tenere traccia delle attività del team vendite, in quanto solitamente creano un record di chiamate telefoniche o e-mail inviate ai potenziali clienti. Altre caratteristiche uniche che possono essere tracciate sono le interazioni di contenuto come download di risorse o visualizzazioni video.

**Quali sono le differenze rispetto alle campagne offline?**

La differenza maggiore è che le campagne possono fornire un solo punto di contatto, perché le campagne consentono un solo membro della campagna per ogni lead o contatto. Ciò significa che non puoi tenere traccia di eventi ricorrenti come chiamate in uscita, demo o partecipanti a webinar, a meno che non crei singole campagne per ciascun raggruppamento. Le attività ti consentono di misurare ogni evento.

**Esiste una differenza tra Attività, Eventi e Attività?**

L&#39;oggetto Activities funge da ombrello, o padre, sugli oggetti Task ed Event. Le attività riguardano essenzialmente sia Attività che Eventi. Le attività vengono in genere utilizzate per registrare elementi singoli rapidi, ad esempio una telefonata o un’e-mail. Gli eventi vengono in genere utilizzati per elementi che potrebbero avere una data di inizio o di fine, come riunioni o conferenze.

**Se ho un lead o un contatto con la stessa attività ricorrente, visualizzerò i punti di contatto dell&#39;acquirente per tutte queste attività?**

Sì. Esiste una relazione 1:1 tra le attività sincronizzate e i punti di contatto creati.

**Come faccio a sapere quali record determinano la creazione di punti di contatto?**

Un buon suggerimento è quello di impostare i filtri utilizzando prima l’oggetto Attività nel CRM. In base alle regole del filtro, puoi avere una buona idea del numero di record che rientrano in quel criterio e poi puoi perfezionarli in base alle esigenze. Non è necessario, ma è un modo utile per consentire agli utenti di capire quanti punti di contatto Attività verranno creati dopo l’impostazione delle regole Attività.

**Cos&#39;è [!DNL Marketo Measure] Nome campagna?**

Poiché queste attività generano un punto di contatto, [!DNL Marketo Measure] devono sapere a quali canali e sottocanale appartengono. Per ogni regola, devi fornire un [!DNL Marketo Measure] Nome della campagna. Dopo la creazione, utilizza il file CSV dei canali online per mappare [!DNL Marketo Measure] Nome della campagna al relativo canale. Il [!DNL Marketo Measure] Il nome della campagna viene visualizzato anche sul punto di contatto all’interno del [!UICONTROL Ad Campaign Name] campo.

**Quali altri campi punto di contatto sono compilati?**

| **Campo punto di contatto** | **Valore** |
|---|---|
| Lead/Contatto | Tutte le attività sono correlate a un lead o a un contatto |
| Campaign | Canale.Sottocanale [[!DNL Marketo Measure]] |
| Sorgente punto di contatto | Attività CRM |
| Medium | Activity.Type |
| Tipo di punto di contatto | Activity.Type |
| Nome campagna pubblicitaria | [!DNL Marketo Measure] Nome campagna |
| Contenuto annuncio | Oggetto attività |
| ID annuncio | ID esterno attività |
| Data punto di contatto | [personalizzato - impostato nelle app] |

**Cosa succede se devo creare una regola diversa per ogni rappresentante di vendita? Devo creare diversi [!DNL Marketo Measure] Campagna per ciascuno?**

No, non è vero. &quot;Nomi campagne dinamici&quot; consente di compilare una parte (o tutte) del [!DNL Marketo Measure] Nome della campagna utilizzando un &quot;parametro di sostituzione&quot; che fa riferimento a un campo dell’oggetto Attività. Ad esempio, se hai un [!DNL Marketo Measure] Nome della campagna intitolato &quot;Chiamata in uscita&quot; ma desideri che il rappresentante commerciale sia alla fine, utilizza il nome del campo CRM e chiama [!DNL Marketo Measure] Nome della campagna &quot;Chiamata in uscita {AssignedTo}&quot; o &quot;Chiamata in uscita {CreatedBy}.&quot;

**Come si impostano le attività in [!DNL Marketo Measure] app?**

Istruzioni su come configurare le attività all’interno di [!UICONTROL Marketo] L’app Measure si trova in [!DNL Marketo Measure] Articolo di supporto sulle attività.

**Cosa significano i diversi operatori?**

* è uguale a: corrispondenza esatta con il valore (alias: social)
* contiene: il testo è al centro (ovvero: &#42;social&#42;)
* inizia con: il valore inizia con il testo (social)&#42;)
* termina con: il valore termina con il testo (alias: &#42;social)
* corrisponde a qualsiasi: è possibile aggiungere più valori separati da virgola. Se [!UICONTROL starts with], [!UICONTROL ends with], o contiene gli operatori devono essere applicati, utilizza il carattere jolly (&#42;)
* maggiore di: utilizzato per campi numerici o campi data/ora
* minore di: utilizzato per campi numerici o campi data/ora

**In quale canale si inseriscono queste attività?**

Quando la regola Attività e la corrispondente [!DNL Marketo Measure] Viene creato il Nome della campagna. Utilizza le definizioni dei canali online per posizionare le campagne nel canale di marketing corretto. [!DNL Marketo Measure] può definire i canali utilizzando non solo il mezzo e l’origine, ma anche la campagna.

Nell’esempio precedente, per assegnare la campagna &quot;Chiamata in uscita {assegnata a}&quot; al canale BDR, inserisci una riga nel file CSV dei canali online per il canale BDR con la definizione della campagna &quot;Chiamata in uscita&quot;&#42;&quot; - l’asterisco indica un valore jolly, pertanto tutte le campagne che iniziano con &quot;Outbound Call&quot; (Chiamata in uscita) rientrano nel canale BDR, anziché dover creare una riga separata per ciascun nome della campagna.
