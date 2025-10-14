---
unique-page-id: 18874761
description: Single Sign-On - [!DNL Marketo Measure]
title: Single Sign-On
exl-id: a328e9cb-8352-4693-8a44-533e08f1a29c
source-git-commit: 4787f765348da71bc149c997470ce678ba498772
workflow-type: tm+mt
source-wordcount: '1257'
ht-degree: 0%

---

# Single Sign-On {#single-sign-on}

SAML (Security Assertion Markup Language) per SSO (Single Sign-On) consente agli utenti di eseguire l&#39;autenticazione tramite il provider di identità di un&#39;azienda quando accedono all&#39;app [!DNL Marketo Measure]. SSO consente a un utente di eseguire l&#39;autenticazione una sola volta, senza dover eseguire l&#39;autenticazione di app separate. SAML è una necessità per i clienti aziendali perché non tutti gli utenti dispongono di un account [!DNL Salesforce] o [!DNL Google] all&#39;interno dell&#39;organizzazione. Per eseguire la scalabilità, [!DNL Marketo Measure] ha sviluppato una soluzione SAML in grado di supportare i provider di identità aziendali.

>[!CAUTION]
>
>Questo articolo descrive il Single Sign-On (SSO) e la gestione avanzata degli utenti CRM. Se il provisioning del tuo account è stato eseguito **dopo il 9/10/2020**, ignora questo articolo, in quanto SSO e Identity Management verranno configurati in [Adobe Admin Console per la tua [!DNL Marketo Measure] integrazione](/help/configuration-and-setup/getting-started-with-marketo-measure/marketo-measure-quick-start.md).

>[!NOTE]
>
>È probabile che le aziende utilizzino diversi provider di identità (ad esempio, Ping Identity, Okta). I termini utilizzati nelle seguenti istruzioni di configurazione e nell’interfaccia utente di potrebbero non corrispondere direttamente a quelli utilizzati dal provider di identità.

## Requisiti {#requirements}

* Utente con autorizzazioni AccountAdmin nell&#39;app [!DNL Marketo Measure]
* Utente con accesso amministrativo al provider di identità del cliente

## Guida introduttiva {#getting-started}

Per iniziare, passare alla pagina Impostazioni > Protezione > Autenticazione nell&#39;applicazione [!DNL Marketo Measure]. Quindi imposta il tipo di accesso su SSO personalizzato per visualizzare le opzioni di configurazione. Le modifiche diventeranno effettive solo dopo aver verificato l&#39;autenticazione e aver fatto clic sul pulsante **[!UICONTROL Save]** nella parte inferiore della pagina.

![](assets/single-sign-on-1.png)

## Processo {#process}

[!DNL Marketo Measure] Single Sign-On richiede la configurazione delle impostazioni di autenticazione in una serie di passaggi in modo da non rischiare di rimanere bloccati dall&#39;account [!DNL Marketo Measure].

Configurare l&#39;applicazione [!DNL Marketo Measure] nel provider di identità. Per le procedure dettagliate, consulta la documentazione esterna elencata di seguito.

    a. Quando viene richiesto l&#39;URL Single Sign On, l&#39;URL del destinatario o l&#39;URL di destinazione, l&#39;URL del servizio clienti SAML Assertion (ACS), utilizzare [https://apps.bizible.com/BizibleSAML2/ReceiveSSORequest](https://apps.bizible.com/BizibleSAML2/ReceiveSSORequest)
    
    b. Quando viene richiesto l&#39;URL di restrizione del pubblico o l&#39;identificatore univoco definito dall&#39;applicazione, utilizzare [https://BizibleLPM](https://biziblelpm/)

Passa all&#39;SSO personalizzato nell&#39;applicazione [!DNL Marketo Measure]

    a. Una volta abilitato il gruppo di fatturazione per il tuo account, ora puoi passare a [!UICONTROL Settings] >>[!UICONTROL Security] >> [!UICONTROL Authentication]
    
    b. Per impostazione predefinita, il Tipo di accesso sarà impostato su &quot;Utenti CRM&quot;.
    
    c. Passa il tipo di accesso a &quot;SSO personalizzato&quot; per avviare il processo di configurazione.

