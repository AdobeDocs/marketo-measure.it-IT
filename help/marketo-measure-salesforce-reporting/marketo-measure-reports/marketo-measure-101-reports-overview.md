---
description: Panoramica di [!DNL Marketo Measure] 101 report - [!DNL Marketo Measure]
title: Panoramica di [!DNL Marketo Measure] 101 report
exl-id: 83977b81-8055-47fd-8a6b-5ef32d280269
feature: Reporting
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 0%

---

# Panoramica di [!DNL Marketo Measure] 101 report {#marketo-measure-101-reports-overview}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedere ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

Tutti i clienti [!DNL Marketo Measure] che utilizzano [!DNL Marketo Measure] e [!DNL Salesforce] hanno accesso alla cartella &quot;Rapporti sui punti di contatto dell&#39;acquirente&quot; all&#39;interno della propria istanza di SFDC. Questa cartella contiene una serie di rapporti predefiniti che possono aiutarti a iniziare a generare rapporti con i dati di Buyer Touchpoint.

![](assets/bizible-101-reports-overview-1.png)

Anche se molti di questi report hanno obiettivi di reporting specifici già stabiliti, esistono sei &quot;_[!DNL Marketo Measure]101..._&quot; rappresentati da tre tipi di report chiave che coprono la maggior parte delle esigenze di reporting.

* Lead con punti di contatto dell&#39;acquirente
* [!DNL Marketo Measure] persone con punti di contatto dell&#39;acquirente
* Punti di contatto di attribuzione acquirente con opportunità

![](assets/bizible-101-reports-overview-2.png)

Questi report forniscono i campi e l&#39;infrastruttura di base necessari per qualsiasi report correlato a [!DNL Marketo Measure] che si desidera creare. Invitiamo tutti i clienti, nuovi e meno recenti, a iniziare con questi rapporti quando esplorano le domande di attribuzione marketing. Di seguito è riportata una spiegazione di ciascuno dei sei report &quot;_[!DNL Marketo Measure]101..._&quot;.

_Se non riesci a trovare la cartella Report punti di contatto acquirenti o i sei report &quot;_[!DNL Marketo Measure] 101..._&quot; all&#39;interno di tale cartella, contatta il supporto tecnico._

**Lead con punti di contatto acquirenti** | Le due varianti seguenti generano rapporti sui lead e sui relativi punti di contatto dell&#39;acquirente. Anche se utilizzano lo stesso tipo di rapporto di base, sono raggruppati per metriche diverse, ID lead e Canale di marketing, per fornire due visualizzazioni chiave dei dati. Questo tipo di rapporto è progettato per funnel reporting ed è ideale quando si vuole esplorare il modo in cui i lead sono coinvolti nelle attività di marketing. Prima di qualsiasi personalizzazione, i due rapporti seguenti mostrano quanto segue:

**[!DNL Marketo Measure]101: lead per canale** | Una panoramica generale del modo in cui i canali di marketing influenzano la creazione di lead e i relativi impegni aggiuntivi.
**[!DNL Marketo Measure]101: lead per ID** | Questo mostra la storia Lead ed è un rapporto molto più granulare, che mostra ogni singolo Lead e i relativi punti di contatto dell&#39;acquirente.

**Lead/Contatti con i punti di contatto dell&#39;acquirente** | Questi rapporti sono comunemente denominati rapporti di [!DNL Marketo Measure] persone. Nei report sopra indicati viene utilizzato l&#39;oggetto personalizzato [!DNL Marketo Measure] _[!DNL Marketo Measure]Persona_ anziché l&#39;oggetto Lead.

L&#39;oggetto persona [!DNL Marketo Measure] mette in relazione gli oggetti Lead e Contact. Per impostazione predefinita, [!DNL Salesforce] non fornisce l&#39;opzione per creare report utilizzando l&#39;oggetto Lead e Contact nello stesso report. Mettendo in relazione il lead e l&#39;oggetto contatto utilizzando l&#39;identificatore univoco di una persona, la relativa e-mail, la persona [!DNL Marketo Measure] può creare rapporti sui punti di contatto dell&#39;acquirente relativi al lead e al contatto all&#39;interno dello stesso rapporto. Questo tipo di report è ideale quando si desidera convalidare le impostazioni dell&#39;account [!DNL Marketo Measure] in quanto rappresenta il livello più completo di reporting dei punti di contatto.

