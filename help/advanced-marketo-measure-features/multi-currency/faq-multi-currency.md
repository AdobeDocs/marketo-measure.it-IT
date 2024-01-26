---
unique-page-id: 27656745
description: Domande frequenti (più divise) - [!DNL Marketo Measure] - Documentazione del prodotto
title: Domande frequenti (più divise)
exl-id: 1d0936fb-4e66-4877-98d2-32c678a7ef3e
feature: Multi-Currency
source-git-commit: b7aea1e0789b2f4f3fd4b250c0f66595618317bb
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 0%

---

# Domande frequenti (più divise) {#faq-multi-currency}

**Come faccio a sapere quale bit di funzione abilitare?**

Tieni presente che per questa funzione sono disponibili due diversi bit di feature. Entrambi si trovano nella scheda Generale della sezione CRM in Impostazioni: Valute multiple e Valute avanzate. È necessario abilitare più divise se il cliente utilizza più di una valuta, mentre il bit di funzione aggiuntivo Divise avanzate può essere abilitato se il cliente utilizza [!DNL Salesforce]la funzione &quot;Advanced Currency Management&quot; in cui l’utente può impostare un intervallo temporale per i tassi di conversione.

Sfortunatamente, non sappiamo quando un cliente passa da Semplice a Avanzato se è già stato attivato Avanzato. Per questo motivo, il cliente deve mantenere manualmente l’impostazione Valute avanzate allineata con la propria impostazione di gestione delle relazioni con i clienti. Questo dovrebbe essere evidente al cliente se le conversioni non sono corrette, il che significa che non sapevamo quale livello di conversione applicare.

**Perché il mio account degli annunci mi sta dando un messaggio di avviso?**

Verrà visualizzato un messaggio di avviso accanto all’account degli annunci che potrebbe contenere valute provenienti da una valuta non supportata. In questo caso, le dashboard conterranno sezioni con un messaggio &quot;Valute miste&quot;. È consigliabile rivolgersi all&#39;amministratore del sistema di gestione delle relazioni con i clienti per assicurarsi che la valuta sconosciuta contenga una conversione nel sistema di gestione delle relazioni con i clienti.

**Cosa significa &quot;Valute miste&quot; nel riquadro del dashboard?**

Se hai un riquadro con il messaggio &quot;Valute miste&quot; in basso, significa che abbiamo importato alcuni costi mappati su una valuta che non riconosciamo. Poiché tutte le nostre conversioni devono provenire dal sistema CRM con un tasso di conversione effettivo, significa che nel sistema CRM manca questa valuta. È consigliabile rivolgersi all&#39;amministratore del sistema di gestione delle relazioni con i clienti per assicurarsi che la valuta sconosciuta contenga una conversione nel sistema di gestione delle relazioni con i clienti.

**Come si aggiunge una nuova valuta o un nuovo tasso di conversione?**

La dichiarazione di una nuova valuta o di un nuovo tasso di conversione può essere eseguita solo in [!DNL Salesforce] o [!DNL Dynamics] affinché ci sia un&#39;unica fonte di verità per questi valori. Quando viene rilevata una nuova valuta o un nuovo tasso di conversione, [!DNL Marketo Measure] scaricherà e lo renderà disponibile. Non offriamo un&#39;area per inserire queste tariffe.

**La valuta non viene visualizzata nel formato corretto. Come posso cambiarlo?**

Sappiamo che alcuni paesi hanno un modo diverso di formattare gli importi (ad esempio, 1.234,00, 1.234, 1.234). Ma introduciamo un altro livello di complessità se dobbiamo non solo determinare la valuta di un utente, ma anche il suo paese di origine, dal momento che diversi paesi e valute possono essere gestiti in modo diverso. Il formato coerente scelto è 1.234,00. Questo non può essere modificato.

**Perché non è possibile visualizzare il simbolo di valuta per la valuta selezionata?**

[!DNL Salesforce] e [!DNL Dynamics] visualizzare gli importi con il codice di conversione di 3 lettere. Quindi, per coerenza, gli importi convertiti vengono visualizzati anche con il Codice di conversione di 3 lettere e non con il simbolo.

**Cosa vedrà il cliente se non ha abilitato la multi-valuta?**

Se il cliente non dispone della funzione multi-valuta, verrà utilizzata per impostazione predefinita la lingua della valuta dal sistema di gestione delle relazioni con i clienti e verranno modificati tutti i codici ISO che mostrano la spesa e i ricavi nella valuta aziendale. Se questo non è corretto e il cliente ha un uso misto di valuta, la soluzione potrebbe essere quella di effettuare l’aggiornamento per ottenere la funzione multi-valuta.

**In che modo questa funzione influisce sui rapporti basati su punti di contatto nel CRM?**

Per [!DNL Dynamics] e [!DNL Salesforce] clienti che utilizzano solo la gestione della valuta di base (non avanzata), gli importi dei ricavi dei punti di contatto devono essere convertiti correttamente, pertanto i rapporti CRM devono funzionare come previsto.

Sfortunatamente, ci sono alcune sfumature nel modo in cui questo funziona per gli utenti di [!DNL Salesforce] Gestione avanzata della valuta, a causa di una limitazione di lunga data [!DNL Salesforce]. La risposta breve a &quot;cosa facciamo in questo caso&quot; è che convertiamo gli importi dei ricavi utilizzando i tassi fissi definiti nella scheda &quot;Gestisci valute&quot; di base (non avanzata). In altre parole, ignoriamo completamente i tassi di cambio datati nonostante il fatto che il cliente abbia definito tassi di cambio datati.

Per il lettore interessato, ecco perché funziona in questo modo. I nostri punti di contatto utilizzano i campi della formula per calcolare i ricavi (derivati dall’importo dell’opportunità associata). [!DNL Salesforce] supporta in modo nativo la conversione della valuta per questi calcoli di formula, ma solo per il gusto di base del supporto della valuta. È impossibile definire un campo formula che faccia riferimento ai tassi di cambio con data. [!DNL Salesforce] semplicemente non supporta tale capacità, quindi non abbiamo modo di fare riferimento ai tassi datati nei nostri calcoli delle entrate, nonostante il fatto che tali tassi datati esistano in [!DNL Salesforce] (sembra folle, ma è così che funziona.)

**Se il cliente ha utilizzato un flusso di lavoro per compilare un campo convertito, in che modo deve utilizzare il campo in futuro?**

Poiché ora l’offerta gestirà le conversioni per il cliente, si consiglia di rimuovere i flussi di lavoro e i campi personalizzati e di importare il valore della quantità non elaborata.

>[!MORELIKETHIS]
>
>[Notifiche di errore](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"}
