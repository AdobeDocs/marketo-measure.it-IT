---
unique-page-id: 18874706
description: Limitazioni delle sessioni di sicurezza - Indirizzi IP da utilizzare per il Inserisco nell'elenco Consentiti di - Marketo Measure - Documentazione del prodotto
title: Limitazioni delle sessioni di sicurezza - Indirizzi IP da Inserire nell'elenco Consentiti per l’accesso a un’istanza di accesso a un sito Web
exl-id: aaf5190f-893c-4872-8d03-93f516e70a59
feature: Tracking
TQID: 'https://experienceleague.adobe.com/Ka7ff5qarBVEm4JdSGCbaUM3Mrug0r3ZOPSKPrnc3Zo'
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: dcbeff6e-0253-5a4b-9ac2-1b67cc4a6286
    internal-label: Tracking
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 7%
---
# Limitazioni della sessione di sicurezza: indirizzi IP da Inserire nell&#39;elenco Consentiti {#security-session-restrictions-ip-addresses-to-allowlist}

Se sono presenti [Impostazioni di sicurezza sessione](https://help.salesforce.com/articleView?id=admin_sessions.htm&type=0){target="_blank"} che impediscono a indirizzi IP specifici di inviare/estrarre dati nell&#39;istanza [!DNL Salesforce], sarà necessario inserire nell&#39;elenco Consentiti i seguenti intervalli IP per consentire a [!DNL Marketo Measure] di inviare dati a [!DNL Salesforce]:

* 52.162.84.192 - 52.162.84.207
* 23.100.229.112 - 23.100.229.127
* 20.186.163.0 - 20.186.163.15

Per aggiungere [!DNL Marketo Measure] IP agli intervalli IP attendibili in Salesforce, fare clic su **[!UICONTROL Setup]** > **[!UICONTROL Administration Setup]** > **[!UICONTROL Security Controls]** > **[!UICONTROL Network Access]** > **[!UICONTROL New]**.

![](assets/1.png)
