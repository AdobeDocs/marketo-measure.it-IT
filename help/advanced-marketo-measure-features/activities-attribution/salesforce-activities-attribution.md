---
unique-page-id: 18874708
description: Attribuzione attività Salesforce - [!DNL Marketo Measure] - Documentazione del prodotto
title: Attribuzione attività Salesforce
exl-id: 1dc6f15b-2a45-4ed3-9fa3-5267366d1f45
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '682'
ht-degree: 0%

---

# Attribuzione attività Salesforce {#salesforce-activities-attribution}

La [!DNL Marketo Measure] L’integrazione delle attività Salesforce porterà nel modello di attribuzione i record Attività ed Evento specifici. Inizia a tenere traccia di cose come le e-mail di vendita o le telefonate di vendita che non ricevevano il giusto credito. Per configurare la regola delle attività, devi andare a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target=&quot;_blank&quot;}. Da lì, vai al **[!UICONTROL Settings]** e fai clic su **[!UICONTROL Activities]** scheda .

Stai per rendere il tuo team di vendita molto felice! Segui un breve tutorial.

![](assets/1.png)

Per iniziare, stiamo introducendo un nuovo concetto chiamato [!DNL Marketo Measure] Campaign. Per ogni regola definita, inserirai i record in una [!DNL Marketo Measure] Campagna che puoi denominare. Aggiungi più campagne in base alle esigenze. Immaginate di misurare l&#39;efficacia di una campagna di vendita in uscita vicino a una campagna di media a pagamento!

Userai questo [!DNL Marketo Measure] Nome campagna per indicarci a quale canale deve essere mappato. Se stai ancora pensando alle vendite in uscita, forse tutte le campagne di vendita in uscita dovrebbero trovarsi in un canale BDR.

Acquisisci familiarità con questa gerarchia:

* Canale
   * Canale secondario
      * Campaign
      * Campaign
   * Canale secondario
      * Campaign

>[!TIP]
>
>Se ad esempio desideri impostare una campagna univoca per ogni rappresentante di vendita, utilizza i nostri parametri di sostituzione dinamici per compilare il [!DNL Marketo Measure] Nome campagna. Nello stesso esempio, puoi immettere `"Outbound Sales - {AssignedTo}"` e lo trasformeremo in qualcosa di simile `"Outbound Sales - Jill"` o `"Outbound Sales - Jack."` Non hai idea di quanto tempo ti abbiamo appena salvato!

![](assets/2.png)

Una volta che [!DNL Marketo Measure] Il nome della campagna è impostato. È ora di impostare le regole dell’attività.

Le regole fungono da filtro per dirci quali record sono idonei per l’attribuzione. Immagina di creare un report nel tuo CRM utilizzando una logica simile per generare il report. Hai la flessibilità di utilizzare una combinazione di istruzioni e/o e vari operatori come le corrispondenze qualsiasi, contiene, inizia con, termina con, è uguale a, ecc. Definisci le istruzioni &quot;e&quot; all’interno di una regola box o di istruzioni &quot;o&quot; di livello all’esterno della casella.

![](assets/3.png)

>[!NOTE]
>
>I campi Formula non possono essere utilizzati all&#39;interno delle regole e non verranno visualizzati nell&#39;elenco a discesa. Poiché le formule si calcolano in background e non modificano un record, [!DNL Marketo Measure] impossibile rilevare se un record soddisfa una regola o meno.
>
>Assicurati di utilizzare i valori corretti per i campi ID come CrmEvent.CreatedById. [!DNL Salesforce IDs] sono lunghi 18 caratteri (ad esempio, 0054H000007WmrfQAC).

Infine, scegliamo uno dei campi data o data/ora da utilizzare come data punto di contatto dell’acquirente. I campi standard e personalizzati sono selezionabili.

>[!TIP]
>
>Con l&#39;installazione del pacchetto, [!DNL Marketo Measure] include un campo personalizzato Data punto di contatto dell’acquirente nel record Attività. Se desideri utilizzare una data dinamica, come la data in cui cambia uno stato, è possibile utilizzare un flusso di lavoro CRM per impostare la &quot;Data punto di contatto dell’acquirente&quot;, quindi selezionare la data del punto di contatto dell’acquirente qui in questo passaggio.

![](assets/4.png)

Non dimenticare di impostare regole diverse per Attività o Eventi. Sarà necessario sapere quale oggetto utilizza il team di vendita per registrare le attività.

![](assets/5.png)

È probabile che si desideri inserire questi nuovi punti di contatto nei relativi [Canale di marketing](https://experience.adobe.com/#/marketo-measure/MyAccount/Business?busView=false&amp;id=10#/!/MyAccount/Business/Account.Settings.SettingsHome?tab=Channels.Online%20Channels){target=&quot;_blank&quot;}. Puoi farlo definendo il Canale con la nuova mappatura Campaign appena creata. Forse creerai una nuova riga per il canale BDR in cui la campagna inizia con Outbound.

>[!TIP]
>
>Quando aggiungi una definizione di canale, utilizza i valori dei caratteri jolly per definire più facilmente gli operatori come:
>
>inizia con ( in uscita&#42; )
>
>contiene ( &#42;In uscita&#42; )
>
>termina con ( &#42;In uscita )
>
>Nessun carattere jolly significa fondamentalmente &quot;è uguale a&quot;, quindi assicurati di utilizzarli in base alle esigenze.

| **Operatore** | **Caso d’uso** |
|---|---|
| È uguale a | Valore singolo - corrispondenza esatta |
| Contiene | Valore singolo - contiene valore |
| Corrisponde a qualsiasi | Valori multipli - Corrispondenza esatta |
| Corrisponde a qualsiasi (contiene) | Valori multipli - &#42;value&#42;, &#42;valore, &#42;value&#42; |

![](assets/6.png)

E infine, ma non meno importante, hai la possibilità di inserire i costi per i tuoi nuovi canali. Nostro [Caricamento della spesa di marketing](https://experience.adobe.com/#/marketo-measure/MyAccount/Business?busView=false&amp;id=10#/!/MyAccount/Business/Account.Settings.SettingsHome?tab=Reporting.Marketing%20Spend){target=&quot;_blank&quot;} ti consente di immettere la spesa a livello di canale, di canale secondario o di campagna. Con il tuo nuovo [!DNL Marketo Measure] Campagne, puoi aggiungere questi costi correlati per mese, quindi visualizzare il ROI per ogni campagna!

![](assets/7.png)

>[!MORELIKETHIS]
>
>[Domande frequenti su Activity Attribution](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)
