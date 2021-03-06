---
title: 'Schnellstart: Beitreten zu einer Teams-Besprechung'
author: askaur
ms.author: askaur
ms.date: 12/08/2020
ms.topic: quickstart
ms.service: azure-communication-services
ms.openlocfilehash: 0c41771af81989ff965098a762338216db54fd27
ms.sourcegitcommit: 77ab078e255034bd1a8db499eec6fe9b093a8e4f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/16/2020
ms.locfileid: "97578014"
---
## <a name="join-the-meeting-chat"></a>Beitreten zum Besprechungschat 

Sobald die Teams-Interoperabilität aktiviert ist, kann ein Communication Services-Benutzer der Teams-Anrufkonferenz als Gastbenutzer mithilfe der aufrufenden Clientbibliothek beitreten. Durch das Beitreten zur Anrufkonferenz wird er dem Besprechungschat als Teilnehmer hinzugefügt und kann Nachrichten mit anderen Benutzern der Anrufkonferenz austauschen. Der Benutzer besitzt keinen Zugriff auf Chatnachrichten, die gesendet wurden, bevor er der Anrufkonferenz beigetreten ist. 

## <a name="get-a-teams-meeting-chat-thread-for-a-communication-services-user"></a>Abrufen eines Teams-Besprechungschatthreads für einen Communication Services-Benutzer

Instanziieren Sie zunächst einen `ChatThreadClient` für den Besprechungschatthread. Analysieren Sie den Besprechungslink, oder verwenden Sie die Graph-APIs mit der Besprechungs-ID, um die Thread-ID abzurufen. 

- Ein Teams-Besprechungslink sieht wie folgt aus: `https://teams.microsoft.com/l/meetup-join/meeting_chat_thread_id/1606337455313?context=some_context_here`. In der Thread-ID befindet sich `meeting_chat_thread_id` in diesem Link. 
- Wenn Sie über die Besprechungs-ID verfügen, können Sie die [Graph-API](https://docs.microsoft.com/graph/api/onlinemeeting-createorget?tabs=http&view=graph-rest-beta) verwenden, um die Thread-ID abzurufen. Die [GET API](https://docs.microsoft.com/graph/api/onlinemeeting-get?view=graph-rest-beta&tabs=http%22%20%5C)-Antwort enthält ein `chatInfo`-Objekt, das die `threadID` enthält. 

Sobald Sie über die Thread-ID des Chats verfügen, können Sie den Chatthreadclient mithilfe der JavaScript-Chatclientbibliothek abrufen: 

```javascript
let chatThreadClient = await chatClient.getChatThreadClient(threadId); 

console.log(`Chat Thread client for threadId:${chatThreadClient.threadId}`); 
```
  
Der `chatThreadClient` kann verwendet werden, um Mitglieder im Chatthread aufzulisten, den Chatverlauf abzurufen und Nachrichten zu senden.  

## <a name="send-and-receive-messages"></a>Senden und Empfangen von Nachrichten  

Verwenden Sie `SendMessage`, um eine Nachricht an den Besprechungschat zu senden. Zum Empfangen eingehender Nachrichten wird die Möglichkeit zum Abonnieren von Ereignissen wie `chatMessageReceived` nicht unterstützt, weil Echtzeitsignale für dieses Szenario noch nicht aktiviert sind. Um die neuesten Nachrichten abzurufen, können Sie die `ListMessages`-API abfragen. Für das Interoperabilitätsszenario unterstützt die `ListMessages`-API jetzt die Rückgabe von drei neuen Nachrichtentypen:
- `RichText/HTML`
- `ThreadActivity/MemberJoined`
- `ThreadActivity/MemberLeft` </br>

Weitere Informationen zu Nachrichtentypen finden Sie [hier](../../../concepts/chat/concepts.md). 

**Hinweis**: Derzeit wird nur das Senden und Empfangen von Nachrichten für Interoperabilitätsszenarien mit Teams unterstützt. Andere Features wie das Eingeben von Indikatoren oder das Hinzufügen oder Entfernen anderer Benutzer aus der Teams-Besprechung durch Communication Services-Benutzer werden noch nicht unterstützt.  

 
