---
unique-page-id: 18874598
description: Configurazione del canale personalizzato offline - [!DNL Marketo Measure] - Documentazione del prodotto
title: Configurazione del canale personalizzato offline
exl-id: c5697714-1a79-40bd-8b7c-e10768f4ef67
source-git-commit: 02f686645e942089df92800d8d14c76215ae558f
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 0%

---

# Configurazione del canale personalizzato offline {#offline-custom-channel-setup}

## Introduzione {#getting-started}

Rispetto a come [!DNL Marketo Measure] gestisce le regole del canale online, noterai che le regole del canale offline non richiedono l’uso di un foglio di calcolo. Tuttavia, esiste ancora un foglio fornito nel piano di implementazione perché può essere utile per riflettere sul modo in cui desideri organizzare i canali offline.

Il foglio di calcolo ha tre colonne:

![](assets/1-2.png)

**[!UICONTROL Salesforce]Tipo di campagna** - aggiungi i tipi di campagna identificati in [!DNL Salesforce] qui

* Ad esempio, potrebbe trattarsi di un&#39;e-mail, un webinar, una conferenza o qualsiasi valore creato per questo campo a cui si desidera attribuire i punti di contatto.

**[!UICONTROL Channel]** - aggiungi qui i vari canali di marketing

**[!UICONTROL Subchannel]** - aggiungi eventuali sottocanali corrispondenti qui

## Logica canale offline {#offline-channel-logic}

[!DNL Marketo Measure] la logica del canale offline è determinata dall’oggetto Campaign, in particolare il [!DNL Salesforce] Tipo di campagna. Ogni sforzo offline deve avere un [!DNL Salesforce] Tipo di campagna, ad esempio cena o fiera, perché [!DNL Marketo Measure] si affida a questo campo per capire a quale canale e subChannel mappare.

I tipi di campagna SFDC verranno visualizzati nella scheda Canale offline, elencata in [!DNL Salesforce] Tipo di campagna. Si prega di notare che [!DNL Marketo Measure] è in grado di importare solo i tipi di campagne SFDC per le campagne a cui sono associati punti di contatto dell’acquirente.

![](assets/2-2.png)

Qui puoi creare la mappatura Canale/Canale secondario nel [!DNL Marketo Measure] app. Sarà probabilmente necessario creare nuovi canali e sottocanali nel [!DNL Marketo Measure] app, che viene eseguita nella sezione Crea canali dell’app, mostrata nell’immagine seguente. È necessario creare nuovi canali e sottocanali per [!DNL Marketo Measure] per capire dove inviare i punti di contatto. Puoi decidere come mappare i tipi di campagna.

![](assets/3-2.png)

## Esempio di mappatura dei canali {#channel-mapping-example}

Ad esempio, immaginate di partecipare a due [!DNL Salesforce] conferenze all&#39;anno. Ogni conferenza, tuttavia, è molto diversa e ha un pubblico di destinazione unico. Vuoi sapere quale dei due dà più valore. Nel tuo [!DNL Salesforce] ambiente, puoi assegnare all’evento di gennaio il tipo di campagna &quot;Conferenza&quot;, denomina il canale &quot;[!DNL Salesforce],&quot; e il tuo canale secondario &quot;Conferenza di gennaio&quot;.

Ora volete fare lo stesso per la conferenza di giugno. Dato che si tratta anche di una conferenza, è possibile assegnargli lo stesso tipo di campagna, in questo caso, &quot;Conferenza&quot;. Il canale è lo stesso, [!DNL Salesforce]e il canale secondario di questa seconda conferenza è &quot;Conferenza di giugno&quot;. Questo ha senso dal punto di vista organizzativo. Tuttavia, è molto confuso con il [!DNL Marketo Measure] per leggere e applicare queste regole perché entrambe le campagne hanno lo stesso tipo di campagna. [!DNL Marketo Measure] lo script non è in grado di mappare dati da un tipo a due diversi sottocanali. Ciò significa che dovrai creare un nuovo tipo di campagna per ogni canale secondario, ma i canali secondari possono avere lo stesso canale.

Di seguito è riportato un esempio di logica che [!DNL Marketo Measure] non sono in grado di leggere:

