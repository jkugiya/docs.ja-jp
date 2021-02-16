---
description: '詳細情報: オブジェクト変数の宣言 (Visual Basic)'
title: オブジェクト変数の宣言
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: 853f9e775976022e52121c164884fd91ef0a831c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463716"
---
# <a name="object-variable-declaration-visual-basic"></a><span data-ttu-id="47adb-103">オブジェクト変数の宣言 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47adb-103">Object Variable Declaration (Visual Basic)</span></span>

<span data-ttu-id="47adb-104">通常の宣言ステートメントを使用して、オブジェクト変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="47adb-104">You use a normal declaration statement to declare an object variable.</span></span> <span data-ttu-id="47adb-105">データ型については、`Object` (つまり、[Object データ型](../../../language-reference/data-types/object-data-type.md)) またはオブジェクトの作成元となるより具体的なクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="47adb-105">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span></span>  
  
 <span data-ttu-id="47adb-106">変数を `Object` として宣言することは、<xref:System.Object?displayProperty=nameWithType> として宣言することと同じです。</span><span class="sxs-lookup"><span data-stu-id="47adb-106">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="47adb-107">特定のオブジェクト クラスを使用して変数を宣言すると、そのクラスによって公開されているすべてのメソッドとプロパティ、およびそのクラスを継承しているクラスに変数でアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="47adb-107">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span></span> <span data-ttu-id="47adb-108"><xref:System.Object> を使用して変数を宣言すると、`Option Strict Off` にして遅延バインディングを許可しない限り、その変数がアクセスできるのは、<xref:System.Object> クラスのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="47adb-108">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="47adb-109">宣言の構文</span><span class="sxs-lookup"><span data-stu-id="47adb-109">Declaration Syntax</span></span>  

 <span data-ttu-id="47adb-110">オブジェクト変数を宣言するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="47adb-110">Use the following syntax to declare an object variable:</span></span>  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 <span data-ttu-id="47adb-111">宣言で [Public](../../../language-reference/modifiers/public.md)、[Protected](../../../language-reference/modifiers/protected.md)、[Friend](../../../language-reference/modifiers/friend.md)、`Protected Friend`、[Private](../../../language-reference/modifiers/private.md)、[Shared](../../../language-reference/modifiers/shared.md)、[Static](../../../language-reference/modifiers/static.md) のいずれかを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="47adb-111">You can also specify [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../language-reference/modifiers/private.md), [Shared](../../../language-reference/modifiers/shared.md), or [Static](../../../language-reference/modifiers/static.md) in the declaration.</span></span> <span data-ttu-id="47adb-112">次の宣言の例は有効です。</span><span class="sxs-lookup"><span data-stu-id="47adb-112">The following example declarations are valid:</span></span>  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a><span data-ttu-id="47adb-113">遅延バインディングと事前バインディング</span><span class="sxs-lookup"><span data-stu-id="47adb-113">Late Binding and Early Binding</span></span>  

 <span data-ttu-id="47adb-114">場合によっては、コードを実行するまで特定のクラスが不明な場合があります。</span><span class="sxs-lookup"><span data-stu-id="47adb-114">Sometimes the specific class is unknown until your code runs.</span></span> <span data-ttu-id="47adb-115">この場合は、`Object` データ型を使用して、オブジェクト変数を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47adb-115">In this case, you must declare the object variable with the `Object` data type.</span></span> <span data-ttu-id="47adb-116">これにより、オブジェクトの任意の型への一般的な参照が作成され、特定のクラスが実行時に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="47adb-116">This creates a general reference to any type of object, and the specific class is assigned at run time.</span></span> <span data-ttu-id="47adb-117">これは "*遅延バインディング*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="47adb-117">This is called *late binding*.</span></span> <span data-ttu-id="47adb-118">遅延バインディングでは、追加の実行時間が必要です。</span><span class="sxs-lookup"><span data-stu-id="47adb-118">Late binding requires additional execution time.</span></span> <span data-ttu-id="47adb-119">また、コードは、最後に割り当てたクラスのメソッドとプロパティに限定されます。</span><span class="sxs-lookup"><span data-stu-id="47adb-119">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span></span> <span data-ttu-id="47adb-120">これにより、コードが別のクラスのメンバーにアクセスしようとした場合に、実行時エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="47adb-120">This can cause run-time errors if your code attempts to access members of a different class.</span></span>  
  
 <span data-ttu-id="47adb-121">コンパイル時に特定のクラスがわかっている場合は、そのクラスのオブジェクト変数を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47adb-121">When you know the specific class at compile time, you should declare the object variable to be of that class.</span></span> <span data-ttu-id="47adb-122">これは、*事前バインディング* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="47adb-122">This is called *early binding*.</span></span> <span data-ttu-id="47adb-123">事前バインディングにより、パフォーマンスが向上し、コードが特定のクラスのすべてのメソッドとプロパティにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="47adb-123">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span></span> <span data-ttu-id="47adb-124">前の例の宣言では、変数 `objA` がクラス <xref:System.Windows.Forms.Label?displayProperty=nameWithType> のオブジェクトのみを使用する場合、その宣言で `As System.Windows.Forms.Label` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47adb-124">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.</span></span>  
  
