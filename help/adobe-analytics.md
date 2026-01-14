---
description: Integrazioni [!DNL Marketo Measure] con Adobe Analytics - [!DNL Marketo Measure]
title: Integrazioni [!DNL Marketo Measure] con [!DNL Adobe Analytics]
exl-id: 3a125a15-eb74-454a-afb3-75746a1dfac6
feature: Integration
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 0%

---


# Integrazioni [!DNL Marketo Measure] con Adobe Analytics {#marketo-measure-integrations-with-adobe-analytics}

L&#39;integrazione degli attributi del cliente B2B consente agli utenti reciproci di [!DNL Marketo Measure] e Adobe Analytics di arricchire i profili utente [!DNL Adobe Analytics] con metadati preziosi derivati dal motore di attribuzione [!DNL Marketo Measure] e tramite la funzionalità di sincronizzazione con CRM ([!DNL Microsoft Dynamics] e [!DNL Salesforce]). È disponibile gratuitamente per tutti i clienti che utilizzano [!DNL Adobe Analytics] e [!DNL Marketo Measure].

>[!PREREQUISITES]
>È necessario disporre di sottoscrizioni attive sia a [!DNL Marketo Measure] che a [!DNL Adobe Analytics].

## Configurazione dell’integrazione {#configuring-the-integration}

1. Crea un nuovo Customer Attributes Data Source nella console Experience Cloud. Le istruzioni dettagliate [sono disponibili qui](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/t-crs-usecase.html?lang=it).

   Prendi nota delle seguenti informazioni, necessarie nei passaggi successivi:

   * L’ID alias, che può essere qualsiasi valore vuoi che sia. Consigliamo &quot;marketomeasure_id&quot;

   * Nome host e credenziali del server FTP (nome utente e password)

1. Una volta creato il Customer Attributes Data Source, continuare il processo di configurazione passando alla schermata **[!UICONTROL Integrations]** > **[!UICONTROL Connections]** nel menu di amministrazione di [!DNL Marketo Measure].

1. Fare clic sul pulsante **[!UICONTROL Set Up New Customer Attributes Connection]** e seguire le istruzioni per configurare l&#39;integrazione Attributi cliente. L’interfaccia utente richiede le informazioni sull’ID alias e sulla connessione FTP acquisite durante la creazione del Source Attributi del cliente nella console dei servizi core. Selezionare il set di attributi dell&#39;account da sincronizzare con l&#39;account [!DNL Adobe Analytics].

   Immetti l’ID della tua organizzazione Adobe IMS. Questo ID viene visualizzato nell’angolo inferiore destro dell’Admin Console di Adobe Experience Cloud. Per maggiori informazioni su come trovare questo ID, rivolgiti al team dell’account di Adobe (il tuo Account Manager).

1. Dopo aver completato la creazione della connessione nell&#39;account [!DNL Marketo Measure], devi tornare alla console Experience Cloud per [convalidare lo schema](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/validate-schema.html?lang=it). Non è necessario preoccuparsi del caricamento del file FTP, [!DNL Marketo Measure] ha automatizzato la parte. Passare alla schermata &quot;Visualizza/Modifica&quot; schema per l&#39;attributo cliente Source creato nel passaggio 1 e indicare ad Adobe i tipi di dati per ciascuno degli attributi caricati da [!DNL Marketo Measure] per tuo conto. Se necessario, puoi anche creare nuovi nomi descrittivi per gli attributi caricati.

   Se si è scelto di sincronizzare gli attributi dall&#39;oggetto account CRM, si consiglia di scegliere nuovi nomi visualizzati, in quanto [!DNL Marketo Measure] popola solo i nomi a livello API per questi attributi, che in genere non sono descrittivi dei rapporti.

