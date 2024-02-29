---
unique-page-id: 18874716
description: Metodologia di mappatura attribuzione - [!DNL Marketo Measure]
title: Metodologia di mappatura attribuzione
exl-id: 4d54dd20-9a82-4b87-8908-ced2bd9c0f2f
feature: Attribution
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Metodologia di mappatura attribuzione {#attribution-mapping-methodology}

La metodologia di mappatura dell’attribuzione è il processo di ricerca di determinati oggetti nel CRM (contatti, opportunità, account) per creare punti di contatto di attribuzione nell’opportunità associata. In altre parole, è il [!DNL Marketo Measure] un modo per capire quali punti di contatto includere nel modello di attribuzione in base ai processi di gestione delle relazioni con i clienti correnti.

## Mappatura ID account {#account-id-mapping}

Pronti all’uso, [!DNL Marketo Measure] fornisce la mappatura dell’ID account. Ciò significa che [!DNL Marketo Measure] esamina le informazioni di marketing Account e Contatti per creare punti di contatto di attribuzione associati all’opportunità. Di seguito è riportata una semplice rappresentazione di tale processo.

![](assets/1-1.png)

Nota bene **non tutti** I punti di contatto dei contatti vengono inseriti nell’opportunità come punti di contatto di attribuzione. La timeline dell’opportunità (data del primo contatto, data di chiusura) determina se un punto di contatto conta come influencer sull’opportunità. Pertanto, se si è verificato un punto di contatto sul contatto A dopo che l’opportunità è stata chiusa, ovvero acquisita/persa, [!DNL Marketo Measure] non invierà il punto di contatto all’opportunità. Questa procedura timeline viene seguita in tutte le altre mappature di oggetti di attribuzione.

Pro: questo metodo di attribuzione è molto efficace per la maggior parte delle aziende. Il team marketing non deve necessariamente affidarsi al team vendite per associare tutti i contatti a una particolare opportunità (che spesso è un problema). Inoltre, anche se un team di vendita associa ruoli di contatto, molte interazioni di altri contatti con il materiale di marketing potrebbero non essere presenti. Infine, questo metodo aiuta la strategia ABM che si sforza di influenzare la totalità di un account, piuttosto che influenzatori specifici.

Contro: se esistono forti accordi sui livelli di servizio di marketing e vendita che definiscono a chi assegnare il merito per cosa, allora questo metodo potrebbe essere problematico. Inoltre, se le persone non utilizzano le gerarchie dei conti per definire specifiche unità aziendali all’interno di un conto più grande (ad esempio, IBM), le interazioni di marketing specifiche per una unità aziendale possono essere distribuite tra altre opportunità di unità aziendali.

## Mappatura ruolo contatto opportunità {#opportunity-contact-role-mapping}

Mentre la maggior parte dei clienti utilizza la mappatura degli ID account, [!DNL Marketo Measure] può cercare i ruoli di contatto (contatti associati all’opportunità) all’interno di un’opportunità per suddividere il processo di attribuzione. Ciò significa che [!DNL Marketo Measure] invierà solo le interazioni di marketing associate ai ruoli di contatto nei punti di contatto di Opportunità as Buyer Attribution. Di seguito è riportata una rappresentazione di questo processo.

![](assets/2-1.png)

Pro: se il team dispone di un processo per i ruoli di contatto ben definito, questo tipo di mappatura di attribuzione potrebbe essere ideale per te. Aiuta ad allineare le vendite e il marketing un po’ di più, in quanto tutti capirebbero appieno come l’attribuzione viene suddivisa. Questo processo è utile anche quando le organizzazioni eseguono il targeting di più business unit all’interno di una grande azienda e quando vendono contemporaneamente prodotti diversi.

Contro: tuttavia, se non è attivo alcun processo per il ruolo di contatto, il marketing perde molti dati di marketing e il team riceverà molto meno credito per le attività di marketing che influenzano le opportunità.

## Mappatura ruolo contatto principale opportunità {#opportunity-primary-contact-role-mapping}

Oltre a esaminare semplicemente i ruoli di contatto nell’opportunità, [!DNL Marketo Measure] può concentrarsi ancora di più per esaminare solo i contatti principali su un’opportunità. Tenendo presente questa configurazione, [!DNL Marketo Measure] acquisirà solo il punto di contatto di marketing associato ai contatti primari in un’opportunità e inserirà tali informazioni nella storia di attribuzione di tale opportunità specifica. Vedi l’immagine seguente.

![](assets/3.png)

Pro: se il team è interessato solo a comprendere l’influenza di marketing sui contatti impostati come &quot;primari&quot; nell’opportunità, questo tipo di mappatura è più adatto al team.

Contro: questo è sicuramente il processo di mappatura meno utilizzato e può minare notevolmente l’influenza di marketing che sta spostando l’ago attraverso altri contatti in un’opportunità.
