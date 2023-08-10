---
unique-page-id: 18874598
description: Impostazione canale personalizzato offline - [!DNL Marketo Measure] - Documentazione del prodotto
title: Impostazione canale personalizzato offline
exl-id: c5697714-1a79-40bd-8b7c-e10768f4ef67
feature: Channels
source-git-commit: 3df1bd288ebd65f75a2ed52d7c8a6faf50c7ff1f
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 0%

---

# Impostazione canale personalizzato offline {#offline-custom-channel-setup}

## Guida introduttiva {#getting-started}

Confronto con come [!DNL Marketo Measure] gestisce le regole del canale online; noterai che le regole del canale offline non richiedono l’utilizzo di un foglio di calcolo. Tuttavia, nel piano di implementazione è ancora presente un foglio, perché può essere utile per riflettere sul modo in cui organizzare i canali offline.

Il foglio di calcolo è composto da tre colonne:

![](assets/1-2.png)

**[!UICONTROL Salesforce]Tipo di campagna** : aggiungi i tipi di campagna identificati in [!DNL Salesforce] qui

* Ad esempio, potrebbe trattarsi di un’e-mail, un webinar, una conferenza o di qualsiasi valore creato per questo campo a cui si desidera attribuire punti di contatto.

**[!UICONTROL Channel]** - aggiungere i vari canali di marketing

**[!UICONTROL Subchannel]** : aggiungi qui eventuali sottocanali corrispondenti

## Logica canale offline {#offline-channel-logic}

[!DNL Marketo Measure] la logica del canale offline è determinata dall’oggetto Campaign, in particolare dal [!DNL Salesforce] Tipo di campagna. Ogni impegno offline deve avere un [!DNL Salesforce] Tipo di campagna, ad esempio cena o fiera, perché [!DNL Marketo Measure] si basa su questo campo per capire a quale canale e sottocanale mappare.

I tipi di campagna SFDC verranno visualizzati nella scheda del canale offline, elencata in [!DNL Salesforce] Tipo di campagna. Tieni presente che [!DNL Marketo Measure] può importare solo i tipi di campagna SFDC per le campagne a cui sono associati punti di contatto buyer.

![](assets/2-2.png)

Qui è possibile creare la mappatura Canale/Sottocanale nel [!DNL Marketo Measure] app. Questo richiederà probabilmente la creazione di nuovi canali e sottocanali nel [!DNL Marketo Measure] , che viene eseguita nella sezione Create Channels (Crea canali) dell&#39;app, come illustrato nell&#39;immagine seguente. È necessario creare nuovi canali e subcanali per [!DNL Marketo Measure] per capire dove inviare i punti di contatto. Puoi decidere come mappare i tipi di campagna.

![](assets/3-2.png)

## Esempio di mappatura dei canali {#channel-mapping-example}

Ad esempio, immagina di partecipare due [!DNL Salesforce] conferenze all&#39;anno. Tuttavia, ogni conferenza è molto diversa e ha un pubblico di destinazione univoco. Vuoi sapere quale dei due apporta più valore. Nel tuo [!DNL Salesforce] ambiente, puoi assegnare all’evento di gennaio il tipo di campagna &quot;Conferenza&quot;, denomina il tuo canale &quot;[!DNL Salesforce],&quot; e il tuo sottocanale &quot;Conferenza di gennaio&quot;.

Ora volete fare lo stesso per la conferenza di giugno. Visto che anche questa è una conferenza, si può dare lo stesso Tipo di campagna, in questo caso, &quot;Conferenza&quot;. Il canale è lo stesso, [!DNL Salesforce], e il sottocanale di questa seconda conferenza è &quot;Conferenza di giugno&quot;. Tutto ciò ha senso da un punto di vista organizzativo. Tuttavia, è molto confuso con [!DNL Marketo Measure] per leggere e applicare queste regole, in quanto entrambe le campagne hanno lo stesso tipo di campagna. [!DNL Marketo Measure] lo script non può mappare i dati da un tipo a due diversi canali secondari. Ciò significa che dovrai creare un nuovo Tipo di campagna per ogni sottocanale, ma che i sottocanali possono avere lo stesso canale.

