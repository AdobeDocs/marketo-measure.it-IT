---
unique-page-id: 34406495
description: Porzioni Ops Marketing - [!DNL Marketo Measure] - Documentazione del prodotto
title: Porzioni Ops di marketing
exl-id: e7978a79-6f6e-4bfd-9962-b35b7d46a9ac
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---

# Porzioni Ops di marketing {#marketing-ops-tiles}

Marketing Ops consente di convalidare e diagnosticare [!DNL Marketo Measure] dati con visibilità completa nei singoli punti di contatto per lead, contatti, account, campagne e opportunità.

<table> 
 <colgroup> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td><br></td> 
   <td><p><strong>ID account</strong></p></td> 
   <td><p><strong>Nome account</strong></p></td> 
   <td><p><strong>ID Opp</strong></p></td> 
   <td><p><strong>Nome Opp</strong></p></td> 
   <td><p><strong>ID lead o contatto</strong></p></td> 
   <td><p><strong>Indirizzo e-mail lead o contatto</strong></p></td> 
   <td><p><strong>ID campagna</strong></p></td> 
   <td><p><strong>Opp Won</strong></p></td> 
   <td><p><strong>Data creazione Opp</strong></p></td> 
   <td><p><strong>Data chiusura Opp</strong></p></td> 
   <td><p><strong>Data punto di contatto</strong></p></td> 
   <td><p><strong>Modello di attribuzione</strong></p></td> 
  </tr> 
  <tr> 
   <td><p><strong>Account</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><br></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Opportunità</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><br></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Contatti</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Lead</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Campagne</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><br></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
 </tbody> 
</table>

## Riquadro account {#account-tile}

![](assets/one-1.png)

Visualizza i seguenti dati relativi ai conti specificati.

**Gli account devono disporre di dati punto di contatto (applicabili solo se ABM è abilitato)**

- ID account: ID account in CRM

- Nome account: Nome account in CRM

Data creazione: Data di creazione dell&#39;account nel CRM

* Drill-down: Vedere Data creazione per ora, minuto, ora

Sito Web: Valore trovato nel campo Sito Web sull&#39;account

- Livello di coinvolgimento: Punteggio di coinvolgimento predittivo (PES) popolato da [!DNL Marketo Measure]^1

-Opportunità: Numero di opportunità connesse all&#39;account

* Drill-down: Visualizza i dettagli delle opportunità associate

-Contatti: Numero di contatti elencati in questo account

* Drill-down: Visualizza i dettagli dei contatti associati

-Lead: Numero di lead mappati a questo account tramite la mappatura dei lead verso account^1

* Drill-down: Visualizza i dettagli dei lead mappati all’account

-Punti di contatto di attribuzione: Numero di punti di contatto dell’attribuzione dell’acquirente per l’account

* Drill-down: Consulta Dettagli punto di contatto di attribuzione dell’acquirente (ID, E-mail, data punto di contatto, nome account, campagna, canale, canale secondario, tipo di contatto marketing, modello di attribuzione)

-Punti di contatto: Numero di punti di contatto presenti nei contatti dell&#39;account^2

* Drill-down: Consulta Punti di contatto sui dettagli del punto di contatto dell’account (ID, E-mail, data punto di contatto, nome account, campagna, canale, canale secondario, tipo di contatto marketing)

>[!NOTE]
>
>Se disponi di ABM, vengono visualizzati i punti di contatto relativi ai lead mappati tramite Mappatura lead su account.

## Riquadro opportunità {#opportunity-tile}

![](assets/two-1.png)

Visualizza i seguenti dati relativi alle opportunità specificate.

-ID opportunità: ID opportunità in CRM

-Nome opportunità: Nome opportunità in CRM

- Nome account: Nome account associato all’opportunità

Data creazione: Data di creazione dell&#39;opportunità nel CRM

Drill-down: Vedere Data creazione per ora, minuto, ora

-Chiudi data: Data di chiusura dell&#39;opportunità nel CRM

Drill-down: Vedere Chiudi data per ora, minuto, ora

-Importo: Importo totale dell&#39;opportunità

-Contatti: Numero di contatti associati all&#39;opportunità

Drill-down: Visualizza i dettagli dei contatti associati

-Punti di contatto di attribuzione: Numero di punti di contatto relativi all’attribuzione dell’acquirente

Drill-down: Consulta Dettagli punto di contatto di attribuzione dell’acquirente (ID, E-mail, data punto di contatto, nome account, campagna, canale, canale secondario, tipo di contatto marketing, modello di attribuzione)

## Riquadro contatti {#contacts-tile}

![](assets/three-1.png)

Visualizza i seguenti dati relativi ai contatti specificati.

-ID contatto: ID contatto in CRM

-Email: Indirizzo e-mail del record di contatto

Data creazione: Data di creazione del contatto nel CRM

* Drill-down: Vedere Data creazione per ora, minuto, ora

- Nome account: Nome account associato al contatto

-Punti di contatto di attribuzione: Numero di punti di contatto per l’attribuzione dell’acquirente per il contatto

* Drill-down: Consulta Dettagli punto di contatto di attribuzione dell’acquirente (ID, E-mail, data punto di contatto, nome account, campagna, canale, canale secondario, tipo di contatto marketing, modello di attribuzione)

-Punti di contatto: Numero di punti di contatto dell&#39;acquirente per il contatto

* Drill-down: Consulta Contatti sui dettagli del punto di contatto dell’account (ID, E-mail, data punto di contatto, nome account, campagna, canale, canale secondario, tipo di contatto marketing)

## Riquadro lead {#leads-tile}

![](assets/four-1.png)

Visualizza i dati seguenti relativi ai lead specificati.

ID lead: ID lead in CRM

-Email: Indirizzo e-mail record lead

Data creazione: Quando il lead è stato creato nel CRM

* Drill-down: Vedere Data creazione per ora, minuto, ora

-Azienda (dal lead): Società elencata nel record nel CRM popolato dal cliente

- Nome account: Nome account [!DNL Marketo Measure] si popola in base alla mappatura lead su account

-Punti di contatto: Numero di punti di contatto associati al lead

* Drill-down: Consulta Contatti sui dettagli del punto di contatto dell’account (ID, E-mail, data punto di contatto, nome account, campagna, canale, canale secondario, tipo di contatto marketing)

## Riquadro Campagne {#campaigns-tile}

![](assets/five-1.png)

Visualizza i seguenti dati relativi alle campagne specificate.

ID campagna: ID campagna in CRM

-Nome campagna: Nome campagna in CRM

-Spesa campagna: La spesa [!DNL Marketo Measure] è stato registrato come associato alla campagna

Modello di attribuzione: Verrà mostrata l’attribuzione appropriata in base al modello selezionato

-Punti di contatto di attribuzione: Numero di punti di contatto di attribuzione dell’acquirente associati alle campagne

* Drill-down: Consulta Dettagli punto di contatto di attribuzione dell’acquirente (ID, E-mail, data punto di contatto, nome account, campagna, canale, canale secondario, tipo di contatto marketing, modello di attribuzione)

-Punti di contatto: Numero di punti di contatto associati alle campagne

* Drill-down: Consulta Contatti sui dettagli del punto di contatto dell’account (ID, E-mail, data punto di contatto, nome account, campagna, canale, canale secondario, tipo di contatto marketing)
