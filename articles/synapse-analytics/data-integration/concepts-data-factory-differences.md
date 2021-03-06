---
title: Unterschiede zu Azure Data Factory
description: Erfahren Sie, wie sich die Datenintegrationsfunktionen von Azure Synapse Analytics von denen in Azure Data Factory unterscheiden.
services: synapse-analytics
author: kromerm
ms.service: synapse-analytics
ms.topic: conceptual
ms.date: 12/10/2020
ms.author: makromer
ms.reviewer: jrasnick
ms.openlocfilehash: 8818d4db489cef8203ae515c18c61e215d577033
ms.sourcegitcommit: ea17e3a6219f0f01330cf7610e54f033a394b459
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97387614"
---
# <a name="data-integration-in-azure-synapse-analytics-versus-azure-data-factory"></a>Datenintegration in Azure Synapse Analytics im Vergleich zu Azure Data Factory

In Azure Synapse Analytics basieren die Datenintegrationsfunktionen wie Synapse-Pipelines und Datenflüsse auf denen von Azure Data Factory. Weitere Informationen finden Sie unter [Was ist Azure Data Factory?](../../data-factory/introduction.md).


## <a name="available-features-in-adf--azure-synapse-analytics"></a>Verfügbare Funktionen in ADF und Azure Synapse Analytics

Sehen Sie in der folgenden Tabelle nach, welche Funktionen zur Verfügung stehen:

| Kategorie                 | Funktion    |  Azure Data Factory  | Azure Synapse Analytics |
| ------------------------ | ---------- | :------------------: | :---------------------: |
| **Integration Runtime**  | Verwenden von SSIS und SSIS Integration Runtime | ✓ | ✗ |
|                          | Unterstützung für regionsübergreifende Integration Runtime (Datenflüsse) | ✓ | ✗ |
|                          | Integration Runtime-Freigabe | ✓<br><small>*Kann für verschiedene Data Factory-Instanzen freigegeben werden* | ✗ |
|                          | Gültigkeitsdauer | ✓ | ✗ |
| **Azure Pipelines-Aktivitäten** | Aktivität „SSIS-Paket“ | ✓ | ✗ |
|                          | Unterstützung für Power Query-Aktivität | ✓ | ✓ |
| **Vorlagenkatalog und Knowledge Center** | Lösungsvorlagen | ✓<br><small>*Azure Data Factory-Vorlagenkatalog* | ✓<br><small>*Knowledge Center für den Synapse-Arbeitsbereich* |
| **Integration von Git-Repository** | Git-Integration | ✓ | ✓ |
| **Überwachung**           | Überwachen von Spark-Aufträgen für den Datenfluss | ✗ | ✓<br><small>*Nutzen der Synapse Spark-Pools* |
|                          | Integration in Azure Monitor | ✓ | ✗ |

> [!Note]
> **Gültigkeitsdauer** ist eine Azure Integration Runtime-Einstellung, die es dem Spark-Cluster ermöglicht, während eines bestimmten Zeitraums nach einer Ausführung des Datenflusses *betriebsbereit zu bleiben*.
>


## <a name="next-steps"></a>Nächste Schritte

Erste Schritte mit der Datenintegration in Ihrem Synapse-Arbeitsbereich, indem Sie lernen, wie Sie [Daten in einem Azure Data Lake Storage Gen2-Konto erfassen](data-integration-data-lake.md).