Specificare le impostazioni di connessione per la configurazione del provider di identità

    a. Il provider di identità potrebbe fornire un documento .xml di metadati IdP che estrae i campi di configurazione richiesti. Caricare il contenuto del documento XML o compilare i tre campi seguenti dall&#39;output ottenuto durante il processo di configurazione del provider di identità. **Non è necessario completare entrambe le operazioni.**
    
    i. URL IdP: l&#39;URL a cui [!DNL Marketo Measure] deve puntare per autenticare gli utenti nell&#39;applicazione  [!DNL Marketo Measure] . A volte indicato come &quot;URL di reindirizzamento&quot;.
    ii. Emittente IdP: identificatore univoco del provider di identità. A volte indicato come &quot;Chiave esterna&quot;.
    iii. Certificato IdP: chiave pubblica che consente a  [!DNL Marketo Measure]  di verificare e convalidare la firma di tutte le risposte del provider di identità.

Imposta la scadenza del token per gli utenti in minuti.

    a. [!DNL Marketo Measure] consente un numero intero da 1 a 1440 minuti. Dopo il superamento del tempo di sessione di un utente, l&#39;utente verrà disconnesso non appena passerà a una nuova pagina.

Imposta e mappa le impostazioni degli attributi utente in base ai rispettivi nomi, cognomi e indirizzi e-mail.

    a. Immettendo gli attributi SAML, [!DNL Marketo Measure] sarà in grado di riconoscere gli utenti in base alle informazioni trasmesse.
    
    i. Attributo e-mail: fornisci il nome attributo utilizzato dal provider di identità per l’indirizzo e-mail dell’utente.
    ii. Attributo nome: fornire il nome attributo utilizzato dal provider di identità per il nome dell&#39;utente.
    iii. Attributo cognome: specificare il nome dell&#39;attributo utilizzato dal provider di identità per il cognome dell&#39;utente.
    
     b. Suggerimento: se verifichi ora la configurazione SAML, verranno analizzati gli attributi E-mail, Nome e Cognome che puoi utilizzare per questa sezione.

![](assets/single-sign-on-2.png)

Imposta e mappa le impostazioni del Ruolo utente sui rispettivi ruoli o gruppi classificati dal tuo IdP.

    a. I clienti possono assegnare  [!DNL Marketo Measure] ruoli utente in base ai gruppi definiti nel proprio provider di identità. Immettendo gli attributi SAML, [!DNL Marketo Measure] sarà in grado di mappare i ruoli e i gruppi dell&#39;utente alle [!DNL Marketo Measure] autorizzazioni utente. È consigliabile configurare questi ruoli in modo che l&#39;amministratore  [!DNL Marketo Measure]  disponga di diritti sufficienti per aggiornare l&#39;account.
    
     b. Se non è stato eseguito il mapping di ruoli o gruppi, l&#39;impostazione predefinita prevede che tutti i dipendenti del provider di identità abbiano l&#39;accesso utente Standard.
    
    i. [!DNL Marketo Measure] Utente standard: fornisci il valore del ruolo o del gruppo (dal provider SSO) per gli utenti che devono avere accesso in sola lettura all&#39;applicazione  [!DNL Marketo Measure] .
    ii. [!DNL Marketo Measure] Utente amministratore account: fornisci il valore del ruolo o del gruppo (dal provider SSO) per gli utenti che devono avere accesso amministrativo all&#39;applicazione  [!DNL Marketo Measure] . Ciò significa che il ruolo ha accesso a modificare le configurazioni e le impostazioni relative al tuo account.
    iii. Nell&#39;IdP deve essere presente un attributo con il nome esatto di &quot;gruppi&quot; che racchiude i valori inseriti negli attributi &quot;Utente standard Bizible&quot; o &quot;Utente amministratore account Bizible&quot;.
    
    c. Se è necessario mappare più ruoli o gruppi a un ruolo, immettere ogni valore separato da una virgola.

![](assets/single-sign-on-3.png)

Verificare la configurazione Single Sign-On

    a. Prima di poter fare clic su Salva, sarà necessario fare clic sul pulsante [!UICONTROL Test SAML Authentication] per verificare che le impostazioni siano state configurate correttamente.
    
     b. Se viene visualizzato un errore, seguire il messaggio e riprovare.

![](assets/single-sign-on-4.png)

