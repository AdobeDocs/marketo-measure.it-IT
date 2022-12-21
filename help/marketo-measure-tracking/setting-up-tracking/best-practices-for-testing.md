---
unique-page-id: 18874722
description: Best practice per i test - [!DNL Marketo Measure] - Documentazione del prodotto
title: Best practice per i test
exl-id: ff95a1a9-d324-47f5-b47d-39014dff77e4
source-git-commit: 993a326c377b3b6ff48c4e0114b59297f9ca2ca6
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 1%

---

# Best practice per i test {#best-practices-for-testing}

È necessario verificare tutti i diversi tipi di moduli necessari per garantire la [!DNL Marketo Measure] JavaScript funziona correttamente.

## Processo di test consigliato {#recommended-test-process}

1. Utilizzare un browser in incognito o cancellare i cookie tra ogni test di invio del modulo _e_ utilizza ogni volta un indirizzo e-mail diverso.

   >[!TIP]
   >
   >Una best practice consigliata è l’utilizzo di un’e-mail falsa che contiene elementi che indicano che si tratta di un test, nonché l’ora del giorno. Ad esempio: `testing830am@test.com`.

1. Avvia la ricerca in un motore di ricerca (ad es. `google.com`) o passa direttamente a un modulo.

1. Invia il modulo sul tuo sito web utilizzando un indirizzo e-mail univoco.

1. Registrare l’URL della pagina in cui si invia il modulo e l’indirizzo e-mail utilizzato.

1. Individua il record creato nel CRM (Lead o Contact) per l’invio del modulo e verifica che un punto di contatto sia stato creato in modo appropriato.

>[!NOTE]
>
>Puoi utilizzare un [!DNL Marketo Measure] bollettino azionario, ad esempio Leads con [!DNL Marketo Measure] Se si sceglie di aggiornare i layout di pagina con i punti di contatto, è possibile osservare il layout della pagina Lead/Contatto [!DNL Marketo Measure] dettagli. L’elaborazione dei dati potrebbe richiedere del tempo.
