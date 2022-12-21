---
unique-page-id: 18874582
description: "[!DNL Marketo Measure] Oggetti Salesforce - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] Oggetti Salesforce"
exl-id: d5d6f334-6531-40fa-b043-75b49d8f43d5
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 0%

---

# [!DNL Marketo Measure] Oggetti Salesforce {#marketo-measure-salesforce-objects}

>[!NOTE]
>
>È possibile visualizzare istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella nostra documentazione, ma vedi ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riflesso nel tuo CRM presto.

Quando [!DNL Marketo Measure] è installato in [!DNL Salesforce] (SFDC), diverse personalizzazioni [!DNL Marketo Measure] Gli oggetti vengono aggiunti. Questo articolo fornisce una spiegazione di diversi di questi [!DNL Marketo Measure] Oggetti. Alcuni oggetti [!DNL Marketo Measure] aggiunge a [!DNL Salesforce] sono:

* [Punto di contatto dell&#39;acquirente](#touchpoint)
* [Punto di contatto dell’attribuzione dell’acquirente](#attribution)
* [[!DNL Marketo Measure] Persona](#person)
* [[!DNL Marketo Measure] Test A/B](#ab)
* [[!DNL Marketo Measure] Eventi](#events)

I punti di contatto acquisiti dalle cose da tracciare verranno scritti negli oggetti personalizzati creati dall&#39;installazione della [!DNL Bizible Salesforce] pacchetto.

[!DNL Marketo Measure] Gli oggetti si riferiscono a specifici standard [!DNL Salesforce] Oggetti. In questo modo puoi creare rapporti su [!DNL Marketo Measure] e [!DNL Salesforce] Oggetti insieme. La tabella seguente mostra quali [!DNL Salesforce] Oggetto [!DNL Marketo Measure] L&#39;oggetto si riferisce a.

![](assets/1-1.png)

## Punto di contatto dell&#39;acquirente {#buyer-touchpoint}

La [!UICONTROL Buyer Touchpoint] (BT) Object racconta la storia di marketing di un individuo. Contiene tutti i dati relativi ai punti di contatto di marketing generati da Lead e Contatti. Il BT mostra informazioni come il canale di marketing da cui proviene il punto di contatto o quale campagna pubblicitaria ha portato quel particolare lead/contatto al tuo sito web.

L&#39;oggetto BT è visibile nelle pagine Lead e Contatti come **Elenco correlato** (vedi immagine qui sotto).

![](assets/2-1.png)

Nell’elenco correlato al BT vengono visualizzati tutti i punti di contatto appartenenti al lead o al contatto. Nell’elenco sono personalizzati [!DNL Marketo Measure] Campi che forniscono ulteriori dettagli su ciascun punto di contatto. Facendo clic sul numero di ID punto di contatto dell’acquirente , potrai accedere alla pagina Dettagli punto di contatto dell’acquirente , che fornisce ulteriori dettagli sul punto di contatto, come la prima pagina web visitata dal lead/contatto durante la sessione web (**pagina di destinazione**).

## Punto di contatto dell’attribuzione dell’acquirente {#buyer-attribution-touchpoint}

La [!UICONTROL Buyer Attribution Touchpoint] Oggetto racconta la storia delle interazioni di marketing dei tuoi contatti relative a un’opportunità. Visualizza la *attribuzione* dati relativi ai punti di contatto di marketing. Questo oggetto ti consente di vedere la quantità di credito di ricavi attribuito a ogni punto di contatto di marketing. Il tipo di modello di attribuzione utilizzato determinerà la percentuale di ricavi attribuiti ai punti di contatto.

I punti di contatto di attribuzione dell’acquirente (BAT) vengono creati solo una volta creata un’opportunità che si riferisce ai contatti che dispongono di dati di punto di contatto dell’acquirente (BT). Le BAT non verranno create senza un’opportunità. Una volta creata l’opportunità, l’oggetto BAT utilizzerà il [!DNL Salesforce] *Importo* campo Opportunità per comprendere la quantità di ricavi da attribuire ai punti di contatto.

A **workflow** deve essere creato se utilizzi un [campo Importo personalizzato](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md) per visualizzare i ricavi relativi all&#39;oggetto opportunità. [!DNL Marketo Measure] non è in grado di leggere le informazioni visualizzate nei campi Importo personalizzati e, di conseguenza, non è in grado di popolare i dati di attribuzione dei ricavi sui punti di contatto. Questo flusso di lavoro utilizza la variabile **[!DNL Marketo Measure]Importo opportunità** Campo, uno dei [!DNL Marketo Measure] campi personalizzati, per mappare il valore dei ricavi dal campo Importo personalizzato al campo Importo opportunità.

![](assets/3-1.png)

L&#39;oggetto BAT è visibile sul [!UICONTROL Opportunity], [!UICONTROL Contact]e [!UICONTROL Account] Oggetto come elenco correlato. Questo elenco visualizza tutti i punti di contatto con i dati di attribuzione appartenenti a un’opportunità. Fai clic su nell’ID punto di contatto dell’attribuzione dell’acquirente per accedere alla pagina Dettagli punto di contatto dell’attribuzione dell’acquirente . Qui puoi vedere dati di attribuzione e informazioni più specifici sulla provenienza del punto di contatto (simili a quelli forniti dall’oggetto punto di contatto dell’acquirente).

## [!DNL Marketo Measure] Persona {#marketo-measure-person}

La [!DNL Marketo Measure] Oggetto Persona mette in relazione gli oggetti Lead e Contatto. Con Salesforce non è possibile creare rapporti utilizzando gli oggetti Lead e Contatto nello stesso rapporto. Per quanto riguarda l&#39;oggetto Lead e Contact, il [!DNL Marketo Measure] Persona consente di creare rapporti su entrambi gli oggetti all’interno dello stesso rapporto. Questo è particolarmente utile quando un lead è stato convertito in un contatto. Su [!DNL Marketo Measure] Record di persona : vedrai una ricerca del corrispondente record Lead e/o Contatto, un elenco correlato dei punti di contatto associati alla persona e l’ID persona (che è sempre l’indirizzo e-mail del lead/contatto). Dal momento che [!DNL Marketo Measure] La persona si riferisce all&#39;oggetto Lead &amp; Contact, non ci sarà mai un [!DNL Marketo Measure] Record personale associato a un punto di contatto di attribuzione dell’acquirente. Di seguito è riportato un esempio di [!DNL Marketo Measure] Record personale in Salesforce:

![](assets/4.png)

## [!DNL Marketo Measure] Test A/B {#marketo-measure-a-b-test}

Se esegui test A/B tramite [!DNL Optimizely] o VWO (Visual Web Optimizer), è possibile collegare questi account al [!DNL Marketo Measure] per visualizzare i dati dei test A/B in Salesforce. La [!DNL Marketo Measure] L’oggetto Test A/B consente essenzialmente di prendere i dati del test A/B da Optimizely/VWO e di collegare i dati a Lead e contatti.

![](assets/5.png)

La [!DNL Marketo Measure] L’oggetto Test A/B viene visualizzato come Elenco correlato in [!UICONTROL Leads], [!UICONTROL Contacts] e [!UICONTROL Opportunity] pagine. L’elenco consente di visualizzare tutti gli esperimenti e le varianti in esecuzione in Optimizely o VWO e di visualizzare gli esperimenti/varianti in base a specifici Lead e Contatti.

## [!DNL Marketo Measure] Eventi {#marketo-measure-events}

La [!DNL Marketo Measure] Oggetto Eventi consente di tenere traccia di eventi specifici che si verificano sul sito web. Per tenere traccia di eventi specifici che si verificano sul sito web, oltre alle pagine è necessario aggiungere codice personalizzato [!DNL Marketo Measure] Javascript. Le informazioni acquisite verranno visualizzate all&#39;interno del [!DNL Marketo Measure] Elenco correlato agli oggetti, disponibile nella [!UICONTROL Leads], [!UICONTROL Contacts] e [!UICONTROL Opportunity] pagine. La [!DNL Marketo Measure] Oggetto Events *non* Lega ai dati di attribuzione. Lo scopo di questo oggetto è quello di vedere se le persone stanno intraprendendo azioni specifiche sul tuo sito web.

## [!DNL Marketo Measure] Campi {#marketo-measure-fields}

Dati acquisiti dal [!DNL Marketo Measure] Javascript verrà inviato nell’app personalizzata [!DNL Marketo Measure] Campi all’interno della [!DNL Marketo Measure] Oggetti. Alcuni campi saranno presenti solo su determinati oggetti. Per un glossario di tutti i [!DNL Marketo Measure] campi, per favore [fai clic qui](/help/introduction-to-marketo-measure/overview-resources/glossary-of-marketo-measure-fields.md). Per una visualizzazione di cui [!DNL Marketo Measure] Oggetto [!DNL Marketo Measure] Il campo si riferisce al [fai clic qui](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-object-and-field-taxonomy.md).

## [!DNL Marketo Measure] Report e dashboard {#marketo-measure-reports-and-dashboards}

La [!DNL Marketo Measure] Report e dashboard aggiunti al [!DNL Salesforce] offre funzionalità di reporting e visualizzazione dei dati predefinite. Questi sono fondamentali [!DNL Marketo Measure] rapporti per consentirti di organizzare, analizzare e comprendere rapidamente i dati dei punti di contatto.
