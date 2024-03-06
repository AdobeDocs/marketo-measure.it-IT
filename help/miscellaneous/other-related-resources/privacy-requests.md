---
description: Richieste di accesso a dati personali - [!DNL Marketo Measure]
title: Richieste di accesso a dati personali
exl-id: 883e475f-9868-412a-b505-230556f38484
feature: APIs, Tracking
source-git-commit: 4787f765348da71bc149c997470ce678ba498772
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Richieste di accesso a dati personali {#privacy-requests}

Questo documento fornisce una panoramica sulla gestione delle singole richieste di privacy dei dati che puoi inviare a [!DNL Marketo Measure] tramite [!DNL Privacy Service] Interfaccia e **[!DNL Privacy Service]API**.

È possibile inviare singole richieste per accedere ed eliminare i dati dei consumatori da [!DNL Marketo Measure] in due modi:

* Attraverso il [[!DNL Privacy Service] UI](https://experienceleague.adobe.com/docs/experience-platform/privacy/ui/overview.html){target="_blank"}.
* Attraverso il **[!DNL Privacy Service]API**. Consulta la documentazione [qui](https://experienceleague.adobe.com/docs/experience-platform/privacy/api/overview.html){target="_blank"} and the API reference [here](https://developer.adobe.com/experience-platform-apis/references/privacy-service/){target="_blank"}.

Il [Privacy Service](https://experienceleague.adobe.com/docs/experience-platform/privacy/home.html){target="_blank"} supporta due tipi di richieste: accesso ai dati ed eliminazione dei dati.

Vediamo come creare richieste di accesso ed eliminazione.

## Configurazione necessaria per inviare richieste per Marketo Measure {#required-setup-to-send-requests-for-marketo-measure}

Per effettuare richieste di accesso ed eliminazione dei dati per [!DNL Marketo Measure], è necessario:

1. Identificare quanto segue:

   a. ID organizzazione IMS

   b. Indirizzo e-mail della persona su cui desideri agire

   Un ID organizzazione IMS è una stringa alfanumerica composta da 24 caratteri a cui segue @AdobeOrg. Se il team marketing o l’amministratore di Adobe interno non conosce l’ID organizzazione IMS dell’organizzazione, contatta l’Assistenza clienti Adobe all’indirizzo gdprsupport@adobe.com. Per inviare richieste all’API per la privacy è necessario l’ID organizzazione IMS.

1. In entrata [!DNL Privacy Service], puoi inviare le richieste di accesso ed eliminazione a [!DNL Marketo Measure], e controlla lo stato delle richieste esistenti.

## Valori campo obbligatori in [!DNL Marketo Measure] Richieste JSON {#required-field-values-in-marketo-measure-json-requests}

&quot;companyContexts&quot;:

* &quot;namespace&quot;: **imsOrgID**
* &quot;value&quot;: `<Your IMS Org ID Value>`

&quot;users&quot; (utenti):

* &quot;action&quot;: [!UICONTROL access] o eliminare
* &quot;userIDs&quot;:
   * &quot;namespace&quot;: email
   * &quot;type&quot;: standard
   * &quot;value&quot;: `<Data Subject's Email Address>`

&quot;include&quot;:

* **marketoMeasure** (prodotto di Adobe applicabile alla richiesta)

&quot;regolamento&quot;:

* **gdpr**, **ccpa**, **pdpa**, **lgpd_bra**, o **nzpa_nzl** (regolamento sulla privacy applicabile alla richiesta)

## Esempio 1: richiesta di eliminazione RGPD {#gdpr-delete-request}

Richiesta JSON

```text
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

```text
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

```text
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

```text
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
