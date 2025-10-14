---
unique-page-id: 18874694
description: Migrazione da Sandbox Salesforce a Produzione - [!DNL Marketo Measure]
title: Migrazione dalla sandbox Salesforce alla produzione
exl-id: b2b71c4a-f192-43ce-a27e-cbd0ec3cf008
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Migrazione dalla sandbox Salesforce alla produzione {#salesforce-sandbox-to-production-migration}

Se hai scelto di testare [!DNL Marketo Measure] in un ambiente Sandbox [!DNL Salesforce], segui queste istruzioni per migrare alla produzione quando sei pronto. Le istruzioni seguenti presuppongono che tu abbia già scaricato il pacchetto [!DNL Marketo Measure] nell&#39;organizzazione sandbox, che tu abbia eseguito i test necessari e che tu sia pronto a inviare [!DNL Marketo Measure] in produzione.

## Passaggio 1: installare il pacchetto [!DNL Marketo Measure] nell&#39;istanza di produzione [!DNL Salesforce]

* Installa il pacchetto [!DNL Marketo Measure] in produzione con l&#39;impostazione &quot;[!UICONTROL All Users]&quot;

   * [Pacchetto base](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"}

* Per ulteriori informazioni sulla relazione [!DNL Marketo Measure] con [!DNL Salesforce], vedere [questo articolo](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md)
* È necessaria una configurazione di [!DNL Salesforce]. Gli elementi dell&#39;azione specifica sono descritti di seguito nel [passaggio 4 seguente](#salesforce-configuration)

## Passaggio 2: eliminare la connessione al sistema CRM sandbox corrente nell&#39;app [!DNL Marketo Measure] {#delete-the-current-sandbox-crm-connection-in-marketo-measure-app}

* Accedere all&#39;applicazione [!DNL Marketo Measure] all&#39;indirizzo experience.adobe.com/marketo-measure
* Passa a Il mio account >[!UICONTROL Settings] >[!UICONTROL Connections]
* Fai clic sull’icona del cestino accanto alla connessione SFDC per eliminarlo
* Viene richiesto di confermare l&#39;eliminazione. Assicurati di leggere attentamente il prompt e comprendere le conseguenze dell’eliminazione

  ![](assets/salesforce-sandbox-to-production-migration-1.png)

   * Digita il nome dell’azienda come richiesto nel modello di conferma e fai clic su &quot;Comprendo le conseguenze, elimina questa connessione&quot;
* Questo attiva il processo di eliminazione e richiederà del tempo

## Passaggio 3: connettere l&#39;istanza di CRM di produzione nell&#39;app [!DNL Marketo Measure] {#connect-the-production-crm-instance-in-marketo-measure-app}

* Accedere all&#39;applicazione [!DNL Marketo Measure] all&#39;indirizzo experience.adobe.com/marketo-measure
* Passa a [!UICONTROL My Account] >[!UICONTROL Settings] > [!UICONTROL Connections]
* Una volta eliminata correttamente la connessione Sandbox, questa scompare dalla pagina; in caso contrario la connessione sarà ancora presente con lo stato &quot;Eliminazione in corso&quot;
* Fai clic su &quot;[!UICONTROL Set up New CRM connection]&quot;
* Nella finestra di dialogo modale &quot;[!UICONTROL Select CRM Connection]&quot;, fai clic sull&#39;azione &quot;[!UICONTROL Connect]&quot; accanto alla piattaforma [!DNL Salesforce], seleziona l&#39;opzione &quot;[!UICONTROL Production]&quot;
* Ti vengono richieste le credenziali, assicurati di inserire i dettagli di accesso alla produzione

## Passaggio 4: configurazione Salesforce {#salesforce-configuration}

[Layout di pagina](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md)

[Set di autorizzazioni](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)

[Condivisione di report](https://help.salesforce.com/s/articleView?language=en_US&id=analytics_share_folder.htm&type=0){target="_blank"}

[Nascondere i tipi di report non necessari](/help/configuration-and-setup/marketo-measure-and-salesforce/hiding-unnecessary-report-types.md)

[Flusso di lavoro personalizzato, se applicabile](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
