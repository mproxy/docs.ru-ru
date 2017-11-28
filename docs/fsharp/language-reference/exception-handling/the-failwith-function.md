---
title: "Исключения. Функция failwith (F#)"
description: "Узнайте, как функция «failwith» приводит к возникновению исключения F #."
keywords: "visual f#, f#, функциональное программирование"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2e0c1f28-cc6c-4ecd-bb93-3816c4dd7cd3
ms.openlocfilehash: 295a4d754e0df015ba67daa9cf80d7df5b40199c
ms.sourcegitcommit: ffb9aa26cd5211dc6d96ebb42968d8357048880e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="exceptions-the-failwith-function"></a><span data-ttu-id="3208b-104">Исключения. Функция failwith</span><span class="sxs-lookup"><span data-stu-id="3208b-104">Exceptions: The failwith Function</span></span>

<span data-ttu-id="3208b-105">`failwith` Функция создает исключение F #.</span><span class="sxs-lookup"><span data-stu-id="3208b-105">The `failwith` function generates an F# exception.</span></span>


## <a name="syntax"></a><span data-ttu-id="3208b-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3208b-106">Syntax</span></span>

```fsharp
failwith error-message-string
```

## <a name="remarks"></a><span data-ttu-id="3208b-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="3208b-107">Remarks</span></span>
<span data-ttu-id="3208b-108">*Строка сообщения об* в предыдущем синтаксисе является строковым литералом или значением типа `string`.</span><span class="sxs-lookup"><span data-stu-id="3208b-108">The *error-message-string* in the previous syntax is a literal string or a value of type `string`.</span></span> <span data-ttu-id="3208b-109">Оно становится `Message` свойства исключения.</span><span class="sxs-lookup"><span data-stu-id="3208b-109">It becomes the `Message` property of the exception.</span></span>

<span data-ttu-id="3208b-110">Исключение, создаваемое `failwith` — `System.Exception` исключение, которое является ссылкой с именем `Failure` в коде F #.</span><span class="sxs-lookup"><span data-stu-id="3208b-110">The exception that is generated by `failwith` is a `System.Exception` exception, which is a reference that has the name `Failure` in F# code.</span></span> <span data-ttu-id="3208b-111">Следующий код иллюстрирует использование `failwith` создаст исключение.</span><span class="sxs-lookup"><span data-stu-id="3208b-111">The following code illustrates the use of `failwith` to throw an exception.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]
    
## <a name="see-also"></a><span data-ttu-id="3208b-112">См. также</span><span class="sxs-lookup"><span data-stu-id="3208b-112">See Also</span></span>
[<span data-ttu-id="3208b-113">Обработка исключений</span><span class="sxs-lookup"><span data-stu-id="3208b-113">Exception Handling</span></span>](index.md)

[<span data-ttu-id="3208b-114">Типы исключения</span><span class="sxs-lookup"><span data-stu-id="3208b-114">Exception Types</span></span>](exception-types.md)

[<span data-ttu-id="3208b-115">Исключения: выражение `try...with`</span><span class="sxs-lookup"><span data-stu-id="3208b-115">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)

[<span data-ttu-id="3208b-116">Исключения: выражение `try...finally`</span><span class="sxs-lookup"><span data-stu-id="3208b-116">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)

[<span data-ttu-id="3208b-117">Исключения: функция `raise`</span><span class="sxs-lookup"><span data-stu-id="3208b-117">Exceptions: the `raise` Function</span></span>](the-raise-function.md)