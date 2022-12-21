---
unique-page-id: 18874799
description: Istruzioni di layout della pagina - [!DNL Marketo Measure] - Documentazione del prodotto
title: Istruzioni di layout della pagina
exl-id: 627377f0-d0cf-448c-a7b5-7eb5634b9627
source-git-commit: b910e5aedb9e178058f7af9a6907a1039458ce7a
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 1%

---

# Istruzioni di layout della pagina {#page-layout-instructions}

>[!NOTE]
>
>È possibile visualizzare istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella nostra documentazione, ma vedi ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riflesso nel tuo CRM presto.

Facile da vedere [!DNL Marketo Measure] è consigliabile aggiornare i layout di pagina per [!UICONTROL Account], [!UICONTROL Contact], [!UICONTROL Lead], [!UICONTROL Opportunity]e [!UICONTROL Campaign] Oggetti. Le istruzioni sono suddivise per ciascun layout della pagina oggetto riportato di seguito.

Per iniziare, passa prima al tuo [!DNL Salesforce] Impostazioni e individua le [!UICONTROL Customize] scheda .

## Oggetto Campaign {#campaign-object}

È consigliabile aggiungere [!DNL Marketo Measure] nella tua campagna SFDC solo per la tua sandbox. I campi possono essere utilizzati per testare la generazione di punti di contatto. In produzione consigliamo di aggiungere solo la variabile [!DNL Marketo Measure] Pulsante Aggiorna in blocco data punto di contatto. Non è consigliabile aggiungere il [!DNL Marketo Measure] campi in produzione, in quanto puoi creare regole per la sincronizzazione delle campagne.

1. All’interno dell’opzione Genera, seleziona **[!UICONTROL Campaigns]**.

1. Clic **[!UICONTROL Page Layouts]**.

   ![](assets/1-1.jpg)

1. Fai clic su **[!UICONTROL Edit]** accanto al layout di pagina da aggiornare.

   ![](assets/2-1.jpg)

1. All&#39;interno di [!UICONTROL fields] seleziona l’opzione **[!UICONTROL Enable Buyer Touchpoints]** e trascinalo ovunque desideri sulla pagina. Quindi, aggiungi la **[!UICONTROL Touchpoint Start Date]** e **[!UICONTROL Touchpoint End Date]** campi.

   ![](assets/3-2.png)

1. Quindi, nella parte superiore della pagina fai clic su &quot;[!UICONTROL Buttons]&quot; nel menu di ricerca rapida.

1. Trascina **[!UICONTROL Bulk Update Touchpoint Date]** nella sezione dei pulsanti personalizzati.

   ![](assets/4-1.jpg)

1. Clic **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Se utilizzi più tipi di record Campaign, i valori della lista di selezione per **[!UICONTROL Enable Buyer Touchpoints]** Il campo dovrà essere aggiornato. Riferimento [articolo](/help/channel-tracking-and-setup/offline-channels/configurations-for-multiple-campaign-record-types.md) per istruzioni.

## Lead {#leads}

1. All’interno dell’opzione Genera, seleziona **[!UICONTROL Leads]**.

1. Clic **[!UICONTROL Page Layouts]**.

1. Fai clic su **[!UICONTROL Edit]** accanto al layout di pagina da aggiornare. Tieni presente che più layout di pagina possono contenere le sezioni Punti di contatto dell’acquirente .

1. Fare clic sull&#39;opzione della pagina VisualForce a sinistra nel menu di ricerca rapida.

1. Crea una nuova sezione e denominala &quot;Punti di contatto dell’acquirente&quot;.

   >[!NOTE]
   >
   >Selezionare il formato &quot;una colonna&quot; per ciascuna di queste sezioni.

1. Trascina **[!UICONTROL Marketo Measure Lead Related List]** Pagina VisualForce nella sezione di layout della pagina.

   ![](assets/5-1.png)

1. Fai clic sulla chiave inglese [!DNL VisualForce] modifica l&#39;altezza a 100 e abilita le barre di scorrimento.

1. Nel menu , seleziona la [!UICONTROL Canvas Apps] e crea una nuova sezione denominata &quot;Marketo Measure Insights&quot; (Approfondimenti misura) sotto i punti di contatto [!DNL VisualForce] sezione appena creata.

   >[!NOTE]
   >
   >Selezionare il formato &quot;una colonna&quot; per ciascuna di queste sezioni.

1. Trascina [!DNL Marketo Measure Insights] App canvas in quella nuova sezione creata. Fai clic su **Salva**. A volte è necessario salvare il layout di pagina prima di rilasciarlo nell’app Canvas, perché Salesforce non lo riconosce istantaneamente. Quindi, dopo aver creato la nuova sezione, salva il layout di pagina e quindi modifica nuovamente per trascinare l’app canvas all’interno di tale sezione. Questo vale per ogni oggetto.

   >[!NOTE]
   >
   >Per [!DNL Marketo Measure Insights] App Canvas per funzionare correttamente, [le autorizzazioni devono essere configurate correttamente](/help/configuration-and-setup/marketo-measure-insights-canvas-app/marketo-measure-insights-configuration.md).

   >[!TIP]
   >
   >La maggior parte dei clienti non utilizza i campi che terminano con (FT) o (LC) perché sono campi legacy da prima del [!DNL Marketo Measure] Il punto di contatto era un oggetto.

