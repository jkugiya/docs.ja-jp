---
description: '詳細情報: Handles 句 (Visual Basic)'
title: Handles 句
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 2bddfdecc163feacaaf042a7928ab16af324b0a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769027"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="7ee18-103">Handles 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ee18-103">Handles Clause (Visual Basic)</span></span>

<span data-ttu-id="7ee18-104">プロシージャが指定されたイベントを処理することを宣言します。</span><span class="sxs-lookup"><span data-stu-id="7ee18-104">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ee18-105">構文</span><span class="sxs-lookup"><span data-stu-id="7ee18-105">Syntax</span></span>  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="7ee18-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="7ee18-106">Parts</span></span>  

 `proceduredeclaration`  
 <span data-ttu-id="7ee18-107">イベントを処理するプロシージャの `Sub` プロシージャ宣言。</span><span class="sxs-lookup"><span data-stu-id="7ee18-107">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="7ee18-108">コンマで区切られた、`proceduredeclaration` が処理するイベントの一覧。</span><span class="sxs-lookup"><span data-stu-id="7ee18-108">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="7ee18-109">イベントは、現在のクラスの基底クラス、または `WithEvents` キーワードを使用して宣言されたオブジェクトによって発生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ee18-109">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ee18-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="7ee18-110">Remarks</span></span>  

 <span data-ttu-id="7ee18-111">プロシージャ宣言の最後で `Handles` キーワードを使用すると、 `WithEvents` キーワードで宣言されたオブジェクト変数によって発生したイベントが処理されるようになります。</span><span class="sxs-lookup"><span data-stu-id="7ee18-111">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="7ee18-112">また、`Handles` キーワードを派生クラスで使用すると、基底クラスからのイベントを処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="7ee18-112">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="7ee18-113">`Handles` キーワードと `AddHandler` ステートメントはどちらも特定のプロシージャで特定のイベントを処理するように指定できますが、両者には違いがあります。</span><span class="sxs-lookup"><span data-stu-id="7ee18-113">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="7ee18-114">`Handles` キーワードは、プロシージャの定義時に特定のイベントを処理するよう指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="7ee18-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="7ee18-115">`AddHandler` ステートメントは、実行時にプロシージャをイベントに接続します。</span><span class="sxs-lookup"><span data-stu-id="7ee18-115">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="7ee18-116">詳細については、「[AddHandler ステートメント](addhandler-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ee18-116">For more information, see [AddHandler Statement](addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="7ee18-117">カスタム イベントの場合、アプリケーションは、プロシージャをイベント ハンドラーとして追加するときにイベントの `AddHandler` アクセサーを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7ee18-117">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="7ee18-118">カスタム イベントの詳細については、「[Event ステートメント](event-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ee18-118">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ee18-119">例</span><span class="sxs-lookup"><span data-stu-id="7ee18-119">Example</span></span>  

 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="7ee18-120">派生クラスで `Handles` ステートメントを使用して基底クラスからのイベントを処理する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="7ee18-120">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="7ee18-121">例</span><span class="sxs-lookup"><span data-stu-id="7ee18-121">Example</span></span>  

 <span data-ttu-id="7ee18-122">次の例には、**WPF アプリケーション** プロジェクトの 2 つのボタン イベント ハンドラーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7ee18-122">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="7ee18-123">例</span><span class="sxs-lookup"><span data-stu-id="7ee18-123">Example</span></span>  

 <span data-ttu-id="7ee18-124">次の例は、前の例と同じです。</span><span class="sxs-lookup"><span data-stu-id="7ee18-124">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="7ee18-125">`Handles` 句の `eventlist` には 2 つのボタンのイベントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7ee18-125">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="7ee18-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ee18-126">See also</span></span>

- [<span data-ttu-id="7ee18-127">WithEvents</span><span class="sxs-lookup"><span data-stu-id="7ee18-127">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="7ee18-128">AddHandler ステートメント</span><span class="sxs-lookup"><span data-stu-id="7ee18-128">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="7ee18-129">RemoveHandler ステートメント</span><span class="sxs-lookup"><span data-stu-id="7ee18-129">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="7ee18-130">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="7ee18-130">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="7ee18-131">RaiseEvent ステートメント</span><span class="sxs-lookup"><span data-stu-id="7ee18-131">RaiseEvent Statement</span></span>](raiseevent-statement.md)
- [<span data-ttu-id="7ee18-132">イベント</span><span class="sxs-lookup"><span data-stu-id="7ee18-132">Events</span></span>](../../programming-guide/language-features/events/index.md)
