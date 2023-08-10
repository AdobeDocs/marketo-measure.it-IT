---
unique-page-id: 35586105
description: Percorso di coinvolgimento - [!DNL Marketo Measure] - Documentazione del prodotto
title: Percorso di coinvolgimento
exl-id: 104d803f-9f40-4ab6-872d-6432f8c087e9
feature: Reporting
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 0%

---

# Percorso di coinvolgimento {#engagement-path}

Il percorso di coinvolgimento consente di visualizzare una panoramica completa degli impegni relativi a lead, contatti, account e opportunità, dal primo contatto fino alla chiusura.

![](assets/one-2.png)

## Descrizione sezione {#tile-description}

**Tipo evento:** Il tipo di punto di contatto (Sessione, Campagna CRM, Evento CRM, Attività CRM, Impression)

**Posizione punto di contatto acquirente:** Punto di contatto Posizione del lead/contatto

**Posizione punto di contatto di attribuzione acquirente:** Punto di contatto di attribuzione acquirente Posizione dell&#39;opportunità

**Data punto di contatto:** Per le origini online: data e ora in cui si è verificato il coinvolgimento. Per gli eventi offline: data e ora impostate nella campagna Salesforce. Per le attività punto di contatto: nella configurazione delle attività viene fatto riferimento al campo data punto di contatto

**E-mail:** L’e-mail associata al coinvolgimento

**Tipo di contatto marketing:** Tipo di coinvolgimento (visita web, modulo web, chat web, gestione delle relazioni con i clienti, tipi di attività)

**Canale:** Canale di marketing che ha guidato il coinvolgimento

**Media:** Canale di coinvolgimento

* Se il coinvolgimento proviene da una piattaforma collegata API (Adwords/BingAds), il supporto sarà CPC
* Se la pagina di destinazione del coinvolgimento contiene utm_medium, verrà analizzato
* Se il coinvolgimento proviene dalla campagna CRM, il supporto proviene dal campo &quot;Tipo&quot; della campagna CRM

**Origine Web:** In questa colonna verrà visualizzata l&#39;origine del coinvolgimento

* Se il coinvolgimento proviene da una piattaforma connessa all’API, il nome della piattaforma dell’annuncio verrà visualizzato nella sorgente web
* Se il punto di contatto proviene da una ricerca organica, in questo campo viene visualizzato il nome del motore di ricerca
* Se non #1 o #2 e il valore utm_source è presente nell’URL della pagina di destinazione per il punto di contatto, tale valore verrà visualizzato qui
* Se non è #1 o #2 e non è presente alcun valore utm_source, qui verrà visualizzato il dominio principale dell’URL di riferimento.
* Se non si verifica alcuna delle condizioni precedenti, verrà visualizzato Web Direct o Web

**Prima interazione con la persona:** In questa colonna verrà visualizzato Sì o No se il punto di contatto è stata la prima interazione con i singoli utenti

**Ricavi attribuiti:** In questa colonna verranno visualizzati i ricavi attribuiti a quel punto di contatto in base al modello di attribuzione selezionato

