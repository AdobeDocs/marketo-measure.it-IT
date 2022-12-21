---
unique-page-id: 18874614
description: Rapporto Lead con punti di contatto dell’acquirente - [!DNL Marketo Measure] - Documentazione del prodotto
title: Rapporto Lead con punti di contatto dell’acquirente
exl-id: 0376abb0-5eed-41bb-ab4f-3c204ab437df
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---

# Rapporto Lead con punti di contatto dell’acquirente {#leads-with-buyer-touchpoints-report}

>[!NOTE]
>
>È possibile visualizzare istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella nostra documentazione, ma ancora vedi &quot;[!DNL Bizible]&quot; nel CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riflesso nel tuo CRM presto.

Con le funzionalità di reporting disponibili puoi contare su numerose funzionalità predefinite per [!DNL Marketo Measure], ma sono disponibili alcuni tipi di report aggiuntivi che consigliamo di creare. Scopri come creare un lead inclusivo con il tipo di rapporto Punti di contatto per l’acquirente qui sotto.

1. Passa all’opzione Configurazione in [!DNL Salesforce]. Da lì, espandi il raggruppamento &quot;Crea&quot; e seleziona **[!UICONTROL Report Types]**.

   ![](assets/1.jpg)

1. Seleziona **[!UICONTROL New Custom Report Type]**.

   ![](assets/2.jpg)

1. Imposta l’oggetto principale come &quot;Lead&quot; e all’interno dell’input &quot;Etichetta del tipo di rapporto&quot; &quot;Lead con punti di contatto dell’acquirente - Inclusivo&quot;. Memorizza il rapporto nella categoria &quot;Lead&quot; e modifica lo stato di distribuzione in **[!UICONTROL Deployed]**. Quindi seleziona **[!UICONTROL Next]**.

   ![](assets/3.jpg)

1. Per le relazioni con gli oggetti, selezionare la **[!DNL Marketo Measure]Persone** come oggetto secondario. Selezionare la relazione da A a B come, &quot;Ogni record &#39;A&#39; deve avere almeno un record &#39;B&#39; correlato.&quot; Da lì, si relazionerà l&#39;oggetto &quot;Buyer Touchpoint&quot; e si selezionerà la stessa relazione tra gli oggetti B e C.

   ![](assets/4.jpg)

1. Salva e inizia a creare alcuni report!
