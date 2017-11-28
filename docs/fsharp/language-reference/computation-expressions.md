---
title: "Выражения вычисления (F#)"
description: "Описание способов создания удобный синтаксис для записи вычислений в F #, который можно упорядочивать и комбинировать с помощью конструкций потока управления и привязок."
keywords: "visual f#, f#, функциональное программирование"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: acabbf5d-fbb8-479f-894c-7251bf16c8c3
ms.openlocfilehash: 15ba2e167efc1d295d81439dcf85bc7272e05265
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="computation-expressions"></a><span data-ttu-id="1fb0b-104">Выражения вычисления</span><span class="sxs-lookup"><span data-stu-id="1fb0b-104">Computation Expressions</span></span>

<span data-ttu-id="1fb0b-105">Вычисление выражений в F # предоставляют удобный синтаксис для записи вычислений, которые можно упорядочивать и комбинировать с помощью конструкций потока управления и привязок.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-105">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="1fb0b-106">Их можно использовать для обеспечения удобного синтаксиса для *компоненты Monad*, функционального программирования, который может использоваться для управления данными, управления и побочными эффектами в функциональных программах.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-106">They can be used to provide a convenient syntax for *monads*, a functional programming feature that can be used to manage data, control, and side effects in functional programs.</span></span>


## <a name="built-in-workflows"></a><span data-ttu-id="1fb0b-107">Встроенные рабочие процессы</span><span class="sxs-lookup"><span data-stu-id="1fb0b-107">Built-in Workflows</span></span>
<span data-ttu-id="1fb0b-108">Выражения последовательностей являются Примером вычислительного выражения асинхронные рабочие потоки и выражения запроса.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-108">Sequence expressions are an example of a computation expression, as are asynchronous workflows and query expressions.</span></span> <span data-ttu-id="1fb0b-109">Дополнительные сведения см. в разделе [последовательности](sequences.md), [асинхронные рабочие потоки](asynchronous-workflows.md), и [выражения запросов](query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1fb0b-109">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

<span data-ttu-id="1fb0b-110">Некоторые функции являются общими для выражения последовательностей и асинхронные рабочие процессы и иллюстрируют базовый синтаксис для вычислительного выражения:</span><span class="sxs-lookup"><span data-stu-id="1fb0b-110">Certain features are common to both sequence expressions and asynchronous workflows and illustrate the basic syntax for a computation expression:</span></span>

```fsharp
builder-name { expression }
```

<span data-ttu-id="1fb0b-111">Представленный выше синтаксис определяет, что данное выражение является вычислительным типа, заданного *имени построителя*.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-111">The previous syntax specifies that the given expression is a computation expression of a type specified by *builder-name*.</span></span> <span data-ttu-id="1fb0b-112">Вычислительное выражение может быть встроенным рабочим процессом, например `seq` или `async`, или это может быть что-то определении.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-112">The computation expression can be a built-in workflow, such as `seq` or `async`, or it can be something you define.</span></span> <span data-ttu-id="1fb0b-113">*Имени построителя* — это идентификатор экземпляра специального типа, известный как *тип построителя*.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-113">The *builder-name* is the identifier for an instance of a special type known as the *builder type*.</span></span> <span data-ttu-id="1fb0b-114">Тип построителя является типом класса, который определяет особые методы, которые задают способ фрагментов вычислительного выражения объединяются, то есть код, которое управляет выполнением выражения.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-114">The builder type is a class type that defines special methods that govern the way the fragments of the computation expression are combined, that is, code that controls how the expression executes.</span></span> <span data-ttu-id="1fb0b-115">Другой способ класс построителя — сказать, что он позволяет настраивать работу многих конструкций языка F #, такие как циклы и привязки.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-115">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

