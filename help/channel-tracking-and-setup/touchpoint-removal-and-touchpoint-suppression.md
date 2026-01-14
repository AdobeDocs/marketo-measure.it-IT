---
description: Linee guida per la rimozione e la soppressione dei punti di contatto per gli utenti di Marketo Measure
title: Rimozione e soppressione dei punti di contatto
exl-id: 201af648-6525-4a80-a7e5-3cbeeb1670b6
feature: Touchpoints
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# Rimozione e soppressione dei punti di contatto {#touchpoint-removal-and-touchpoint-suppression}

Scopri come rimuovere o eliminare dal CRM i punti di contatto che soddisfano criteri specifici. Questo può essere utile per liberare spazio di dati se si dispone di [!DNL Salesforce] limiti di archiviazione dati.

Esiste una differenza chiave tra le regole di rimozione dei punti di contatto e le regole di eliminazione dei punti di contatto:

* Rimozione punto di contatto: [!DNL Marketo Measure] eliminerà (ovvero rimuoverà) tutti i punti di contatto dal CRM che soddisfano i criteri della regola. I dati _possono_ essere inseriti nel report nel dashboard ROI di [!DNL Marketo Measure], ma non più nel CRM.
* Eliminazione dei punti di contatto: simile alla rimozione dei punti di contatto, ma i dati NON POSSONO essere segnalati nella dashboard del ROI.

Prima di iniziare a creare regole di rimozione/eliminazione dei punti di contatto, è consigliabile condividere il piano di implementazione con il team delle operazioni di marketing e vendita. Dovresti avere già un’idea dei tipi o dei valori da rimuovere. Alcuni dei casi d’uso comuni sono:

* Elimina punti di contatto da opportunità perse chiuse
* Elimina punti di contatto da lead molto vecchi
* Elimina punti di contatto da lead non qualificati

Una volta salvate le regole, [!DNL Marketo Measure] eliminerà e ridistribuirà il modello di attribuzione. Ciò significa che cambieranno le tappe e le posizioni e cambierà anche il merito di attribuzione del tuo canale! In questo modo i dati verranno modificati; se hai bisogno di assistenza, contatta quindi il tuo Success Manager.

`1)` Sono disponibili due sezioni per le impostazioni di rimozione/soppressione. È possibile impostarla per i punti di contatto dell&#39;acquirente (lead e contatti) o per i punti di contatto di attribuzione dell&#39;acquirente (contatti, opportunità e account).

Inizia aggiungendo una regola e selezionando il Campo che definirà i criteri.

Scegli da un elenco di operatori che saranno correlati al successivo set di valori, che aggiungerai nella colonna successiva.

![Scegli da un elenco di operatori che si riferiranno al successivo](assets/touchpoint-settings-10.png)

>[!TIP]
>
>Per aggiungere più valori in un campo, utilizza l’operatore &quot;corrisponde a qualsiasi&quot; con virgole che separano ciascun valore.

>[!TIP]
>
>Per includere un valore vuoto o NULL in un campo, è sufficiente lasciare vuota la casella [!UICONTROL Value]. Questo prenderà in considerazione scenari come la valutazione rispetto a un punto di contatto senza URL modulo.

>[!NOTE]
>
>I campi formula non possono essere utilizzati nelle regole e non verranno visualizzati nell&#39;elenco a discesa. Poiché le formule vengono calcolate in background e non modificano un record, [!DNL Marketo Measure] non è in grado di rilevare se un record soddisfa o meno una regola.

`2)` Aggiungi regole nello stesso gruppo per utilizzare la logica &quot;AND&quot; nell&#39;istruzione.
In alternativa, aggiungere nuove istruzioni all&#39;esterno del gruppo per utilizzare la logica &quot;OR&quot; nell&#39;istruzione.

![Oppure, aggiungi nuove istruzioni all&#39;esterno del gruppo per utilizzare la logica &quot;OR&quot;](assets/touchpoint-settings-11.png)

`3)` Se le regole diventano complesse ed è necessario ricreare i gruppi e apportare piccole modifiche a ogni istruzione, utilizzare l&#39;opzione [!UICONTROL Clone] per semplificare.

![3) Se le tue regole diventano complesse e devi ricreare i gruppi](assets/touchpoint-settings-6.png)

Se fai un errore, non preoccuparti. È inoltre possibile eliminare singole righe dell&#39;istruzione o gruppi completi.

![Se commetti un errore, non preoccuparti. È possibile eliminare singole righe](assets/touchpoint-settings-7.png)

`4)` Impostare le regole per i punti di contatto di attribuzione buyer se si desidera applicarle a entrambi gli oggetti. La nostra flessibilità consente di impostare regole per uno o entrambi gli oggetti e, se applicabili, può scegliere di impostarle per entrambi.

![4) Impostare le regole per i punti di contatto di attribuzione buyer se si desidera](assets/touchpoint-settings-8.png)

Per terminare, [!UICONTROL Save and Process] le tue regole. Se effettui molte modifiche, assicurati di salvarle durante il processo. [!DNL Marketo Measure] non inizierà effettivamente a rimuovere i tuoi punti di contatto fino a quando non fai clic su
[!UICONTROL **Salva ed elabora**].

| **Operatore** | **Caso d&#39;uso** |
|---|---|
| È uguale a | Valore singolo - Corrispondenza esatta |
| Contiene | Valore singolo - contiene valore |
| Corrisponde a qualsiasi | Più valori - Corrispondenza esatta |
| Corrisponde a qualsiasi (contiene) | Più valori - &#42;valore&#42;, &#42;valore, &#42;valore&#42; |

Per i clienti che utilizzano Dynamics e che desiderano impostare regole di soppressione basate su Status e/o Status code, è necessaria la seguente formattazione durante la configurazione della regola: `[Object].Statecode` è uguale/non uguale a `[Status Value]`. Ad esempio, se il codice di stato di Dynamics legge &quot;1&quot; su un contatto e lo stato è &quot;Inattivo&quot; e si desidera eliminare tutti i contatti di questo tipo, il seguente formato non è corretto per la regola di eliminazione: Contact.Statecode è uguale a 1. Si desidera invece utilizzare il seguente formato: poiché Statecode e Status funzionano in coppia, [!DNL Marketo Measure] legge il valore di Status nella query: Contact.Statecode è uguale a Inactive.
