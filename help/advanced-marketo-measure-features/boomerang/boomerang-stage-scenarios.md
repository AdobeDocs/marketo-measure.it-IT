---
unique-page-id: 18874692
description: Scenari di stadio di Boomerang - [!DNL Marketo Measure] - Documentazione del prodotto
title: Scenari di stadio di Boomerang
exl-id: 150db070-eef5-4741-845c-775ab4034ead
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '1683'
ht-degree: 0%

---

# Scenari di stadio di Boomerang {#boomerang-stage-scenarios}

Di seguito sono riportati alcuni esempi di scenari di Boomerang Stage per fornire una comprensione di come [!DNL Marketo Measure] creerà punti di contatto in ogni situazione.

## Scenari singoli lead {#single-lead-scenarios}

**Scenario 1: Punti di contatto Boomerang standard per un lead**

Questo è lo scenario più semplice di Boomerang. La riga superiore (con l’etichetta Lead 1) rappresenta il percorso dei singoli lead e il modo in cui i relativi punti di contatto vengono visualizzati nel record Lead. La riga in basso (Opportunità) mostra come i punti di contatto dei lead si traducono nell’opportunità. La progressione dei punti di contatto sarà spiegata in caso cronologico, da sinistra a destra.

In questo scenario, un cliente ha scelto di **MQL** e **SQL** stadi tracciati con Boomerang. Ogni posizione del punto di contatto Boomerang sarà etichettata con lo stadio e il numero in cui si verifica (MQL-01, SQL-01, MQL-02. ecc.). L’ultimo punto di contatto boomerang per quel palco avrà anche &quot;(Ultimo)&quot; nella posizione del punto di contatto.

Il lead 1 viene quindi convertito in un contatto con un’opportunità, che viene considerato il tocco OC.

![](assets/1-1.png)

**Scenario 2: Punti di contatto Boomerang e stadi personalizzati per un lead**

In questo scenario, un cliente ha scelto solo di tenere traccia del **Fase SQL** con punti di contatto boomerang. Le fasi MQL e SAL sono ancora in fase di tracciamento, ma con [!DNL Marketo Measure] Funzione Stage personalizzata.

![](assets/2-1.png)

La posizione del punto di contatto MQL non è contrassegnata da un numero. Questo perché non è stato selezionato per essere tracciato con i punti di contatto Boomerang. Durante la creazione di punti di contatto per le aree di visualizzazione incluse nel modello personalizzato, ma non vengono tracciati con Boomerang, [!DNL Marketo Measure] prenderà l&#39;ultima occorrenza da quel momento.

Nel caso della fase SAL, [!DNL Marketo Measure] ignora le prime due occorrenze di questo passaggio. [!DNL Marketo Measure] crea un solo punto di contatto SAL per _last_ occorrenza. Nell’esempio precedente, questo accade immediatamente prima del punto di contatto OC.

La fase SQL viene monitorata con i punti di contatto Boomerang e sono stati creati e etichettati di conseguenza tre punti di contatto.

Il lead 1 viene quindi convertito in un contatto con un’opportunità, che viene considerato il tocco OC.

**Scenario 3: Quando i lead non raggiungono/saltano un’area di visualizzazione**

Questo scenario utilizza gli stessi criteri dello scenario 2. Un cliente ha scelto solo di tenere traccia della fase SQL con punti di contatto boomerang. MQL e SAL ancora in fase di tracciamento, ma con il [!DNL Marketo Measure] Funzione Stage personalizzata.

![](assets/3.png)

In questo scenario, il lead non passa mai effettivamente alla fase SAL. Si converte in un contatto prima di raggiungere la fase SAL, essenzialmente &quot;saltando&quot; la fase SAL. In tale situazione, [!DNL Marketo Measure] si presume che l’SAL si verifichi con il punto di contatto OC e che la posizione SAL e OC sia visualizzata sullo stesso punto di contatto.

Il lead 1 viene quindi convertito in un contatto con un’opportunità, che viene considerato il tocco OC.

## Scenari con più lead {#scenarios-with-multiple-leads}

I seguenti scenari sono quelli in cui Boomerang Stages può diventare più complicato, in quanto stiamo cercando di vedere come più Lead possono influenzare il percorso Opportunità.

La riga superiore (con etichetta Lead 1, in blu) rappresenta il percorso dei singoli Lead e il modo in cui i relativi punti di contatto vengono visualizzati nel record Lead. Lo stesso vale per il piombo 2 (in rosa) e il piombo 3 (in arancione). La riga in basso (Opportunità) mostra come entrambi i punti di contatto di questi lead si traducono nell’opportunità. La progressione dei punti di contatto sarà spiegata in caso cronologico, da sinistra a destra.

