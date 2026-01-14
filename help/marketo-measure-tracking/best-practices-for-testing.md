---
description: Tecniche consigliate per il test delle linee guida per gli utenti di Marketo Measure
title: Best practice per i test
exl-id: ff95a1a9-d324-47f5-b47d-39014dff77e4
feature: Tracking
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 1%

---

# Best practice per i test {#best-practices-for-testing}

È necessario eseguire il test di tutti i diversi tipi di moduli necessari per verificare che il JavaScript [!DNL Marketo Measure] funzioni correttamente.

## Processo di test consigliato {#recommended-test-process}

1. Utilizza un browser in incognito o cancella i cookie tra ogni test di invio modulo _e_ utilizza ogni volta un indirizzo e-mail diverso.

   >[!TIP]
   >
   >Una best practice consiste nell’utilizzare un’e-mail falsa che contiene qualcosa che indica che si tratta di un test, nonché l’ora del giorno. Esempio: `testing830am@test.com`.

1. Avviare la ricerca da un motore di ricerca (ad esempio, `google.com`) o passare direttamente a un modulo.

1. Inviare il modulo sul sito Web utilizzando un indirizzo e-mail univoco.

1. Registra l’URL della pagina su cui stai inviando il modulo e l’indirizzo e-mail utilizzato.

1. Individua il record creato nel CRM (lead o contatto) per l’invio del modulo e verifica che sia stato creato correttamente un punto di contatto.

>[!NOTE]
>
>Se si sceglie di aggiornare i layout di pagina con [!DNL Marketo Measure] dettagli, è possibile utilizzare un report azionario [!DNL Marketo Measure], ad esempio Lead con [!DNL Marketo Measure] punti di contatto, oppure esaminare il layout di pagina Lead/Contatto. L’elaborazione dei dati potrebbe richiedere del tempo.
