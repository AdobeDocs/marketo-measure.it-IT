---
unique-page-id: 18874706
description: Restrizioni alle sessioni di sicurezza - Indirizzi IP Inserire nell'elenco Consentiti - Misura Marketo - Documentazione del prodotto
title: Restrizioni alle sessioni di sicurezza - Indirizzi IP da Inserire nell'elenco Consentiti
exl-id: aaf5190f-893c-4872-8d03-93f516e70a59
source-git-commit: b9d9e3110e87be0d6311c17b0ef76dfad8735a00
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 3%

---

# Restrizioni delle sessioni di sicurezza: Indirizzi IP a Inserire nell&#39;elenco Consentiti {#security-session-restrictions-ip-addresses-to-allowlist}

Se ci sono [Impostazioni di sicurezza della sessione](https://help.salesforce.com/articleView?id=admin_sessions.htm&amp;type=0){target=&quot;_blank&quot;} non consente a specifici indirizzi IP di inviare/richiamare dati al proprio interno [!DNL Salesforce] Ad esempio, è necessario inserire nell&#39;elenco Consentiti i seguenti intervalli IP per consentire [!DNL Marketo Measure] per inviare dati a [!DNL Salesforce]:

* 52.162.84.192 - 52.162.84.207
* 23.100.229.112 - 23.100.229.127
* 20.186.163.0 - 20.186.163.15

Per aggiungere [!DNL Marketo Measure] IP degli intervalli IP attendibili in Salesforce, fare clic su **[!UICONTROL Setup]** > **[!UICONTROL Administration Setup]** > **[!UICONTROL Security Controls]** > **[!UICONTROL Network Access]** > **[!UICONTROL New]**.

![](assets/1.png)
