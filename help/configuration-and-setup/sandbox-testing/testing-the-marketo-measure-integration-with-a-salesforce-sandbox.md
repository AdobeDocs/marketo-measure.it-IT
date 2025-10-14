---
unique-page-id: 18874765
description: Verifica dell'integrazione di Marketo Measure con una sandbox Salesforce - [!DNL Marketo Measure]
title: Test dell’integrazione di Marketo Measure con una sandbox Salesforce
exl-id: df40b000-4572-46df-aef5-8f690ca8ed7a
feature: Salesforce
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 1%

---

# Test dell’integrazione di Marketo Measure con una sandbox Salesforce {#testing-the-marketo-measure-integration-with-a-salesforce-sandbox}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedere ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

Una delle funzionalità di base di [!DNL Marketo Measure] è la capacità di monitorare le attività di marketing digitale attraverso le azioni sul sito Web e quindi di inviare tali dati alla produzione [!DNL Salesforce org] tramite lead e contatti. Tuttavia, in genere non sono presenti lead in entrata creati dal sito web all’interno di un’integrazione Sandbox, pertanto l’attenzione sui dati sarà focalizzata da un punto di vista puramente offline.

Di seguito sono elencate le due origini a cui si fa riferimento per entrambe le fasi del test. [Passaggi 1-4](https://help.salesforce.com/s/articleView?id=lead_import_wizard.htm&language=en_US&type=5) e [Passaggi 5-6](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md). Si consiglia di rivedere questi documenti in quanto forniscono maggiori dettagli in alcune aree.

1. Devi creare alcuni lead in un CSV in modo da poterli caricare in una campagna. A tal fine, devi esportare alcuni lead tramite un rapporto nella tua Salesforce di produzione. In caso contrario, puoi creare manualmente i lead in un file Excel e quindi salvarlo come CSV per l’importazione. Sono necessari solo circa 20 record. Il file deve avere le seguenti colonne:

   1. E-mail
   1. Azienda
   1. Cognome
   1. Nome (facoltativo ma consigliato)

1. Accedi all’ambiente Sandbox.
1. Crea una campagna di test. Utilizza un tipo di campagna come Evento o Newsletter.
1. Una volta creata la campagna, carica i lead come membri della campagna selezionando **[!UICONTROL Manage Members]** > **[!UICONTROL Add Members]** > **[!UICONTROL Import Files]**.
1. Una volta completato, tornando al layout della pagina Campaign, potrai &quot;Abilitare i punti di contatto dell’acquirente&quot;, che è un campo dell’elenco a discesa. Scegliere il valore: **[!UICONTROL Include All Campaign Members]**.

Al termine, avvia una sincronizzazione tra [!DNL Marketo Measure] e [!DNL Salesforce] e applica punti di contatto ai record Lead. Si consiglia di controllare nuovamente il giorno successivo tramite un report denominato: &quot;Buyer Touchpoint su lead&quot; trovato nella cartella [!UICONTROL Buyer Touchpoints Reports] all&#39;interno della scheda Report. Se il report compila un punto di contatto per ogni lead, questo è un segno di successo.
