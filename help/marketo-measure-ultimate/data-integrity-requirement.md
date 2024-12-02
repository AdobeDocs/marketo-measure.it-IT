---
description: Requisiti di integrità dei dati di [!DNL Marketo Measure] Ultimate - [!DNL Marketo Measure]
title: Requisiti di integrità dei dati di [!DNL Marketo Measure] Ultimate
feature: Integration, Tracking, Attribution
exl-id: 8ad001d0-e9fe-46f5-b808-d6203a55a229
source-git-commit: 54695bd795fe9bdb58d97b6b0762b9e9fe8f17cf
workflow-type: tm+mt
source-wordcount: '1611'
ht-degree: 16%

---

# Requisiti di integrità dei dati di [!DNL Marketo Measure] Ultimate {#marketo-measure-ultimate-data-integrity-requirement}

[!DNL Marketo Measure] convalida i set di dati AEP in arrivo per garantire che i dati siano sufficienti e coerenti per l&#39;attribuzione. Il mancato rispetto del requisito di integrità dei dati determina il rifiuto del set di dati da parte del sistema [!DNL Marketo Measure]. Questo articolo descrive i requisiti di integrità dei dati, fornisce esempi di query per l’ispezione dei dati e consiglia una soluzione per i campi obbligatori con valore nullo.

## Oggetto entità {#entity-object}

