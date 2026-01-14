---
description: Indicazioni sulle richieste di accesso a dati personali per gli utenti di Marketo Measure
title: Richieste sulla privacy
exl-id: 883e475f-9868-412a-b505-230556f38484
feature: APIs, Tracking
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 24%

---


# Richieste sulla privacy {#privacy-requests}

In questo documento viene fornita una panoramica sulla gestione delle singole richieste di privacy dei dati che è possibile inviare a [!DNL Marketo Measure] tramite l&#39;interfaccia utente [!DNL Privacy Service] e l&#39;API **[!DNL Privacy Service]**.

È possibile inviare singole richieste per accedere ed eliminare i dati dei consumatori da [!DNL Marketo Measure] in due modi:

* Tramite l&#39;[[!DNL Privacy Service] interfaccia utente](https://experienceleague.adobe.com/docs/experience-platform/privacy/ui/overview.html?lang=it){target="_blank"}.
* Tramite l&#39;API **[!DNL Privacy Service]**. Consulta la documentazione [qui](https://experienceleague.adobe.com/docs/experience-platform/privacy/api/overview.html?lang=it){target="_blank"} e il riferimento API [qui](https://developer.adobe.com/experience-platform-apis/references/privacy-service/){target="_blank"}.

[Privacy Service](https://experienceleague.adobe.com/docs/experience-platform/privacy/home.html?lang=it){target="_blank"} supporta due tipi di richieste: accesso ai dati ed eliminazione dei dati.

Vediamo come creare richieste di accesso ed eliminazione.

## Configurazione necessaria per inviare richieste per Marketo Measure {#required-setup-to-send-requests-for-marketo-measure}

Per richiedere l&#39;accesso e l&#39;eliminazione dei dati per [!DNL Marketo Measure], è necessario:

1. Identificare quanto segue:

   a. ID organizzazione IMS

   b. Indirizzo e-mail della persona su cui desideri agire

   Un ID organizzazione IMS è una stringa alfanumerica composta da 24 caratteri, con l&#39;aggiunta di @AdobeOrg. Se il team marketing o l&#39;amministratore di sistema Adobe interno non conosce l&#39;ID organizzazione IMS dell&#39;azienda, contatta l&#39;Assistenza clienti Adobe all&#39;indirizzo gdprsupport@adobe.com. Per inviare richieste all’API per la privacy è necessario l’ID organizzazione IMS.

1. In [!DNL Privacy Service] è possibile inviare le richieste di accesso ed eliminazione a [!DNL Marketo Measure] e controllare lo stato delle richieste esistenti.

## Valori campo obbligatori nelle richieste JSON di [!DNL Marketo Measure] {#required-field-values-in-marketo-measure-json-requests}

&quot;companyContexts&quot;:

* &quot;namespace&quot;: **imsOrgID**
* &quot;value&quot;: `<Your IMS Org ID Value>`

&quot;users&quot; (utenti):

* &quot;action&quot;: [!UICONTROL access] o elimina
* &quot;userIDs&quot;:
   * &quot;namespace&quot;: email
   * &quot;type&quot;: standard
   * &quot;value&quot;: `<Data Subject's Email Address>`

&quot;include&quot;:

* **marketoMeasure** (prodotto Adobe applicabile alla richiesta)

&quot;regolamento&quot;:

* **gdpr**, **ccpa**, **pdpa**, **lgpd_bra** o **nzpa_nzl** (normativa sulla privacy applicabile alla richiesta)

## Esempio 1: richiesta di eliminazione RGPD {#gdpr-delete-request}

Richiesta JSON

```json
{
  "companyContexts": [
    {
      "namespace": "imsOrgID",
      "value": "1231659F56A68A8B7F000101@AdobeOrg"
    }
  ],
  "users": [
    {
      "action": [
        "delete"
      ],
      "userIDs": [
        {
          "namespace": "email",
          "type": "standard",
          "value": "john.doe@adobe.com"
        }
      ]
    }
  ],
  "include": [
    "marketoMeasure"
  ],
  "regulation": "gdpr",
}
```

Risposta JSON

```json
{
  "requestId": "16331241037112570RX-245",
  "totalRecords": 1,
  "jobs": [
    {
      "jobId": "997b01e3-9568-402c-904b-b4e60a437875",
      "customer": {
        "user": {
          "action": [
            "delete"
          ],
          "userIDs": [
            {
              "namespace": "email",
              "value": "john.doe@adobe.com",
              "type": "standard",
              "namespaceId": 6,
              "isDeletedClientSide": false
            }
          ]
        }
      }
    }
  ]
}
```

## Esempio 2: richiesta di accesso CCPA {#ccpa-access-request}

Richiesta JSON

```json
{
  "companyContexts": [
    {
      "namespace": "imsOrgID",
      "value": "1231659F56A68A8B7F000101@AdobeOrg"
    }
  ],
  "users": [
    {
      "action": [
        "access"
      ],
      "userIDs": [
        {
          "namespace": "email",
          "type": "standard",
          "value": "john.doe@adobe.com"
        }
      ]
    }
  ],
  "include": [
    "marketoMeasure"
  ],
  "regulation": "ccpa",
}
```

Risposta JSON

```json
{
  "requestId": "16329573462631890RX-207",
  "totalRecords": 1,
  "jobs": [
    {
      "jobId": "3115e42d-011b-47ab-a2b0-ed4356af4d3e",
      "customer": {
        "user": {
          "action": [
            "access"
          ],
          "userIDs": [
            {
              "namespace": "email",
              "value": "john.doe@adobe.com",
              "type": "standard",
              "namespaceId": 6,
              "isDeletedClientSide": false
            }
          ]
        }
      }
    }
  ]
}
```
