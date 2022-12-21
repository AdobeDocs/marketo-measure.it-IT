---
unique-page-id: 18874761
description: Single Sign On - [!DNL Marketo Measure] - Documentazione del prodotto
title: Single Sign On
exl-id: a328e9cb-8352-4693-8a44-533e08f1a29c
source-git-commit: 09ffdbb0b1baeed870a3145268997e63a3707c97
workflow-type: tm+mt
source-wordcount: '1310'
ht-degree: 0%

---

# Single Sign On {#single-sign-on}

SAML (security assertion markup language) per SSO (single sign-on) consente agli utenti di eseguire l&#39;autenticazione tramite il provider di identità di un&#39;azienda quando effettuano l&#39;accesso al [!DNL Marketo Measure] app. SSO consente a un utente di eseguire l&#39;autenticazione una sola volta, senza la necessità di autenticare applicazioni separate. SAML è una necessità per i clienti aziendali perché non tutti gli utenti avranno un [!DNL Salesforce] o [!DNL Google] conto all&#39;interno della loro organizzazione. Per scalare, [!DNL Marketo Measure] ha sviluppato una soluzione SAML in grado di supportare i provider di identità aziendali.

>[!CAUTION]
>
>Questo articolo delinea il Single Sign On (SSO) e la gestione avanzata degli utenti CRM. Se è stato eseguito il provisioning del tuo account **dopo il 10/09/2020**, si prega di ignorare questo articolo, in quanto SSO e Identity Management saranno impostati all&#39;interno del [Adobe Admin Console per il tuo [!DNL Marketo Measure] integrazione](/help/configuration-and-setup/getting-started-with-marketo-measure/marketo-measure-quick-start.md).

>[!NOTE]
>
>È probabile che le aziende utilizzino diversi provider di identità (ad esempio, Ping Identity, Okta). I termini utilizzati nelle seguenti istruzioni di configurazione e nell’interfaccia utente potrebbero non corrispondere direttamente a quelli utilizzati dal provider di identità.

## Requisiti {#requirements}

* Utente con le autorizzazioni AccountAdmin nel [!DNL Marketo Measure] App
* Utente con accesso amministrativo al provider di identità del cliente

## Introduzione {#getting-started}

Per iniziare, passa a Impostazioni > Protezione > Autenticazione nella pagina [!DNL Marketo Measure] applicazione. Quindi, imposta il tipo di accesso su SSO personalizzato per visualizzare le opzioni di configurazione. Le modifiche diventeranno effettive solo dopo aver verificato l’autenticazione e aver fatto clic sul pulsante **[!UICONTROL Save]** nella parte inferiore della pagina.

![](assets/single-sign-on-1.png)

## Processo {#process}

[!DNL Marketo Measure] L&#39;accesso singolo richiede la configurazione delle impostazioni di autenticazione in una serie di passaggi importanti da seguire in modo da non rischiare di essere bloccato fuori dal tuo [!DNL Marketo Measure] conto.

Imposta la [!DNL Marketo Measure] Applicazione nel provider di identità. Per informazioni dettagliate, consulta la documentazione esterna elencata di seguito.

    a) Quando viene richiesto l’URL di accesso singolo o l’URL di destinazione o destinazione, l’URL del servizio clienti di asserzione SAML (ACS), utilizza [https://apps.bizible.com/BizibleSAML2/ReceiveSSORequest](https://apps.bizible.com/BizibleSAML2/ReceiveSSORequest)
    
    b) Quando viene richiesto l&#39;URL di restrizione del pubblico o l&#39;identificatore univoco definito dall&#39;applicazione, utilizza [https://BizibleLPM](https://biziblelpm/)

Passa a SSO personalizzato nella [!DNL Marketo Measure] Applicazione

    a) Una volta abilitato il gruppo di fatturazione per l&#39;account, puoi ora passare a [!UICONTROL Settings] >>[!UICONTROL Security] >> [!UICONTROL Authentication]
    
    b) Per impostazione predefinita, il tipo di accesso sarà impostato su &quot;Utenti CRM&quot;.
    
    c. Passa il tipo di accesso a &quot;SSO personalizzato&quot; per avviare il processo di configurazione.

