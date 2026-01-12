---
description: Domande frequenti sul modello di apprendimento automatico - [!DNL Marketo Measure]
title: Domande frequenti sul modello di apprendimento automatico
exl-id: 2fc142b2-8ac4-4c48-a8f1-398e29ccfe97
feature: Custom Models
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 0%

---


# Domande frequenti sul modello di apprendimento automatico {#machine-learning-model-faq}

Il modello di apprendimento automatico [!DNL Marketo Measure] utilizza i dati dei punti di contatto per calcolare la quantità di ponderazione dell&#39;attribuzione da assegnare a ogni fase. Ciò è determinato dall&#39;importanza di ciascuna fase nel portare a termine le offerte.

Quali sono le percentuali di attribuzione indicate dal modello di apprendimento automatico per ciascuna fase?

Le percentuali di attribuzione di ogni fase riflettono il potenziale impatto delle attività di marketing. Una percentuale più elevata significa che il marketing può influenzare direttamente il movimento del funnel a quel punto. Una percentuale di attribuzione inferiore indica che le fasi sono meno importanti per il monitoraggio del team.

Come viene calcolato il modello di apprendimento automatico?

[!DNL Marketo Measure] calcola l&#39;importanza di ogni fase personalizzata utilizzando i dati del punto di contatto del tuo account. I criteri utilizzati per determinare l&#39;importanza di ciascuna fase sono i seguenti:

* Precisione del modello: se costruiamo un modello predittivo con i dati dei punti di contatto per prevedere se alla fine vinceremo un’offerta, quanto sarà accurato il modello? Una maggiore precisione predittiva significa che i dettagli di questa fase sono più correlati con la chiusura o meno di un’offerta
* Tasso di conversione: se lead o opportunità in questa fase vengono convertiti alla fase successiva a un tasso elevato, ciò suggerisce che le attività di marketing che si sono verificate in questa fase non hanno avuto molta importanza. Al contrario, se una certa fase converte alla fase successiva con un tasso basso, ciò può suggerire che le attività di marketing che si sono verificate in questa fase sono state influenti nel promuovere la conversione.
* Peso di unicità del punto di contatto: se una fase si verifica come transizione autonoma, ovvero non vi sono state altre transizioni di fase che si sono verificate contemporaneamente, questa fase potrebbe ricevere un peso di attribuzione più elevato. Al contrario, se un punto di contatto per una fase viene condiviso con altre fasi (ad esempio, il punto di contatto condivide le fasi Primo contatto, Conversione lead e Conversione opportunità) questa fase potrebbe ricevere una ponderazione di attribuzione inferiore.

Il peso finale per una fase personalizzata viene calcolato come tale:

**_Percentuale modello = Precisione modello x Tasso di conversione x Peso di unicità punto di contatto_**

Alla fine, tutti i pesi degli stadi personalizzati vengono normalizzati e convertiti in % come mostrato di seguito.

Perché non viene visualizzato alcun numero nella colonna Machine Learning?

Quando il modello di attribuzione personalizzata è abilitato per il tuo account, in genere l’esecuzione e la generazione di questi numeri da parte del modello variano da 3 a 7 giorni in base ai dati storici.

Con quale frequenza viene aggiornato il modello di apprendimento automatico?

Il modello viene rieseguito ogni 7 giorni.

Perché il modello imposta sempre il valore di Middle Touch (Contatto intermedio) al 10%?

L’assegnazione di un credito di attribuzione del 10% a Middle Touches è un’impostazione standard in tutti i nostri modelli di attribuzione.

Quando devo modificare la distribuzione dell’attribuzione?

Rivolgiti al tuo account manager per discutere le implicazioni della modifica delle percentuali di attribuzione e quali fasi includere nel modello personalizzato. Ogni [!DNL Salesforce] e processo di vendita è univoco e vogliamo garantire che il modello personalizzato sia modellato in modo accurato.

Detto questo, abbiamo identificato alcune tendenze generali nei nostri clienti:

Una tendenza che abbiamo notato è che non è sempre utile includere più fasi nel modello. Ad esempio, quando i clienti hanno aggiunto più fasi di opportunità verso il fondo di funnel, queste fasi tendono a ricevere valori percentuali di attribuzione molto bassi. Valori percentuali bassi indicano un alto tasso di conversione, che in genere significa che queste fasi non hanno lo stesso impatto sulla chiusura delle offerte. Alcuni clienti alla fine decidono di non includere queste fasi in funnel. Se si decide di rimuovere uno stadio dal modello di attribuzione, il modello di macchina ricalcola e ridistribuisce le percentuali.

Abbiamo anche notato che c’è un alto tasso di conversione dalla creazione di lead alle fasi qualificate per il marketing, e di conseguenza, la fase qualificata per il marketing potrebbe ricevere una ponderazione di attribuzione in percentuale più bassa. A seconda del ciclo commerciale e di vendita, può essere utile rimuovere questa fase dal modello personalizzato.

Tieni presente che se desideri tenere traccia delle attività di marketing attraverso una transizione di fase specifica, ma non vuoi che questa fase riceva un credito di attribuzione, puoi includere questa fase nel modello e assegnare un credito di attribuzione dello 0% a quella fase.