Di seguito è riportato un esempio di logica [!DNL Marketo Measure] non è in grado di leggere:

![](assets/4-2.png)

Nello scenario precedente, creerai un tipo di campagna univoco perché non puoi mappare lo stesso tipo di campagna a due canali secondari diversi. È invece necessario impostare tipi univoci come i seguenti:

![](assets/5-2.png)

Eventuali tipi di campagna esistenti devono essere inclusi nella mappa del canale e &quot;NULL&quot; deve essere aggiunto come canale.

Prenditi del tempo per entrare in [!DNL Salesforce] per determinare il numero e la natura dei tipi di record esistenti che si desidera includere e se è necessario creare ulteriori campagne in base alle informazioni riportate sopra. Una volta completate tutte le informazioni necessarie, puoi procedere al caricamento.

Ulteriori informazioni su [sincronizzazione offline [!DNL Salesforce] Campagne con [!DNL Marketo Measure]](/help/channel-tracking-and-setup/offline-channels/deprecated-processes/syncing-offline-campaigns.md).

## Gestione delle campagne SFDC per le attività di marketing online {#handling-sfdc-campaigns-for-online-marketing-efforts}

La creazione di [!DNL Salesforce] campagne per tenere traccia delle varie attività di marketing digitale. Non c’è alcun problema con questa pratica; tuttavia, è importante trattare queste campagne in modo diverso rispetto alle vere campagne offline, come ad esempio direct mailing o conferenze. Le campagne correlate a eventi digitali (interazioni che si verificano sul tuo sito web) non devono essere sincronizzate con [!DNL Marketo Measure]. La sincronizzazione di queste campagne comporterebbe la duplicazione dei punti di contatto perché il [!DNL Marketo Measure] JavaScript sta già tenendo traccia delle attività online.

Un altro suggerimento per la gestione delle campagne per le attività online è quello di mappare [!DNL Salesforce] Tipo di campagna su NULL. A questo scopo, crea un canale in [!DNL Marketo Measure] app con titolo NULL, come illustrato nell’immagine seguente. Questo si trova nel [!DNL Marketo Measure] app sotto **Crea canali** sezione. Questo sarà utile nel caso in cui una campagna che non deve essere sincronizzata venga sincronizzata accidentalmente. È facile trovare la campagna e correggere lo stato di sincronizzazione osservando tutti gli elementi inseriti nel bucket con NULL.

![](assets/6-2.png)

## Immissione delle regole del canale offline nell’app {#entering-your-offline-channel-rules-to-the-app}

Dopo aver modificato e aggiornato il foglio di calcolo con le regole personalizzate, il passaggio successivo consiste nel ricreare la mappatura del canale in [!DNL Marketo Measure] app: non verrà caricato un foglio di calcolo per i canali offline. Piuttosto, immetterai le informazioni nelle caselle dell’elenco a discesa come mostrato nell’immagine seguente. Per trovare l’elemento, fai clic su **[!UICONTROL Offline Channels]** sotto **[!UICONTROL Channels]** sezione.

![](assets/7-2.png)

>[!TIP]
>
>Vuoi determinare _quando_ a [!DNL Salesforce] Il tipo di campagna viene incluso in [!DNL Marketo Measure] mappatura dei canali? È sufficiente andare a **[!UICONTROL Setup]** > **[!UICONTROL Campaigns]** > **[!UICONTROL Fields]** > **[!UICONTROL Type]**. Puoi quindi vedere quali valori sono presenti nell’elenco a discesa e quali sono inattivi. Quelli inattivi non verranno visualizzati come tipo selezionabile nel nostro &quot;[!UICONTROL Offline Channels]&quot;. Tieni presente che questo processo può richiedere da qualche minuto fino a 48 ore.

Clic **[!UICONTROL Save]** quando hai finito e [!DNL Marketo Measure] carica le modifiche ed elabora nuovamente i dati.

>[!MORELIKETHIS]
>
>* [[!DNL Marketo Measure] University: mappatura dei canali offline](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c630eca34d9f0367662b77f)
>
>* [[!DNL Marketo Measure] University: sincronizzazione di campagne offline](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63286e34d9f0367662b78b)
>
>* [Integrazione dei programmi di Marketo Engage](/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md#channel-mapping)