**Scenario 1:[!UICONTROL Three Leads with Opportunity]**

In questo scenario, un cliente ha scelto di tenere traccia delle **MQL** e **Fasi SAL** con punti di contatto boomerang. Lo stadio SQL viene tracciato dalle fasi personalizzate standard.

![](assets/4.png)

I punti di contatto FT e LC sull&#39;opportunità verranno da Lead 1 (blu), perché si sono verificati prima del FT e LC di Lead 2 (rosa). Il punto di contatto LC per Lead 2 verrà visualizzato come punto di contatto &quot;Modulo&quot; sull’opportunità.

L’MQL-01 (Ultimo) da Lead 2 diventerà il primo MQL sull’opportunità. L’MQL-01 da Lead 1 non verrà visualizzato come punto di contatto sull’opportunità perché l’MQL di Lead 2 si è verificato per primo. Tuttavia, MQL-02 e MQL-03 di Lead 1 verranno visualizzati sull&#39;opportunità.

Tenere presente che lo stadio SQL viene tracciato con stadi personalizzati e non con quelli boomerang. Anche se ci sono tre occorrenze dello stadio SQL tra Lead 1 e Lead 2, solo l’ultima occorrenza SQL verrà inclusa come punto di contatto sull’opportunità.

Il punto di contatto SAL-01 (Ultimo) da Lead 1 viene riportato come punto di contatto sull’opportunità. Il lead 1 viene quindi convertito in un contatto con un’opportunità, che viene considerato il tocco OC. Il punto di contatto SAL-01 (Ultimo) del lead 2 verrà creato come punto di contatto in quanto si è verificata questa transizione _dopo_ il tocco OC.

I punti di contatto FT, LC e MQL, SQL, SAL (arancione) di Lead 3 si sono verificati dopo il punto di contatto OC sull&#39;opportunità. Questi punti di contatto saranno inclusi nell’opportunità, ma sono considerati come &quot;punti di contatto centrali&quot;.

Se il lead 2 e 3 sono convertiti in contatti, [!DNL Marketo Measure] non creerà un altro punto di contatto OC perché può esserci una sola fase di creazione delle opportunità.

**Scenario 2 -[!UICONTROL Three Leads with Opportunity]**

In questo scenario, un cliente ha scelto di tenere traccia delle **MQL**, **SQL** e **SAL** stadi con punti di contatto boomerang.

Tutti i punti di contatto da Lead 1 saranno inclusi nell’opportunità, da FT a SAL-01 (Last). Il punto di contatto LC da Lead 2 sarà incluso come punto di contatto Modulo tra i punti di contatto LC e MQL-01 sull’opportunità.

![](assets/5.png)

L’MQL-01 (Ultimo) da Lead 2 finisce per essere il punto di contatto MQL-04 (Ultimo) sull’opportunità. Poiché in questo scenario vengono esaminati più percorsi di lead all’interno di un’unica opportunità, il posizionamento e la numerazione dei punti di contatto dei lead può variare quando vengono tradotti come punti di contatto nell’opportunità. Analogamente, il SQL-01 (Ultimo) dal lead 2 diventa il SQL-04 (Ultimo) nell&#39;Opp. SAL-01 (Ultimo) del lead 2 diventa anche il SAL-02 dell&#39;opportunità (Ultimo).

Inoltre, noterai che nell’opportunità sono inclusi solo 2 punti di contatto SAL. [!DNL Marketo Measure] non tenterà di forzare/creare punti di contatto per le transizioni di stage, se non si sono verificate effettivamente.

Il percorso dei punti di contatto del piombo 3 inizia poco prima del contatto OC, ma molto tempo dopo il contatto FT e LC del lead 1 e del lead 2. In questo caso, FT e LC di Lead 3 appariranno come punto di contatto Modulo sull’opportunità. Il lead 1 viene quindi convertito in un contatto con un’opportunità, che viene considerato il tocco OC.

I contatti MQL, SQL e SAL del lead 3 si verificano contemporaneamente, dopo il tocco OC. Poiché si sono verificati dopo il punto di contatto OC, questo punto di contatto verrà visualizzato come un punto di contatto Form/Middle sull&#39;opportunità anziché come una transizione della fase Boomerang.

**Scenario 2a - Punti di contatto per le visite web Boomerang**

In questo scenario, un cliente ha scelto di tenere traccia delle **MQL**, **SQL** e **SAL** stadi con punti di contatto boomerang. Questo scenario è quasi identico a quello precedente, con alcune eccezioni.

![](assets/6.png)

