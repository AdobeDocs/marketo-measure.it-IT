---
unique-page-id: 18874775
description: Domande frequenti sul modello di apprendimento automatico - [!DNL Marketo Measure] - Documentazione del prodotto
title: Domande frequenti sul modello di apprendimento automatico
exl-id: 2fc142b2-8ac4-4c48-a8f1-398e29ccfe97
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# Domande frequenti sul modello di apprendimento automatico {#machine-learning-model-faq}

La [!DNL Marketo Measure] Il modello di apprendimento automatico utilizza i dati dei punti di contatto per calcolare la ponderazione dell’attribuzione da assegnare a ogni fase. Ciò è determinato dall&#39;importanza di ogni fase nella conclusione delle trattative.

Cosa mi dicono le percentuali di attribuzione del modello di apprendimento automatico su ogni fase?

Le percentuali di attribuzione di ogni fase riflettono il potenziale impatto delle tue attività di marketing. Una percentuale più elevata significa che il marketing può influenzare direttamente lo spostamento dell&#39;imbuto in quel momento. Una percentuale di attribuzione inferiore indica che le aree di visualizzazione sono meno importanti per il controllo da parte del team.

Come viene calcolato il modello di apprendimento automatico?

[!DNL Marketo Measure] calcola l’importanza di ogni fase personalizzata utilizzando i dati del punto di contatto dell’account. I criteri utilizzati per determinare l&#39;importanza di ciascuna fase sono i seguenti:

* Precisione del modello: Se costruiamo un modello predittivo con i dati dei punti di contatto per prevedere se alla fine vinceremo un accordo, quanto sarà preciso il modello? Una maggiore precisione predittiva significa che i dettagli di questa fase sono più correlati al fatto che un accordo si chiuderà
* Tasso di conversione: Se i Lead o le Opportunità in questa fase si convertono nella fase successiva ad un tasso elevato, ciò suggerisce che le attività di marketing che si sono verificate in questa fase non importavano molto. Al contrario, se una determinata fase converte alla fase successiva a un tasso basso, ciò può suggerire che le attività di marketing che si sono verificate in questa fase sono state influenzabili nel promuovere la conversione.
* Peso dell&#39;unità del punto di contatto: Se un passaggio si verifica come transizione autonoma, il che significa che non vi erano altre transizioni di stage che si sono verificate nello stesso momento, questo passaggio potrebbe ricevere un maggiore peso di attribuzione. Al contrario, se un punto di contatto per un’area di visualizzazione viene condiviso con altre fasi (ad esempio, il punto di contatto condivide le fasi Primo contatto, Conversione lead e Conversione opportunità), questa fase potrebbe ricevere una ponderazione di attribuzione inferiore.

Il peso finale di una fase personalizzata viene calcolato come tale:

**_Percentuale modello = Precisione del modello x Tasso di conversione x Peso dell&#39;univocità del punto di contatto_**

Alla fine, tutti i pesi personalizzati dello stadio vengono normalizzati e convertiti in % come mostrato di seguito.

Perché non vedo numeri nella colonna Apprendimento automatico?

Quando il modello di attribuzione personalizzato è abilitato per l’account, in genere l’esecuzione e la generazione di tali numeri richiede tra 3 e 7 giorni, in base ai dati storici.

Con quale frequenza viene aggiornato il modello di apprendimento automatico?

Rieseguiamo il modello ogni 7 giorni.

Perché il modello imposta sempre i punti intermedi al 10%?

L’assegnazione di un credito di attribuzione del 10% ai punti a termine è un’impostazione standard per tutti i nostri modelli di attribuzione.

Quando devo modificare la distribuzione dell’attribuzione?

Rivolgiti al tuo account manager per discutere le implicazioni della modifica delle percentuali di attribuzione e le fasi da includere nel modello personalizzato. Ogni [!DNL Salesforce] e il processo di vendita è unico e vogliamo garantire che il modello personalizzato sia modellato in modo accurato.

Detto questo, abbiamo identificato alcune tendenze generali tra i nostri clienti:

Una tendenza che abbiamo notato è che non sempre è utile includere più fasi nel vostro modello. Ad esempio, quando i clienti hanno aggiunto più fasi Opportunità verso la parte inferiore del funnel, queste fasi tendono a ricevere valori percentuali di attribuzione molto bassi. Valori percentuali bassi indicano un alto tasso di conversione, il che significa che queste fasi non hanno lo stesso impatto sulla conclusione delle offerte. Alcuni clienti decidono infine di non includere queste fasi nel funnel. Se decidi di rimuovere un passaggio dal modello di attribuzione, il modello di computer ricalcola e ridistribuisce le percentuali.

Abbiamo anche notato che c&#39;è un alto tasso di conversione dalla creazione di lead alle fasi qualificate per il marketing, e di conseguenza, lo stadio Qualificato per il marketing potrebbe ricevere una ponderazione percentuale inferiore. A seconda del ciclo di business e di vendita, può essere utile rimuovere questa fase dal modello personalizzato.

Tieni presente che se desideri tenere traccia delle attività di marketing attraverso una transizione di fase specifica ma non desideri che questa fase riceva un credito di attribuzione, puoi includere questa fase nel modello e assegnare un credito di attribuzione allo 0% a tale fase.
