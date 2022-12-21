---
unique-page-id: 18874564
description: Definizione di [!DNL Marketo Measure] Sessioni Web - [!DNL Marketo Measure] - Documentazione del prodotto
title: Definizione di [!DNL Marketo Measure] Sessioni web
exl-id: ddf4f19d-2024-413a-b0ae-4efd468c24de
source-git-commit: ae5b77744d523606ce6cfcf48d7e8d5049d5ccb7
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Definizione di [!DNL Marketo Measure] Sessioni web {#definition-of-marketo-measure-web-sessions}

Scopri come [!DNL Marketo Measure] definisce le sessioni web.

A **sessione web** si riferisce alle interazioni di una persona con il tuo sito web per un certo periodo di tempo. La sessione inizia quando un utente arriva sul tuo sito web.

Ad esempio, Haley visita adobe.com. La sua visita al sito inizia una sessione. Quando Haley lascia il sito, chiudendo la scheda/il browser web o andando via dal sito, la sessione termina.

Un utente non può aprire più sessioni contemporaneamente. Se Haley apre [!DNL adobe.com] in 10 schede separate, è stata creata una sola sessione in relazione alla sua visita al sito web.

## Come funziona [!DNL Marketo Measure] definire una nuova sessione? {#how-does-marketo-measure-define-a-new-session}

Sono disponibili alcuni elementi che determinano quando termina una sessione e quando inizia una nuova sessione. Le due principali vie [!DNL Marketo Measure] le sessioni possono terminare:

* **Scadenza basata sul tempo**
* **Scadenza basata sul canale**

## Scadenza basata sul tempo {#time-based-expiration}

**Quanto dura una sessione?**

[!DNL Marketo Measure] le sessioni termineranno dopo 30 minuti di inattività sul sito web. Ad esempio:

Quando Haley visita adobe.com, inizia una sessione. Esplora il sito web per qualche minuto e poi si allontana dal suo computer, ma lascia il sito web aperto. Dopo 30 minuti di inattività la sessione terminerà.

Attualmente, [!DNL Marketo Measure] considera solo la navigazione nelle pagine e gli invii dei moduli come attività. Lo scorrimento all’interno della pagina web o il passaggio del mouse su un elemento della pagina non è considerato attività. Quindi se Haley visita adobe.com per leggere un post sul blog e le ci vuole un&#39;ora per leggere, la sua sessione web terminerà dopo 30 minuti anche se sta scorrendo il contenuto della pagina.

## Scadenza basata sul canale {#channel-based-expiration}

[!DNL Marketo Measure] inizierà una nuova sessione ogni volta che un utente accede al tuo sito web da un canale di marketing digitale diverso o da un sito web esterno. Ciò include:

* Un sito web di riferimento
* Canali sociali ([!DNL Facebook], [!DNL LinkedIn], ecc.)
* Canali di ricerca a pagamento o biologici ([!DNL Google/Bing])

**Siti web di riferimento e canali social**

Ogni volta che un visitatore accede al tuo sito web da un sito web di riferimento o da un canale social, inizierà una nuova sessione.

Di&#39; che Haley è su LinkedIn, clicca su un [!DNL Marketo Measure] pubblica e viene reindirizzato al sito web Adobe. Quindi, mentre scorri attraverso [!DNL Facebook]Haley vede un altro [!DNL Marketo Measure] post. Quando fa clic su questo post e viene reindirizzato al sito di Adobe, si verifica la prima sessione Web correlata a [!DNL LinkedIn] e una nuova sessione relativa [!DNL Facebook] inizia.

**Canali di ricerca a pagamento o biologici**

Le nuove sessioni inizieranno ogni volta che un utente arriva al tuo sito attraverso canali di ricerca a pagamento o biologici. Se Haley arriva al sito web di Adobe tramite ricerca organica, e poi visita immediatamente il tuo sito web attraverso un annuncio a pagamento su Google, verranno create due sessioni separate.

**Traffico diretto web**

Se un visitatore accede al sito web digitando l’URL del sito web nella barra degli indirizzi, non sempre viene avviata una nuova sessione.

Se la prima sessione web di Haley inizia come risultato di una visita da un sito di riferimento, un canale social o un canale di ricerca a pagamento/organico e poi visita il sito tramite web direct, questo non farà iniziare una nuova sessione.

_Tuttavia_, se la prima sessione web di Haley ha avuto origine da Web Direct, e poi visita il sito web tramite _un sito esterno/di riferimento_, la prima sessione terminerà e verrà aperta una nuova sessione relativa al sito esterno/di riferimento.

## Google Analytics Sessions {#google-analytics-sessions}

Ci sono alcune somiglianze con come [!DNL Marketo Measure] e Google Analytics definisce le sessioni. Per ulteriori informazioni su come Google Analytics definisce le sessioni, visita: [https://support.google.com/analytics/answer/2731565?hl=en](http://support.google.com/analytics/answer/2731565?hl=en){target=&quot;_blank&quot;}
