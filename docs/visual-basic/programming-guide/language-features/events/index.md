---
description: '詳細情報: イベント (Visual Basic)'
title: イベント
ms.date: 07/20/2015
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
ms.openlocfilehash: 6cd4a4b997ec13b394cae38e9d66c7dd9c283aaf
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483678"
---
# <a name="events-visual-basic"></a><span data-ttu-id="fa175-103">イベント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa175-103">Events (Visual Basic)</span></span>

<span data-ttu-id="fa175-104">Visual Studio プロジェクトとは、順に実行される一連のプロシージャと思っているかもしれませんが、実際には、ほとんどのプログラムはイベント ドリブン型です。つまり、実行の流れは、外部で発生する "*イベント*" と呼ばれる事象によって決まります。</span><span class="sxs-lookup"><span data-stu-id="fa175-104">While you might visualize a Visual Studio project as a series of procedures that execute in a sequence, in reality, most programs are event driven—meaning the flow of execution is determined by external occurrences called *events*.</span></span>  
  
 <span data-ttu-id="fa175-105">イベントは、何らかの重要な出来事が発生したことをアプリケーションに通知するシグナルです。</span><span class="sxs-lookup"><span data-stu-id="fa175-105">An event is a signal that informs an application that something important has occurred.</span></span> <span data-ttu-id="fa175-106">たとえば、ユーザーがフォーム上のコントロールをクリックすると、フォームは、`Click` イベントを発生させて、そのイベントを処理するプロシージャを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="fa175-106">For example, when a user clicks a control on a form, the form can raise a `Click` event and call a procedure that handles the event.</span></span> <span data-ttu-id="fa175-107">イベントは、複数のタスク間の通信を可能にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="fa175-107">Events also allow separate tasks to communicate.</span></span> <span data-ttu-id="fa175-108">たとえば、メインのアプリケーションとは別のアプリケーションで並べ替えタスクを実行するとします。</span><span class="sxs-lookup"><span data-stu-id="fa175-108">Say, for example, that your application performs a sort task separately from the main application.</span></span> <span data-ttu-id="fa175-109">ユーザーが並べ替えを取り消した場合、アプリケーションは並べ替え処理の停止を指示するキャンセル イベントを送信できます。</span><span class="sxs-lookup"><span data-stu-id="fa175-109">If a user cancels the sort, your application can send a cancel event instructing the sort process to stop.</span></span>  
  
## <a name="event-terms-and-concepts"></a><span data-ttu-id="fa175-110">イベントの用語と概念</span><span class="sxs-lookup"><span data-stu-id="fa175-110">Event Terms and Concepts</span></span>  

 <span data-ttu-id="fa175-111">このセクションでは、Visual Studio で使用される用語と概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="fa175-111">This section describes the terms and concepts used with events in Visual Basic.</span></span>  
  
