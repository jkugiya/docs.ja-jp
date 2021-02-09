---
description: '詳細情報: Of 句 (Visual Basic)'
title: Of 句
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: d6002041a2fe8db5b07e12e9e396a65fde30b716
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768845"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="9b7b2-103">Of 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b7b2-103">Of Clause (Visual Basic)</span></span>

<span data-ttu-id="9b7b2-104">`Of` 句が導入されています。これは、*ジェネリック* クラス、構造体、インターフェイス、デリゲート、またはプロシージャの *型パラメーター* を識別します。</span><span class="sxs-lookup"><span data-stu-id="9b7b2-104">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="9b7b2-105">ジェネリック型については、「[Visual Basic におけるジェネリック型](../../programming-guide/language-features/data-types/generic-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b7b2-105">For information on generic types, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="9b7b2-106">Of キーワードの使用</span><span class="sxs-lookup"><span data-stu-id="9b7b2-106">Using the Of Keyword</span></span>  

 <span data-ttu-id="9b7b2-107">次のコード例では、`Of` キーワードを使用して、2 つの型パラメーターを受け取るクラスの概要を定義しています。</span><span class="sxs-lookup"><span data-stu-id="9b7b2-107">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="9b7b2-108">それは、<xref:System.IComparable> インターフェイスによって、`keyType` パラメーターを *制約* します。つまり、使用するコードで、<xref:System.IComparable> を実装する型引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b7b2-108">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="9b7b2-109">これは、`add` プロシージャで <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> メソッドを呼び出せるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="9b7b2-109">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9b7b2-110">制約の詳細については、「 [Type List](type-list.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9b7b2-110">For more information on constraints, see [Type List](type-list.md).</span></span>  
  
```vb  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 <span data-ttu-id="9b7b2-111">前のクラス定義を完了したら、そこからさまざまな `dictionary` クラスを構築できます。</span><span class="sxs-lookup"><span data-stu-id="9b7b2-111">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="9b7b2-112">`entryType` および `keyType` に指定する型によって、クラスで保持されるエントリの型と、各エントリに関連付けられるキーの型が決まります。</span><span class="sxs-lookup"><span data-stu-id="9b7b2-112">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="9b7b2-113">制約のため、`keyType` に <xref:System.IComparable> を実装する型を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b7b2-113">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="9b7b2-114">次のコード例では、`String` エントリを保持し、それぞれに `Integer` キーを関連付けるオブジェクトを作成しています。</span><span class="sxs-lookup"><span data-stu-id="9b7b2-114">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="9b7b2-115">`Integer` は <xref:System.IComparable> を実装しており、そのため、`keyType` の制約を満たします。</span><span class="sxs-lookup"><span data-stu-id="9b7b2-115">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="9b7b2-116">キーワード `Of` は次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9b7b2-116">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="9b7b2-117">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="9b7b2-117">Class Statement</span></span>](class-statement.md)  
  
 [<span data-ttu-id="9b7b2-118">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="9b7b2-118">Delegate Statement</span></span>](delegate-statement.md)  
  
 [<span data-ttu-id="9b7b2-119">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="9b7b2-119">Function Statement</span></span>](function-statement.md)  
  
 [<span data-ttu-id="9b7b2-120">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="9b7b2-120">Interface Statement</span></span>](interface-statement.md)  
  
 [<span data-ttu-id="9b7b2-121">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="9b7b2-121">Structure Statement</span></span>](structure-statement.md)  
  
 [<span data-ttu-id="9b7b2-122">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="9b7b2-122">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9b7b2-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b7b2-123">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="9b7b2-124">型リスト</span><span class="sxs-lookup"><span data-stu-id="9b7b2-124">Type List</span></span>](type-list.md)
- [<span data-ttu-id="9b7b2-125">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b7b2-125">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="9b7b2-126">In</span><span class="sxs-lookup"><span data-stu-id="9b7b2-126">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="9b7b2-127">Out</span><span class="sxs-lookup"><span data-stu-id="9b7b2-127">Out</span></span>](../modifiers/out-generic-modifier.md)
