---
unique-page-id: 18874704
description: Domande frequenti su Attribuzione attività - [!DNL Marketo Measure]
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

**In che modo si differenzia da Campagne offline?**

La differenza maggiore è che le campagne possono fornire un solo punto di contatto, perché le campagne consentono un solo membro della campagna per ogni lead o contatto. Ciò significa che non puoi tenere traccia di eventi ricorrenti come chiamate in uscita, demo o partecipanti a webinar, a meno che non crei singole campagne per ciascun raggruppamento. Le attività ti consentono di misurare ogni evento.

**Esiste una differenza tra Attività, Eventi e Attività?**

L&#39;oggetto Activities funge da ombrello, o padre, sugli oggetti Task ed Event. Le attività riguardano essenzialmente sia Attività che Eventi. Le attività vengono in genere utilizzate per registrare elementi singoli rapidi, ad esempio una telefonata o un’e-mail. Gli eventi vengono in genere utilizzati per elementi che potrebbero avere una data di inizio o di fine, come riunioni o conferenze.

**Se ho un lead o un contatto con la stessa attività ricorrente, vedrò i punti di contatto dell&#39;acquirente per tutte queste attività?**

Sì. Esiste una relazione 1:1 tra le attività sincronizzate e i punti di contatto creati.

**Come posso sapere quali record determinano la creazione di punti di contatto?**

Un buon suggerimento è quello di impostare i filtri utilizzando prima l’oggetto Attività nel CRM. In base alle regole del filtro, puoi avere una buona idea del numero di record che rientrano in quel criterio e poi puoi perfezionarli in base alle esigenze. Non è necessario, ma è un modo utile per consentire agli utenti di capire quanti punti di contatto Attività verranno creati dopo l’impostazione delle regole Attività.

**Qual è il nome della campagna [!DNL Marketo Measure]?**

Poiché queste attività generano un punto di contatto, [!DNL Marketo Measure] deve sapere a quale canale e sottocanale appartengono. Per ogni regola, è necessario fornire il nome della campagna [!DNL Marketo Measure]. Dopo la creazione, utilizzare il file CSV dei canali online per mappare il nome della campagna [!DNL Marketo Measure] sul canale appropriato. Il nome della campagna [!DNL Marketo Measure] viene visualizzato anche nel punto di contatto stesso all&#39;interno del campo [!UICONTROL Ad Campaign Name].

**Quali altri campi punto di contatto sono compilati?**

| **Campo punto di contatto** | **Valore** |
|---|---|
| Lead/Contatto | Tutte le attività sono correlate a un lead o a un contatto |
| Campaign | Canale.Sottocanale [[!DNL Marketo Measure]] |
| Source punto di contatto | Attività CRM |
| Medium | Activity.Type |
| Tipo di punto di contatto | Activity.Type |
| Nome campagna pubblicitaria | Nome campagna [!DNL Marketo Measure] |
| Contenuto annuncio | Oggetto attività |
| ID annuncio | ID esterno attività |
| Data punto di contatto | [personalizzato - impostato nelle app] |

**Cosa succede se devo creare una regola diversa per ogni rappresentante di vendita? È necessario creare una [!DNL Marketo Measure] campagna diversa per ciascuna?**

No, non è vero. &quot;Nomi campagne dinamici&quot; consente di compilare una parte (o tutte) del Nome campagna [!DNL Marketo Measure] utilizzando un &quot;parametro di sostituzione&quot; che fa riferimento a un campo dell&#39;oggetto Attività. Ad esempio, se si dispone di un nome di campagna [!DNL Marketo Measure] denominato &quot;Chiamata in uscita&quot; ma si desidera che il rappresentante commerciale si trovi alla fine, utilizzare il nome del campo CRM e chiamare il nome della campagna [!DNL Marketo Measure] &quot;Chiamata in uscita {AssignedTo}&quot; o &quot;Chiamata in uscita {CreatedBy}&quot;.

**Come si impostano le attività nell&#39;app [!DNL Marketo Measure]?**

Le istruzioni su come configurare le attività nell&#39;app [!UICONTROL Marketo] Measure sono disponibili nell&#39;articolo Supporto delle attività di [!DNL Marketo Measure].

**Che cosa significano i diversi operatori?**

* è uguale a: corrispondenza esatta con il valore (alias: social)
* contiene: il testo si trova al centro (alias: &#42;social&#42;)
* inizia con: il valore inizia con il testo (ossia social&#42;)
* termina con: il valore termina con il testo (ovvero &#42;social)
* corrisponde a qualsiasi: è possibile aggiungere più valori separati da virgola. Se è necessario applicare [!UICONTROL starts with], [!UICONTROL ends with] o contiene operatori, utilizzare il carattere jolly (&#42;)
* maggiore di: utilizzato per campi numerici o campi data/ora
* minore di: utilizzato per campi numerici o campi data/ora

**In quale canale si trovano queste attività?**

Quando vengono creati la regola Attività e il nome della campagna [!DNL Marketo Measure] corrispondente, utilizza le definizioni dei canali online per posizionare tali campagne nel canale di marketing corretto. [!DNL Marketo Measure] può definire i canali utilizzando non solo il supporto e l&#39;origine, ma anche la campagna.

Nell’esempio precedente, per assegnare la campagna &quot;Chiamata in uscita {Assegnata a}&quot; al canale BDR, inserisci una riga nel file CSV dei canali online per il canale BDR con una definizione di campagna &quot;Chiamata in uscita&#42;&quot;. L’asterisco indica un valore jolly, pertanto tutte le campagne che iniziano con &quot;Chiamata in uscita&quot; ricadranno sotto il canale BDR, anziché dover creare una riga separata per ogni nome di campagna.