### <a name="advantages-of-early-binding"></a><span data-ttu-id="47adb-125">事前バインディングの利点</span><span class="sxs-lookup"><span data-stu-id="47adb-125">Advantages of Early Binding</span></span>  

 <span data-ttu-id="47adb-126">オブジェクト変数を特定のクラスとして宣言することには、いくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="47adb-126">Declaring an object variable as a specific class gives you several advantages:</span></span>  
  
- <span data-ttu-id="47adb-127">自動型チェック</span><span class="sxs-lookup"><span data-stu-id="47adb-127">Automatic type checking</span></span>  
  
- <span data-ttu-id="47adb-128">特定のクラスのすべてのメンバーへのアクセスが保証される</span><span class="sxs-lookup"><span data-stu-id="47adb-128">Guaranteed access to all members of the specific class</span></span>  
  
- <span data-ttu-id="47adb-129">コード エディターでの Microsoft IntelliSense のサポート</span><span class="sxs-lookup"><span data-stu-id="47adb-129">Microsoft IntelliSense support in the Code Editor</span></span>  
  
- <span data-ttu-id="47adb-130">コードの読みやすさの向上</span><span class="sxs-lookup"><span data-stu-id="47adb-130">Improved readability of your code</span></span>  
  
- <span data-ttu-id="47adb-131">コード内のエラーの数が減る</span><span class="sxs-lookup"><span data-stu-id="47adb-131">Fewer errors in your code</span></span>  
  
- <span data-ttu-id="47adb-132">実行時ではなくコンパイル時にエラーが見つかる</span><span class="sxs-lookup"><span data-stu-id="47adb-132">Errors caught at compile time rather than run time</span></span>  
  
- <span data-ttu-id="47adb-133">コード実行の高速化</span><span class="sxs-lookup"><span data-stu-id="47adb-133">Faster code execution</span></span>  
  
## <a name="access-to-object-variable-members"></a><span data-ttu-id="47adb-134">オブジェクト変数メンバーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="47adb-134">Access to Object Variable Members</span></span>  

 <span data-ttu-id="47adb-135">`Option Strict` が `On` になっている場合に、オブジェクト変数がアクセスできるのは、それを宣言するときに指定したクラスのメソッドとプロパティだけです。</span><span class="sxs-lookup"><span data-stu-id="47adb-135">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="47adb-136">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="47adb-136">The following example illustrates this.</span></span>  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 <span data-ttu-id="47adb-137">この例の場合、 `p` で使用できるのは <xref:System.Object> クラス自体のメンバーのみです。 `Left` プロパティは含まれません。</span><span class="sxs-lookup"><span data-stu-id="47adb-137">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="47adb-138">一方、 `q` は、 <xref:System.Windows.Forms.Label>型として宣言されているため、 <xref:System.Windows.Forms.Label> 名前空間の <xref:System.Windows.Forms> クラスのすべてのメソッドとプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="47adb-138">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
