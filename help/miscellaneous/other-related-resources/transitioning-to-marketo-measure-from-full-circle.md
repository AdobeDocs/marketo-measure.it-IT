---
unique-page-id: 18874535
description: Transizione a  [!DNL Marketo Measure]  da Cerchio completo - [!DNL Marketo Measure]
title: Transizione a  [!DNL Marketo Measure]  da Cerchio completo
exl-id: fd471771-33e2-413a-b155-02ba6e32e10c
feature: Attribution, Fundamentals
source-git-commit: 4787f765348da71bc149c997470ce678ba498772
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Transizione a [!DNL Marketo Measure] da Cerchio completo {#transitioning-to-marketo-measure-from-full-circle}

Spostarsi da Cerchio completo a [!DNL Marketo Measure]? Tu non sei da sola. Ecco le considerazioni principali da tenere a mente e le lezioni che abbiamo imparato da altri clienti che hanno effettuato il passaggio.

## Tracciamento basato su campagne e tracciamento con più Source {#campaign-based-tracking-vs-multi-source-tracking}

Tutte le interazioni in [!UICONTROL Full Circle] vengono tracciate tramite l&#39;iscrizione alla campagna CRM. Con [!DNL Marketo Measure], il percorso di acquisto viene compilato tramite una combinazione dei record di JavaScript, iscrizione alla campagna CRM e attività CRM. Fare lo spostamento mentale da &quot;tutte le interazioni devono essere tracciate in una campagna di gestione delle relazioni con i clienti affinché il nostro reporting di attribuzione funzioni&quot; a &quot;solo questo sottoinsieme di interazioni deve essere tracciato in una campagna di gestione delle relazioni con i clienti perché il nostro reporting di attribuzione funzioni&quot; può essere complicato.

In generale, [!DNL Marketo Measure] crea record dei punti di contatto per i principali tipi di interazioni:

* Compilazioni modulo nei siti: [!DNL Marketo Measure] JavaScript
* Visualizzazioni di pagina sui siti: creato da [!DNL Marketo Measure] JavaScript solo se questa visualizzazione di pagina ha determinato una fase cardine del sistema di gestione delle relazioni con i clienti designata (ad esempio Creazione di lead o opportunità)
* Interazioni offline come conferenze o fiere d’affari: iscrizione alla campagna CRM
* Interazioni digitali che si verificano ovunque su Internet che non è il tuo sito (come un webinar ospitato su un sito di terze parti che genera un caricamento di elenco): iscrizione alla campagna CRM
* Interazioni con il team vendite: record attività CRM

Se hai familiarità con la gestione delle campagne CRM e preferisci mantenere i processi esistenti sul posto, non c’è problema. Non fa male a [!DNL Marketo Measure] continuare a monitorare tutte le interazioni nelle campagne CRM. Puoi progettare una logica che crei punti di contatto solo da un sottoinsieme desiderato di campagne per evitare la duplicazione dei punti di contatto.

## Visibilità e attribuzione {#visibility-vs-attribution}

Con la maggior parte delle configurazioni Full Circle, puoi vedere ogni interazione di una persona con le tue attività di marketing o di vendita. Visualizzazioni di pagina, visite di pagina ripetute, appartenenza a campagne triplicate: il cerchio completo fa emergere tutte queste campagne. Se visualizzi una pagina 300 volte, Full Circle crea 300 campagne duplicate e ti assegna l’iscrizione a ciascuna di esse. [!DNL Marketo Measure] no, e questa è stata una decisione consapevole da parte nostra.

[!DNL Marketo Measure] ha lo scopo di fornirti una storia di attribuzione che evidenzia interazioni significative e distribuisce il peso tra i punti di contatto più rilevanti in modo appropriato. Ad esempio, il framework [!DNL Marketo Measure] non presenterà le visualizzazioni di pagina (senza riempimenti di moduli) come punti di contatto di routine. È improbabile che una visualizzazione di pagina autonoma abbia un impatto su come portare avanti un percorso di acquisto, ma viene creato un punto di contatto se si tratta dell’interazione più recente prima di una fase cardine del sistema CRM designata (ad esempio Creazione di lead o opportunità). Non vogliamo mostrarti tutto. Vogliamo mostrarvi le cose che contano, dal punto di vista dell&#39;attribuzione.

Collabora con il tuo rappresentante [!DNL Marketo Measure] per impostare le aspettative appropriate in merito ai dati che non saranno più disponibili per il tuo team.

## Dati precedenti a [!DNL Marketo Measure] {#pre-marketo-measure-data}

Il consiglio standard è quello di avviare la generazione di rapporti e la raccolta dati dal giorno in cui è stato implementato il JavaScript [!DNL Marketo Measure] in avanti, e questo raddoppia per gli ex clienti Full Circle. Pensa alle due sezioni precedenti: sei abituato a vedere una quantità maggiore di dati e sei abituato a tutti quei dati provenienti dall’iscrizione alla campagna CRM. Se scegli di includere alcuni o tutti i dati precedenti all&#39;implementazione di [!DNL Marketo Measure], non effettuerai il confronto tra Apple e Apples per tutta la data di implementazione di JavaScript.

Detto questo, sappiamo che molti clienti hanno bisogno di questi dati storici; soprattutto se hai un ciclo di vendita più lungo (più di 90 giorni), potresti voler dare a [!DNL Marketo Measure] la visibilità sui dati precedenti a[!DNL Marketo Measure]. Discuti attentamente di questo aspetto con il tuo rappresentante [!DNL Marketo Measure] e tieni sempre presente che uno sfasamento tra le date di implementazione può portare alla comparsa di miglioramenti o riduzioni nelle prestazioni o nel coinvolgimento del canale e ad altre deduzioni potenzialmente errate.

## In sintesi {#in-summary}

Sei in buona compagnia e abbiamo aiutato molti altri clienti a gestire questi cambiamenti. Collabora con il tuo rappresentante [!DNL Marketo Measure] per capire gli effetti di cui sopra e qualsiasi altro problema che potresti avere.