### <a name="declaring-events"></a><span data-ttu-id="fa175-112">イベントの宣言</span><span class="sxs-lookup"><span data-stu-id="fa175-112">Declaring Events</span></span>  

 <span data-ttu-id="fa175-113">イベントは、次の例に示すように、`Event` キーワードを使用して、クラス、構造体、モジュール、およびインターフェイス内で宣言します。</span><span class="sxs-lookup"><span data-stu-id="fa175-113">You declare events within classes, structures, modules, and interfaces using the `Event` keyword, as in the following example:</span></span>  
  
 [!code-vb[VbVbalrEvents#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#24)]  
  
### <a name="raising-events"></a><span data-ttu-id="fa175-114">イベントの発生</span><span class="sxs-lookup"><span data-stu-id="fa175-114">Raising Events</span></span>  

 <span data-ttu-id="fa175-115">イベントは、重要な出来事が発生したことを通知するメッセージに似ています。</span><span class="sxs-lookup"><span data-stu-id="fa175-115">An event is like a message announcing that something important has occurred.</span></span> <span data-ttu-id="fa175-116">メッセージをブロードキャストする動作は、"*イベントの発生*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="fa175-116">The act of broadcasting the message is called *raising* the event.</span></span> <span data-ttu-id="fa175-117">Visual Studio では、次の例に示すように、`RaiseEvent` ステートメントを使用してイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="fa175-117">In Visual Basic, you raise events with the `RaiseEvent` statement, as in the following example:</span></span>  
  
 [!code-vb[VbVbalrEvents#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#25)]  
  
 <span data-ttu-id="fa175-118">イベントは、イベントを宣言しているクラス、モジュール、または構造体のスコープ内で発生させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa175-118">Events must be raised within the scope of the class, module, or structure where they are declared.</span></span> <span data-ttu-id="fa175-119">たとえば、基本クラスから継承された派生クラスでイベントを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="fa175-119">For example, a derived class cannot raise events inherited from a base class.</span></span>  
  
### <a name="event-senders"></a><span data-ttu-id="fa175-120">イベントの送信元</span><span class="sxs-lookup"><span data-stu-id="fa175-120">Event Senders</span></span>  

 <span data-ttu-id="fa175-121">イベントを発生させる機能を持つオブジェクトが "*イベントの送信元*" になります。これは "*イベント ソース*" とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="fa175-121">Any object capable of raising an event is an *event sender*, also known as an *event source*.</span></span> <span data-ttu-id="fa175-122">イベントの送信元の例として、フォーム、コントロール、およびユーザー定義オブジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="fa175-122">Forms, controls, and user-defined objects are examples of event senders.</span></span>  
  
### <a name="event-handlers"></a><span data-ttu-id="fa175-123">イベント ハンドラー</span><span class="sxs-lookup"><span data-stu-id="fa175-123">Event Handlers</span></span>  

 <span data-ttu-id="fa175-124">"*イベント ハンドラー*" は、対応するイベントが発生したときに呼び出されるプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="fa175-124">*Event handlers* are procedures that are called when a corresponding event occurs.</span></span> <span data-ttu-id="fa175-125">イベント ハンドラーと一致するシグネチャを持つ任意の有効なサブルーチンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fa175-125">You can use any valid subroutine with a matching signature as an event handler.</span></span> <span data-ttu-id="fa175-126">ただし、関数はイベント ソースに値を返すことができないため、イベント ハンドラーとして使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="fa175-126">You cannot use a function as an event handler, however, because it cannot return a value to the event source.</span></span>  
  
 <span data-ttu-id="fa175-127">Visual Studio では、イベント ハンドラーの標準的な名前付け規則である、イベントの送信元、アンダースコア、およびイベントの名前の組み合わせを使用しています。</span><span class="sxs-lookup"><span data-stu-id="fa175-127">Visual Basic uses a standard naming convention for event handlers that combines the name of the event sender, an underscore, and the name of the event.</span></span> <span data-ttu-id="fa175-128">たとえば、`button1` という名前のボタンの `Click` イベントには、`Sub button1_Click` という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="fa175-128">For example, the `Click` event of a button named `button1` would be named `Sub button1_Click`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa175-129">独自のイベントに対するイベント ハンドラーを定義するときは、この名前付け規則を使用することをお勧めしますが、使用は必須ではありません。任意の有効なサブルーチン名を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="fa175-129">We recommend that you use this naming convention when defining event handlers for your own events, but it is not required; you can use any valid subroutine name.</span></span>  
  
## <a name="associating-events-with-event-handlers"></a><span data-ttu-id="fa175-130">イベントとイベント ハンドラーの関連付け</span><span class="sxs-lookup"><span data-stu-id="fa175-130">Associating Events with Event Handlers</span></span>  

 <span data-ttu-id="fa175-131">イベント ハンドラーを使用する前に、`Handles` ステートメントまたは `AddHandler` ステートメントを使用して、イベントをイベント ハンドラーに関連付けておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa175-131">Before an event handler becomes usable, you must first associate it with an event by using either the `Handles` or `AddHandler` statement.</span></span>  
  
### <a name="withevents-and-the-handles-clause"></a><span data-ttu-id="fa175-132">WithEvents と Handles 句</span><span class="sxs-lookup"><span data-stu-id="fa175-132">WithEvents and the Handles Clause</span></span>  

 <span data-ttu-id="fa175-133">`WithEvents` ステートメントと `Handles` 句を使用して、指定するイベント ハンドラーを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="fa175-133">The `WithEvents` statement and `Handles` clause provide a declarative way of specifying event handlers.</span></span> <span data-ttu-id="fa175-134">`WithEvents` キーワードを使用して宣言されたオブジェクトによって発生したイベントは、次の例に示すように、そのイベント用の `Handles` ステートメントがある任意のプロシージャで処理できます。</span><span class="sxs-lookup"><span data-stu-id="fa175-134">An event raised by an object declared with the `WithEvents` keyword can be handled by any procedure with a `Handles` statement for that event, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbalrEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#1)]  
  
 <span data-ttu-id="fa175-135">多くの場合、イベント ハンドラーを指定するための最善の選択は、`WithEvents` ステートメントと `Handles` 句を使用することです。これは、宣言型の構文により簡単にコーディング、読み取り、デバッグを実行できるためです。</span><span class="sxs-lookup"><span data-stu-id="fa175-135">The `WithEvents` statement and the `Handles` clause are often the best choice for event handlers because the declarative syntax they use makes event handling easier to code, read and debug.</span></span> <span data-ttu-id="fa175-136">ただし、`WithEvents` 変数には、次の使用制限があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fa175-136">However, be aware of the following limitations on the use of `WithEvents` variables:</span></span>  
  
- <span data-ttu-id="fa175-137">`WithEvents` 変数をオブジェクト変数として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="fa175-137">You cannot use a `WithEvents` variable as an object variable.</span></span> <span data-ttu-id="fa175-138">つまり、`Object` として宣言することはできません。変数を宣言するときは、クラス名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa175-138">That is, you cannot declare it as `Object`—you must specify the class name when you declare the variable.</span></span>  
  
- <span data-ttu-id="fa175-139">共有イベントはクラス インスタンスに関連付けられないため、`WithEvents` を使用して共有イベントを宣言によって処理することはできません。</span><span class="sxs-lookup"><span data-stu-id="fa175-139">Because shared events are not tied to class instances, you cannot use `WithEvents` to declaratively handle shared events.</span></span> <span data-ttu-id="fa175-140">同様に、`WithEvents` または`Handles` を使用して `Structure` からイベントを処理することはできません。</span><span class="sxs-lookup"><span data-stu-id="fa175-140">Similarly, you cannot use `WithEvents` or `Handles` to handle events from a `Structure`.</span></span> <span data-ttu-id="fa175-141">どちらの場合も、`AddHandler` ステートメント使用して、これらのイベントを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="fa175-141">In both cases, you can use the `AddHandler` statement to handle those events.</span></span>  
  
- <span data-ttu-id="fa175-142">`WithEvents` 変数の配列を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="fa175-142">You cannot create arrays of `WithEvents` variables.</span></span>  
  
 <span data-ttu-id="fa175-143">`WithEvents` 変数を使用して、1 つのイベント ハンドラーで 1 つまたは複数の種類のイベントを、または 1 つまたは複数のイベント ハンドラーで同じ種類のイベントを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="fa175-143">`WithEvents` variables allow a single event handler to handle one or more kind of event, or one or more event handlers to handle the same kind of event.</span></span>  
  
 <span data-ttu-id="fa175-144">`Handles` 句は、イベントをイベント ハンドラーに関連付けるための標準的な方法ですが、イベントをイベント ハンドラーに関連付ける動作はコンパイル時に限定されます。</span><span class="sxs-lookup"><span data-stu-id="fa175-144">Although the `Handles` clause is the standard way of associating an event with an event handler, it is limited to associating events with event handlers at compile time.</span></span>  
  
 <span data-ttu-id="fa175-145">場合によっては (フォームやコントロールに関連付けられたイベントなど)、Visual Studio は、空のイベント ハンドラーを自動的にスタブとして作成し、それをイベントに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="fa175-145">In some cases, such as with events associated with forms or controls, Visual Basic automatically stubs out an empty event handler and associates it with an event.</span></span> <span data-ttu-id="fa175-146">たとえば、デザイン モードでフォームのコマンド ボタンをダブルクリックすると、次のコードに示すように、Visual Studio はコマンド ボタン用の空のイベント ハンドラーと `WithEvents` 変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="fa175-146">For example, when you double-click a command button on a form in design mode, Visual Basic creates an empty event handler and a `WithEvents` variable for the command button, as in the following code:</span></span>  
  
 [!code-vb[VbVbalrEvents#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#26)]  
  
### <a name="addhandler-and-removehandler"></a><span data-ttu-id="fa175-147">AddHandler と RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="fa175-147">AddHandler and RemoveHandler</span></span>  

 <span data-ttu-id="fa175-148">`AddHandler` ステートメントは、イベント ハンドラーを指定できるという点で `Handles` 句に似ています。</span><span class="sxs-lookup"><span data-stu-id="fa175-148">The `AddHandler` statement is similar to the `Handles` clause in that both allow you to specify an event handler.</span></span> <span data-ttu-id="fa175-149">ただし、`AddHandler` を `RemoveHandler` と一緒に使用すると、`Handles` 句よりも柔軟性が増し、イベントに関連付けられたイベント ハンドラーを動的に追加、削除、変更することができます。</span><span class="sxs-lookup"><span data-stu-id="fa175-149">However, `AddHandler`, used with `RemoveHandler`, provides greater flexibility than the `Handles` clause, allowing you to dynamically add, remove, and change the event handler associated with an event.</span></span> <span data-ttu-id="fa175-150">共有イベントまたは構造体からのイベントを処理する場合は、`AddHandler` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa175-150">If you want to handle shared events or events from a structure, you must use `AddHandler`.</span></span>  
  
 <span data-ttu-id="fa175-151">`AddHandler` は 2 つの引数 (コントロールなどのイベントの送信元から渡されるイベント名と、デリゲートを評価する式) を使用します。</span><span class="sxs-lookup"><span data-stu-id="fa175-151">`AddHandler` takes two arguments: the name of an event from an event sender such as a control, and an expression that evaluates to a delegate.</span></span> <span data-ttu-id="fa175-152">`AddHandler` を使用する場合はデリゲート クラスを明示的に指定する必要がありません。これは、`AddressOf` ステートメントが常にデリゲートへの参照を返すためです。</span><span class="sxs-lookup"><span data-stu-id="fa175-152">You do not need to explicitly specify the delegate class when using `AddHandler`, since the `AddressOf` statement always returns a reference to the delegate.</span></span> <span data-ttu-id="fa175-153">次の例では、オブジェクトによって発生するイベントにイベント ハンドラーを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="fa175-153">The following example associates an event handler with an event raised by an object:</span></span>  
  
 [!code-vb[VbVbalrEvents#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#28)]  
  
 <span data-ttu-id="fa175-154">イベントとイベント ハンドラーと関連付けを解除する `RemoveHandler` は、`AddHandler` と同じ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="fa175-154">`RemoveHandler`, which disconnects an event from an event handler, uses the same syntax as `AddHandler`.</span></span> <span data-ttu-id="fa175-155">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="fa175-155">For example:</span></span>  
  
 [!code-vb[VbVbalrEvents#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#29)]  
  
 <span data-ttu-id="fa175-156">次の例では、イベントにイベント ハンドラーが関連付けられた後、イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="fa175-156">In the following example, an event handler is associated with an event, and the event is raised.</span></span> <span data-ttu-id="fa175-157">イベント ハンドラーがイベントをキャッチし、メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="fa175-157">The event handler catches the event and displays a message.</span></span>  
  
 <span data-ttu-id="fa175-158">次に、最初のイベント ハンドラーが削除され、別のイベント ハンドラーがイベントに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="fa175-158">Then the first event handler is removed and a different event handler is associated with the event.</span></span> <span data-ttu-id="fa175-159">もう一度イベントが発生し、別のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fa175-159">When the event is raised again, a different message is displayed.</span></span>  
  
 <span data-ttu-id="fa175-160">最後に、2 つ目のイベント ハンドラーが削除され、3 回目のイベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="fa175-160">Finally, the second event handler is removed and the event is raised for a third time.</span></span> <span data-ttu-id="fa175-161">イベントに関連付けられているイベント ハンドラーがないため、何も実行されません。</span><span class="sxs-lookup"><span data-stu-id="fa175-161">Because there is no longer an event handler associated with the event, no action is taken.</span></span>  
  
 [!code-vb[VbVbalrEvents#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class2.vb#38)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a><span data-ttu-id="fa175-162">基本クラスから継承されたイベントの処理</span><span class="sxs-lookup"><span data-stu-id="fa175-162">Handling Events Inherited from a Base Class</span></span>  

 <span data-ttu-id="fa175-163">"*派生クラス*" は基本クラスから特性を継承したクラスであり、基本クラスによって発生したイベントを `Handles MyBase` ステートメントを使用して処理できます。</span><span class="sxs-lookup"><span data-stu-id="fa175-163">*Derived classes*—classes that inherit characteristics from a base class—can handle events raised by their base class using the `Handles MyBase` statement.</span></span>  
  
### <a name="to-handle-events-from-a-base-class"></a><span data-ttu-id="fa175-164">基本クラスのイベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="fa175-164">To handle events from a base class</span></span>  
  
- <span data-ttu-id="fa175-165">イベント ハンドラー プロシージャの宣言行に `Handles MyBase.`*eventname* ステートメントを追加して、派生クラスのイベント ハンドラーを宣言します。*eventname* は処理する基本クラスのイベント名です。</span><span class="sxs-lookup"><span data-stu-id="fa175-165">Declare an event handler in the derived class by adding a `Handles MyBase.`*eventname* statement to the declaration line of your event-handler procedure, where *eventname* is the name of the event in the base class you are handling.</span></span> <span data-ttu-id="fa175-166">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="fa175-166">For example:</span></span>  
  
     [!code-vb[VbVbalrEvents#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#12)]  
  
## <a name="related-sections"></a><span data-ttu-id="fa175-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa175-167">Related Sections</span></span>  
  
|<span data-ttu-id="fa175-168">Title</span><span class="sxs-lookup"><span data-stu-id="fa175-168">Title</span></span>|<span data-ttu-id="fa175-169">説明</span><span class="sxs-lookup"><span data-stu-id="fa175-169">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="fa175-170">チュートリアル: イベントの宣言と発生</span><span class="sxs-lookup"><span data-stu-id="fa175-170">Walkthrough: Declaring and Raising Events</span></span>](walkthrough-declaring-and-raising-events.md)|<span data-ttu-id="fa175-171">クラスのイベントを宣言して発生させる方法を手順を追って説明します。</span><span class="sxs-lookup"><span data-stu-id="fa175-171">Provides a step-by-step description of how to declare and raise events for a class.</span></span>|  
|[<span data-ttu-id="fa175-172">チュートリアル: イベントの処理</span><span class="sxs-lookup"><span data-stu-id="fa175-172">Walkthrough: Handling Events</span></span>](walkthrough-handling-events.md)|<span data-ttu-id="fa175-173">イベント ハンドラー プロシージャの記述方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fa175-173">Demonstrates how to write an event-handler procedure.</span></span>|  
|[<span data-ttu-id="fa175-174">方法: カスタム イベントを宣言してブロックを回避する</span><span class="sxs-lookup"><span data-stu-id="fa175-174">How to: Declare Custom Events To Avoid Blocking</span></span>](how-to-declare-custom-events-to-avoid-blocking.md)|<span data-ttu-id="fa175-175">イベント ハンドラーを非同期に呼び出すことができるカスタム イベントの定義方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fa175-175">Demonstrates how to define a custom event that allows its event handlers to be called asynchronously.</span></span>|  
|[<span data-ttu-id="fa175-176">方法: カスタム イベントを宣言してメモリを節約する</span><span class="sxs-lookup"><span data-stu-id="fa175-176">How to: Declare Custom Events To Conserve Memory</span></span>](how-to-declare-custom-events-to-conserve-memory.md)|<span data-ttu-id="fa175-177">イベントを処理するときにのみ、メモリを使用するカスタム イベントを定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fa175-177">Demonstrates how to define a custom event that uses memory only when the event is handled.</span></span>|  
|[<span data-ttu-id="fa175-178">Visual Basic での継承されたイベント ハンドラーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fa175-178">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](troubleshooting-inherited-event-handlers.md)|<span data-ttu-id="fa175-179">継承されたコンポーネントのイベント ハンドラーで生じる一般的な問題を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="fa175-179">Lists common issues that arise with event handlers in inherited components.</span></span>|  
|[<span data-ttu-id="fa175-180">イベント</span><span class="sxs-lookup"><span data-stu-id="fa175-180">Events</span></span>](../../../../standard/events/index.md)|<span data-ttu-id="fa175-181">.NET Framework のイベント モデルについて概説します。</span><span class="sxs-lookup"><span data-stu-id="fa175-181">Provides an overview of the event model in the .NET Framework.</span></span>|  
|[<span data-ttu-id="fa175-182">Windows フォーム内でのイベント ハンドラーの作成</span><span class="sxs-lookup"><span data-stu-id="fa175-182">Creating Event Handlers in Windows Forms</span></span>](/dotnet/desktop/winforms/creating-event-handlers-in-windows-forms)|<span data-ttu-id="fa175-183">Windows フォーム オブジェクトに関連付けられているイベントの処理方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fa175-183">Describes how to work with events associated with Windows Forms objects.</span></span>|  
|[<span data-ttu-id="fa175-184">デリゲート</span><span class="sxs-lookup"><span data-stu-id="fa175-184">Delegates</span></span>](../delegates/index.md)|<span data-ttu-id="fa175-185">Visual Basic でのデリゲートの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="fa175-185">Provides an overview of delegates in Visual Basic.</span></span>|