<table style="table-layout:auto">
  <tr>
    <th>Classe XDM</th>
    <th>Gruppo di campi XDM</th>
    <th>Percorso XDM</th>
    <th>Tipo XDM</th>
    <th>Campo Source dati</th>
    <th>Obbligatorio</th>
    <th>Note</th>
  </tr>
  <tbody>
    <tr>
      <td colspan="7"><strong>Account</strong> (account per Salesforce, società e/o account denominato per Marketo)</td>
    </tr>
    <tr>
      <td rowspan="6">Account aziendale XDM</td>
      <td></td>
      <td>accountKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Ad esempio: 123@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceID</td>
      <td>stringa</td>
      <td>ID</td>
      <td>Sì</td>
      <td>Esempio: - 123</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceInstanceID</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>data-ora</td>
      <td>CreatedDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>data-ora</td>
      <td>ModifiedDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>Dettagli dell’account aziendale XDM</td>
      <td>accountName</td>
      <td>stringa</td>
      <td>Nome</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Campagna</strong> (Campagna per Salesforce, Programma per Marketo)</td>
    </tr>
    <tr>
      <td rowspan="8">Campagna aziendale XDM</td>
      <td></td>
      <td>campaignKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceID</td>
      <td>stringa</td>
      <td>ID</td>
      <td>Sì</td>
      <td>Ad esempio: - 55555</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceInstanceID</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>data-ora</td>
      <td>CreatedDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>data-ora</td>
      <td>ModifiedDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>campaignName</td>
      <td>stringa</td>
      <td>Nome</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>campaignType</td>
      <td>stringa</td>
      <td>CampaignType</td>
      <td>No</td>
      <td>Per la mappatura dei canali</td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="5">Dettagli della campagna aziendale XDM</td>
      <td>channelName</td>
      <td>stringa</td>
      <td>NomeCanale</td>
      <td>No</td>
      <td>Per la mappatura dei canali</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignStartDate</td>
      <td>data-ora</td>
      <td>DataInizio</td>
      <td>No</td>
      <td>Per costo campagna</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignEndDate</td>
      <td>data-ora</td>
      <td>EndDate</td>
      <td>No</td>
      <td>Per costo campagna</td>
    </tr>
    <tr>
      <td></td>
      <td>actualCost.amount</td>
      <td>numero</td>
      <td>Costo</td>
      <td>No</td>
      <td>Per costo campagna</td>
    </tr>
    <tr>
      <td></td>
      <td>actualCost.currencyCode</td>
      <td>
        <p>stringa</p>
        <p>^[A-Z]{3}$</p>
      </td>
      <td>CurrencyIsoCode</td>
      <td>No</td>
      <td>Per costo campagna</td>
    </tr>
    <tr>
      <td colspan="7"><strong>Membro della campagna</strong> (membro della campagna per Salesforce, iscrizioni al programma per Marketo)</td>
    </tr>
    <tr>
      <td rowspan="14">Membri della campagna aziendale XDM</td>
      <td></td>
      <td>campaignMemberKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 987654321@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignMemberKey.sourceID</td>
      <td>stringa</td>
      <td>ID</td>
      <td>Sì</td>
      <td>Ad esempio: - 987654321</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignMemberKey.sourceInstanceID</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignMemberKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>data-ora</td>
      <td>CreatedDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>data-ora</td>
      <td>ModifiedDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceID</td>
      <td>stringa</td>
      <td>ID lead o ID contatto</td>
      <td>Sì</td>
      <td>
        <p>Ad esempio: - 333, a seconda della tabella dell’origine dati, può essere un ID lead o un ID contatto.</p>
        <p>Chiave esterna per lead o contatto</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceInstanceID</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceID</td>
      <td>stringa</td>
      <td>ID campagna</td>
      <td>Sì</td>
      <td>
        <p>Ad esempio: - 55555.</p>
        <p>Chiave esterna di Campaign</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceInstanceID</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="4">Dettagli del membro della campagna aziendale XDM</td>
      <td>b2b.personType</td>
      <td>stringa</td>
      <td>"Lead" o "Contact"</td>
      <td>Sì</td>
      <td>A seconda della tabella dell’origine dati, deve essere impostato su "Lead" o "Contact". Per la maggior parte dei casi d’uso consigliamo di impostarlo su "Contatto"</td>
    </tr>
    <tr>
      <td></td>
      <td>memberStatus</td>
      <td>stringa</td>
      <td>Stato</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>hasResponded</td>
      <td>booleano</td>
      <td>Ha risposto</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>firstRespondedDate</td>
      <td>data-ora</td>
      <td>FirstRespondedDate</td>
      <td>No</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Persona</strong> (contatto o lead per Salesforce, persone per Marketo)</td>
    </tr>
    <tr>
      <td>Profilo individuale XDM</td>
      <td rowspan="11">Dettagli persona aziendale XDM</td>
      <td>b2b.personKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Ad esempio: 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personKey.sourceID</td>
      <td>stringa</td>
      <td>ID</td>
      <td>Sì</td>
      <td>Ad esempio: - 333, a seconda della tabella dell’origine dati, può essere un ID lead o un ID contatto</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personKey.sourceInstanceID</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>workEmail.address</td>
      <td>
        <p>stringa</p>
        <p>e-mail</p>
      </td>
      <td>E-mail</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personStatus</td>
      <td>stringa</td>
      <td>Stato</td>
      <td><b><i>Sì solo per il tipo di persona lead</i></b></td>
      <td>Richiesto solo se b2b.personType è "Lead"</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>data-ora</td>
      <td>CreatedDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>data-ora</td>
      <td>ModifiedDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.isConverted</td>
      <td>booleano</td>
      <td>IsConverted</td>
      <td><b><i>Sì solo per il tipo di persona lead</i></b></td>
      <td>Richiesto solo se b2b.personType è "Lead"</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personType</td>
      <td>stringa</td>
      <td>"Lead" o "Contact"</td>
      <td>Sì</td>
      <td>A seconda della tabella dell’origine dati, deve essere impostato su "Lead" o "Contact". Per la maggior parte dei casi d’uso consigliamo di impostarlo su "Contatto"</td>
    </tr>
    <tr>
      <td></td>
      <td>extendedWorkDetails.jobTitle</td>
      <td>stringa</td>
      <td></td>
      <td>No</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="4">Componenti della persona aziendale XDM</td>
      <td>personComponents.sourceAccountKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>No</td>
      <td>
        <p>Ad esempio: 123@999-abc-888.Marketo.</p>
        <p>Il set di campi sourceAccountKey è "obbligatorio" solo per i record Contatto effettivi, definiti come record persona collegati a Account. Se manca, il set di dati non verrà rifiutato, ma i risultati dell’attribuzione saranno disattivati.</p>
        <p>personComponents è un array, ma Marketo Measure accetta solo il primo elemento personComponents[0]</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personComponents.sourceAccountKey.sourceID</td>
      <td>stringa</td>
      <td>ID account</td>
      <td>No</td>
      <td>
        <p>Esempio: - 123.</p>
        <p>Chiave esterna dell’account</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personComponents.sourceAccountKey.sourceInstanceID</td>
      <td>stringa</td>
      <td></td>
      <td>No</td>
      <td>es. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>personComponents.sourceAccountKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>No</td>
      <td>Esempio: Marketo</td>
    </tr>
    <tr>
      <td colspan="7"><strong>Opportunità</strong> (opportunità per Salesforce, opportunità per Marketo)</td>
    </tr>
    <tr>
      <td rowspan="13">Opportunità di business XDM</td>
      <td></td>
      <td>opportunityKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 77777@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceID</td>
      <td>stringa</td>
      <td>ID</td>
      <td>Sì</td>
      <td>Ad esempio: - 77777</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceInstanceID</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>data-ora</td>
      <td>CreatedDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>data-ora</td>
      <td>ModifiedDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 123@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceID</td>
      <td>stringa</td>
      <td>ID account</td>
      <td>Sì</td>
      <td>
        <p>Esempio: - 123.</p>
        <p>Chiave esterna dell’account</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceInstanceID</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>NomeOpzione</td>
      <td>stringa</td>
      <td>Nome</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>optionStage</td>
      <td>stringa</td>
      <td>Fase</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>tipo opportunità</td>
      <td>stringa</td>
      <td></td>
      <td>No</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="5">Dettagli sull’opportunità di business XDM</td>
      <td>isWon</td>
      <td>booleano</td>
      <td>È vinto</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>isClosed</td>
      <td>booleano</td>
      <td>IsClosed</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>expectedCloseDate</td>
      <td>data</td>
      <td>CloseDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityAmount.amount</td>
      <td>numero</td>
      <td>Importo</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityAmount.currencyCode</td>
      <td>
        <p>stringa</p>
        <p>^[A-Z]{3}$</p>
      </td>
      <td>CurrencyIsoCode</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Ruolo contatto opportunità (necessario solo se si intende utilizzare il Ruolo contatto opportunità come gruppo di acquisto per l’attribuzione)</strong></td>
    </tr>
    <tr>
      <td rowspan="16">Relazione della persona dell’opportunità di business XDM</td>
      <td></td>
      <td>personKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceID</td>
      <td>stringa</td>
      <td>ID contatto</td>
      <td>Sì</td>
      <td>
        <p>Esempio: - 333.</p>
        <p>Chiave esterna al contatto</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceInstanceID</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>isPrimary</td>
      <td>booleano</td>
      <td>IsPrimary</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 77777@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceID</td>
      <td>stringa</td>
      <td>ID opportunità</td>
      <td>Sì</td>
      <td>
        <p>Esempio: - 77777.</p>
        <p>Chiave esterna dell’opportunità</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceInstanceID</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 222222@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceID</td>
      <td>stringa</td>
      <td>ID</td>
      <td>Sì</td>
      <td>Esempio: - 222222</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceInstanceID</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>personRole</td>
      <td>stringa</td>
      <td>Ruolo</td>
      <td>No</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>data-ora</td>
      <td>CreatedDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>data-ora</td>
      <td>ModifiedDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Tasso di conversione (necessario solo se si utilizzano più valute; è possibile attivare un solo set di dati per il tasso di conversione in Marketo Measure)</strong></td>
    </tr>
    <tr>
      <td rowspan="7">Conversione</td>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 8888@0x012345.Salesforce</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceId</td>
      <td>stringa</td>
      <td>ID</td>
      <td>Sì</td>
      <td>Esempio: - 8888</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceInstanceId</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: - 0x012345</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: Salesforce</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>data-ora</td>
      <td>CreatedDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>data-ora</td>
      <td>ModifiedDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>isDeleted</td>
      <td>booleano</td>
      <td></td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="5">Dettagli tasso di conversione valuta</td>
      <td>conversionRate</td>
      <td>numero</td>
      <td>ConversionRate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>endDate</td>
      <td>data</td>
      <td>NextStartDate</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>startDate</td>
      <td>data</td>
      <td>DataInizio</td>
      <td>Sì</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>sourceISOCode</td>
      <td>stringa</td>
      <td>Codice ISOC</td>
      <td>Sì</td>
      <td>Ad esempio EUR</td>
    </tr>
    <tr>
      <td></td>
      <td>targetISOCode</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Il codice valuta predefinito impostato in Marketo Measure, ad esempio USD</td>
    </tr>
  </tbody>
