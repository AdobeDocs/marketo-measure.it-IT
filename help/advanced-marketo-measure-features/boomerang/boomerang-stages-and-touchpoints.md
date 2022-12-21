---
unique-page-id: 18874558
description: Fasi e punti di contatto di Boomerang - [!DNL Marketo Measure] - Documentazione del prodotto
title: Fasi e punti di contatto di Boomerang
exl-id: e58169a3-3637-4878-8a0e-1920d873ff52
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 0%

---

# Fasi e punti di contatto di Boomerang {#boomerang-stages-and-touchpoints}

[!DNL Marketo Measure] ha rilasciato la nostra funzione Boomerang Stage! La funzione Boomerang Stage è stata creata per offrire una maggiore visibilità al percorso del cliente per [!DNL Marketo Measure] clienti con cicli di vendita lunghi. Questa funzione consente agli addetti al marketing di creare punti di contatto per tutte le transizioni di stage che si verificano nel percorso Opportunity, come quando un contatto MQL, poi si sposta su SAL e quindi torna al passaggio MQL. Quando i contatti &quot;entrano nuovamente nella fase MQL&quot; o &quot;re-MQL&quot;, consideriamo l&#39;MQL come una fase boomerang. La funzione Boomerang Stage funziona insieme alla funzione [!DNL Marketo Measure] Stadi personalizzati.

## Funzione {#what-this-feature-does}

* Crea un punto di contatto &quot;boomerang&quot; per tutte le transizioni di stage che si verificano nel percorso di un’opportunità
* Tiene traccia delle transizioni ripetute tra uno stadio personalizzato (ad esempio, quando un Contact MQLs si sposta su SAL e quindi torna alla fase MQL)
* Consente di specificare il numero e il set di transizioni di stage da includere nell’opportunità (ad esempio, I primi 10 MQL (O gli ultimi 5 MQL)
* Se sei un utente di Modello personalizzato, puoi determinare la ponderazione dell’attribuzione e il credito percentuale da allocare a ciascuna di queste fasi (ad esempio. specifica il peso dell’attribuzione alla prima o all’ultima occorrenza di MQL o distribuisci la ponderazione dell’attribuzione in modo uniforme tra tutte le occorrenze)

>[!NOTE]
>
>[Istruzioni su come impostare Boomerang Stages](/help/advanced-marketo-measure-features/boomerang/setting-up-boomerang-stages.md).

## Che aspetto hanno le fasi e i punti di contatto di Boomerang nel tuo CRM {#what-boomerang-stages-and-touchpoints-look-like-in-your-crm}

Senza fasi Boomerang (il &quot;prima&quot;), vedrai solo il MQL più recente o il punto di contatto SQL più recente associato a un record Lead/Contatto.

![](assets/1.png)

Con Boomerang Stages e punti di contatto puoi vedere i punti di contatto che si verificano per ogni transizione di fase. La convenzione di denominazione per questi punti di contatto boomerang sarà la seguente:

**[Nome della fase]-00.**

Utilizzando l’esempio seguente, questo [!DNL Marketo Measure] l&#39;account ha incluso MQL e SQL nelle loro fasi boomerang e ha scelto di visualizzare 2 punti di contatto boomerang per stadio.

![](assets/2.png)

**MQL-01** è la prima transizione di fase MQL.

Il valore numerico nella posizione del punto di contatto indica l’ordine in cui si è verificata la transizione dello stadio. L’ultimo punto di contatto boomerang deve essere contrassegnato come:

MQL-02 **(Ultimo)**

## Modifica dei dati esistenti nelle fasi di Boomerang {#how-boomerang-stages-change-your-existing-data}

Le fasi di Boomerang avranno un impatto:

**Attribuzione per canale**

* Da [!DNL Boomerang Stages] per creare più punti di contatto, verrà modificato il modo in cui l’attribuzione viene distribuita tra i punti di contatto attualmente presenti nei dati. Di conseguenza, ciò può significare che il valore dei ricavi si sposterà tra i canali di marketing. Tieni presente questo aspetto prima di implementare [!DNL Boomerang stages]oppure contatta il tuo account manager per ulteriori informazioni.

**Qualsiasi rapporto che utilizza &quot;è uguale a&quot; [Posizione punto di contatto]&quot;**

* Le fasi di Boomerang introdurranno nuove posizioni dei punti di contatto nei tuoi dati. [!DNL Marketo Measure] sta modificando il formato della posizione del punto di contatto in modo da includere l&#39;occorrenza dello stadio, come &quot;MQL-01&quot; o &quot;MQL-05 (Last)&quot;. Utilizzando questo esempio, Boomerang Stages interesserà tutti i rapporti che utilizzano &quot;Touchpoint Position is equal to MQL&quot; (Posizione punto di contatto è uguale a MQL). Per regolare questi rapporti, il filtro deve utilizzare l’operatore &quot;contiene&quot;.

## Domande frequenti {#faq}

**Quanti stadi boomerang posso includere nel mio modello di attribuzione?**

È possibile selezionare fino a 15 fasi.

**D: Quanti punti di contatto &quot;boomerang&quot; posso avere per palco?**

È possibile selezionare fino a 10 punti di contatto boomerang per fase.

**D: Perché siamo limitati a 10 boomerang per palco?**

[!DNL Marketo Measure] deve stabilire un limite al numero di fasi per tenere sotto controllo i tempi di elaborazione. Se scegli di includere nel modello di attribuzione tutte le 15 fasi di Boomerang e 10 punti di contatto boomerang per fase, potresti potenzialmente avere più di 150 punti di contatto per record Lead/Contatto.

**D: Ho Data Warehouse. Ottengo tutti i dati o il limite Boomerang Stages si applica anche a me?**

Il limite si applicherà alla Data Warehouse e alle CRM a causa dei limiti di elaborazione che [!DNL Marketo Measure] è al suo posto. La Data Warehouse vedrà anche il limite di 10 punti di contatto per fase.

**D: Qual è il vantaggio di utilizzare Boomerang Stages con la modellazione personalizzata?**

Utilizzo [!UICONTROL Boomerang] Le fasi con la modellazione personalizzata consentono di assegnare la ponderazione dell’attribuzione a [!UICONTROL Boomerang] punti di contatto, che attribuiranno il credito di ricavi a queste fasi.

Senza modellazione personalizzata, [!DNL Marketo Measure] crea punti di contatto per ogni boomerang e transizione stage, ma non assegna alcun credito di attribuzione a tali punti di contatto. Gli unici punti di contatto boomerang che riceveranno crediti di attribuzione sono i punti di contatto per l’invio dei moduli. Senza modello personalizzato, [!DNL Boomerang] i punti di contatto sono considerati come un &quot;contatto intermedio&quot; e ricevono di conseguenza il credito di attribuzione.
