---
title: Verbessern der Synthese mit Custom Voice – Speech-Dienst
titleSuffix: Azure Cognitive Services
description: Bei Custom Voice handelt es sich um eine Reihe von Onlinetools, mit denen Sie eine wiedererkennbare, einzigartige Stimme für Ihre Marke erstellen können. Für den Einstieg benötigen Sie lediglich einige Audiodateien und die dazugehörigen Transkriptionen. Nutzen Sie die unten angegebenen Links, um mit der Erstellung einer benutzerdefinierten Spracherkennung zu beginnen.
services: cognitive-services
author: trevorbye
manager: nitinme
ms.service: cognitive-services
ms.subservice: speech-service
ms.topic: conceptual
ms.date: 02/17/2020
ms.author: trbye
ms.openlocfilehash: e48dfd224a9656c7d8327dd77f1b55e9a744f3af
ms.sourcegitcommit: 65cef6e5d7c2827cf1194451c8f26a3458bc310a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/19/2021
ms.locfileid: "98573087"
---
# <a name="get-started-with-custom-voice"></a>Erste Schritte mit Custom Voice

Bei [Custom Voice](https://aka.ms/customvoice) handelt es sich um eine Reihe von Onlinetools, mit denen Sie eine wiedererkennbare, einzigartige Stimme für Ihre Marke erstellen können. Für den Einstieg benötigen Sie lediglich einige Audiodateien und die dazugehörigen Transkriptionen. Nutzen Sie die unten angegebenen Links, um mit dem Erstellen einer benutzerdefinierten Sprachsynthese zu beginnen.

## <a name="whats-in-custom-voice"></a>Was ist in Custom Voice enthalten?

Bevor Sie mit der Verwendung von Custom Voice beginnen können, benötigen Sie ein Azure-Konto und ein Abonnement für den Speech-Dienst. Nachdem Sie ein Konto erstellt haben, können Sie Ihre Daten vorbereiten, Ihre Modelle trainieren und testen, die Stimmqualität bewerten und schließlich Ihr benutzerdefiniertes Stimmmodell bereitstellen.

Im folgenden Diagramm sind die Schritte zum Erstellen eines benutzerdefinierten Stimmmodells über das [Custom Voice-Portal](https://aka.ms/customvoice) hervorgehoben. Weitere Informationen finden Sie unter den Links.

![Custom Voice-Architekturdiagramm](media/custom-voice/custom-voice-diagram.png)

1. [Abonnieren und Erstellen eines Projekts:](#set-up-your-azure-account) Erstellen Sie ein Azure-Konto und ein Abonnement für den Speech-Dienst. Durch dieses konsolidierte Abonnement erhalten Sie Zugriff auf die Spracherkennung, Sprachsynthese, Sprachübersetzung und das Custom Voice-Portal. Erstellen Sie anschließend unter Verwendung Ihres Abonnements für den Speech-Dienst Ihr erstes Custom Voice-Projekt.

2. [Hochladen von Daten:](how-to-custom-voice-create-voice.md#upload-your-datasets) Laden Sie Daten (Audio und Text) über das Custom Voice-Portal oder über die Custom Voice-API hoch. Über das Portal können Sie Aussprachebewertungen und Signal-Rausch-Verhältnisse untersuchen und bewerten. Weitere Informationen finden Sie unter [Prepare data to create a custom voice](how-to-custom-voice-prepare-data.md) (Vorbereiten von Daten zum Erstellen einer benutzerdefinierten Stimme).

3. [Trainieren Ihres Modells:](how-to-custom-voice-create-voice.md#build-your-custom-voice-model) Erstellen Sie unter Verwendung Ihrer Daten ein benutzerdefiniertes Stimmmodell für die Sprachsynthese. Sie können ein Modell in verschiedenen Sprachen trainieren. Testen Sie Ihr trainiertes Modell. Wenn Sie mit dem Ergebnis zufrieden sind, können Sie das Modell bereitstellen.

4. [Bereitstellen Ihres Modells:](how-to-custom-voice-create-voice.md#create-and-use-a-custom-voice-endpoint) Erstellen Sie einen benutzerdefinierten Endpunkt für Ihr Stimmmodell für die Sprachsynthese, und verwenden sie ihn für die Sprachsynthese in Ihren Produkten, Tools und Anwendungen.

## <a name="custom-neural-voices"></a>Benutzerdefinierte neuronale Stimmen

Custom Voice unterstützt aktuell sowohl neuronale Ebenen als auch Standardebenen. Das Feature „Benutzerdefinierte neuronale Stimme“ ermöglicht es Benutzern, leistungsfähigere Sprachmodelle zu erstellen, für die weniger Daten erforderlich sind. Außerdem werden über das Feature Methoden bereitgestellt, die Sie dabei unterstützen, KI verantwortungsbewusst zu nutzen. Sie sollten das Feature „Benutzerdefinierte neuronale Stimme“ verwenden, um realistischere Stimmen für natürlichere Konversationsschnittstellen zu entwickeln. So können Sie es Ihren Kunden und Endbenutzern ermöglichen, die Vorteile der aktuellen Text-zu-Sprache-Technologie verantwortungsvoll zu nutzen. [Hier](https://aka.ms/CNV-Transparency-Note) erhalten Sie weitere Informationen zum Feature „Benutzerdefinierte neuronale Stimme“. 

> [!NOTE]
> Im Rahmen der Zusage von Microsoft zu einem verantwortungsbewussten Umgang mit KI haben wir die Verwendung des Features „Benutzerdefinierte neuronale Stimme“ beschränkt. Sie erhalten erst Zugriff auf die Technologie, nachdem Ihre Anwendungen überprüft wurden und Sie sich zur Einhaltung der Prinzipien eines verantwortungsbewussten Umgangs mit KI verpflichtet haben. [Hier](https://aka.ms/gating-overview) erhalten Sie weitere Informationen zu unserer Richtlinie zur Zugriffsbeschränkung. [Hier](https://aka.ms/customneural) können Sie den Zugriff anfordern. Die für die Standardversion und die neuronale Version von Custom Voice unterstützten [Sprachen](language-support.md#customization) und [Regionen](regions.md#custom-voices) unterscheiden sich. Überprüfen Sie die Details, bevor Sie loslegen.  

## <a name="set-up-your-azure-account"></a>Einrichten Ihres Azure-Kontos

Sie benötigen ein Abonnement für den Speech-Dienst, um das Custom Speech-Portal zum Erstellen eines benutzerdefinierten Modells verwenden zu können. Befolgen Sie diese Anweisungen, um in Azure ein Abonnement für den Speech-Dienst zu erstellen. Sollten Sie über kein Azure-Konto verfügen, können Sie sich für ein neues Konto registrieren.  

Nachdem Sie ein Azure-Konto und ein Abonnement für den Speech-Dienst erstellt haben, müssen Sie sich beim Custom Voice-Portal anmelden und eine Verbindung mit Ihrem Abonnement herstellen.

1. Rufen Sie über das Azure-Portal Ihren Abonnementschlüssel für die Speech-Dienste ab.
2. Melden Sie sich beim [Custom Voice-Portal](https://aka.ms/custom-voice) an.
3. Wählen Sie Ihr Abonnement aus, und erstellen Sie ein Speech-Projekt.
4. Wenn Sie zu einem anderen Speech-Abonnement wechseln möchten, verwenden Sie das Zahnradsymbol auf der oberen Navigationsleiste.

> [!NOTE]
> Sie müssen über einen in Azure erstellten F0- oder S0-Schlüssel für den Speech-Dienst verfügen, um den Dienst nutzen zu können. Das Feature „Benutzerdefinierte neuronale Stimme“ unterstützt nur die S0-Ebene. 

## <a name="how-to-create-a-project"></a>So erstellen Sie ein Projekt

Inhalte wie Daten, Modelle, Tests und Endpunkte sind im Custom Voice-Portal in **Projekten** organisiert. Jedes Projekt ist spezifisch für ein Land/eine Sprache und das Geschlecht der Stimme, die Sie erstellen möchten. So können Sie beispielsweise ein Projekt mit einer weiblichen Stimme für die Chatbots Ihres Callcenters erstellen, die US-amerikanisches Englisch (en-US) verwenden.

Wählen Sie zum Erstellen Ihres ersten Projekts die Registerkarte **Text-to-Speech/Custom Voice** (Sprachsynthese/Benutzerdefinierte Stimme) aus, und klicken Sie auf **Neues Projekt**. Folgen Sie den Anweisungen des Assistenten, um Ihr Projekt zu erstellen. Nachdem Sie ein Projekt erstellt haben, werden vier Registerkarten angezeigt: **Daten**, **Training**, **Test** und **Bereitstellung**. Verwenden Sie die Links unter [Nächste Schritte](#next-steps), um mehr über die Verwendung der einzelnen Registerkarten zu erfahren.

> [!IMPORTANT]
> Das [Custom Voice-Portal](https://aka.ms/custom-voice) wurde kürzlich aktualisiert! Wenn Sie vorherige Daten, Modelle, Tests und veröffentlichte Endpunkte im CRIS.ai-Portal oder mit APIs erstellt haben, müssen Sie im neuen Portal ein neues Projekt erstellen, um eine Verbindung mit diesen alten Entitäten herzustellen.

## <a name="next-steps"></a>Nächste Schritte

- [Get started with Custom Voice](how-to-custom-voice-prepare-data.md) (Erste Schritte mit Custom Voice)
- [Create a Custom Voice](how-to-custom-voice-create-voice.md) (Erstellen einer benutzerdefinierten Stimme)
- [Aufzeichnen Aufnehmen Ihrer Sprachbeispiele](record-custom-voice-samples.md)
