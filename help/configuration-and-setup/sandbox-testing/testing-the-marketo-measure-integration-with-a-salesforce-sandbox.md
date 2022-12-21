---
unique-page-id: 18874765
description: Verifica dell’integrazione delle misure di Marketo con una Sandbox Salesforce - [!DNL Marketo Measure] - Documentazione del prodotto
title: Verifica dell’integrazione delle misure Marketo con una sandbox Salesforce
exl-id: df40b000-4572-46df-aef5-8f690ca8ed7a
source-git-commit: 993a326c377b3b6ff48c4e0114b59297f9ca2ca6
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 1%

---

# Verifica dell’integrazione delle misure Marketo con una sandbox Salesforce {#testing-the-marketo-measure-integration-with-a-salesforce-sandbox}

>[!NOTE]
>
>È possibile visualizzare istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella nostra documentazione, ma vedi ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riflesso nel tuo CRM presto.

Uno dei [!DNL Marketo Measure] Le funzionalità principali sono la capacità di monitorare le attività di marketing digitale attraverso azioni sul sito web e quindi inviare tali dati alla produzione [!DNL Salesforce org] tramite Lead e contatti. Tuttavia, in genere non vi sono lead in entrata creati dal sito web all’interno di un’integrazione Sandbox, pertanto l’attenzione sui dati proverrà da un punto di vista puramente offline.

Di seguito sono riportate le due fonti a cui si fa riferimento per entrambe le fasi del test. [Passaggi 1-4](https://help.salesforce.com/apex/HTViewHelpDoc?id=lead_import_wizard.htm&amp;language=en_US) e [Passaggi 5-6](/help/channel-tracking-and-setup/offline-channels/syncing-offline-campaigns.md). Si consiglia di rivedere questi documenti in quanto forniscono maggiori dettagli in alcune aree.

1. Sarà necessario creare alcuni lead in un CSV per caricarli in una campagna. Il modo per farlo è esportare alcuni Lead attraverso un report nella tua produzione Salesforce. In caso contrario, puoi creare manualmente i lead in un file Excel e quindi salvarli come CSV da importare. Ti servono solo circa 20 dischi. Il file deve avere le colonne seguenti:

   1. E-mail
   1. Azienda
   1. Cognome
   1. Nome (facoltativo ma consigliato)

1. Accedi al tuo ambiente Sandbox.
1. Innanzitutto creerai una campagna di test. È consigliabile utilizzare un tipo di campagna, ad esempio Evento o Newsletter.
1. Una volta creata la campagna, caricate i lead come membri della campagna selezionando **[!UICONTROL Manage Members]** > **[!UICONTROL Add Members]** > **[!UICONTROL Import Files]**.
1. Al termine, tornando al layout della pagina Campaign, verrà visualizzato il campo &quot;Abilita punti di contatto dell’acquirente&quot;, che è un campo di selezione. Scegli il valore: **[!UICONTROL Include All Campaign Members]**.

Al termine, verrà avviata una sincronizzazione tra [!DNL Marketo Measure] e [!DNL Salesforce] e applicare punti di contatto ai record Lead. È consigliabile controllare nuovamente il giorno successivo tramite un rapporto denominato: &quot;Punto di contatto dell&#39;acquirente sui lead&quot; trovato nella sezione [!UICONTROL Buyer Touchpoints Reports] nella scheda Rapporti. Se il rapporto popola un punto di contatto per ogni lead, questo è un segno di successo.
