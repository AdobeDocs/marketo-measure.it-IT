---
unique-page-id: 35586105
description: Percorso di coinvolgimento - [!DNL Marketo Measure] - Documentazione del prodotto
title: Percorso di coinvolgimento
exl-id: 104d803f-9f40-4ab6-872d-6432f8c087e9
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 0%

---

# Percorso di coinvolgimento {#engagement-path}

Il percorso di coinvolgimento ti consente di visualizzare una visione completa dei lead, dei contatti, degli account e delle opportunità dal primo contatto fino alla chiusura.

![](assets/one-2.png)

## Descrizione sezione {#tile-description}

**Tipo evento:** Tipo di punto di contatto (sessione, campagna CRM, evento CRM, attività CRM, impression)

**Posizione punto di contatto dell&#39;acquirente:** Punto di contatto Posizione del lead/contatto

**Posizione punto di contatto dell&#39;attribuzione dell&#39;acquirente:** Posizione punto di contatto dell’opportunità per l’attribuzione dell’acquirente

**Data punto di contatto:** Per le fonti online: data e ora del coinvolgimento. Per gli eventi offline: data e ora impostate nella campagna Salesforce. Per le attività punto di contatto: campo data punto di contatto a cui si fa riferimento nella configurazione delle attività

**E-mail:** E-mail associata al coinvolgimento

**Tipo di contatto marketing:** Tipo di coinvolgimento (Visita web, Modulo web, Chat web, CRM, Tipi di attività)

**Canale:** Canale di marketing che ha guidato il coinvolgimento

**Media:** Mezzo di coinvolgimento

* Se il coinvolgimento proviene da una piattaforma connessa API (Adwords/BingAds), il supporto sarà CPC
* Se la pagina di destinazione del coinvolgimento contiene utm_medium, analizzeremo
* Se il coinvolgimento proviene dalla campagna CRM, il supporto proviene dal campo &quot;Tipo&quot; dalla campagna CRM

**Origine Web:** In questa colonna viene visualizzata l’origine del coinvolgimento

* Se il coinvolgimento proviene da una piattaforma connessa all’API, l’origine web visualizza il nome della piattaforma pubblicitaria
* Se il punto di contatto proviene da una ricerca organica, in questo campo viene visualizzato il nome del motore di ricerca
* Se non #1 o #2 e il valore utm_source è presente nell’URL della pagina di destinazione per il punto di contatto, tale valore verrà visualizzato qui
* Se non sono presenti i valori #1 o #2 e non è presente alcun valore utm_source, il dominio principale dell’URL di riferimento verrà visualizzato qui.
* In nessuno dei casi precedenti, verranno visualizzati Web Direct o Web

**Prima interazione con la persona:** Questa colonna mostra Sì o No se quel punto di contatto è stata la prima interazione tra gli individui

