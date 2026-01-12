---
description: Record duplicati e  [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Record duplicati e  [!DNL Marketo Measure]
exl-id: e340100c-120a-4771-946d-336a1458da4e
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---


# Record duplicati e [!DNL Marketo Measure] {#duplicate-records-and-marketo-measure}

>[!NOTE]
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedere ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

[!DNL Marketo Measure] utilizza l&#39;indirizzo e-mail come identificatore univoco quando abbina i dati a un lead o contatto correlato nel CRM. Quando [!DNL Marketo Measure] trova più lead o contatti con lo stesso indirizzo e-mail, vengono visualizzati gli stessi dati in tutti i record. L&#39;impatto di questa situazione si verifica quando si eseguono rapporti sui lead o sui contatti con [!DNL Marketo Measure] e si può erroneamente gonfiare il numero di persone univoche che che dispongono di punti di contatto dell&#39;acquirente.

Come si presenta nel reporting di [!DNL Marketo Measure]?

_Report di esempio: [!DNL Marketo Measure] persone con punti di contatto dell&#39;acquirente._

![&#x200B; 1](assets/1-1.png)

Per l&#39;ID persona [!DNL Marketo Measure] di kelsey@adobe.com è possibile vedere che esiste sia un lead che un contatto con tale indirizzo e-mail. In questo rapporto sono riportati 2 primi contatti, due contatti per la creazione di lead e due interazioni PostLC. Questi record duplicati condividono informazioni relative alla data e al punto di contatto che potrebbero portare alla conclusione che si tratta di due persone diverse nonostante siano la stessa persona.

**Consiglio**

* Per massimizzare il ritorno nei rapporti, ti consigliamo di utilizzare uno strumento di deduplicazione all’interno del CRM per assicurarti di creare solo record netti nuovi e univoci. Questa operazione può essere eseguita con lo strumento di automazione marketing o con un software separato installato nel sistema CRM. [!DNL Marketo Measure] non deduplica automaticamente i record e non offre questo servizio tramite il nostro software.
* In alternativa, è possibile unire manualmente i record durante l&#39;identificazione dei duplicati. Questo processo può essere lungo e noioso, ma l&#39;output di un reporting accurato vale l&#39;investimento di tempo.
