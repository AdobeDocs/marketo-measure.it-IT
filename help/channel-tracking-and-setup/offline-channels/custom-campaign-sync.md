---
description: Indicazioni di sincronizzazione di Campaign personalizzate per gli utenti di Marketo Measure
title: Sincronizzazione campagna personalizzata
exl-id: 66f0e4e3-c1b6-443e-8ffa-06b67862b855
feature: Channels
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 0%

---

# Sincronizzazione campagna personalizzata {#custom-campaign-sync}

Oggi, con il pacchetto [!DNL Marketo Measure] installato, è possibile indicare quali campagne includere come punto di contatto idoneo. Ci sono diversi ostacoli a questo come in precedenza esisteva. Una volta installato il pacchetto [!DNL Marketo Measure] nel CRM, l&#39;approvazione da parte del team di sicurezza potrebbe richiedere del tempo. Inoltre, l’utilizzo di un singolo elenco di selezione sull’oggetto Campaign non è flessibile. Con questa nuova funzionalità, non è necessario installare un pacchetto per iniziare a utilizzare i record dei membri di Campaign e Campaign. È possibile creare regole per definire esattamente quali record possono essere generati per definire esattamente quali record sono idonei.

## Requisiti {#requirements}

* La sincronizzazione delle campagne è disponibile in tutti i livelli
* Per importare i dati, è comunque necessario collegare il CRM all&#39;account [!DNL Marketo Measure]

## Come funziona {#how-it-works}

1. Con le autorizzazioni AccountAdmin, puoi passare a **[!UICONTROL Settings]** > **[!UICONTROL Campaigns]** e visualizzare l’interfaccia utente delle regole di sincronizzazione dei membri della campagna.
1. Fai clic sull&#39;icona **+** per iniziare a creare una regola.

   ![](assets/offline-channels-1.png)

1. È possibile creare una regola dai campi [!UICONTROL Campaign] o [!UICONTROL Campaign Member]. Compila il resto della regola con l’Operatore e il Valore che si prevede di convalidare. Nell’esempio seguente, stiamo verificando la presenza di una specifica campagna in base al suo nome.

   ![](assets/offline-channels-10.jpg)

   >[!NOTE]
   >
   >I campi formula non possono essere utilizzati nelle regole e non verranno visualizzati nell&#39;elenco a discesa. Poiché le formule vengono calcolate in background e non modificano un record, [!DNL Marketo Measure] non è in grado di rilevare se un record soddisfa o meno una regola.

1. Scegliere la data del punto di contatto. L&#39;elenco delle date possibili verrà visualizzato dopo l&#39;immissione di una parentesi graffa `{`, quindi è possibile selezionare la data che si desidera applicare a tutti i punti di contatto creati dalla regola.

   ![](assets/offline-channels-11.png)

   >[!NOTE]
   >
   >Se si utilizzano le regole di sincronizzazione delle campagne personalizzate, [!DNL Marketo Measure] non leggerà gli aggiornamenti effettuati utilizzando il pulsante Bulk Update Touchpoint Date (Aggiorna data punto di contatto in blocco).

1. Fai clic sul segno di spunta, quindi aggiungi ulteriori regole per le campagne aggiuntive in base alle esigenze.

   ![](assets/offline-channels-12.png)

   >[!NOTE]
   >
   >Ora che le regole sono definite insieme alla sincronizzazione CRM, le regole dichiarate inizieranno naturalmente a entrare in conflitto. Se si sceglie di continuare a utilizzare sia la sincronizzazione campagna personalizzata _che_ il tipo di sincronizzazione CRM, è fondamentale creare regole in modo che i tipi di sincronizzazione CRM non vengano ignorati.

   ![](assets/offline-channels-13.png)

   >[!NOTE]
   >
   >Se stai valutando la possibilità di arrestare l&#39;utente di [!UICONTROL CRM Sync Type], è consigliabile creare regole che non facciano riferimento al &quot;Tipo di sincronizzazione&quot; ma che _mantengano_ i punti di contatto CRM correnti. In questo modo le regole funzionano ancora se/quando viene effettuato il passaggio.

Ecco un esempio di come apparirebbe, in modo che non vadano persi punti di contatto CRM esistenti:

## Convalida {#validation}

Puoi controllare facilmente i punti di contatto dell’acquirente e i record di Buyer Attribution Touchpoint all’interno di Campaign per verificare che le regole funzionino correttamente. Ecco un BAT creato da [!DNL Marketo Measure] con la data del punto di contatto dinamico appropriata, estratto dalla campagna. Il campo Data di creazione è nell&#39;immagine sottostante.

![](assets/offline-channels-14.png)

## Test {#testing}

1. La funzione di sincronizzazione di Campaign è dotata di una funzione di test che consente di verificare se le regole create soddisfano effettivamente i criteri di Campaign. Iniziare facendo clic sul pulsante [!UICONTROL Test]. Prima di iniziare il test, è necessario salvare le regole.

   ![](assets/offline-channels-15.jpg)

   Verrà visualizzato un pop-up in cui puoi immettere un ID campagna (15 o 18 caratteri dal CRM) da testare. Il punto è quello di inserire l’ID campagna dal sistema di gestione delle relazioni con i clienti che stavi tentando di sincronizzare per assicurarti che corrisponda alla regola creata.

   ![](assets/offline-channels-16.png)

1. Dopo aver fatto clic su [!UICONTROL Test], verranno visualizzati il nome della campagna e il numero di membri della campagna idonei per i punti di contatto. Di seguito verrà visualizzata una tabella che mostra tutte le regole che corrispondono al tuo ID campagna. Verranno visualizzate solo le corrispondenze.

   ![](assets/offline-channels-17.png)

1. È inoltre possibile fare clic sul conteggio dei membri per visualizzare un elenco dei lead e dei contatti e dei relativi ID che fanno parte dell’idoneità della regola Campaign. Questo è solo un set di esempio e visualizzerà fino a 50 in modo da poter avere un’idea di quali record sono idonei.

   ![](assets/offline-channels-18.jpg)
