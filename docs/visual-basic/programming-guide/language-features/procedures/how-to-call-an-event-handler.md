---
description: '詳細情報: Visual Basic でイベント ハンドラーを呼び出す方法'
title: イベント ハンドラーを呼び出す方法
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
no-loc:
- WithEvents
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 7e65b36d392211be533bb4881658b1cdb8057d5d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476255"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="ddd04-103">Visual Basic でイベント ハンドラーを呼び出す方法</span><span class="sxs-lookup"><span data-stu-id="ddd04-103">How to call an event handler in Visual Basic</span></span>

<span data-ttu-id="ddd04-104">"*イベント*" とは、何らかのプログラム コンポーネントによって認識されるアクションまたは発生 (マウス クリックやクレジット限度額の超過など) であり、それらに対して応答するコードを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="ddd04-104">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="ddd04-105">"*イベント ハンドラー*" とは、イベントに応答するために記述するコードです。</span><span class="sxs-lookup"><span data-stu-id="ddd04-105">An *event handler* is the code you write to respond to an event.</span></span>

<span data-ttu-id="ddd04-106">Visual Basic のイベント ハンドラーは `Sub` プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="ddd04-106">An event handler in Visual Basic is a `Sub` procedure.</span></span> <span data-ttu-id="ddd04-107">ただし、通常は、これを他の `Sub` プロシージャと同じ方法で呼び出すことはありません。</span><span class="sxs-lookup"><span data-stu-id="ddd04-107">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="ddd04-108">代わりに、プロシージャをイベントのハンドラーとして指定します。</span><span class="sxs-lookup"><span data-stu-id="ddd04-108">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="ddd04-109">これを行うには、[`Handles`](../../../language-reference/statements/handles-clause.md) 句と [`WithEvents`](../../../language-reference/modifiers/withevents.md) 変数を使用することも、[AddHandler ステートメント](../../../language-reference/statements/addhandler-statement.md)を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ddd04-109">You can do this either with a [`Handles`](../../../language-reference/statements/handles-clause.md) clause and a [`WithEvents`](../../../language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="ddd04-110">`Handles` 句の使用が、Visual Basic でイベント ハンドラーを宣言する場合の既定の方法となります。</span><span class="sxs-lookup"><span data-stu-id="ddd04-110">Using a `Handles` clause is the default way to declare an event handler in Visual Basic.</span></span> <span data-ttu-id="ddd04-111">統合開発環境 (IDE) でプログラミングする場合、デザイナーではこの方法を使用してイベント ハンドラーが記述されます。</span><span class="sxs-lookup"><span data-stu-id="ddd04-111">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="ddd04-112">`AddHandler` ステートメントは、実行時にイベントを動的に発生させるのに適しています。</span><span class="sxs-lookup"><span data-stu-id="ddd04-112">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>

<span data-ttu-id="ddd04-113">イベントが発生すると、イベント ハンドラー プロシージャが Visual Basic によって自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ddd04-113">When the event occurs, Visual Basic automatically calls the event handler procedure.</span></span> <span data-ttu-id="ddd04-114">イベントへのアクセス権を持つコードいずれも、[RaiseEvent ステートメント](../../../language-reference/statements/raiseevent-statement.md)を実行することによってそれを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="ddd04-114">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../language-reference/statements/raiseevent-statement.md).</span></span>

