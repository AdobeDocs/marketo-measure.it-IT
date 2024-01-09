---
description: Panoramica delle autorizzazioni di integrazione - [!DNL Marketo Measure] - Documentazione del prodotto
title: Panoramica delle autorizzazioni di integrazione
hide: true
hidefromtoc: true
feature: APIs, Integration
source-git-commit: 3d4ee7c71ed241c8e3885b4db57168f753dcdf65
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 2%

---

# Panoramica delle autorizzazioni di integrazione {#integration-permissions-overview}

Questa guida descrive le autorizzazioni necessarie per un’integrazione perfetta con Marketo Measure, garantendo che ogni integrazione funzioni in modo efficace e senza problemi.

<table>
<thead>
  <tr>
    <th style="width:10%">Integrazione</th>
    <th style="width:25%">Tipo di dati
    <li>Dati interazione web</li>
    <li>Dati di sistema B2B</li>
    <li>Dati della piattaforma dell’annuncio</li></th>
    <th style="width:25%">Cosa tracciamo</th>
    <th style="width:40%">Requisiti delle autorizzazioni</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Salesforce</td>
    <td>Dati di sistema B2B    
</td>
    <td>Marketo Measure sta tracciando:
    <p>
    <li>Account</li>
    <li>Campaign</li>
    <li>MembroCampagna</li>
    <li>Contatto</li>
    <li>CurrencyConversionRange</li>
    <li>CurrencyStatus</li>
    <li>Eventi</li>
    <li>Cronologia campi (lead, contatto e opportunità)</li>
    <li>Lead</li>
    <li>Opportunità</li>
    <li>OpportunityContactRole</li>
    <li>CronologiaOpportunità</li>
    <li>Attività</li>
<p>
I punti di contatto creati e altri dati vengono scritti in campi bizzarri personalizzati in Account, Campaign, CampaignMember, Case, Contact, Lead e Opportunity.</td>
    <td><b>Autorizzazioni utente connesso Salesforce (obbligatorio)</b>
    <p>
    <b>Set Di Autorizzazioni Di Amministratore Marketo Measure Per Utente Dedicato:</b> Consenti all'amministratore SFDC di eseguire operazioni CRUD sul mercato per misurare gli oggetti.
    <br>
    <b>Visualizza e modifica set di autorizzazioni lead convertiti:</b> Questo consente a Marketo Measure di decorare i lead dopo che sono stati convertiti in contatti.
    <br>
    <b>Casella di selezione utente marketing Salesforce:</b> La casella di controllo Utente marketing consente agli utenti di creare campagne e utilizzare l’Importazione guidata campagne.
    <br>
    <b>Utente Marketo Measure Standard:</b> Consente a un utente di leggere record da oggetti Marketo Measure.
    <p>
    <b>Autorizzazioni per i campi Salesforce Standard</b>
    <br>
    <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Oggetti e accesso standard Salesforce</a>
    <p>
    <b>Autorizzazioni campo personalizzato Salesforce</b>
    <br>
    Forniamo le impostazioni della funzione per contenere i campi personalizzati di Salesforce che i clienti possono utilizzare. Se queste impostazioni di funzionalità sono definite, è necessario l’accesso in LETTURA a ciascuno dei campi Salesforce salvati nell’impostazione di funzionalità (ad esempio, se il valore dell’impostazione CustomLeadSourceField è uguale a "LeadSource__c", è necessario l’accesso in LETTURA a questo campo).
    </td>
  </tr>
  <tr>
    <td>Dynamics</td>
    <td>Dati di sistema B2B</td>
    <td>Marketo Measure sta tracciando:
    <p>
    <li>Account
<li>ActivityParty
<li>ActivityPointer
<li>Campaign
<li>CampaignItem (Elenco campagne nel nostro sistema)
<li>CampaignResponse (CampaignMember nel nostro sistema)
<li>Contatto
<li>Lead
<li>Elenco (MarketingList nel nostro sistema)
<li>ListMember (MarketingListMember nel nostro sistema)
<li>Opportunità
<li>Organizzazione
<li>TransactionCurrency (CurrencyConversionRange e CurrencyStatus nel nostro sistema)
<li>Appuntamento, Attività campagna, E-mail, Fax, IncidentResolution, Lettera, PhoneCall, RicorrenteAppuntamentoMaster, AppuntamentoServizio, Attività
<li>bizible2_bizible_abtest
<li>bizible2_bizible_attribution_touchpoint
<li>bizible2_bizible_event
<li>bizible2_bizible_history
<li>bizible2_bizible_touchpoint
<p>
I punti di contatto creati e altri dati vengono scritti in campi bizzarri personalizzati su account, campagna, risposta campagna, contatto, lead, elenco, opportunità e chiamata</td>
    <td><b>Autorizzazioni utente di Marketo Measure</b>
