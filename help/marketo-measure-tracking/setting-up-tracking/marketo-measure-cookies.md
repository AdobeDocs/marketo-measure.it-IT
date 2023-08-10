---
unique-page-id: 18874590
description: "[!DNL Marketo Measure] Cookie - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] Cookie"
exl-id: de6e35ae-af92-43ba-8416-3e07d3dd470c
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Cookie di Marketo Measure {#marketo-measure-cookies}

Scopri i vari [!DNL Marketo Measure] Cookie caricati sul sito quando si applica il [!DNL Marketo Measure] JavaScript per le pagine di destinazione. Queste informazioni possono essere utili al team di sviluppo web durante l’implementazione.

| **Nome cookie** | **Tipo di cookie** | **Finalità** |
|---|---|---|
| _BUID | Terze parti, salvate nel dominio .bizible.com | ID utente universale per identificare lo stesso utente nei domini di più client. |
| _biz_uid | Prima parte | ID utente nel dominio corrente. |
| _biz_sid | Prima parte | ID sessione dell’utente. |
| _biz_flagsA | Prima parte | Un singolo cookie che memorizza più informazioni, ad esempio se l’utente ha inviato o meno un modulo, eseguito una migrazione tra domini diversi, inviato un pixel viewthrough, escluso dal tracciamento, ecc. |
| _biz_nA | Prima parte | Numero di sequenza che [!DNL Marketo Measure] include per tutte le richieste, a scopo di diagnostica interna |
| _biz_dfsA | Prima parte | Memorizza temporaneamente i dati di invio del modulo che si verificano prima [!DNL bizible.js] riceve un JS di configurazione per determinare se il modulo di tracciamento su HTTPS è abilitato o meno. |
| _biz_pendingA | Prima parte | Memorizza temporaneamente i dati di analisi che non sono stati inviati correttamente a [!DNL Marketo Measure] server. |

Se durante la configurazione di JavaScript viene attivato un avviso WAF (Web Application Firewall), gli utenti possono disattivare tale regola WAF o inserire nell’elenco Consentiti i cookie, come nell’esempio seguente:

![](assets/marketo-measure-cookies-1.png)
