---
description: '詳細情報: オブジェクト変数への代入 (Visual Basic)'
title: オブジェクト変数の代入
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: ac5e534a03d651a23e651e1049477b2bd0769b82
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481650"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="a3799-103">オブジェクト変数への代入 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3799-103">Object Variable Assignment (Visual Basic)</span></span>

<span data-ttu-id="a3799-104">オブジェクトにオブジェクト変数を代入するには、通常の代入ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="a3799-104">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="a3799-105">次の例で示すように、オブジェクト式または [Nothing](../../../language-reference/nothing.md) キーワードを代入することができます。</span><span class="sxs-lookup"><span data-stu-id="a3799-105">You can assign an object expression or the [Nothing](../../../language-reference/nothing.md) keyword, as the following example illustrates.</span></span>

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

<span data-ttu-id="a3799-106">`Nothing` は、現在変数に代入されているオブジェクトがないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="a3799-106">`Nothing` means there is no object currently assigned to the variable.</span></span>

## <a name="initialization"></a><span data-ttu-id="a3799-107">初期化</span><span class="sxs-lookup"><span data-stu-id="a3799-107">Initialization</span></span>

<span data-ttu-id="a3799-108">コードの実行が開始されると、オブジェクト変数は、`Nothing` に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="a3799-108">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="a3799-109">宣言に初期化を含むものは、宣言ステートメントの実行時に、指定された値に再初期化されます。</span><span class="sxs-lookup"><span data-stu-id="a3799-109">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>

<span data-ttu-id="a3799-110">宣言に初期化を含めるには、[New](../../../language-reference/operators/new-operator.md) キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="a3799-110">You can include initialization in your declaration by using the [New](../../../language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="a3799-111">次の宣言ステートメントは、オブジェクト変数 `testUri` と `ver` を宣言し、それらに特定のオブジェクトを代入します。</span><span class="sxs-lookup"><span data-stu-id="a3799-111">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="a3799-112">それぞれは、適切なクラスのオーバーロードされたコンストラクターのいずれかを使用して、オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="a3799-112">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a><span data-ttu-id="a3799-113">関連付けの解除</span><span class="sxs-lookup"><span data-stu-id="a3799-113">Disassociation</span></span>

<span data-ttu-id="a3799-114">オブジェクト変数を `Nothing` に設定すると、変数と特定のオブジェクトの関連付けは解除されます。</span><span class="sxs-lookup"><span data-stu-id="a3799-114">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="a3799-115">これにより、変数の変更によってオブジェクトが誤って変更されることがなくなります。</span><span class="sxs-lookup"><span data-stu-id="a3799-115">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="a3799-116">また、次の例で示すように、オブジェクト変数が有効なオブジェクトを指しているかどうかをテストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a3799-116">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

<span data-ttu-id="a3799-117">変数が参照するオブジェクトが別のアプリケーション内にある場合、このテストでは、そのアプリケーションが終了したか、またはオブジェクトを無効にしただけであるかを判断することはできません。</span><span class="sxs-lookup"><span data-stu-id="a3799-117">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>

<span data-ttu-id="a3799-118">値が `Nothing` に設定されたオブジェクト変数は、"*null 参照*" とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="a3799-118">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>

## <a name="current-instance"></a><span data-ttu-id="a3799-119">現在のインスタンス</span><span class="sxs-lookup"><span data-stu-id="a3799-119">Current Instance</span></span>

<span data-ttu-id="a3799-120">オブジェクトの "*現在のインスタンス*" は、コードで現在実行されているインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="a3799-120">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="a3799-121">すべてのコードはプロシージャ内で実行されるため、現在のインスタンスは、プロシージャを呼び出したインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="a3799-121">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>

<span data-ttu-id="a3799-122">`Me` キーワードは、現在のインスタンスを参照するオブジェクト変数として機能します。</span><span class="sxs-lookup"><span data-stu-id="a3799-122">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="a3799-123">プロシージャが [Shared](../../../language-reference/modifiers/shared.md) ではない場合、`Me` キーワードを使用して、現在のインスタンスへのポインターを取得できます。</span><span class="sxs-lookup"><span data-stu-id="a3799-123">If a procedure is not [Shared](../../../language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="a3799-124">Shared プロシージャを、クラスの特定のインスタンスに関連付けることはできません。</span><span class="sxs-lookup"><span data-stu-id="a3799-124">Shared procedures cannot be associated with a specific instance of a class.</span></span>

<span data-ttu-id="a3799-125">`Me` は、現在のインスタンスを別のモジュールのプロシージャに渡す場合に使用すると特に有用です。</span><span class="sxs-lookup"><span data-stu-id="a3799-125">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="a3799-126">たとえば、複数の XML ドキュメントがあり、これらのすべてに何らかの標準テキストを追加したいとします。</span><span class="sxs-lookup"><span data-stu-id="a3799-126">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="a3799-127">次の例は、このためのプロシージャを定義します。</span><span class="sxs-lookup"><span data-stu-id="a3799-127">The following example defines a procedure to do this.</span></span>

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

<span data-ttu-id="a3799-128">すべての XML ドキュメント オブジェクトは、このプロシージャを呼び出して、その現在のインスタンスを引数として渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="a3799-128">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="a3799-129">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a3799-129">The following example demonstrates this.</span></span>

```vb
addStandardText(Me)
```

## <a name="see-also"></a><span data-ttu-id="a3799-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3799-130">See also</span></span>

- [<span data-ttu-id="a3799-131">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="a3799-131">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="a3799-132">オブジェクト変数の宣言</span><span class="sxs-lookup"><span data-stu-id="a3799-132">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="a3799-133">オブジェクト変数の値</span><span class="sxs-lookup"><span data-stu-id="a3799-133">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="a3799-134">方法: Visual Basic でオブジェクト変数を宣言してオブジェクトを代入する</span><span class="sxs-lookup"><span data-stu-id="a3799-134">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="a3799-135">方法: オブジェクト変数がインスタンスを参照しないようにする</span><span class="sxs-lookup"><span data-stu-id="a3799-135">How to: Make an Object Variable Not Refer to Any Instance</span></span>](how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [<span data-ttu-id="a3799-136">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="a3799-136">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
