---
description: Metodi di gestione della spesa - [!DNL Marketo Measure]
title: Metodi di gestione della spesa
exl-id: 36478d8d-986c-4d4f-8854-3287d6c57a9d
feature: Spend Management
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# Metodi di gestione della spesa {#spend-management-methods}

I dati di spesa sono fondamentali per il successo dei rapporti sul ROI con [!DNL Marketo Measure]. Per ottenere rapporti sul ROI precisi e completi su tutti i canali e i sottocanali, è necessario assicurarsi di disporre dei dati di spesa appropriati da inserire in [!DNL Marketo Measure].

Esistono tre modi per inserire i dati di spesa in [!DNL Marketo Measure]. Ogni metodo è progettato per estrarre i dati di spesa da input di dati specifici.

**1 account API connessi**

Qualsiasi account annuncio a cui ti sei connesso [!DNL Marketo Measure] tramite un’API, la sua spesa viene automaticamente inserita in [!DNL Marketo Measure] per il reporting sul ROI. Per verificare quali account hai connesso e quindi richiamare la spesa, vai al tuo [!DNL Marketo Measure] App e seleziona la [!UICONTROL Connections] sotto il [!UICONTROL Integrations] sezione. Per ulteriori dettagli sulla configurazione delle connessioni API, consulta [Piattaforme di annunci integrate](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms).

**Sincronizzazione costi campagna CRM 2**

Ogni [!DNL Marketo Measure] l’account ha accesso a una funzione denominata [Sincronizza costi campagna CRM](/help/marketing-spend/spend-management/crm-campaign-costs.md#availability). Per impostazione predefinita, questo bit di funzione è impostato su &quot;No&quot; ma può essere attivato in qualsiasi momento.

![](assets/spend-management-methods-1.png)

Quando è abilitata, questa funzione richiama automaticamente le spese da qualsiasi campagna/programma di gestione delle relazioni con i clienti che soddisfa i seguenti criteri:

i. [!DNL Marketo Measure] cerca innanzitutto di verificare se la campagna/il programma sta creando punti di contatto, da un [Regola di sincronizzazione della campagna](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md) creato o un corrispondente [Regola di sincronizzazione programmi](/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md) che è stato creato o [Abilita valore punti di contatto acquirenti](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md#how-to-create-a-campaign-and-sync-buyer-touchpoints) è &quot;Includi tutti i membri della campagna&quot; o &quot;Includi i membri della campagna &quot;Con risposta&quot;.&quot;

ii. È necessario inserire una data di inizio nella campagna/nel programma

iii. È necessario inserire una data di fine nella campagna/nel programma

iv. È necessario specificare il costo effettivo (per le campagne in SFDC) o il costo del periodo (per i programmi in Marketo).

**3 Caricamento manuale dei costi**

Questo metodo consente di: [carica manualmente i dati di spesa](/help/marketing-spend/spend-management/marketing-channel-costs.md#uploading-marketing-costs) per i canali e i sottocanali che non sono coperti dagli account API connessi o dalla sincronizzazione dei costi delle campagne CRM. Passando alla sezione Spese di marketing nel tuo [!DNL Marketo Measure] , puoi caricare i dati di spesa tramite un file CSV per qualsiasi canale.

I clienti possono utilizzare una combinazione di tutti e tre questi metodi per gestire la propria spesa, a seconda della configurazione specifica del [!DNL Marketo Measure]. Perché esistono tre metodi per importare la spesa in [!DNL Marketo Measure], consigliamo vivamente di utilizzare la bacheca Marketing Spend che si trova in Discover per ottenere una visualizzazione completa di tutti i dati di spesa. Questa bacheca è l’unico posto in cui potrai vedere tutti i tuoi canali e la relativa spesa associata. Il comitato per le spese di marketing può aiutarti a identificare rapidamente dove potrebbero essere presenti delle lacune nei dati di spesa e come migliorare il reporting sul ROI.
