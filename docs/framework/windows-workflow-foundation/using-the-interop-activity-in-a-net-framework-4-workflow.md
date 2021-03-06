---
title: "Использование действия «Interop» в рабочем процессе платформы .NET Framework 4"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a02d6dbc7c6f6583a174bd10853d8c8070ac273
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a>Использование действия «Interop» в рабочем процессе платформы .NET Framework 4
Действия, созданные в [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] или в [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], могут использоваться в рабочем процессе [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] посредством использования действия <xref:System.Activities.Statements.Interop>. В этом разделе приведены общие сведения об использовании действия <xref:System.Activities.Statements.Interop>.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop> Действия не отображается в области элементов конструктора рабочих процессов, если проект рабочего процесса имеет его **требуемой версии .NET Framework** задано значение **.Net Framework 4** или более поздней версии.  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a>Использование действия Interop в рабочих процессах платформы .NET Framework 4.5  
 В данном разделе создается библиотека действий [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], содержащая действие `DiscountCalculator`. Действие `DiscountCalculator` вычисляет скидку на основе стоимости приобретений и состоит из действия <xref:System.Workflow.Activities.SequenceActivity>, содержащего действие <xref:System.Workflow.Activities.PolicyActivity>.  
  
> [!NOTE]
>  Действие [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], создаваемое в этом разделе, использует действие <xref:System.Workflow.Activities.PolicyActivity> для реализации логики действия. Для использования правил в рабочем процессе [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] не обязательно использовать пользовательское действие <xref:System.Activities.Statements.Interop> или действие [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Пример использования правила в [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] рабочего процесса без использования <xref:System.Activities.Statements.Interop> действия, в разделе [действие политики в .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) образца.  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a>Создание проекта библиотеки действий платформы .NET Framework 3.5  
  
1.  Откройте [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] и выберите **New** и затем **проекта...** из **файл** меню.  
  
2.  Разверните **другие типы проектов** узел в **установленные шаблоны** области и выберите команду **решения Visual Studio**.  
  
3.  Выберите **пустое решение** из **решения Visual Studio** списка. Тип `PolicyInteropDemo` в **имя** и нажмите кнопку **ОК**.  
  
4.  Щелкните правой кнопкой мыши **PolicyInteropDemo** в **обозревателе решений** и выберите **добавить** и затем **новый проект...** .  
  
    > [!TIP]
    >  Если **обозревателе решений** окно не отображается, выберите пункт **обозревателе решений** из **представление** меню.  
  
5.  В **установленные шаблоны** выберите **Visual C#** и затем **рабочего процесса**. Выберите **.NET Framework 3.5** в раскрывающемся списке версий .NET Framework, а затем выберите **библиотека действий рабочих процессов** из **шаблоны** списка.  
  
6.  Тип `PolicyActivityLibrary` в **имя** и нажмите кнопку **ОК**.  
  
7.  Щелкните правой кнопкой мыши **Activity1.cs** в **обозревателе решений** и выберите **удалить**. Нажмите кнопку **ОК** для подтверждения.  
  
#### <a name="to-create-the-discountcalculator-activity"></a>Создание действия DiscountCalculator  
  
1.  Щелкните правой кнопкой мыши **PolicyActivityLibrary** в **обозревателе решений** и выберите **добавить** и затем **действия...** .  
  
2.  Выберите **действие (с разделением кода)** из **элементы Visual C#** списка. Тип `DiscountCalculator` в **имя** и нажмите кнопку **ОК**.  
  
3.  Щелкните правой кнопкой мыши **DiscountCalculator.xoml** в **обозревателе решений** и выберите **Просмотр кода**.  
  
4.  Добавьте в класс `DiscountCalculator` приведенные ниже три свойства.  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  Щелкните правой кнопкой мыши **DiscountCalculator.xoml** в **обозревателе решений** и выберите **конструктор представлений**.  
  
6.  Перетащите **политики** действия из **Windows Workflow v3.0** раздел **элементов** и поместите его **DiscountCalculator** действия .  
  
    > [!TIP]
    >  Если **элементов** окно не отображается, выберите пункт **элементов** из **представление** меню.  
  
#### <a name="to-configure-the-rules"></a>Настройка правил  
  
1.  Щелкните только что добавленном **политики** действия, чтобы выбрать его, если он еще не выбран.  
  
2.  Нажмите кнопку **RuleSetReference** свойство в **свойства** окно, чтобы выбрать ее и нажмите кнопку с многоточием справа от свойства.  
  
    > [!TIP]
    >  Если **свойства** окно не отображается, выберите **окно свойств** из **представление** меню.  
  
3.  Выберите **щелкните Добавить...** .  
  
4.  Нажмите кнопку **добавить правило**.  
  
5.  Введите следующее выражение в **условие** поле.  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  Введите следующее выражение в **действия Then** поле.  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  Нажмите кнопку **добавить правило**.  
  
8.  Введите следующее выражение в **условие** поле.  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. Введите следующее выражение в **действия Then** поле.  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. Нажмите кнопку **добавить правило**.  
  
11. Введите следующее выражение в **условие** поле.  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. Введите следующее выражение в **действия Then** поле.  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. Введите следующее выражение в **действия Else** поле.  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. Нажмите кнопку **ОК** закрыть **редактор набора правил** диалоговое окно.  
  
15. Убедитесь, что вновь созданные <xref:System.Workflow.Activities.Rules.RuleSet> выбран в **имя** списке и нажмите кнопку **ОК**.  
  
16. Чтобы построить решение, нажмите CTRL+SHIFT+B.  
  
 Правила, добавленные в действие `DiscountCalculator` в ходе выполнения этой процедуры, показаны в следующем примере кода.  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 При выполнении действия <xref:System.Workflow.Activities.PolicyActivity> выполняется оценка этих трех правил, которые соответственно изменяют значения свойств `Subtotal`, `DiscountPercent` и `Total` для действия `DiscountCalculator` с целью вычисления требуемой скидки.  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a>Использование действия DiscountCalculator совместно с действием Interop  
 Чтобы использовать действие `DiscountCalculator` в рабочем процессе [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], используется действие <xref:System.Activities.Statements.Interop>. В данном разделе создаются два рабочих процесса (один с использованием кода и один с помощью конструктора рабочего процесса), которые демонстрируют использование действия <xref:System.Activities.Statements.Interop> совместно с действием `DiscountCalculator`. Для обоих рабочих процессов используется одно ведущее приложение.  
  
#### <a name="to-create-the-host-application"></a>Создание ведущего приложения  
  
1.  Щелкните правой кнопкой мыши **PolicyInteropDemo** в **обозревателе решений** и выберите **добавить**, а затем **новый проект...** .  
  
2.  Убедитесь, что **.NET Framework 4.5** выбран в раскрывающемся списке версий .NET Framework и выберите **консольное приложение рабочего процесса** из **элементы Visual C#** списка.  
  
3.  Тип `PolicyInteropHost` в **имя** и нажмите кнопку **ОК**.  
  
4.  Щелкните правой кнопкой мыши **PolicyInteropHost** в **обозревателе решений** и выберите **свойства**.  
  
5.  В **требуемой версии .NET framework** раскрывающемся списке, измените выбранный вариант с **клиентский профиль .NET Framework 4** для **.NET Framework 4.5**. Нажмите кнопку **Да** для подтверждения.  
  
6.  Щелкните правой кнопкой мыши **PolicyInteropHost** в **обозревателе решений** и выберите **добавить ссылку...** .  
  
7.  Выберите **PolicyActivityLibrary** из **проекты** и нажмите кнопку **ОК**.  
  
8.  Щелкните правой кнопкой мыши **PolicyInteropHost** в **обозревателе решений** и выберите **добавить ссылку...** .  
  
9. Выберите **System.Workflow.Activities**, **System.Workflow.ComponentModel**, а затем **System.Workflow.Runtime** из **.NET**и нажмите кнопку **ОК**.  
  
10. Щелкните правой кнопкой мыши **PolicyInteropHost** в **обозревателе решений** и выберите **Назначить запускаемым проектом**.  
  
11. Чтобы построить решение, нажмите CTRL+SHIFT+B.  
  
### <a name="using-the-interop-activity-in-code"></a>Использование действия Interop в коде  
 В данном примере определение рабочего процесса создается с использованием кода, содержащего действия <xref:System.Activities.Statements.Interop> и `DiscountCalculator`. Этот рабочий процесс вызывается с помощью <xref:System.Activities.WorkflowInvoker>, а результаты оценки правила записываются в консоль с использованием действия <xref:System.Activities.Statements.WriteLine>.  
  
##### <a name="to-use-the-interop-activity-in-code"></a>Использование действия Interop в коде  
  
1.  Щелкните правой кнопкой мыши **Program.cs** в **обозревателе решений** и выберите **Просмотр кода**.  
  
2.  Добавьте следующую инструкцию`using` в начало файла.  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  Удалите содержимое метода `Main` и замените его следующим кодом.  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  Создайте новый метод в классе `Program` с именем `CalculateDiscountUsingCodeWorkflow`, который содержит следующий код.  
  
    ```csharp  
    static void CalculateDiscountUsingCodeWorkflow()  
    {  
        Variable<double> Subtotal = new Variable<double>  
        {  
            Default = 75.99,  
            Name = "Subtotal"  
        };  
  
        Variable<double> DiscountPercent = new Variable<double>  
        {  
            Name = "DiscountPercent"  
        };  
  
        Variable<double> Total = new Variable<double>  
        {  
            Name = "Total"  
        };  
  
        Activity wf = new Sequence  
        {  
            Variables = { Subtotal, DiscountPercent, Total },  
            Activities =   
            {  
                new Interop  
                {  
                    ActivityType = typeof(DiscountCalculator),  
                    ActivityProperties =   
                    {  
                        { "Subtotal", new InArgument<double>(Subtotal) },  
                        { "DiscountPercentOut", new OutArgument<double>(DiscountPercent) },  
                        { "TotalOut", new OutArgument<double>(Total) }  
                    }  
                },  
                new WriteLine  
                {  
                    Text =  new InArgument<string>(env =>   
                        string.Format("Subtotal: {0:C}, Discount {1}%, Total {2:C}",   
                        Subtotal.Get(env), DiscountPercent.Get(env) * 100, Total.Get(env)))  
                }  
            }  
        };  
  
        WorkflowInvoker.Invoke(wf);  
    }  
    ```  
  
    > [!NOTE]
    >  Свойства `Subtotal`, `DiscountPercent` и `Total` действия `DiscountCalculator` отображаются как аргументы действия <xref:System.Activities.Statements.Interop>, привязанные к переменным локального рабочего процесса в коллекции <xref:System.Activities.Statements.Interop> действия <xref:System.Activities.Statements.Interop.ActivityProperties%2A>. `Subtotal` добавляется как аргумент <xref:System.Activities.ArgumentDirection.In>, поскольку данные `Subtotal` направляются действию <xref:System.Activities.Statements.Interop>, а `DiscountPercent` и `Total` добавляются как аргументы <xref:System.Activities.ArgumentDirection.Out>, так как их потоки данных происходят из действия <xref:System.Activities.Statements.Interop>. Следует заметить, что аргументы <xref:System.Activities.ArgumentDirection.Out> добавляются с именами `DiscountPercentOut` и `TotalOut` чтобы показать, что они представляют аргументы с направлением <xref:System.Activities.ArgumentDirection.Out>. Тип `DiscountCalculator` указан как тип <xref:System.Activities.Statements.Interop> действия <xref:System.Activities.Statements.Interop.ActivityType%2A>.  
  
5.  Нажмите клавиши CTRL+F5 для сборки и запуска приложения. Подставляя различные значения в качестве значения `Subtotal`, можно проверить различные уровни скидок, реализуемые действием `DiscountCalculator`.  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a>Использование действия Interop в конструкторе рабочих процессов  
 В данном примере рабочий процесс создается с использованием конструктора рабочих процессов. Рабочий процесс выполняет те же функции, что и предыдущий пример, за одним исключением: вместо использования действия <xref:System.Activities.Statements.WriteLine> для отображения скидки ведущее приложение получает и отображает сведения о скидке при завершении рабочего процесса. Также локальные переменные рабочего процесса не используются для хранения данных. Вместо этого аргументы создаются в конструкторе рабочих процессов, а значения передаются из ведущего приложения при вызове рабочего процесса.  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a>Размещение PolicyActivity с использованием рабочего процесса, созданного в конструкторе рабочих процессов  
  
1.  Щелкните правой кнопкой мыши **Workflow1.xaml** в **обозревателе решений** и выберите **удалить**. Нажмите кнопку **ОК** для подтверждения.  
  
2.  Щелкните правой кнопкой мыши **PolicyInteropHost** в **обозревателе решений** и выберите **добавить**, **новый элемент...** .  
  
3.  Разверните **элементы Visual C#** , а затем выберите **рабочего процесса**. Выберите **действия** из **элементы Visual C#** списка.  
  
4.  Тип `DiscountWorkflow` в **имя** и нажмите кнопку **добавить**.  
  
5.  Нажмите кнопку **аргументы** кнопки в нижнем левом углу конструктора рабочих процессов для отображения **аргументы** области.  
  
6.  Нажмите кнопку **создать аргумент**.  
  
7.  Тип `Subtotal` в **имя** выберите **в** из **направление** раскрывающийся список, выберите **двойные** из **Тип аргумента** раскрывающегося списка, а затем нажмите клавишу ВВОД, чтобы сохранить аргумент.  
  
    > [!NOTE]
    >  Если **двойные** не находится в **тип аргумента** раскрывающемся списке выберите **поиск типов...** , тип `System.Double` в **имя типа** и нажмите кнопку **ОК**.  
  
8.  Нажмите кнопку **создать аргумент**.  
  
9. Тип `DiscountPercent` в **имя** выберите **Out** из **направление** раскрывающийся список, выберите **двойные** из **Тип аргумента** раскрывающегося списка, а затем нажмите клавишу ВВОД, чтобы сохранить аргумент.  
  
10. Нажмите кнопку **создать аргумент**.  
  
11. Тип `Total` в **имя** выберите **Out** из **направление** раскрывающийся список, выберите **двойные** из **Тип аргумента** раскрывающегося списка, а затем нажмите клавишу ВВОД, чтобы сохранить аргумент.  
  
12. Нажмите кнопку **аргументы** кнопки в нижнем левом углу конструктора рабочих процессов, чтобы закрыть **аргументы** области.  
  
13. Перетащите **последовательности** действия из **поток управления** раздел **элементов** и поместите его на поверхность конструктора рабочих процессов.  
  
14. Перетащите **взаимодействия** действия из **миграции** раздел **элементов** и поместите его **последовательности** действия.  
  
15. Нажмите кнопку **взаимодействия** действия на **нажмите, чтобы просмотреть...** Метка, введите **DiscountCalculator** в **имя типа** и нажмите кнопку **ОК**.  
  
    > [!NOTE]
    >  Если действие <xref:System.Activities.Statements.Interop> добавляется в рабочий процесс, а тип `DiscountCalculator` указан в качестве типа <xref:System.Activities.Statements.Interop.ActivityType%2A>, то действие <xref:System.Activities.Statements.Interop> предоставит три аргумента <xref:System.Activities.ArgumentDirection.In> и три аргумента <xref:System.Activities.ArgumentDirection.Out>, представляющие три открытых свойства действия `DiscountCalculator`. <xref:System.Activities.ArgumentDirection.In> Аргументы имеют имя, совпадающее с именем и три открытых свойства, а также три <xref:System.Activities.ArgumentDirection.Out> аргументы имеют те же имена с **Out** добавляется к имени свойства. В ходе последующих шагов аргументы рабочего процесса, созданные ранее, привязываются к аргументам действия <xref:System.Activities.Statements.Interop>.  
  
16. Тип `DiscountPercent` в **введите выражение VB** поле справа от **DiscountPercentOut** свойство и нажмите клавишу TAB.  
  
17. Тип `Subtotal` в **введите выражение VB** поле справа от **Subtotal** свойство и нажмите клавишу TAB.  
  
18. Тип `Total` в **введите выражение VB** поле справа от **TotalOut** свойство и нажмите клавишу TAB.  
  
19. Щелкните правой кнопкой мыши **Program.cs** в **обозревателе решений** и выберите **Просмотр кода**.  
  
20. Добавьте следующую инструкцию`using` в начало файла.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. Закомментируйте вызов метода `CalculateDiscountInCode` в методе `Main` и добавьте следующий код.  
  
    > [!NOTE]
    >  Если предыдущая процедура не была выполнена и код `Main` по умолчанию все еще присутствует, замените содержимое метода `Main` следующим кодом.  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. Создайте новый метод в классе `Program` с именем `CalculateDiscountUsingDesignerWorkflow`, который содержит следующий код.  
  
    ```csharp  
    static void CalculateDiscountUsingDesignerWorkflow()  
    {  
        double SubtotalValue = 125.99;  
        Dictionary<string, object> wfargs = new Dictionary<string, object>  
        {  
            {"Subtotal", SubtotalValue}  
        };  
  
        Activity wf = new DiscountWorkflow();  
  
        IDictionary<string, object> outputs =  
            WorkflowInvoker.Invoke(wf, wfargs);  
  
        Console.WriteLine("Subtotal: {0:C}, Discount {1}%, Total {2:C}",  
            SubtotalValue, (double)outputs["DiscountPercent"] * 100,  
            outputs["Total"]);  
    }  
    ```  
  
23. Нажмите клавиши CTRL+F5 для сборки и запуска приложения. Чтобы задать другую сумму `Subtotal`, измените значение `SubtotalValue` в следующем коде.  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a>Общие сведения об особенностях правил  
 Обработчик правил [!INCLUDE[wf1](../../../includes/wf1-md.md)] обеспечивает поддержку обработки правил с учетом приоритетов и поддержкой прямых логических цепочек. Оценка правил может проводиться для одного элемента или для элементов коллекции. Общие сведения о правилах, а также сведения о функциональных возможностях отдельных правил см. в следующей таблице.  
  
|Возможность правил|Документация|  
|-------------------|-------------------|  
|Общие сведения о правилах|[Введение в обработчик правил Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=152836)|  
|RuleSet|[Использование наборов правил в рабочих процессах](http://go.microsoft.com/fwlink/?LinkId=178516) и<xref:System.Workflow.Activities.Rules.RuleSet>|  
|Оценка правил|[Вычисление правил в наборы правил](http://go.microsoft.com/fwlink/?LinkId=178517)|  
|Цепочки правил|[Прямой цепочки управления](http://go.microsoft.com/fwlink/?LinkId=178518) и [прямые логические цепочки правил](http://go.microsoft.com/fwlink/?LinkId=178519)|  
|Обработка коллекций в правилах|[Обработка коллекций в правилах](http://go.microsoft.com/fwlink/?LinkId=178520)|  
|Использование действия PolicyActivity|[Использование действия PolicyActivity](http://go.microsoft.com/fwlink/?LinkId=178521) и<xref:System.Workflow.Activities.PolicyActivity>|  
  
 Рабочие процессы, созданные в [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], используют не все предоставляемые в [!INCLUDE[wf1](../../../includes/wf1-md.md)] возможности правил, например они не реализуют декларативные условия действий и условные действия, такие как <xref:System.Workflow.Activities.ConditionedActivityGroup> и <xref:System.Workflow.Activities.ReplicatorActivity>. При необходимости можно воспользоваться этими функциональными возможностями в рабочих процессах, созданных с помощью [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] и [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Руководство по миграции](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).
