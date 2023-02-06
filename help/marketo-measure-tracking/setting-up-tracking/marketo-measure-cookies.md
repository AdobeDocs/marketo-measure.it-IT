---
unique-page-id: 18874590
description: "[!DNL Marketo Measure] Cookie - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] Cookie"
exl-id: de6e35ae-af92-43ba-8416-3e07d3dd470c
source-git-commit: 3a13ab3e497652d1975e69280a3d224ac95504aa
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Cookie di Marketo Measure {#marketo-measure-cookies}

Scopri le varie [!DNL Marketo Measure] Cookie caricati sul sito quando si applica il [!DNL Marketo Measure] JavaScript per le pagine di destinazione. Queste informazioni possono essere utili per il team di sviluppo web durante l’implementazione.

| **Nome cookie** | **Tipo di cookie** | **Finalità** |
|---|---|---|
| _BUID | Terze parti, salvate sul dominio .bizible.com | ID utente universale per identificare lo stesso utente tra più domini di client. |
| _biz_uid | Prima parte | ID utente sul dominio corrente. |
| _biz_sid | Prima parte | ID sessione dell’utente. |
| _biz_flagsA | Prima parte | Un singolo cookie che memorizza più informazioni, ad esempio se l’utente ha inviato o meno un modulo, ha eseguito una migrazione tra domini diversi, ha inviato un pixel view-through, ha rinunciato al tracciamento, ecc. |
| _biz_nA | Prima parte | Numero di sequenza che [!DNL Marketo Measure] include per tutte le richieste, per scopi diagnostici interni |
| _biz_dfsA | Prima parte | Memorizza temporaneamente i dati di invio del modulo che si verificano in precedenza [!DNL bizible.js] riceve una configurazione JS per determinare se il modulo di tracciamento su HTTPS è abilitato o meno. |
| _biz_pendingA | Prima parte | Memorizza temporaneamente i dati analitici che non sono stati inviati correttamente a [!DNL Marketo Measure] server ancora. |

Se durante l&#39;installazione di JavaScript viene attivato un avviso WAF (Web Application Firewall), gli utenti possono disattivare tale regola WAF o inserire nell&#39;elenco Consentiti i cookie, come nell&#39;esempio seguente:

![](assets/marketo-measure-cookies-1.png)
