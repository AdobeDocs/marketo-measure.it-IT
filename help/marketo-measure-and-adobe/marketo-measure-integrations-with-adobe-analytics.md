---
description: "[!DNL Marketo Measure] Integrazioni con Adobe Analytics - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] Integrazioni con [!DNL Adobe Analytics]"
exl-id: 3a125a15-eb74-454a-afb3-75746a1dfac6
source-git-commit: 54337a0a65b79d80ebeae6531f5e92f4f48721a7
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 0%

---

# [!DNL Marketo Measure] Integrazioni con Adobe Analytics {#marketo-measure-integrations-with-adobe-analytics}

L’integrazione degli attributi del cliente B2B consente agli utenti reciproci di [!DNL Marketo Measure] e Adobe Analytics per arricchire i loro [!DNL Adobe Analytics] profili utente con metadati preziosi derivati da [!DNL Marketo Measure] motore di attribuzione e tramite la sua funzionalità di sincronizzazione con CRM ([!DNL Microsoft Dynamics] e [!DNL Salesforce]). È disponibile gratuitamente per tutti i clienti che utilizzano [!DNL Adobe Analytics] e [!DNL Marketo Measure].

>[!PREREQUISITES]
>
>È necessario disporre di abbonamenti attivi a entrambi [!DNL Marketo Measure] e [!DNL Adobe Analytics].

## Configurazione dell’integrazione {#configuring-the-integration}

1. Inizia creando una nuova origine dati Attributi del cliente nella console Experience Cloud. Istruzioni dettagliate [si trova qui](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/t-crs-usecase.html).

   Prendi nota delle seguenti informazioni, in quanto ne avrai bisogno per alcuni dei passaggi successivi del processo:

   * ID alias, che può essere qualsiasi valore desiderato. Consigliamo &quot;marketomeasure_id&quot;

   * Nome host e credenziali del server FTP (nome utente e password)

1. Una volta creata l&#39;origine dati Attributi del cliente, continua il processo di configurazione passando alla **[!UICONTROL Integrations]** > **[!UICONTROL Connections]** nella schermata [!DNL Marketo Measure] menu di amministrazione.

1. Fai clic sul pulsante **[!UICONTROL Set Up New Customer Attributes Connection]** e segui le istruzioni per configurare l&#39;integrazione Attributi del cliente. Nell’interfaccia utente vengono richieste le informazioni relative all’ID alias e alla connessione FTP acquisite durante la creazione dell’origine degli attributi del cliente nella console Servizi di base, nonché il set di attributi dell’account che si desidera sincronizzare con la [!DNL Adobe Analytics] conto.

   Devi anche inserire il tuo ID organizzazione Adobe IMS. Questo ID viene visualizzato nell&#39;angolo in basso a destra del tuo Admin Console Adobe Experience Cloud. Per ulteriori informazioni su come trovare questo ID, consulta il tuo Customer Success Manager.

1. Una volta completata la creazione della connessione nel [!DNL Marketo Measure] account, dovrai tornare alla console Experience Cloud per [convalida dello schema](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/validate-schema.html). Non devi preoccuparti del caricamento del file FTP, [!DNL Marketo Measure] ha automatizzato quella parte per te. Tutto quello che devi fare è andare alla schermata dello schema &quot;Visualizza/Modifica&quot; per l&#39;origine dell&#39;attributo del cliente creata nel passaggio 1 e dire ad Adobe quali sono i tipi di dati per ciascuno degli attributi che [!DNL Marketo Measure] è stato caricato per tuo conto. Puoi anche creare nuovi nomi descrittivi della visualizzazione per gli attributi caricati, se necessario.

   Se hai scelto di sincronizzare gli attributi dall&#39;oggetto account CRM, ti consigliamo vivamente di scegliere nuovi nomi visualizzati per essi, come [!DNL Marketo Measure] compilerà solo i nomi a livello di API per questi attributi, che in genere non sono compatibili con i rapporti.

1. L&#39;ultimo passaggio consiste nel configurare le sottoscrizioni di attributi per le applicazioni di Experience Cloud in cui si desidera utilizzare gli attributi.  Puoi configurare le sottoscrizioni per [!DNL Adobe Analytics] o [!DNL Adobe Target].  Ulteriori informazioni su come farlo [si trova qui](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/subscription.html).

## Descrizioni degli attributi {#attribute-descriptions}

