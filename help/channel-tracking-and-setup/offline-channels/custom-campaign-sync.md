---
unique-page-id: 18874588
description: Sincronizzazione campagna personalizzata - [!DNL Marketo Measure] - Documentazione del prodotto
title: Sincronizzazione campagna personalizzata
exl-id: 66f0e4e3-c1b6-443e-8ffa-06b67862b855
source-git-commit: 02f686645e942089df92800d8d14c76215ae558f
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%

---

# Sincronizzazione campagna personalizzata {#custom-campaign-sync}

Oggi, con l&#39;installato [!DNL Marketo Measure] Puoi indicare quali campagne includere come punto di contatto idoneo. Ci sono diversi ostacoli a questo come esisteva in precedenza. Una volta che [!DNL Marketo Measure] Il pacchetto è installato nel CRM, può richiedere tempo per essere approvato dal team di sicurezza. Inoltre, l’utilizzo di un singolo elenco di selezione sull’oggetto Campaign risulta poco flessibile. Con questa nuova funzione, non è necessaria un’installazione del pacchetto per iniziare a utilizzare i record dei membri di Campaign e Campaign. Le regole possono essere create per definire esattamente quali record possono essere generati per definire esattamente quali record sono idonei.

## Requisiti {#requirements}

* La sincronizzazione delle campagne è disponibile in tutti i livelli
* Per importare i dati, è comunque necessario collegare il CRM al proprio [!DNL Marketo Measure] account

## Come funziona {#how-it-works}

1. Con le autorizzazioni AccountAdmin, puoi passare a **[!UICONTROL Settings]** > **[!UICONTROL Campaigns]** e consulta l’interfaccia utente delle regole per i membri della campagna di sincronizzazione .
1. Fai clic sul pulsante **+** per iniziare a creare una regola.

   ![](assets/1-1.png)

1. Puoi creare una regola da [!UICONTROL Campaign] o [!UICONTROL Campaign Member] campi. Compila il resto della regola con l’operatore e il valore che ci aspettiamo di convalidare. Nell’esempio seguente, stiamo verificando la presenza di una campagna specifica per nome.

   ![](assets/2-1.png)

   >[!NOTE]
   >
   >I campi Formula non possono essere utilizzati all&#39;interno delle regole e non verranno visualizzati nell&#39;elenco a discesa. Poiché le formule si calcolano in background e non modificano un record, [!DNL Marketo Measure] impossibile rilevare se un record soddisfa una regola o meno.

1. Scegliere la data del punto di contatto. Dopo aver inserito una parentesi graffa, viene visualizzato l’elenco delle date possibili `{` - quindi puoi selezionare la data che desideri applicare a tutti i punti di contatto creati dalla regola.

   ![](assets/3-1.png)

   >[!NOTE]
   >
   >Se utilizzi regole di sincronizzazione di campagne personalizzate, [!DNL Marketo Measure] non leggerà gli aggiornamenti che hai effettuato utilizzando il pulsante Aggiorna in blocco data punto di contatto .

1. Fai clic sul segno di spunta, quindi aggiungi ulteriori regole per le campagne aggiuntive in base alle esigenze.

   ![](assets/4-1.png)

   >[!NOTE]
   >
   >Ora che le regole sono definite insieme a CRM Sync, le regole che sono indicate cominceranno naturalmente a entrare in conflitto. Se scegli di continuare a utilizzare sia la sincronizzazione personalizzata di Campaign _e_ Tipo di sincronizzazione CRM, è fondamentale creare regole in modo che i tuoi tipi di sincronizzazione CRM non vengano ignorati.

   ![](assets/5-1.png)

   >[!NOTE]
   >
   >Se stai valutando di interrompere l&#39;utente del [!UICONTROL CRM Sync Type], è ideale creare regole che non fanno riferimento al &quot;Tipo di sincronizzazione&quot; ma _fermo_ mantiene i punti di contatto CRM correnti. In questo modo le regole continuano a funzionare se/quando viene effettuato l’interruttore.

Ecco un esempio di come dovrebbe essere, in modo che nessun punto di contatto CRM esistente venga perso:

## Convalida {#validation}

Puoi controllare facilmente i record Buyer Touchpoints e Buyer Attribution Touchpoint all’interno di Campaign per garantire che le regole funzionino correttamente. Ecco un BAT che [!DNL Marketo Measure] creato con la data del punto di contatto dinamico appropriata, estratto dalla campagna. Il campo Data creazione si trova nell&#39;immagine sottostante.

![](assets/6-1.png)

## Test {#testing}

1. La funzione di sincronizzazione delle campagne include una funzione di test che ti consente di verificare se le regole create soddisfano effettivamente i criteri di Campaign. Inizia facendo clic sul pulsante [!UICONTROL Test] pulsante . Prima di poter iniziare il test, è necessario salvare le regole.

   ![](assets/7-1.png)

   Viene visualizzato un pop-up in cui puoi inserire un ID campagna (15 o 18 caratteri dal CRM) da testare. Il punto è quello di inserire l&#39;ID campagna dal CRM che stavi cercando di sincronizzare per assicurarti che corrisponda alla regola creata.

   ![](assets/8-1.png)

1. Dopo aver fatto clic su [!UICONTROL Test], vedrai il nome della campagna e il numero di membri della campagna idonei per i punti di contatto. Segue una tabella che mostra tutte le regole che corrispondono al tuo ID campagna. Verranno visualizzate solo le corrispondenze.

   ![](assets/9.png)

1. Puoi anche fare clic sul conteggio dei membri per visualizzare un elenco dei lead e dei contatti e dei relativi ID che fanno parte dell’idoneità della regola Campaign. Questo è solo un set di campioni e verrà visualizzato fino a 50 in modo da poter ottenere un&#39;idea di quali record sono qualificati.

   ![](assets/10.png)