<br>
È consigliabile creare un utente Marketo Measure dedicato all’interno di Dynamics per esportare e importare dati tramite al fine di evitare problemi con altri utenti nel CRM. Prendi nota del nome utente e della password, nonché dell’URL dell’endpoint, in quanto verranno utilizzati durante la creazione dell’account Marketo Measure.
<p>
<b>Ruoli di sicurezza</b>
<br>
Se l’organizzazione utilizza i ruoli di sicurezza di Dynamics, assicurati che l’utente connesso o l’utente Marketo Measure dedicato disponga di autorizzazioni di lettura/scrittura sufficienti per le entità richieste.
<br>
I ruoli di sicurezza si trovano qui: Impostazioni &gt; Sicurezza &gt; Ruoli di sicurezza
<br>
Per le entità personalizzate Marketo Measure, saranno necessarie autorizzazioni complete per tutte le nostre entità.
<p>
<b>Autorizzazioni campo Dynamics Standard</b>
<br>
<a href="/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/marketo-measure-dynamics-schema.md">Schema Marketo Measure Dynamics</a>
<p>
<b>Autorizzazioni campo personalizzato Dynamics</b>
<br>
È necessario l’accesso in LETTURA per qualsiasi campo nell’entità lead o contatto che il cliente desidera utilizzare per le regole personalizzate di eliminazione/rimozione delle impostazioni dei punti di contatto.
<br>
È necessario l’accesso in LETTURA per qualsiasi campo dell’entità Lead o Opportunità che il cliente desidera utilizzare per le regole del segmento o la mappatura dello stadio.
<br>
È necessario l’accesso in LETTURA per qualsiasi campo delle entità Campaign, CampaignResponse ed List che il cliente desidera utilizzare per la sincronizzazione dei membri di Campaign/MarketingList.
</td>
  </tr>
  <tr>
    <td>Facebook</td>
    <td>Dati della piattaforma dell’annuncio</td>
    <td>Dell si integra con Facebook per:
<p>
<li>Importare dati degli annunci dei clienti</li>
<li>Importa dati costo annunci cliente</li>
<li>Aggiornare gli annunci del client aggiungendo i parametri URL</li>
<p>
Marketo Measure tiene traccia di account, campagne, gruppi di annunci, annunci, ID filtro e URL.</td>
    <td><li>L’autorizzazione ads_management è necessaria per creare campagne, gestire annunci o recuperare metriche di annunci.</li>
<li>L’autorizzazione e-mail è necessaria per consentire agli utenti di accedere alla posta Facebook.</li>
<p>
<b>Ambiti</b>
<br>
<a href="https://developers.facebook.com/docs/permissions/reference/ads_management/">ads_management</a>
<br>
<li>Crea campagne a livello di programmazione, gestisci annunci e recupera metriche.</li>
<li>Creare strumenti di gestione degli annunci che forniscano soluzioni innovative e valore differenziato per gli inserzionisti.</li>
<br>
<br>
<a href="https://developers.facebook.com/docs/permissions/reference/email">email</a>
<br>
<li>Comunicare con le persone e consentire loro di accedere all’app con l’indirizzo e-mail associato al loro profilo Facebook.</li></td>
  </tr>
  <tr>
    <td>LinkedIn</td>
    <td>Dati della piattaforma dell’annuncio
    <p>
    Dati di sistema B2B (dati del modulo di generazione del lead, inclusi moduli e invii, classificati come attività di gestione delle relazioni con i clienti).</td>
    <td>Marketo Measure tiene traccia di campagne, creatività e dati sui costi di LinkedIn Ads, nonché delle risposte e dei Forms della generazione di lead. In base ai dati importati, possiamo generare punti di contatto LinkedIn e associare le risposte dei moduli dei lead ai lead per i clienti.</td>
    <td><li>È necessario il ruolo di Campaign Manager o Account Manager per consentire a Marketo Measure di scaricare i dati sui costi. (Riga ambito 1)</li>
    <br>
    <li>Forms Per consentire a Marketo Measure di accedere ai dati dei moduli di generazione lead è necessario un ruolo di amministratore privilegiato (ruolo di amministratore pagina, riga 2 ambiti) o un ruolo di amministratore responsabile di generazione (ruolo di amministratore media a pagamento, riga 3 ambiti)</li>
    <br>
    <li>Marketo Measure Per poter manipolare l’assegnazione automatica di tag è necessario un amministratore privilegiato (ruolo di amministratore pagina, riga 2 ambiti) o un poster di contenuti sponsorizzati (ruolo di amministratore dei contenuti multimediali a pagamento, riga 3 ambiti)</li>
    <p>
    <b>Ambiti</b>
    <br>
    <a href="https://www.linkedin.com/campaignmanager/accounts">Configurare il ruolo utente nel portale (è necessario accedere all'account LinkedIn)</a> - <a href="https://www.linkedin.com/help/lms/answer/a425731/user-roles-and-functions-in-campaign-manager">Panoramica sui ruoli utente</a>: ruolo utente, visualizzazione e gestione delle autorizzazioni utente, assegnazione di ruoli come responsabile account o responsabile campagna
    <p>
    <a href="https://www.linkedin.com/help/linkedin/answer/a570172/add-or-remove-admins-on-your-showcase-page?lang=en">Imposta ruolo amministratore pagina - <a href="https://www.linkedin.com/help/linkedin/answer/a541981/linkedin-page-admin-roles-overview">Definizioni dei ruoli di amministratore pagina</a>: ruolo amministratore pagina, nella pagina di amministrazione desiderata
    <p>
    <a href="https://www.linkedin.com/help/linkedin/answer/a570172/add-or-remove-admins-on-your-showcase-page?lang=en">Imposta ruolo amministratore media a pagamento (cerca amministratore media a pagamento) - <a href="https://www.linkedin.com/help/linkedin/answer/a554540">Definizioni dell’amministratore dei contenuti multimediali a pagamento</a>: Ruoli di amministratore di contenuti multimediali a pagamento</td>
  </tr>
  <tr>
    <td>Doppio clic</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>AdWords</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Bing</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Marketo Engage</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe Analytics</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Javascript Bizible</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>