Quando si crea una nuova connessione attributo cliente B2B, [!DNL Marketo Measure] creerà automaticamente un set standard di attributi cliente B2B per te. Questi attributi sono descritti nella tabella seguente.

Oltre a quelli elencati di seguito, puoi caricare anche qualsiasi attributo associato all&#39;oggetto account nel tuo CRM. Se più account sono legati a un determinato utente, [!DNL Marketo Measure] compilerà tutti i valori degli attributi di conto corrispondenti in un elenco delimitato da punti e virgola.

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
   <td>I nomi account associati al visitatore Web specificato. Se più account sono legati a un determinato utente, [!DNL Marketo Measure] compilerà tutti i nomi di account corrispondenti in un elenco delimitato da punto e virgola.<br/>
   <strong>Nota:</strong> account.name è il nome a livello di API Salesforce per l'attributo name sull'oggetto account. È possibile scegliere un nome visualizzato migliore (ad esempio, "Società") per questo attributo durante il passaggio Convalida schema della configurazione di integrazione (passaggio 4).</td>
  </tr>
  <tr> 
   <td>Entrate Attribuite - NUMERO MODEL›</td> 
   <td>I ricavi attribuiti a questo cliente in virtù della loro associazione con opportunità chiuse nel tuo CRM, come calcolato dal [!DNL Marketo Measure] motore di attribuzione.<br/>
   Sarà presente uno di questi attributi per ogni modello di attribuzione che il tuo [!DNL Marketo Measure] gli abbonamenti consentono (ad esempio, "Entrate attribuite - Percorso completo").</td>
  </tr>
  <tr> 
   <td>Stage funnel più profondo</td> 
   <td>La fase funnel più profonda di qualsiasi opportunità aperta associata all'utente specificato.</td>
  </tr>
  <tr> 
   <td>Opportunità aperte</td> 
   <td>Elenco degli ID opportunità a cui è associato l'utente in base ai dati CRM.</td>
  </tr> 
 </tbody> 
</table>

**Una nota sui limiti degli attributi**

Tieni presente che gli attributi generati tramite questa integrazione continueranno a essere conteggiati rispetto ai limiti degli attributi contrattuali in [!DNL Adobe Analytics] e [!DNL Adobe Target]. Solo gli attributi visualizzati tramite una sottoscrizione attributo (passaggio 5 in [Configurazione dell’integrazione](#configuring-the-integration)) verrà conteggiato in base al limite per l’applicazione sottoscritta.

## Domande frequenti {#faqs}

**Come posso modificare il set di attributi che voglio condividere tramite questa integrazione?**

Per un attributo condiviso da [!DNL Marketo Measure] nell’organizzazione Adobe IMS tramite questa integrazione per essere visibile e utilizzato in [!DNL Adobe Analytics], deve essere visualizzata tramite una sottoscrizione attributo configurata nella console Servizi di base. Pertanto, se desideri rimuovere un attributo in modo che non venga più visualizzato in [!DNL Adobe Analytics], è possibile ottenere questo risultato semplicemente eliminando la sottoscrizione dell’attributo.

È inoltre possibile eliminare la connessione dell&#39;attributo cliente B2B in [!DNL Marketo Measure] e ricrealo con l’attributo che non desideri più condividere escluso dalla configurazione della connessione. Allo stesso modo, per aggiungere attributi all&#39;integrazione, dovrai eliminare la connessione esistente e crearne una nuova con gli attributi desiderati aggiunti alla configurazione.

Alla luce di quanto precede, si consiglia vivamente di impostare per la prima volta la connessione attributo nel modo più inclusivo possibile durante la selezione degli attributi.

**Quali sono alcuni esempi di casi d’uso per questa integrazione?**

1. Metriche del traffico basate su account: Utilizzando l’attributo nome account, puoi creare segmenti di uno o più account di destinazione in Adobe Analytics e analizzare le metriche del traffico del sito solo per il sottoinsieme di traffico proveniente dagli account di destinazione.
1. Analisi dei contenuti: Utilizza la metrica Ricavo per analizzare il contenuto del sito più coinvolgente per i clienti che acquistano in ultima analisi il tuo prodotto o servizio, o per quelli che raggiungono uno specifico stadio di interesse funnel.
1. Supporto live: Arma il tuo team di vendita con informazioni fruibili analizzando il comportamento del sito per gli utenti associati a una specifica opportunità aperta nel tuo CRM.
