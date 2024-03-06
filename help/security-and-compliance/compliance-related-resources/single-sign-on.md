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

SAML (Security Assertion Markup Language) per SSO (Single Sign-On) consente agli utenti di eseguire l&#39;autenticazione tramite il provider di identità di un&#39;azienda quando accedono al [!DNL Marketo Measure] app. SSO consente a un utente di eseguire l&#39;autenticazione una sola volta, senza dover eseguire l&#39;autenticazione di app separate. SAML è una necessità per i clienti aziendali perché non tutti gli utenti hanno un [!DNL Salesforce] o [!DNL Google] all&#39;interno della loro organizzazione. Per ridimensionare, [!DNL Marketo Measure] ha sviluppato una soluzione SAML in grado di supportare i provider di identità aziendali.

>[!CAUTION]
>
>Questo articolo descrive il Single Sign-On (SSO) e la gestione avanzata degli utenti CRM. Se è stato eseguito il provisioning del tuo account **dopo il 9/10/2020**, ignora questo articolo, in quanto SSO e Identity Management verranno impostati all&#39;interno di [Adobe Admin Console per [!DNL Marketo Measure] integrazione](/help/configuration-and-setup/getting-started-with-marketo-measure/marketo-measure-quick-start.md).

>[!NOTE]
>
>È probabile che le aziende utilizzino diversi provider di identità (ad esempio, Ping Identity, Okta). I termini utilizzati nelle seguenti istruzioni di configurazione e nell’interfaccia utente di potrebbero non corrispondere direttamente a quelli utilizzati dal provider di identità.

## Requisiti {#requirements}

* Utente con autorizzazioni AccountAdmin in [!DNL Marketo Measure] App
* Utente con accesso amministrativo al provider di identità del cliente

## Guida introduttiva {#getting-started}

Per iniziare, passa a Impostazioni > Sicurezza > Pagina Autenticazione in [!DNL Marketo Measure] applicazione. Quindi imposta il tipo di accesso su SSO personalizzato per visualizzare le opzioni di configurazione. Le modifiche diventeranno effettive solo dopo aver verificato l’autenticazione e aver fatto clic su **[!UICONTROL Save]** nella parte inferiore della pagina.

![](assets/single-sign-on-1.png)

## Processo {#process}

[!DNL Marketo Measure] Single Sign-On richiede la configurazione delle impostazioni di autenticazione in una serie di passaggi, in modo da non rischiare di rimanere bloccati [!DNL Marketo Measure] account.

