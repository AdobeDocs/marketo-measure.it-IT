---
unique-page-id: 18874572
description: Duplicare record e [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Duplicare record e [!DNL Marketo Measure]
exl-id: e340100c-120a-4771-946d-336a1458da4e
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Duplicare record e [!DNL Marketo Measure] {#duplicate-records-and-marketo-measure}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedi ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

[!DNL Marketo Measure] utilizza l’indirizzo e-mail come identificatore univoco quando si abbinano i dati a un lead o contatto correlato nel sistema di gestione delle relazioni con i clienti. Quando [!DNL Marketo Measure] trova più lead o contatti con lo stesso indirizzo e-mail, vengono visualizzati gli stessi dati su tutti i record. L’impatto di questo avviene quando esegui rapporti sui lead o sui contatti con [!DNL Marketo Measure] e può erroneamente gonfiare il numero di persone univoche che hanno punti di contatto dell’acquirente.

Come si presenta in [!DNL Marketo Measure] Generare rapporti?

_Esempio di rapporto: [!DNL Marketo Measure] Persone con punti di contatto dell’acquirente._

![](assets/1-1.png)

È possibile visualizzare per [!DNL Marketo Measure] ID persona di kelsey@adobe.com che indica l’esistenza di un lead e di un contatto con tale indirizzo e-mail. In questo rapporto sono riportati 2 primi contatti, due contatti per la creazione di lead e due interazioni PostLC. Questi record duplicati condividono informazioni relative alla data e al punto di contatto che potrebbero portare alla conclusione che si tratta di due persone diverse nonostante siano la stessa persona.

**Consiglio**

* Per massimizzare il ritorno nei rapporti, ti consigliamo di utilizzare uno strumento di deduplicazione all’interno del CRM per assicurarti di creare solo record netti nuovi e univoci. Questa operazione può essere eseguita con lo strumento di automazione marketing o con un software separato installato nel sistema CRM. [!DNL Marketo Measure] non deduplica automaticamente i record e non offre questo servizio tramite il nostro software.
* In alternativa, è possibile unire manualmente i record durante l&#39;identificazione dei duplicati. Questo processo può essere lungo e noioso, ma l&#39;output di un reporting accurato vale l&#39;investimento di tempo.
