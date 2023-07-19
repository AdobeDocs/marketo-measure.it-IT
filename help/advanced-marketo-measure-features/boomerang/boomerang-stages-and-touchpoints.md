---
unique-page-id: 18874558
description: Stadi e punti di contatto del boomerang - [!DNL Marketo Measure] - Documentazione del prodotto
title: Fasi e punti di contatto del boomerang
exl-id: e58169a3-3637-4878-8a0e-1920d873ff52
source-git-commit: 01be819ccee1b3079b15a748480e9dacf6adb488
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Fasi e punti di contatto del boomerang {#boomerang-stages-and-touchpoints}

>[!AVAILABILITY]
>
>La funzione Boomerang è abilitata solo per i clienti di livello 3. Per richiedere un livello di account più alto, contatta l’Adobe Account Team (il tuo account manager).

[!DNL Marketo Measure] ha rilasciato la nostra funzione Boomerang Stage! La funzione Boomerang Stage è stata creata per fornire maggiore visibilità al percorso del cliente per [!DNL Marketo Measure] clienti con lunghi cicli di vendita. Questa funzione consente agli addetti al marketing di creare punti di contatto per tutte le transizioni di fase che si verificano nel percorso di opportunità, come quando un contatto MQLs, quindi si sposta su SAL e quindi ritorna alla fase MQL. Quando i contatti &quot;rientrano nella fase MQL&quot; o &quot;re-MQL&#39;s&quot;, consideriamo la MQL come una fase di boomerang. La funzione Boomerang Stage funziona insieme al [!DNL Marketo Measure] Fasi personalizzate.

## Funzionamento di questa funzione {#what-this-feature-does}

* Crea un punto di contatto &quot;boomerang&quot; per tutte le transizioni di fase che si verificano nel percorso di un’opportunità
* Tiene traccia delle transizioni ripetute tra qualsiasi area di visualizzazione personalizzata (ad esempio quando un contatto MQL si sposta su SAL e quindi torna alla fase MQL)
* Consente di specificare il numero e il set di transizioni di fase da includere nell’opportunità (ad esempio I primi 10 MQL O gli ultimi 5 MQL)
* Se sei un utente del modello personalizzato, puoi determinare la ponderazione dell’attribuzione e il credito percentuale che desideri allocare a ciascuno di questi stadi (ad esempio designare il peso dell’attribuzione per la prima o l’ultima occorrenza MQL, oppure distribuire uniformemente la ponderazione dell’attribuzione tra tutte le occorrenze)

>[!NOTE]
>
>[Istruzioni su come impostare le fasi di Boomerang](/help/advanced-marketo-measure-features/boomerang/setting-up-boomerang-stages.md).

## Come si presentano le fasi di boomerang e i punti di contatto nel CRM {#what-boomerang-stages-and-touchpoints-look-like-in-your-crm}

Senza le fasi Boomerang (il &quot;prima&quot;), verrà visualizzato solo il punto di contatto MQL o SQL più recente associato a un record Lead/Contatto.

![](assets/1.png)

Con Boomerang Stages e punti di contatto, vedrai i punti di contatto che si verificano per ogni transizione di fase. La convenzione di denominazione per questi punti di contatto boomerang sarà la seguente:

**[Nome fase]-00.**

Utilizzando l’esempio seguente, [!DNL Marketo Measure] L&#39;account ha incluso MQL e SQL nelle loro fasi di boomerang, e ha scelto di mostrare 2 punti di contatto boomerang per ogni fase.

![](assets/2.png)

**MQL-01** è la prima transizione di stadio MQL.

Il valore numerico nella posizione del punto di contatto indica l’ordine in cui si è verificata la transizione dell’area di visualizzazione. L’ultimo punto di contatto boomerang deve essere timbrato come:

MQL-02 **(Ultimo)**

## Come le fasi di Boomerang cambiano i dati esistenti {#how-boomerang-stages-change-your-existing-data}

Il Boomerang Stages avrà un impatto su:

**Attribuzione per canale**

* Da [!DNL Boomerang Stages] creerà altri punti di contatto, questo cambierà il modo in cui l’attribuzione viene distribuita tra i punti di contatto attualmente esistenti nei dati. Di conseguenza, i valori dei ricavi potrebbero spostarsi tra i canali di marketing. Tieni presente questo aspetto prima di implementare [!DNL Boomerang stages]o contatta il tuo account manager per ulteriori informazioni.

**Qualsiasi rapporto che utilizza &quot;è uguale a [Posizione punto di contatto]&quot;**

* Le fasi Boomerang introdurranno nuove posizioni di punti di contatto nei tuoi dati. [!DNL Marketo Measure] sta modificando il formato della posizione del punto di contatto per includere l’occorrenza dell’area di visualizzazione, come &quot;MQL-01&quot; o &quot;MQL-05 (Last)&quot;. Utilizzando questo esempio, Boomerang Stages (Fasi boomerang) influirà su tutti i rapporti che utilizzano &quot;La posizione del punto di contatto è uguale a MQL&quot;. Per regolare questi rapporti, il filtro deve utilizzare l’operatore &quot;contiene&quot;.

## Domande frequenti {#faq}

**Quante fasi di boomerang posso includere nel mio modello di attribuzione?**

Puoi selezionare fino a 15 stadi.

**D: Quanti punti di contatto &quot;boomerang&quot; posso avere per palco?**

Puoi selezionare fino a 10 punti di contatto boomerang per fase.

**D: Perché siamo limitati a soli 10 boomerang per tappa?**

[!DNL Marketo Measure] deve limitare il numero di fasi per tenere sotto controllo i tempi di trasformazione. Se scegli di includere tutti i 15 stadi boomerang nel modello di attribuzione e 10 punti di contatto boomerang per stadio, potresti potenzialmente avere oltre 150 punti di contatto per record Lead/Contatto.

**D: Ho la Data Warehouse. Ottengo tutti i dati o il limite dei Boomerang Stages si applica anche a me?**

Il limite si applicherà alle Date Warehouse e ai sistemi CRM a causa dei limiti di elaborazione che [!DNL Marketo Measure] ha installato. Data Warehouse vedrà anche il limite di 10 punti di contatto per fase.

**D: Qual è il vantaggio di utilizzare Boomerang Stages con la modellazione personalizzata?**

Utilizzo di [!UICONTROL Boomerang] Le fasi con la modellazione personalizzata ti consentono di assegnare la ponderazione dell’attribuzione a [!UICONTROL Boomerang] punti di contatto, che assegneranno il credito dei ricavi a queste fasi.

Senza modellazione personalizzata, [!DNL Marketo Measure] creerà punti di contatto per ciascuna transizione boomerang e stage, ma non assegnerà alcun merito di attribuzione a tali punti di contatto. Gli unici punti di contatto boomerang che riceveranno crediti di attribuzione sono i punti di contatto per l’invio di moduli. Senza modello personalizzato, [!DNL Boomerang] i punti di contatto sono considerati come un &quot;contatto intermedio&quot; e ricevono di conseguenza il credito di attribuzione.
