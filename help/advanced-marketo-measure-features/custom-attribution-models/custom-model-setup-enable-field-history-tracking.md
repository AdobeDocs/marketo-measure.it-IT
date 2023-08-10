---
unique-page-id: 18874777
description: Impostazione modello personalizzato - Abilita tracciamento cronologia campi - [!DNL Marketo Measure] - Documentazione del prodotto
title: Impostazione modello personalizzato - Abilita tracciamento cronologia campi
exl-id: 70328e67-051b-4864-891b-b251e49859c2
feature: Custom Models
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Impostazione modello personalizzato: abilita tracciamento cronologia campi {#custom-model-setup-enable-field-history-tracking}

## Perché e quando abilitare il tracciamento della cronologia dei campi {#why-and-when-to-enable-field-history-tracking}

Se decidi di includere un campo personalizzato come fase nel modello di attribuzione personalizzato, verifica della cronologia dei campi **deve essere abilitato** per questo campo. L’abilitazione del tracciamento della cronologia dei campi consentirà [!DNL Salesforce] per tenere traccia delle modifiche apportate al campo personalizzato, creare un record nella tabella Tracciamento cronologia. [!DNL Marketo Measure] può scaricare quella tabella e utilizzare queste informazioni per misurare il giorno e l’ora in cui si è verificata una &quot;transizione&quot;. Senza tracciamento cronologia campi, [!DNL Marketo Measure] non è in grado di tenere traccia delle modifiche relative a questo campo.

Solo se [!UICONTROL Lead Status] o nel modello personalizzato vengono utilizzati gli stadi dell’opportunità, non è necessario attivare il tracciamento della cronologia dei campi, in quanto verrà tracciato automaticamente come transizione dell’area di visualizzazione.

Per abilitare il tracciamento della cronologia dei campi, segui le istruzioni riportate di seguito.

## Abilita tracciamento cronologia campi {#enable-field-history-tracking}

>[!NOTE]
>
>Per apportare queste modifiche ai campi dell&#39;oggetto Lead/Contatto/Opportunità, è necessario essere amministratore di sistema.

1. Vai all’oggetto in cui si trova il campo personalizzato e fai clic sul pulsante **[!UICONTROL Set History Tracking]** pulsante.

   ![](assets/1.png)

1. Seleziona i campi in cui desideri tenere traccia delle modifiche.

   ![](assets/2.png)

[!DNL Marketo Measure] può reimportare un record solo se vede che è stato modificato di recente. I campi formula tecnicamente non modificano un record quando viene modificato, in quanto il calcolo viene eseguito in background. Si sono verificati dei problemi in cui una regola viene saltata perché [!DNL Marketo Measure] non ha visto la modifica del record, pertanto si consiglia di **non utilizzare i campi formula nelle definizioni delle regole**. La soluzione consiste nel creare un campo di testo e utilizzare un flusso di lavoro per compilare tale campo con il valore o il calcolo corretto ogni volta che il record viene modificato o soddisfa i criteri. Questo richiede che tutti i record vengano modificati in modo che il flusso di lavoro possa funzionare retroattivamente sui record precedenti.
