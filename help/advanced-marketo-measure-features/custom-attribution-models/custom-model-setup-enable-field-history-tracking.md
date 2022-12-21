---
unique-page-id: 18874777
description: Impostazione modello personalizzato - Abilita tracciamento cronologia campi - [!DNL Marketo Measure] - Documentazione del prodotto
title: Impostazione del modello personalizzato - Abilita tracciamento cronologia campi
exl-id: 70328e67-051b-4864-891b-b251e49859c2
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Impostazione del modello personalizzato: Abilita tracciamento cronologia campi {#custom-model-setup-enable-field-history-tracking}

## Perché e quando abilitare il tracciamento della cronologia dei campi {#why-and-when-to-enable-field-history-tracking}

Se decidi di includere un campo personalizzato come fase nel modello di attribuzione personalizzato, tieni traccia della cronologia dei campi **deve essere abilitato** per questo campo. L’abilitazione del tracciamento della cronologia dei campi consentirà [!DNL Salesforce] per tenere traccia di ogni modifica del campo personalizzato creando un record nella tabella Tracking della cronologia. [!DNL Marketo Measure] può scaricare la tabella e utilizzare queste informazioni per misurare l’ora e il giorno in cui si è verificata una &quot;transizione&quot;. Senza tracciamento della cronologia dei campi, [!DNL Marketo Measure] non è in grado di tenere traccia delle modifiche relative a questo campo.

Solo se [!UICONTROL Lead Status] Per gli stadi opportunità utilizzati nel modello personalizzato, non è necessario attivare il tracciamento della cronologia dei campi, perché verrà tracciato automaticamente come transizione di fase.

Per abilitare il tracciamento della cronologia dei campi, segui le istruzioni riportate di seguito.

## Abilita tracciamento cronologia campi {#enable-field-history-tracking}

>[!NOTE]
>
>È necessario essere un amministratore di sistema per apportare queste modifiche ai campi dell’oggetto Lead/Contact/Opportunity.

1. Passa all’oggetto in cui si trova il campo personalizzato e fai clic sul pulsante **[!UICONTROL Set History Tracking]** pulsante .

   ![](assets/1.png)

1. Seleziona i campi sui quali desideri tenere traccia delle modifiche.

   ![](assets/2.png)

[!DNL Marketo Measure] può reimportare un record solo se rileva che il record è stato modificato di recente. I campi Formula tecnicamente non modificano un record quando viene modificato poiché esegue il calcolo in background. Sono stati riscontrati problemi a causa dei quali una regola viene ignorata [!DNL Marketo Measure] non ha visto la modifica del record, quindi si consiglia di **non utilizzare i campi formula nelle definizioni delle regole**. La soluzione consiste nel creare un campo di testo e utilizzare un flusso di lavoro per popolare tale campo con il valore o il calcolo appropriati ogni volta che il record viene modificato o si adatta ai criteri. Questo richiede che tutti i record vengano modificati in modo che il flusso di lavoro possa funzionare retroattivamente sui vecchi record.
