---
description: "[!DNL Marketo Measure] Panoramica di 101 rapporti - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Panoramica di 101 rapporti"
exl-id: 83977b81-8055-47fd-8a6b-5ef32d280269
feature: Reporting
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 0%

---

# [!DNL Marketo Measure] Panoramica di 101 rapporti {#marketo-measure-101-reports-overview}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedi ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

Tutti [!DNL Marketo Measure] clienti che utilizzano [!DNL Marketo Measure] e [!DNL Salesforce] hanno accesso alla cartella &quot;Rapporti sui punti di contatto dell’acquirente&quot; all’interno della loro istanza SFDC. Questa cartella contiene una serie di rapporti predefiniti che possono aiutarti a iniziare a generare rapporti con i dati dei punti di contatto dell’acquirente.

![](assets/bizible-101-reports-overview-1.png)

Anche se molti di questi rapporti hanno obiettivi di reporting specifici già stabiliti, ce ne sono sei &quot;._[!DNL Marketo Measure]101..._&quot; rappresentati da tre tipi di rapporti chiave che coprono la maggior parte delle esigenze di reporting.

* Lead con punti di contatto dell&#39;acquirente
* [!DNL Marketo Measure] Persone con punti di contatto dell&#39;acquirente
* Punti di contatto di attribuzione acquirente con opportunità

![](assets/bizible-101-reports-overview-2.png)

Questi report forniscono i campi e l&#39;infrastruttura di base necessari per qualsiasi [!DNL Marketo Measure] report correlato che si desidera creare. Invitiamo tutti i clienti, nuovi e meno recenti, a iniziare con questi rapporti quando esplorano le domande di attribuzione marketing. Qui sotto troverete una spiegazione di ciascuno dei sei &quot;._[!DNL Marketo Measure]101..._&quot; rapporti.

_Se non riesci a trovare la cartella Rapporto Punti di contatto dell&#39;acquirente o i sei &quot;_[!DNL Marketo Measure] 101..._&quot; rapporti all’interno di tale cartella, contatta il supporto per assistenza._

**Lead con punti di contatto dell&#39;acquirente** | Le due varianti seguenti generano rapporti sui lead e sui relativi punti di contatto dell&#39;acquirente. Anche se utilizzano lo stesso tipo di rapporto di base, sono raggruppati per metriche diverse, ID lead e Canale di marketing, per fornire due visualizzazioni chiave dei dati. Questo tipo di rapporto è progettato per funnel reporting ed è ideale quando si vuole esplorare il modo in cui i lead sono coinvolti nelle attività di marketing. Prima di qualsiasi personalizzazione, i due rapporti seguenti mostrano quanto segue:

**[!DNL Marketo Measure]101: Lead per canale** | Una panoramica generale del modo in cui i canali di marketing influenzano la creazione di lead e i relativi impegni aggiuntivi.
**[!DNL Marketo Measure]101: Lead per ID** | Questo mostra la storia Lead ed è un rapporto molto più granulare, che mostra ogni singolo Lead e i relativi punti di contatto dell&#39;acquirente.

**Lead/Contatti con i punti di contatto dell&#39;acquirente** | Questi rapporti sono comunemente denominati [!DNL Marketo Measure] Rapporti sulle persone. Utilizzano [!DNL Marketo Measure] oggetto personalizzato _[!DNL Marketo Measure]Persona_ a differenza dell&#39;oggetto Lead nei report sopra menzionati.

Il [!DNL Marketo Measure] Oggetto Person mette in relazione gli oggetti Lead e Contact. Pronti all’uso, [!DNL Salesforce] non fornisce l&#39;opzione per creare report utilizzando l&#39;oggetto Lead e Contact nello stesso report. Tramite la relazione con l&#39;oggetto lead e contatto utilizzando l&#39;identificatore univoco di una persona, la sua e-mail, il [!DNL Marketo Measure] All’interno dello stesso rapporto, la persona può generare rapporti sui punti di contatto lead e acquirenti correlati ai contatti. Questo tipo di rapporto è ideale quando si desidera convalidare uno dei [!DNL Marketo Measure] Impostazioni account in quanto è il livello più inclusivo di reporting dei punti di contatto.

