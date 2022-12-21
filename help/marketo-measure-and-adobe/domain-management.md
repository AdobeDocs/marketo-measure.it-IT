---
description: Gestione del dominio - [!DNL Marketo Measure] - Documentazione del prodotto
title: Gestione dei domini
exl-id: 4db287a0-0267-463c-a359-266b41f15c59
source-git-commit: 54337a0a65b79d80ebeae6531f5e92f4f48721a7
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Gestione dei domini {#domain-management}

Per gli inquilini abilitati IMS in esecuzione [!DNL Marketo Measure] nella shell unificata, [!DNL Marketo Measure] fornisce un’interfaccia che consente agli utenti di gestire il proprio elenco di domini. [!DNL Marketo Measure] gli utenti devono prima verificare tutti i domini che desiderano monitorare nel [Adobe Admin Console](https://adminconsole.adobe.com/). Una volta verificati i domini nell’Admin Console, gli utenti possono gestire se [!DNL Marketo Measure] utilizza questi domini per tenere traccia del traffico del sito web.

## Aggiunta di domini nell’Admin Console {#adding-domains-in-admin-console}

Gli utenti IMS con accesso a Adobe Admin Console possono aggiungere e convalidare i domini di loro proprietà. La convalida del dominio comporta l’aggiunta di un record DNS per ciascun dominio e la successiva autorizzazione dell’Admin Console a verificare tale record.

![](assets/domain-management-1.png)

Le istruzioni per l’aggiunta di domini sono disponibili nella sezione [Documentazione di Admin Console](https://helpx.adobe.com/enterprise/using/set-up-identity.html#setup-domains). Una volta aggiunto il dominio, deve essere [collegato a una directory](https://helpx.adobe.com/enterprise/using/set-up-identity.html#link-domains-to-directories).

## Gestione dei domini in [!DNL Marketo Measure] {#managing-domains-in-marketo-measure}

Una volta aggiunto un dominio nell’Admin Console, [!DNL Marketo Measure] sincronizzerà regolarmente questo record nel nostro database. Questa sincronizzazione avviene ogni notte e ogni volta che un utente visita il **[!UICONTROL Domains]** nella pagina [!DNL Marketo Measure] Interfaccia utente. Per impostazione predefinita, qualsiasi record che [!DNL Marketo Measure] le importazioni verranno disattivate e il tenant deve abilitare manualmente ogni dominio.

![](assets/domain-management-2.png)

Sulla **[!UICONTROL Integration]** > **[!UICONTROL Domains]** page, l&#39;utente vedrà tutti i domini che ha registrato nell&#39;Admin Console, insieme al loro stato. Ogni dominio può essere abilitato o disabilitato. Se un dominio è abilitato, [!DNL Marketo Measure] il tracciamento raccoglierà il traffico visualizzato in quel dominio. Se un dominio è disabilitato, [!DNL Marketo Measure] ignora il traffico visualizzato proveniente da quel dominio e non crea punti di contatto o altri dati. [!DNL Marketo Measure] confermerà inoltre la disattivazione di un dominio e avviserà delle ramificazioni:

![](assets/domain-management-3.png)

L’impatto dell’attivazione/disattivazione di un dominio è immediato e le modifiche non sono retroattive. In futuro, [!DNL Marketo Measure] eliminerà i dati dai domini disabilitati dopo un determinato periodo di tempo.

## Stati {#statuses}

Admin Console Gli stati sono organizzati come segue:

* **CONVALIDATO**: Questo dominio viene verificato nell’Admin Console
* **NON VERIFICATO**: Questo dominio non è verificato completamente in Admin Console e non è idoneo per il tracciamento in [!DNL Marketo Measure]
* **NON VALIDO**: Il dominio potrebbe essere scaduto o essere stato rimosso dall&#39;Admin Console. Tracciamento dei dati in [!DNL Marketo Measure] è contrassegnato per l&#39;eliminazione
* **LEGACY**: Il dominio è stato creato in [!DNL Marketo Measure] e non esiste nell&#39;Admin Console

Gli stati di tracciamento possono essere i seguenti:

* **ATTIVO**: [!DNL Marketo Measure] sta attualmente ricevendo dati da questo dominio
* **DISABILITATO**: Questo dominio è disponibile per il tracciamento, ma al momento è disabilitato
* **NON DISPONIBILE**: Dominio non disponibile per il tracciamento perché non verificato

Passando il puntatore del mouse su un singolo elemento di stato verrà attivata una descrizione comandi che spiega ulteriormente tale stato.

## Domande frequenti {#faq}

**Cosa succede quando un dominio viene rimosso nell’Admin Console?**

Quando un dominio viene rimosso nell’Admin Console, [!DNL Marketo Measure] contrassegna il dominio come eliminato. [!DNL Marketo Measure] interromperà immediatamente il tracciamento del traffico su questo dominio, ma non rimuoverà i dati raccolti in precedenza.

**Perché non posso abilitare un dominio?**

Ci sono diversi motivi per cui un dominio potrebbe non essere consentito per la selezione in questa pagina. Se il dominio non viene convalidato nell’Admin Console, non sarà disponibile in [!DNL Marketo Measure]. Analogamente, se il dominio è di proprietà di un&#39;organizzazione Adobe diversa dall&#39;attuale [!DNL Marketo Measure] tenant, potrebbe non essere disponibile per la selezione.

**Come si rimuove un dominio da questo elenco?**

Se l&#39;interruttore &quot;abilitato&quot; di un dominio è disattivato, [!DNL Marketo Measure] la ignorerà e verrà effettivamente rimossa [!DNL Marketo Measure]. Per rimuovere definitivamente un dominio da [!DNL Marketo Measure], devi disattivarlo in [!DNL Marketo Measure]e successivamente rimuoverlo dall&#39;Admin Console.