<span data-ttu-id="ddd04-115">複数のイベント ハンドラーを同じイベントに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="ddd04-115">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="ddd04-116">場合によっては、ハンドラーとイベントとの関連付けを解除することができます。</span><span class="sxs-lookup"><span data-stu-id="ddd04-116">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="ddd04-117">詳細については、「[イベント](../events/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddd04-117">For more information, see [Events](../events/index.md).</span></span>

## <a name="call-an-event-handler-using-no-loc-texthandles-and-withevents"></a><span data-ttu-id="ddd04-118">:::no-loc text="Handles"::: と WithEvents を使用してイベント ハンドラーを呼び出す</span><span class="sxs-lookup"><span data-stu-id="ddd04-118">Call an event handler using :::no-loc text="Handles"::: and WithEvents</span></span>

1. <span data-ttu-id="ddd04-119">[Event ステートメント](../../../language-reference/statements/event-statement.md)を使用してイベントが宣言されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ddd04-119">Make sure the event is declared with an [Event Statement](../../../language-reference/statements/event-statement.md).</span></span>

2. <span data-ttu-id="ddd04-120">[`WithEvents`](../../../language-reference/modifiers/withevents.md) キーワードを使用して、モジュール レベルまたはクラス レベルでオブジェクト変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="ddd04-120">Declare an object variable at module or class level, using the [`WithEvents`](../../../language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="ddd04-121">この変数の `As` 句で、イベントを発生させるクラスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddd04-121">The `As` clause for this variable must specify the class that raises the event.</span></span>

3. <span data-ttu-id="ddd04-122">イベント処理プロシージャ `Sub` の宣言内に、`WithEvents` 変数とイベント名を指定する [`Handles`](../../../language-reference/statements/handles-clause.md) 句を追加します。</span><span class="sxs-lookup"><span data-stu-id="ddd04-122">In the declaration of the event-handling `Sub` procedure, add a [`Handles`](../../../language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>

4. <span data-ttu-id="ddd04-123">イベントが発生すると、`Sub` プロシージャが Visual Basic によって自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ddd04-123">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="ddd04-124">コードでは、`RaiseEvent` ステートメントを使用してイベントを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="ddd04-124">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

    <span data-ttu-id="ddd04-125">次の例では、イベントと共に、そのイベントを発生させるクラスを参照する `WithEvents` 変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="ddd04-125">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="ddd04-126">イベント処理プロシージャ `Sub` では、`Handles` 句を使用して、処理するクラスとイベントが指定されます。</span><span class="sxs-lookup"><span data-stu-id="ddd04-126">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="4":::

## <a name="call-an-event-handler-using-addhandler"></a><span data-ttu-id="ddd04-127">AddHandler を使用してイベント ハンドラーを呼び出す</span><span class="sxs-lookup"><span data-stu-id="ddd04-127">Call an event handler using AddHandler</span></span>

1. <span data-ttu-id="ddd04-128">`Event` ステートメントを使用してイベントが宣言されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ddd04-128">Make sure the event is declared with an `Event` statement.</span></span>

2. <span data-ttu-id="ddd04-129">[AddHandler ステートメント](../../../language-reference/statements/addhandler-statement.md)を実行して、イベント処理プロシージャ `Sub` をイベントに動的に接続します。</span><span class="sxs-lookup"><span data-stu-id="ddd04-129">Execute an [AddHandler statement](../../../language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>

3. <span data-ttu-id="ddd04-130">イベントが発生すると、`Sub` プロシージャが Visual Basic によって自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ddd04-130">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="ddd04-131">コードでは、`RaiseEvent` ステートメントを使用してイベントを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="ddd04-131">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

    <span data-ttu-id="ddd04-132">次の例では、コンストラクターの [AddHandler ステートメント](../../../language-reference/statements/addhandler-statement.md)を使用し、`OnFormClosing` プロシージャを <xref:System.Windows.Forms.Form.FormClosing> のイベント ハンドラーとして関連付けます。</span><span class="sxs-lookup"><span data-stu-id="ddd04-132">The following example uses the [AddHandler statement](../../../language-reference/statements/addhandler-statement.md) in the constructor to associate the `OnFormClosing` procedure as an event handler for <xref:System.Windows.Forms.Form.FormClosing>.</span></span>

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="5":::

    <span data-ttu-id="ddd04-133">イベント ハンドラーとイベントの関連付けを解除するには、[RemoveHandler ステートメント](../../../language-reference/statements/removehandler-statement.md)を実行します。</span><span class="sxs-lookup"><span data-stu-id="ddd04-133">You can dissociate an event handler from an event by executing the [RemoveHandler statement](../../../language-reference/statements/removehandler-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ddd04-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="ddd04-134">See also</span></span>

- [<span data-ttu-id="ddd04-135">手順</span><span class="sxs-lookup"><span data-stu-id="ddd04-135">Procedures</span></span>](index.md)
- [<span data-ttu-id="ddd04-136">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ddd04-136">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="ddd04-137">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="ddd04-137">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="ddd04-138">AddressOf 演算子</span><span class="sxs-lookup"><span data-stu-id="ddd04-138">AddressOf Operator</span></span>](../../../language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="ddd04-139">方法: プロシージャを作成する</span><span class="sxs-lookup"><span data-stu-id="ddd04-139">How to: Create a Procedure</span></span>](how-to-create-a-procedure.md)
- [<span data-ttu-id="ddd04-140">方法: 値を返さないプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="ddd04-140">How to: Call a Procedure that Does Not Return a Value</span></span>](how-to-call-a-procedure-that-does-not-return-a-value.md)