</table>

## Requisiti per i dati di conversione valuta {#currency-conversion-data-requirements}

**Valuta predefinita**: in Marketo Measure, tutti i ricavi e i costi vengono convertiti in una valuta predefinita al momento della generazione del rapporto. Deve esistere un record con la stessa copertura data per la valuta target stessa (ad esempio, da USD a USD) con un tasso di conversione di 1.

**Tassi di conversione**: ogni coppia (valuta di origine, valuta di destinazione) può avere più tassi di conversione per diversi periodi di date. Le percentuali devono coprire l&#39;intero intervallo di tempo compreso tra 0001-01-01 e 9999-12-31, in base all&#39;oggetto Salesforce DatedConversionRate.

**Intervallo date**:
* Nessun intervallo di date sovrapposto all’interno di un set di tassi (valuta di origine, valuta di destinazione) (ad esempio, dal 2023-01-01 al 2023-02-01 e dal 2023-01-01 al 2024-01-01).
* Nessun intervallo tra intervalli di date. La data di inizio è inclusiva e la data di fine è esclusiva.

<p>

## ExperienceEvent {#experienceevent}

<table style="table-layout:auto">
  <tr>
    <th>Classe XDM</th>
    <th>Gruppo di campi XDM</th>
    <th>Percorso XDM</th>
    <th>Tipo XDM</th>
    <th>Campo Source dati</th>
    <th>Obbligatorio</th>
    <th>Note</th>
  </tr>
  <tbody>
    <tr>
      <td colspan="7"><strong>Attività</strong></td>
    </tr>
    <tr>
      <td rowspan="3">XDM ExperienceEvent</td>
      <td></td>
      <td>_id</td>
      <td>stringa</td>
      <td>ID</td>
      <td>Sì</td>
      <td>Sì</td>
    </tr>
    <tr>
      <td></td>
      <td>eventType</td>
      <td>stringa</td>
      <td>TipoAttività</td>
      <td>Sì</td>
      <td>Sì</td>
    </tr>
    <tr>
      <td></td>
      <td>timestamp</td>
      <td>data-ora</td>
      <td>Data attività</td>
      <td>Sì</td>
      <td>Sì</td>
    </tr>
    <tr>
      <td></td>
      <td>Identificatore della persona</td>
      <td>personKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>personKey.sourceID</td>
      <td>stringa</td>
      <td>ID lead o ID contatto</td>
      <td>Sì</td>
      <td>
        <p>Ad esempio: - 333, a seconda della tabella dell’origine dati, può essere un ID lead o un ID contatto.</p>
        <p>Chiave esterna per lead o contatto</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>personKey.sourceInstanceID</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>personKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>Sì</td>
      <td>Esempio: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>Aggiungi a campagna</td>
      <td>leadOperation.addToCampaign.campaignKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>Sì solo per il tipo leadOperation.addToCampaign</td>
      <td>Esempio: 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.addToCampaign.campaignKey.sourceId</td>
      <td>stringa</td>
      <td>ID campagna</td>
      <td>Sì solo per il tipo leadOperation.addToCampaign</td>
      <td>
        <p>Ad esempio: - 55555.</p>
        <p>Chiave esterna di Campaign</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.addToCampaign.campaignKey.sourceInstanceId</td>
      <td>stringa</td>
      <td></td>
      <td>Sì solo per il tipo leadOperation.addToCampaign</td>
      <td>Esempio: 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.addToCampaign.campaignKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>Sì solo per il tipo leadOperation.addToCampaign</td>
      <td>Esempio: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>Stato nella progressione della campagna modificato</td>
      <td>leadOperation.campaignProgression.campaignKey.sourceKey</td>
      <td>stringa</td>
      <td></td>
      <td>Sì solo per il tipo leadOperation.campaignProgression</td>
      <td>Esempio: 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.campaignProgression.campaignKey.sourceId</td>
      <td>stringa</td>
      <td>ID campagna</td>
      <td>Sì solo per il tipo leadOperation.campaignProgression</td>
      <td>
        <p>Ad esempio: - 55555.</p>
        <p>Chiave esterna di Campaign</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.campaignProgression.campaignKey.sourceInstanceId</td>
      <td>stringa</td>
      <td></td>
      <td>Sì solo per il tipo leadOperation.campaignProgression</td>
      <td>Esempio: 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.campaignProgression.campaignKey.sourceType</td>
      <td>stringa</td>
      <td></td>
      <td>Sì solo per il tipo leadOperation.campaignProgression</td>
      <td>Esempio: Marketo</td>
    </tr>
  </tbody>
