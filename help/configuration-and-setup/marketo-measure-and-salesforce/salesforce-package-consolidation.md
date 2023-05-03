---
description: "[!DNL Salesforce] Consolidamento dei pacchetti - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Salesforce] Consolidamento dei pacchetti"
source-git-commit: e0a471a8e74cdba23a01bea02054c82ede82de9b
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# [!DNL Salesforce] Consolidamento dei pacchetti {#salesforce-package-consolidation}

Siamo entusiasti di annunciare le prossime modifiche ai pacchetti Marketo Measure Salesforce. Per migliorare l&#39;esperienza utente e semplificare l&#39;utilizzo, stiamo consolidando tutti i pacchetti esistenti in un unico pacchetto completo.

## Ritiro del pacchetto {#package-retirement}

A seguito di questo consolidamento, gli attuali pacchetti V1, V2_EXT, V2_Security e tutti i pacchetti Reporting verranno ritirati dopo agosto 2023. Se hai già installato il pacchetto V2, devi aggiornarlo alla nuova versione consolidata.

## Nuovo pacchetto consolidato {#new-consolidated-package}

Il nuovo pacchetto V2 consolidato incorpora tutte le caratteristiche e funzionalità dei pacchetti precedenti, fornendo un&#39;esperienza utente migliorata. Questo pacchetto aggiornato consente un monitoraggio più efficiente delle prestazioni di marketing e di vendita e consente di ottenere informazioni più approfondite sul comportamento dei clienti.

## Supporto e transizione {#support-and-transition}

Comprendiamo che questo cambiamento può richiedere degli aggiustamenti e ci impegniamo a sostenerti durante tutto il processo. Nostro [Team di supporto](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} è prontamente disponibile per rispondere a qualsiasi domanda e contribuire ad assicurare una transizione senza scosse al nuovo pacchetto consolidato.

## Azioni necessarie {#retired-actions}

* Se hai già installato il pacchetto V2, devi aggiornarlo alla nuova versione consolidata.
* Se disponi di rapporti o dashboard da qualsiasi pacchetto di reporting, puoi facilmente ricrearli senza apportare alcuna modifica, poiché tutti i campi utilizzati esistono nel pacchetto consolidato.
* Se hai rapporti che utilizzano campi nel pacchetto V2_EXT, puoi ricrearli nel pacchetto consolidato attraverso i passaggi seguenti:
   * Tutti i dati contenuti nei campi V2_EXT sono disponibili nei campi Punto di contatto, per cui puoi modificare i rapporti per recuperare dati dai corrispondenti campi dei punti di contatto V2, aggiungendo un filtro nella posizione del punto di contatto.
   * Esempio di rapporto che recupera tutti i lead con contenuto annuncio FT contenente testo &quot;Outreach&quot;.
      * Query V2_EXT:
         * bizible2_ext_Ad_Content_FT_c contiene Outreach

![](assets/package-consolidation-1.png)

* Query corrispondente nel pacchetto consolidato:
   * bizible2__Touchpoint_Position__c contiene FT AND
   * bizible2__Ad_Content__c contiene Outreach

![](assets/salesforce-package-consolidation-2.png)

## Domande frequenti {#faq}

**Il pacchetto consolidato avrà conflitti con i campi del pacchetto esistente?**

Non è necessario disinstallare il pacchetto prima di installare il pacchetto consolidato. Non ci saranno conflitti nei campi perché si troveranno in uno spazio dei nomi diverso.

**Come posso eseguire il backfill dei dati dei pacchetti correnti?**

È possibile presentare un ticket [con supporto](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} per il backfill e la rielaborazione dei dati BT/BAT in modo da compilare i campi ID punto di contatto e ID modulo.

**I campi nei pacchetti V1 e V2_EXT saranno disponibili nel pacchetto consolidato?**

Sì. Il pacchetto consolidato conterrà gli stessi campi nella versione V1 con ulteriori suddivisioni per oggetti e i campi V2_EXT per i campi Punto di contatto.

**I rapporti che utilizzano campi V2_EXT possono essere ricreati nel pacchetto consolidato?**

Sì. Segui i passaggi descritti nella sezione [Azioni necessarie](#retired-actions) sezione precedente.
