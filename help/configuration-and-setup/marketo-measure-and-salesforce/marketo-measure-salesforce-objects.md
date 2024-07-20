---
unique-page-id: 18874582
description: "[!DNL Marketo Measure] oggetti Salesforce - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] oggetti Salesforce"
exl-id: d5d6f334-6531-40fa-b043-75b49d8f43d5
feature: Salesforce
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 0%

---

# [!DNL Marketo Measure] oggetti Salesforce {#marketo-measure-salesforce-objects}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedere ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

Quando [!DNL Marketo Measure] è installato in [!DNL Salesforce] (SFDC), vengono aggiunti diversi oggetti [!DNL Marketo Measure] personalizzati. In questo articolo viene fornita una spiegazione di alcuni degli oggetti [!DNL Marketo Measure] personalizzati. Alcuni oggetti aggiunti da [!DNL Marketo Measure] a [!DNL Salesforce] sono:

* [Buyer Touchpoint](#touchpoint)
* [Buyer Attribution Touchpoint](#attribution)
* [[!DNL Marketo Measure] persona](#person)
* [[!DNL Marketo Measure] test A/B](#ab)
* [[!DNL Marketo Measure] eventi](#events)

I punti di contatto acquisiti dagli elementi che si desidera monitorare verranno scritti negli oggetti personalizzati creati dall&#39;installazione del pacchetto [!DNL Bizible Salesforce].

Gli oggetti [!DNL Marketo Measure] sono correlati a specifici oggetti standard [!DNL Salesforce]. In questo modo è possibile creare un report sugli oggetti [!DNL Marketo Measure] e [!DNL Salesforce] insieme. La tabella seguente mostra l&#39;oggetto [!DNL Salesforce] a cui l&#39;oggetto [!DNL Marketo Measure] si riferisce.

![](assets/1-1.png)

## Buyer Touchpoint {#buyer-touchpoint}

L&#39;oggetto [!UICONTROL Buyer Touchpoint] (BT) racconta la storia di marketing di un singolo utente. Racchiude tutti i dati relativi ai punti di contatto di marketing generati da lead e contatti. L’BT mostra informazioni come il canale di marketing da cui proviene il punto di contatto o quale campagna pubblicitaria ha portato quel particolare lead/contatto al tuo sito web.

L&#39;oggetto BT è visibile nelle pagine Lead e Contatti come **Elenco correlato** (vedi immagine seguente).

![](assets/2-1.png)

Nell’elenco correlato all’BT vengono visualizzati tutti i punti di contatto che appartengono al lead o al contatto. Nell&#39;elenco sono presenti campi [!DNL Marketo Measure] personalizzati che forniscono ulteriori dettagli su ogni punto di contatto. Facendo clic sul numero Buyer Touchpoint ID si accede alla pagina Dettagli Buyer Touchpoint, che fornisce ulteriori dettagli sul punto di contatto, come la prima pagina Web visitata dal lead/contatto durante la sessione Web (**pagina di destinazione**).

## Buyer Attribution Touchpoint {#buyer-attribution-touchpoint}

L&#39;oggetto [!UICONTROL Buyer Attribution Touchpoint] racconta la storia delle interazioni di marketing dei tuoi contatti relative a un&#39;opportunità. Visualizza i dati di *attribuzione* relativi ai punti di contatto di marketing. Questo oggetto ti consente di vedere quanto credito di ricavi viene attribuito a ogni punto di contatto di marketing. Il tipo di modello di attribuzione utilizzato determinerà la percentuale di ricavi attribuiti ai punti di contatto.

I punti di contatto per l’attribuzione dell’acquirente (BAT) vengono creati solo dopo la creazione di un’opportunità relativa a contatti che dispongono di dati Buyer Touchpoint (BT). L’BAT non verrà creato senza un’opportunità. Una volta creata l&#39;opportunità, l&#39;oggetto BAT utilizzerà il campo [!DNL Salesforce] *Importo* dell&#39;opportunità per capire l&#39;importo dei ricavi da attribuire ai punti di contatto.

È necessario creare un **flusso di lavoro** se si utilizza un [campo Importo personalizzato](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md) per visualizzare le entrate nell&#39;oggetto opportunità. [!DNL Marketo Measure] non è in grado di leggere le informazioni visualizzate nei campi di importo personalizzati e di conseguenza non è in grado di popolare i dati di attribuzione dei ricavi sui punti di contatto. Questo flusso di lavoro utilizzerà il campo **[!DNL Marketo Measure]Importo opportunità**, uno dei campi personalizzati di [!DNL Marketo Measure], per mappare il valore di ricavo dal campo Importo personalizzato al campo Importo opportunità.

![](assets/3-1.png)

L&#39;oggetto BAT è visibile nell&#39;oggetto [!UICONTROL Opportunity], [!UICONTROL Contact] e [!UICONTROL Account] come elenco correlato. In questo elenco vengono visualizzati tutti i punti di contatto con i dati di attribuzione appartenenti a un’opportunità. Facendo clic su Buyer Attribution Touchpoint ID si aprirà la pagina Buyer Attribution Touchpoint Detail. Qui potrai vedere dati di attribuzione e informazioni più specifiche sulla provenienza del punto di contatto (simili a quelli forniti dall’oggetto Buyer Touchpoint).

## [!DNL Marketo Measure] persona {#marketo-measure-person}

L&#39;oggetto persona [!DNL Marketo Measure] mette in relazione gli oggetti Lead e Contact. Con Salesforce non è possibile creare report utilizzando l’oggetto Lead e Contact all’interno dello stesso report. Tramite la relazione con l&#39;oggetto lead e contatto, la persona [!DNL Marketo Measure] consente di creare rapporti su entrambi gli oggetti all&#39;interno dello stesso rapporto. Questa funzione è particolarmente utile quando un lead è stato convertito in un contatto. In un record Persona [!DNL Marketo Measure] verrà visualizzata una ricerca nel record Lead e/o Contatto corrispondente, un elenco correlato dei punti di contatto associati alla persona e l&#39;ID persona (che è sempre l&#39;indirizzo e-mail del lead/contatto). Poiché la persona [!DNL Marketo Measure] si riferisce all&#39;oggetto lead e contatto, non ci sarà mai un record persona [!DNL Marketo Measure] legato a un Buyer Attribution Touchpoint. Di seguito è riportato un esempio di record persona [!DNL Marketo Measure] in Salesforce:

![](assets/4.png)

## Test A/B [!DNL Marketo Measure] {#marketo-measure-a-b-test}

Se si eseguono test A/B tramite [!DNL Optimizely] o VWO (Visual Web Optimizer), è possibile collegare tali account all&#39;account [!DNL Marketo Measure] per visualizzare i dati dei test A/B in Salesforce. L&#39;oggetto test A/B [!DNL Marketo Measure] consente di estrarre i dati del test A/B da Optimizely/VWO e collegarli a lead e contatti.

![](assets/5.png)

L&#39;oggetto test A/B [!DNL Marketo Measure] viene visualizzato come elenco correlato nelle pagine [!UICONTROL Leads], [!UICONTROL Contacts] e [!UICONTROL Opportunity]. L’elenco fa emergere tutti gli esperimenti e le varianti che stai eseguendo in Optimizely o VWO, e ti consente di visualizzare gli esperimenti/le varianti in quanto si riferiscono a lead e contatti specifici.

## [!DNL Marketo Measure] eventi {#marketo-measure-events}

L&#39;oggetto [!DNL Marketo Measure] Events consente di tenere traccia di eventi specifici che si verificano sul sito Web. Per tenere traccia di eventi specifici che si verificano sul sito Web, è necessario aggiungere alle pagine il codice personalizzato oltre al codice JavaScript [!DNL Marketo Measure]. Le informazioni acquisite verranno visualizzate nell&#39;elenco correlato agli oggetti [!DNL Marketo Measure], disponibile nelle pagine [!UICONTROL Leads], [!UICONTROL Contacts] e [!UICONTROL Opportunity]. L&#39;oggetto eventi [!DNL Marketo Measure] *non è* collegato ai dati di attribuzione. Lo scopo di questo oggetto è quello di verificare se le persone stanno eseguendo azioni specifiche sul sito web.

## [!DNL Marketo Measure] campi {#marketo-measure-fields}

I dati acquisiti dal JavaScript [!DNL Marketo Measure] vengono inviati nei campi [!DNL Marketo Measure] personalizzati all&#39;interno degli oggetti [!DNL Marketo Measure]. Alcuni campi sono presenti solo su determinati oggetti. Puoi rivedere il [glossario di [[!DNL Marketo Measure] campi]](/help/introduction-to-marketo-measure/overview-resources/glossary-of-marketo-measure-fields.md) e una [visualizzazione dei relativi [!DNL Marketo Measure] oggetti](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-object-and-field-taxonomy.md).

## [!DNL Marketo Measure] report e dashboard {#marketo-measure-reports-and-dashboards}

I report e le dashboard di [!DNL Marketo Measure] aggiunti a [!DNL Salesforce] forniscono funzionalità predefinite di reporting e visualizzazione dei dati. Si tratta di report [!DNL Marketo Measure] di base che consentono di organizzare, analizzare e comprendere rapidamente i dati dei punti di contatto.
