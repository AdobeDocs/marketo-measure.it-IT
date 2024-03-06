---
description: "[!DNL Marketo Measure] Integrazioni con Adobe Analytics - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Integrazioni con [!DNL Adobe Analytics]"
exl-id: 3a125a15-eb74-454a-afb3-75746a1dfac6
feature: Integration
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 0%

---

# [!DNL Marketo Measure] Integrazioni con Adobe Analytics {#marketo-measure-integrations-with-adobe-analytics}

L’integrazione degli attributi del cliente B2B consente agli utenti di [!DNL Marketo Measure] e Adobe Analytics per arricchire i [!DNL Adobe Analytics] profili utente con metadati preziosi derivati dal [!DNL Marketo Measure] motore di attribuzione e tramite la sua funzionalità di sincronizzazione con i sistemi CRM ([!DNL Microsoft Dynamics] e [!DNL Salesforce]). È disponibile gratuitamente per tutti i clienti che utilizzano [!DNL Adobe Analytics] e [!DNL Marketo Measure].

>[!PREREQUISITES]
>
>Devi disporre di abbonamenti attivi a entrambi [!DNL Marketo Measure] e [!DNL Adobe Analytics].

## Configurazione dell’integrazione {#configuring-the-integration}

1. Crea una nuova origine dati per gli attributi del cliente nella console di Experienci Cloud. Istruzioni dettagliate [si trova qui](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/t-crs-usecase.html).

   Prendi nota delle seguenti informazioni, necessarie nei passaggi successivi:

   * L’ID alias, che può essere qualsiasi valore vuoi che sia. Consigliamo &quot;marketomeasure_id&quot;

   * Nome host e credenziali del server FTP (nome utente e password)

1. Una volta creata l’origine dati degli attributi del cliente, continua il processo di configurazione passando al **[!UICONTROL Integrations]** > **[!UICONTROL Connections]** schermata in [!DNL Marketo Measure] menu di amministrazione.

1. Fai clic su **[!UICONTROL Set Up New Customer Attributes Connection]** e seguire le istruzioni per configurare l’integrazione Attributi del cliente. L’interfaccia utente richiede di specificare l’ID alias e le informazioni di connessione FTP acquisiti durante la creazione dell’origine attributi del cliente nella console dei servizi core. Seleziona il set di attributi dell’account da sincronizzare con [!DNL Adobe Analytics] account.

   Immetti l’ID della tua organizzazione Adobe IMS. Questo ID viene visualizzato nell’angolo inferiore destro dell’Admin Console di Adobe Experience Cloud. Per maggiori informazioni su come trovare questo ID, rivolgiti al team dell’account Adobe (il tuo Account Manager).

1. Dopo aver completato la creazione della connessione nel [!DNL Marketo Measure] account, devi tornare alla console Experience Cloud per [convalidare lo schema](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/validate-schema.html?lang=en). Non devi preoccuparti del caricamento del file FTP, [!DNL Marketo Measure] ha automatizzato quella parte per te. Vai alla schermata &quot;View/Edit&quot; schema (Visualizza/Modifica) per l’origine degli attributi del cliente creata nel passaggio 1 e indica all’Adobe quali sono i tipi di dati per ciascuno degli attributi che [!DNL Marketo Measure] ha caricato per tuo conto. Se necessario, puoi anche creare nuovi nomi descrittivi per gli attributi caricati.

   Se hai scelto di sincronizzare gli attributi dall’oggetto account CRM, ti consigliamo vivamente di sceglierne di nuovi, come [!DNL Marketo Measure] compila solo i nomi a livello di API per questi attributi, che in genere non sono descrittivi dei rapporti.

1. L’ultimo passaggio consiste nel configurare le sottoscrizioni di attributi per le applicazioni di Experience Cloud in cui desideri utilizzare gli attributi. Puoi configurare le iscrizioni per [!DNL Adobe Analytics] o [!DNL Adobe Target].  Ulteriori informazioni su come eseguire questa operazione [si trova qui](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/subscription.html).

