---
unique-page-id: 18874718
description: Creazione di una visualizzazione elenco di campagne per [!DNL Salesforce Campaigns] - [!DNL Marketo Measure] - Documentazione del prodotto
title: Creazione di una visualizzazione elenco di campagne per [!DNL Salesforce] Campagne
exl-id: 8c673ea3-ac24-4b3d-b67d-76888179c07a
source-git-commit: 02f686645e942089df92800d8d14c76215ae558f
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Creazione di una visualizzazione elenco di campagne per [!DNL Salesforce] Campagne {#creating-a-campaign-list-view-for-salesforce-campaigns}

Scopri come creare una visualizzazione a elenco per le campagne da sincronizzare con i punti di contatto dell’acquirente.

La vista a elenco Campagna che può essere creata ti consente di disporre di una posizione di &quot;partenza&quot; per visualizzare e gestire i campi &quot;Tipo&quot; e &quot;Abilita punti di contatto dell’acquirente&quot; per garantire che ciascuno dei tuoi [!DNL Salesforce] le campagne che informano i tuoi canali di marketing offline sono impostate correttamente.

1. Vai alla scheda Campagne in [!DNL Salesforce] e creare una nuova vista a elenco
1. Assegna un nome alla visualizzazione &quot;Campagne con cui sincronizzare [!DNL Marketo Measure].&quot;
1. Vogliamo che questo elenco mostri solo le campagne con cui desideri eseguire la sincronizzazione [!DNL Marketo Measure] quindi abbiamo bisogno di un paio di filtri:

   * **Tipo** [UGUALE A] &quot;Tutti i tipi di campagna mappati ai tuoi canali offline&quot;. Fai riferimento al piano di implementazione o alla scheda Canali offline in [!DNL Marketo Measure] ([experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target=&quot;_blank&quot;} -> Il mio account -> Impostazioni -> Canali offline). Puoi selezionare i tipi desiderati (quelli mappati su un canale di marketing offline) tramite l’icona della lente di ingrandimento.

      * Scegli 3 tipi max per ogni filtro. In un campo filtro è possibile includere un limite di caratteri. Inizia con 3 tipi per filtro e aggiungi ulteriori righe di filtri &quot;Type&quot; se necessario.
   * **Data creazione** [MAGGIORE O UGUALE A] le [!DNL Marketo Measure] data di inizio. Puoi trovare la data di inizio nel dashboard ROI all’interno di [!DNL Marketo Measure] App. Seleziona &quot;Dalla data di creazione&quot; nell&#39;intervallo di date del trattino e mostrerà la data di inizio.
   * **&#42;Tipo di record&#42;** - Per apportare modifiche nella vista a elenco, è necessario aggiungere un filtro per Tipo di record. Per ogni record della campagna che è necessario modificare è necessario lo stesso tipo di record.


1. Modifica i campi selezionati per visualizzarli nella vista a elenco. L’impostazione completa della vista a elenco dovrebbe essere simile a quella riportata di seguito:

   Questa visualizzazione ti consente di visualizzare le campagne e, se necessario, di modificare i campi &quot;Tipo&quot; e &quot;Abilita punti di contatto dell’acquirente&quot;. Quando crei nuove campagne con cui sincronizzare [!DNL Marketo Measure], vengono visualizzate in questa visualizzazione e puoi gestire tutte le impostazioni per tali campagne direttamente dall’elenco.

   Per apportare modifiche in linea dalla vista a elenco, è necessario assicurarsi che quanto segue sia valido anche all’interno della [!DNL Salesforce] configurazione:

   * **[!UICONTROL Setup]** > **[!UICONTROL User Interface]** > **[!UICONTROL Enable Inline Editing]**
   * È inoltre necessario abilitare gli elenchi migliorati selezionati (sotto la casella per la modifica in linea)
   * Assicurati di disporre delle autorizzazioni per i campi

>[!MORELIKETHIS]
>
>[Risoluzione dei problemi comuni relativi alla modifica in linea della vista a elenco](http://help.salesforce.com/articleView?id=000003911&amp;language=en_US&amp;type=1){target=&quot;_blank&quot;}
