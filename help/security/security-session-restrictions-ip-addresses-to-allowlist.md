---
description: Inserire nell'elenco Consentiti Limitazioni delle sessioni di sicurezza - Indirizzi IP da
title: Inserire nell'elenco Consentiti Limitazioni delle sessioni di sicurezza - Indirizzi IP da
exl-id: aaf5190f-893c-4872-8d03-93f516e70a59
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---


# Inserire nell&#39;elenco Consentiti Limitazioni della sessione di sicurezza: indirizzi IP da {#security-session-restrictions-ip-addresses-to-allowlist}

Se sono presenti [Impostazioni di sicurezza sessione](https://help.salesforce.com/articleView?id=admin_sessions.htm&type=0){target="_blank"} che impediscono a indirizzi IP specifici di inviare/estrarre dati nell&#39;istanza [!DNL Salesforce], sarà necessario inserire nell&#39;elenco Consentiti i seguenti intervalli IP per consentire a [!DNL Marketo Measure] di inviare dati a [!DNL Salesforce]:

* 52.162.84.192 - 52.162.84.207
* 23.100.229.112 - 23.100.229.127
* 20.186.163.0 - 20.186.163.15

Per aggiungere [!DNL Marketo Measure] IP agli intervalli IP attendibili in Salesforce, fare clic su **[!UICONTROL Setup]** > **[!UICONTROL Administration Setup]** > **[!UICONTROL Security Controls]** > **[!UICONTROL Network Access]** > **[!UICONTROL New]**.

![Pagina Accesso alla rete di Salesforce per l&#39;aggiunta di intervalli IP attendibili](assets/1.png)
