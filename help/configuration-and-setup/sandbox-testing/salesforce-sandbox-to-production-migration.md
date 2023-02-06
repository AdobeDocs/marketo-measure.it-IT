---
unique-page-id: 18874694
description: Migrazione da Salesforce Sandbox alla produzione - [!DNL Marketo Measure] - Documentazione del prodotto
title: Migrazione da Salesforce Sandbox alla produzione
exl-id: b2b71c4a-f192-43ce-a27e-cbd0ec3cf008
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# Migrazione da Salesforce Sandbox alla produzione {#salesforce-sandbox-to-production-migration}

Se hai scelto di eseguire il test [!DNL Marketo Measure] in [!DNL Salesforce] Ambiente sandbox, segui queste istruzioni per effettuare la migrazione a Produzione una volta pronto. Le seguenti istruzioni presuppongono che tu abbia già scaricato il [!DNL Marketo Measure] crea un pacchetto nell’organizzazione Sandbox, esegue i test necessari e è pronto per il push [!DNL Marketo Measure] alla produzione.

## Passaggio 1: Installa [!DNL Marketo Measure] Pacchetti nella produzione [!DNL Salesforce] Istanza {#install-marketo-measure-packages-into-your-production-salesforce-instance}

* Installa i due [!DNL Marketo Measure] pacchetti in produzione con &quot;[!UICONTROL All Users]&quot; impostazione

   * [Pacchetto di base](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"}
   * [Pacchetto di estensione del dashboard](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t610000001jI6){target="_blank"}

* Per ulteriori informazioni sulla [!DNL Marketo Measure] rapporto con [!DNL Salesforce], dai un&#39;occhiata [articolo](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md)
* Un po&#39; [!DNL Salesforce] la configurazione è necessaria. I punti specifici dell&#39;azione sono descritti di seguito in [Passaggio 4:](#salesforce-configuration)

## Passaggio 2: Elimina la connessione CRM Sandbox corrente in [!DNL Marketo Measure] App {#delete-the-current-sandbox-crm-connection-in-marketo-measure-app}

* Accedi a [!DNL Marketo Measure] all&#39;indirizzo experience.adobe.com/marketo-measure
* Passa a Il mio account >[!UICONTROL Settings] >[!UICONTROL Connections]
* Fai clic sull’icona del cestino accanto alla connessione SFDC da eliminare
* Verrà richiesto di confermare l&#39;eliminazione. Assicurati di leggere attentamente il prompt e capire le conseguenze della cancellazione

   ![](assets/salesforce-sandbox-to-production-migration-1.png)

   * Digitare il nome dell&#39;azienda come richiesto nel modello di conferma e fare clic su &quot;Comprendo le conseguenze, elimina questa connessione&quot;
* Questo attiverà il processo di eliminazione e ci vorrà del tempo per terminare

## Passaggio 3: Connetti l’istanza di gestione delle relazioni con i clienti di Produzione in [!DNL Marketo Measure] App {#connect-the-production-crm-instance-in-marketo-measure-app}

* Accedi a [!DNL Marketo Measure] all&#39;indirizzo experience.adobe.com/marketo-measure
* Passa a [!UICONTROL My Account] >[!UICONTROL Settings] > [!UICONTROL Connections]
* Una volta che l’eliminazione della connessione Sandbox è stata completata correttamente, la connessione scomparirà dalla pagina, altrimenti la connessione sarà ancora presente con lo stato &quot;Eliminazione in corso&quot;
* Clic &quot;[!UICONTROL Set up New CRM connection]&quot;
* In &quot;[!UICONTROL Select CRM Connection]&quot; finestra di dialogo modale, fai clic su &quot;[!UICONTROL Connect]&quot; Azione accanto al [!DNL Salesforce] Piattaforma, seleziona la &quot;[!UICONTROL Production]&quot; opzione
* Ti verrà richiesto di specificare le tue credenziali, assicurati di inserire i dettagli di accesso alla produzione

## Passaggio 4: Configurazione Salesforce {#salesforce-configuration}

[Layout di pagina](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md)

[Set di autorizzazioni](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)

[Condivisione di rapporti](https://help.salesforce.com/articleView?id=analytics_share_folder.htm&amp;type=0){target="_blank"}

[Nascondere tipi di report non necessari](/help/configuration-and-setup/marketo-measure-and-salesforce/hiding-unnecessary-report-types.md)

[Flusso di lavoro personalizzato, se applicabile](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
