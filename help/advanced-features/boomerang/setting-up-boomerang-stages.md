---
description: Impostazione delle fasi del boomerang - [!DNL Marketo Measure]
title: Impostazione delle fasi del boomerang
exl-id: 00dd2826-27a3-462e-a70e-4cec90d07f92
feature: Boomerang
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# Impostazione delle fasi del boomerang {#setting-up-boomerang-stages}

>[!AVAILABILITY]
>La funzione Boomerang è abilitata solo per i clienti di livello 2 e 3. Per richiedere un livello di account superiore, contatta il team dell’account di Adobe (il tuo account manager).

Per abilitare [!UICONTROL Boomerang] fasi per il tuo account, devi essere un Amministratore account. In alternativa, è possibile abilitarlo contattando il [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}. Dopo aver attivato la funzione, segui queste istruzioni per configurarla.

## Configurazione fase boomerang {#boomerang-stage-setup}

1. Vai a [!UICONTROL Stage Mapping]. Nella colonna &quot;[!UICONTROL Boomerang]&quot; selezionare le caselle accanto alle fasi che si desidera monitorare.

   ![Interfaccia di mappatura dello stage che mostra la colonna Boomerang con caselle di controllo per la selezione dello stage](assets/1-2.png)

1. Vai alla scheda [!UICONTROL Attribution Settings] e inserisci il numero di punti di contatto per ogni fase che desideri visualizzare. Consentiamo un massimo di 10. Il valore predefinito è 1.

   ![Scheda Impostazioni attribuzione che mostra i campi di input del conteggio dei punti di contatto per ogni fase del boomerang](assets/2-2.png)

1. Fai clic su **[!UICONTROL Save]**.

   >[!NOTE]
   >Consenti 24-48 ore per la rielaborazione dei dati in base a queste modifiche.

## Configurazione di Boomerang Stage con attribuzione di modello personalizzato {#boomerang-stage-setup-with-custom-model-attribution}

1. Vai a [!UICONTROL Stage Mapping]. Nella colonna &quot;[!UICONTROL Boomerang]&quot; selezionare le caselle accanto alle fasi che si desidera monitorare.

   ![Interfaccia di mappatura dello stage con colonne Boomerang e Custom Model per la selezione dello stage](assets/3-1.png)

1. Se desideri anche che queste fasi Boomerang siano incluse nel modello personalizzato e ricevano il credito di attribuzione, assicurati di selezionare anche la casella nella colonna &quot;[!UICONTROL Custom Model]&quot;.

   ![Mappatura stadio con le caselle di controllo della colonna Modello personalizzato selezionate per le fasi di boomerang](assets/4-1.png)

1. Passa alla scheda [!UICONTROL Attribution Settings]. Determina come desideri ponderare l’attribuzione per le fasi del boomerang. Le opzioni consentono di ponderare l’attribuzione sulla prima o sull’ultima occorrenza oppure di suddividerla in modo uniforme tra tutte le occorrenze.

   ![Impostazioni di attribuzione che mostrano le opzioni di ponderazione boomerang per la prima, l&#39;ultima o persino la divisione](assets/5-1.png)

1. Immettere il numero di occorrenze di ogni fase che si desidera visualizzare. Possiamo consentire un massimo di 10. Il valore predefinito è 1.

   ![Impostazioni di attribuzione che mostrano i campi di input del conteggio delle occorrenze per ogni fase del boomerang](assets/6-1.png)

1. Imposta la percentuale di attribuzione da allocare agli stadi boomerang inclusi nel modello personalizzato. Assicurati che l’attribuzione totale per tutte le fasi sia pari al 100%. Fai clic su **[!UICONTROL Save and Process]**.

   ![Impostazioni di attribuzione che mostrano i campi di allocazione percentuale per le fasi di boomerang nel modello personalizzato](assets/7-1.png)

   >[!NOTE]
   >Consenti 24-48 ore per la rielaborazione dei dati in base a queste modifiche.
