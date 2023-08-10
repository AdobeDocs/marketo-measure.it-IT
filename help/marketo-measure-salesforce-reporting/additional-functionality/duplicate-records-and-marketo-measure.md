---
unique-page-id: 18874572
description: Duplicare record e [!DNL Marketo Measure] - [!DNL Marketo Measure] - Documentazione del prodotto
title: Duplicare record e [!DNL Marketo Measure]
exl-id: e340100c-120a-4771-946d-336a1458da4e
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Duplicare record e [!DNL Marketo Measure] {#duplicate-records-and-marketo-measure}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella nostra documentazione, ma vedi ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

[!DNL Marketo Measure] sfrutta l’indirizzo e-mail come identificatore univoco quando si abbinano i dati a un lead o contatto correlato nel CRM. Quando [!DNL Marketo Measure] trova più lead o contatti con lo stesso indirizzo e-mail, gli stessi dati verranno visualizzati su tutti i record. L’impatto di questo avviene quando esegui rapporti sui lead o sui contatti con [!DNL Marketo Measure] e può erroneamente gonfiare la quantità di persone univoche che hanno punti di contatto dell’acquirente.

Come si presenta in [!DNL Marketo Measure] Generare rapporti?

_Esempio di rapporto: [!DNL Marketo Measure] Persone con punti di contatto dell’acquirente._

![](assets/1-1.png)

È possibile visualizzare per [!DNL Marketo Measure] ID persona di kelsey@adobe.com che indica l’esistenza di un lead e di un contatto con tale indirizzo e-mail. In questo rapporto sono riportati 2 primi contatti, 2 contatti per la creazione di lead e 2 interazioni PostLC. Questi record duplicati condividono la stessa data di contatto e le stesse informazioni sui punti di contatto che potrebbero portare alla conclusione che sono due persone diverse nonostante siano la stessa persona.

**Consiglio**

* Per massimizzare il ritorno nei rapporti, ti consigliamo di sfruttare uno strumento di deduplicazione all’interno del tuo sistema di gestione delle relazioni con i clienti per assicurarti di creare solo record netti nuovi e univoci. Questa operazione può essere eseguita con lo strumento di automazione marketing o con un software separato installato nel sistema CRM. [!DNL Marketo Measure] non deduplica automaticamente i record e non offre questo servizio tramite il nostro software.
* In alternativa, è possibile unire manualmente i record durante l&#39;identificazione dei duplicati. Questo processo può essere lungo e noioso, ma il risultato di una segnalazione accurata vale il tempo investito.
