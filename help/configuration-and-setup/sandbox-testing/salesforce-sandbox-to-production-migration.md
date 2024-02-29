---
unique-page-id: 18874694
description: Migrazione dalla sandbox Salesforce alla produzione - [!DNL Marketo Measure]
title: Migrazione dalla sandbox Salesforce alla produzione
exl-id: b2b71c4a-f192-43ce-a27e-cbd0ec3cf008
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Migrazione dalla sandbox Salesforce alla produzione {#salesforce-sandbox-to-production-migration}

Se hai scelto di testare [!DNL Marketo Measure] in un [!DNL Salesforce] Ambiente sandbox, segui queste istruzioni per migrare alla produzione quando sei pronto. Le istruzioni seguenti presuppongono che tu abbia già scaricato [!DNL Marketo Measure] nell’organizzazione Sandbox, ha eseguito i test necessari e è pronto per eseguire il push [!DNL Marketo Measure] alla produzione.

## Passaggio 1: installare [!DNL Marketo Measure] Pacchetto nella tua produzione [!DNL Salesforce] Istanza

* Installare [!DNL Marketo Measure] in produzione con il software &quot;[!UICONTROL All Users]&quot; impostazione

   * [Pacchetto base](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"}

* Per ulteriori informazioni su [!DNL Marketo Measure] relazione con [!DNL Salesforce], guarda [questo articolo](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md)
* Un po&#39; di [!DNL Salesforce] è necessaria la configurazione. Le azioni specifiche sono descritte di seguito in [Passaggio 4 sotto](#salesforce-configuration)

## Passaggio 2: eliminare la connessione alla gestione delle relazioni con i clienti sandbox corrente in [!DNL Marketo Measure] App {#delete-the-current-sandbox-crm-connection-in-marketo-measure-app}

* Accedi a [!DNL Marketo Measure] applicazione all&#39;indirizzo experience.adobe.com/marketo-measure
* Passa a Il mio account >[!UICONTROL Settings] >[!UICONTROL Connections]
* Fai clic sull’icona del cestino accanto alla connessione SFDC per eliminarlo
* Viene richiesto di confermare l&#39;eliminazione. Assicurati di leggere attentamente il prompt e comprendere le conseguenze dell’eliminazione

  ![](assets/salesforce-sandbox-to-production-migration-1.png)

   * Digita il nome dell’azienda come richiesto nel modello di conferma e fai clic su &quot;Comprendo le conseguenze, elimina questa connessione&quot;
* Questo attiva il processo di eliminazione e richiederà del tempo

## Passaggio 3: connettere l’istanza CRM di produzione in [!DNL Marketo Measure] App {#connect-the-production-crm-instance-in-marketo-measure-app}

* Accedi a [!DNL Marketo Measure] applicazione all&#39;indirizzo experience.adobe.com/marketo-measure
* Accedi a [!UICONTROL My Account] >[!UICONTROL Settings] > [!UICONTROL Connections]
* Una volta eliminata correttamente la connessione Sandbox, questa scompare dalla pagina; in caso contrario la connessione sarà ancora presente con lo stato &quot;Eliminazione in corso&quot;
* Fai clic su &quot;[!UICONTROL Set up New CRM connection]&quot;
* Nella sezione &quot;[!UICONTROL Select CRM Connection]&quot; finestra di dialogo modale, fai clic su &quot;[!UICONTROL Connect]&quot; Azione accanto al [!DNL Salesforce] Platform, seleziona la &quot;[!UICONTROL Production]Opzione &quot;
* Ti vengono richieste le credenziali, assicurati di inserire i dettagli di accesso alla produzione

## Passaggio 4: configurazione Salesforce {#salesforce-configuration}

[Layout di pagina](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md)

[Set di autorizzazioni](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)

[Condivisione dei rapporti](https://help.salesforce.com/s/articleView?language=en_US&amp;id=analytics_share_folder.htm&amp;type=0){target="_blank"}

[Nascondere i tipi di report non necessari](/help/configuration-and-setup/marketo-measure-and-salesforce/hiding-unnecessary-report-types.md)

[Flusso di lavoro personalizzato, se applicabile](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
