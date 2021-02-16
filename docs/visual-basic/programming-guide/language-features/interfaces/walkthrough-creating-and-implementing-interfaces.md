---
description: '詳細情報: チュートリアル: インターフェイスの作成と実装 (Visual Basic)'
title: インターフェイスの作成と実装
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 058011d311fdecba626a59228816f9bced319c97
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468422"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="535eb-103">チュートリアル: インターフェイスの作成と実装 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="535eb-103">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>

<span data-ttu-id="535eb-104">インターフェイスには、プロパティ、メソッド、およびイベントの特性が記述されていますが、実装の詳細は構造体またはクラスに委ねられています。</span><span class="sxs-lookup"><span data-stu-id="535eb-104">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="535eb-105">このチュートリアルでは、インターフェイスを宣言し、実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="535eb-105">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="535eb-106">このチュートリアルでは、ユーザー インターフェイスの作成方法については説明しません。</span><span class="sxs-lookup"><span data-stu-id="535eb-106">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a><span data-ttu-id="535eb-107">インターフェイスを定義するには</span><span class="sxs-lookup"><span data-stu-id="535eb-107">To define an interface</span></span>
  
1. <span data-ttu-id="535eb-108">新しい Visual Basic Windows アプリケーション プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="535eb-108">Open a new Visual Basic Windows Application project.</span></span>  
  
2. <span data-ttu-id="535eb-109">**[プロジェクト]** メニューの **[モジュールの追加]** をクリックして、プロジェクトに新しいモジュールを追加します。</span><span class="sxs-lookup"><span data-stu-id="535eb-109">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3. <span data-ttu-id="535eb-110">新しいモジュールに `Module1.vb` という名前を付け、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="535eb-110">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="535eb-111">新しいモジュールのコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="535eb-111">The code for the new module is displayed.</span></span>  
  
4. <span data-ttu-id="535eb-112">`Module` ステートメントと `End Module` ステートメントの間に `Interface TestInterface` と入力し、ENTER キーを押して、`Module1` 内に `TestInterface` という名前のインターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="535eb-112">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="535eb-113">**コード エディター** によって `Interface` キーワードがインデントされ、`End Interface` ステートメントが追加されて、コード ブロックが形成されます。</span><span class="sxs-lookup"><span data-stu-id="535eb-113">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5. <span data-ttu-id="535eb-114">`Interface` ステートメントと `End Interface` ステートメントの間に次のコードを配置して、インターフェイスのプロパティ、メソッド、およびイベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="535eb-114">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a><span data-ttu-id="535eb-115">実装</span><span class="sxs-lookup"><span data-stu-id="535eb-115">Implementation</span></span>

 <span data-ttu-id="535eb-116">インターフェイス メンバーを宣言するために使用する構文は、クラス メンバーを宣言するために使用する構文とは異なるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="535eb-116">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="535eb-117">この差異は、インターフェイスに実装コードを含めることができないという事実を反映しています。</span><span class="sxs-lookup"><span data-stu-id="535eb-117">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
### <a name="to-implement-the-interface"></a><span data-ttu-id="535eb-118">インターフェイスを実装するには</span><span class="sxs-lookup"><span data-stu-id="535eb-118">To implement the interface</span></span>
  
