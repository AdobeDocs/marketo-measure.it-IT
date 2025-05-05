---
unique-page-id: 18874708
description: Attribuzione attività Salesforce - [!DNL Marketo Measure]
title: Attribuzione attività Salesforce
exl-id: 1dc6f15b-2a45-4ed3-9fa3-5267366d1f45
feature: Attribution, Salesforce
source-git-commit: e5931d783d8aad9ab0b32b4e30bbbfdfd46230dd
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 1%

---

# Attribuzione attività Salesforce {#salesforce-activities-attribution}

L&#39;integrazione delle attività di Salesforce [!DNL Marketo Measure] inserisce record Attività ed Evento specifici nel modello di attribuzione. Inizia a tenere traccia di elementi come e-mail di vendita o telefonate di vendita che non ricevevano il dovuto credito. Per configurare la regola delle attività, vai a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}. Da qui, passare alla scheda **[!UICONTROL Settings]** e fare clic sulla scheda **[!UICONTROL Activities]**.

![](assets/1.png)

>[!AVAILABILITY]
>
>Questa funzione è abilitata solo per i clienti di livello 2. Per richiedere un livello di account superiore, contatta l’Adobe Account Team (il tuo account manager).

Per iniziare, stiamo introducendo un nuovo concetto denominato [!DNL Marketo Measure] Campaign. Per ogni regola definita, eseguirai il bucket dei record in una campagna [!DNL Marketo Measure] a cui puoi assegnare un nome. Aggiungi più campagne in base alle esigenze. Immagina di misurare l’efficacia di una campagna di vendita in uscita accanto a una campagna a pagamento.

Stai per utilizzare questo nome della campagna [!DNL Marketo Measure] per indicarci a quale canale deve essere mappato. Se stai ancora pensando a Vendite in uscita, forse tutte le campagne Vendite in uscita dovrebbero stare in un canale BDR.

Acquisisci familiarità con questa gerarchia:

* Channel
   * Sottocanale
      * Campaign
      * Campaign
   * Sottocanale
      * Campaign

>[!TIP]
>
>Se ad esempio si desidera impostare una campagna univoca per ogni rappresentante di vendita, utilizzare i parametri di sostituzione dinamici per compilare il nome della campagna [!DNL Marketo Measure]. Nello stesso esempio, è possibile immettere `"Outbound Sales - {AssignedTo}"` che verrà modificato in `"Outbound Sales - Jill"` o `"Outbound Sales - Jack."`

![](assets/2.png)

Una volta impostato il nome della campagna [!DNL Marketo Measure], è necessario impostare le regole di attività.

Le regole fungono da filtro per indicarci quali record sono idonei per l’attribuzione. Immagina di creare un rapporto nel CRM utilizzando una logica simile per generare tale rapporto. È possibile utilizzare una combinazione di istruzioni e/o e vari operatori come `matches any`, `contains`, `starts with`, `ends with`, `is equal to`. Definisci `and` istruzioni in una regola o in un livello &quot;in box&quot; `or` istruzioni esterne alla casella.

![](assets/3.png)

>[!NOTE]
>
>I campi formula non possono essere utilizzati nelle regole e non verranno visualizzati nell&#39;elenco a discesa. Poiché le formule vengono calcolate in background e non modificano un record, [!DNL Marketo Measure] non è in grado di rilevare se un record soddisfa o meno una regola.
>
>Assicurati di utilizzare i valori corretti per i campi ID come CrmEvent.CreatedById. [!DNL Salesforce IDs] sono lunghi 18 caratteri ( 0054H000007WmrfQAC).

Infine, scegli uno dei campi data o data/ora da utilizzare come data Buyer Touchpoint. È possibile selezionare i campi standard e personalizzati.

>[!TIP]
>
>Con l&#39;installazione del pacchetto, [!DNL Marketo Measure] include un campo Data Buyer Touchpoint personalizzato nel record Attività. Se desideri utilizzare una data dinamica, come la data in cui uno stato cambia, puoi utilizzare un flusso di lavoro di gestione delle relazioni con i clienti per impostare la &quot;Data Buyer Touchpoint&quot; e quindi selezionare qui la Data Buyer Touchpoint in questo passaggio.

![](assets/4.png)

Non dimenticare di impostare regole diverse per Attività o Eventi. È necessario conoscere l&#39;oggetto utilizzato dal team vendite per registrare le attività.

![](assets/5.png)

Inserire questi nuovi punti di contatto nel [canale di marketing](https://experience.adobe.com/#/marketo-measure/MyAccount/Business?busView=false&amp;id=10#/!/MyAccount/Business/Account.Settings.SettingsHome?tab=Channels.Online%20Channels){target="_blank"} appropriato. Per farlo, definisci il canale con la nuova mappatura Campaign appena creata.

>[!TIP]
>
>Quando aggiungi una definizione di canale, utilizza valori con caratteri jolly, un modo più semplice per indicare gli operatori come:
>
>inizia con ( In uscita&#42; )
>
>contiene ( &#42;In uscita&#42; )
>
>termina con ( &#42;In uscita )
>
>Nessun carattere jolly in pratica significa &quot;è uguale a&quot;, quindi assicurati di utilizzarli in base alle esigenze.

| **Operatore** | **Caso d&#39;uso** |
|---|---|
| È uguale a | Valore singolo - Corrispondenza esatta |
| Contains | Valore singolo - contiene valore |
| Corrisponde a qualsiasi | Più valori - Corrispondenza esatta |
| Corrisponde a qualsiasi (contiene) | Più valori - &#42;valore&#42;, &#42;valore, &#42;valore&#42; |

![](assets/6.png)

Infine, ma non per importanza, puoi immettere i costi per i nuovi canali. Il [caricamento della spesa di marketing](https://experience.adobe.com/#/marketo-measure/MyAccount/Business?busView=false&amp;id=10#/!/MyAccount/Business/Account.Settings.SettingsHome?tab=Reporting.Marketing%20Spend){target="_blank"} ti consente di inserire la spesa a livello di canale, sottocanale o campagna. Con le nuove [!DNL Marketo Measure] campagne, puoi aggiungere questi costi correlati per mese, quindi visualizzare il ROI di ogni campagna.

![](assets/7.png)

>[!MORELIKETHIS]
>
>[Domande frequenti su Activity Attribution](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)
