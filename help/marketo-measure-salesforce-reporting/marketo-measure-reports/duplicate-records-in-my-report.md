---
unique-page-id: 18874634
description: Record duplicati nel mio rapporto - [!DNL Marketo Measure] - Documentazione del prodotto
title: Record duplicati nel rapporto personale
exl-id: 4ee42371-5b67-4c69-9b49-3249f33614d0
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Record duplicati nel rapporto personale {#duplicate-records-in-my-report}

>[!NOTE]
>
>È possibile visualizzare istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella nostra documentazione, ma ancora vedi &quot;[!DNL Bizible]&quot; nel CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riflesso nel tuo CRM presto.

Quando ti immergi nel [!DNL Marketo Measure] Rapporti in [!DNL Salesforce], potresti iniziare a trovare record &quot;duplicati&quot; nei tuoi rapporti. Probabilmente questo sentimento si verifica quando si esamina [!DNL Marketo Measure] rapporti predefiniti.

Quando esegui il reporting con l’oggetto Punti di contatto dell’acquirente o con l’oggetto Punto di contatto dell’attribuzione dell’acquirente, è importante comprendere che non stai più segnalando il numero di lead, contatti o opportunità, ma piuttosto segnalerai il numero di punti di contatto dell’acquirente o di punti di contatto dell’attribuzione dell’acquirente associati a tali oggetti standard (lead, contatti, opportunità).

Prendiamo ad esempio il seguente rapporto:

Questa è una **Contatti con i punti di contatto dell&#39;acquirente** rapporto. Anche in questo caso, stiamo valutando il numero di punti di contatto associati a un singolo contatto.

![](assets/1.gif)

Come potete vedere, sembra che ci siano tre contatti di James Williams nel rapporto, e quindi potreste pensare, &quot;duplicati!&quot;

Tuttavia, questo rapporto mostra il numero di punti di contatto relativi a James. All’interno del rapporto, puoi vedere che James ha un singolo FT (First Touch), una singola LC, una maschera (Lead Creation Touch) e un punto di contatto PostLC (una sottomissione del modulo che avviene dopo il punto di contatto LC).

Se desideri comprendere il &quot;conteggio dei contatti&quot; puoi utilizzare i campi &quot;Conteggio - Primo contatto&quot;, &quot;Conteggio-lead creazione contatto&quot; o &quot;Conte-U-a forma di&quot; per capire quanti contatti hanno avuto interazioni di marketing.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Università: Rapporti SFDC](https://universityonline.marketo.com/courses/bizible-fundamentals-bizible-102/#/page/5c5cb68dfb384d0c9fb96cc4)