Le due varianti di rapporto seguenti utilizzano lo stesso tipo di rapporto, ma sono raggruppate per metriche diverse: ID persona (e-mail) rispetto al canale di marketing. Questi sono i report migliori per funnel/mid of funnel quando si vuole esplorare il modo in cui i lead e i contatti interagiscono con le attività di marketing. Prima di qualsiasi personalizzazione, i due rapporti seguenti mostrano quanto segue:

**[!DNL Marketo Measure]101: lead/contatti per canale** | Una panoramica generale del modo in cui i canali di marketing influenzano la creazione di lead o contatti e i relativi impegni aggiuntivi. Questo rapporto è ideale quando si cerca di comprendere il coinvolgimento totale nei diversi canali di marketing e quali canali di marketing stanno guidando l’emergere di nuovi nomi all’interno della tua istanza Salesforce.
**[!DNL Marketo Measure]101: lead/contatti per ID** | Questo mostra la storia di ogni persona [!DNL Marketo Measure] ed è un report molto più granulare, che mostra ogni persona e i suoi punti di contatto dell&#39;acquirente, indipendentemente dal fatto che il punto di contatto si sia verificato quando era un lead o come un contatto.

**Opportunità con punti di contatto di attribuzione buyer** | Gli ultimi due report &quot;_[!DNL Marketo Measure]101..._&quot; sono alla fine dei report funnel che visualizzano i dati Buyer Attribution Touchpoint relativi alle opportunità. Il fattore chiave per questi rapporti è che sono generati da _Punti di contatto di attribuzione buyer_ che si riferiscono ai dati a livello di opportunità e opportunità, ad esempio i ricavi. Ogni volta che desideri generare rapporti sulle opportunità o sui ricavi attribuiti, devi utilizzare questo tipo di rapporto. I due rapporti seguenti utilizzano lo stesso tipo di rapporto, ma sono raggruppati per metriche diverse, ID opportunità e Canale di marketing. Prima di qualsiasi personalizzazione, i due rapporti seguenti mostrano quanto segue:

**[!DNL Marketo Measure]101: opportunità per canale** | Una visione di alto livello di come i canali di marketing influenzano e generano ricavi attribuiti nelle opportunità.
**[!DNL Marketo Measure]101: opportunità per ID** | Questa versione di report granulare mostra il percorso completo delle opportunità. In questo rapporto puoi vedere ogni Buyer Attribution Touchpoint associato a un’opportunità e i relativi ricavi attribuiti tramite i vari modelli di attribuzione.

È consigliabile considerare i report &quot;_[!DNL Marketo Measure]101..._&quot; come modelli per le proprie esigenze di reporting. Iniziare da uno dei rapporti di cui sopra ti farà risparmiare tempo e assicurarti di utilizzare i campi corretti relativi ai dati [!DNL Marketo Measure]. Assicurati sempre di salvare con nome ogni volta che apporti personalizzazioni ai modelli &quot;_[!DNL Marketo Measure]101..._&quot; per mantenere la variante originale del rapporto.

La cartella &quot;Rapporti di Buyer Touchpoint&quot; è progettata per aiutarti a iniziare a creare rapporti di [!DNL Marketo Measure]. Per i rapporti utilizzabili, dovrai personalizzare tali rapporti in modo che siano personalizzati in base alle tue esigenze di reporting. dovrai aggiungere i filtri necessari per garantire che i record all’interno del rapporto (e i relativi punti di contatto) siano allineati con l’obiettivo di reporting.

Se si ha familiarità con i report &quot;_[!DNL Marketo Measure]101..._&quot;, è possibile ricrearli dai tipi di report personalizzati per esigenze di reporting più personalizzate. La creazione di [[!DNL Marketo Measure] tipi di report personalizzati](/help/marketo-measure-salesforce-reporting/new-report-types/creating-custom-marketo-measure-report-types.md) consente di richiamare campi personalizzati che è possibile utilizzare comunemente in altri report CRM. Questo ti aiuterà a portare il reporting di [!DNL Marketo Measure] al livello successivo.