Inserisci le impostazioni di connessione per la configurazione del provider di identità

    a) Il provider di identità potrebbe fornire un documento con estensione xml di metadati IdP che estrarrà i campi di configurazione richiesti. Carica il contenuto del documento .xml o compila i tre campi seguenti dall’output ottenuto durante il processo di configurazione del provider di identità. **Non è necessario completare entrambi.**
    
    i. URL IdP: URL che [!DNL Marketo Measure] deve puntare a per autenticare gli utenti nel [!DNL Marketo Measure] applicazione. A volte indicato come &quot;URL di reindirizzamento&quot;.
    ii) Emittente IdP: Identificatore univoco del provider di identità. A volte indicato come &quot;Chiave esterna&quot;.
    iii) Certificato IdP: Una chiave pubblica che consente [!DNL Marketo Measure] per verificare e convalidare la firma di tutte le risposte del provider di identità.

Imposta la scadenza del token per gli utenti in minuti.

    a) [!DNL Marketo Measure] consente un numero intero da 1 a 1440 minuti. Una volta superato il tempo di sessione di un utente, quest’ultimo viene disconnesso quando passa a una nuova pagina.

Imposta e mappa le impostazioni dell&#39;attributo utente in base al rispettivo nome, cognome e indirizzo e-mail.

    a) Inserendo gli attributi SAML, [!DNL Marketo Measure] sarà in grado di riconoscere gli utenti dalle informazioni trasmesse.
    
    i. Attributo e-mail: Specifica il nome dell’attributo utilizzato dal provider di identità per l’indirizzo e-mail dell’utente.
    ii) Attributo nome: Specifica il nome dell’attributo utilizzato dal provider di identità per il nome dell’utente.
    iii) Attributo cognome: Specifica il nome dell’attributo utilizzato dal provider di identità per il cognome dell’utente.
    
    b) Suggerimento: Se ora verifichi la configurazione SAML, analizzeremo gli attributi Email, First Name e Last Name che puoi utilizzare per questa sezione.

![](assets/single-sign-on-2.png)

Imposta e mappa le impostazioni del Ruolo utente sui rispettivi ruoli o gruppi classificati dal tuo IdP.

    a) I clienti possono scegliere di assegnare [!DNL Marketo Measure] ruoli utente in base ai gruppi definiti nel relativo provider di identità. Inserendo gli attributi SAML, [!DNL Marketo Measure] sarà in grado di mappare i ruoli e i gruppi dell&#39;utente su [!DNL Marketo Measure] autorizzazioni utente. Consigliamo vivamente di impostare questi ruoli in modo che [!DNL Marketo Measure] l&#39;amministratore dispone di diritti sufficienti per aggiornare l&#39;account.
    
    b) Se non è stato mappato alcun ruolo o gruppo, l’impostazione predefinita prevede che tutti i dipendenti del provider di identità abbiano accesso utente standard.
    
    i. [!DNL Marketo Measure] Utente standard: Fornisci il ruolo o il valore del gruppo (dal provider SSO) per gli utenti che devono avere accesso in sola lettura al [!DNL Marketo Measure] applicazione.
    ii) [!DNL Marketo Measure] Utente amministratore account: Fornisci il ruolo o il valore del gruppo (dal provider SSO) per gli utenti che devono avere accesso amministrativo al [!DNL Marketo Measure] applicazione. Questo significa che il ruolo ha accesso alle modifiche alle configurazioni e alle impostazioni relative al tuo account.
    iii) Devi avere un attributo nel tuo IdP con il nome esatto di &quot;gruppi&quot; che contenga i valori inseriti negli attributi &quot;Utente standard Bizible&quot; o &quot;Utente amministratore account Bizible&quot;.
    
    c. Se più ruoli o gruppi devono essere mappati a un ruolo, immetti ogni valore separato da una virgola.

![](assets/single-sign-on-3.png)

Verificare la configurazione del Single Sign-On

    a) Prima di premere Salva, dovrai fare clic sul pulsante [!UICONTROL Test SAML Authentication] per verificare che le impostazioni siano state configurate correttamente.
    
    b) Se viene visualizzato un errore di errore, segui il messaggio e riprova.

![](assets/single-sign-on-4.png)