1. L’ultimo passaggio consiste nel configurare le sottoscrizioni di attributi per le applicazioni Experience Cloud in cui desideri utilizzare gli attributi. È possibile configurare le sottoscrizioni per [!DNL Adobe Analytics] o [!DNL Adobe Target].  Ulteriori informazioni su come eseguire questa operazione [&#x200B; sono disponibili qui](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/subscription.html?lang=it).

## Descrizioni attributi {#attribute-descriptions}

Quando si crea una connessione attributo cliente B2B, [!DNL Marketo Measure] crea automaticamente un set standard di attributi cliente B2B. Questi attributi sono descritti nella tabella seguente.

Oltre a quelli elencati di seguito, puoi anche caricare qualsiasi attributo associato all’oggetto account nel CRM. Se più account sono associati all&#39;utente specificato, [!DNL Marketo Measure] compila tutti i valori degli attributi dell&#39;account corrispondenti in un elenco delimitato da punti e virgola.

<table>
 <colgroup>
  <col>
  <col>
 </colgroup>
 <tbody>
  <tr>
   <td><b>Nome attributo</b></td>
   <td><b>Descrizione</b></td>
  </tr>
  <tr>
   <td>Account.Name</td>
   <td>I nomi account associati al visitatore Web specificato. Se più account sono associati all'utente specificato, [!DNL Marketo Measure] compila tutti i nomi di account corrispondenti in un elenco delimitato da punti e virgola.<br/>
   <strong>Nota:</strong> account.name è il nome a livello di API Salesforce per l'attributo name nell'oggetto account. Puoi scegliere un nome visualizzato migliore (ad esempio, "Company") per questo attributo durante il passaggio di convalida dello schema della configurazione dell’integrazione (passaggio 4).</td>
  </tr>
  <tr>
   <td>Ricavi attribuiti - ‹MODEL›</td>
   <td>I ricavi attribuiti a questo cliente in virtù della sua associazione con opportunità acquisite nel tuo sistema CRM, come calcolato dal motore di attribuzione [!DNL Marketo Measure].<br/>
   Per ogni modello di attribuzione consentito dalle sottoscrizioni di [!DNL Marketo Measure] è disponibile uno di questi attributi (ad esempio, "Ricavi attribuiti - Percorso completo").</td>
  </tr>
  <tr>
   <td>Fase Funnel più profonda</td>
   <td>La fase funnel più profonda di qualsiasi opportunità aperta associata all’utente specificato.</td>
  </tr>
  <tr>
   <td>Opportunità aperte</td>
   <td>Un elenco delimitato da punti e virgola degli ID opportunità a cui l’utente è legato in base ai dati CRM.</td>
  </tr>
 </tbody>
</table>

**Nota sui limiti degli attributi**

Gli attributi visualizzati tramite questa integrazione vengono conteggiati rispetto ai limiti degli attributi contrattuali in [!DNL Adobe Analytics] e [!DNL Adobe Target]. Solo gli attributi visualizzati tramite una sottoscrizione di attributi (passaggio 5 in [Configurazione dell&#39;integrazione](#configuring-the-integration)) vengono conteggiati rispetto al limite per l&#39;applicazione sottoscritta.

## Domande frequenti {#faqs}

**Come si modifica il set di attributi che si desidera condividere tramite questa integrazione?**

Affinché un attributo condiviso da [!DNL Marketo Measure] con l&#39;organizzazione Adobe IMS tramite questa integrazione sia visibile e utilizzato in [!DNL Adobe Analytics], è necessario che venga visualizzato tramite un Abbonamento di attributi configurato nella console dei servizi core. Pertanto, se si desidera rimuovere un attributo in modo che non venga più visualizzato in [!DNL Adobe Analytics], è possibile eliminarlo semplicemente eliminando la sottoscrizione dell&#39;attributo.

È inoltre possibile eliminare la connessione dell&#39;attributo cliente B2B in [!DNL Marketo Measure] e ricrearla con l&#39;attributo che non si desidera più condividere escluso dalla configurazione della connessione. Allo stesso modo, per aggiungere attributi all’integrazione, devi eliminare la connessione esistente e crearne una nuova con gli attributi desiderati aggiunti alla configurazione.

Alla luce di quanto sopra, si consiglia vivamente di selezionare gli attributi il più inclusivi possibile durante la configurazione della connessione degli attributi per la prima volta.

**Quali sono alcuni casi d&#39;uso di esempio per questa integrazione?**

1. Metriche del traffico basate sull’account: utilizzando l’attributo nome account, puoi creare segmenti di uno o più account di destinazione in Adobe Analytics e analizzare le metriche del traffico del sito solo per il sottoinsieme del traffico proveniente dagli account di destinazione.
1. Content Analytics: utilizza la metrica dei ricavi per analizzare il contenuto del sito più coinvolgente per i clienti che alla fine acquistano il tuo prodotto o servizio, o per coloro che raggiungono uno specifico stadio di interesse funnel.
1. Supporto live-deal: dota il team di vendita di insight actionable analizzando il comportamento del sito per gli utenti associati a una specifica opportunità aperta nel CRM.
