---
author: DCtheGeek
ms.service: azure-policy
ms.topic: include
ms.date: 01/25/2021
ms.author: dacoulte
ms.custom: generated
ms.openlocfilehash: 2d28e331b576c9152593b556864fb2c4b50a3742
ms.sourcegitcommit: fc8ce6ff76e64486d5acd7be24faf819f0a7be1d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98807424"
---
|Name<br /><sub>(Azure-Portal)</sub> |BESCHREIBUNG |Auswirkungen |Version<br /><sub>(GitHub)</sub> |
|---|---|---|---|
|[Azure Data Factorys müssen mit einem kundenseitig verwalteten Schlüssel (CMK) verschlüsselt werden](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F4ec52d6d-beb7-40c4-9a9e-fe753254690e) |Verwenden Sie kundenseitig verwaltete Schlüssel (Customer-Managed Keys, CMKs), um die Verschlüsselung ruhender Daten für Ihre Azure Data Factory-Instanz zu verwalten. Standardmäßig werden Kundendaten mit dienstseitig verwalteten Schlüsseln verschlüsselt. CMKs sind jedoch häufig zur Einhaltung gesetzlicher Bestimmungen erforderlich. Mit CMKs können die Daten mit einem Azure Key Vault-Schlüssel verschlüsselt werden, der von Ihnen erstellt wird und sich in Ihrem Besitz befindet. Sie verfügen über die volle Kontrolle über und Verantwortung für den Schlüssellebenszyklus, einschließlich Rotation und Verwaltung. Weitere Informationen zur CMK-Verschlüsselung finden Sie unter [https://aka.ms/adf-cmk](https://aka.ms/adf-cmk). |Audit, Deny, Disabled |[1.0.0](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Data%20Factory/DataFactory_CustomerManagedKey_Audit.json) |
