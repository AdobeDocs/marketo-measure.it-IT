---
description: Rapporto Lead con punti di contatto buyer - [!DNL Marketo Measure]
title: Rapporto Lead con punti di contatto buyer
exl-id: 0376abb0-5eed-41bb-ab4f-3c204ab437df
feature: Touchpoints, Reporting
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---


# Rapporto Lead con punti di contatto buyer {#leads-with-buyer-touchpoints-report}

>[!NOTE]
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedere comunque &quot;[!DNL Bizible]&quot; nel CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

Sono disponibili numerose funzionalità di reporting a portata di mano per [!DNL Marketo Measure], ma si consiglia di creare alcuni tipi di report aggiuntivi. Scopri come creare un tipo di rapporto Lead inclusivi con punti di contatto buyer di seguito.

1. Passare all&#39;opzione di installazione in [!DNL Salesforce]. Da qui, espandere il raggruppamento &quot;Crea&quot; e selezionare **[!UICONTROL Report Types]**.

   ![Pagina Tipi di report Salesforce che mostra la configurazione di lead con punti di contatto acquirenti](assets/1.jpg)

1. Seleziona **[!UICONTROL New Custom Report Type]**.

   ![Creazione guidata nuovo tipo di report personalizzato in Salesforce](assets/2.jpg)

1. Impostare l&#39;oggetto principale come &quot;Lead&quot; e all&#39;interno dell&#39;input &quot;Etichetta tipo di report&quot; &quot;Lead con punti di contatto buyer - Inclusivi&quot;. Memorizzare il report nella categoria &quot;Lead&quot; e modificare lo stato di distribuzione in **[!UICONTROL Deployed]**. Quindi selezionare **[!UICONTROL Next]**.

   ![Dettagli del tipo di report con lead come oggetto principale](assets/3.jpg)

1. Per le relazioni tra gli oggetti, selezionare l&#39;oggetto **[!DNL Marketo Measure]Persons** come oggetto secondario. Selezionare la relazione da A a B come, &quot;Ogni record &#39;A&#39; deve avere almeno un record &#39;B&#39; correlato.&quot; A questo punto, verrà correlato l&#39;oggetto &quot;Buyer Touchpoint&quot; e verrà selezionata la stessa relazione tra gli oggetti B e C.

   ![Selezione delle relazioni tra gli oggetti, inclusi i punti di contatto Marketo Measure Persons e Buyer](assets/4.jpg)

1. Salva e inizia a creare alcuni rapporti.