## Descrizioni attributi {#attribute-descriptions}

Quando crei una connessione attributo cliente B2B, [!DNL Marketo Measure] crea automaticamente un set standard di attributi del cliente B2B. Questi attributi sono descritti nella tabella seguente.

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
   <strong>Nota:</strong> account.name è il nome a livello di API Salesforce per l’attributo name nell’oggetto account. Puoi scegliere un nome visualizzato migliore (ad esempio, "Company") per questo attributo durante il passaggio di convalida dello schema della configurazione dell’integrazione (passaggio 4).</td>
  </tr>
  <tr> 
   <td>Ricavi attribuiti - ‹MODEL›</td> 
   <td>I ricavi attribuiti a questo cliente in virtù della sua associazione con opportunità acquisite nel tuo sistema CRM, come calcolato dalla [!DNL Marketo Measure] motore di attribuzione.<br/>
   Esiste uno di questi attributi per ogni modello di attribuzione che [!DNL Marketo Measure] gli abbonamenti consentono (ad esempio, "Entrate attribuite - Percorso completo").</td>
  </tr>
  <tr> 
   <td>Fase funnel più profonda</td> 
   <td>La fase funnel più profonda di qualsiasi opportunità aperta associata all’utente specificato.</td>
  </tr>
  <tr> 
   <td>Opportunità aperte</td> 
   <td>Un elenco delimitato da punti e virgola degli ID opportunità a cui l’utente è legato in base ai dati CRM.</td>
  </tr> 
 </tbody> 
</table>

**Nota sui limiti degli attributi**

Gli attributi visualizzati tramite questa integrazione vengono conteggiati rispetto ai limiti degli attributi contrattuali in [!DNL Adobe Analytics] e [!DNL Adobe Target]. Solo gli attributi visualizzati tramite una sottoscrizione di attributi (passaggio 5 in [Configurazione dell’integrazione](#configuring-the-integration)) a fronte del limite per l&#39;applicazione sottoscritta.

## Domande frequenti {#faqs}

**Come posso modificare il set di attributi che voglio condividere tramite questa integrazione?**

Per un attributo condiviso da [!DNL Marketo Measure] all’organizzazione Adobe IMS tramite questa integrazione per essere visibile e utilizzato in [!DNL Adobe Analytics], deve essere implementato tramite un Abbonamento di attributi configurato nella console dei servizi core. Pertanto, se desideri rimuovere un attributo in modo che non venga più visualizzato in [!DNL Adobe Analytics], puoi farlo semplicemente eliminando l’abbonamento all’attributo.

È inoltre possibile eliminare la connessione Attributi del cliente B2B in [!DNL Marketo Measure] e ricrearlo con l’attributo che non desideri più condividere escluso dalla configurazione della connessione. Allo stesso modo, per aggiungere attributi all’integrazione, devi eliminare la connessione esistente e crearne una nuova con gli attributi desiderati aggiunti alla configurazione.

Alla luce di quanto sopra, si consiglia vivamente di selezionare gli attributi il più inclusivi possibile durante la configurazione della connessione degli attributi per la prima volta.

**Quali sono alcuni casi di utilizzo di esempio per questa integrazione?**

1. Metriche del traffico basate sull’account: utilizzando l’attributo nome account, puoi creare segmenti di uno o più account di destinazione in Adobe Analytics e analizzare le metriche del traffico del sito solo per il sottoinsieme del traffico proveniente dagli account di destinazione.
1. Analisi del contenuto: utilizza la metrica delle entrate per analizzare quale contenuto del sito è più coinvolgente per i clienti che alla fine acquistano il tuo prodotto o servizio, o per coloro che raggiungono una specifica fase di funnel di interesse.
1. Supporto live-deal: fornisci al team di vendita informazioni fruibili analizzando il comportamento del sito per gli utenti associati a una specifica opportunità aperta nel CRM.