## Descrizione filtro {#filter-description}

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th>Nome filtro</th> 
   <th>Descrizione</th> 
  </tr> 
  <tr> 
   <td><p>Nome/ID account</p></td> 
   <td><p>Consente l’inserimento di più valori aggiungendo filtri tramite il segno più "+" a destra. Più valori di filtro avranno una relazione "o", il che significa che le sezioni mostreranno i risultati per entrambi i valori di filtro. Se uno dei valori del filtro non è valido, il dashboard non produrrà risultati per il valore non valido, ma continuerà a filtrare in base ai valori del filtro validi. Senza distinzione tra maiuscole e minuscole.</p></td> 
  </tr> 
  <tr> 
   <td><p>Nome/ID opportunità</p></td> 
   <td><p>Consente l’inserimento di più valori aggiungendo filtri tramite il segno più "+" a destra. Più valori di filtro avranno una relazione "o", il che significa che le sezioni mostreranno i risultati per entrambi i valori di filtro. Se uno dei valori del filtro non è valido, il dashboard non produrrà risultati per il valore non valido, ma continuerà a filtrare in base ai valori del filtro validi. Senza distinzione tra maiuscole e minuscole.</p></td> 
  </tr> 
  <tr> 
   <td><p>ID lead/E-mail</p></td> 
   <td><p>Consente l’inserimento di più valori aggiungendo filtri tramite il segno più "+" a destra. Più valori di filtro avranno una relazione "o", il che significa che le sezioni mostreranno i risultati per entrambi i valori di filtro. Se uno dei valori del filtro non è valido, il dashboard non produrrà risultati per il valore non valido, ma continuerà a filtrare in base ai valori del filtro validi. Senza distinzione tra maiuscole e minuscole.</p></td> 
  </tr> 
  <tr> 
   <td><p>ID contatto/E-mail</p></td> 
   <td><p>Consente l’inserimento di più valori aggiungendo filtri tramite il segno più "+" a destra. Più valori di filtro avranno una relazione "o", il che significa che le sezioni mostreranno i risultati per entrambi i valori di filtro. Se uno dei valori del filtro non è valido, il dashboard non produrrà risultati per il valore non valido, ma continuerà a filtrare in base ai valori del filtro validi. Senza distinzione tra maiuscole e minuscole.</p><p>Nome/ID account, ID lead/E-mail, ID contatto/Filtro e-mail sono relazione "o", il che significa che se sia il filtro lead che il filtro contatto hanno valore, verranno visualizzati tutti i record per uno degli ID.</p></td> 
  </tr> 
  <tr> 
   <td><p>Modello di attribuzione</p></td> 
   <td><p>Specifica a quale modello devono essere calcolati i ricavi attribuiti. Valori consentiti: "Full Path Attribution", "First Touch Attribution", "Custom Model Attribution", "Lead Creation Attribution", "U Shaped Attribution", "W Shaped Attribution".</p></td> 
  </tr> 
  <tr> 
   <td><p>Tipo di evento</p></td> 
   <td><p>Filtra il percorso per tipo di evento su cui si basa il punto di contatto utente. Consente l’inserimento di più valori aggiungendo filtri tramite il segno più "+" a destra. Valori consentiti: "Sessione", "Campagna CRM", "Evento CRM", "Attività CRM", "Impression".</p></td> 
  </tr> 
  <tr> 
   <td><p>Fasi lead</p></td> 
   <td><p>Filtra percorso per fase di lead su cui si basa il punto di contatto dell’utente. Consente l’inserimento di più valori aggiungendo filtri tramite il segno più "+" a destra. L’impostazione predefinita del filtro "è uguale a" mostrerà i suggerimenti tra cui scegliere, ma si consiglia di utilizzare "contiene" come criteri di filtro per più filtri nelle fasi.</p></td> 
  </tr> 
  <tr> 
   <td><p>Fasi dell’opportunità</p></td> 
   <td><p>Filtra percorso per fase di opportunità su cui si basa il punto di contatto utente. Consente l’inserimento di più valori aggiungendo filtri tramite il segno più "+" a destra. L’impostazione predefinita del filtro "è uguale a" mostrerà i suggerimenti tra cui scegliere, ma si consiglia di utilizzare "contiene" come criteri di filtro per più filtri nelle fasi.</p></td> 
  </tr> 
  <tr> 
   <td><p>Data punto di contatto</p></td> 
   <td><p>Filtra il percorso per data/ora di contatto.</p></td> 
  </tr> 
  <tr> 
   <td><p>E-mail punto di contatto utente</p></td> 
   <td><p>Filtra percorso per e-mail sul punto di contatto dell’utente. Questo consente di filtrare le e-mail non associate a un lead/contatto/account.</p></td> 
  </tr> 
  <tr> 
   <td><p>Tipo di contatto marketing</p></td> 
   <td><p>Filtra percorso per tipo di contatto marketing.</p></td> 
  </tr> 
  <tr> 
   <td><p>Canale</p></td> 
   <td><p>Filtra percorso per canale.</p></td> 
  </tr> 
  <tr> 
   <td><p>Medium</p></td> 
   <td><p>Filtra il percorso in base al mezzo.</p></td> 
  </tr> 
  <tr> 
   <td><p>Sorgente web</p></td> 
   <td><p>Filtra percorso per origine web.</p></td> 
  </tr> 
  <tr> 
   <td><p>Prima interazione con la persona</p></td> 
   <td><p>Filtra il percorso in base alla colonna "È il primo contatto" nella tabella dei punti di contatto dell’utente.</p></td> 
  </tr> 
  <tr> 
   <td><p>Reddito Attribuito</p></td> 
   <td><p>Filtra percorso per valore di ricavo attribuito.</p></td> 
  </tr> 
 </tbody> 
</table>
