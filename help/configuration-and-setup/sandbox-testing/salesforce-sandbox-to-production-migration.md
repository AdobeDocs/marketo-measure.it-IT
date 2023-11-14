---
unique-page-id: 18874694
description: Migrazione dalla sandbox Salesforce alla produzione - [!DNL Marketo Measure] - Documentazione del prodotto
title: Migrazione dalla sandbox Salesforce alla produzione
exl-id: b2b71c4a-f192-43ce-a27e-cbd0ec3cf008
feature: Salesforce
source-git-commit: 86d610d07ab699266ba68a6f2eaf7c7981e62019
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Migrazione dalla sandbox Salesforce alla produzione {#salesforce-sandbox-to-production-migration}

Se hai scelto di testare [!DNL Marketo Measure] in un [!DNL Salesforce] Ambiente sandbox, segui queste istruzioni per migrare alla produzione quando sei pronto. Le istruzioni seguenti presuppongono che tu abbia già scaricato [!DNL Marketo Measure] nell’organizzazione Sandbox, ha eseguito i test necessari e è pronto per eseguire il push [!DNL Marketo Measure] alla produzione.

## Passaggio 1: installare [!DNL Marketo Measure] Pacchetti nella tua produzione [!DNL Salesforce] Istanza {#install-marketo-measure-packages-into-your-production-salesforce-instance}

* Installare i due [!DNL Marketo Measure] pacchetti in Produzione con &quot;[!UICONTROL All Users]&quot; impostazione

   * [Pacchetto base](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"}

* Per ulteriori informazioni su [!DNL Marketo Measure] relazione con [!DNL Salesforce], dai un&#39;occhiata [questo articolo](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md)
* Un po&#39; di [!DNL Salesforce] è necessaria la configurazione. Le azioni specifiche sono descritte di seguito in [Passaggio 4 sotto](#salesforce-configuration)

## Passaggio 2: eliminare la connessione alla gestione delle relazioni con i clienti sandbox corrente in [!DNL Marketo Measure] App {#delete-the-current-sandbox-crm-connection-in-marketo-measure-app}

* Accedi a [!DNL Marketo Measure] applicazione all&#39;indirizzo experience.adobe.com/marketo-measure
* Passa a Il mio account >[!UICONTROL Settings] >[!UICONTROL Connections]
* Fai clic sull’icona del cestino accanto alla connessione SFDC per eliminarlo
* Ti verrà chiesto di confermare l’eliminazione. Si assicuri di leggere attentamente il prompt e di comprendere le conseguenze della cancellazione

  ![](assets/salesforce-sandbox-to-production-migration-1.png)

   * Digita il nome dell’azienda come richiesto nel modello di conferma e fai clic su &quot;Comprendo le conseguenze, elimina questa connessione&quot;
* Il processo di eliminazione verrà attivato e il completamento richiederà del tempo

## Passaggio 3: connettere l’istanza CRM di produzione in [!DNL Marketo Measure] App {#connect-the-production-crm-instance-in-marketo-measure-app}

* Accedi a [!DNL Marketo Measure] applicazione all&#39;indirizzo experience.adobe.com/marketo-measure
* Accedi a [!UICONTROL My Account] >[!UICONTROL Settings] > [!UICONTROL Connections]
* Una volta eliminata correttamente la connessione Sandbox, questa scompare dalla pagina; in caso contrario la connessione rimane presente e lo stato è &quot;Eliminazione in corso&quot;
* Clic &quot;[!UICONTROL Set up New CRM connection]&quot;
* Nella sezione &quot;[!UICONTROL Select CRM Connection]&quot; finestra di dialogo modale, fai clic su &quot;[!UICONTROL Connect]&quot; Azione accanto al [!DNL Salesforce] Platform, seleziona la &quot;[!UICONTROL Production]Opzione &quot;
* Ti verranno richieste le credenziali, assicurati di inserire i dettagli di accesso alla produzione

## Passaggio 4: configurazione Salesforce {#salesforce-configuration}

[Layout di pagina](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md)

[Set di autorizzazioni](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)

[Condivisione dei rapporti](https://help.salesforce.com/articleView?id=analytics_share_folder.htm&amp;type=0){target="_blank"}

[Nascondere i tipi di report non necessari](/help/configuration-and-setup/marketo-measure-and-salesforce/hiding-unnecessary-report-types.md)

[Flusso di lavoro personalizzato, se applicabile](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