Le due varianti di rapporto seguenti utilizzano lo stesso tipo di rapporto, ma sono raggruppate per metriche diverse: ID persona (e-mail) rispetto al canale di marketing. Questi sono i report migliori per funnel/mid of funnel quando si vuole esplorare il modo in cui i lead e i contatti interagiscono con le attività di marketing. Prima di qualsiasi personalizzazione, i due rapporti seguenti mostrano quanto segue:

**[!DNL Marketo Measure]101: lead/contatti per canale** | Una panoramica generale del modo in cui i canali di marketing influenzano la creazione di lead o contatti e i relativi impegni aggiuntivi. Questo rapporto è ideale quando si cerca di comprendere il coinvolgimento totale tra i canali di marketing e quali canali di marketing stanno guidando nuovi nomi all’interno della tua istanza Salesforce.
**[!DNL Marketo Measure]101: lead/contatti per ID** | Questo mostra ogni [!DNL Marketo Measure] La storia della persona ed è un rapporto molto più granulare, che mostra ogni individuo e i suoi punti di contatto acquirente, indipendentemente dal fatto che il punto di contatto si sia verificato quando era un lead o come un contatto.

**Opportunità con punti di contatto di attribuzione buyer** | Gli ultimi due &quot;_[!DNL Marketo Measure]101..._&quot;I rapporti sono la parte inferiore dei rapporti funnel che visualizzano i dati dei punti di contatto di attribuzione buyer relativi alle opportunità. La differenza fondamentale per questi rapporti è che sono costruiti su _Punti di contatto di attribuzione acquirente_ che si riferiscono ai dati a livello di opportunità e opportunità, ad esempio i ricavi. Ogni volta che desideri generare rapporti sulle opportunità o sui ricavi attribuiti, devi utilizzare questo tipo di rapporto. I due rapporti seguenti utilizzano lo stesso tipo di rapporto, ma sono raggruppati per metriche diverse, ID opportunità e Canale di marketing. Prima di qualsiasi personalizzazione, i due rapporti seguenti mostrano quanto segue:

**[!DNL Marketo Measure]101: Opportunità per canale** | Una visione di alto livello di come i canali di marketing influenzano e generano ricavi attribuiti nelle opportunità.
**[!DNL Marketo Measure]101: Opportunità per ID** | Questa versione di report granulare mostra il percorso completo delle opportunità. In questo rapporto puoi vedere ogni punto di contatto di attribuzione dell’acquirente associato a un’opportunità e i relativi ricavi attribuiti tramite i vari modelli di attribuzione.

È considerata una best practice trattare il problema &quot;._[!DNL Marketo Measure]101..._&quot; i report come modelli per le tue esigenze di reporting. Iniziare da uno dei rapporti di cui sopra ti farà risparmiare tempo e assicurarti di lavorare con i campi corretti relativi a [!DNL Marketo Measure] dati. Assicurati sempre di &quot;Salvare con nome&quot; ogni volta che apporti personalizzazioni al &quot;_[!DNL Marketo Measure]101..._&quot; modelli per mantenere la variante originale del rapporto.

La cartella &quot;Rapporti sui punti di contatto dell&#39;acquirente&quot; è stata progettata per aiutarti a iniziare a utilizzare [!DNL Marketo Measure] per i rapporti utilizzabili, è necessario personalizzare tali rapporti in modo che siano personalizzati in base alle tue esigenze di reporting. dovrai aggiungere i filtri necessari per garantire che i record all’interno del rapporto (e i relativi punti di contatto) siano allineati con l’obiettivo di reporting.

Quando hai familiarità con &quot;_[!DNL Marketo Measure]101..._&quot;, potrebbe essere utile ricrearli dai tipi di rapporto personalizzati per esigenze di reporting più personalizzate. Creazione di [[!DNL Marketo Measure] Tipi di rapporti personalizzati](/help/marketo-measure-salesforce-reporting/new-report-types/creating-custom-marketo-measure-report-types.md) ti consentirà di estrarre campi personalizzati che potrebbero essere comunemente utilizzati in altri rapporti di gestione delle relazioni con i clienti. Questo ti aiuterà a portarti [!DNL Marketo Measure] reportistica di livello superiore!