**Ricavi attribuiti:** In questa colonna vengono visualizzati i ricavi attribuiti a quel punto di contatto in base al modello di attribuzione selezionato

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
   <td><p>Consente l’aggiunta di più valori tramite il segno più "+" a destra. Più valori di filtro avranno una relazione "o", il che significa che la porzione mostrerà i risultati per entrambi i valori di filtro. Se uno dei valori del filtro non è valido, il dashboard non produrrà risultati per il valore non valido, ma continuerà a filtrare in base ai valori del filtro validi. Senza distinzione tra maiuscole e minuscole.</p></td> 
  </tr> 
  <tr> 
   <td><p>Nome opportunità/ID</p></td> 
   <td><p>Consente l’aggiunta di più valori tramite il segno più "+" a destra. Più valori di filtro avranno una relazione "o", il che significa che la porzione mostrerà i risultati per entrambi i valori di filtro. Se uno dei valori del filtro non è valido, il dashboard non produrrà risultati per il valore non valido, ma continuerà a filtrare in base ai valori del filtro validi. Senza distinzione tra maiuscole e minuscole.</p></td> 
  </tr> 
  <tr> 
   <td><p>ID lead/E-mail</p></td> 
   <td><p>Consente l’aggiunta di più valori tramite il segno più "+" a destra. Più valori di filtro avranno una relazione "o", il che significa che la porzione mostrerà i risultati per entrambi i valori di filtro. Se uno dei valori del filtro non è valido, il dashboard non produrrà risultati per il valore non valido, ma continuerà a filtrare in base ai valori del filtro validi. Senza distinzione tra maiuscole e minuscole.</p></td> 
  </tr> 
  <tr> 
   <td><p>ID contatto/e-mail</p></td> 
   <td><p>Consente l’aggiunta di più valori tramite il segno più "+" a destra. Più valori di filtro avranno una relazione "o", il che significa che la porzione mostrerà i risultati per entrambi i valori di filtro. Se uno dei valori del filtro non è valido, il dashboard non produrrà risultati per il valore non valido, ma continuerà a filtrare in base ai valori del filtro validi. Senza distinzione tra maiuscole e minuscole.</p><p>Nome/ID account, ID lead/e-mail, ID contatto/filtro e-mail sono relazioni "o", il che significa che se il filtro lead e il filtro contatti hanno valore, verranno visualizzati tutti i record per uno degli ID.</p></td> 
  </tr> 
  <tr> 
   <td><p>Modello di attribuzione</p></td> 
   <td><p>Specificare il modello su cui calcolare i ricavi attribuiti. Valori consentiti: "Attribuzione percorso completo", "Attribuzione primo contatto", "Attribuzione modello personalizzato", "Attribuzione creazione lead", "Attribuzione a forma di U", "Attribuzione a forma di W".</p></td> 
  </tr> 
  <tr> 
   <td><p>Tipo evento</p></td> 
   <td><p>Filtra percorso per tipo di evento su cui si basa il punto di contatto dell’utente. Consente l’aggiunta di più valori tramite il segno più "+" a destra. Valori consentiti: "Sessione", "campagna CRM", "evento CRM", "attività CRM", "impression".</p></td> 
  </tr> 
  <tr> 
   <td><p>Fasi lead</p></td> 
   <td><p>Filtrare il percorso in base alla fase del lead su cui si basa il punto di contatto dell’utente. Consente l’aggiunta di più valori tramite il segno più "+" a destra. Per impostazione predefinita, il filtro "è uguale a" mostra i suggerimenti tra cui scegliere, ma consiglia di utilizzare "contiene" come criteri di filtro per più filtri per più fasi.</p></td> 
  </tr> 
  <tr> 
   <td><p>Fasi opportunità</p></td> 
   <td><p>Filtrare il percorso per fase opportunità in base al punto di contatto dell’utente. Consente l’aggiunta di più valori tramite il segno più "+" a destra. Per impostazione predefinita, il filtro "è uguale a" mostra i suggerimenti tra cui scegliere, ma consiglia di utilizzare "contiene" come criteri di filtro per più filtri per più fasi.</p></td> 
  </tr> 
  <tr> 
   <td><p>Data punto di contatto</p></td> 
   <td><p>Filtrare percorso per data/ora del punto di contatto.</p></td> 
  </tr> 
  <tr> 
   <td><p>E-mail punto di contatto utente</p></td> 
   <td><p>Filtrare i percorsi per e-mail sui punti di contatto dell’utente. Questo consente di filtrare le e-mail che non sono associate a un lead/contatti/account.</p></td> 
  </tr> 
  <tr> 
   <td><p>Tipo di contatto marketing</p></td> 
   <td><p>Filtrare il percorso in base al tipo di contatto marketing.</p></td> 
  </tr> 
  <tr> 
   <td><p>Canale</p></td> 
   <td><p>Filtra percorso per canale.</p></td> 
  </tr> 
  <tr> 
   <td><p>Medium</p></td> 
   <td><p>Filtrare il percorso per mezzo.</p></td> 
  </tr> 
  <tr> 
   <td><p>Origine Web</p></td> 
   <td><p>Filtrare il percorso per origine web.</p></td> 
  </tr> 
  <tr> 
   <td><p>Prima interazione con la persona</p></td> 
   <td><p>Filtrare il percorso per la colonna "È il primo contatto" sulla tabella dei punti di contatto dell’utente.</p></td> 
  </tr> 
  <tr> 
   <td><p>Entrate attribuite</p></td> 
   <td><p>Filtrare il percorso in base al valore dei ricavi attribuiti.</p></td> 
  </tr> 
 </tbody> 
</table>
