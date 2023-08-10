---
unique-page-id: 18874614
description: Rapporto Lead con punti di contatto buyer - [!DNL Marketo Measure] - Documentazione del prodotto
title: Rapporto Lead con punti di contatto buyer
exl-id: 0376abb0-5eed-41bb-ab4f-3c204ab437df
feature: Touchpoints, Reporting
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---

# Rapporto Lead con punti di contatto buyer {#leads-with-buyer-touchpoints-report}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella nostra documentazione, ma vedi comunque &quot;[!DNL Bizible]&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

Sono già disponibili numerose funzionalità di reporting per [!DNL Marketo Measure], ma è consigliabile creare alcuni tipi di rapporto aggiuntivi. Scopri come creare un tipo di rapporto Lead inclusivi con punti di contatto buyer di seguito.

1. Passa all’opzione Configurazione in [!DNL Salesforce]. Da qui, espandi il raggruppamento &quot;Crea&quot; e seleziona **[!UICONTROL Report Types]**.

   ![](assets/1.jpg)

1. Seleziona **[!UICONTROL New Custom Report Type]**.

   ![](assets/2.jpg)

1. Impostare l&#39;oggetto principale come &quot;Lead&quot; e all&#39;interno dell&#39;input &quot;Etichetta tipo di report&quot; &quot;Lead con punti di contatto buyer - Inclusivi&quot;. Memorizza il rapporto nella categoria &quot;Lead&quot; e modifica lo stato di distribuzione in **[!UICONTROL Deployed]**. Quindi seleziona **[!UICONTROL Next]**.

   ![](assets/3.jpg)

1. Per le relazioni tra gli oggetti, selezionare **[!DNL Marketo Measure]Persone** come oggetto secondario. Selezionare la relazione da A a B come, &quot;Ogni record &#39;A&#39; deve avere almeno un record &#39;B&#39; correlato.&quot; A questo punto, verrà correlato l&#39;oggetto &quot;Punto di contatto acquirente&quot; e verrà selezionata la stessa relazione tra gli oggetti B e C.

   ![](assets/4.jpg)

1. Salva e inizia a creare alcuni rapporti.
