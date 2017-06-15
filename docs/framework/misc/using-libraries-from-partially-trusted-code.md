---
title: "Using Libraries from Partially Trusted Code | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "security [.NET Framework], partially trusted code"
  - "partially trusted code"
  - "partial trust"
  - "AllowPartiallyTrustedCallersAttribute attribute"
  - "code access security, partially trusted code"
  - "APTCA"
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
caps.latest.revision: 25
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 23
---
# Using Libraries from Partially Trusted Code
> [!NOTE]
>  Этот раздел описывает поведение сборок со строгими именами и применяется только к сборкам [уровня 1](../../../docs/framework/misc/security-transparent-code-level-1.md). Сборки [Security\-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) в [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] или более поздних версий не зависят от строгих имен. Дополнительные сведения об изменениях системы безопасности см. в разделе [Изменения системы безопасности](../../../docs/framework/security/security-changes.md).  
  
> [!CAUTION]
>  Управление доступом для кода и частично доверенный код  
>   
>  Платформа .NET Framework предоставляет механизм для принудительного применения различных уровней доверия к разным частям кода, выполняемым в одном и том же приложении. Этот механизм называется управлением доступом для кода.  Управление доступом для кода в .NET Framework не следует использовать в качестве средства безопасности при работе с частично доверенным кодом, особенно кодом неизвестного происхождения. Мы не рекомендуем загружать и выполнять код из неизвестных источников, не предприняв дополнительные меры безопасности.  
>   
>  Эта политика действует в отношении всех версий платформы .NET Framework, кроме платформы .NET Framework в составе Silverlight.  
  
 Приложения, которые не получают полное доверие со стороны узла или песочницы, не могут вызывать общие управляемые библиотеки, если только автор библиотеки не разрешил это специально при помощи атрибута <xref:System.Security.AllowPartiallyTrustedCallersAttribute>. Таким образом, авторы приложений должны иметь в виду, что некоторые библиотеки будут им недоступны в контексте частичного доверия. По умолчанию весь код, выполняемый в частично доверенной [песочнице](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) и не входящий в список сборок с полным доверием, имеет частичное доверие. Если не предполагается, что код будет запускаться в частично доверенном контексте или вызываться кодом с частичным доверием, данный раздел можно игнорировать. Однако при написании кода, который должен взаимодействовать с частично доверенным кодом или работать из частично доверенного контекста, следует учитывать следующие факторы.  
  
-   Библиотеки должны быть подписаны строгим именем, чтобы их могли совместно использовать несколько приложений. Строгие имена позволяют помещать код в глобальный кэш сборок или добавлять его в список полного доверия песочницы <xref:System.AppDomain>, а также позволяют потребителям удостовериться, что данный фрагмент мобильного кода действительно исходит от вас.  
  
-   По умолчанию общие библиотеки [уровня 1](../../../docs/framework/misc/security-transparent-code-level-1.md) со строгими именами выполняют неявную операцию [LinkDemand](../../../docs/framework/misc/link-demands.md) для полного доверия автоматически, не требуя от автора библиотеки никаких действий.  
  
-   Если вызывающий объект не имеет полного доверия, однако пытается вызывать такую библиотеку, среда выполнения создает <xref:System.Security.SecurityException>, а вызывающему объекту запрещается связь с библиотекой.  
  
-   Чтобы отключить автоматическое выполнение операции **LinkDemand** и предотвратить возникновение исключения, можно поместить атрибут **AllowPartiallyTrustedCallersAttribute** в область действия сборки общей библиотеки. Этот атрибут позволяет вызывать библиотеки из частично доверенного управляемого кода.  
  
-   На частично доверенный код, получающий доступ к библиотеке при помощи этого атрибута, по\-прежнему налагаются дополнительные ограничения, определяемые <xref:System.AppDomain>.  
  
-   Не существует программного способа обеспечить вызов частично доверенным кодом библиотеки, которая не имеет атрибута **AllowPartiallyTrustedCallersAttribute**.  
  
 Библиотеки, являющиеся собственными для определенного приложения, не требуют строгого имени или атрибута **AllowPartiallyTrustedCallersAttribute**, а также на них не может ссылаться потенциально вредоносный код извне приложения. Такой код защищен от преднамеренного или непреднамеренного неправильного использования со стороны мобильного кода с частичным доверием, и никаких дополнительных действий со стороны разработчика не требуется.  
  
 Рекомендуется явно разрешить использование частично доверенным кодом для следующих типов кода.  
  
-   Код, который был тщательно протестирован на наличие уязвимостей безопасности и соответствует рекомендациям, приведенным в разделе [Правила написания безопасного кода](../../../docs/standard/security/secure-coding-guidelines.md).  
  
-   Строго именованные библиотеки кода, специально написанные для частично доверенных сценариев.  
  
-   Все компоненты \(с частичным или полным доверием\), подписанные строгим именем, которые будут вызываться кодом, скачанным из Интернета.  
  
> [!NOTE]
>  Некоторые классы в библиотеке классов платформы .NET Framework не имеют атрибута **AllowPartiallyTrustedCallersAttribute** и не могут вызываться кодом с частичным доверием.  
  
## См. также  
 [Code Access Security](../../../docs/framework/misc/code-access-security.md)