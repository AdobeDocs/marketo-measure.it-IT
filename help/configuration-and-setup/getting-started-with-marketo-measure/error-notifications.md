---
description: Notifiche di errore - [!DNL Marketo Measure]
title: Notifiche di errore
feature: Fundamentals
exl-id: ed07eed6-ddeb-4856-a1ac-ea3d571283f6
source-git-commit: 20f886a0c6f448956ad2fda2d21a25f8d9a5a6af
workflow-type: tm+mt
source-wordcount: '1692'
ht-degree: 0%

---

# Notifiche di errore {#error-notifications}

Di seguito è riportato un elenco di errori che potresti ricevere tramite notifica in-app o e-mail. Se ricevi uno di questi, segui i rispettivi passaggi per la risoluzione dei problemi. Se questi passaggi non risolvono il problema, contattare il [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support).

Per visualizzare il messaggio di notifica completo in [!DNL Marketo Measure], fare clic su **Visualizza tutto** nella parte inferiore della scheda Notifiche.

![](assets/error-notifications-1.png)

<table>
  <tbody>
    <tr>
      <th style="width:31%">Codice di errore</th>
      <th style="width:23%">Esempio di notifica</th>
      <th style="width:23%">Descrizione</th>
      <th style="width:23%">Passaggi per la risoluzione dei problemi</th>
    </tr>
    <tr>
      <td>API_DISABLED</td>
      <td>Errore durante l'importazione CRM : API_DISABLED : le chiamate API sono state disabilitate per questo utente</td>
      <td>L’autorizzazione API è stata disabilitata per l’utente Marketo Measure.</td>
      <td>Consulta la seguente documentazione di Salesforce su <a href="https://help.salesforce.com/s/articleView?language=en_US&id=sf.branded_apps_commun_api_permset.htm&type=5">come abilitare l'accesso API</a>.</td>
    </tr>
    <tr>
      <td>API_LIMIT_EXCEEDED</td>
      <td>Errore durante l'esportazione CRM : PI_LIMIT_EXCEEDED</td>
      <td>Il limite API del sistema CRM è stato superato (24 ore).</td>
      <td>Per assistenza nella regolazione delle allocazioni di credito API, consulta la seguente documentazione per il CRM:</p>
          <ul>
            <li><a href="https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/service-protection-monitoring">Dynamics</a>
            </li>
            <li><a href="https://developer.salesforce.com/docs/atlas.en-us.salesforce_app_limits_cheatsheet.meta/salesforce_app_limits_cheatsheet/salesforce_app_limits_platform_api.htm">Salesforce</a>
            </li>
          </ul>
          <p>Puoi anche regolare i crediti CRM che Marketo Measure utilizza seguendo i passaggi seguenti:</p>
          <ul>
            <li>Passa a <b>Impostazioni</b> &gt; <b>CRM</b> &gt; <b>Generale</b></li>
            <li>Aggiorna il limite API CRM giornaliero<br/>
              <ul>
                <li><b>Nota: il valore predefinito è 100.000</b></li>
              </ul>
            </li>
          </ul>
          <p>
           <img src="assets/error-notifications-2.png">
          </p>
      </td>
    </tr>
    <tr>
      <td>CANNOT_EXECUTE_FLOW_TRIGGER</td>
      <td>Errore durante l’esportazione Crm: CANNOT_EXECUTE_FLOW_TRIGGER : tipo di entità "Contatto" Fornisci questi dettagli all’amministratore Salesforce.
Limite superato
Il limite massimo per questa funzione è stato superato dall’utente o dall’organizzazione. ID errore: 123456</td>
      <td>Impossibile salvare il record perché non soddisfa una regola di flusso del trigger impostata nell’organizzazione Salesforce.</td>
      <td>Rivedi tutti i dettagli del messaggio di notifica e controlla i trigger di flusso nell’organizzazione Salesforce.
