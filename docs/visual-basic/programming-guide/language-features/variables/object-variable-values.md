---
description: '詳細情報: オブジェクト変数の値 (Visual Basic)'
title: オブジェクト変数の値
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 3259a0b04ed629feea89c1a3e9dba69ed7d226f6
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481676"
---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="1cd27-103">オブジェクト変数の値 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1cd27-103">Object Variable Values (Visual Basic)</span></span>

<span data-ttu-id="1cd27-104">[Object データ型](../../../language-reference/data-types/object-data-type.md)の変数は、任意の型のデータを参照できます。</span><span class="sxs-lookup"><span data-stu-id="1cd27-104">A variable of the [Object Data Type](../../../language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="1cd27-105">`Object` 変数に格納した値はメモリ内のどこかに保持されますが、変数自体にはデータへのポインターが保持されます。</span><span class="sxs-lookup"><span data-stu-id="1cd27-105">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="1cd27-106">オブジェクト分類子関数</span><span class="sxs-lookup"><span data-stu-id="1cd27-106">Object Classifier Functions</span></span>  

 <span data-ttu-id="1cd27-107">Visual Basic には、次の表に示すように、`Object` 変数の参照先に関する情報を返す関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="1cd27-107">Visual Basic supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="1cd27-108">関数</span><span class="sxs-lookup"><span data-stu-id="1cd27-108">Function</span></span>|<span data-ttu-id="1cd27-109">オブジェクト変数が参照している場合に True を返す</span><span class="sxs-lookup"><span data-stu-id="1cd27-109">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|<span data-ttu-id="1cd27-110">単一の値ではなく、値の配列</span><span class="sxs-lookup"><span data-stu-id="1cd27-110">An array of values, rather than a single value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|<span data-ttu-id="1cd27-111">[Date データ型](../../../language-reference/data-types/date-data-type.md)値、または日付と時刻の値として解釈できる文字列</span><span class="sxs-lookup"><span data-stu-id="1cd27-111">A [Date Data Type](../../../language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|<span data-ttu-id="1cd27-112">欠落しているデータまたは存在しないデータを表す <xref:System.DBNull> 型のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="1cd27-112">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|<span data-ttu-id="1cd27-113"><xref:System.Exception> から派生する例外オブジェクト</span><span class="sxs-lookup"><span data-stu-id="1cd27-113">An exception object, which derives from <xref:System.Exception></span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|<span data-ttu-id="1cd27-114">[Nothing](../../../language-reference/nothing.md)、つまり、現在、変数に割り当てられているオブジェクトがない</span><span class="sxs-lookup"><span data-stu-id="1cd27-114">[Nothing](../../../language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|<span data-ttu-id="1cd27-115">数値、または数値として解釈できる文字列</span><span class="sxs-lookup"><span data-stu-id="1cd27-115">A number, or a string that can be interpreted as a number</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|<span data-ttu-id="1cd27-116">参照型 (文字列、配列、デリゲート、またはクラス型など)</span><span class="sxs-lookup"><span data-stu-id="1cd27-116">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="1cd27-117">これらの関数を使用すると、操作やプロシージャに無効な値が送信されるのを回避できます。</span><span class="sxs-lookup"><span data-stu-id="1cd27-117">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="1cd27-118">TypeOf 演算子</span><span class="sxs-lookup"><span data-stu-id="1cd27-118">TypeOf Operator</span></span>  

 <span data-ttu-id="1cd27-119">また、[TypeOf 演算子](../../../language-reference/operators/typeof-operator.md)を使用すると、オブジェクト変数が現在、特定のデータ型を参照しているかどうかを判断することもできます。</span><span class="sxs-lookup"><span data-stu-id="1cd27-119">You can also use the [TypeOf Operator](../../../language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="1cd27-120">オペランドのランタイム型が指定された型から派生しているか、または指定された型を実装している場合、`TypeOf`...`Is` 式の結果は `True` になります。</span><span class="sxs-lookup"><span data-stu-id="1cd27-120">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="1cd27-121">次の例では、値型と参照型を参照するオブジェクト変数に対して `TypeOf` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="1cd27-121">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
```vb  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 <span data-ttu-id="1cd27-122">上記の例では、次の行が **[デバッグ]** ウィンドウに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="1cd27-122">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="1cd27-123">オブジェクト変数 `num` は `Integer` 型のデータを参照し、`frm` はクラス <xref:System.Windows.Forms.Form> のオブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="1cd27-123">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="1cd27-124">オブジェクトの配列</span><span class="sxs-lookup"><span data-stu-id="1cd27-124">Object Arrays</span></span>  

 <span data-ttu-id="1cd27-125">`Object` 変数の配列を宣言して使用することができます。</span><span class="sxs-lookup"><span data-stu-id="1cd27-125">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="1cd27-126">これは、さまざまなデータ型とオブジェクト クラスを処理する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="1cd27-126">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="1cd27-127">配列内のすべての要素が、宣言されたデータ型と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="1cd27-127">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="1cd27-128">このデータ型を `Object` として宣言すると、オブジェクトとクラス インスタンスを配列内の他のデータ型と共に格納できます。</span><span class="sxs-lookup"><span data-stu-id="1cd27-128">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cd27-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="1cd27-129">See also</span></span>

- [<span data-ttu-id="1cd27-130">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="1cd27-130">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="1cd27-131">オブジェクト変数の宣言</span><span class="sxs-lookup"><span data-stu-id="1cd27-131">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="1cd27-132">オブジェクト変数の代入</span><span class="sxs-lookup"><span data-stu-id="1cd27-132">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="1cd27-133">方法: オブジェクトの現在のインスタンスを参照する</span><span class="sxs-lookup"><span data-stu-id="1cd27-133">How to: Refer to the Current Instance of an Object</span></span>](how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="1cd27-134">方法: オブジェクト変数で参照している型を確認する</span><span class="sxs-lookup"><span data-stu-id="1cd27-134">How to: Determine What Type an Object Variable Refers To</span></span>](how-to-determine-what-type-an-object-variable-refers-to.md)
- [<span data-ttu-id="1cd27-135">方法: 2 つのオブジェクトが関連しているかどうかを判別する</span><span class="sxs-lookup"><span data-stu-id="1cd27-135">How to: Determine Whether Two Objects Are Related</span></span>](how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="1cd27-136">方法: 2 つのオブジェクトが同一であるかどうかを判別する</span><span class="sxs-lookup"><span data-stu-id="1cd27-136">How to: Determine Whether Two Objects Are Identical</span></span>](how-to-determine-whether-two-objects-are-identical.md)
- [<span data-ttu-id="1cd27-137">データの種類</span><span class="sxs-lookup"><span data-stu-id="1cd27-137">Data Types</span></span>](../data-types/index.md)