</table>

## Tipo di ExperienceEvent supportato {#experienceevent-type-supported}

<table style="table-layout:auto">
  <tr>
    <th>Tipo evento</th>
    <th>Tipo di evento XDM</th>
    <th>Descrizione</th>
  </tr>
  <tbody>
    <tr>
      <td>Nuovo lead</td>
      <td>leadOperation.newLead</td>
      <td>Utilizzare per registrare la creazione e i dettagli di un nuovo lead di marketing</td>
    </tr>
    <tr>
      <td>Converti lead</td>
      <td>leadOperation.convertLead</td>
      <td>Utilizzare quando un lead di marketing viene convertito in un contatto qualificato per la vendita assegnato a un utente di vendita</td>
    </tr>
    <tr>
      <td>Momento di interesse</td>
      <td>leadOperation.interestingMoment</td>
      <td>Usa per il tracciamento delle attività di valore elevato da parte di clienti potenziali</td>
    </tr>
    <tr>
      <td>Compila modulo</td>
      <td>web.formFilledOut</td>
      <td>Utilizzare per acquisire dettagli quando una persona compila un modulo su una pagina web</td>
    </tr>
    <tr>
      <td>Annulla iscrizione e-mail</td>
      <td>directMarketing.emailUnsubscribed</td>
      <td>Utilizzare per acquisire dettagli quando una persona annulla l’iscrizione a un’e-mail</td>
    </tr>
    <tr>
      <td>Apri e-mail</td>
      <td>directMarketing.emailOpened</td>
      <td>Utilizzare per acquisire dettagli quando una persona apre un’e-mail di marketing</td>
    </tr>
    <tr>
      <td>Fai clic su E-mail</td>
      <td>directMarketing.emailClicked</td>
      <td>Utilizzare per acquisire dettagli quando una persona fa clic su un collegamento in un’e-mail di marketing</td>
    </tr>
    <tr>
      <td>Modifica stato in progressione</td>
      <td>leadOperation.statusInCampaignProgressionChanged</td>
      <td>Utilizzare per acquisire dettagli quando lo stato di un lead in una campagna cambia</td>
    </tr>
    <tr>
      <td>Aggiungi al programma di coinvolgimento (aggiungi allo sviluppo)</td>
      <td>leadOperation.addToCampaign</td>
      <td>Utilizza per aggiungere una persona alla campagna specifica.</td>
    </tr>
  </tbody>
