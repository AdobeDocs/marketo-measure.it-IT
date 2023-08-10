---
unique-page-id: 18874706
description: Limitazioni delle sessioni di sicurezza - Indirizzi IP da utilizzare per il Inserisco nell'elenco Consentiti di - Marketo Measure - Documentazione del prodotto
title: Limitazioni delle sessioni di sicurezza - Indirizzi IP da Inserire nell'elenco Consentiti per l’accesso a un’istanza di accesso a un sito Web
exl-id: aaf5190f-893c-4872-8d03-93f516e70a59
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '79'
ht-degree: 3%

---

# Limitazioni della sessione di sicurezza: indirizzi IP da Inserire nell&#39;elenco Consentiti {#security-session-restrictions-ip-addresses-to-allowlist}

Se sono presenti [Impostazioni di sicurezza della sessione](https://help.salesforce.com/articleView?id=admin_sessions.htm&amp;type=0){target="_blank"} impedisce a indirizzi IP specifici di inviare/richiamare dati al tuo [!DNL Salesforce] per consentirla, sarà necessario inserire nell&#39;elenco Consentiti i seguenti intervalli IP [!DNL Marketo Measure] per inviare dati a [!DNL Salesforce]:

* 52.162.84.192 - 52.162.84.207
* 23.100.229.112 - 23.100.229.127
* 20.186.163.0 - 20.186.163.15

Da aggiungere [!DNL Marketo Measure] IP degli intervalli IP attendibili in Salesforce, fai clic su **[!UICONTROL Setup]** > **[!UICONTROL Administration Setup]** > **[!UICONTROL Security Controls]** > **[!UICONTROL Network Access]** > **[!UICONTROL New]**.

![](assets/1.png)