![](assets/4-2.png)

Nello scenario precedente, desideri creare un tipo di campagna univoco perché non puoi mappare lo stesso tipo di campagna su due diversi canali secondari. Imposta invece tipi univoci come segue:

![](assets/5-2.png)

Eventuali tipi di campagna esistenti devono essere inclusi nella mappa del canale e deve essere aggiunto come canale &quot;NULL&quot;.

Prenditi del tempo per entrare [!DNL Salesforce] per determinare il numero e la natura dei tipi di record esistenti da includere e se è necessario creare campagne aggiuntive in base alle informazioni di cui sopra. Dopo aver compilato tutte le informazioni necessarie, puoi effettuare il caricamento.

Ulteriori informazioni [sincronizzazione offline [!DNL Salesforce] Campagne con [!DNL Marketo Measure]](/help/channel-tracking-and-setup/offline-channels/syncing-offline-campaigns.md).

## Gestione delle campagne SFDC per gli sforzi di marketing online {#handling-sfdc-campaigns-for-online-marketing-efforts}

È comune per i team di marketing creare [!DNL Salesforce] campagne per tenere traccia delle varie attività di marketing digitale. Questa pratica non presenta problemi; tuttavia, è importante trattare queste campagne in modo diverso rispetto alle vere campagne offline, ad esempio direct mailing o conferenze. Le campagne correlate a eventi digitali (interazioni che si verificano sul sito web) non devono essere sincronizzate con [!DNL Marketo Measure]. La sincronizzazione di queste campagne comporterebbe la duplicazione di punti di contatto perché il [!DNL Marketo Measure] JavaScript sta già monitorando gli sforzi online.

Un altro suggerimento per la gestione delle campagne per le attività online è mappare [!DNL Salesforce] Tipo di campagna su NULL. A questo scopo, crea prima un canale nel [!DNL Marketo Measure] l’app ha titolo NULL come mostrato nell’immagine seguente. Si trova nella [!DNL Marketo Measure] app sotto **Crea canali** sezione . Questa opzione è utile nel caso in cui una campagna che non deve essere sincronizzata venga sincronizzata accidentalmente. È facile trovare la campagna e correggere lo stato di sincronizzazione guardando tutti gli elementi inseriti in NULL.

![](assets/6-2.png)

## Inserimento delle regole del canale offline nell’app {#entering-your-offline-channel-rules-to-the-app}

Dopo aver modificato e aggiornato il foglio di calcolo con le regole personalizzate, il passaggio successivo consiste nel ricreare la mappatura del canale nel [!DNL Marketo Measure] app: non puoi caricare un foglio di calcolo per i canali offline. Le informazioni verranno invece inserite nelle caselle di selezione come mostrato nell’immagine seguente. Questa operazione si trova facendo clic su **[!UICONTROL Offline Channels]** in **[!UICONTROL Channels]** sezione .

![](assets/7-2.png)

>[!TIP]
>
>Vuoi determinare _quando_ a [!DNL Salesforce] Il tipo di campagna viene estratto in [!DNL Marketo Measure] mappatura canale? Basta andare a **[!UICONTROL Setup]** > **[!UICONTROL Campaigns]** > **[!UICONTROL Fields]** > **[!UICONTROL Type]**. Puoi quindi vedere quali valori si trovano nell’elenco di selezione e quali sono inattivi. Quelli inattivi non vengono visualizzati come tipo selezionabile nel nostro &quot;[!UICONTROL Offline Channels]&quot; sezione. Tieni presente che questo processo può richiedere da qualche minuto a 48 ore.

Fai clic su **[!UICONTROL Save]** quando hai finito e [!DNL Marketo Measure] carica le modifiche e rielabora i dati.

>[!MORELIKETHIS]
>
>* [[!DNL Marketo Measure] Università: Mappatura dei canali offline](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c630eca34d9f0367662b77f)
>
>* [[!DNL Marketo Measure] Università: Sincronizzazione delle campagne offline](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63286e34d9f0367662b78b)
>
>* [Integrazione dei programmi di Marketo Engage](/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md#channel-mapping)

