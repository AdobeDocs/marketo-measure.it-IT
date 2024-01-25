---
description: Notifiche di errore - [!DNL Marketo Measure] - Documentazione del prodotto
title: Notifiche di errore
feature: Fundamentals
source-git-commit: 05ec40d3fa1fe1076eeaa755a9244b614ac5fda6
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Notifiche di errore {#error-notifications}

Di seguito è riportato un elenco di errori che potresti ricevere tramite notifica in-app o e-mail. Se ricevi uno di questi, segui i rispettivi passaggi per la risoluzione dei problemi. Se questi passaggi non risolvono il problema, contatta [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support).

<table>
  <tbody>
    <tr>
      <th>Codice di errore</th>
      <th>Esempio di notifica</th>
      <th>Descrizione</th>
      <th>Passaggi per la risoluzione dei problemi</th>
    </tr>
    <tr>
      <td>API_DISABLED</td>
      <td>Errore durante l'importazione CRM : API_DISABLED : le chiamate API sono state disabilitate per questo utente</td>
      <td>L’autorizzazione API è stata disabilitata per l’utente Marketo Measure.</td>
      <td>Consulta la seguente documentazione di Salesforce su <a href="https://help.salesforce.com/s/articleView?id=sf.branded_apps_commun_api_permset.htm&amp;type=5">come abilitare l’accesso API</a>.</td>
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
            <li>Passa a Impostazioni → CRM → Generale</li>
            <li>Aggiornare il limite API CRM giornaliero<br/>
              <ul>
                <li><b>Nota</b>: il valore predefinito è 100.000</li>
              </ul>
            </li>
          </ul>
          <p>
           <img src="assets/error-notifications-1.png">
          </p>
      </td>
    </tr>
    <tr>
      <td>INVALID_ADOBE_ANALYTICS_CONFIGURATION</td>
      <td>Si è verificato un errore durante l’esportazione di Adobe Analytics: INVALID_ADOBE_ANALYTICS_CONFIGURATION : Errore: caricamento non consentito. Conferma lo schema dell’origine dati prima del caricamento. Id Origine Dati:1234</td>
      <td>L’integrazione di Adobe Analytics non è configurata correttamente.</td>
      <td>Per garantire la corretta configurazione, consulta i seguenti articoli della guida:
        <ul>
          <li>
            <a href="/help/marketo-measure-and-adobe/marketo-measure-integrations-with-adobe-analytics.md">Integrazioni di Marketo Measure con Adobe Analytics</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/t-crs-usecase.html">Creare un’origine di attributi cliente e caricare il file di dati</a>
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
      <td>Nel sistema di origine indicato nella notifica (Ad, Crm, Marketo) assicurati che la valuta associata al record abbia una valuta supportata e valida. Le valute supportate sono derivate dagli standard di valuta ISO.</td>
    </tr>
    <tr>
      <td>MISSING_CONVERTED_LEAD_PERMISSION</td>
      <td>Errore durante l'esportazione CRM: MISSING_CONVERTED_LEAD_PERMISSION</td>
      <td>In Marketo Measure manca l’autorizzazione Visualizza/Modifica lead convertiti</td>
      <td>Per assistenza sull’abilitazione di questa autorizzazione nel CRM, consulta il seguente documento di Experience League<br/>
          <a href="/help/marketo-measure-salesforce-reporting/additional-functionality/enabling-the-permission-to-edit-converted-leads.md">Abilitazione dell’autorizzazione per la modifica di lead convertiti</a></td>
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
      <td>NULL_EMPTY_CURRENCY_ISO_CODE</td>
      <td>
        <p>
          Errore durante l'importazione di CRM: NULL_EMPTY_CURRENCY_ISO_CODE: il codice ISO della valuta è NULL o vuoto quando MultiCurrency è abilitato per RecordId 1234
      </td>
      <td>La valuta deve essere un codice valuta ISO supportato.</td>
      <td>Nel sistema di origine indicato nella notifica (Ad, Crm, Marketo) assicurati che la valuta associata al record abbia una valuta supportata e valida. Le valute supportate sono derivate dagli standard di valuta ISO.</td>
    </tr>
    <tr>
      <td>OPERATION_TOO_LARGE</td>
      <td>Errore durante l'importazione di CRM: OPERATION_TOO_LARGE : per eseguire correttamente la query sulle attività è necessaria l'autorizzazione 'Visualizza tutti i dati'.</td>
      <td>Le impostazioni di gestione delle relazioni con i clienti non consentono a Marketo Measure di eseguire query su un set di dati sufficientemente grande</td>
      <td>Concedere a Marketo Measure le autorizzazioni 'Visualizza tutti i dati' per l'oggetto designato.
      <p>
      Ulteriori informazioni sull’autorizzazione "Visualizza tutti i dati" <a href="https://developer.salesforce.com/docs/atlas.en-us.securityImplGuide.meta/securityImplGuide/users_profiles_view_all_mod_all.htm">si trova qui</a>.</td>
    </tr>
    <tr>
      <td>UNSUPPORTED_CRM_PACKAGE_VERSION</td>
      <td>Errore durante l'importazione CRM: UNSUPPORTED_CRM_PACKAGE_VERSION : Aggiornare il pacchetto CRM</td>
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
