---
unique-page-id: 18874535
description: Transizione a [!DNL Marketo Measure] da Cerchio intero - [!DNL Marketo Measure] - Documentazione del prodotto
title: Transizione a [!DNL Marketo Measure] da Cerchio intero
exl-id: fd471771-33e2-413a-b155-02ba6e32e10c
feature: Attribution, Fundamentals
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---

# Transizione a [!DNL Marketo Measure] da Cerchio intero {#transitioning-to-marketo-measure-from-full-circle}

Spostamento da Cerchio intero a [!DNL Marketo Measure]? Tu non sei da sola. Ecco le considerazioni principali da tenere a mente e le lezioni che abbiamo imparato da altri clienti che hanno effettuato il passaggio.

## Tracciamento basato su campagne e tracciamento multi-sorgente {#campaign-based-tracking-vs-multi-source-tracking}

Tutte le interazioni in [!UICONTROL Full Circle] vengono tracciati tramite l’iscrizione alla campagna CRM. Con [!DNL Marketo Measure], il percorso di acquisto viene compilato tramite una combinazione dei nostri record JavaScript, di iscrizione alla campagna CRM e di attività CRM. Fare lo spostamento mentale da &quot;tutte le interazioni devono essere tracciate in una campagna di gestione delle relazioni con i clienti affinché il nostro reporting di attribuzione funzioni&quot; a &quot;solo questo sottoinsieme di interazioni deve essere tracciato in una campagna di gestione delle relazioni con i clienti perché il nostro reporting di attribuzione funzioni&quot; può essere difficile.

In generale, ecco come [!DNL Marketo Measure] crea record dei punti di contatto per i principali tipi di interazioni:

* Compilazioni modulo nei siti: [!DNL Marketo Measure] JavaScript
* Visualizzazioni di pagina sui siti: creato da [!DNL Marketo Measure] JavaScript solo se questa visualizzazione di pagina ha guidato una milestone CRM designata (ad esempio Creazione di lead o opportunità)
* Interazioni offline come conferenze o fiere d’affari: iscrizione alla campagna CRM
* Interazioni digitali che si verificano ovunque su Internet che non è il tuo sito (come un webinar ospitato su un sito di terze parti che genera un caricamento di elenco): iscrizione alla campagna CRM
* Interazioni con il team vendite: record attività CRM

Se hai dimestichezza con la gestione delle campagne CRM e preferisci mantenere i processi esistenti sul posto, non c’è problema. Non fa male [!DNL Marketo Measure] per continuare a tenere traccia di tutte le interazioni nelle campagne CRM. Puoi progettare una logica che crei punti di contatto solo da un sottoinsieme desiderato di campagne per evitare la duplicazione dei punti di contatto.

## Visibilità e attribuzione {#visibility-vs-attribution}

Con la maggior parte delle configurazioni Full Circle, puoi vedere ogni singola interazione che una persona ha con le tue attività di marketing o di vendita. Visualizzazioni di pagina, visite di pagina ripetute, appartenenza a campagne duplicate e triplicate - Cerchio completo fa emergere tutte queste campagne. Se visualizzi una pagina 300 volte, Full Circle crea 300 campagne duplicate e ti assegna l’iscrizione a ciascuna di esse. [!DNL Marketo Measure] non lo fa, e questa è stata una decisione consapevole di progettazione da parte nostra.

[!DNL Marketo Measure] mira a fornirti una storia di attribuzione che metta in evidenza interazioni significative e distribuisca il peso tra i punti di contatto più incisivi in modo appropriato. Ad esempio, il [!DNL Marketo Measure] il framework non fa emergere le visualizzazioni di pagina (senza riempimenti modulo) come punti di contatto di routine. È improbabile che una visualizzazione di pagina autonoma abbia un impatto su come promuovere il percorso di acquisto, ma verrà creato un punto di contatto se si tratta dell’interazione più recente prima di una fase cardine del sistema CRM designata (ad esempio Creazione di lead o opportunità). Non vogliamo mostrarti tutto. Vogliamo mostrarvi le cose che contano, dal punto di vista dell&#39;attribuzione.

Utilizzare [!DNL Marketo Measure] rep per impostare le aspettative appropriate in merito ai dati che non saranno più disponibili per il team.

## Pre-[!DNL Marketo Measure] Dati {#pre-marketo-measure-data}

Il consiglio standard è quello di iniziare a generare rapporti e raccogliere dati dal giorno in cui hai implementato [!DNL Marketo Measure] JavaScript avanti, e raddoppia per gli ex clienti Full Circle. Pensa alle due sezioni precedenti: sei abituato a vedere una maggiore quantità di dati e sei abituato a tutti quei dati che provengono dall&#39;iscrizione alla campagna CRM. Se scegli di includere alcuni o tutti i dati di precedenti al [!DNL Marketo Measure] implementazione di, non effettuerai il confronto tra Apple e Apples nella data di implementazione di JavaScript.

Detto questo, sappiamo che molti clienti hanno bisogno di questi dati storici; soprattutto se si ha un ciclo di vendita più lungo (più di 90 giorni), si può desiderare di dare [!DNL Marketo Measure] visibilità in[!DNL Marketo Measure] dati. Discuti attentamente di questo argomento con il tuo [!DNL Marketo Measure] rep e ricorda sempre che sfasare la data di implementazione può portare alla comparsa di miglioramenti o riduzioni nelle prestazioni o nel coinvolgimento dei canali, nonché ad altre deduzioni potenzialmente errate.

## In sintesi {#in-summary}

Sei in buona compagnia e abbiamo aiutato molti altri clienti a gestire questi cambiamenti. Utilizzare [!DNL Marketo Measure] rep per comprendere gli impatti di cui sopra, così come qualsiasi altra preoccupazione che si possono avere.
