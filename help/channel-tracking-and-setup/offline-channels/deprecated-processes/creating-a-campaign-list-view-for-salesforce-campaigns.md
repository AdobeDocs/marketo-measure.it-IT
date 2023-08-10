---
unique-page-id: 18874718
description: Creazione di una vista a elenco campagne per [!DNL Salesforce Campaigns] - [!DNL Marketo Measure] - Documentazione del prodotto
title: Creazione di una vista a elenco campagne per [!DNL Salesforce] Campagne
exl-id: 8c673ea3-ac24-4b3d-b67d-76888179c07a
feature: Channels
source-git-commit: e01738222e8845112892c0258cb084a4f0ebb257
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Creazione di una vista a elenco campagne per [!DNL Salesforce] Campagne {#creating-a-campaign-list-view-for-salesforce-campaigns}

Scopri come creare una Vista a elenco per le campagne da sincronizzare con i punti di contatto dell’acquirente.

>[!NOTE]
>
>Questo articolo riguarda un processo obsoleto. Invitiamo gli utenti a utilizzare [processo in-app nuovo e migliorato](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

La vista a elenco di Campaign che è possibile creare consente di avere una posizione &quot;vai a&quot; per visualizzare e gestire i campi &quot;Tipo&quot; e &quot;Abilita punti di contatto acquirenti&quot; per garantire che ciascuno dei [!DNL Salesforce] le campagne che informano i canali di marketing offline vengono configurate correttamente.

1. Passa alla scheda Campagne in [!DNL Salesforce] e crea una nuova vista a elenco
1. Denomina la visualizzazione &quot;Campagne da sincronizzare con [!DNL Marketo Measure].&quot;
1. Vogliamo che questo elenco mostri solo le campagne con cui desideri sincronizzarle [!DNL Marketo Measure] quindi abbiamo bisogno di un paio di filtri:

   * **Tipo** [È UGUALE A] &quot;Tutti i tipi di campagna mappati sui canali offline&quot;. Consulta il piano di implementazione o la scheda Canali offline in [!DNL Marketo Measure] ([experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} -> Il mio account -> Impostazioni -> Canali offline). Puoi selezionare i Tipi desiderati (quelli mappati a un canale di marketing offline) tramite l’icona della lente di ingrandimento.

      * Scegli un massimo di 3 tipi per ciascun filtro. In un campo filtro è disponibile un limite di caratteri. Inizia con 3 Tipi per filtro e aggiungi ulteriori righe di filtri &quot;Tipo&quot;, se necessario.

   * **Data di creazione** [MAGGIORE O UGUALE A] tuo [!DNL Marketo Measure] data di inizio. Puoi trovare la data di inizio nella dashboard del ROI all’interno di [!DNL Marketo Measure] App. Seleziona semplicemente &quot;Dalla data di creazione&quot; nell’intervallo di date del trattino per visualizzare la data di inizio.
   * **&#42;Tipo di record&#42;** - Per apportare modifiche nella Vista a elenco, è necessario aggiungere un filtro per Tipo di record. Ogni record della campagna che potresti dover modificare deve avere lo stesso Tipo di record.

1. Modifica i campi selezionati da visualizzare nella vista a elenco. L’impostazione completa della vista a elenco dovrebbe avere un aspetto simile a quello riportato di seguito:

   Questa vista ti consente di visualizzare le campagne e, se necessario, modificare i campi &quot;Tipo&quot; e &quot;Abilita punti di contatto buyer&quot;. Quando crei nuove campagne da sincronizzare con [!DNL Marketo Measure], saranno visibili in questa visualizzazione e puoi gestire tutte le impostazioni per tali campagne direttamente dall’interno dell’elenco.

   Per apportare modifiche in linea dalla vista a elenco, è necessario assicurarsi che quanto segue sia vero anche all’interno della [!DNL Salesforce] configurazione:

   * **[!UICONTROL Setup]** > **[!UICONTROL User Interface]** > **[!UICONTROL Enable Inline Editing]**
   * È inoltre necessario selezionare Abilita elenchi avanzati (sotto la casella per la modifica in linea)
   * Assicurati di disporre delle autorizzazioni per i campi

>[!MORELIKETHIS]
>
>[Risoluzione dei problemi comuni della vista a elenco Modifica in linea](http://help.salesforce.com/articleView?id=000003911&amp;language=en_US&amp;type=1){target="_blank"}
