---
description: '詳細情報: 方法:オブジェクトのメンバーにアクセスする (Visual Basic)'
title: '方法: オブジェクトのメンバーにアクセスする'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: b4aed213bbe520b7b7027acc146d0973f7273fd1
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100435526"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="9f3bf-103">方法: オブジェクトのメンバーにアクセスする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f3bf-103">How to: Access Members of an Object (Visual Basic)</span></span>

<span data-ttu-id="9f3bf-104">オブジェクトを参照しているオブジェクト変数がある場合、そのオブジェクトのメンバー (メソッド、プロパティ、フィールド、イベントなど) を使いたいことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-104">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="9f3bf-105">たとえば、新しい <xref:System.Windows.Forms.Form> オブジェクトを作成した後、その <xref:System.Windows.Forms.Control.Text%2A> プロパティを設定したり、その <xref:System.Windows.Forms.Control.Focus%2A> メソッドを呼び出したりする場合です。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-105">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="9f3bf-106">メンバーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="9f3bf-106">Accessing Members</span></span>

<span data-ttu-id="9f3bf-107">オブジェクトのメンバーには、それを参照している変数を使用してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-107">You access an object's members through the variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="9f3bf-108">オブジェクトのメンバーにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="9f3bf-108">To access members of an object</span></span>

- <span data-ttu-id="9f3bf-109">オブジェクト変数名とメンバー名の間に、メンバー アクセス演算子 (`.`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-109">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    currentText = newForm.Text
    ```

    <span data-ttu-id="9f3bf-110">メンバーが [Shared](../../../language-reference/modifiers/shared.md) である場合は、そのメンバーにアクセスするために変数は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-110">If the member is [Shared](../../../language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>

## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="9f3bf-111">既知の型のオブジェクトのメンバーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="9f3bf-111">Accessing Members of an Object of Known Type</span></span>

<span data-ttu-id="9f3bf-112">コンパイル時にオブジェクトの型がわかっている場合は、それを参照している変数に対して "*事前バインディング*" を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-112">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="9f3bf-113">コンパイル時に型がわかっているオブジェクトのメンバーにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="9f3bf-113">To access members of an object for which you know the type at compile time</span></span>

1. <span data-ttu-id="9f3bf-114">変数に割り当てるオブジェクトの型として、オブジェクト変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-114">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    <span data-ttu-id="9f3bf-115">`Option Strict On` を使用すると、<xref:System.Windows.Forms.Form> オブジェクト (または、<xref:System.Windows.Forms.Form> から派生した型のオブジェクト) のみを、`extraForm` に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-115">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="9f3bf-116"><xref:System.Windows.Forms.Form> への `CType` 拡大変換を使用してクラスまたは構造体を定義した場合は、そのクラスまたは構造体を `extraForm` に割り当てることもできます。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-116">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>

2. <span data-ttu-id="9f3bf-117">オブジェクト変数名とメンバー名の間に、メンバー アクセス演算子 (`.`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-117">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    extraForm.Show()
    ```

    <span data-ttu-id="9f3bf-118">`Option Strict` の設定に関係なく、<xref:System.Windows.Forms.Form> クラスに固有のすべてのメソッドとプロパティにアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-118">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>

## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="9f3bf-119">型が不明なオブジェクトのメンバーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="9f3bf-119">Accessing Members of an Object of Unknown Type</span></span>

<span data-ttu-id="9f3bf-120">コンパイル時にオブジェクトの型がわからない場合は、それを参照している変数に対して "*遅延バインディング*" を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-120">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="9f3bf-121">コンパイル時に型がわからないオブジェクトのメンバーにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="9f3bf-121">To access members of an object for which you do not know the type at compile time</span></span>

1. <span data-ttu-id="9f3bf-122">オブジェクト変数を [Object データ型](../../../language-reference/data-types/object-data-type.md)として宣言します。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-122">Declare the object variable to be of the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="9f3bf-123">(変数を `Object` として宣言することは、<xref:System.Object?displayProperty=nameWithType> として宣言することと同じです。)</span><span class="sxs-lookup"><span data-stu-id="9f3bf-123">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>

    ```vb
    Dim someControl As Object
    ```

    <span data-ttu-id="9f3bf-124">`Option Strict On` を使用すると、<xref:System.Object> クラスで定義されているメンバーにのみアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-124">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>

2. <span data-ttu-id="9f3bf-125">オブジェクト変数名とメンバー名の間に、メンバー アクセス演算子 (`.`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-125">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    someControl.GetType()
    ```

    <span data-ttu-id="9f3bf-126">オブジェクト変数に割り当てる任意のオブジェクトのメンバーにアクセスできるようにするには、`Option Strict Off` を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-126">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="9f3bf-127">このようにすると、変数に割り当てたオブジェクトによって特定のメンバーが公開されていることを、コンパイラでは保証できません。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-127">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="9f3bf-128">アクセスしようとしたメンバーがオブジェクトによって公開されていない場合、<xref:System.MemberAccessException> 例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="9f3bf-128">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f3bf-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f3bf-129">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="9f3bf-130">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="9f3bf-130">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="9f3bf-131">オブジェクト変数の宣言</span><span class="sxs-lookup"><span data-stu-id="9f3bf-131">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="9f3bf-132">Object 型</span><span class="sxs-lookup"><span data-stu-id="9f3bf-132">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="9f3bf-133">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="9f3bf-133">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