Configurare [!DNL Marketo Measure] Applicazione nel provider di identità. Per le procedure dettagliate, consulta la documentazione esterna elencata di seguito.

    a. Quando viene richiesto l’URL Single Sign On, l’URL del destinatario o l’URL di destinazione, l’URL del servizio clienti SAML Assertion (ACS), utilizza [https://apps.bizible.com/BizibleSAML2/ReceiveSSORequest](https://apps.bizible.com/BizibleSAML2/ReceiveSSORequest)
    
    b. Quando viene richiesto l’URL di Restrizione del pubblico o un identificatore univoco definito dall’applicazione, utilizza [https://BizibleLPM](https://biziblelpm/)

Passa a SSO personalizzato in [!DNL Marketo Measure] Applicazione

    a. Una volta che il gruppo di fatturazione è stato abilitato per il tuo account, ora puoi passare a [!UICONTROL Settings] >>[!UICONTROL Security] >> [!UICONTROL Authentication]
    
    b. Per impostazione predefinita, il Tipo di accesso verrà impostato su &quot;Utenti CRM&quot;.
    
    c. Passa il tipo di accesso a &quot;SSO personalizzato&quot; per avviare il processo di configurazione.

Specificare le impostazioni di connessione per la configurazione del provider di identità

    a. Il provider di identità potrebbe fornire un documento .xml di metadati IdP che estrae i campi di configurazione richiesti. Caricare il contenuto del documento XML o compilare i tre campi seguenti dall&#39;output ottenuto durante il processo di configurazione del provider di identità. **Non è necessario completare entrambe le operazioni.**
    
    i. URL IdP: URL che [!DNL Marketo Measure] deve puntare a per autenticare gli utenti in [!DNL Marketo Measure] applicazione. A volte indicato come &quot;URL di reindirizzamento&quot;.
    ii. Emittente IdP: identificatore univoco del provider di identità. A volte indicato come &quot;Chiave esterna&quot;.
    iii. Certificato IdP: chiave pubblica che consente [!DNL Marketo Measure] per verificare e convalidare la firma di tutte le risposte del provider di identità.

Imposta la scadenza del token per gli utenti in minuti.

    a. [!DNL Marketo Measure] consente un numero intero da 1 a 1440 minuti. Una volta superato il tempo di sessione di un utente, quest’ultimo verrà disconnesso non appena si sposta su una nuova pagina.

Imposta e mappa le impostazioni degli attributi utente in base ai rispettivi nomi, cognomi e indirizzi e-mail.

    a. inserendo gli attributi SAML, [!DNL Marketo Measure] sarà in grado di riconoscere gli utenti in base alle informazioni trasmesse.
    
    i. Attributo e-mail: fornisci il nome dell’attributo utilizzato dal provider di identità per l’indirizzo e-mail dell’utente.
    ii. Attributo nome: fornire il nome attributo utilizzato dal provider di identità per il nome dell&#39;utente.
    iii. Attributo cognome: specificare il nome dell&#39;attributo utilizzato dal provider di identità per il cognome dell&#39;utente.
    
    b. Suggerimento: se verifichi la configurazione SAML ora, verranno analizzati gli attributi E-mail, Nome e Cognome che puoi utilizzare per questa sezione.

![](assets/single-sign-on-2.png)

Imposta e mappa le impostazioni del Ruolo utente sui rispettivi ruoli o gruppi classificati dal tuo IdP.

    a. I clienti hanno la possibilità di assegnare [!DNL Marketo Measure] ruoli utente in base ai gruppi definiti nel proprio provider di identità. Immettendo gli attributi SAML, [!DNL Marketo Measure] sarà in grado di mappare i ruoli e i gruppi dell’utente su [!DNL Marketo Measure] autorizzazioni utente. È consigliabile impostare questi ruoli in modo che [!DNL Marketo Measure] l&#39;amministratore dispone di diritti sufficienti per aggiornare l&#39;account.
    
    b. Se non viene eseguito il mapping di ruoli o gruppi, l&#39;impostazione predefinita prevede che tutti i dipendenti del provider di identità abbiano accesso utente Standard.
    
    i. [!DNL Marketo Measure] Utente standard: fornisci il valore del ruolo o del gruppo (dal provider SSO) per gli utenti che devono avere accesso in sola lettura al [!DNL Marketo Measure] applicazione.
    ii. [!DNL Marketo Measure] Utente amministratore account: fornisci il valore del ruolo o del gruppo (dal provider SSO) per gli utenti che devono avere accesso amministrativo al [!DNL Marketo Measure] applicazione. Ciò significa che il ruolo ha accesso a modificare le configurazioni e le impostazioni relative al tuo account.
    iii. Nell&#39;IdP deve essere presente un attributo con il nome esatto di &quot;gruppi&quot; che racchiude i valori inseriti negli attributi &quot;Utente standard Bizible&quot; o &quot;Utente amministratore account Bizible&quot;.
    
    c. Se è necessario mappare più ruoli o gruppi a un ruolo, immettere ogni valore separato da una virgola.

![](assets/single-sign-on-3.png)

Verificare la configurazione Single Sign-On

    a. Prima di poter premere Salva, è necessario fare clic sul pulsante [!UICONTROL Test SAML Authentication] per verificare che le impostazioni siano state configurate correttamente.
    
    b. Se viene visualizzato un errore di tipo &quot;errore&quot;, segui il messaggio e riprova.

![](assets/single-sign-on-4.png)

Salvare le impostazioni e invitare i colleghi a utilizzare [!UICONTROL Single Sign On] con il nuovo URL di accesso personalizzato.

    a. Importante: una volta salvate le nuove impostazioni di autenticazione, è possibile che la sessione termini quando si passa a una nuova pagina, poiché è stato disabilitato l’accesso da parte degli utenti CRM e abilitato l’SSO personalizzato.

![](assets/single-sign-on-5.png)

Provalo!

    a. Utilizza il nuovo URL di accesso personalizzato e prova ad accedere nuovamente al [!DNL Marketo Measure] con le credenziali del provider di identità.
    
    b. Il formato sarà simile a &quot;https://apps.adobe.com/business/[accountName]&quot;
    
    C. Congratulazioni! L&#39;accesso Single Sign-On è stato impostato correttamente in [!DNL Marketo Measure] Richiesta per il tuo account.

![](assets/single-sign-on-6.png)

>[!NOTE]
>
>Dopo aver configurato l&#39;SSO, non sarà più necessario aggiungere utenti all&#39;interno del [!DNL Marketo Measure] applicazione. Il provisioning degli utenti deve essere gestito direttamente all’interno del provider di identità.

## Utenti CRM (configurazione avanzata) {#crm-users-advanced-setup}

Per impostazione predefinita, tutti gli account possono accedere a [!DNL Marketo Measure] dell&#39;applicazione utilizzando le credenziali CRM. A volte, i proprietari dell’account devono limitare l’accesso a determinati ruoli e non aprirlo a tutti gli utenti con una licenza di gestione delle relazioni con i clienti attiva. La configurazione avanzata ti consente di mappare i ruoli e i gruppi di gestione delle relazioni con i clienti a [!DNL Marketo Measure] autorizzazioni utente.

Se non è stato mappato alcun ruolo o gruppo, l&#39;impostazione predefinita prevede che tutte le licenze attive nel CRM dispongano dell&#39;accesso utente Standard.

* [!DNL Marketo Measure] Utente standard: fornisci il valore del ruolo o del gruppo per gli utenti che devono avere accesso in sola lettura al [!DNL Marketo Measure] applicazione.
* [!DNL Marketo Measure] Utente amministratore account: fornisci il valore del ruolo o del gruppo per gli utenti che devono avere accesso amministrativo al [!DNL Marketo Measure] applicazione. Ciò significa che il ruolo ha accesso a modificare le configurazioni e le impostazioni relative al tuo account.

Se è necessario mappare più ruoli o gruppi a un ruolo, immettere ogni valore separato da una virgola.

**Ruoli Salesforce**

Per [!DNL Salesforce] Ruoli, utilizzare il nome di ogni Ruolo. Tutti i Ruoli si trovano sotto [!UICONTROL Setup] >[!UICONTROL Manage Users] >[!UICONTROL Roles] menu.

![](assets/6.png)

**Ruoli Dynamics**

Per [!DNL Dynamics] Ruoli, utilizzare il nome di ogni Ruolo di protezione. Tutti i Ruoli di Sicurezza si trovano sotto [!UICONTROL Settings] >[!UICONTROL Security] >[!UICONTROL Security Roles] menu.

![](assets/7.png)

![](assets/8.png)

**Utenti Google**

Una volta configurato l&#39;SSO personalizzato, [!UICONTROL Users] La pagina viene aggiornata per mostrare solo gli utenti esterni che sono stati aggiunti con gli accessi di Google. Poiché tutti gli utenti con accesso sono definiti tramite la configurazione SSO, qui sono elencati altri utenti esterni.

![](assets/9.png)

Solo valido [!DNL Google] Gli account possono essere aggiunti e devono avere un Ruolo Utente definito.

## Collegamenti esterni {#external-links}

* [Okta](https://developer.okta.com/standards/SAML/setting_up_a_saml_application_in_okta)
* [Ping identità](https://docs.pingidentity.com:443/bundle/p1_enterpriseConfigSsoSaml_cas/page/enableAppWithoutURL.html)
* [OneLogin](https://onelogin.service-now.com/support?id=kb_article&amp;sys_id=b2c91143db109700d5505eea4b9619d5)
* [Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-saas-custom-apps)