Tutti i punti di contatto da Lead 1 saranno inclusi nell’opportunità, da FT a SAL-01 (Last). Il punto di contatto LC da Lead 2 sarà incluso come punto di contatto Modulo tra i punti di contatto LC e MQL-01 sull’opportunità.

L’MQL-01 (ultima) di Lead 2 (visita web) non verrà creato come punto di contatto nell’Opp. Questo perché questo punto di contatto era una visita Web che si verifica dopo l&#39;ultima occorrenza dello stadio SQL e non aiuta a guidare l&#39;opportunità in avanti.

Lo stadio lead 1 diventa SAL e quindi viene convertito in Contatto con un’opportunità; in questo caso, la posizione SAL-01 (Last) e OC verranno combinate nello stesso punto di contatto.

Il tocco FT,LC di Lead 3 verrà creato come punto di contatto Modulo su Opp. Dopo il tocco OC, verranno create come punti di contatto solo le azioni di compilazione del modulo. Per questo motivo, le transizioni di fase SQL-01 (Ultimo) e SAL-01 (Ultimo) per Lead due non verranno create come punti di contatto, perché questi punti di contatto erano visite web.

I contatti MQL, SQL e SAL di Lead 3 verranno inclusi come punto di contatto, perché si trattava di un’azione di compilazione del modulo.

**Scenario 3 - Ponderazione attribuzione Boomerang**

In questo scenario, un cliente ha scelto di tenere traccia delle **MQL**, **SQL** e **SAL** stadi con punti di contatto boomerang.

![](assets/7.png)

I punti di contatto FT e LC sull&#39;opportunità verranno da Lead 1 (blu), perché si sono verificati prima del FT e LC di Lead 2 (rosa). Il punto di contatto LC per Lead 2 verrà visualizzato come punto di contatto &quot;Modulo&quot; sull’opportunità.

L’MQL-01 (Ultimo) da Lead 2 diventerà il primo MQL sull’opportunità. L’MQL-01 da Lead 1 non verrà visualizzato come punto di contatto sull’opportunità perché l’MQL di Lead 2 si è verificato per primo.

SQL-01 (Ultimo) dal lead 2 diventerà SQL-01 sull&#39;opportunità. SQL-01 sul lead 1 non verrà visualizzato come punto di contatto sull&#39;opportunità, perché SQL-01 sul lead 2 è stato eseguito per primo.

Tieni presente che Lead 1 è boomerang tra MQL e SQL un paio di volte prima di raggiungere infine lo stadio SAL. SQL-01, MQL-02, SQL-02, MQL-03, SQL-03 _non_ essere inclusi come punti di contatto sull&#39;opportunità, in quanto queste transizioni di fase non aiutano a far progredire l&#39;opportunità nel percorso.

Il punto di contatto SAL-01 (Ultimo) da Lead 1 sarà il prossimo punto di contatto da includere nell’Opp. Il lead 1 si converte quindi in un contatto con un’opportunità, creando il punto di contatto OC.

I punti di contatto FT e LC del lead 3 e MQL, SQL e SAL verranno visualizzati come un modulo che tocca l&#39;opportunità.

Il punto di contatto SQL-01 (Ultimo) del lead 2 non verrà incluso come punto di contatto nell’Opp perché si è verificato dopo il punto di contatto OC. Inoltre, si è verificata la transizione fase SQL del lead 2 _dopo la transizione finale della fase SAL_ e non aiuta a far progredire il percorso di opportunità.

## Scenari di opportunità {#opportunity-scenarios}

**Scenario 1 - Contatti con Opportunità e tracciamento Boomerang**

In questo scenario, un cliente ha scelto di tenere traccia delle **Transizioni della fase Demo e Negoziazione** sulla **Contatto**. Ogni stadio boomerang può ricevere fino a due punti di contatto. La differenza tra le transizioni di stage su un contatto e le transizioni di stage su un lead è che le transizioni di fase Contatto possono apparire come punti di contatto Boomerang sull’opportunità _dopo_ punto di contatto OC. Questo non è vero per le transizioni di stage che si verificano sul lead, in quanto appariranno come punto di contatto Modulo .

![](assets/8.png)

In questo esempio, le transizioni Demo e fase di negoziazione di Contact 1 sono incluse come punti di contatto Demo-01 e Negoziazione-01 sull’opportunità. Si verifica la transizione della fase Demo di Contact 2 _dopo_ Contatta 1 e viene visualizzato come punto di contatto Demo-02 (Ultimo) sull’opportunità.

Si noti che non esiste una seconda transizione alla fase di negoziazione; l’opportunità passa immediatamente da Demo-02 (Ultimo) a Chiudi won. In questo caso, [!DNL Marketo Measure] includerà la transizione Negoziazione con il punto di contatto Chiudi Won.
