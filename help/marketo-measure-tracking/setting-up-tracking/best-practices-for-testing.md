---
unique-page-id: 18874722
description: Best practice per i test - [!DNL Marketo Measure]
title: Best practice per i test
exl-id: ff95a1a9-d324-47f5-b47d-39014dff77e4
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---

# Best practice per i test {#best-practices-for-testing}

È necessario testare tutti i diversi tipi di moduli necessari per garantire [!DNL Marketo Measure] JavaScript funziona correttamente.

## Processo di test consigliato {#recommended-test-process}

1. Utilizza un browser in incognito o cancella i cookie tra ciascun test di invio del modulo _e_ utilizza ogni volta un indirizzo e-mail diverso.

   >[!TIP]
   >
   >Una best practice consiste nell’utilizzare un’e-mail falsa che contiene qualcosa che indica che si tratta di un test, nonché l’ora del giorno. Ad esempio: `testing830am@test.com`.

1. Avvia la ricerca da un motore di ricerca (ad es. `google.com`) o passare direttamente a un modulo.

1. Inviare il modulo sul sito Web utilizzando un indirizzo e-mail univoco.

1. Registra l’URL della pagina su cui stai inviando il modulo e l’indirizzo e-mail utilizzato.

1. Individua il record creato nel CRM (lead o contatto) per l’invio del modulo e verifica che sia stato creato correttamente un punto di contatto.

>[!NOTE]
>
>È possibile utilizzare una [!DNL Marketo Measure] rapporto sulle scorte, ad esempio Lead con [!DNL Marketo Measure] Punti di contatto o osserva il layout della pagina Lead/Contatto se hai scelto di aggiornare i layout di pagina con [!DNL Marketo Measure] dettagli. L’elaborazione dei dati potrebbe richiedere del tempo.
