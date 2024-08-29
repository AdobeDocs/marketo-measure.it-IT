---
description: Scopri come gestire gli errori nelle esportazioni CRM
title: Gestione degli errori per le esportazioni CRM
feature: Salesforce
source-git-commit: 24cb14c0f5db13c791966d21b4a1145b655ecc1b
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Gestione degli errori per le esportazioni CRM

La funzione Pausa per errori di esportazione consente di controllare se i processi di esportazione CRM devono essere messi in pausa quando si verifica un errore a livello di record.

L&#39;impostazione è disponibile in **Account personale** > **Impostazioni** > **CRM** > **Generale**.

>[!NOTE]
>
>Questa funzione è visibile solo se la funzione &quot;Esporta in CRM&quot; è abilitata.

Quando questa funzione è abilitata, il processo di esportazione cessa di progredire e rimane sul record in cui si è verificato l’errore, fino a quando il problema non viene risolto. Questi errori sono in genere dovuti a autorizzazioni mancanti, regole di convalida personalizzate applicate in modo errato o problemi nei flussi di lavoro/trigger. Il processo continuerà a essere eseguito come pianificato e tenterà automaticamente di nuovo di esportare il record non riuscito fino a quando non avrà esito positivo.

Se scegli di disabilitare questa funzione, verrà visualizzata una finestra a comparsa di avviso che ti informerà che ciò potrebbe causare incoerenze nei dati. Sarà tua responsabilità affrontare eventuali problemi che potrebbero sorgere da queste incoerenze.

In entrambi i casi, indipendentemente dal fatto che la funzionalità sia attivata o disattivata, tutti gli errori a livello di record rilevati vengono registrati nella tabella `ExportErrors` e il processo `CRMExport_ExportError` tenterà automaticamente di riesportare questi record ogni giorno. Questo elimina la necessità di una richiesta di supporto per avviare una riesportazione, in quanto ciò avverrà automaticamente senza alcun intervento degli sviluppatori.

Perché è necessario il comportamento di interruzione del processo data la funzionalità `ExportErrors`? Interrompendo i processi di esportazione CRM regolari in un record specifico, la risoluzione dei problemi diventa molto più semplice. Consente di eseguire processi in locale e di evitare la creazione di un numero potenzialmente elevato di errori di esportazione, che dovrebbero essere recuperati ed elaborati durante la riesportazione.

Questa funzione può essere attivata o disattivata in base al comportamento desiderato. Ad esempio, se riscontri un codice di errore particolarmente impegnativo e preferisci accettare temporaneamente dati &quot;incompleti&quot;, puoi disattivare la funzione. Una volta risolto il problema, puoi riattivare la funzione per garantire che le esportazioni future siano complete e precise.
