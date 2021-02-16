---
description: '詳細情報: チュートリアル: クラスの定義 (Visual Basic)'
title: クラスの定義
ms.date: 07/20/2015
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
ms.openlocfilehash: a97e04b92db3387966afa410d5697a05b482ae09
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438789"
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="abda5-103">チュートリアル: クラスの定義 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abda5-103">Walkthrough: Defining Classes (Visual Basic)</span></span>

<span data-ttu-id="abda5-104">このチュートリアルでは、クラスを定義する方法について説明します。このクラスを使用してオブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="abda5-104">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="abda5-105">また、新しいクラスにプロパティとメソッドを追加する方法と、オブジェクトを初期化する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="abda5-105">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a><span data-ttu-id="abda5-106">クラスを定義するには</span><span class="sxs-lookup"><span data-stu-id="abda5-106">To define a class</span></span>
  
1. <span data-ttu-id="abda5-107">**[ファイル]** メニューの **[新しいプロジェクト]** をクリックして、プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="abda5-107">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="abda5-108">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="abda5-108">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="abda5-109">Visual Basic プロジェクト テンプレートの一覧から [Windows アプリケーション] を選択して、新しいプロジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="abda5-109">Select Windows Application from the list of Visual Basic project templates to display the new project.</span></span>  
  
3. <span data-ttu-id="abda5-110">**[プロジェクト]** メニューの **[クラスの追加]** をクリックして、プロジェクトに新しいクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="abda5-110">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="abda5-111">**[新しい項目の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="abda5-111">The **Add New Item** dialog box appears.</span></span>  
  
4. <span data-ttu-id="abda5-112">**[クラス]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="abda5-112">Select the **Class** template.</span></span>  
  
5. <span data-ttu-id="abda5-113">新しいクラスに `UserNameInfo.vb` という名前を指定し、 **[追加]** をクリックして新しいクラスのコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="abda5-113">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > <span data-ttu-id="abda5-114">Visual Basic **コード エディター** を使用すると、`Class` キーワードに続けて新しいクラスの名前を入力することで、クラスをスタートアップ フォームに追加できます。</span><span class="sxs-lookup"><span data-stu-id="abda5-114">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="abda5-115">**コードエディター** には、対応する `End Class` ステートメントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="abda5-115">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6. <span data-ttu-id="abda5-116">`Class` ステートメントと `End Class` ステートメントの間に次のコードを追加して、クラスのプライベート フィールドを定義します。</span><span class="sxs-lookup"><span data-stu-id="abda5-116">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     <span data-ttu-id="abda5-117">フィールドを `Private` として宣言すると、そのクラス内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="abda5-117">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="abda5-118">より多くのアクセスを提供する `Public` などのアクセス修飾子を使用すると、クラスの外部からフィールドを使用できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="abda5-118">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="abda5-119">詳しくは、「[Visual Basic でのアクセス レベル](../declared-elements/access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abda5-119">For more information, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
7. <span data-ttu-id="abda5-120">次のコードを追加して、クラスのプロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="abda5-120">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. <span data-ttu-id="abda5-121">次のコードを追加して、クラスのメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="abda5-121">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. <span data-ttu-id="abda5-122">`Sub New` という名前のプロシージャを追加して、新しいクラスのパラメーター化されたコンストラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="abda5-122">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     <span data-ttu-id="abda5-123">このクラスに基づくオブジェクトが作成されると、`Sub New` コンストラクターが自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="abda5-123">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="abda5-124">このコンストラクターは、ユーザー名を保持するフィールドの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="abda5-124">This constructor sets the value of the field that holds the user name.</span></span>  
  
## <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="abda5-125">クラスをテストするボタンを作成するには</span><span class="sxs-lookup"><span data-stu-id="abda5-125">To create a button to test the class</span></span>
  
1. <span data-ttu-id="abda5-126">**ソリューション エクスプローラー** で名前を右クリックし、 **[ビュー デザイナー]** をクリックして、スタートアップ フォームをデザイン モードに変更します。</span><span class="sxs-lookup"><span data-stu-id="abda5-126">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="abda5-127">既定では、Windows アプリケーション プロジェクトのスタートアップ フォームには、Form1.vb という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="abda5-127">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="abda5-128">メイン フォームが表示されます。</span><span class="sxs-lookup"><span data-stu-id="abda5-128">The main form will then appear.</span></span>  
  
2. <span data-ttu-id="abda5-129">メイン フォームにボタンを追加し、それをダブルクリックして、`Button1_Click` イベント ハンドラーのコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="abda5-129">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="abda5-130">テスト プロシージャを呼び出す次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="abda5-130">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a><span data-ttu-id="abda5-131">アプリケーションを実行するには</span><span class="sxs-lookup"><span data-stu-id="abda5-131">To run your application</span></span>
  
1. <span data-ttu-id="abda5-132">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="abda5-132">Run your application by pressing F5.</span></span> <span data-ttu-id="abda5-133">フォーム上のボタンをクリックして、テスト プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="abda5-133">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="abda5-134">元の `UserName` が "MOORE, BOBBY" であることを示すメッセージが表示されます。これは、プロシージャがオブジェクトの `Capitalize` メソッドを呼び出したためです。</span><span class="sxs-lookup"><span data-stu-id="abda5-134">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2. <span data-ttu-id="abda5-135">**[OK]** をクリックしてメッセージ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="abda5-135">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="abda5-136">`Button1 Click` プロシージャによって `UserName` プロパティの値が変更され、`UserName` の新しい値が "Worden, Joe" であることを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="abda5-136">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abda5-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="abda5-137">See also</span></span>

- [<span data-ttu-id="abda5-138">オブジェクト指向プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abda5-138">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
- [<span data-ttu-id="abda5-139">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="abda5-139">Objects and Classes</span></span>](index.md)
