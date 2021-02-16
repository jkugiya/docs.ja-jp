---
description: '詳細情報: 値型と参照型'
title: 値型と参照型
ms.date: 07/20/2015
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
ms.openlocfilehash: 22cce68260955545e810f6fefe645b5ad6a37ca5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462140"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="7d9a3-103">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="7d9a3-103">Value Types and Reference Types</span></span>

<span data-ttu-id="7d9a3-104">Visual Basic には、参照型と値型という 2 種類の型があります。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-104">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="7d9a3-105">参照型の変数はデータ (オブジェクト) への参照を格納するのに対して、値型の変数はデータを直接格納します。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-105">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="7d9a3-106">参照型の場合、2 つの変数が同じオブジェクトを参照できるため、ある変数に対する演算によって、他の変数が参照しているオブジェクトが影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-106">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="7d9a3-107">値型の場合、各変数が独自のデータ コピーを保持し、ある変数に対する操作が別の変数に影響を与えることはありません ([パラメーターの ByRef 修飾子](../../../language-reference/modifiers/byref.md)の場合を除きます)。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-107">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="7d9a3-108">値型</span><span class="sxs-lookup"><span data-stu-id="7d9a3-108">Value Types</span></span>  

 <span data-ttu-id="7d9a3-109">データ型は、独自のメモリ割り当てでデータを保持する場合、"*値型*" です。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-109">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="7d9a3-110">値型は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-110">Value types include the following:</span></span>  
  
- <span data-ttu-id="7d9a3-111">すべての数値データ型</span><span class="sxs-lookup"><span data-stu-id="7d9a3-111">All numeric data types</span></span>  
  
- <span data-ttu-id="7d9a3-112">`Boolean`、 `Char`、および `Date`</span><span class="sxs-lookup"><span data-stu-id="7d9a3-112">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="7d9a3-113">すべての構造体 (メンバーが参照型の場合であっても)</span><span class="sxs-lookup"><span data-stu-id="7d9a3-113">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="7d9a3-114">列挙体 (基になる型が常に `SByte`、`Short`、`Integer`、`Long`、`Byte`、`UShort`、`UInteger`、または `ULong` であるため)</span><span class="sxs-lookup"><span data-stu-id="7d9a3-114">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="7d9a3-115">すべての構造体は、参照型のメンバーが含まれている場合でも、値型です。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-115">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="7d9a3-116">このため、`Char` や `Integer` などの値型は .NET Framework 構造体によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-116">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="7d9a3-117">予約済みのキーワード (`Decimal`など) を使用して値型を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-117">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="7d9a3-118">`New` キーワードを使用して値型を初期化することもできます。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-118">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="7d9a3-119">これは、型にパラメーターを受け取るコンストラクターがある場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-119">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="7d9a3-120">この例として、指定したパーツから新しい `Decimal` 値を構築する <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> コンストラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-120">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="7d9a3-121">参照型</span><span class="sxs-lookup"><span data-stu-id="7d9a3-121">Reference Types</span></span>  

 <span data-ttu-id="7d9a3-122">"*参照型*" はデータへの参照を格納します。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-122">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="7d9a3-123">参照型は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-123">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="7d9a3-124">すべての配列 (要素が値型であっても)</span><span class="sxs-lookup"><span data-stu-id="7d9a3-124">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="7d9a3-125"><xref:System.Windows.Forms.Form> などのクラス型</span><span class="sxs-lookup"><span data-stu-id="7d9a3-125">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="7d9a3-126">デリゲート</span><span class="sxs-lookup"><span data-stu-id="7d9a3-126">Delegates</span></span>  
  
 <span data-ttu-id="7d9a3-127">クラスは "*参照型*" です。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-127">A class is a *reference type*.</span></span> <span data-ttu-id="7d9a3-128">すべての配列は参照型であることにご注意ください。これは、そのメンバーが値型の場合でも同様です。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-128">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="7d9a3-129">参照型はすべて、基になる .NET Framework クラスを表しているため、初期化するときは [New 演算子](../../../language-reference/operators/new-operator.md)キーワードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-129">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="7d9a3-130">次のステートメントで配列を初期化します。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-130">The following statement initializes an array.</span></span>  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="7d9a3-131">型ではない要素</span><span class="sxs-lookup"><span data-stu-id="7d9a3-131">Elements That Are Not Types</span></span>  

 <span data-ttu-id="7d9a3-132">次のプログラミング要素は、宣言した要素のデータ型として指定できないため、型としては使用できません。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-132">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="7d9a3-133">名前空間</span><span class="sxs-lookup"><span data-stu-id="7d9a3-133">Namespaces</span></span>  
  
- <span data-ttu-id="7d9a3-134">モジュール</span><span class="sxs-lookup"><span data-stu-id="7d9a3-134">Modules</span></span>  
  
- <span data-ttu-id="7d9a3-135">イベント</span><span class="sxs-lookup"><span data-stu-id="7d9a3-135">Events</span></span>  
  
- <span data-ttu-id="7d9a3-136">プロパティとプロシージャ</span><span class="sxs-lookup"><span data-stu-id="7d9a3-136">Properties and procedures</span></span>  
  
- <span data-ttu-id="7d9a3-137">変数、定数、フィールド</span><span class="sxs-lookup"><span data-stu-id="7d9a3-137">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="7d9a3-138">オブジェクト データ型の使用</span><span class="sxs-lookup"><span data-stu-id="7d9a3-138">Working with the Object Data Type</span></span>  

 <span data-ttu-id="7d9a3-139">`Object` データ型の変数には、参照型または値型のどちらでも割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-139">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="7d9a3-140">`Object` 変数では、データ自体ではなく、常にデータへの参照が保持されます。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-140">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="7d9a3-141">ただし、`Object` 変数に値型を割り当てた場合は、独自のデータを保持しているかのような動作になります。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-141">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="7d9a3-142">詳細については、「[Object データ型](../../../language-reference/data-types/object-data-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-142">For more information, see [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="7d9a3-143">`Object` 変数が参照型と値型のどちらとして機能しているかを確認するには、<xref:Microsoft.VisualBasic?displayProperty=nameWithType> 名前空間の <xref:Microsoft.VisualBasic.Information> クラスの <xref:Microsoft.VisualBasic.Information.IsReference%2A> メソッドにそれを渡します。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-143">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="7d9a3-144">`Object` 変数の内容が参照型を表している場合、<xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> で `True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="7d9a3-144"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d9a3-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d9a3-145">See also</span></span>

- [<span data-ttu-id="7d9a3-146">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="7d9a3-146">Nullable Value Types</span></span>](nullable-value-types.md)
- [<span data-ttu-id="7d9a3-147">Visual Basic における型変換</span><span class="sxs-lookup"><span data-stu-id="7d9a3-147">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="7d9a3-148">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="7d9a3-148">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="7d9a3-149">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="7d9a3-149">Efficient Use of Data Types</span></span>](efficient-use-of-data-types.md)
- [<span data-ttu-id="7d9a3-150">Object 型</span><span class="sxs-lookup"><span data-stu-id="7d9a3-150">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="7d9a3-151">データの種類</span><span class="sxs-lookup"><span data-stu-id="7d9a3-151">Data Types</span></span>](index.md)
