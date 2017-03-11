---
title: "Автоматически реализуемые свойства (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.AutoProperty"
  - "vb.AutoImplementedProperty"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "автоматически реализуемые свойства [Visual Basic]"
  - "свойства [Visual Basic], автоматически реализуемые"
  - "свойства, автоматически реализуемые [Visual Basic]"
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Автоматически реализуемые свойства (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

*Автоматически реализуемые свойства* позволяют быстро задать свойство класса без написания кода для свойств `Get` и `Set`.  При написании кода для автоматически реализуемого свойства компилятор Visual Basic автоматически создает закрытое поле для хранения переменной свойства, в дополнение к созданию связанных процедур `Get` и `Set`.  
  
 С помощью автоматически реализуемых свойств вы сможете объявлять свойства, включая значение по умолчанию, в одной строке.  В следующем примере показано три объявления свойства.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/auto-implemented-propert_1_1.vb)]  
  
 Автоматически реализуемые свойства эквивалентны свойствам, значения которых хранятся в закрытом поле.  В следующем примере кода показано автоматически реализуемое свойство.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/auto-implemented-propert_1_2.vb)]  
  
 В следующем примере кода показан эквивалентный код для предыдущего примера автоматически реализуемого свойства.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/auto-implemented-propert_1_3.vb)]  
  
 В следующем примере кода показана реализация свойств только для чтения:  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
  
```  
  
 Вы можете назначить свойству выражения инициализации, как показано в примере, или можно присвоить значения свойствам в конструкторе этого типа.  Резервные поля свойств только для чтения можно назначить в любое время.  
  
## Резервное поле  
 При объявлении автоматически реализуемого свойства Visual Basic автоматически создает скрытое закрытое поле с именем *Резервное поле* для хранения значения свойства.  Имя резервного поля — это имя автоматически реализуемого свойства, с добавленным в начало знаком подчеркивания \(\_\).  Например, при объявлении автоматически реализуемого свойства с именем `ID` именем резервного поля будет `_ID`.  Если добавить элемент класса также с именем `_ID`, возникнет конфликт имен, и Visual Basic сообщает об ошибке компилятора.  
  
 Резервное поле также имеет следующие характеристики:  
  
-   модификатор доступа для резервного поля — всегда `Private`, даже если само свойство имеет другой уровень доступа, например `Public`;  
  
-   если свойство помечено как `Shared`, резервное поле также будет общим;  
  
-   атрибуты, указанные для свойства, не применяются к резервному полю;  
  
-   доступ к резервному полю можно получить из кода внутри класса и из средств отладки, например окна контрольных значений.  Однако резервное поле не отображается в списке предложений IntelliSense.  
  
## Инициализация автоматически реализуемого свойства  
 Любое выражение, которое может использоваться для инициализации поля, можно применять для инициализации автоматически реализуемого свойства.  При инициализации автоматически реализуемого свойства выражение анализируется и передается процедуре `Set` для свойства.  В следующих примерах кода показаны некоторые автоматически реализуемые свойства с начальными значениями.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/auto-implemented-propert_1_4.vb)]  
  
 Невозможно инициализировать автоматически реализуемое свойство, которое является элементом `Interface` или помечено как `MustOverride`.  
  
 При объявлении автоматически реализуемого свойства как элемента `Structure` его можно инициализировать, только если оно помечено как `Shared`.  
  
 При объявлении автоматически реализуемого свойства как массива невозможно указать явные границы массива.  Однако можно задать значение с помощью инициализатора массива, как показано в следующих примерах.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/auto-implemented-propert_1_5.vb)]  
  
## Определения свойств, для которых требуется стандартный синтаксис  
 Автоматически реализуемые свойства удобны и поддерживают множество сценариев программирования.  Однако существуют ситуации, в которых их нельзя использовать, и приходится применять стандартный \(*развернутый*\) синтаксис свойств.  
  
 Расширенный синтаксис определения свойства необходимо использовать, если вам нужно выполнить следующие действия.  
  
-   Добавить код для процедуры `Get` или `Set` свойства, например для проверки входящих значений в процедуре `Set`.  Например, вам требуется убедиться, что строка, представляющая номер телефона, содержит необходимое количество цифр перед заданием значения свойства.  
  
-   Указать другой уровень доступа для процедуры `Get` и `Set`.  Например, вам может потребоваться сделать процедуру `Set` `Private`, а процедуру `Get` — `Public`.  
  
-   Создать свойства типа `WriteOnly`.  
  
-   Использовать параметризованные свойства \(включая `Default`\).  Чтобы задать параметр для свойства или указать дополнительные параметры, требуется объявить развернутое свойство процедуры `Set`.  
  
-   Добавить атрибут в резервное поле или изменить уровень доступа резервного поля.  
  
-   Добавить XML\-комментарии для резервного поля.  
  
## Расширение автоматически реализуемого свойства  
 Если вам требуется преобразовать автоматически реализуемое свойство в расширенное свойство, которое содержит процедуру `Get` или `Set`, редактор кода Visual Basic может автоматически создать процедуры `Get` и `Set` и оператор `End Property` для свойства.  Чтобы создать код, поместите курсор на пустую строку после оператора `Property`, введите `G` \(для `Get`\) или `S` \(для `Set`\) и нажмите клавишу ВВОД.  Редактор кода Visual Basic автоматически создает процедуру `Get` или `Set` для свойств только для чтения и только для записи при нажатии клавиши ВВОД после оператора `Property`.  
  
## См. также  
 [Практическое руководство. Объявление и вызов свойства по умолчанию в Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [Практическое руководство. Объявление свойства со смешанным уровнем доступа](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [Оператор Property](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)   
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)   
 [Объекты и классы](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)