Salva le impostazioni e indirizza i tuoi colleghi a utilizzare [!UICONTROL Single Sign On] con il nuovo URL di accesso personalizzato.

    a. Importante: una volta salvate le nuove impostazioni di autenticazione, è possibile che la sessione termini quando si passa a una nuova pagina perché è stato disabilitato l&#39;accesso da parte degli utenti CRM e abilitato l&#39;SSO personalizzato.

![](assets/single-sign-on-5.png)

Provalo!

    a. Utilizza il nuovo URL di accesso personalizzato e prova ad accedere nuovamente all&#39;applicazione  [!DNL Marketo Measure] con le credenziali del provider di identità.
    
     b. Il formato sarà simile a &quot;https://apps.adobe.com/business/[accountName]&quot;
    
    c. Congratulazioni! Hai configurato correttamente l&#39;accesso Single Sign-On nell&#39;applicazione  [!DNL Marketo Measure] per il tuo account!

![](assets/single-sign-on-6.png)

>[!NOTE]
>
>Dopo aver configurato l&#39;SSO, non sarà più necessario aggiungere utenti all&#39;interno dell&#39;applicazione [!DNL Marketo Measure]. Il provisioning degli utenti deve essere gestito direttamente all’interno del provider di identità.

## Utenti CRM (configurazione avanzata) {#crm-users-advanced-setup}

Per impostazione predefinita, tutti gli account possono accedere all&#39;applicazione [!DNL Marketo Measure] utilizzando le credenziali CRM. A volte, i proprietari dell’account devono limitare l’accesso a determinati ruoli e non aprirlo a tutti gli utenti con una licenza di gestione delle relazioni con i clienti attiva. La configurazione avanzata consente di mappare i ruoli e i gruppi di gestione delle relazioni con i clienti alle autorizzazioni utente [!DNL Marketo Measure].

Se non è stato mappato alcun ruolo o gruppo, l&#39;impostazione predefinita prevede che tutte le licenze attive nel CRM dispongano dell&#39;accesso utente Standard.

* Utente standard [!DNL Marketo Measure]: fornire il valore del ruolo o del gruppo per gli utenti che devono avere accesso in sola lettura all&#39;applicazione [!DNL Marketo Measure].
* Utente amministratore account [!DNL Marketo Measure]: fornire il valore del ruolo o del gruppo per gli utenti che devono avere accesso amministrativo all&#39;applicazione [!DNL Marketo Measure]. Ciò significa che il ruolo ha accesso a modificare le configurazioni e le impostazioni relative al tuo account.

Se è necessario mappare più ruoli o gruppi a un ruolo, immettere ogni valore separato da una virgola.

**Ruoli Salesforce**

Per [!DNL Salesforce] ruoli, utilizzare il nome di ogni ruolo. Tutti i ruoli sono disponibili nel menu [!UICONTROL Setup] >[!UICONTROL Manage Users] >[!UICONTROL Roles].

![](assets/6.png)

**Ruoli Dynamics**

Per [!DNL Dynamics] ruoli, utilizzare il nome di ogni ruolo di protezione. Tutti i ruoli di protezione sono disponibili nel menu [!UICONTROL Settings] >[!UICONTROL Security] >[!UICONTROL Security Roles].

![](assets/7.png)

![](assets/8.png)

**Utenti Google**

Una volta configurato l&#39;SSO personalizzato, la pagina [!UICONTROL Users] viene aggiornata per mostrare solo gli utenti esterni che sono stati aggiunti con gli accessi a Google. Poiché tutti gli utenti con accesso sono definiti tramite la configurazione SSO, qui sono elencati altri utenti esterni.

![](assets/9.png)

È possibile aggiungere solo account [!DNL Google] validi e deve essere definito un ruolo utente.

## Collegamenti esterni {#external-links}

* [Okta](https://developer.okta.com/standards/SAML/setting_up_a_saml_application_in_okta)
* [Effettua ping dell&#39;identità](https://docs.pingidentity.com:443/bundle/p1_enterpriseConfigSsoSaml_cas/page/enableAppWithoutURL.html)
* [OneLogin](https://onelogin.service-now.com/support?id=kb_article&sys_id=b2c91143db109700d5505eea4b9619d5)
* [Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-saas-custom-apps)