</table>

Utilizza il tipo di evento &quot;Momento di interesse&quot; per i tipi di evento non supportati nella tabella precedente. Aggiungi un campo personalizzato per indicare il sottotipo &quot;Momento di interesse&quot;.

## Esempi di query per l’ispezione dei dati {#query-examples-for-data-inspection}

Di seguito è riportato un elenco di esempi di query per l’analisi dei set di dati acquisiti nel data lake di AEP. Per utilizzarli nei set di dati, sostituisci il nome della tabella negli esempi di query seguenti con il nome effettivo della tabella del set di dati.

Tutti i conteggi dovrebbero essere 0.

Per il campo personType sono previsti solo valori &quot;Lead&quot; o &quot;Contact&quot; e non è presente alcun valore null.

Per tutti i record relativi a &quot;Contatto&quot;, si presume che sia presente una chiave esterna dell&#39;account.

Per i record persona &quot;Lead&quot;, la chiave esterna dell’account non esiste e non è obbligatoria. Se scegli di acquisire i record persona &quot;Lead&quot; come record persona &quot;di contatto&quot; (opzione consigliata), non è necessaria una chiave esterna Account in tali record persona.

### Account aziendale XDM {#xdm-business-account}

```
select 'account source id', count(*) from salesforce_account where accountKey.sourceId is null
union all
select 'account source type', count(*) from salesforce_account where accountKey.sourceType is null
union all
select 'account source instance id', count(*) from salesforce_account where accountKey.sourceInstanceId is null
union all
select 'account source key', count(*) from salesforce_account where accountKey.sourceKey is null
union all
select 'account name', count(*) from salesforce_account where accountName is null
union all
select 'created date', count(*) from salesforce_account where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_account where extSourceSystemAudit.lastUpdatedDate is null;
```

