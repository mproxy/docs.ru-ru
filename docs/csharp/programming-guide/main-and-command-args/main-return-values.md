---
title: "Значения, возвращаемые методом Main() (Руководство по программированию на C#)"
ms.date: 08/02/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f317879a4941adfd3d125c7697226f8a510254c
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="main-return-values-c-programming-guide"></a>Значения, возвращаемые методом Main() (Руководство по программированию на C#)

Метод `Main` может возвращать значение `void`:

[!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]

Он также может возвращать значение типа `int`:

[!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]

Если значение, возвращаемое методом `Main`, не используется, то указание в качестве возвращаемого типа `void` несколько упрощает код. Однако возврат целого значения позволяет программе передавать информацию о своем состоянии другим программам и скриптам, которые вызывают исполняемый файл. Возвращаемое значение `Main` рассматривается как код выхода процесса. В приведенном ниже примере показано, как получить доступ к значению, возвращаемому методом `Main`.

## <a name="example"></a>Пример

В этом примере используются средства командной строки [.NET Core](../../../core/index.md). Если вы не знакомы со средствами командной строки .NET Core, можете обратиться к [этому руководству по началу работы](../../../core/tutorials/using-with-xplat-cli.md).

Измените метод `Main` в файле *program.cs* следующим образом:

[!code-csharp[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]

При запуске программы в Windows значение, возвращаемое функцией `Main`, сохраняется в переменной среды. Эту переменную можно получить из пакетного файла с помощью команды `ERRORLEVEL` или в PowerShell с помощью команды `$LastExitCode`.

Для сборки приложения можно выполнить команду `dotnet build` [интерфейса командной строки .NET](../../../core/tools/dotnet.md).

Затем создайте сценарий PowerShell для запуска приложения и отображения результата. Вставьте следующий код в текстовый файл и сохраните его под именем `test.ps1` в папке проекта. Запустите сценарий PowerShell, набрав команду `test.ps1` в командной строке PowerShell.

Так как код возвращает нулевое значение, пакетный файл сообщает об успехе. Но если изменить файл MainReturnValTest.cs, чтобы он возвращал ненулевое значение, и затем повторно скомпилировать программу, то при последующем выполнении сценария PowerShell будет выдано сообщение об ошибке.

```powershell
dotnet run
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a>Пример полученных результатов

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a>Значения, возвращаемые асинхронным методом main

Возвращаемые значения асинхронного метода main перемещают стандартный код, необходимый для вызова асинхронных методов в `Main`, в код, созданный компилятором. Ранее для вызова асинхронного кода и для запуска программы до завершения асинхронной операции приходилось использовать следующую конструкцию:

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

Теперь ее можно заменить на:

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

Преимущество нового синтаксиса состоит в том, что компилятор всегда формирует правильный код.

## <a name="compiler-generated-code"></a>Код, созданный компилятором

Если точка входа приложения возвращает `Task` или `Task<int>`, то компилятор создает новую точку входа, которая вызывает метод точки входа, объявленный в коде приложения. Предположим, что эта точка входа называется `$GeneratedMain`. В этом случае компилятор создает следующий код для этих точек входа:

- `static Task Main()` приводит к тому, что компилятор формирует эквивалент `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])` приводит к тому, что компилятор формирует эквивалент `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()` приводит к тому, что компилятор формирует эквивалент `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])` приводит к тому, что компилятор формирует эквивалент `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Если бы в примерах использовался модификатор `async` метода `Main`, компилятор сформировал бы точно такой же код.

## <a name="see-also"></a>См. также
[Руководство по программированию на C#](../../programming-guide/index.md)
[Справочник по C#](../index.md)
[Main() и аргументы командной строки](index.md)
[Руководство: отображение аргументов командной строки](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
[Руководство: доступ к аргументам командной строки с помощью foreach](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
