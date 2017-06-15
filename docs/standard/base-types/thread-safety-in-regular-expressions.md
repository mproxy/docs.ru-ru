---
title: "Потокобезопасность в регулярных выражениях | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "регулярные выражения .NET Framework, потоки"
  - "разбор текста с регулярными выражениями, потоки"
  - "синтаксис соответствия шаблону с регулярными выражениями, потоки"
  - "регулярные выражения, потоки"
  - "поиск с регулярными выражениями, потоки"
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Потокобезопасность в регулярных выражениях
Сам по себе класс <xref:System.Text.RegularExpressions.Regex> является потокобезопасным и неизменяемым \(предназначенным только для чтения\).  Это означает, что объекты **Regex** могут создаваться в любом потоке и совместно использоваться несколькими потоками; одни и те же методы могут вызываться из любого потока, никак не изменяя при этом глобальное состояние.  
  
 Тем не менее, объекты с результатами \(**Match** и **MatchCollection**\), возвращаемые **Regex**, следует использовать только в одном потоке.  Несмотря на то что по своей логике многие из этих объектов неизменяемы, их реализации способны задерживать вычисление некоторых результатов для повышения эффективности работы, поэтому в итоге вызывающим объектам приходится сериализовывать доступ к ним.  
  
 Если доступ к объектам с результатами **Regex** необходимо предоставить нескольким потокам, то эти объекты можно преобразовать в потокобезопасные, вызвав их синхронизированные методы.  Все классы регулярных выражений, за исключением перечислителей, являются потокобезопасными или же могут быть преобразованы в потокобезопасные объекты с помощью синхронизированных методов.  
  
 Перечислители являются единственным исключением из этого правила.  Вызовы, обращенные к перечислителям коллекций, в приложениях должны быть сериализованы.  Общее правило здесь состоит в том, что если существует возможность одновременной работы перечислителей из нескольких потоков с одной коллекцией, то их методы необходимо синхронизировать в корневом объекте коллекции, по которой проходит перечислитель.  
  
## См. также  
 [Регулярные выражения в .NET Framework](../../../docs/standard/base-types/regular-expressions.md)