### Campagna aziendale XDM {#xdm-business-campaign}

```
select 'campaign source id', count(*) from salesforce_campaign where campaignKey.sourceId is null
union all
select 'campaign source type', count(*) from salesforce_campaign where campaignKey.sourceType is null
union all
select 'campaign source instance id', count(*) from salesforce_campaign where campaignKey.sourceInstanceId is null
union all
select 'campaign source key', count(*) from salesforce_campaign where campaignKey.sourceKey is null
union all
select 'campaign name', count(*) from salesforce_campaign where campaignName is null
union all
select 'created date', count(*) from salesforce_campaign where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_campaign where extSourceSystemAudit.lastUpdatedDate is null;
```

### Membro della campagna aziendale XDM {#xdm-business-campaign-member}

```
select 'campaign member source id', count(*) from salesforce_campaign_member where campaignMemberKey.sourceId is null
union all
select 'campaign member source type', count(*) from salesforce_campaign_member where campaignMemberKey.sourceType is null
union all
select 'campaign member source instance id', count(*) from salesforce_campaign_member where campaignMemberKey.sourceInstanceId is null
union all
select 'campaign member source key', count(*) from salesforce_campaign_member where campaignMemberKey.sourceKey is null
union all
select 'campaign source id', count(*) from salesforce_campaign_member where campaignKey.sourceId is null
union all
select 'campaign source type', count(*) from salesforce_campaign_member where campaignKey.sourceType is null
union all
select 'campaign source instance id', count(*) from salesforce_campaign_member where campaignKey.sourceInstanceId is null
union all
select 'campaign source key', count(*) from salesforce_campaign_member where campaignKey.sourceKey is null
union all
select 'person source id', count(*) from salesforce_campaign_member where personKey.sourceId is null
union all
select 'person source type', count(*) from salesforce_campaign_member where personKey.sourceType is null
union all
select 'person source instance id', count(*) from salesforce_campaign_member where personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from salesforce_campaign_member where personKey.sourceKey is null
union all
select distinct 'person type', b2b.personType from salesforce_campaign_member
union all
select 'member status', count(*) from salesforce_campaign_member where memberStatus is null
union all
select 'has responded', count(*) from salesforce_campaign_member where hasResponded is null
union all
select 'created date', count(*) from salesforce_campaign_member where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_campaign_member where extSourceSystemAudit.lastUpdatedDate is null;
```