<span data-ttu-id="1fb0b-116">В вычислительных выражениях для некоторых общих конструкций языка доступны две формы.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-116">In computation expressions, two forms are available for some common language constructs.</span></span> <span data-ttu-id="1fb0b-117">Варианты конструкций можно вызвать с помощью!</span><span class="sxs-lookup"><span data-stu-id="1fb0b-117">You can invoke the variant constructs by using a !</span></span> <span data-ttu-id="1fb0b-118">(восклицательный знак) суффикс определенные ключевые слова, такие как `let!`, `do!`, и т. д.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-118">(bang) suffix on certain keywords, such as `let!`, `do!`, and so on.</span></span> <span data-ttu-id="1fb0b-119">Такие специальные формы заставляют некоторые функции, определенные в классе построителя для замены обычное встроенное поведение этих операций.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-119">These special forms cause certain functions defined in the builder class to replace the ordinary built-in behavior of these operations.</span></span> <span data-ttu-id="1fb0b-120">Эти формы подобны `yield!` форму `yield` ключевое слово, которое используется в выражениях последовательности.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-120">These forms resemble the `yield!` form of the `yield` keyword that is used in sequence expressions.</span></span> <span data-ttu-id="1fb0b-121">Дополнительные сведения см. в разделе [последовательности](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="1fb0b-121">For more information, see [Sequences](sequences.md).</span></span>


## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="1fb0b-122">Создание нового типа вычислительного выражения</span><span class="sxs-lookup"><span data-stu-id="1fb0b-122">Creating a New Type of Computation Expression</span></span>
<span data-ttu-id="1fb0b-123">Можно определить характеристики собственных вычислительных выражений, создав класс построителя и определив специальные методы в классе.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-123">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="1fb0b-124">Класс построителя при необходимости можно определить методы, перечисленные в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-124">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="1fb0b-125">В следующей таблице описаны методы, которые могут использоваться в классе построителя рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-125">The following table describes methods that can be used in a workflow builder class.</span></span>


|<span data-ttu-id="1fb0b-126">**Метод**</span><span class="sxs-lookup"><span data-stu-id="1fb0b-126">**Method**</span></span>|<span data-ttu-id="1fb0b-127">**Типичные сигнатуры**</span><span class="sxs-lookup"><span data-stu-id="1fb0b-127">**Typical signature(s)**</span></span>|<span data-ttu-id="1fb0b-128">**Описание**</span><span class="sxs-lookup"><span data-stu-id="1fb0b-128">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="1fb0b-129">Вызывается для `let!` и `do!` в вычислительных выражениях.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-129">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="1fb0b-130">Создает оболочку вычислительного выражения в виде функции.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-130">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="1fb0b-131">Вызывается для `return` в вычислительных выражениях.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-131">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="1fb0b-132">Вызывается для `return!` в вычислительных выражениях.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-132">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="1fb0b-133">`M<'T> -> M<'T>` или</span><span class="sxs-lookup"><span data-stu-id="1fb0b-133">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="1fb0b-134">Выполняет вычислительное выражение.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-134">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="1fb0b-135">`M<'T> * M<'T> -> M<'T>` или</span><span class="sxs-lookup"><span data-stu-id="1fb0b-135">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="1fb0b-136">Вызывается для последовательности в вычислительных выражениях.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-136">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="1fb0b-137">`seq<'T> * ('T -> M<'U>) -> M<'U>` или</span><span class="sxs-lookup"><span data-stu-id="1fb0b-137">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="1fb0b-138">Вызывается для `for...do` в вычислительных выражениях.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-138">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="1fb0b-139">Вызывается для `try...finally` в вычислительных выражениях.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-139">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="1fb0b-140">Вызывается для `try...with` в вычислительных выражениях.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-140">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|<span data-ttu-id="1fb0b-141">Вызывается для `use` привязки в вычислительных выражениях.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-141">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="1fb0b-142">Вызывается для `while...do` в вычислительных выражениях.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-142">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="1fb0b-143">Вызывается для `yield` в вычислительных выражениях.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-143">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="1fb0b-144">Вызывается для `yield!` в вычислительных выражениях.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-144">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="1fb0b-145">Вызывается для пустых `else` ответвления `if...then` в вычислительных выражениях.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-145">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
<span data-ttu-id="1fb0b-146">Многие методы в классе построителя используют и возвращают `M<'T>` конструкцию, которая обычно является отдельно определенный тип, характеризующий вид объединяемых вычислений, например, `Async<'T>` асинхронные рабочие процессы и `Seq<'T>` для рабочих процессов последовательности.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-146">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="1fb0b-147">Сигнатуры этих методов включить их следует объединить и вложенные друг с другом, чтобы объект рабочего процесса, возвращаемый из одной конструкции могут передаваться в следующий.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-147">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="1fb0b-148">Когда компилятор анализирует вычислительное выражение преобразует его в ряд вложенные вызовы функций с помощью методов в предыдущей таблице и кода в вычислительное выражение.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-148">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="1fb0b-149">Вложенное выражение имеет следующую форму:</span><span class="sxs-lookup"><span data-stu-id="1fb0b-149">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="1fb0b-150">В приведенном выше коде вызовы `Run` и `Delay` пропускаются, если они не определены в классе построителя вычислительных выражений.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-150">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="1fb0b-151">Тело вычислительного выражения, обозначенное здесь как `{| cexpr |}`, преобразуются в вызовы с участием методов класса построителя посредством преобразований, приведенных в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-151">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="1fb0b-152">Вычислительное выражение `{| cexpr |}` определяется рекурсивно в соответствии с этими преобразованиями где `expr` выражение F # и `cexpr` выражение вычисления.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-152">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>



|<span data-ttu-id="1fb0b-153">Выражение</span><span class="sxs-lookup"><span data-stu-id="1fb0b-153">Expression</span></span>|<span data-ttu-id="1fb0b-154">Перевод</span><span class="sxs-lookup"><span data-stu-id="1fb0b-154">Translation</span></span>|
|----------|-----------|
|<code>{&#124; let binding in cexpr &#124;}</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{&#124; let! pattern = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; do! expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; yield expr &#124;}</code>|`builder.Yield(expr)`|
|<code>{&#124; yield! expr &#124;}</code>|`builder.YieldFrom(expr)`|
|<code>{&#124; return expr &#124;}<code>|`builder.Return(expr)`|
|<code>{&#124; return! expr &#124;}</code>|`builder.ReturnFrom(expr)`|
|<code>{&#124; use pattern = expr in cexpr &#124;}</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; use! value = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> {&#124; cexpr &#124;}))))</code>|
|<code>{&#124; if expr then cexpr0 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else binder.Zero()</code>|
|<code>{&#124; if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else {&#124; cexpr1 &#124;}</code>|
|<code>{&#124; match expr with &#124; pattern_i -> cexpr_i &#124;}</code>|<code>match expr with &#124; pattern_i -> {&#124; cexpr_i &#124;}</code>|
|<code>{&#124; for pattern in expr do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; for identifier = expr1 to expr2 do cexpr &#124;}<code>|<code>builder.For(enumeration, (fun identifier -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr), builder.Delay({&#124;cexpr &#124;})</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|
<span data-ttu-id="1fb0b-155">В таблице выше `other-expr` соответствует выражению, в противном случае не указан в таблице.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-155">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="1fb0b-156">Класс построителя не реализует все методы и поддерживает все переводы, перечисленные в предыдущей таблице.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-156">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="1fb0b-157">Эти конструкции, которые не реализованы недоступны в вычислительных выражениях данного типа.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-157">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="1fb0b-158">Например, если не требуется поддерживать `use` ключевое слово в вычислительных выражениях можно опустить определение `Use` в классе построителя.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-158">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="1fb0b-159">В следующем примере кода показано выражение вычисления, инкапсулирующий вычисление вычисленному один шаг ряд шагов, которые могут быть одновременно.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-159">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="1fb0b-160">Объект размеченные объединения типа `OkOrException`, кодирует состояние ошибки выражения, вычисленному на данный момент.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-160">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="1fb0b-161">Этот код демонстрирует несколько типичных шаблонов, которые можно использовать в выражениях вычислений, таких как стандартный реализации для некоторых методов построителя.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-161">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> NotYetDone (fun () -> func value)
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res -> 
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally 
            (whileLoop 
                (fun () -> ie.MoveNext()) 
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn " x = %d" x
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this 
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "NotYetDone <closure>"
comp |> step |> step |> step |> step |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step |> step |> step |> step |> step
```

<span data-ttu-id="1fb0b-162">Вычислительное выражение имеет базовый тип, который возвращает выражение.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-162">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="1fb0b-163">Базовый тип может представлять вычисленных результирующих или отложенное вычисление, которое может быть выполнена, или обеспечивают способ итерации по коллекции своего рода.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-163">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="1fb0b-164">В предыдущем примере был базовый тип **со временем**.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-164">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="1fb0b-165">В случае выражения последовательности базовым типом является <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-165">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1fb0b-166">Для выражения запроса, базовым типом является <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-166">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1fb0b-167">Для асинхронного рабочего процесса, базовым типом является [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span><span class="sxs-lookup"><span data-stu-id="1fb0b-167">For an asychronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="1fb0b-168">`Async` Трудозатрат для вычисления результат представляет объект.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-168">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="1fb0b-169">Например, можно вызвать [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) для выполнения вычислений и возвращают результат.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-169">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="1fb0b-170">Пользовательские операции</span><span class="sxs-lookup"><span data-stu-id="1fb0b-170">Custom Operations</span></span>
<span data-ttu-id="1fb0b-171">Можно определить пользовательскую операцию на вычислительное выражение и использовать пользовательскую операцию как оператор в выражении вычисления.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-171">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="1fb0b-172">Например можно включить оператора запроса в выражении запроса.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-172">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="1fb0b-173">При определении пользовательскую операцию, необходимо определить доход и для методов в вычислительное выражение.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-173">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="1fb0b-174">Чтобы определить пользовательскую операцию, поместите его в классе построитель вычислительного выражения и примените [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span><span class="sxs-lookup"><span data-stu-id="1fb0b-174">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="1fb0b-175">Этот атрибут принимает строку в качестве аргумента, то есть имя для использования в пользовательской операции.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-175">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="1fb0b-176">Это имя поступает в область видимости в начале открывающая фигурная скобка вычислительного выражения.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-176">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="1fb0b-177">Таким образом не следует использовать идентификаторы, которые имеют имя, совпадающее с именем пользовательской операции в этом блоке.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-177">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="1fb0b-178">Например, такие как Избегайте использования идентификаторов `all` или `last` в выражениях запросов.</span><span class="sxs-lookup"><span data-stu-id="1fb0b-178">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

## <a name="see-also"></a><span data-ttu-id="1fb0b-179">См. также</span><span class="sxs-lookup"><span data-stu-id="1fb0b-179">See Also</span></span>
[<span data-ttu-id="1fb0b-180">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="1fb0b-180">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="1fb0b-181">Асинхронные рабочие потоки</span><span class="sxs-lookup"><span data-stu-id="1fb0b-181">Asynchronous Workflows</span></span>](asynchronous-workflows.md)

[<span data-ttu-id="1fb0b-182">Последовательности</span><span class="sxs-lookup"><span data-stu-id="1fb0b-182">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)

[<span data-ttu-id="1fb0b-183">Выражения запросов</span><span class="sxs-lookup"><span data-stu-id="1fb0b-183">Query Expressions</span></span>](query-expressions.md)