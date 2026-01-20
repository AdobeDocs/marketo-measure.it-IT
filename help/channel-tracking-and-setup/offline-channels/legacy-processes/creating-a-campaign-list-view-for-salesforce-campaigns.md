---
unique-page-id: 18874718
description: Creazione di una visualizzazione elenco campagne per  [!DNL Salesforce Campaigns] - [!DNL Marketo Measure]
title: Creazione di una visualizzazione elenco campagne per [!DNL Salesforce] Campagne
exl-id: 8c673ea3-ac24-4b3d-b67d-76888179c07a
feature: Channels
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# Creazione di una visualizzazione elenco campagne per [!DNL Salesforce] campagne {#creating-a-campaign-list-view-for-salesforce-campaigns}

Scopri come creare una Vista a elenco per le campagne da sincronizzare con i punti di contatto dell’acquirente.

>[!NOTE]
>
>Questo articolo riguarda un processo obsoleto. Invitiamo gli utenti a utilizzare il [nuovo processo in-app migliorato](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

La visualizzazione elenco di Campaign che è possibile creare consente di avere una posizione di destinazione per visualizzare e gestire i campi Tipo e Abilita punti di contatto dell&#39;acquirente per garantire che tutte le campagne [!DNL Salesforce] che informano i canali di marketing offline siano configurate correttamente.

1. Passa alla scheda Campagne in [!DNL Salesforce] e crea una nuova visualizzazione elenco
1. Denomina la visualizzazione &quot;Campagne da sincronizzare con [!DNL Marketo Measure]&quot;.
1. L&#39;elenco deve mostrare solo le campagne che si desidera sincronizzare con [!DNL Marketo Measure], pertanto sono necessari due filtri:

   * **Tipo** [UGUALE A] &#39;Tutti i tipi di campagna mappati ai tuoi canali offline&#39;. Consulta il tuo piano di implementazione o la scheda Canali offline in [!DNL Marketo Measure] ([experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} -> Il mio account -> Impostazioni -> Canali offline). Puoi selezionare i Tipi desiderati (quelli mappati a un canale di marketing offline) tramite l’icona della lente di ingrandimento.

      * Scegli un massimo di 3 tipi per ciascun filtro. In un campo filtro è disponibile un limite di caratteri. Inizia con 3 Tipi per filtro e aggiungi ulteriori righe di filtri &quot;Tipo&quot;, se necessario.

   * **Data creazione** [MAGGIORE O UGUALE] la data di inizio [!DNL Marketo Measure]. Puoi trovare la data di inizio nel dashboard del ROI all&#39;interno dell&#39;app [!DNL Marketo Measure]. Seleziona semplicemente &quot;Dalla data di creazione&quot; nell’intervallo di date del trattino per visualizzare la data di inizio.
   * **&#42;Tipo di record&#42;** - Per apportare modifiche nella visualizzazione elenco, è necessario aggiungere un filtro per il tipo di record. Ogni record della campagna che potresti dover modificare deve avere lo stesso Tipo di record.

1. Modifica i campi selezionati da visualizzare nella vista a elenco. L’impostazione completa della vista a elenco dovrebbe avere un aspetto simile a quello riportato di seguito:

   Questa vista ti consente di visualizzare le campagne e, se necessario, modificare i campi &quot;Tipo&quot; e &quot;Abilita punti di contatto buyer&quot;. Quando crei nuove campagne che devono essere sincronizzate con [!DNL Marketo Measure], queste appariranno in questa visualizzazione e puoi gestire tutte le impostazioni per tali campagne direttamente dall&#39;elenco.

   Per apportare modifiche in linea dalla Vista a elenco, è necessario verificare che anche le seguenti condizioni siano soddisfatte nella configurazione di [!DNL Salesforce]:

   * **[!UICONTROL Setup]** > **[!UICONTROL User Interface]** > **[!UICONTROL Enable Inline Editing]**
   * È inoltre necessario selezionare Abilita elenchi avanzati (sotto la casella per la modifica in linea)
   * Assicurati di disporre delle autorizzazioni per i campi

>[!MORELIKETHIS]
>
>[Risoluzione dei problemi comuni relativi alla modifica in linea della vista a elenco](http://help.salesforce.com/articleView?id=000003911&language=en_US&type=1){target="_blank"}