La documentazione di Salesforce sui trigger di flusso <a href="https://admin.salesforce.com/blog/2023/what-is-a-record-triggered-flow#:~:text=A%20record%2Dtriggered%20flow%20allows,is%20created%20and%2For%20updated"> è disponibile qui</a>.
      </td>
    </tr>
    <tr>
      <td>IMPOSSIBILE_INSERIRE_AGGIORNA_ATTIVA_ENTITÀ</td>
      <td>Errore durante l'esportazione CRM: CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY : Tipo di entità 'Lead': Codice errore CRM: CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY, Messaggio di errore CRM: System.LimitException: limite di tempo CPU Apex superato, RecordId: 0123456
      <p>
      Errore durante l'esportazione CRM: CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY : Tipo di entità 'Account': Codice errore CRM: CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY, Messaggio di errore CRM: tipo di entità non aggiornabile: Account, ID record: 0123456</td>
      <td>Gli attivatori impediscono l'aggiornamento o l'inserimento di un oggetto.
      <p>
      OPPURE
      <p>
      Autorizzazioni mancanti per l'oggetto.</td>
      <td>Esamina il codice del trigger che causa l’errore di inserimento/aggiornamento. Per ulteriori informazioni sui trigger, consulta la seguente documentazione di Salesforce:
        <ul>
          <li><a href="https://help.salesforce.com/s/articleView?id=sf.code_manage_triggers.htm&type=5">Trigger Apex</a>
          </li>
          <li><a href="https://admin.salesforce.com/blog/2023/what-is-a-record-triggered-flow#:~:text=A%20record%2Dtriggered%20flow%20allows,is%20created%20and%2For%20updated">Trigger del flusso</a>
          </li>
        </ul>
        <p>
        Fornisci tutte le autorizzazioni necessarie all'<a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">utente Marketo Measure</a>.
      </td>
    </tr>
    <tr>
      <td>DUPLICATES_DETECTED</td>
      <td>Errore durante l'esportazione CRM: DUPLICATES_DETECTED : Tipo di entità 'Contatto': Codice errore CRM: DUPLICATES_DETECTED, Messaggio di errore CRM: Stai creando un record duplicato. È consigliabile utilizzare invece un record esistente., RecordId: 0123456</td>
      <td>Il record da importare nell’organizzazione Salesforce esiste già.</td>
      <td><a href="https://help.salesforce.com/s/articleView?id=000390009&type=1">Disattivare l'impostazione "Duplicate Rule"</a> per consentire duplicati.
          <p>
          Escludi l'utente dedicato Marketo Measure da <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">regole di convalida personalizzate</a>.</td>
    </tr>
    <tr>
      <td>DUPLICATE_VALUE</td>
      <td>Errore durante l'esportazione CRM: DUPLICATE_VALUE : tipo di entità 'Lead': Codice errore CRM: DUPLICATE_VALUE, Messaggio errore CRM: valore duplicato trovato: Email_Unique__c duplica il valore nel record con ID: 123, ID record: 456</td>
      <td>Il campo importato nell’organizzazione Salesforce non consente valori duplicati.</td>
      <td>Deseleziona la <a href="https://help.salesforce.com/s/articleView?id=000390009&type=1">"Casella di controllo univoca"</a> in Salesforce.
          <p>
          Escludi l'utente dedicato Marketo Measure da <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">regole di convalida personalizzate</a>.</td>
    </tr>
    <tr>
      <td>ENTITY_IS_LOCKED</td>
      <td>Errore durante l'esportazione CRM: ENTITY_IS_LOCKED : tipo di entità 'Account': Codice errore CRM: ENTITY_IS_LOCKED, Messaggio di errore CRM: questo record è bloccato. Se devi modificarlo, contatta l’amministratore., ID record: 0123456</td>
      <td>Quando un record è in un processo di approvazione e un utente che non è l'approvatore corrente o l'amministratore di sistema tenta di modificare il record.</td>
      <td>
        <ul>
          <li>Risolvi il processo di approvazione in sospeso per quel record nell’organizzazione Salesforce.</li>
          <li>Escludi l'utente dedicato Marketo Measure da <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">regole di convalida personalizzate</a>.
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>FIELD_FILTER_VALIDATION_EXCEPTION</td>
      <td>Errore durante l'esportazione CRM: FIELD_FILTER_VALIDATION_EXCEPTION : tipo di entità 'Lead': Codice errore CRM: FIELD_FILTER_VALIDATION_EXCEPTION, Campo/i: User__C, Messaggio errore CRM: il valore non esiste o non corrisponde ai criteri del filtro. Selezionare un utente con il ruolo "Account Executive, Inside Sales"; ID record: 0123456</td>
      <td>Il record modificato non soddisfa più i filtri di ricerca definiti sull'oggetto.</td>
      <td>Verifica la presenza di filtri sull’oggetto che Marketo Measure sta tentando di modificare. Consulta <a href="https://help.salesforce.com/s/articleView?id=000384756&type=1">questo articolo di Salesforce</a> per scoprire come verificare la presenza di filtri su un oggetto.</td>
    </tr>
    <tr>
      <td>FIELD_INTEGRITY_EXCEPTION</td>
      <td>Errore durante l'esportazione CRM: FIELD_INTEGRITY_EXCEPTION : Tipo di entità 'Lead': Codice errore CRM: FIELD_INTEGRITY_EXCEPTION, Campo/i: Country, Messaggio di errore CRM: Si è verificato un problema con questo paese, anche se potrebbe sembrare corretto. Selezionare un paese dall'elenco dei paesi validi.: Country, RecordId: 0123456</td>
      <td>Il tipo previsto del record non corrisponde.</td>
      <td>Il caso più comune è che non si seguono gli standard di denominazione Stato/Paese impostati nell’organizzazione Salesforce perché i campi Stato/Paese sono stati standardizzati per accettare solo determinati valori della lista di selezione. Per risolvere questo problema, è possibile:
        <ul>
          <li>Aggiorna il record in modo che segua i valori accettati dall’organizzazione per quel campo. Contatta l’amministratore SFDC per ottenere l’elenco dei valori accettati.</li>
          <li><a href="https://help.salesforce.com/s/articleView?id=sf.admin_state_country_picklist_enable.htm&type=5">Disattivare gli elenchi di selezione Stato/Paese</a>.
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>INACTIVE_OWNER_OR_USER</td>
      <td>Errore durante l'esportazione CRM: INACTIVE_OWNER_OR_USER : tipo di entità 'Contatto': Codice errore CRM: INACTIVE_OWNER_OR_USER, Messaggio di errore CRM: operazione eseguita con l'utente inattivo [1234] come proprietario del contatto, ID record: 0123456</td>
      <td>In Marketo Measure manca l’autorizzazione "Aggiorna record con proprietari inattivi".</td>
      <td>Concedi a Marketo Measure l'autorizzazione "<a href="https://help.salesforce.com/s/articleView?id=000386699&type=1">Aggiorna record con proprietari inattivi</a>".</td>
    </tr>
    <tr>
      <td>INSUFFICIENTE_ACCESS_OR_READONLY</td>
      <td>Si è verificato un errore durante l'esportazione CRM: INSUFFICIENT_ACCESS_OR_READONLY : tipo di entità 'Account': CRM ErrorCode: INSUFFICIENT_ACCESS_OR_READONLY, CRM ErrorMessage: diritti di accesso insufficienti sull'ID oggetto: [123], RecordId: 456</td>
      <td>In Marketo Measure mancano le autorizzazioni per un oggetto o un campo oppure l’oggetto è di sola lettura.</td>
      <td>Consulta il seguente <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Experience League</a> per informazioni sulle autorizzazioni richieste da Marketo Measure.</td>
    </tr>
    <tr>
      <td>INVALID_ADOBE_ANALYTICS_CONFIGURATION</td>
      <td>Si è verificato un errore durante l’esportazione di Adobe Analytics: INVALID_ADOBE_ANALYTICS_CONFIGURATION : Errore: caricamento non consentito. Conferma lo schema dell’origine dati prima del caricamento. Id Origine Dati:1234</td>
      <td>L’integrazione di Adobe Analytics non è configurata correttamente.</td>
      <td>Per garantire la corretta configurazione, consulta i seguenti articoli della guida:
        <ul>
          <li>
            <a href="/help/marketo-measure-and-adobe/marketo-measure-integrations-with-adobe-analytics.md">Integrazioni Marketo Measure con Adobe Analytics</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/t-crs-usecase.html?lang=it">Crea un'origine attributo cliente e carica il file di dati</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>INVALID_CURRENCY_ISO_CODE</td>
      <td>Si è verificato un errore durante l’importazione dell’annuncio: INVALID_CURRENCY_ISO_CODE: la valuta XXX non è supportata da Marketo Measure.
      <p>
      Si è verificato un errore durante l’importazione dell’annuncio: INVALID_CURRENCY_ISO_CODE : La valuta XXX nell’account per 1234 non è supportata da Marketo Measure.</td>
      <td>Rilevata valuta non supportata.</td>
      <td>Nel sistema di origine indicato nella notifica (Ad, Crm, Marketo) la valuta associata al record è supportata e valida. Le valute supportate sono derivate dagli standard di valuta ISO.</td>
    </tr>
    <tr>
      <td>MISSING_BIZIBLE_CUSTOM_FIELDS_PERMISSIONS</td>
      <td>Errore durante l'esportazione CRM: MISSING_BIZIBLE_CUSTOM_FIELDS_PERMISSIONS : Tipo di entità 'Campaign': CRM ErrorCode: INVALID_FIELD_FOR_INSERT_UPDATE, Campo/i: bizible2__UniqueId__c, CRM ErrorMessage: Impossibile creare/aggiornare i campi: bizible2__UniqueId__c. Controlla le impostazioni di protezione di questo campo e verifica che sia in lettura/scrittura per il tuo profilo o set di autorizzazioni.</td>
      <td>In Marketo Measure mancano le autorizzazioni per i campi bizzarri.</td>
      <td>Sono necessarie autorizzazioni di lettura e scrittura per tutti i campi con prefisso "bizible2__". Un elenco completo di questi campi si trova <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">in questo articolo</a>.</td>
    </tr>
    <tr>
      <td>MISSING_CONVERTED_LEAD_PERMISSION</td>
      <td>Errore durante l'esportazione CRM: MISSING_CONVERTED_LEAD_PERMISSION</td>
      <td>In Marketo Measure manca l’autorizzazione Visualizza/Modifica lead convertiti</td>
      <td>Per assistenza sull'abilitazione di questa autorizzazione nel CRM, fare riferimento al seguente Experience League di documento<br/>
          <a href="/help/marketo-measure-salesforce-reporting/additional-functionality/enabling-the-permission-to-edit-converted-leads.md">Abilitazione dell'autorizzazione per la modifica di lead convertiti</a></td>
    </tr>
    <tr>
      <td>CAMPO_MANCANTE_AUTORIZZAZIONE_LETTURA</td>
      <td>Errore durante l'importazione CRM: MISSING_FIELD_READ_PERMISSION : Tipo di entità 'Event': INVALID_FIELD:<br/>
    SystemModstamp,IsDeleted,WhoId,bizible2__Bizible_Touchpoint_Date__c</td>
      <td>In Marketo Measure mancano le autorizzazioni di lettura per un campo obbligatorio.</td>
      <td>Per informazioni sulle autorizzazioni richieste da Marketo Measure, consulta i seguenti articoli della guida:
        <ul>
          <li><a href="/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/marketo-measure-dynamics-schema.md">Dynamics</a>
          </li>
          <li><a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Salesforce</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>MISSING_ISREPLICATEABLE_PERMISSION</td>
      <td>Si è verificato un errore durante l’importazione Crm: MISSING_ISREPLICATEABLE_PERMISSION : Autorizzazione IsReplicateable mancante in Campaign</td>
      <td>Questa autorizzazione è necessaria per gli oggetti Salesforce affinché possiamo mantenere sincronizzati Marketo Measure e Salesforce.</td>
      <td>Contatta il supporto Salesforce per assistenza nell’impostazione delle autorizzazioni replicabili sugli oggetti.</td>
    </tr>
    <tr>
      <td>AUTORIZZAZIONE_LETTURA_OGGETTO_MANCANTE</td>
      <td>Errore durante l'importazione CRM: MISSING_OBJECT_READ_PERMISSION : tipo di entità Campaign': CRM ErrorCode: MISSING_PERMISSION</td>
      <td>In Marketo Measure mancano le autorizzazioni di lettura per un oggetto richiesto.</td>
      <td rowspan="2">Per informazioni sulle autorizzazioni richieste da Marketo Measure, consulta i seguenti articoli della guida:
          <ul>
            <li><a href="/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/marketo-measure-dynamics-schema.md">Dynamics</a>
            </li>
            <li><a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Salesforce</a>
            </li>
          </ul>
      </td>
    </tr>
    <tr>
      <td>MANCA_OBJECT_WRITE_PERMISSION</td>
      <td>Errore durante l'esportazione CRM: MISSING_OBJECT_WRITE_PERMISSION : Tipo di entità 'bizible2_Bizible_Attribution_Touchpoint': Codice errore CRM: MISSING_PERMISSION</td>
      <td>In Marketo Measure mancano le autorizzazioni di scrittura per un oggetto richiesto.</td>
    </tr>
    <tr>
      <td>AUTORIZZAZIONI_OGGETTO_RECORD_MANCANTI</td>
      <td>Errore durante l'esportazione CRM: MISSING_RECORD_OBJECT_PERMISSIONS : Tipo di entità 'bizible2__Bizible_Touchpoint__c': Codice errore CRM: INSUFFICIENT_ACCESS_ON_CROSS_REFERENCE_ENTITY, Campo/i: Account, Messaggio di errore CRM: diritti di accesso insufficienti sull'ID riferimento incrociato: 0123456</td>
      <td>Autorizzazioni mancanti per Marketo Measure.</td>
      <td>Questo errore è dovuto a diversi motivi specifici per l’organizzazione Salesforce. Di seguito sono riportati alcuni passaggi comuni per la risoluzione dei problemi che possono risolvere il problema:
        <ul>
          <li>Rivedi tutte le autorizzazioni necessarie per ogni <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">oggetto e campo</a>.</li>
          <li>Escludi l'utente dedicato Marketo Measure da <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">regole di convalida personalizzate</a>.</li>
          <li>Concedi autorizzazioni "<a href="https://developer.salesforce.com/docs/atlas.en-us.securityImplGuide.meta/securityImplGuide/users_profiles_view_all_mod_all.htm">Modifica tutte</a>" a Marketo Measure.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>NULL_EMPTY_CURRENCY_ISO_CODE</td>
      <td>
        <p>
          Errore durante l'importazione di CRM: NULL_EMPTY_CURRENCY_ISO_CODE: il codice ISO della valuta è NULL o vuoto quando MultiCurrency è abilitato per RecordId 1234
      </td>
      <td>La valuta deve essere un codice valuta ISO supportato.</td>
      <td>Nel sistema di origine indicato nella notifica (Ad, Crm, Marketo) la valuta associata al record è supportata e valida. Le valute supportate sono derivate dagli standard di valuta ISO.</td>
    </tr>
    <tr>
      <td>OPERATION_TOO_LARGE</td>
      <td>Errore durante l'importazione di CRM: OPERATION_TOO_LARGE : per eseguire correttamente la query sulle attività è necessaria l'autorizzazione 'Visualizza tutti i dati'.</td>
      <td>Le impostazioni di gestione delle relazioni con i clienti non consentono a Marketo Measure di eseguire query su un set di dati sufficientemente grande</td>
      <td>Concedere a Marketo Measure le autorizzazioni 'Visualizza tutti i dati' per l'oggetto designato.
      <p>
      Ulteriori informazioni sull'autorizzazione 'Visualizza tutti i dati' <a href="https://developer.salesforce.com/docs/atlas.en-us.securityImplGuide.meta/securityImplGuide/users_profiles_view_all_mod_all.htm">sono disponibili qui</a>.</td>
    </tr>
    <tr>
      <td>RECORD_NONCOMPLIANT_WITH_VALIDATION_RULES</td>
      <td>Errore durante l'esportazione CRM: RECORD_NONCOMPLIANT_WITH_VALIDATION_RULES : tipo di entità 'Lead': CRM ErrorCode: FIELD_CUSTOM_VALIDATION_EXCEPTION, campi: Lead_Status_Reason__c, CRM ErrorMessage: È necessario selezionare il motivo dello stato del lead, ID record: 0123456</td>
      <td>Il record in fase di aggiornamento non soddisfa una regola di convalida impostata nell’organizzazione Salesforce.</td>
      <td>Escludi l'utente dedicato Marketo Measure da <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">regole di convalida personalizzate</a>.
      <p>
      Aggiorna le <a href="https://help.salesforce.com/s/articleView?id=sf.fields_about_field_validation.htm&type=5">regole di convalida</a>.</td>
    </tr>
    <tr>
      <td>RESTRICT_PICKLIST_VALUES_ENABLED</td>
      <td>Errore durante l'esportazione CRM: RESTRICT_PICKLIST_VALUES_ENABLED : Tipo di entità 'Campaign': CRM ErrorCode: INVALID_OR_NULL_FOR_RESTRICTED_PICKLIST, Campo/i: Areas_of_Interest__c, CRM ErrorMessage: valore non valido per il campo dell'elenco a discesa con restrizioni: Sconosciuto</td>
      <td>Quando "Limita elenco di selezione ai valori definiti nel set di valori" è abilitato nella configurazione del campo elenco di selezione o il valore inserito nel campo non è disponibile nel tipo di record dell’oggetto.</td>
      <td>Disattiva l’impostazione Limita elenco a discesa nell’organizzazione Salesforce.
          <p>
          Escludi l'utente dedicato Marketo Measure da <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">regole di convalida personalizzate</a>.
      </td>
    </tr>
    <tr>
      <td>CAMPO_OBBLIGATORIO_MANCANTE</td>
      <td>Errore durante l'esportazione CRM: MISSING_REQUIRED_FIELD : Tipo di entità 'Lead': Codice errore CRM: REQUIRED_FIELD_MISSING, Campo/i: Product_Type__c, Messaggio di errore CRM: Mancano campi obbligatori: [Product_Type__c], RecordId: 0123456</td>
      <td>Quando una regola di convalida specifica campi obbligatori sugli oggetti.</td>
      <td>Escludi l'utente dedicato Marketo Measure da <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">regole di convalida personalizzate</a>.
      </td>
    </tr>
    <tr>
      <td>ECCEZIONE_SCONOSCIUTA</td>
      <td>Errore durante l'esportazione CRM: UNKNOWN_EXCEPTION : Tipo di entità 'Contatto': Codice errore CRM: UNKNOWN_EXCEPTION, Messaggio errore CRM: gli utenti del portale non possono possedere account partner, ID record: 0123456</td>
      <td>Eccezione non gestita in Salesforce.</td>
      <td>Se il problema persiste, crea un caso con Salesforce e copia i valori numerici nel messaggio di errore.</td>
    </tr>
    <tr>
      <td>UNSUPPORTED_CRM_PACKAGE_VERSION</td>
      <td>Errore durante l'importazione CRM: UNSUPPORTED_CRM_PACKAGE_VERSION : Aggiorna il pacchetto CRM</td>
      <td>Il pacchetto corrente rilevato non è più supportato.</td>
      <td>Aggiorna il pacchetto alla versione più recente:
        <ul>
          <li><a href="/help/configuration-and-setup/marketo-measure-and-salesforce/best-practices-for-marketo-measure-crm-package.md">Best practice</a>
          </li>
          <li><a href="/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/microsoft-dynamics-crm-installation-guide.md">Dynamics</a>
          </li>
          <li><a href="/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md">Salesforce</a>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