1. <span data-ttu-id="535eb-119">`Module1` に次のステートメントを追加し、ENTER キーを押して、`ImplementationClass` という名前のクラスを追加します。追加する場所は、`End Interface` ステートメントの後で、`End Module` ステートメントの前です。</span><span class="sxs-lookup"><span data-stu-id="535eb-119">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     <span data-ttu-id="535eb-120">統合開発環境内で作業している場合は、ENTER キーを押すと、**コード エディター** によって対応する `End Class` ステートメントが提供されます。</span><span class="sxs-lookup"><span data-stu-id="535eb-120">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2. <span data-ttu-id="535eb-121">次の `Implements` ステートメントを `ImplementationClass` に追加します。これにより、クラスで実装するインターフェイスに名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="535eb-121">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     <span data-ttu-id="535eb-122">`Implements` ステートメントが、クラスまたは構造体の先頭にある他の項目とは別にリストされている場合、そのステートメントは、クラスまたは構造体がインターフェイスを実装していることを示します。</span><span class="sxs-lookup"><span data-stu-id="535eb-122">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="535eb-123">統合開発環境内で作業している場合は、ENTER キーを押すと、**コード エディター** によって `TestInterface` に必要なクラス メンバーが実装され、次の手順をスキップできます。</span><span class="sxs-lookup"><span data-stu-id="535eb-123">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3. <span data-ttu-id="535eb-124">統合開発環境内で作業していない場合は、`MyInterface` インターフェイスのすべてのメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="535eb-124">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="535eb-125">次のコードを `ImplementationClass` に追加して、`Event1`、`Method1`、および `Prop1` を実装します。</span><span class="sxs-lookup"><span data-stu-id="535eb-125">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     <span data-ttu-id="535eb-126">`Implements` ステートメントで、実装するインターフェイスとインターフェイス メンバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="535eb-126">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4. <span data-ttu-id="535eb-127">プロパティ値を格納したプライベート フィールドをクラスに追加して、`Prop1` の定義を完了します。</span><span class="sxs-lookup"><span data-stu-id="535eb-127">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     <span data-ttu-id="535eb-128">プロパティの get アクセサーで `pval` の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="535eb-128">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     <span data-ttu-id="535eb-129">プロパティの set アクセサーで `pval` の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="535eb-129">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. <span data-ttu-id="535eb-130">次のコードを追加して、`Method1` の定義を完了します。</span><span class="sxs-lookup"><span data-stu-id="535eb-130">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="535eb-131">インターフェイスの実装をテストするには</span><span class="sxs-lookup"><span data-stu-id="535eb-131">To test the implementation of the interface</span></span>
  
1. <span data-ttu-id="535eb-132">**ソリューション エクスプローラー** でプロジェクトのスタートアップ フォームを右クリックし、 **[コードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="535eb-132">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="535eb-133">エディターにスタートアップ フォームのクラスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="535eb-133">The editor displays the class for your startup form.</span></span> <span data-ttu-id="535eb-134">既定では、スタートアップ フォームは `Form1` という名前です。</span><span class="sxs-lookup"><span data-stu-id="535eb-134">By default, the startup form is called `Form1`.</span></span>  
  
2. <span data-ttu-id="535eb-135">次の `testInstance` フィールドを `Form1` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="535eb-135">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     <span data-ttu-id="535eb-136">`testInstance` を `WithEvents` として宣言することで、`Form1` クラスがそのイベントを処理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="535eb-136">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3. <span data-ttu-id="535eb-137">`testInstance` によって発生するイベントを処理するために、次のイベント ハンドラーを `Form1` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="535eb-137">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. <span data-ttu-id="535eb-138">実装クラスをテストするために、`Test` という名前のサブルーチンを `Form1` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="535eb-138">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     <span data-ttu-id="535eb-139">`Test` プロシージャは、`MyInterface` を実装するクラスのインスタンスを作成し、そのインスタンスを `testInstance` フィールドに割り当て、プロパティを設定し、インターフェイスを介してメソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="535eb-139">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5. <span data-ttu-id="535eb-140">スタートアップ フォームの `Form1 Load` プロシージャから `Test` プロシージャを呼び出すコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="535eb-140">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. <span data-ttu-id="535eb-141">F5 キーを押して、`Test` プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="535eb-141">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="535eb-142">"Prop1 が 9 に設定されました" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="535eb-142">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="535eb-143">[OK] をクリックします。クリック後、"The X parameter for Method1 is 5 (Method1 の X パラメーターは 5 です)" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="535eb-143">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="535eb-144">[OK] をクリックします。"The event handler caught the event (イベント ハンドラーがイベントをキャッチしました)" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="535eb-144">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="535eb-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="535eb-145">See also</span></span>

- [<span data-ttu-id="535eb-146">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="535eb-146">Implements Statement</span></span>](../../../language-reference/statements/implements-statement.md)
- [<span data-ttu-id="535eb-147">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="535eb-147">Interfaces</span></span>](index.md)
- [<span data-ttu-id="535eb-148">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="535eb-148">Interface Statement</span></span>](../../../language-reference/statements/interface-statement.md)
- [<span data-ttu-id="535eb-149">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="535eb-149">Event Statement</span></span>](../../../language-reference/statements/event-statement.md)
