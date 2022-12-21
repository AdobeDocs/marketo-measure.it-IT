---
unique-page-id: 27656745
description: Domande frequenti (a più byte) - [!DNL Marketo Measure] - Documentazione del prodotto
title: Domande frequenti (a più byte)
exl-id: 1d0936fb-4e66-4877-98d2-32c678a7ef3e
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 0%

---

# Domande frequenti (a più byte) {#faq-multi-currency}

**Come faccio a sapere quale bit di funzionalità abilitare?**

Tieni presente che per questa funzione sono disponibili due diverse parti di feature. Entrambi si trovano nella scheda Generale della sezione CRM in Impostazioni: Valute multiple e Valute avanzate. Se il cliente utilizza più di una moneta, è necessario abilitare le divise multiple, mentre è possibile abilitare il bit di funzione aggiuntivo Valute avanzate se il cliente utilizza [!DNL Salesforce]La funzione &quot;Gestione avanzata della valuta&quot; consente di impostare un intervallo temporale per i tassi di conversione.

Sfortunatamente, non sappiamo quando un cliente passa da Semplice a Avanzate se Advanced è già stato attivato. Per questo motivo, il cliente deve mantenere l&#39;impostazione Valute avanzate allineata manualmente con la propria impostazione CRM. Questo dovrebbe essere evidente al cliente se le conversioni sono errate, il che significa che non sapevamo quale livello di conversione applicare.

**Perché il mio account di annunci mi dà un messaggio di avviso?**

Visualizzeremo un messaggio di avviso accanto al tuo account degli annunci che potrebbe avere valute provenienti da una valuta non supportata. In questo caso, le dashboard conterranno riquadri con un messaggio &quot;Valute diverse&quot;. Consigliamo di lavorare con l&#39;amministratore CRM per assicurarti che questa valuta sconosciuta contenga una conversione nel CRM.

**Cosa significa &quot;Valute miste&quot; nel riquadro del dashboard?**

Se hai un riquadro con un messaggio &quot;Valute miste&quot; in basso, significa che abbiamo importato alcuni costi mappati su una valuta che non riconosciamo. Poiché tutte le nostre conversioni devono provenire dal CRM con un tasso di conversione effettivo, significa che al CRM manca questa valuta. Consigliamo di lavorare con l&#39;amministratore CRM per assicurarti che questa valuta sconosciuta contenga una conversione nel CRM.

**Come posso aggiungere una nuova valuta o un tasso di conversione?**

Dichiarare una nuova valuta o un tasso di conversione può essere fatto solo in [!DNL Salesforce] o [!DNL Dynamics] affinché vi sia una sola fonte di verità per questi valori. Una volta rilevata una nuova valuta o un tasso di conversione, [!DNL Marketo Measure] lo scaricherà e lo renderà disponibile a voi. Non offriamo un&#39;area per inserire questi tassi.

**La valuta non viene visualizzata nel formato corretto. Come posso cambiare questo?**

Sappiamo che alcuni paesi hanno un modo diverso di formattare gli importi (ad esempio 1.234.00, 1.234, 1.234). Ma introduciamo un altro livello di complessità se non dobbiamo solo determinare la valuta di un utente, ma il suo paese di origine, dal momento che i diversi paesi e valute possono essere gestiti in modo diverso. Il formato coerente scelto è 1.234.00. Questo non può essere modificato.

**Perché non è possibile visualizzare il simbolo di valuta per la valuta selezionata?**

[!DNL Salesforce] e [!DNL Dynamics] visualizza i relativi importi con il codice di conversione a 3 lettere. Per coerenza, i nostri importi convertiti vengono visualizzati anche con il Codice di Conversione a 3 lettere e non con il simbolo.

**Cosa vedrà il mio cliente se non ha abilitato più valute?**

Se il cliente non dispone della funzionalità multi-valuta, verrà impostato il valore predefinito per le impostazioni internazionali della valuta dal CRM e verranno modificati tutti i codici ISO che mostrano le spese e i ricavi nella valuta aziendale. Se questo non è corretto e il cliente ha un uso misto di valuta, la soluzione sarebbe quella di aggiornare per ottenere la funzionalità multi-valuta.

**In che modo questa funzione influisce sui rapporti basati su punti di contatto nel CRM?**

Per [!DNL Dynamics] e [!DNL Salesforce] i clienti che utilizzano solo la gestione della valuta di base (non avanzata), gli importi dei ricavi dei punti di contatto devono essere convertiti correttamente, pertanto i rapporti CRM devono funzionare come previsto.

Purtroppo c&#39;è qualche sfumatura nel modo in cui funziona per gli utenti di [!DNL Salesforce] Gestione avanzata delle valute, a causa di una limitazione di lunga data [!DNL Salesforce]. La risposta breve a &quot;cosa facciamo in questo caso&quot; è che convertiamo gli importi delle entrate utilizzando i tassi forfettari definiti nella scheda &quot;Gestisci valute&quot; di base (cioè non avanzate). In altre parole, ignoriamo del tutto i vecchi tassi di cambio nonostante il fatto che il cliente abbia definito tassi di cambio datati.

Per il lettore interessato, ecco perché funziona in questo modo. I nostri punti di contatto utilizzano campi formula per calcolare i ricavi (derivati dalla quantità di opportunità associata). [!DNL Salesforce] supporta in modo nativo la conversione della valuta per questi calcoli di formula, ma solo per il loro gusto di base di supporto della valuta. È impossibile per noi definire un campo formula che faccia riferimento ai tassi di cambio datati. [!DNL Salesforce] semplicemente non supporta tale capacità, pertanto non abbiamo modo di fare riferimento ai tassi obsoleti nel calcolo dei ricavi, nonostante il fatto che tali tassi scaduti esistano in [!DNL Salesforce] (sembra folle ma è così che funziona.)

**Se il mio cliente ha utilizzato un flusso di lavoro per compilare un campo convertito, come dovrebbe procedere l’utilizzo di questo campo?**

Poiché la nostra offerta gestirà le conversioni per il cliente, si consiglia di rimuovere i flussi di lavoro e il campo personalizzato e di importare il valore dell’importo non elaborato.
