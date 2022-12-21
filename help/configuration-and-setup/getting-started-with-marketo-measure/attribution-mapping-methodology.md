---
unique-page-id: 18874716
description: Metodologia di mappatura dell’attribuzione - [!DNL Marketo Measure] - Documentazione del prodotto
title: Metodologia di mappatura dell’attribuzione
exl-id: 4d54dd20-9a82-4b87-8908-ced2bd9c0f2f
source-git-commit: 993a326c377b3b6ff48c4e0114b59297f9ca2ca6
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 0%

---

# Metodologia di mappatura dell’attribuzione {#attribution-mapping-methodology}

La metodologia di mappatura dell’attribuzione è il processo di ricerca di determinati oggetti nel CRM (Contatti, Opportunità, Account) per creare punti di contatto di attribuzione nell’opportunità associata. In altre parole, è il [!DNL Marketo Measure] modo per comprendere quali punti di contatto includere nel modello di attribuzione in base ai processi CRM correnti.

## Mappatura degli ID account {#account-id-mapping}

Fuori dalla scatola, [!DNL Marketo Measure] fornisce la mappatura dell&#39;ID account. Ciò significa che [!DNL Marketo Measure] esamina le informazioni di marketing Account e Contatti per creare punti di contatto di attribuzione associati all’opportunità. Di seguito è riportata una semplice rappresentazione del processo.

![](assets/1-1.png)

Tieni presente che **non tutti** i punti di contatto dei contatti verranno inseriti nell’opportunità come punti di contatto di attribuzione. La timeline dell’opportunità (data di primo contatto - data di chiusura) determina se un punto di contatto verrà conteggiato come influenziatore dell’opportunità. Pertanto, se un punto di contatto sul contatto A si è verificato dopo la chiusura dell’opportunità, è stato vinto/perso, [!DNL Marketo Measure] non invierà tale punto di contatto all’opportunità. Questa procedura della timeline viene seguita in tutte le altre mappature degli oggetti di attribuzione.

Pro: Questo metodo di attribuzione è molto efficace per la maggior parte delle aziende. Il team marketing non deve affidarsi al team di vendita per associare tutti i contatti a una particolare opportunità (che spesso è un problema). Inoltre, anche se un team di vendita associa ruoli di contatto, molte altre interazioni di contatto con materiali di marketing potrebbero essere perse. Infine, questo metodo aiuta le strategie ABM che si sforzano di influenzare la totalità di un conto, piuttosto che specifici influenzatori.

Cons: Se ci sono degli SLA di Marketing e Vendite forti che definiscono chi deve ricevere credito per cosa, allora questo metodo potrebbe essere problematico. Inoltre, se le persone non utilizzano gerarchie di account per definire unità di business specifiche all&#39;interno di un conto più grande (ad esempio: IBM), le interazioni di marketing specifiche per una business unit possono essere distribuite su altre opportunità di business unit.

## Mappatura del ruolo del contatto opportunità {#opportunity-contact-role-mapping}

Mentre la maggior parte dei client utilizza la mappatura degli ID account, [!DNL Marketo Measure] può cercare i ruoli di contatto (contatti associati all’opportunità) all’interno di un’opportunità per suddividere il processo di attribuzione. Ciò significa che [!DNL Marketo Measure] invierà solo le interazioni di marketing associate ai ruoli di contatto nell’opportunità come punti di contatto di attribuzione dell’acquirente. Di seguito è riportata una rappresentazione di questo processo.

![](assets/2-1.png)

Pro: Se il tuo team dispone di un processo di ruoli di contatto molto ben definito, questo tipo di mappatura dell’attribuzione potrebbe essere ideale per te. Aiuterà ad allineare un po&#39; di più le vendite e il marketing, in quanto tutti comprenderebbero appieno come l’attribuzione viene suddivisa. Questo processo è molto utile anche quando le organizzazioni si rivolgono a più business unit all&#39;interno di una grande azienda e quando vendono allo stesso tempo prodotti diversi.

Cons: Tuttavia, se non è in atto un processo per il ruolo di contatto, il marketing perderà molti dati di marketing e il team finirà per ricevere molto meno credito per le attività di marketing che stanno influenzando le opportunità.

## Mappatura del ruolo di contatto principale opportunità {#opportunity-primary-contact-role-mapping}

Oltre a guardare semplicemente i ruoli di contatto sull&#39;opportunità, [!DNL Marketo Measure] può concentrarsi ancora di più per guardare solo i contatti principali su un&#39;opportunità. Con questa configurazione, [!DNL Marketo Measure] acquisirà solo il punto di contatto marketing associato ai contatti principali su un’opportunità e inserirà tali informazioni nel racconto di attribuzione di tale opportunità specifica. Vedi l&#39;immagine seguente.

![](assets/3.png)

Pro: Se il tuo team è interessato solo a comprendere l&#39;influenza di marketing sui contatti impostati come &quot;primari&quot; sull&#39;opportunità, questo tipo di mappatura si adatta al meglio al team.

Cons: Questo è certamente il processo di mappatura meno utilizzato e può minare fortemente l&#39;influenza di marketing che sta spostando l&#39;ago attraverso altri contatti su un&#39;opportunità.
