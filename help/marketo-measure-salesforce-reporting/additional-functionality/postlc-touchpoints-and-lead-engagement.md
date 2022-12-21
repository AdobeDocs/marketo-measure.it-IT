---
unique-page-id: 18874562
description: Punti di contatto post-LC e lead Engagement - Misura Marketo - Documentazione del prodotto
title: Punti di contatto post-LC e coinvolgimento lead
exl-id: 3ee5c571-195e-46c7-b150-fedcbc3614cb
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Punti di contatto post-LC e coinvolgimento lead {#postlc-touchpoints-and-lead-engagement}

[!DNL Marketo Measure] I punti di contatto per la creazione di lead (PostLC) sono disponibili per i clienti che utilizzano modelli di attribuzione multi-touch (forma W e versioni successive). Quando un lead o un contatto ritorna sul tuo sito web e continua a compilare moduli, questi invii verranno registrati come punti di contatto PostLC. Questi punti di contatto consentono di vedere quali contenuti veicolano i Lead per continuare a interagire con il sito, molto tempo dopo la loro prima conversione. I punti di contatto PostLC condividono il credito di attribuzione con tutti i punti di contatto intermedi all’interno di un’opportunità; Il credito di attribuzione 10% è assegnato ai punti di contatto intermedi e viene distribuito equamente tra tutti i contatti.

![](assets/1.png)

Puoi regolare il numero di punti di contatto PostLC che verranno visualizzati in [!DNL SFDC]. In genere consigliamo di aumentare fino a cinque punti di contatto PostLC; ogni punto di contatto richiede 1 KB in [!DNL SFDC].

>[!NOTE]
>
>Le istruzioni su come regolare le impostazioni dei punti di contatto PostLC si trovano alla fine di questo articolo.

I punti di contatto PostLC sono dinamici. Come lead o contatti continua a inviare moduli PostLC, [!DNL Marketo Measure] aggiornerà i punti di contatto PostLC nel tuo CRM per mostrarti i loro ultimi invii di moduli. In particolare, se hai impostato un limite di 5 punti di contatto PostLC, [!DNL Marketo Measure] premere sempre il 5 _più recente_ punti di contatto per il CRM.  In questo esempio, questo account ha impostato il limite PostLC a quattro punti di contatto. Questo lead ha già raggiunto il numero massimo di punti di contatto PostLC che può avere nel CRM. L&#39;ultimo tocco PostLC è stato il 2/6/2018. Se questa persona dovesse compilare un altro modulo il giorno successivo, [!DNL Marketo Measure] rimuove il primo punto di contatto PostLC dall’11/9/2017 per aggiungere l’ultimo punto di contatto dal 7/2/2018.

![](assets/2.png)

>[!NOTE]
>
>[!DNL Marketo Measure] aggiornerà solo i punti di contatto PostLC sul lead o sul contatto e non aggiornerà i punti di contatto di attribuzione PostLC su un’opportunità. Tutti i punti di contatto PostLC pertinenti su un contatto saranno inclusi nell&#39;opportunità.

## Come cambiare le impostazioni dei punti di contatto PostLC {#how-to-change-postlc-touchpoint-settings}

Per regolare le impostazioni dei punti di contatto PostLC per i lead o i contatti, seguire le istruzioni riportate di seguito.

**Lead**

1. Accedi al tuo [!DNL Marketo Measure] conto a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target=&quot;_blank&quot;} e vai a [!UICONTROL Settings].

1. In CRM, seleziona **[!UICONTROL Leads]**.

1. Inserisci il numero di punti di contatto postLC che desideri inviare ai tuoi lead e fai clic su **[!UICONTROL Save]**.

   ![](assets/3.png)

**Contatti**

1. Accedi al tuo [!DNL Marketo Measure] conto a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target=&quot;_blank&quot;} e vai a [!UICONTROL Settings].

1. In CRM, seleziona **[!UICONTROL Contacts]**.

1. Inserisci il numero di punti di contatto postLC che desideri inviare ai tuoi contatti e fai clic su **[!UICONTROL Save]**.

   ![](assets/4.png)
