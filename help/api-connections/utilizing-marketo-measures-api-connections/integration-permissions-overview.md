---
description: Panoramica delle autorizzazioni di integrazione - [!DNL Marketo Measure] - Documentazione del prodotto
title: Panoramica delle autorizzazioni di integrazione
hide: true
hidefromtoc: true
feature: APIs, Integration
source-git-commit: 9196877384140d60a22012b43ea960017528f4d5
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 3%

---

# Panoramica delle autorizzazioni di integrazione {#integration-permissions-overview}

Questa guida descrive le autorizzazioni necessarie per un’integrazione perfetta con Marketo Measure, garantendo che ogni integrazione funzioni in modo efficace e senza problemi.

<table>
<thead>
  <tr>
    <th style="width:10%">Integrazione</th>
    <th style="width:20%">Tipo di dati
    <li>Dati interazione web</li>
    <li>Dati di sistema B2B</li>
    <li>Dati della piattaforma dell’annuncio</li></th>
    <th style="width:30%">Cosa tracciamo</th>
    <th style="width:40%">Requisiti delle autorizzazioni</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Salesforce</td>
    <td>Dati di sistema B2B    
</td>
    <td>Marketo Measure sta tracciando:
    <br>
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
<br>
I punti di contatto creati e altri dati vengono scritti in campi bizzarri personalizzati in Account, Campaign, CampaignMember, Case, Contact, Lead e Opportunity.</td>
    <td><b>Autorizzazioni utente connesso Salesforce (obbligatorio)</b>
    <br>
    <b>Set Di Autorizzazioni Di Amministratore Marketo Measure Per Utente Dedicato:</b> Consenti all'amministratore SFDC di eseguire operazioni CRUD sul mercato per misurare gli oggetti.
    <br>
    <b>Visualizza e modifica set di autorizzazioni lead convertiti:</b> Questo consente a Marketo Measure di decorare i lead dopo che sono stati convertiti in contatti.
    <br>
    <b>Casella di selezione utente marketing Salesforce:</b> La casella di controllo Utente marketing consente agli utenti di creare campagne e utilizzare l’Importazione guidata campagne.
    <br>
    <b>Utente Marketo Measure Standard:</b> Consente a un utente di leggere record da oggetti Marketo Measure.
    <p>
    <b>Autorizzazioni per i campi Salesforce Standard</b>
    <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Oggetti e accesso standard Salesforce</a>
    <p>
    <b>Autorizzazioni campo personalizzato Salesforce</b>
    <br>
    Forniamo le impostazioni della funzione per contenere i campi personalizzati di Salesforce che i clienti possono utilizzare. Se queste impostazioni di funzionalità sono definite, è necessario l’accesso in LETTURA a ciascuno dei campi Salesforce salvati nell’impostazione di funzionalità (ad esempio, se il valore dell’impostazione CustomLeadSourceField è uguale a "LeadSource__c", è necessario l’accesso in LETTURA a questo campo).
    </td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>
