---
title: Renderingmodi
description: Beschreibt die verschiedenen serverseitigen Renderingmodi.
author: florianborn71
ms.author: flborn
ms.date: 02/03/2020
ms.topic: conceptual
ms.custom: devx-track-csharp
ms.openlocfilehash: 3d8ff6640f856b3227cead6dc50befca5d5ef3e8
ms.sourcegitcommit: 957c916118f87ea3d67a60e1d72a30f48bad0db6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92202768"
---
# <a name="rendering-modes"></a>Renderingmodi

Für Remote Rendering stehen zwei hauptsächliche Betriebsmodi zur Verfügung: **TileBasedComposition** und **DepthBasedComposition**. Diese Modi bestimmen, wie die Workload auf mehrere GPUs auf dem Server verteilt wird. Der Modus muss zur Verbindungszeit angegeben werden und kann während der Laufzeit nicht geändert werden.

Beide Modi verfügen über Vorteile, aber auch über jeweilige Featureeinschränkungen, sodass die Auswahl des am besten geeigneten Modus für den Anwendungsfall spezifisch ist.

## <a name="modes"></a>Modi

Die beiden Modi werden nun ausführlicher erläutert.

### <a name="tilebasedcomposition-mode"></a>Modus „TileBasedComposition“

Im Modus **TileBasedComposition** rendert jede beteiligte GPU bestimmte Unterrechtecke (Kacheln) auf dem Bildschirm. Die Haupt-GPU stellt das endgültige Bild aus den Kacheln zusammen, bevor es als Videoframe an den Client gesendet wird. Dementsprechend müssen alle GPUs über denselben Ressourcensatz für das Rendering verfügen, sodass die geladenen Medienobjekte in den Arbeitsspeicher einer einzelnen GPU passen müssen.

Die Renderingqualität in diesem Modus ist etwas besser als im Modus **DepthBasedComposition**, da MSAA für jede GPU am vollständigen Geometriesatz arbeiten kann. Der folgende Screenshot zeigt, dass Antialiasing für beide Ränder ordnungsgemäß funktioniert:

![MSAA in TileBasedComposition](./media/service-render-mode-quality.png)

Außerdem kann in diesem Modus jedes Teil in ein transparentes Material oder über [HierarchicalStateOverrideComponent](../overview/features/override-hierarchical-state.md) in den **durchsichtigen** Modus umgeschaltet werden.

### <a name="depthbasedcomposition-mode"></a>Modus „DepthBasedComposition“

Im Modus **DepthBasedComposition** rendert jede beteiligte GPU mit vollständiger Bildschirmauflösung, aber nur eine Teilmenge der Gittermodelle. Die endgültige Bildkomposition auf der Haupt-GPU ist dafür verantwortlich, dass Teile entsprechend Ihrer Tiefeninformationen ordnungsgemäß zusammengeführt werden. Natürlich wird die Speichernutzlast auf die GPUs verteilt und ermöglicht das Rendern von Modellen, die nicht in den Arbeitsspeicher einer einzelnen GPU passen würden.

Jede einzelne GPU verwendet MSAA für das Antialiasing von lokalen Inhalten. Möglicherweise gibt es jedoch ein inhärentes Aliasing zwischen den Rändern von unterschiedlichen GPUs. Dieser Effekt wird durch die Nachverarbeitung des endgültigen Bilds verringert, die MSAA-Qualität ist aber noch schlechter als im **TileBasedComposition**-Modus.

MSAA-Artefakte werden in der folgenden Abbildung gezeigt: ![MSAA in DepthBasedComposition](./media/service-render-mode-balanced.png)

Antialiasing funktioniert ordnungsgemäß zwischen der Skulptur und dem Vorhang, da beide Teile auf derselben GPU gerendert werden. Auf der anderen Seite zeigt der Rand zwischen dem Vorhang und der Wand etwas Aliasing, da diese beiden Teile von unterschiedlichen GPUs zusammengesetzt werden.

Die größte Einschränkung dieses Modus besteht darin, dass Geometrieteile nicht dynamisch in transparente Materialien umgeschaltet werden können. Auch funktioniert der **durchsichtige** Modus nicht für [HierarchicalStateOverrideComponent](../overview/features/override-hierarchical-state.md). Andere Statusüberschreibungsfunktionen (Umriss, Farbschattierung usw.) funktionieren jedoch. Auch Materialien, die bei der Konvertierung als transparent gekennzeichnet wurden, funktionieren in diesem Modus ordnungsgemäß.

### <a name="performance"></a>Leistung

Die Leistungsmerkmale beider Modi variieren je nach Anwendungsfall, und es ist schwierig, Aussagen zu treffen oder allgemeine Empfehlungen auszusprechen. Wenn die oben genannten Einschränkungen (Arbeitsspeicher oder Transparenz/Durchsichtigkeit) für Sie unproblematisch sind, wird empfohlen, beide Modi auszuprobieren und die Leistung mithilfe verschiedener Kamerapositionen zu überwachen.

## <a name="setting-the-render-mode"></a>Festlegen des Renderingmodus

Der auf einem Remote Rendering-Server verwendete Renderingmodus wird während `AzureSession.ConnectToRuntime` über `ConnectToRuntimeParams` angegeben.

```cs
async void ExampleConnect(AzureSession session)
{
    ConnectToRuntimeParams parameters = new ConnectToRuntimeParams();

    // Connect with one rendering mode
    parameters.mode = ServiceRenderMode.TileBasedComposition;
    await session.ConnectToRuntime(parameters).AsTask();

    session.DisconnectFromRuntime();

    // Wait until session.IsConnected == false

    // Reconnect with a different rendering mode
    parameters.mode = ServiceRenderMode.DepthBasedComposition;
    await session.ConnectToRuntime(parameters).AsTask();
}
```

## <a name="api-documentation"></a>API-Dokumentation

* [C# AzureSession.ConnectToRuntime()](/dotnet/api/microsoft.azure.remoterendering.azuresession.connecttoruntime)
* [C# ConnectToRuntimeParams-Struktur](/dotnet/api/microsoft.azure.remoterendering.connecttoruntimeparams)
* [C++ AzureSession::ConnectToRuntime()](/cpp/api/remote-rendering/azuresession#connecttoruntime)
* [C++ ConnectToRuntimeParams-Struktur](/cpp/api/remote-rendering/connecttoruntimeparams)

## <a name="next-steps"></a>Nächste Schritte

* [Sitzungen](../concepts/sessions.md)
* [Komponente „Hierarchische Zustandsüberschreibung“](../overview/features/override-hierarchical-state.md)