Se utilizzi il [!DNL Marketo Measure] caratteristica ABM, [fai clic qui per ulteriori istruzioni sul layout della pagina](/help/advanced-marketo-measure-features/account-based-marketing/account-based-marketing-overview.md).

## Contatti {#contacts}

1. All’interno dell’opzione Genera, seleziona **[!UICONTROL Contacts]**.

1. Clic **[!UICONTROL Page Layouts]**.

1. Selezionare il layout di pagina da modificare.

   Passa all’opzione Elenchi correlati nel menu di ricerca rapida e aggiungi la **[!UICONTROL Buyer Touchpoints]** elenco correlato.

1. Fai clic sull’icona a forma di chiave inglese e aggiungi le seguenti colonne in questo ordine:

   * Punto di contatto dell&#39;acquirente
   * Canale di marketing
   * Origine punto di contatto
   * Nome della campagna pubblicitaria
   * Posizione punto di contatto
   * Data punto di contatto

1. Ordina per: Data punto di contatto, crescente.

   ![](assets/6.jpg)

1. Espandi l’opzione Pulsanti e deseleziona **[!UICONTROL New]**.

   ![](assets/7.png)

1. Torna alla pagina [!UICONTROL Related List] nel menu e ora aggiungi la **[!UICONTROL Buyer Attribution Touchpoint]** elenco correlato.

1. Fai clic sull’icona a forma di chiave inglese e aggiungi le seguenti colonne in questo ordine:

   * Punto di contatto attribuzione
   * Canale di marketing
   * Opportunità
   * Nome della campagna pubblicitaria
   * Tipo punto di contatto
   * Posizione punto di contatto
   * A forma di W dell’attribuzione (_o modello di attribuzione più affidabile, ad esempio Percorso completo o Personalizzato_)
   * A forma di W ricavi (_o modello di attribuzione più affidabile, ad esempio Percorso completo o Personalizzato_)
   * Data punto di contatto

1. Ordina per punto di contatto [!UICONTROL Date] > [!UICONTROL Ascending].

1. Espandi la sezione Pulsanti e deseleziona **[!UICONTROL New]**.

1. Clic **[!UICONTROL Save]**.

## Opportunità {#opportunities}

1. All’interno dell’opzione Genera, seleziona **[!UICONTROL Opportunities]**.

1. Clic **[!UICONTROL Page Layouts]**.

1. Selezionare il layout di pagina da modificare.

1. Aggiungi il **[!UICONTROL Buyer Attribution Touchpoint]** Elenco correlato e fai clic sulla chiave inglese per aggiungere le colonne seguenti per Opportunità:

   * Punto di contatto attribuzione
   * Canale di marketing
   * Contatto
   * Nome della campagna pubblicitaria
   * Tipo punto di contatto
   * Posizione punto di contatto
   * A forma di W dell’attribuzione (_o modello di attribuzione più affidabile, ad esempio Percorso completo o Personalizzato_)
   * A forma di W ricavi (_o modello di attribuzione più affidabile, ad esempio Percorso completo o Personalizzato_)
   * Data punto di contatto

1. Ordina per [!UICONTROL Touchpoint Date] > [!UICONTROL Ascending].

1. Deseleziona **[!UICONTROL New]** all&#39;interno del [!UICONTROL Buttons] sezione .

1. Clic **[!UICONTROL Save]**.

## Account {#accounts}

1. All’interno dell’opzione Genera, seleziona **[!UICONTROL Accounts]**.

1. Clic **[!UICONTROL Page Layouts]**.

1. Selezionare il layout di pagina da modificare.

1. Aggiungi il **[!UICONTROL Buyer Attribution Touchpoint]** Elenco correlato e fai clic sulla chiave inglese per aggiungere le colonne seguenti:

   * Punto di contatto attribuzione
   * Canale di marketing
   * Opportunità
   * Nome della campagna pubblicitaria
   * Tipo punto di contatto
   * Posizione punto di contatto
   * A forma di W dell’attribuzione (_o modello di attribuzione più affidabile, ad esempio Percorso completo o Personalizzato_)
   * A forma di W ricavi (_o modello di attribuzione più affidabile, ad esempio Percorso completo o Personalizzato_)
   * Data punto di contatto

1. Ordina per data punto di contatto > Crescente.

1. Deseleziona **[!UICONTROL New]** all&#39;interno del [!UICONTROL Buttons] sezione .

1. Clic **[!UICONTROL Save]**.

Se utilizzi il [!DNL Marketo Measure] caratteristica ABM,  [fai clic qui per ulteriori istruzioni sul layout della pagina](/help/advanced-marketo-measure-features/account-based-marketing/account-based-marketing-overview.md).