Salva le impostazioni e indirizza i tuoi colleghi a utilizzare [!UICONTROL Single Sign On] con il nuovo URL di accesso personalizzato.

    a) Importante: Una volta salvate le nuove impostazioni di autenticazione, è possibile che la sessione si concluda quando si passa a una nuova pagina perché l&#39;accesso è stato disabilitato dagli utenti CRM e attivato SSO personalizzato.

![](assets/single-sign-on-5.png)

Provatela!

    a) Utilizza il tuo nuovo URL di accesso personalizzato e tenta di accedere di nuovo a [!DNL Marketo Measure] Applicazione con le credenziali del provider di identità.
    
    b) Il formato sarà simile a &quot;https://apps.adobe.com/business/[accountName]&quot;
    
    c. Congratulazioni! È stato configurato l&#39;accesso singolo nel [!DNL Marketo Measure] Domanda per il tuo account!

![](assets/single-sign-on-6.png)

>[!NOTE]
>
>Dopo aver configurato SSO, non dovrai più aggiungere utenti all&#39;interno di [!DNL Marketo Measure] applicazione. Il provisioning degli utenti deve essere gestito direttamente all’interno del provider di identità.

## Utenti CRM (configurazione avanzata) {#crm-users-advanced-setup}

Per impostazione predefinita, tutti gli account possono accedere al [!DNL Marketo Measure] applicazione che utilizza le relative credenziali CRM. A volte, i proprietari dell&#39;account devono limitare l&#39;accesso a determinati ruoli e non aprirlo a tutti gli utenti con una licenza CRM attiva. La configurazione avanzata ti consentirà di mappare i ruoli e i gruppi CRM in [!DNL Marketo Measure] autorizzazioni utente.

Se non è stato mappato alcun ruolo o gruppo, l&#39;impostazione predefinita prevede che tutte le licenze attive nel CRM avranno accesso utente standard.

* [!DNL Marketo Measure] Utente standard: Fornisci il ruolo o il valore del gruppo per gli utenti che devono avere accesso in sola lettura al [!DNL Marketo Measure] applicazione.
* [!DNL Marketo Measure] Utente amministratore account: Fornisci il ruolo o il valore del gruppo per gli utenti che devono avere accesso amministrativo al [!DNL Marketo Measure] applicazione. Questo significa che il ruolo ha accesso alle modifiche alle configurazioni e alle impostazioni relative al tuo account.

Se più ruoli o gruppi devono essere mappati a un ruolo, immetti ogni valore separato da una virgola.

**Ruoli Salesforce**

Per [!DNL Salesforce] Ruoli, utilizza il nome di ciascun Ruolo. Tutti i ruoli si trovano nella sezione [!UICONTROL Setup] >[!UICONTROL Manage Users] >[!UICONTROL Roles] menu.

![](assets/6.png)

**Ruoli di Dynamics**

Per [!DNL Dynamics] Ruoli, utilizza il nome di ogni ruolo di sicurezza. Tutti i ruoli di sicurezza si trovano nella [!UICONTROL Settings] >[!UICONTROL Security] >[!UICONTROL Security Roles] menu.

![](assets/7.png)

![](assets/8.png)

**Utenti Google**

Una volta configurato l&#39;SSO personalizzato, il [!UICONTROL Users] verrà aggiornata per mostrare solo gli utenti esterni che sono stati aggiunti con gli accessi a Google. Poiché tutti gli utenti con accesso sono definiti tramite la configurazione SSO, ulteriori utenti esterni sono elencati qui.

![](assets/9.png)

Solo valido [!DNL Google] Gli account possono essere aggiunti e devono avere un Ruolo utente definito.

## Collegamenti esterni {#external-links}

* [Okta](http://developer.okta.com/standards/SAML/setting_up_a_saml_application_in_okta)
* [Ping Identity](http://docs.pingidentity.com/bundle/p1_enterpriseConfigSsoSaml_cas/page/enableAppWithoutURL.html)
* [OneLogin](http://onelogin.service-now.com/support?id=kb_article&amp;sys_id=b2c91143db109700d5505eea4b9619d5)
* [Active Directory](http://docs.microsoft.com/en-us/azure/active-directory/active-directory-saas-custom-apps)