### Persona aziendale XDM {#xdm-business-person}

```
select 'person source id', count(*) from marketo_person where b2b.personKey.sourceId is null
union all
select 'person source type', count(*) from marketo_person where b2b.personKey.sourceType is null
union all
select 'person source instance id', count(*) from marketo_person where b2b.personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from marketo_person where b2b.personKey.sourceKey is null
union all
select 'email', count(*) from marketo_person where workEmail.address is null
union all
select 'Lead - person status', count(*) from marketo_person where b2b.personType = 'Lead' and b2b.personStatus is null
union all
select 'Lead - is converted', count(*) from marketo_person where b2b.personType = 'Lead' and b2b.isConverted is null
union all
select distinct 'person type', b2b.personType from marketo_person
union all
select 'created date', count(*) from marketo_person where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from marketo_person where extSourceSystemAudit.lastUpdatedDate is null;
```

```
select 'person source id', count(*) from salesforce_contact where b2b.personKey.sourceId is null
union all
select 'person source type', count(*) from salesforce_contact where b2b.personKey.sourceType is null
union all
select 'person source instance id', count(*) from salesforce_contact where b2b.personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from salesforce_contact where b2b.personKey.sourceKey is null
union all
select 'email', count(*) from salesforce_contact where workEmail.address is null
union all
select 'Lead - person status', count(*) from salesforce_contact where b2b.personType = 'Lead' and b2b.personStatus is null
union all
select 'Lead - is converted', count(*) from salesforce_contact where b2b.personType = 'Lead' and b2b.isConverted is null
union all
select distinct 'person type', b2b.personType from salesforce_contact
union all
select 'account source id', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceId is null
union all
select 'account source type', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceType is null
union all
select 'account source instance id', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceInstanceId is null
union all
select 'account source key', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceKey is null
union all
select 'created date', count(*) from salesforce_contact where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_contact where extSourceSystemAudit.lastUpdatedDate is null;
```

### Opportunità di business XDM {#xdm-business-opportunity}

```
select 'opportunity source id', count(*) from salesforce_opportunity where opportunityKey.sourceId is null
union all
select 'opportunity source type', count(*) from salesforce_opportunity where opportunityKey.sourceType is null
union all
select 'opportunity source instance id', count(*) from salesforce_opportunity where opportunityKey.sourceInstanceId is null
union all
select 'opportunity source key', count(*) from salesforce_opportunity where opportunityKey.sourceKey is null
union all
select 'account source id', count(*) from salesforce_opportunity where accountKey.sourceId is null
union all
select 'account source type', count(*) from salesforce_opportunity where accountKey.sourceType is null
union all
select 'account source instance id', count(*) from salesforce_opportunity where accountKey.sourceInstanceId is null
union all
select 'account source key', count(*) from salesforce_opportunity where accountKey.sourceKey is null
union all
select 'opportunity name', count(*) from salesforce_opportunity where opportunityName is null
union all
select 'opportunity stage', count(*) from salesforce_opportunity where opportunityStage is null
union all
select 'is won', count(*) from salesforce_opportunity where isWon is null
union all
select 'is closed', count(*) from salesforce_opportunity where isClosed is null
union all
select 'expected close date', count(*) from salesforce_opportunity where expectedCloseDate is null
union all
select 'opportunity amount', count(*) from salesforce_opportunity where opportunityAmount.amount is null
union all
select 'currency code', count(*) from salesforce_opportunity where opportunityAmount.currencyCode is null
union all
select 'created date', count(*) from salesforce_opportunity where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_opportunity where extSourceSystemAudit.lastUpdatedDate is null;
```

