---
description: Metodi di gestione delle spese - [!DNL Marketo Measure] - Documentazione del prodotto
title: Metodi di gestione delle spese
exl-id: 36478d8d-986c-4d4f-8854-3287d6c57a9d
source-git-commit: 54337a0a65b79d80ebeae6531f5e92f4f48721a7
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Metodi di gestione delle spese {#spend-management-methods}

I dati di spesa sono fondamentali per il successo del reporting sul ROI con [!DNL Marketo Measure]. Per ottenere un reporting accurato e completo sul ROI su tutti i canali e i sottocanali, è necessario assicurarsi di disporre dei dati di spesa appropriati [!DNL Marketo Measure].

Ci sono tre modi per spenderli in [!DNL Marketo Measure]. Ogni metodo è progettato per estrarre i dati da particolari input di dati.

**1) Account collegati API**

Qualsiasi account annuncio a cui ti sei connesso [!DNL Marketo Measure] tramite un’API la spesa viene automaticamente inserita in [!DNL Marketo Measure] per la generazione di rapporti sul ROI. Per verificare quali account si sono connessi e quindi tirare in spesa, vai al [!DNL Marketo Measure] L&#39;app e seleziona la [!UICONTROL Connections] sotto la scheda [!UICONTROL Integrations] sezione . Per maggiori dettagli su come impostare le connessioni API, consulta la nostra [Piattaforme integrate di annunci](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms) articolo.

**2) Sincronizzazione dei costi della campagna CRM**

Ogni [!DNL Marketo Measure] ha accesso a una funzione denominata [Sincronizza i costi della campagna CRM](/help/marketing-spend/spend-management/crm-campaign-costs.md#availability). Per impostazione predefinita, questo bit di funzione è impostato su &quot;No&quot; ma può essere attivato in qualsiasi momento.

![](assets/spend-management-methods-1.png)

Una volta abilitata questa funzione, estrarrà automaticamente la spesa da qualsiasi campagna/programma CRM che soddisfi i seguenti criteri

i. [!DNL Marketo Measure] cerca innanzitutto se Campaign/Program sta creando punti di contatto, da una corrispondenza [Regola di sincronizzazione della campagna](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md) creato o corrispondente [Regola di sincronizzazione del programma](/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md) creato, oppure [Abilita valore punti di contatto acquirenti](/help/channel-tracking-and-setup/offline-channels/syncing-offline-campaigns.md#how-to-create-a-campaign-and-sync-buyer-touchpoints) è &quot;Includi tutti i membri della campagna&quot; o &quot;Includi i membri della campagna &quot;rispondi&quot;.&quot;

ii) Una data di inizio deve essere compilata nella campagna o nel programma

iii) È inoltre necessario compilare una data di fine per la campagna o il programma

IV. Infine, è necessario specificare un costo effettivo (per le campagne in SFDC) o il costo del periodo (per i programmi in Marketo).

**3) Caricamento manuale dei costi**

Questo metodo consente di: [caricare manualmente i dati di spesa](/help/marketing-spend/spend-management/marketing-channel-costs.md#uploading-marketing-costs) per i canali e i sottocanali che non sono coperti da account connessi API o dalla sincronizzazione dei costi della campagna di gestione delle relazioni con i clienti. Passando alla sezione Marketing Spend (Spesa di marketing) nel vostro [!DNL Marketo Measure] puoi caricare i dati di spesa tramite un file CSV per uno qualsiasi dei tuoi canali.

I clienti possono utilizzare una combinazione di tutti e tre questi metodi per gestire la spesa e dipenderanno dalla configurazione specifica della [!DNL Marketo Measure]. Perché esistono tre metodi per importare le spese in [!DNL Marketo Measure], consigliamo vivamente di utilizzare la bacheca di spesa per il marketing disponibile in Discover per ottenere una visione completa di tutti i dati di spesa. Questa bacheca è l&#39;unico luogo in cui potrete vedere tutti i vostri canali e le relative spese. La bacheca delle spese di marketing può aiutarti a identificare rapidamente dove potrebbero esserci lacune nei dati di spesa e come migliorare il reporting sul ROI.
