---
unique-page-id: 18874572
description: Record duplicati e [!DNL Marketo Measure] - [!DNL Marketo Measure] - Documentazione del prodotto
title: Record duplicati e [!DNL Marketo Measure]
exl-id: e340100c-120a-4771-946d-336a1458da4e
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Record duplicati e [!DNL Marketo Measure] {#duplicate-records-and-marketo-measure}

>[!NOTE]
>
>È possibile visualizzare istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella nostra documentazione, ma vedi ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riflesso nel tuo CRM presto.

[!DNL Marketo Measure] sfrutta l’indirizzo e-mail come identificatore univoco quando si corrispondono dati a un lead o a un contatto correlato nel CRM. Quando [!DNL Marketo Measure] trova più lead o contatti con lo stesso indirizzo e-mail, verranno visualizzati gli stessi dati su tutti i record. L&#39;impatto di questo si verifica quando si esegue il reporting sui lead o contatti con [!DNL Marketo Measure] e può gonfiare erroneamente la quantità di persone univoche che hanno punti di contatto per l’acquirente.

A cosa assomiglia? [!DNL Marketo Measure] Segnalazione?

_Esempio di rapporto: [!DNL Marketo Measure] Persone con punti di contatto dell&#39;acquirente._

![](assets/1-1.png)

Puoi vedere per [!DNL Marketo Measure] ID persona di kelsey@adobe.com che esiste un lead e un contatto con tale indirizzo e-mail. In questo rapporto sono riportati 2 primi contatti, 2 contatti per la creazione di lead e 2 rapporti di interazione PostLC. Questi record duplicati condividono la stessa data del punto di contatto e le stesse informazioni del punto di contatto, il che potrebbe portare alla conclusione che si tratta di 2 persone diverse nonostante siano la stessa persona.

**Consiglio**

* Per massimizzare il ritorno nei tuoi rapporti, ti consigliamo di utilizzare uno strumento di eliminazione del carico di lavoro all’interno del tuo CRM per assicurarti di creare solo nuovi record univoci netti. Questo può essere fatto con il tuo strumento di automazione marketing o un software separato installato nel tuo CRM. [!DNL Marketo Measure] non deduplica automaticamente i record e non offre questo servizio tramite il nostro software.
* Un&#39;opzione alternativa consiste nell&#39;unire manualmente i record durante l&#39;identificazione dei duplicati. Questo processo può richiedere molto tempo e può essere noioso, ma l&#39;output di report accurati vale la pena di investire tempo.