## <a name="flexibility-of-object-variables"></a><span data-ttu-id="47adb-139">オブジェクト変数の柔軟性</span><span class="sxs-lookup"><span data-stu-id="47adb-139">Flexibility of Object Variables</span></span>  

 <span data-ttu-id="47adb-140">継承階層内のオブジェクトを操作する場合は、オブジェクト変数の宣言に使用するクラスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="47adb-140">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span></span> <span data-ttu-id="47adb-141">この選択を行うには、オブジェクトの割り当ての柔軟性と、クラスのメンバーへのアクセスとのバランスを取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="47adb-141">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span></span> <span data-ttu-id="47adb-142">たとえば、<xref:System.Windows.Forms.Form?displayProperty=nameWithType> クラスにつながる継承階層を考えてみます。</span><span class="sxs-lookup"><span data-stu-id="47adb-142">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:</span></span>  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 <span data-ttu-id="47adb-143">アプリケーションで、クラス <xref:System.Windows.Forms.Form> から継承される `specialForm` というフォーム クラスが定義されているとします。</span><span class="sxs-lookup"><span data-stu-id="47adb-143">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="47adb-144">次の例に示すように、明確に `specialForm` を参照するオブジェクト変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="47adb-144">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span></span>  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 <span data-ttu-id="47adb-145">上記の例の宣言では、変数 `nextForm` を `specialForm` クラスのオブジェクトに限定していますが、`specialForm` のすべてのメソッドとプロパティが、`nextForm` と、`specialForm` の継承元のすべてのクラスのすべてのメンバーで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="47adb-145">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span></span>  
  
 <span data-ttu-id="47adb-146">次の例に示すように、オブジェクト変数は、<xref:System.Windows.Forms.Form> 型になるように宣言することで、より一般的なものにすることができます。</span><span class="sxs-lookup"><span data-stu-id="47adb-146">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span></span>  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="47adb-147">上記の例の宣言により、アプリケーションの任意のフォームを `anyForm` に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="47adb-147">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span></span> <span data-ttu-id="47adb-148">ただし、`anyForm` はクラス <xref:System.Windows.Forms.Form> のすべてのメンバーにアクセスできますが、`specialForm` などの特定のフォームに対して定義されている追加のメソッドやプロパティを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="47adb-148">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span></span>  
  
 <span data-ttu-id="47adb-149">基底クラスのすべてのメンバーは派生クラスで使用できますが、派生クラスの追加メンバーを基底クラスで使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="47adb-149">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47adb-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="47adb-150">See also</span></span>

- [<span data-ttu-id="47adb-151">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="47adb-151">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="47adb-152">オブジェクト変数の代入</span><span class="sxs-lookup"><span data-stu-id="47adb-152">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="47adb-153">オブジェクト変数の値</span><span class="sxs-lookup"><span data-stu-id="47adb-153">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="47adb-154">方法: Visual Basic でオブジェクト変数を宣言し、オブジェクト変数にオブジェクトを代入する</span><span class="sxs-lookup"><span data-stu-id="47adb-154">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="47adb-155">方法: オブジェクトのメンバーにアクセスする</span><span class="sxs-lookup"><span data-stu-id="47adb-155">How to: Access Members of an Object</span></span>](how-to-access-members-of-an-object.md)
- [<span data-ttu-id="47adb-156">New 演算子</span><span class="sxs-lookup"><span data-stu-id="47adb-156">New Operator</span></span>](../../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="47adb-157">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="47adb-157">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="47adb-158">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="47adb-158">Local Type Inference</span></span>](local-type-inference.md)