### XDM ExperienceEvent {#xdm-experienceevent}

```
select 'id', count(*) from marketo_activity where _id is null
union all
select 'event type', count(*) from marketo_activity where eventType is null
union all
select 'timestamp', count(*) from marketo_activity where timestamp is null
union all
select 'person source id', count(*) from marketo_activity where personKey.sourceId is null
union all
select 'person source type', count(*) from marketo_activity where personKey.sourceType is null
union all
select 'person source instance id', count(*) from marketo_activity where personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from marketo_activity where personKey.sourceKey is null
union all
select 'addToCampaign campaign id', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceId is null
union all
select 'addToCampaign campaign type', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceType is null
union all
select 'addToCampaign campaign instance id', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceInstanceId is null
union all
select 'addToCampaign campaign key', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceKey is null
union all
select 'statusInCampaignProgressionChanged campaign id', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceId is null
union all
select 'statusInCampaignProgressionChanged campaign type', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceType is null
union all
select 'statusInCampaignProgressionChanged campaign instance id', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceInstanceId is null
union all
select 'statusInCampaignProgressionChanged campaign key', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceKey is null;
```

```
select 'id', count(*) from salesforce_task where _id is null
union all
select 'event type', count(*) from salesforce_task where eventType is null
union all
select 'timestamp', count(*) from salesforce_task where timestamp is null
union all
select 'person source id', count(*) from salesforce_task where personKey.sourceId is null
union all
select 'person source type', count(*) from salesforce_task where personKey.sourceType is null
union all
select 'person source instance id', count(*) from salesforce_task where personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from salesforce_task where personKey.sourceKey is null;
```

### Conversione {#conversion}

```
select 'conversion rate', count(*) from currency_conversion_rate where conversionRate is null
union all
select 'end date', count(*) from currency_conversion_rate where endDate is null
union all
select 'start date', count(*) from currency_conversion_rate where startDate is null
union all
select 'source ISO Code', count(*) from currency_conversion_rate where sourceISOCode is null
union all
select 'target ISO Code', count(*) from currency_conversion_rate where targetISOCode is null
union all
select 'source id', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceId is null
union all
select 'source type', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceType is null
union all
select 'source instance id', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceInstanceId is null
union all
select 'source key', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceKey is null
union all
select 'created date', count(*) from currency_conversion_rate where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from currency_conversion_rate where extSourceSystemAudit.lastUpdatedDate is null;
```

## Soluzione consigliata per i campi obbligatori con valore NULL {#recommended-solution-for-required-fields-with-a-null-value}

È consigliabile utilizzare un campo calcolato nel mapping dei campi per impostare il campo come predefinito su un valore non NULL. Di seguito sono riportati due esempi:

* Se il valore di NomeOpportunità di alcuni record di opportunità è Null, creare e utilizzare il seguente campo calcolato nella mappatura dei campi
   * `iif(name != null && trim(name) != "", name, "Unknown")`

* Se leadOperation.campaignProgression.campaignID di alcuni record experienceevent sono null, crea e utilizza il seguente campo calcolato nella mappatura dei campi
   * `iif(leadOperation.campaignProgression.campaignID != null && leadOperation.campaignProgression.campaignID != "" , to_object("sourceType", "Marketo", "sourceInstanceID", "123-abc-321", "sourceID", leadOperation.campaignProgression.campaignID, "sourceKey", concat(leadOperation.campaignProgression.campaignID,"@123-abc-321.Marketo")), iif(eventType == "leadOperation.statusInCampaignProgressionChanged", to_object("sourceType", "Marketo", "sourceInstanceID", "123-abc-321", "sourceID", "Unknown", "sourceKey", "Unknown@123-abc-321.Marketo"), null))`
