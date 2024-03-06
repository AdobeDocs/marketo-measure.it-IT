---
unique-page-id: 18874708
description: Attribuzione attività Salesforce - [!DNL Marketo Measure]
title: Attribuzione attività Salesforce
exl-id: 1dc6f15b-2a45-4ed3-9fa3-5267366d1f45
feature: Attribution, Salesforce
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---

# Attribuzione attività Salesforce {#salesforce-activities-attribution}

Il [!DNL Marketo Measure] L’integrazione delle attività di Salesforce porta record specifici di attività ed eventi nel modello di attribuzione. Inizia a tenere traccia di elementi come e-mail di vendita o telefonate di vendita che non ricevevano il dovuto credito. Per configurare la regola delle attività, vai a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}. Da lì, vai al **[!UICONTROL Settings]** e fai clic sul pulsante **[!UICONTROL Activities]** scheda.

![](assets/1.png)

Per cominciare, stiamo introducendo un nuovo concetto chiamato [!DNL Marketo Measure] Campagna. Per ogni regola definita, devi inserire i record in un bucket [!DNL Marketo Measure] Campagna a cui puoi assegnare un nome. Aggiungi più campagne in base alle esigenze. Immagina di misurare l’efficacia di una campagna di vendita in uscita accanto a una campagna a pagamento.

Stai per utilizzare questo [!DNL Marketo Measure] Nome della campagna per indicarci a quale canale deve essere mappato. Se stai ancora pensando a Vendite in uscita, forse tutte le campagne Vendite in uscita dovrebbero stare in un canale BDR.

Acquisisci familiarità con questa gerarchia:

* Canale
   * Sottocanale
      * Campaign
      * Campaign
   * Sottocanale
      * Campaign

>[!TIP]
>
>Se ad esempio desideri impostare una campagna univoca per ogni rappresentante di vendita, utilizza i parametri di sostituzione dinamici per compilare il [!DNL Marketo Measure] Nome della campagna. Nello stesso esempio è possibile immettere `"Outbound Sales - {AssignedTo}"` e la cambia in qualcosa di simile a `"Outbound Sales - Jill"` o `"Outbound Sales - Jack."`

![](assets/2.png)

Una volta [!DNL Marketo Measure] Se si imposta il nome della campagna, è il momento di impostare le regole di attività.

Le regole fungono da filtro per indicarci quali record sono idonei per l’attribuzione. Immagina di creare un rapporto nel CRM utilizzando una logica simile per generare tale rapporto. Puoi utilizzare in modo flessibile una combinazione di istruzioni e/o e vari operatori come `matches any`, `contains`, `starts with`, `ends with`, `is equal to`. Definisci `and` istruzioni all&#39;interno di una regola o di un livello &quot;in box&quot; `or` istruzioni esterne alla scatola.

![](assets/3.png)

>[!NOTE]
>
>I campi formula non possono essere utilizzati nelle regole e non verranno visualizzati nell&#39;elenco a discesa. Poiché le formule vengono calcolate in background senza modificare un record, [!DNL Marketo Measure] non è in grado di rilevare se un record soddisfa o meno una regola.
>
>Assicurati di utilizzare i valori corretti per i campi ID come CrmEvent.CreatedById. [!DNL Salesforce IDs] hanno una lunghezza di 18 caratteri ( 0054H000007WmrfQAC).

Infine, scegli uno dei campi di data o data/ora da utilizzare come data del punto di contatto dell&#39;acquirente. È possibile selezionare i campi standard e personalizzati.

>[!TIP]
>
>Con l’installazione del pacchetto, [!DNL Marketo Measure] include un campo Data punto di contatto buyer personalizzato nel record Attività. Se desideri utilizzare una data dinamica, come la data in cui lo stato cambia, puoi utilizzare un flusso di lavoro di gestione delle relazioni con i clienti per impostare la &quot;Data punto di contatto acquirente&quot;, quindi seleziona la Data punto di contatto acquirente qui in questo passaggio.

![](assets/4.png)

Non dimenticare di impostare regole diverse per Attività o Eventi. È necessario conoscere l&#39;oggetto utilizzato dal team vendite per registrare le attività.

![](assets/5.png)

È probabile che tu voglia inserire questi nuovi punti di contatto nel loro appropriato [Canale di marketing](https://experience.adobe.com/#/marketo-measure/MyAccount/Business?busView=false&amp;id=10#/!/MyAccount/Business/Account.Settings.SettingsHome?tab=Channels.Online%20Channels){target="_blank"}. Per farlo, definisci il canale con la nuova mappatura Campaign appena creata.

>[!TIP]
>
>Quando aggiungi una definizione di canale, utilizza valori con caratteri jolly, un modo più semplice per indicare gli operatori come:
>
>inizia con ( In uscita&#42; )
>
contiene ( &#42;In uscita&#42; )
>
termina con ( &#42;In uscita )
>
Nessun carattere jolly in pratica significa &quot;è uguale a&quot;, quindi assicurati di utilizzarli in base alle esigenze.

| **Operatore** | **Caso d’uso** |
|---|---|
| È uguale a | Valore singolo - Corrispondenza esatta |
| Contiene | Valore singolo - contiene valore |
| Corrisponde a qualsiasi | Più valori - Corrispondenza esatta |
| Corrisponde a qualsiasi (contiene) | Più valori - &#42;valore&#42;, &#42;valore, &#42;valore&#42; |

![](assets/6.png)

Infine, ma non per importanza, puoi immettere i costi per i nuovi canali. Il [Caricamento delle spese di marketing](https://experience.adobe.com/#/marketo-measure/MyAccount/Business?busView=false&amp;id=10#/!/MyAccount/Business/Account.Settings.SettingsHome?tab=Reporting.Marketing%20Spend){target="_blank"} consente di immettere la spesa a livello di canale, sottocanale o campagna. Con il tuo nuovo [!DNL Marketo Measure] Per le campagne, puoi aggiungere i costi correlati per mese, quindi visualizzare il ROI di ogni campagna.

![](assets/7.png)

>[!MORELIKETHIS]
>
[Domande frequenti su Activity Attribution](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)
