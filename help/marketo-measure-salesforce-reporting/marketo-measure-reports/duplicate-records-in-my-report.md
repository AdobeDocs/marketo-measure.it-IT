---
unique-page-id: 18874634
description: Record duplicati nel mio report - [!DNL Marketo Measure]
title: Record duplicati nel mio report
exl-id: 4ee42371-5b67-4c69-9b49-3249f33614d0
feature: Reporting
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Record duplicati nel mio report {#duplicate-records-in-my-report}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedi comunque &quot;[!DNL Bizible]&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

Mentre vi immergete nel [!DNL Marketo Measure] Rapporti in [!DNL Salesforce], è possibile che nei rapporti si trovino record &quot;duplicati&quot;. È probabile che provi questa sensazione quando rivedi [!DNL Marketo Measure] rapporti predefiniti.

Quando si esegue il reporting con l&#39;oggetto Punti di contatto buyer o con l&#39;oggetto Punto di contatto di attribuzione buyer, è importante comprendere che non si sta più eseguendo il reporting sul numero di lead, contatti o opportunità, ma che verrà invece eseguito il reporting sul numero di punti di contatto buyer o di punti di contatto di attribuzione buyer associati a tali oggetti standard (lead, contatti, opportunità).

Prendiamo il seguente rapporto come esempio:

Questo è un **Contatti con i punti di contatto dell&#39;acquirente** rapporto. Anche in questo caso, ciò significa che stiamo esaminando il numero di punti di contatto associati a un singolo contatto.

![](assets/1.gif)

Come potete vedere, sembra che ci siano tre contatti di James Williams nel rapporto, e quindi potreste pensare, &quot;duplicati!&quot;

Tuttavia, questo rapporto mostra il numero di punti di contatto relativi a James. All’interno del rapporto, puoi vedere che James ha un FT individuale (First Touch), un LC individuale, un Form (Lead Creation Touch) e un punto di contatto PostLC (un invio di moduli che avviene dopo il punto di contatto LC).

Se desideri comprendere il &quot;conteggio dei contatti&quot;, puoi quindi utilizzare i campi &quot;Conteggio - Primo contatto&quot;, &quot;Conteggio-contatto di creazione lead&quot; o &quot;Conteggio-a forma di U&quot; per capire quanti contatti hanno avuto interazioni di marketing.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Università: rapporti SFDC Stock](https://universityonline.marketo.com/courses/bizible-fundamentals-bizible-102/#/page/5c5cb68dfb384d0c9fb96cc4)
