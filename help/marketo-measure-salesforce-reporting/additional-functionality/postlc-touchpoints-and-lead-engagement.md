---
description: Scopri come creare punti di contatto PostLC aggiornati e limitati per lead e contatti
title: Punti di contatto PostLC e coinvolgimento lead
exl-id: 3ee5c571-195e-46c7-b150-fedcbc3614cb
feature: Touchpoints
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Punti di contatto PostLC e coinvolgimento lead {#postlc-touchpoints-and-lead-engagement}

Sono disponibili [!DNL Marketo Measure] punti di contatto Post-Lead Creation (PostLC) per i clienti che utilizzano modelli di attribuzione multi-touch (W-Shape e versioni successive). Quando un lead o un contatto ritorna sul sito web e continua a compilare moduli, questi invii di moduli si registrano come punti di contatto PostLC. Questi punti di contatto consentono di vedere quali contenuti stanno guidando i lead a continuare a interagire con il sito, molto tempo dopo la loro prima conversione. I punti di contatto PostLC condividono il credito di attribuzione con tutti i punti di contatto intermediari all’interno di un’opportunità; il 10% di credito di attribuzione viene assegnato ai punti di contatto intermediari e viene distribuito equamente tra tutti i contatti.

![](assets/additional-functionality-1.png)

È possibile regolare il numero di punti di contatto PostLC visualizzati in [!DNL SFDC]. In genere si consiglia di spingere fino a cinque punti di contatto PostLC; ogni punto di contatto occupa 1 KB in [!DNL SFDC].

>[!NOTE]
>
>Le istruzioni su come regolare le impostazioni dei punti di contatto PostLC sono disponibili alla fine di questo articolo.

I punti di contatto PostLC sono dinamici. Poiché un lead o un contatto continua a inviare moduli PostLC, [!DNL Marketo Measure] aggiorna i punti di contatto PostLC nel tuo CRM per mostrarti i loro invii di moduli più recenti. In particolare, se hai impostato un limite di 5 punti di contatto PostLC, [!DNL Marketo Measure] invia sempre i cinque _punti di contatto più recenti_ al CRM.  In questo esempio, questo account ha impostato il limite PostLC su quattro punti di contatto. Questo lead ha già raggiunto il numero massimo di punti di contatto PostLC che può avere nel CRM. L’ultimo contatto PostLC è avvenuto il 2/6/2018. Se questa persona compila un altro modulo il giorno successivo, [!DNL Marketo Measure] rimuoverà il primo punto di contatto PostLC dal 11/9/2017 per aggiungere l&#39;ultimo punto di contatto dal 2/7/2018.

![](assets/additional-functionality-2.png)

>[!NOTE]
>
>[!DNL Marketo Measure] aggiorna solo i punti di contatto PostLC sul lead o sul contatto e non aggiorna i punti di contatto di attribuzione PostLC su un&#39;opportunità. Tutti i punti di contatto PostLC rilevanti su un contatto sono inclusi nell’opportunità.

## Come modificare le impostazioni dei punti di contatto PostLC {#how-to-change-postlc-touchpoint-settings}

Per regolare le impostazioni dei punti di contatto PostLC per i lead o i contatti, attenersi alle istruzioni riportate di seguito.

**Lead**

1. Accedi al tuo account [!DNL Marketo Measure] all&#39;indirizzo [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} e passa a [!UICONTROL Settings].

1. In CRM, selezionare **[!UICONTROL Leads]**.

1. Immettere il numero di punti di contatto postLC da inviare ai lead e fare clic su **[!UICONTROL Save]**.

   ![](assets/additional-functionality-3.png)

**Contatti**

1. Accedi al tuo account [!DNL Marketo Measure] all&#39;indirizzo [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} e passa a [!UICONTROL Settings].

1. In CRM, selezionare **[!UICONTROL Contacts]**.

1. Immettere il numero di punti di contatto postLC da inviare ai contatti e fare clic su **[!UICONTROL Save]**.

   ![](assets/additional-functionality-4.png)
